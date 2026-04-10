# NMT-assistant-
<!DOCTYPE html>
<html lang="uk">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>НМТ Академія — Підготовка 2025/2026</title>
<link href="https://fonts.googleapis.com/css2?family=Unbounded:wght@400;600;700;900&family=Manrope:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
/* ============ RESET & VARIABLES ============ */
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
:root {
  --bg: #0d0f1a; --surface: #151728; --surface2: #1e2138; --surface3: #252847;
  --border: rgba(255,255,255,0.07); --border2: rgba(255,255,255,0.12);
  --text: #eef0f8; --text-muted: #7b82a8; --text-dim: #4a5080;
  --accent: #4f6ef7; --accent2: #a78bfa; --accent3: #60a5fa;
  --coin: #f5c542; --success: #22c55e; --error: #ef4444; --warn: #f59e0b;
  --math: #3498db; --history: #e67e22; --ukr: #d4ac0d; --eng: #9b59b6;
  --radius: 18px; --radius-sm: 10px; --radius-xs: 6px;
  --shadow: 0 8px 32px rgba(0,0,0,0.45); --shadow-lg: 0 20px 60px rgba(0,0,0,0.6);
  --font-display: 'Unbounded', sans-serif; --font-body: 'Manrope', sans-serif;
  --tr: 0.3s cubic-bezier(.4,0,.2,1);
}
html { font-family: var(--font-body); background: var(--bg); color: var(--text); scroll-behavior: smooth; }
body { min-height: 100vh; overflow-x: hidden; }
.screen { display: none; min-height: 100vh; animation: fadeIn 0.4s ease; }
.screen.active { display: flex; }
@keyframes fadeIn { from { opacity:0; transform:translateY(10px); } to { opacity:1; transform:none; } }

/* ======== AUTH SCREENS ======== */
.auth-bg {
position:fixed; inset:0; z-index:0;
background:
radial-gradient(ellipse 80% 60% at 50% -10%, rgba(79,110,247,0.22) 0%, transparent 65%),
radial-gradient(ellipse 50% 40% at 85% 85%, rgba(167,139,250,0.14) 0%, transparent 55%),
radial-gradient(ellipse 40% 30% at 10% 70%, rgba(96,165,250,0.08) 0%, transparent 50%);
}
.auth-bg::before {
content: ''; position:absolute; inset:0;
background-image: radial-gradient(circle, rgba(255,255,255,0.035) 1px, transparent 1px);
background-size: 38px 38px;
}
.auth-wrap {
position:relative; z-index:1;
display:flex; align-items:center; justify-content:center;
min-height:100vh; padding:24px;
}
.auth-card {
background: var(--surface); border:1px solid var(--border2);
border-radius:28px; padding:clamp(32px,5vw,52px) clamp(24px,5vw,48px);
width:100%; max-width:460px; box-shadow: var(--shadow-lg);
}
.auth-logo { display:flex; align-items:center; gap:14px; margin-bottom:8px; }
.auth-logo-icon {
width:50px; height:50px; border-radius:14px;
background:linear-gradient(135deg,var(--accent),var(--accent2));
display:flex; align-items:center; justify-content:center;
font-size:22px; box-shadow:0 4px 20px rgba(79,110,247,0.45); flex-shrink:0;
}
.auth-logo h1 {
font-family:var(--font-display); font-size:1.3rem; font-weight:700; line-height:1.2;
background:linear-gradient(135deg,#fff,var(--accent2));
-webkit-background-clip:text; -webkit-text-fill-color:transparent;
}
.auth-logo span { font-size:0.62rem; color:var(--text-muted); font-weight:400; letter-spacing:.05em; display:block; -webkit-text-fill-color:var(--text-muted); }
.auth-subtitle { color:var(--text-muted); font-size:0.88rem; margin-bottom:30px; line-height:1.5; }
.auth-tabs { display:flex; gap:4px; background:var(--surface2); border-radius:var(--radius-sm); padding:4px; margin-bottom:28px; }
.auth-tab {
flex:1; padding:9px; border:none; border-radius:8px; cursor:pointer;
font-family:var(--font-display); font-size:0.75rem; font-weight:700;
color:var(--text-muted); background:transparent; transition:all var(--tr);
}
.auth-tab.active { background:var(--surface3); color:var(--text); box-shadow:0 2px 8px rgba(0,0,0,0.3); }

.form-group { margin-bottom:16px; position:relative; }
.form-group label { display:block; font-size:0.78rem; font-weight:700; color:var(--text-muted); text-transform:uppercase; letter-spacing:.08em; margin-bottom:7px; }
.form-group input {
width:100%; padding:13px 16px; background:var(--surface2);
border:1.5px solid var(--border); border-radius:var(--radius-sm);
color:var(--text); font-family:var(--font-body); font-size:0.95rem;
transition:border-color var(--tr), box-shadow var(--tr); outline:none;
}
.form-group input:focus { border-color:var(--accent); box-shadow:0 0 0 3px rgba(79,110,247,0.15); }

.btn-primary {
width:100%; padding:14px; margin-top:6px;
background:linear-gradient(135deg,var(--accent),var(--accent2));
border:none; border-radius:var(--radius-sm); color:#fff;
font-family:var(--font-display); font-size:0.88rem; font-weight:700;
cursor:pointer; letter-spacing:.02em;
transition:opacity var(--tr), transform var(--tr);
display:flex; align-items:center; justify-content:center; gap:8px;
}
.auth-switch { text-align:center; margin-top:18px; font-size:0.8rem; color:var(--text-muted); }
.auth-switch span { color:var(--accent); cursor:pointer; font-weight:600; }
</style>
</head>
<body>

<div id="auth-screen" class="screen active">
  <div class="auth-bg"></div>
  <div class="auth-wrap">
    <div class="auth-card">
      <div class="auth-logo">
        <div class="auth-logo-icon">🎓</div>
        <h1>НМТ Академія<span>Підготовка до іспитів 2025/2026</span></h1>
      </div>
      <p class="auth-subtitle">Інтерактивний тренажер з чотирьох предметів.</p>

      <div class="auth-tabs">
        <button class="auth-tab active" id="tab-login" onclick="switchAuthTab('login')">Увійти</button>
        <button class="auth-tab" id="tab-register" onclick="switchAuthTab('register')">Реєстрація</button>
      </div>

      <div id="form-register" style="display:block">
        <div class="form-group">
          <label>Логін</label>
          <input type="text" id="reg-username" placeholder="olenak_nmt">
        </div>
        <div class="form-group">
          <label>Пароль</label>
          <input type="password" id="reg-pw" placeholder="••••••••">
        </div>
        <button class="btn-primary" onclick="handleRegister()">Створити акаунт →</button>
      </div>
    </div>
  </div>
</div>

<script>
// Простая функция для теста регистрации
function handleRegister() {
    const user = document.getElementById('reg-username').value;
    const pass = document.getElementById('reg-pw').value;
    
    // Простейшая проверка
    if(user.length < 3) {
        alert("Логін занадто короткий!");
        return;
    }
    
    localStorage.setItem('nmt_user', JSON.stringify({username: user, coins: 0}));
    alert("Реєстрація успішна! Ласкаво просимо, " + user);
    // Тут должен быть переход на Dashboard
}

function switchAuthTab(type) {
    const loginTab = document.getElementById('tab-login');
    const regTab = document.getElementById('tab-register');
    if(type === 'login') {
        loginTab.classList.add('active');
        regTab.classList.remove('active');
    } else {
        regTab.classList.add('active');
        loginTab.classList.remove('active');
    }
}
</script>
</body>
</html>
