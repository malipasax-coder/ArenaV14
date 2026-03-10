# ArenaV14
<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>ARENA V14 | ELITE 1v1 PLATFORM</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    
    <script src="https://www.gstatic.com/firebasejs/9.6.10/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.6.10/firebase-auth-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.6.10/firebase-database-compat.js"></script>

    <style>
        @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@700;900&family=Inter:wght@400;600;700;900&display=swap');
        body { font-family: 'Inter', sans-serif; background-color: #020617; color: white; margin: 0; overflow: hidden; user-select: none; }
        .font-orbitron { font-family: 'Orbitron', sans-serif; }
        .glass { background: rgba(15, 23, 42, 0.7); backdrop-filter: blur(12px); border: 1px solid rgba(59, 130, 246, 0.2); box-shadow: 0 4px 30px rgba(0, 0, 0, 0.5); }
        .page { position: fixed; inset: 0; padding: 1.25rem; overflow-y: auto; z-index: 10; padding-bottom: 100px; background: radial-gradient(circle at center, #0f172a 0%, #020617 100%); }
        .hidden { display: none !important; }
        .input-field { width: 100%; background: rgba(15, 23, 42, 0.8); padding: 1rem; border-radius: 0.75rem; margin-bottom: 1rem; border: 1px solid rgba(255,255,255,0.1); outline: none; color: white; transition: all 0.3s ease; }
        .input-field:focus { border-color: #3b82f6; box-shadow: 0 0 15px rgba(59, 130, 246, 0.3); }
        
        #game-area { position: relative; width: 100%; height: 60vh; background: rgba(0,0,0,0.6); border-radius: 24px; border: 2px solid #1e293b; overflow: hidden; cursor: crosshair; }
        .target { position: absolute; width: 55px; height: 55px; background: radial-gradient(circle, #60a5fa, #2563eb); border: 3px solid #fff; border-radius: 50%; display: flex; align-items: center; justify-content: center; box-shadow: 0 0 20px #3b82f6; transform: scale(0); animation: pop 0.2s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards; }
        .target::after { content: ''; width: 25px; height: 25px; background: #fff; border-radius: 50%; opacity: 0.5; }
        @keyframes pop { to { transform: scale(1); } }
        
        #toast-container { position: fixed; top: 20px; left: 50%; transform: translateX(-50%); z-index: 9999; display: flex; flex-direction: column; gap: 10px; pointer-events: none; width: 90%; max-width: 400px; }
        .toast { padding: 12px 20px; border-radius: 8px; font-weight: bold; font-size: 14px; animation: slideDown 0.3s ease forwards; display: flex; align-items: center; gap: 10px; box-shadow: 0 4px 15px rgba(0,0,0,0.3); color: white; }
        .toast.success { background: rgba(16, 185, 129, 0.95); border: 1px solid #34d399; }
        .toast.error { background: rgba(239, 68, 68, 0.95); border: 1px solid #f87171; }
        .toast.info { background: rgba(59, 130, 246, 0.95); border: 1px solid #60a5fa; }
        .toast.admin { background: rgba(139, 92, 246, 0.95); border: 1px solid #a78bfa; }
        .toast.reward { background: linear-gradient(45deg, #f59e0b, #d97706); border: 1px solid #fbbf24; }
        @keyframes slideDown { from { opacity: 0; transform: translateY(-20px); } to { opacity: 1; transform: translateY(0); } }
        
        table { width: 100%; border-collapse: collapse; margin-top: 1rem; }
        th, td { padding: 0.75rem; text-align: left; border-bottom: 1px solid rgba(255,255,255,0.05); font-size: 0.875rem; }
        th { color: #a78bfa; font-weight: 900; }
        tr:hover { background: rgba(255,255,255,0.02); }
    </style>
</head>
<body>

    <div id="toast-container"></div>

    <div id="matchmaking-overlay" class="fixed inset-0 bg-black/90 backdrop-blur-md z-50 hidden flex-col justify-center items-center">
        <div class="w-24 h-24 border-4 border-blue-500 border-t-transparent rounded-full animate-spin mb-6 shadow-[0_0_20px_rgba(59,130,246,0.6)]"></div>
        <h2 class="text-3xl font-black text-white font-orbitron tracking-widest animate-pulse mb-2 text-center">RAKİP ARANIYOR</h2>
        <p class="text-blue-400 font-bold mb-8" id="matchmaking-room-name">...</p>
        <button onclick="cancelMatchmaking()" class="bg-red-600 hover:bg-red-500 px-10 py-4 rounded-xl font-bold shadow-[0_0_20px_rgba(220,38,38,0.5)] transition-all">İPTAL ET VE ÇIK</button>
    </div>

    <div id="auth-page" class="page flex flex-col justify-center items-center">
        <div class="mb-10 text-center">
            <h1 class="text-5xl font-black italic text-transparent bg-clip-text bg-gradient-to-r from-blue-400 to-blue-600 mb-2 font-orbitron drop-shadow-[0_0_15px_rgba(59,130,246,0.5)]">ARENA V14</h1>
            <p class="text-slate-400 text-sm tracking-widest font-bold">1v1 CANLI YARIŞMA PLATFORMU</p>
        </div>
        
        <div id="login-form" class="glass p-8 rounded-3xl w-full max-w-sm">
            <h2 class="text-2xl font-bold mb-6 text-center text-white">SİSTEME GİRİŞ</h2>
            <input id="l-user" type="text" placeholder="Kullanıcı Adı" class="input-field" autocomplete="off">
            <input id="l-pass" type="password" placeholder="Şifre" class="input-field">
            <button onclick="handleLogin()" class="w-full bg-blue-600 hover:bg-blue-500 py-4 rounded-xl font-bold uppercase mb-4 shadow-[0_0_15px_rgba(59,130,246,0.4)] transition-colors">Giriş Yap</button>
            <p class="text-center text-sm text-slate-400">Hesabın yok mu? <a href="#" onclick="toggleAuth()" class="text-blue-400 font-bold">Kayıt Ol</a></p>
        </div>

        <div id="register-form" class="glass p-8 rounded-3xl w-full max-w-sm hidden">
            <h2 class="text-2xl font-bold mb-6 text-center text-white">YENİ KAYIT</h2>
            <input id="r-user" type="text" placeholder="Kullanıcı Adı" class="input-field" autocomplete="off">
            <input id="r-pass" type="password" placeholder="Şifre (Min 6 Karakter)" class="input-field">
            <button onclick="handleRegister()" class="w-full bg-emerald-600 hover:bg-emerald-500 py-4 rounded-xl font-bold uppercase mb-4 shadow-[0_0_15px_rgba(16,185,129,0.4)] transition-colors">Hesap Oluştur</button>
            <p class="text-center text-sm text-slate-400">Zaten üye misin? <a href="#" onclick="toggleAuth()" class="text-emerald-400 font-bold">Giriş Yap</a></p>
        </div>
    </div>

    <div id="admin-page" class="page hidden">
        <div class="flex justify-between items-center mb-6 glass p-4 rounded-2xl border-purple-500/50 shadow-[0_0_20px_rgba(139,92,246,0.3)]">
            <div class="flex items-center gap-3">
                <div class="w-12 h-12 bg-gradient-to-tr from-purple-600 to-pink-600 rounded-full flex items-center justify-center border-2 border-purple-400">
                    <i class="fa-solid fa-user-tie text-xl text-white"></i>
                </div>
                <div>
                    <p class="text-[10px] text-purple-300 font-bold tracking-wider">KONTROL MERKEZİ</p>
                    <h2 class="font-bold text-white text-lg">YÖNETİCİ & MUHASEBE</h2>
                </div>
            </div>
            <button onclick="logout()" class="text-slate-400 hover:text-red-400 bg-slate-800 p-3 rounded-xl transition-colors"><i class="fa-solid fa-power-off"></i></button>
        </div>

        <div class="glass p-6 rounded-3xl border-green-500/30 mb-6 bg-green-900/10">
            <h3 class="text-sm font-bold text-green-400 mb-1"><i class="fa-solid fa-vault mr-2"></i> SİSTEM KASASI (NET KÂR)</h3>
            <span class="text-white font-black text-4xl font-orbitron" id="admin-sys-commission">0 ₺</span>
            <p class="text-[10px] text-slate-400 mt-2">* 1v1 maçlardan otomatik kesilen komisyonların anlık toplamıdır.</p>
        </div>

        <div class="glass p-6 rounded-3xl border-orange-500/30 mb-6">
            <h3 class="text-xl font-black font-orbitron text-orange-400 mb-4"><i class="fa-solid fa-hammer mr-2"></i> YENİ ODA KUR</h3>
            <div class="grid grid-cols-2 gap-3 mb-3">
                <input id="new-room-name" type="text" placeholder="Oda Adı (Örn: 20K VİP)" class="input-field bg-slate-900 border-orange-500/20 col-span-2 m-0">
                <input id="new-room-entry" type="number" placeholder="Giriş Ücreti (₺)" class="input-field bg-slate-900 border-orange-500/20 m-0">
                <input id="new-room-reward" type="number" placeholder="Kazanan Ödülü (₺)" class="input-field bg-slate-900 border-orange-500/20 m-0">
            </div>
            <button onclick="adminCreateRoom()" class="w-full bg-gradient-to-r from-orange-600 to-red-600 py-3 rounded-xl font-bold uppercase shadow-[0_0_15px_rgba(249,115,22,0.4)]">Odayı Lobide Aktif Et</button>
            <div id="admin-active-rooms" class="mt-4 space-y-2"></div>
        </div>

        <div class="glass p-6 rounded-3xl border-purple-500/30 overflow-x-auto">
            <h3 class="text-xl font-black font-orbitron text-purple-400 mb-4"><i class="fa-solid fa-users-gear mr-2"></i> OYUNCU YÖNETİMİ</h3>
            <div class="flex gap-2 mb-4 bg-slate-900 p-3 rounded-xl border border-purple-500/20">
                <input id="quick-uid" type="hidden">
                <input id="quick-username" type="text" placeholder="Seçilen Oyuncu" class="input-field m-0 p-2 text-sm bg-transparent border-none" readonly>
                <input id="quick-amount" type="number" placeholder="Miktar (₺)" class="input-field m-0 p-2 text-sm border-purple-500/30 w-1/3">
                <button onclick="adminExecuteBalance(true)" class="bg-green-600 px-4 rounded-lg font-bold text-xs"><i class="fa-solid fa-plus"></i> EKLE</button>
                <button onclick="adminExecuteBalance(false)" class="bg-red-600 px-4 rounded-lg font-bold text-xs"><i class="fa-solid fa-minus"></i> KES</button>
            </div>
            <table id="admin-users-table">
                <thead>
                    <tr>
                        <th>KULLANICI</th>
                        <th>BAKİYE (₺)</th>
                        <th>G / M</th>
                        <th>SEÇ</th>
                    </tr>
                </thead>
                <tbody id="admin-users-list"></tbody>
            </table>
        </div>
    </div>

    <div id="lobby-page" class="page hidden">
        <div class="flex justify-between items-center mb-6 glass p-4 rounded-2xl">
            <div class="flex items-center gap-3">
                <div class="w-12 h-12 bg-gradient-to-tr from-blue-600 to-cyan-600 rounded-full flex items-center justify-center border-2 border-blue-400">
                    <i class="fa-solid fa-user-astronaut text-xl text-white"></i>
                </div>
                <div>
                    <h2 id="display-name" class="font-bold text-white text-lg">...</h2>
                    <p class="text-[10px] text-slate-400 font-bold tracking-wider mt-1">Galibiyet: <span id="stat-wins" class="text-green-400">0</span> | Mağlubiyet: <span id="stat-losses" class="text-red-400">0</span></p>
                </div>
            </div>
            <button onclick="logout()" class="text-slate-400 hover:text-red-400 bg-slate-800 p-3 rounded-xl transition-colors"><i class="fa-solid fa-power-off"></i></button>
        </div>
        
        <div class="glass p-6 rounded-3xl mb-4 relative overflow-hidden">
            <div class="absolute -right-6 -top-6 text-blue-500/10 text-9xl"><i class="fa-solid fa-gem"></i></div>
            <span class="text-slate-300 font-bold text-sm block mb-1">GÜNCEL BAKİYE (1 ELMAS = 1 ₺)</span>
            <span class="text-cyan-400 font-black text-4xl font-orbitron drop-shadow-[0_0_10px_rgba(34,211,238,0.4)]" id="user-diamonds">0 ₺</span>
        </div>

        <div class="grid grid-cols-3 gap-3 mb-8">
            <button onclick="showPage('store-page')" class="bg-gradient-to-r from-blue-600 to-blue-500 py-3 rounded-xl font-bold text-[10px] shadow-[0_0_15px_rgba(59,130,246,0.3)] flex flex-col items-center gap-1"><i class="fa-solid fa-wallet text-lg"></i> KASA YÜKLE</button>
            <button onclick="claimDailyReward()" class="bg-gradient-to-r from-amber-500 to-orange-500 py-3 rounded-xl font-bold text-[10px] shadow-[0_0_15px_rgba(245,158,11,0.3)] flex flex-col items-center gap-1"><i class="fa-solid fa-gift text-lg"></i> GÜNLÜK ÖDÜL</button>
            <button onclick="openLeaderboard()" class="glass py-3 rounded-xl font-bold text-[10px] text-white border-white/10 flex flex-col items-center gap-1"><i class="fa-solid fa-trophy text-yellow-400 text-lg"></i> SIRALAMA</button>
        </div>

        <h3 class="text-slate-400 font-bold text-sm mb-4 tracking-wider"><i class="fa-solid fa-crosshairs mr-2"></i> CANLI 1v1 ODALARI</h3>
        
        <div class="space-y-4" id="rooms-list">
            <p class="text-center text-slate-500 text-sm"><i class="fa-solid fa-spinner fa-spin"></i> Odalar Yükleniyor...</p>
        </div>
    </div>

    <div id="game-page" class="page hidden bg-[#020617]">
        <div class="glass p-3 rounded-2xl flex justify-between items-center mb-6">
            <div class="text-center w-[30%] bg-blue-900/40 p-2 rounded-xl border border-blue-500/50">
                <p class="text-[10px] text-blue-400 font-bold uppercase truncate">BEN</p>
                <span id="my-score" class="text-3xl font-black font-orbitron text-white">0</span>
            </div>
            <div class="text-center w-[30%]">
                <p class="text-[10px] text-slate-400 font-bold"><i class="fa-solid fa-clock"></i> SÜRE</p>
                <span id="game-time" class="text-2xl font-black font-orbitron text-red-400">30s</span>
            </div>
            <div class="text-center w-[30%] bg-red-900/40 p-2 rounded-xl border border-red-500/50">
                <p class="text-[10px] text-red-400 font-bold uppercase truncate" id="opp-name">RAKİP</p>
                <span id="opp-score" class="text-3xl font-black font-orbitron text-white">0</span>
            </div>
        </div>
        
        <div id="game-area"></div>
    </div>

    <div id="leaderboard-page" class="page hidden">
        <div class="flex items-center mb-8">
            <button onclick="showPage('lobby-page')" class="w-10 h-10 glass rounded-full flex items-center justify-center text-slate-300 hover:text-white mr-4"><i class="fa-solid fa-arrow-left"></i></button>
            <h2 class="text-2xl font-black font-orbitron text-yellow-400"><i class="fa-solid fa-trophy mr-2"></i> ZENGİNLER LİSTESİ</h2>
        </div>
        <div class="glass rounded-3xl p-2" id="leaderboard-list"></div>
    </div>

    <div id="store-page" class="page hidden">
        <div class="flex items-center mb-8">
            <button onclick="showPage('lobby-page')" class="w-10 h-10 glass rounded-full flex items-center justify-center text-slate-300 hover:text-white mr-4"><i class="fa-solid fa-arrow-left"></i></button>
            <h2 class="text-2xl font-black font-orbitron text-blue-400">KASA YÜKLE</h2>
        </div>
        <div class="grid grid-cols-2 gap-4">
            <div onclick="purchaseDiamonds(1000)" class="glass p-6 rounded-2xl text-center border-t-2 border-blue-500 cursor-pointer hover:bg-white/5">
                <i class="fa-solid fa-money-bill-wave text-4xl text-blue-400 mb-3"></i>
                <div class="font-black text-white text-lg">1.000 ₺</div>
            </div>
            <div onclick="purchaseDiamonds(5000)" class="glass p-6 rounded-2xl text-center border-t-2 border-purple-500 cursor-pointer hover:bg-white/5">
                <i class="fa-solid fa-money-bill-wave text-4xl text-purple-400 mb-3"></i>
                <div class="font-black text-white text-lg">5.000 ₺</div>
            </div>
            <div onclick="purchaseDiamonds(10000)" class="glass p-6 rounded-2xl text-center border-t-2 border-orange-500 cursor-pointer hover:bg-white/5 col-span-2">
                <i class="fa-solid fa-money-bill-wave text-4xl text-orange-400 mb-3"></i>
                <div class="font-black text-white text-xl">10.000 ₺ YÜKLE</div>
            </div>
        </div>
    </div>

    <script>
        const firebaseConfig = {
            apiKey: "AIzaSyCpBrkM6Yh__FXhc8aznEp1G2AqMgxr_iE",
            authDomain: "arenav14-8ad95.firebaseapp.com",
            projectId: "arenav14-8ad95",
            storageBucket: "arenav14-8ad95.firebasestorage.app",
            messagingSenderId: "818899825621",
            appId: "1:818899825621:web:a51cd631c943863fcb435c",
            databaseURL: "https://arenav14-8ad95-default-rtdb.firebaseio.com"
        };

        firebase.initializeApp(firebaseConfig);
        const auth = firebase.auth();
        const db = firebase.database();

        let currentUserUid = null;
        let currentUsername = "";
        let userData = { diamonds: 0, wins: 0, losses: 0, lastDaily: 0 };
        let isAdminMode = false;
        
        let gameInterval, targetInterval, timeLeft = 30;
        let currentGameId = null, myPlayerKey = null; // 1v1 Değişkenleri
        let currentMatchRoomId = null, currentMatchEntry = null;

        function showToast(message, type = 'success') {
            const container = document.getElementById('toast-container');
            const toast = document.createElement('div');
            toast.className = `toast ${type}`;
            let icon = type === 'success' ? '<i class="fa-solid fa-circle-check"></i>' : 
                       type === 'error' ? '<i class="fa-solid fa-circle-xmark"></i>' : 
                       type === 'admin' ? '<i class="fa-solid fa-vault"></i>' :
                       type === 'reward' ? '<i class="fa-solid fa-gift"></i>' : '<i class="fa-solid fa-circle-info"></i>';
            toast.innerHTML = `${icon} <span>${message}</span>`;
            container.appendChild(toast);
            setTimeout(() => {
                toast.style.animation = 'slideDown 0.3s ease reverse forwards';
                setTimeout(() => toast.remove(), 300);
            }, 3000);
        }

        function toggleAuth() {
            document.getElementById('login-form').classList.toggle('hidden');
            document.getElementById('register-form').classList.toggle('hidden');
        }

        function formatEmail(username) { return username.trim().toLowerCase() + "@arenav14.app"; }

        function handleRegister() {
            const user = document.getElementById('r-user').value.trim().toLowerCase();
            const pass = document.getElementById('r-pass').value.trim();
            if(user === "admin") return showToast("Bu kullanıcı adı rezerve edilmiştir!", "error");
            if(user.length < 3) return showToast("Kullanıcı adı min 3 karakter!", "error");
            if(pass.length < 6) return showToast("Şifre min 6 karakter!", "error");

            auth.createUserWithEmailAndPassword(formatEmail(user), pass)
                .then((userCred) => {
                    db.ref('users/' + userCred.user.uid).set({
                        username: user, diamonds: 1000, wins: 0, losses: 0, lastDaily: 0
                    }).then(() => {
                        showToast("Kayıt başarılı! 1.000 ₺ Hediye!", "success");
                        toggleAuth();
                    });
                })
                .catch((err) => showToast(err.code === 'auth/email-already-in-use' ? "Kullanıcı adı alınmış!" : err.message, "error"));
        }

        function handleLogin() {
            const user = document.getElementById('l-user').value.trim().toLowerCase();
            const pass = document.getElementById('l-pass').value.trim();
            if(!user || !pass) return showToast("Tüm alanları doldurun!", "error");

            if(user === "admin" && pass === "123456") {
                isAdminMode = true;
                showPage('admin-page');
                startAdminPanel();
                showToast("Muhasebe ve Yönetim Paneline Geçildi", "admin");
                return;
            }

            auth.signInWithEmailAndPassword(formatEmail(user), pass)
                .then((userCred) => {
                    isAdminMode = false;
                    currentUserUid = userCred.user.uid;
                    currentUsername = user;
                    startApp();
                    showToast("Sisteme başarıyla giriş yapıldı.", "success");
                }).catch(() => showToast("Hatalı kullanıcı adı veya şifre!", "error"));
        }

        function logout() {
            if(isAdminMode) {
                isAdminMode = false;
                showPage('auth-page');
            } else {
                auth.signOut().then(() => location.reload());
            }
        }

        function startAdminPanel() {
            db.ref('system/accounting/commission').on('value', snap => {
                document.getElementById('admin-sys-commission').innerText = (snap.val() || 0).toLocaleString('tr-TR') + " ₺";
            });

            db.ref('system/rooms').on('value', snap => {
                let html = '';
                snap.forEach(child => {
                    const r = child.val();
                    html += `
                    <div class="flex justify-between items-center bg-slate-800/50 p-3 rounded-lg border border-slate-700">
                        <div>
                            <span class="font-bold text-white text-sm">${r.name}</span>
                            <div class="text-[10px] text-slate-400">Giriş: ${r.entryFee} ₺ | Ödül: ${r.reward} ₺ | Kesinti: ${r.systemCut} ₺</div>
                        </div>
                        <button onclick="adminDeleteRoom('${child.key}')" class="text-red-500 hover:text-red-400"><i class="fa-solid fa-trash"></i></button>
                    </div>`;
                });
                document.getElementById('admin-active-rooms').innerHTML = html;
            });

            db.ref('users').on('value', snap => {
                let html = '';
                snap.forEach(child => {
                    const u = child.val();
                    html += `
                    <tr>
                        <td class="font-bold text-white uppercase">${u.username}</td>
                        <td class="text-cyan-400 font-bold">${(u.diamonds || 0).toLocaleString('tr-TR')} ₺</td>
                        <td class="text-xs"><span class="text-green-400">${u.wins || 0}</span> / <span class="text-red-400">${u.losses || 0}</span></td>
                        <td>
                            <button onclick="selectUserForBalance('${child.key}', '${u.username}')" class="bg-blue-600 px-3 py-1 rounded text-xs text-white font-bold"><i class="fa-solid fa-hand-pointer"></i></button>
                        </td>
                    </tr>`;
                });
                document.getElementById('admin-users-list').innerHTML = html;
            });
        }

        function adminCreateRoom() {
            const name = document.getElementById('new-room-name').value.trim();
            const entry = parseInt(document.getElementById('new-room-entry').value);
            const reward = parseInt(document.getElementById('new-room-reward').value);

            if(!name || isNaN(entry) || isNaN(reward)) return showToast("Tüm oda bilgilerini eksiksiz girin!", "error");
            
            const sysCut = (entry * 2) - reward;
            if(sysCut < 0) return showToast("Matematiksel Hata: Ödül, havuzdan (Giriş x2) büyük olamaz!", "error");

            db.ref('system/rooms').push({
                name: name, entryFee: entry, reward: reward, systemCut: sysCut
            }).then(() => {
                showToast("Yeni Oda Lobide Aktif Edildi!", "success");
                document.getElementById('new-room-name').value = '';
                document.getElementById('new-room-entry').value = '';
                document.getElementById('new-room-reward').value = '';
            });
        }

        function adminDeleteRoom(roomId) {
            db.ref('system/rooms/' + roomId).remove().then(() => showToast("Oda kapatıldı.", "info"));
        }

        function selectUserForBalance(uid, username) {
            document.getElementById('quick-uid').value = uid;
            document.getElementById('quick-username').value = username.toUpperCase();
        }

        function adminExecuteBalance(isAdd) {
            const uid = document.getElementById('quick-uid').value;
            const username = document.getElementById('quick-username').value;
            const amount = parseInt(document.getElementById('quick-amount').value);
            if(!uid || isNaN(amount) || amount <= 0) return showToast("Oyuncu seçin ve geçerli miktar girin!", "error");
            const finalAmount = isAdd ? amount : -amount;

            db.ref('users/' + uid + '/diamonds').transaction(current => {
                let newVal = (current || 0) + finalAmount;
                return newVal < 0 ? 0 : newVal;
            }, (error, committed, snapshot) => {
                if(error) { showToast("Bakiye işlemi başarısız!", "error"); }
                else if(committed) { 
                    showToast(`${username} bakiyesi güncellendi! Yeni: ${snapshot.val()} ₺`, "admin"); 
                    document.getElementById('quick-amount').value = '';
                }
            });
        }

        function startApp() {
            document.getElementById('display-name').innerText = currentUsername.toUpperCase();
            showPage('lobby-page');
            
            db.ref('users/' + currentUserUid).on('value', snap => {
                if(snap.exists()) {
                    userData = snap.val();
                    document.getElementById('user-diamonds').innerText = (userData.diamonds || 0).toLocaleString('tr-TR') + " ₺";
                    document.getElementById('stat-wins').innerText = userData.wins || 0;
                    document.getElementById('stat-losses').innerText = userData.losses || 0;
                }
            });

            db.ref('system/rooms').on('value', snap => {
                const list = document.getElementById('rooms-list');
                if(!snap.exists()) { list.innerHTML = '<p class="text-center text-slate-500">Şu an aktif oda yok.</p>'; return; }
                
                let html = '';
                snap.forEach(child => {
                    const r = child.val();
                    let borderCol = r.entryFee >= 10000 ? 'border-orange-500' : r.entryFee >= 5000 ? 'border-blue-500' : 'border-slate-400';
                    let titleCol = r.entryFee >= 10000 ? 'text-orange-400' : r.entryFee >= 5000 ? 'text-blue-400' : 'text-slate-300';
                    let btnCol = r.entryFee >= 10000 ? 'bg-orange-600 hover:bg-orange-500' : r.entryFee >= 5000 ? 'bg-blue-600 hover:bg-blue-500' : 'bg-slate-600 hover:bg-slate-500';

                    html += `
                    <div class="glass p-4 rounded-2xl border-l-4 ${borderCol} hover:bg-slate-800/50 transition-colors">
                        <div class="flex justify-between items-center mb-2">
                            <div>
                                <h4 class="font-black text-lg ${titleCol} font-orbitron">${r.name.toUpperCase()}</h4>
                                <p class="text-[10px] text-slate-300">⚔️ 1V1 CANLI SAVAŞ</p>
                            </div>
                            <button onclick="joinRoom('${child.key}', ${r.entryFee}, ${r.reward}, '${r.name}')" class="${btnCol} px-6 py-2 rounded-xl text-xs font-bold">GİRİŞ YAP</button>
                        </div>
                        <div class="text-[10px] text-slate-400 flex justify-between bg-black/40 p-2 rounded-lg">
                            <span>Giriş: <b class="text-red-400">${r.entryFee.toLocaleString('tr-TR')} ₺</b></span>
                            <span>Kazanç: <b class="text-green-400">${r.reward.toLocaleString('tr-TR')} ₺</b></span>
                            <span>Sistem Payı: <b class="text-purple-400">${r.systemCut.toLocaleString('tr-TR')} ₺</b></span>
                        </div>
                    </div>`;
                });
                list.innerHTML = html;
            });

            // 1v1 Oyun Başlangıcını Dinle
            db.ref('system/active_players/' + currentUserUid + '/currentGame').on('value', snap => {
                const gameId = snap.val();
                if(gameId) {
                    hideMatchmakingUI();
                    enterGameScreen(gameId);
                }
            });
        }

        function showPage(id) {
            document.querySelectorAll('.page').forEach(p => p.classList.add('hidden'));
            document.getElementById(id).classList.remove('hidden');
        }

        function claimDailyReward() {
            const now = Date.now();
            if(now - (userData.lastDaily || 0) >= 86400000) {
                db.ref('users/' + currentUserUid + '/diamonds').transaction(curr => (curr || 0) + 250);
                db.ref('users/' + currentUserUid).update({ lastDaily: now });
                showToast("GÜNLÜK ÖDÜL: 250 ₺ Kazandın!", "reward");
            } else {
                showToast(`Ödülünü zaten aldın! Yarına tekrar gel.`, "error");
            }
        }

        function openLeaderboard() {
            showPage('leaderboard-page');
            const listEl = document.getElementById('leaderboard-list');
            db.ref('users').orderByChild('diamonds').limitToLast(10).once('value', snapshot => {
                if(snapshot.exists()) {
                    let players = [];
                    snapshot.forEach(c => players.push(c.val()));
                    players.reverse();
                    let html = '';
                    players.forEach((p, i) => {
                        let c = i===0 ? 'text-yellow-400' : i===1 ? 'text-slate-300' : i===2 ? 'text-orange-400' : 'text-slate-500';
                        html += `
                        <div class="flex justify-between items-center p-4 border-b border-white/5 last:border-0">
                            <div class="flex items-center gap-4">
                                <span class="font-black text-xl w-6 ${c}">#${i+1}</span>
                                <span class="font-bold text-white uppercase">${p.username}</span>
                            </div>
                            <span class="font-bold text-cyan-400 font-orbitron">${(p.diamonds||0).toLocaleString('tr-TR')} ₺</span>
                        </div>`;
                    });
                    listEl.innerHTML = html;
                }
            });
        }

        function purchaseDiamonds(amount) {
            db.ref('users/' + currentUserUid + '/diamonds').transaction(curr => (curr || 0) + amount);
            showToast(`Hesabına ${amount.toLocaleString('tr-TR')} ₺ eklendi!`, "success");
        }

        // --- 1V1 MATCHMAKING MANTIĞI ---
        function joinRoom(roomId, entryFee, reward, roomName) {
            if(userData.diamonds < entryFee) return showToast("Bakiye Yetersiz! Kasa Yükle.", "error");

            // Bakiye Kesme
            db.ref('users/' + currentUserUid + '/diamonds').transaction(curr => {
                if((curr||0) >= entryFee) return curr - entryFee; 
                return curr;
            }, (err, comm, snap) => {
                if(comm && snap.val() < userData.diamonds) {
                    processMatchmaking(roomId, entryFee, reward, roomName);
                } else {
                    showToast("Bakiye işlemi reddedildi!", "error");
                }
            });
        }

        function processMatchmaking(roomId, entryFee, reward, roomName) {
            currentMatchRoomId = roomId;
            currentMatchEntry = entryFee;
            let matchRef = db.ref('system/matchmaking/' + roomId);
            
            matchRef.transaction(current => {
                if (current === null) {
                    // Odada kimse yok, ben bekliyorum
                    return { uid: currentUserUid, username: currentUsername, status: 'waiting', entryFee: entryFee, reward: reward };
                } else if (current.status === 'waiting' && current.uid !== currentUserUid) {
                    // Rakip buldum!
                    current.status = 'matched';
                    current.p2 = { uid: currentUserUid, username: currentUsername };
                    return current;
                } else {
                    return; // İptal
                }
            }, (err, comm, snap) => {
                if(err) return showToast("Eşleşme sunucusu hatası!", "error");
                if(comm && snap.val()) {
                    const data = snap.val();
                    if(data.status === 'matched' && data.p2.uid === currentUserUid) {
                        // Ben Player 2'yim (Rakibi Buldum)
                        setupGame(roomId, {uid: data.uid, username: data.username}, data.p2, entryFee, reward);
                        matchRef.remove(); // Havuzu temizle
                    } else if(data.status === 'waiting' && data.uid === currentUserUid) {
                        // Ben Player 1'im (Bekliyorum)
                        showMatchmakingUI(roomName);
                    }
                }
            });
        }

        function setupGame(roomId, p1, p2, entryFee, reward) {
            const gameId = 'g_' + Date.now();
            const gameData = {
                roomId: roomId, entryFee: entryFee, reward: reward, status: 'playing',
                p1: p1.uid, p1Name: p1.username, p1Score: 0,
                p2: p2.uid, p2Name: p2.username, p2Score: 0
            };
            db.ref('system/games/' + gameId).set(gameData).then(() => {
                db.ref('system/active_players/' + p1.uid + '/currentGame').set(gameId);
                db.ref('system/active_players/' + p2.uid + '/currentGame').set(gameId);
            });
        }

        function showMatchmakingUI(roomName) {
            document.getElementById('matchmaking-room-name').innerText = roomName.toUpperCase();
            document.getElementById('matchmaking-overlay').style.display = 'flex';
        }

        function hideMatchmakingUI() {
            document.getElementById('matchmaking-overlay').style.display = 'none';
        }

        function cancelMatchmaking() {
            if(!currentMatchRoomId) return;
            db.ref('system/matchmaking/' + currentMatchRoomId).transaction(curr => {
                if(curr && curr.uid === currentUserUid) return null; // İptal et ve temizle
                return curr;
            }, (err, comm) => {
                if(comm) {
                    // Paramı geri ver
                    db.ref('users/' + currentUserUid + '/diamonds').transaction(c => (c||0) + currentMatchEntry);
                    hideMatchmakingUI();
                    showToast("Sıradan çıkıldı, para iade edildi.", "info");
                }
            });
        }

        // --- 1V1 OYUN MEKANİĞİ ---
        function enterGameScreen(gameId) {
            currentGameId = gameId;
            score = 0; timeLeft = 30;
            showPage('game-page');
            document.getElementById('game-area').innerHTML = "";
            
            // Oyun Verisini Canlı Dinle (Rakibin skorunu görmek için)
            db.ref('system/games/' + gameId).on('value', snap => {
                const g = snap.val();
                if(!g) return;

                if(currentUserUid === g.p1) {
                    myPlayerKey = 'p1Score';
                    document.getElementById('my-score').innerText = g.p1Score;
                    document.getElementById('opp-score').innerText = g.p2Score;
                    document.getElementById('opp-name').innerText = g.p2Name.toUpperCase();
                } else {
                    myPlayerKey = 'p2Score';
                    document.getElementById('my-score').innerText = g.p2Score;
                    document.getElementById('opp-score').innerText = g.p1Score;
                    document.getElementById('opp-name').innerText = g.p1Name.toUpperCase();
                }
            });

            showToast("VS BAŞLADI! KİMSE KİMSENİN GÖZÜNÜN YAŞINA BAKMAZ!", "info");
            
            // Sayaç
            gameInterval = setInterval(() => {
                timeLeft--;
                document.getElementById('game-time').innerText = timeLeft + "s";
                if(timeLeft <= 0) endGame(false);
            }, 1000);

            // Hedef Üretimi
            spawnTarget();
            targetInterval = setInterval(spawnTarget, 650); // Savaş modu, hedefler daha hızlı!
        }

        function spawnTarget() {
            const area = document.getElementById('game-area');
            const target = document.createElement('div');
            target.className = 'target';
            target.style.left = Math.floor(Math.random() * (area.clientWidth - 70)) + 'px';
            target.style.top = Math.floor(Math.random() * (area.clientHeight - 70)) + 'px';
            
            target.onmousedown = function() {
                this.remove();
                // Veritabanına anında skor yazılımı
                if(currentGameId && myPlayerKey) {
                    db.ref('system/games/' + currentGameId + '/' + myPlayerKey).transaction(s => (s||0)+1);
                }
            };
            area.appendChild(target);
            setTimeout(() => { if(target.parentElement) target.remove(); }, 1000); // 1 saniyede kaybolur
        }

        function endGame(isSurrender) {
            clearInterval(gameInterval);
            clearInterval(targetInterval);
            document.getElementById('game-area').innerHTML = "";
            
            // Dinlemeyi bırak
            db.ref('system/games/' + currentGameId).off();

            // Savaş Sonucunu Hesapla
            db.ref('system/games/' + currentGameId).once('value', snap => {
                const g = snap.val();
                if(!g) {
                    db.ref('system/active_players/' + currentUserUid + '/currentGame').remove();
                    return showPage('lobby-page');
                }

                const myScore = currentUserUid === g.p1 ? g.p1Score : g.p2Score;
                const oppScore = currentUserUid === g.p1 ? g.p2Score : g.p1Score;
                const systemCut = (g.entryFee * 2) - g.reward;

                if(isSurrender) {
                    db.ref('users/' + currentUserUid + '/losses').transaction(c => (c||0) + 1);
                    showToast(`PES ETTİN! ${g.entryFee.toLocaleString('tr-TR')} ₺ Yandı.`, "error");
                } else {
                    if(myScore > oppScore) {
                        // KAZANDI
                        db.ref('users/' + currentUserUid + '/diamonds').transaction(c => (c||0) + g.reward);
                        db.ref('users/' + currentUserUid + '/wins').transaction(c => (c||0) + 1);
                        db.ref('system/accounting/commission').transaction(c => (c||0) + systemCut);
                        showToast(`TEBRİKLER! RAKİBİ EZDİN! ${g.reward.toLocaleString('tr-TR')} ₺ KAZANDIN!`, "success");
                    } else if(myScore < oppScore) {
                        // KAYBETTİ
                        db.ref('users/' + currentUserUid + '/losses').transaction(c => (c||0) + 1);
                        showToast(`YENİLDİN! Rakip senden daha hızlıydı.`, "error");
                    } else {
                        // BERABERE
                        db.ref('users/' + currentUserUid + '/diamonds').transaction(c => (c||0) + g.entryFee);
                        showToast(`MAÇ BERABERE! Para iade edildi.`, "info");
                    }
                }

                // Aktif oyundan çık ve lobiye dön
                db.ref('system/active_players/' + currentUserUid + '/currentGame').remove();
                setTimeout(() => { showPage('lobby-page'); }, 2500);
            });
        }
        
        auth.onAuthStateChanged((user) => {
            if (user && !isAdminMode) {
                currentUserUid = user.uid;
                currentUsername = user.email.split('@')[0];
                startApp();
            } else if (!isAdminMode) {
                showPage('auth-page');
            }
        });
    </script>
</body>
</html>
