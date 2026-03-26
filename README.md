import requests
from telebot import types

# --- 1. الإعدادات الخاصة بك ---
TOKEN = '8710572450:AAEiv8YOXGRMDosY3bb-zWHNSgPQImYrpgw'
ADMIN_ID = 123456789  # ضع الآيدي (ID) الخاص بك هنا (أرقام فقط)

# بيانات الـ API
SMM_API_URL = "https://الرابط_الخاص_بالموقع.com/api/v2" 
SMM_API_KEY = "3a8121775cd65156a4b663aa5a7a4302"

# قائمة الخدمات (يجب مطابقة الـ ID مع الموقع)
SERVICES = {
    'members': {'id': '100', 'price': 2.0, 'name': '👥 أعضاء قنوات'}, 
    'views': {'id': '200', 'price': 0.1, 'name': '👁 مشاهدات منشورات'},
    'reactions': {'id': '300', 'price': 0.5, 'name': '❤️ تفاعلات (لايكات)'}
}

bot = telebot.TeleBot(TOKEN)
user_states = {}

# --- 2. إدارة قاعدة البيانات ---
def init_db():
    conn = sqlite3.connect('smm_database.db')
    c = conn.cursor()
    c.execute('''CREATE TABLE IF NOT EXISTS users 
                 (user_id INTEGER PRIMARY KEY, balance REAL DEFAULT 0)''')
    conn.commit()
    conn.close()

def get_balance(user_id):
    conn = sqlite3.connect('smm_database.db')
    c = conn.cursor()
    c.execute("SELECT balance FROM users WHERE user_id=?", (user_id,))
    res = c.fetchone()
    conn.close()
    if res: 
        return res[0]
    else:
        conn = sqlite3.connect('smm_database.db')
        c = conn.cursor()
        c.execute("INSERT INTO users (user_id, balance) VALUES (?, 0)", (user_id,))
        conn.commit()
        conn.close()
        return 0

def update_balance(user_id, amount):
    conn = sqlite3.connect('smm_database.db')
    c = conn.cursor()
    c.execute("UPDATE users SET balance = balance + ? WHERE user_id = ?", (amount, user_id))
    conn.commit()
    conn.close()

init_db()

# --- 3. الكيبورد الرئيسي ---
def main_menu():
    markup = types.ReplyKeyboardMarkup(resize_keyboard=True)
    markup.add("🚀 طلب خدمة", "💰 رصيدي")
    markup.add("💳 شحن الرصيد", "🛠 الدعم الفني")
    return markup

@bot.message_handler(commands=['start'])
def welcome(message):
    get_balance(message.from_user.id)
    bot.send_message(message.chat.id, "👋 أهلاً بك في بوت الرشق المتكامل!\nخدمات سريعة ودعم متواصل.", reply_markup=main_menu())

# --- 4. معالجة طلب الخدمات ---
@bot.message_handler(func=lambda m: m.text == "🚀 طلب خدمة")
def show_services(message):
    markup = types.InlineKeyboardMarkup()
    for key, s in SERVICES.items():
        markup.add(types.InlineKeyboardButton(f"{s['name']} - ${s['price']}/1k", callback_data=f"ord_{key}"))
    bot.send_message(message.chat.id, "اختر نوع الخدمة التي تود طلبها:", reply_markup=markup)

@bot.callback_query_handler(func=lambda call: call.data.startswith('ord_'))
def handle_selection(call):
    service_key = call.data.split('_')[1]
    user_states[call.from_user.id] = {'service': service_key}
    bot.edit_message_text(f"لقد اخترت: {SERVICES[service_key]['name']}\n\nأرسل الآن الرابط والعدد مفصولين بمسافة.\nمثال:\n`https://t.me/your_channel 500`", call.message.chat.id, call.message.message_id, parse_mode="Markdown")

@bot.message_handler(func=lambda m: m.from_user.id in user_states)
def finalize_order(message):
    try:
        parts = message.text.split()
        if len(parts) < 2:
            bot.reply_to(message, "⚠️ يرجى إرسال الرابط ثم مسافة ثم العدد.")
            return

        link = parts[0]
        quantity = int(parts[1])
        
        service_data = SERVICES[user_states[message.from_user.id]['service']]
        cost = (quantity / 1000) * service_data['price']
        balance = get_balance(message.from_user.id)
        
        if balance < cost:
            bot.reply_to(message, f"❌ رصيدك غير كافٍ!\nالتكلفة: ${cost:.2f}\nرصيدي: ${balance:.2f}")
            del user_states[message.from_user.id]
            return

        # الاتصال بالـ API
        payload = {
            'key': SMM_API_KEY,
            'action': 'add',
            'service': service_data['id'],
            'link': link,
            'quantity': quantity
        }
        
        try:
            response = requests.post(SMM_API_URL, data=payload)
            res_data = response.json()
            if 'order' in res_data:
                update_balance(message.from_user.id, -cost)
                bot.send_message(message.chat.id, f"✅ تم تنفيذ طلبك بنجاح!\nرقم الطلب: `{res_data['order']}`\nالتكلفة: `${cost:.2f}`", parse_mode="Markdown")
            else:
                bot.send_message(message.chat.id, f"❌ فشل من المصدر: {res_data.get('error', 'خطأ غير معروف')}")
        except:
            bot.send_message(message.chat.id, "❌ حدث خطأ في الاتصال بموقع الخدمات.")

        del user_states[message.from_user.id]

    except Exception as e:
        bot.reply_to(message, "⚠️ خطأ! أرسل الرابط ثم مسافة ثم العدد (أرقام فقط).")

# --- 5. لوحة الآدمن ---
@bot.message_handler(commands=['add'])
def add_balance_admin(message):
    if message.from_user.id == ADMIN_ID:
        try:
            parts = message.text.split()
            target_id = int(parts[1])
            amount = float(parts[2])
            update_balance(target_id, amount)
            bot.send_message(message.chat.id, f"✅ تم إضافة ${amount} بنجاح لـ {target_id}")
            bot.send_message(target_id, f"🎉 تم شحن حسابك بمبلغ: ${amount}")
        except:
            bot.send_message(message.chat.id, "الاستخدام: `/add 1234567 10`", parse_mode="Markdown")

@bot.message_handler(func=lambda m: m.text == "💰 رصيدي")
def balance_check(message):
    balance = get_balance(message.from_user.id)
    bot.reply_to(message, f"حسابك: `{message.from_user.id}`\nرصيدك المتوفر: **${balance:.2f}**", parse_mode="Markdown")

@bot.message_handler(func=lambda m: m.text == "💳 شحن الرصيد")
def deposit_msg(message):
    bot.send_message(message.chat.id, "لشحن رصيدك يرجى إرسال المال عبر (زين كاش) ثم تزويد الآدمن بلقطة شاشة.\n\nتواصل هنا: @HL_mdred")

print("البوت يعمل الآن...")
bot.infinity_polling()
