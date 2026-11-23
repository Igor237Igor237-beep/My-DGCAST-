<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">
<meta name="theme-color" content="#0A2A5E">
<title>My DGCAST</title>
<link rel="manifest" href="manifest.json">
<link rel="icon" type="image/png" href="logo.png">
<link rel="apple-touch-icon" href="logo.png">
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent;user-select:none}
:root{--navy:#0A2A5E;--gold:#D4AF37;--white:#FFF;--lblue:#8ECBF5;--red:#E60000;--gray:#f8f9fa;--text:#1a1a1a;--muted:#6b7280;--border:#e5e7eb;--ok:#10b981;--warn:#f59e0b;--err:#ef4444;--purple:#8B5CF6;--bg:#f8f9fa;--card:#fff}
body.dark{--bg:#0f172a;--text:#e2e8f0;--card:#1e293b;--border:#334155;--muted:#94a3b8;--gray:#0f172a}
body{font-family:'Poppins',system-ui,sans-serif;background:var(--bg);color:var(--text);min-height:100vh;overflow-x:hidden;transition:all 0.3s}
button{font-family:inherit;cursor:pointer;border:none;background:none;-webkit-tap-highlight-color:transparent}
input,select,textarea{font-family:inherit;font-size:15px;user-select:text}
.hidden{display:none!important}

/* iOS Bubble Effect */
.ios-btn{position:relative;overflow:hidden;transition:transform 0.1s cubic-bezier(0.4,0,0.2,1);transform:translateY(0) scale(1)}
.ios-btn::before{content:'';position:absolute;top:50%;left:50%;width:0;height:0;border-radius:50%;background:rgba(255,255,255,0.5);transform:translate(-50%,-50%);transition:width 0.6s,height 0.6s,opacity 0.6s;opacity:0}
.ios-btn:active{transform:translateY(2px) scale(0.95)}
.ios-btn:active::before{width:300px;height:300px;opacity:1;transition:0s}
.ios-btn.pop{animation:popEffect 0.4s cubic-bezier(0.4,0,0.2,1)}
@keyframes popEffect{0%{transform:scale(1)}50%{transform:scale(0.92)}100%{transform:scale(1)}}

/* Login */
#loginScreen{position:relative;min-height:100vh;background:linear-gradient(135deg,#f5f3ff 0%,#ede9fe 50%,#ddd6fe 100%);overflow:hidden;padding:20px}
#loginScreen::before{content:'';position:absolute;top:-100px;right:-100px;width:500px;height:500px;background:radial-gradient(circle,rgba(139,92,246,0.5) 0%,rgba(167,139,250,0.3) 40%,transparent 70%);filter:blur(80px);z-index:0;animation:pulse 8s ease-in-out infinite}
@keyframes pulse{0%,100%{transform:scale(1);opacity:0.7}50%{transform:scale(1.1);opacity:0.9}}
.login-header{position:relative;z-index:1;display:flex;align-items:center;gap:16px;margin-top:20px;margin-bottom:30px}
.login-logo{width:90px;height:90px;border-radius:50%;box-shadow:0 10px 40px rgba(139,92,246,0.4);flex-shrink:0;border:3px solid var(--gold)}
.school-info{flex:1}
.school-info h1{font-size:20px;font-weight:800;color:var(--navy);line-height:1.2;margin-bottom:4px;text-shadow:0 2px 4px rgba(0,0,0,0.1)}
.school-info p{font-size:13px;color:var(--purple);font-weight:600}
.lang-btns{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:16px;position:relative;z-index:1}
.lang-btn{padding:18px;font-size:16px;font-weight:700;color:#fff;border-radius:16px;box-shadow:0 8px 0 rgba(0,0,0,0.2),0 12px 24px rgba(0,0,0,0.15)}
.lang-btn.en{background:linear-gradient(135deg,#0A2A5E,#1e3a8a);box-shadow:0 8px 0 #051d42,0 12px 24px rgba(10,42,94,0.4)}
.lang-btn.fr{background:linear-gradient(135deg,#D4AF37,#b8941f);color:var(--navy);box-shadow:0 8px 0 #8B6914,0 12px 24px rgba(212,175,55,0.4)}
.role-tabs{display:grid;grid-template-columns:repeat(2,1fr);gap:10px;margin-bottom:24px;position:relative;z-index:1}
.role-tab{padding:14px 10px;font-size:13px;font-weight:600;text-align:center;background:#fff;color:var(--navy);border:2px solid var(--border);border-radius:14px;box-shadow:0 6px 0 var(--border),0 8px 16px rgba(0,0,0,0.08);transition:all 0.15s}
.role-tab.active{background:linear-gradient(135deg,#0A2A5E,#1e3a8a);color:#fff;border-color:var(--navy);box-shadow:0 6px 0 #051d42,0 8px 16px rgba(10,42,94,0.3)}
.login-card{background:#fff;border-radius:24px;padding:24px;box-shadow:0 20px 60px rgba(0,0,0,0.15);position:relative;z-index:1}
.form-group{margin-bottom:14px}
.form-group label{display:block;font-size:13px;font-weight:700;color:var(--navy);margin-bottom:6px}
.form-group input,.form-group select,.form-group textarea{width:100%;padding:14px;border:2px solid var(--border);border-radius:12px;font-size:15px;transition:border-color 0.2s;background:#fafafa}
.form-group input:focus,.form-group select:focus,.form-group textarea:focus{outline:none;border-color:var(--purple);background:#fff}
.btn-primary{width:100%;padding:18px;background:linear-gradient(135deg,#0A2A5E,#1e3a8a);color:#fff;font-size:18px;font-weight:700;border-radius:16px;box-shadow:0 8px 0 #051d42,0 12px 24px rgba(10,42,94,0.4);transition:all 0.1s}
.demo-box{background:#f0f9ff;border:1px solid #bae6fd;border-radius:12px;padding:12px;margin-top:16px;font-size:11px}
.demo-box b{color:var(--navy)}
.footer-copy{color:var(--muted);font-size:11px;text-align:center;margin-top:20px;position:relative;z-index:1}

/* Header */
header{background:linear-gradient(135deg,#0A2A5E,#1e3a8a);color:#fff;padding:14px 16px;display:flex;align-items:center;gap:12px;position:sticky;top:0;z-index:100;box-shadow:0 4px 12px rgba(0,0,0,0.15)}
header .logo{width:40px;height:40px;border-radius:50%;flex-shrink:0}
header h1{font-size:18px;font-weight:800;flex:1}
.lang-switch,.logout-btn,.theme-btn{background:rgba(255,255,255,0.15);color:#fff;padding:6px 12px;border-radius:20px;font-size:12px;font-weight:600;border:2px solid rgba(255,255,255,0.3);box-shadow:0 4px 0 rgba(0,0,0,0.2);margin-right:6px}
.logout-btn{background:rgba(230,0,0,0.2);border-color:rgba(230,0,0,0.3)}

/* Dashboard */
.dashboard{padding:16px;padding-bottom:80px;max-width:900px;margin:0 auto}
.stats{display:grid;grid-template-columns:repeat(2,1fr);gap:12px;margin-bottom:20px}
.stat{background:linear-gradient(135deg,var(--navy),#1e3a8a);color:#fff;padding:16px;border-radius:16px;box-shadow:0 8px 0 #051d42,0 12px 24px rgba(10,42,94,0.3)}
.stat .n{font-size:28px;font-weight:800}
.stat .l{font-size:12px;opacity:0.85}
.stat.gold{background:linear-gradient(135deg,var(--gold),#b8941f);box-shadow:0 8px 0 #8B6914,0 12px 24px rgba(212,175,55,0.3)}
.stat.gold .n{color:var(--navy)}
.stat.red{background:linear-gradient(135deg,#ef4444,#dc2626);box-shadow:0 8px 0 #991b1b,0 12px 24px rgba(239,68,68,0.3)}
.stat.green{background:linear-gradient(135deg,#10b981,#059669);box-shadow:0 8px 0 #047857,0 12px 24px rgba(16,185,129,0.3)}

.child-sel{display:flex;gap:10px;overflow-x:auto;padding:4px 0;margin-bottom:16px}
.child-chip{flex-shrink:0;background:var(--card);border:2px solid var(--border);border-radius:14px;padding:10px 14px;display:flex;align-items:center;gap:10px;cursor:pointer;box-shadow:0 6px 0 var(--border),0 8px 16px rgba(0,0,0,0.08);transition:all 0.15s}
.child-chip.active{border-color:var(--navy);background:#eff6ff;box-shadow:0 6px 0 var(--navy),0 8px 16px rgba(10,42,94,0.2)}
.child-chip .av{width:40px;height:40px;border-radius:50%;background:var(--lblue);display:flex;align-items:center;justify-content:center;font-weight:700;color:var(--navy);font-size:16px}
.child-chip .nm{font-weight:600;font-size:14px}
.child-chip .cl{font-size:11px;color:var(--muted)}

.section-title{font-size:20px;font-weight:800;color:var(--navy);margin-bottom:14px;position:relative;padding-bottom:8px;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:8px}
.section-title::after{content:'';position:absolute;bottom:0;left:0;width:50px;height:4px;background:linear-gradient(90deg,var(--gold),transparent);border-radius:2px}

.grade-card{background:var(--card);border-radius:16px;padding:14px;margin-bottom:10px;box-shadow:0 6px 0 var(--border),0 8px 16px rgba(0,0,0,0.08);display:flex;align-items:center;gap:12px}
.grade-icon{width:46px;height:46px;border-radius:50%;background:linear-gradient(135deg,#D4AF37,#b8941f);display:flex;align-items:center;justify-content:center;font-size:22px;flex-shrink:0;box-shadow:0 6px 0 #8B6914,0 8px 16px rgba(212,175,55,0.3)}
.grade-info{flex:1}
.grade-info h3{font-size:15px;font-weight:600;color:var(--navy);margin-bottom:2px}
.grade-info p{font-size:11px;color:var(--muted)}
.grade-mark{background:linear-gradient(135deg,#D4AF37,#b8941f);color:var(--navy);padding:8px 14px;border-radius:12px;font-size:16px;font-weight:800;box-shadow:0 6px 0 #8B6914,0 8px 16px rgba(212,175,55,0.3)}

.tabs{display:flex;gap:8px;margin-bottom:14px;overflow-x:auto}
.tab{padding:10px 14px;border-radius:12px;font-size:12px;font-weight:600;color:var(--muted);white-space:nowrap;background:var(--card);border:2px solid var(--border);box-shadow:0 6px 0 var(--border),0 8px 16px rgba(0,0,0,0.08);transition:all 0.15s}
.tab.active{background:linear-gradient(135deg,var(--navy),#1e3a8a);color:#fff;border-color:var(--navy);box-shadow:0 6px 0 #051d42,0 8px 16px rgba(10,42,94,0.3)}

table{width:100%;border-collapse:collapse;font-size:12px}
th{background:var(--navy);color:#fff;padding:10px 8px;text-align:left;font-weight:600}
td{padding:10px 8px;border-bottom:1px solid var(--border)}
tr:nth-child(even) td{background:rgba(0,0,0,0.02)}
body.dark tr:nth-child(even) td{background:rgba(255,255,255,0.02)}
.tbl-wrap{overflow-x:auto;border-radius:12px;border:1px solid var(--border);background:var(--card);box-shadow:0 6px 0 var(--border),0 8px 16px rgba(0,0,0,0.08)}

.btn{padding:10px 16px;border-radius:12px;font-size:13px;font-weight:600;display:inline-flex;align-items:center;gap:6px;transition:all 0.1s;box-shadow:0 6px 0 rgba(0,0,0,0.2),0 8px 16px rgba(0,0,0,0.15)}
.btn:active{transform:translateY(6px);box-shadow:0 0 0 rgba(0,0,0,0.2),0 2px 4px rgba(0,0,0,0.15)}
.btn-sm{padding:8px 12px;font-size:11px}
.btn-navy{background:linear-gradient(135deg,#0A2A5E,#1e3a8a);color:#fff;box-shadow:0 6px 0 #051d42,0 8px 16px rgba(10,42,94,0.3)}
.btn-gold{background:linear-gradient(135deg,#D4AF37,#b8941f);color:var(--navy);box-shadow:0 6px 0 #8B6914,0 8px 16px rgba(212,175,55,0.3)}
.btn-red{background:linear-gradient(135deg,#ef4444,#dc2626);color:#fff;box-shadow:0 6px 0 #991b1b,0 8px 16px rgba(239,68,68,0.3)}
.btn-outline{background:transparent;border:2px solid var(--navy);color:var(--navy);box-shadow:0 6px 0 var(--navy),0 8px 16px rgba(10,42,94,0.2)}
.btn-ok{background:linear-gradient(135deg,#10b981,#059669);color:#fff;box-shadow:0 6px 0 #047857,0 8px 16px rgba(16,185,129,0.3)}
.btn-wa{background:linear-gradient(135deg,#25D366,#128C7E);color:#fff;box-shadow:0 6px 0 #0a6b54,0 8px 16px rgba(37,211,102,0.3)}
.btn-block{width:100%;justify-content:center}

.modal-bg{position:fixed;inset:0;background:rgba(0,0,0,0.5);display:flex;align-items:center;justify-content:center;z-index:500;padding:16px;backdrop-filter:blur(4px)}
.modal{background:var(--card);border-radius:24px;padding:24px;width:100%;max-width:500px;max-height:90vh;overflow-y:auto;box-shadow:0 30px 80px rgba(0,0,0,0.4)}
.modal h2{font-size:20px;font-weight:700;color:var(--navy);margin-bottom:16px}
.modal-actions{display:flex;gap:10px;margin-top:16px}
.modal-actions .btn{flex:1}

.sub-banner{background:linear-gradient(135deg,var(--gold),#b8941f);color:var(--navy);padding:16px;border-radius:16px;margin-bottom:14px;box-shadow:0 8px 0 #8B6914,0 12px 24px rgba(212,175,55,0.3)}
.sub-banner h3{font-size:16px;font-weight:700;margin-bottom:4px}
.sub-banner .price{font-size:28px;font-weight:800}
.sub-banner .expiry{font-size:12px;opacity:0.9;margin-top:4px}

.lock-overlay{background:var(--card);backdrop-filter:blur(4px);border-radius:16px;padding:30px 20px;text-align:center;border:2px dashed var(--gold);box-shadow:0 10px 40px rgba(0,0,0,0.1)}
.lock-overlay .icon{font-size:48px;margin-bottom:12px}

.event{border-left:4px solid var(--navy);padding:14px;background:var(--card);border-radius:0 12px 12px 0;margin-bottom:10px;box-shadow:0 6px 0 var(--border),0 8px 16px rgba(0,0,0,0.08)}
.event.urgent{border-color:var(--red)}
.event .cat{font-size:11px;font-weight:700;text-transform:uppercase;color:var(--gold)}
.event .ttl{font-weight:700;font-size:15px;margin:4px 0;color:var(--navy)}
.event .dt{font-size:11px;color:var(--muted)}
.event-img{width:100%;max-height:200px;object-fit:cover;border-radius:10px;margin-top:8px}

.search-bar{display:flex;gap:8px;margin-bottom:14px}
.search-bar input,.search-bar select{flex:1;padding:12px;border:2px solid var(--border);border-radius:12px;font-size:14px;background:var(--card)}

.toast{position:fixed;bottom:100px;left:50%;transform:translateX(-50%);background:var(--navy);color:#fff;padding:14px 24px;border-radius:14px;font-size:14px;font-weight:600;z-index:1000;box-shadow:0 12px 32px rgba(0,0,0,0.3);animation:slideUp 0.3s}
@keyframes slideUp{from{transform:translate(-50%,100px);opacity:0}to{transform:translate(-50%,0);opacity:1}}

#offlineBanner{background:var(--red);color:#fff;text-align:center;padding:10px;font-size:13px;font-weight:600;display:none}

.rank-badge{display:inline-block;padding:4px 10px;border-radius:20px;font-weight:700;font-size:11px;background:linear-gradient(135deg,#D4AF37,#b8941f);color:var(--navy);box-shadow:0 3px 0 #8B6914}
.rank-1{background:linear-gradient(135deg,#FFD700,#FFA500);color:#fff;box-shadow:0 3px 0 #CC8400}
.rank-2{background:linear-gradient(135deg,#C0C0C0,#A0A0A0);color:#fff;box-shadow:0 3px 0 #808080}
.rank-3{background:linear-gradient(135deg,#CD7F32,#A0522D);color:#fff;box-shadow:0 3px 0 #8B4513}

.security-badge{background:linear-gradient(135deg,#10b981,#059669);color:#fff;padding:6px 12px;border-radius:20px;font-size:11px;font-weight:700;display:inline-flex;align-items:center;gap:6px;box-shadow:0 4px 0 #047857,0 6px 12px rgba(16,185,129,0.3)}

/* Badge/Innovation */
.badge-new{background:var(--red);color:#fff;padding:2px 8px;border-radius:10px;font-size:10px;font-weight:700;margin-left:6px;animation:pulse 2s infinite}
.alert-box{background:linear-gradient(135deg,#fef3c7,#fde68a);border:2px solid var(--warn);border-radius:14px;padding:14px;margin-bottom:12px;display:flex;align-items:center;gap:10px}
.alert-box .icon{font-size:24px}
.alert-box.danger{background:linear-gradient(135deg,#fee2e2,#fecaca);border-color:var(--err)}
.alert-box.success{background:linear-gradient(135deg,#d1fae5,#a7f3d0);border-color:var(--ok)}

.whatsapp-contact{background:linear-gradient(135deg,#25D366,#128C7E);color:#fff;padding:12px;border-radius:14px;margin-top:10px;display:flex;align-items:center;gap:10px;box-shadow:0 6px 0 #0a6b54,0 8px 16px rgba(37,211,102,0.3)}
.whatsapp-contact .icon{font-size:28px}
.whatsapp-contact a{color:#fff;font-weight:700;text-decoration:none}

.claim-form{background:var(--card);border:2px solid var(--err);border-radius:16px;padding:16px;margin-top:12px}
.claim-form h4{color:var(--err);margin-bottom:10px}

.dotation-card{background:var(--card);border-radius:14px;padding:14px;margin-bottom:10px;box-shadow:0 6px 0 var(--border),0 8px 16px rgba(0,0,0,0.08);border-left:4px solid var(--purple)}
.dotation-card .status{display:inline-block;padding:4px 10px;border-radius:20px;font-size:11px;font-weight:700;margin-top:6px}
.dotation-card .status.ok{background:var(--ok);color:#fff}
.dotation-card .status.warn{background:var(--warn);color:#fff}
.dotation-card .status.err{background:var(--err);color:#fff}

.seq-input{width:60px;padding:6px;border:2px solid var(--border);border-radius:8px;text-align:center;font-weight:600}

@media(max-width:480px){
  .role-tabs{grid-template-columns:repeat(2,1fr)}
  .stats{grid-template-columns:1fr 1fr}
  header h1{font-size:16px}
  .school-info h1{font-size:17px}
  .login-logo{width:75px;height:75px}
}
</style>
</head>
<body>

<div id="offlineBanner">⚠ <span data-i18n="offline">Pas de connexion, réessayez.</span></div>

<div id="langScreen">
  <div class="login-header">
    <img src="logo.png" class="login-logo" alt="DGCAST" onerror="this.style.background='var(--gold)'">
    <div class="school-info">
      <h1>Divine Grace College<br>of Arts, Science and Technology</h1>
      <p>Garoua, Cameroon 🇨🇲</p>
    </div>
  </div>
  <div class="lang-btns">
    <button class="lang-btn en ios-btn" onclick="setLang('en')">🇬🇧 ENGLISH</button>
    <button class="lang-btn fr ios-btn" onclick="setLang('fr')">🇫🇷 FRANÇAIS</button>
  </div>
</div>

<div id="app" class="hidden">
  <header>
    <img src="logo.png" class="logo" alt="DGCAST" onerror="this.style.background='var(--gold)'">
    <h1 id="headerTitle">My DGCAST</h1>
    <button class="theme-btn ios-btn" onclick="toggleTheme()" id="themeBtn">🌙</button>
    <button class="lang-switch ios-btn" onclick="toggleLang()">EN/FR</button>
    <button class="logout-btn hidden ios-btn" id="logoutBtn" onclick="logout()">🔒</button>
  </header>
  <main id="main"></main>
</div>

<div id="modalRoot"></div>

<script>
/* ==================== SÉCURITÉ RENFORCÉE ==================== */
const SECURITY = {
  hashPassword: (pwd) => {
    const salt = 'DGCAST2025_SALT_SECURE';
    return btoa(unescape(encodeURIComponent(pwd + salt))).split('').reverse().join('');
  },
  sanitize: (str) => {
    if (!str) return '';
    return String(str).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;').replace(/'/g,'&#039;').trim();
  },
  isValidEmail: (email) => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email),
  isValidMatricule: (m) => /^DGCAST\/\d{4}\/\d{3}$/i.test(m),
  isValidCode: (c) => /^\d{4}$/.test(c),
  isValidPhone: (p) => /^6\d{8}$/.test(p.replace(/\s/g,'')),
  loginAttempts: {},
  checkRateLimit: (key) => {
    const now = Date.now();
    if (!SECURITY.loginAttempts[key]) SECURITY.loginAttempts[key] = {count:0, lastAttempt:0};
    const att = SECURITY.loginAttempts[key];
    if (now - att.lastAttempt > 300000) att.count = 0;
    if (att.count >= 5) return false;
    att.count++;
    att.lastAttempt = now;
    return true;
  },
  generateToken: () => Math.random().toString(36).substr(2) + Date.now().toString(36),
  encrypt: (data) => btoa(unescape(encodeURIComponent(JSON.stringify(data)))),
  decrypt: (data) => { try { return JSON.parse(decodeURIComponent(escape(atob(data)))); } catch(e) { return null; } }
};

/* ==================== HEURE CAMEROUN (UTC+1) ==================== */
const CAMEROON_TZ = 'Africa/Douala';
function getCameroonTime() {
  return new Date().toLocaleString('fr-FR', { timeZone: CAMEROON_TZ });
}
function getCameroonTimestamp() {
  return Date.now(); // Utilisé pour calculer les 3 mois
}
const THREE_MONTHS_MS = 90 * 24 * 60 * 60 * 1000; // 90 jours

/* ==================== I18N ==================== */
const I18N = {
  en: {
    chooseLang:"Choose your language", logout:"Logout", login:"Login", email:"Email", password:"Password",
    matricule:"Matricule", secretCode:"Secret Code (4 digits)", parent:"Parent", teacher:"Teacher",
    principal:"Director", superAdmin:"Super Admin", secretary:"Secretary",
    dashboard:"Dashboard", myChildren:"My Children", grades:"Grades", attendance:"Attendance",
    fees:"Fees", events:"Events & News", reportCard:"Report Card",
    myClasses:"My Classes", enterGrades:"Enter Grades", enterAttendance:"Mark Attendance",
    students:"Students", teachers:"Teachers", classes:"Classes", subjects:"Subjects",
    publishGrades:"Publish Grades", subscriptions:"Subscriptions", settings:"Settings",
    add:"Add", edit:"Edit", delete:"Delete", save:"Save", cancel:"Cancel", search:"Search",
    filter:"Filter", all:"All", name:"Name", code:"Code", coeff:"Coefficient", track:"Track",
    classLevel:"Class Level", teacher:"Teacher", general:"General", technical:"Technical", both:"Both",
    firstTerm:"First Term", secondTerm:"Second Term", thirdTerm:"Third Term",
    seq1:"Sequence 1", seq2:"Sequence 2", termAverage:"Term Average", rank:"Rank",
    mark:"Mark", average:"Average", position:"Position", comment:"Comment",
    present:"Present", absent:"Absent", late:"Late",
    paid:"Paid", partial:"Partial", unpaid:"Unpaid",
    publish:"Publish", unpublish:"Unpublish", draft:"Draft", published:"Published",
    downloadPDF:"Download PDF", noData:"No data yet",
    subscriptionExpired:"Your subscription has expired", payToUnlock:"Pay to unlock grades",
    amountToPay:"Amount to pay", children:"children", youHave:"You have",
    momoPay:"MTN MoMo", orangePay:"Orange Money", sendTo:"Send to", reference:"Reference",
    transactionId:"Transaction ID", verify:"Verify", unlock:"Unlock",
    pending:"Pending", active:"Active", expired:"Expired",
    welcome:"Welcome", totalStudents:"Total Students", totalTeachers:"Total Teachers",
    totalClasses:"Total Classes", totalSubjects:"Total Subjects",
    addStudent:"Add Student", addTeacher:"Add Teacher", addClass:"Add Class", addSubject:"Add Subject",
    addEvent:"Add Event/News", studentName:"Student Name", parentPhone:"Parent Phone",
    parentName:"Parent Name", photo:"Photo", generateMatricule:"Auto-generate Matricule",
    secretCodeGen:"Auto-generate Secret Code",
    copySubject:"Duplicate", copyTo:"Copy to class",
    searchFilter:"Search & Filter", byTrack:"By Track", byClass:"By Class", byTeacher:"By Teacher",
    schoolMoMo:"School MoMo Number", saveSettings:"Save Settings",
    backup:"Weekly Backup", exportCSV:"Export All Data (CSV)",
    eventTitle:"Title", eventDesc:"Description", eventDate:"Date", eventCategory:"Category",
    event:"Event", announcement:"Announcement", exam:"Exam", holiday:"Holiday", urgent:"Urgent",
    selectClass:"Select Class", selectSubject:"Select Subject", selectTerm:"Select Term",
    allStudents:"All Students", saveDraft:"Save Draft", publishTerm:"Publish Term",
    locked:"Locked", freeAccess:"Free Access",
    loginFailed:"Invalid credentials", fieldRequired:"This field is required",
    success:"Success", error:"Error", confirmDelete:"Are you sure?",
    form1:"Form 1", form2:"Form 2", form3:"Form 3", form4:"Form 4", form5:"Form 5",
    lowerSixth:"Lower Sixth", upperSixth:"Upper Sixth",
    offline:"No connection, please try again.",
    paymentInstructions:"Payment Instructions",
    step1:"1. Send the exact amount to the number below",
    step2:"2. Use your child's Matricule as reference",
    step3:"3. Enter the Transaction ID here",
    demoParent:"Demo Parent", demoTeacher:"Demo Teacher", demoPrincipal:"Demo Director", demoSuperAdmin:"Demo Super Admin",
    feesStatus:"Fees Status", markFees:"Mark Fees", amount:"Amount",
    terms:"Terms", currentTerm:"Current Term",
    noSubscription:"No active subscription", renewNow:"Renew Now",
    attendanceRate:"Attendance Rate", avgGrade:"Average Grade",
    schoolStamp:"School Stamp", principalSign:"Director Signature",
    reportFor:"Report Card for", academicYear:"Academic Year",
    total:"Total", outOf:"out of", coeffTotal:"Coeff. Total",
    congratulations:"Congratulations", keepItUp:"Keep up the good work!",
    needsImprovement:"Needs improvement",
    selectChild:"Select a child", noChildren:"No children linked",
    momoNumber:"MoMo / Orange Money Number", configure:"Configure",
    numberChildren:"Number of Children", term:"Term", expectedAmount:"Expected Amount",
    status:"Status", actions:"Actions",
    firstName:"First Name", lastName:"Last Name", dob:"Date of Birth", gender:"Gender",
    male:"Male", female:"Female",
    assignTeacher:"Assign Teacher", noTeacher:"No teacher assigned",
    duplicateSuccess:"Subject duplicated successfully",
    publishSuccess:"Grades published successfully",
    unpublishSuccess:"Grades unpublished",
    saveSuccess:"Saved successfully",
    deleteSuccess:"Deleted successfully",
    loginSuccess:"Login successful",
    wrongCredentials:"Wrong credentials. Please try again.",
    fillAll:"Please fill all required fields",
    invalidMatricule:"Invalid matricule format. Use DGCAST/YYYY/XXX",
    invalidCode:"Secret code must be 4 digits",
    noGradesYet:"No grades published yet",
    noEvents:"No events yet",
    viewAll:"View All",
    recentEvents:"Recent Events",
    quickActions:"Quick Actions",
    manageSchool:"Manage School",
    schoolInfo:"School Information",
    academicYear2025:"2025-2026",
    welcomeMsg:"Welcome to My DGCAST",
    parentWelcome:"Parent Dashboard",
    teacherWelcome:"Teacher Dashboard",
    adminWelcome:"Admin Dashboard",
    selectRole:"Select your role",
    backToLogin:"Back to Login",
    autoGenerated:"Auto-generated",
    studentAdded:"Student added successfully",
    credentials:"Credentials",
    copyCredentials:"Copy credentials",
    load:"Load",
    seq1Mark:"Seq. 1",
    seq2Mark:"Seq. 2",
    termAvg:"Avg",
    positionRank:"Rank",
    noStudentsInClass:"No students in this class yet",
    selectClassFirst:"Please select a class first",
    gradesFor:"Grades for",
    classOf:"Class",
    termLabel:"Term",
    quickAdd:"Quick Add",
    onlyNameClass:"Only name and class required",
    autoSort:"Auto-sorted alphabetically",
    securityEnabled:"Security Enabled",
    accessDenied:"Access Denied",
    secretaryLimited:"Secretary can add students, events & manage subscriptions",
    rateLimited:"Too many attempts. Wait 5 minutes.",
    sessionExpired:"Session expired. Please login again.",
    passwordChanged:"Password changed successfully",
    changePassword:"Change Password",
    currentPassword:"Current Password",
    newPassword:"New Password",
    confirmPassword:"Confirm Password",
    passwordMismatch:"Passwords do not match",
    auditLog:"Audit Log",
    userActions:"User Actions",
    lastLogin:"Last Login",
    ip:"IP Address",
    device:"Device",
    restricted:"Restricted Access",
    // NOUVEAUX
    announcements:"Announcements", news:"News", addAnnouncement:"Add Announcement",
    photoEvent:"Event Photo", uploadPhoto:"Upload Photo",
    activateSubscription:"Activate Subscription",
    subscriptionActivated:"Subscription activated",
    expiresOn:"Expires on",
    activatedOn:"Activated on",
    daysLeft:"days left",
    expired:"Expired",
    contactTeacher:"Contact Teacher",
    teacherPhone:"Teacher WhatsApp",
    claimGrade:"Claim/Dispute Grade",
    claimForm:"Grade Claim Form",
    claimSubject:"Subject",
    claimReason:"Reason for claim",
    claimSent:"Claim sent successfully",
    claims:"Claims",
    newClaim:"New Claim",
    resolveClaim:"Resolve",
    claimResolved:"Claim resolved",
    dotation:"Dotation/Equipment",
    manageDotation:"Manage Dotation",
    addDotation:"Add Equipment",
    dotationName:"Equipment Name",
    dotationClass:"Class",
    dotationQty:"Quantity",
    dotationStatus:"Status",
    dotationGood:"Good",
    dotationWorn:"Worn",
    dotationBroken:"Broken",
    dotationAdded:"Equipment added",
    lowAverageAlert:"Low average alert",
    excellentStudent:"Excellent student",
    badge:"Badge",
    darkMode:"Dark Mode",
    lightMode:"Light Mode",
    notifications:"Notifications",
    schoolCalendar:"School Calendar",
    gallery:"Photo Gallery",
    feedback:"Feedback",
    help:"Help",
    about:"About",
    version:"Version",
    cameroonTime:"Cameroon Time",
    autoExpiry:"Auto-expires after 3 months",
    whatsapp:"WhatsApp",
    send:"Send",
    message:"Message",
    parentMsg:"Message to teacher",
    urgentClaim:"Urgent claim",
    normalClaim:"Normal request",
    claimType:"Claim type",
    resolve:"Resolve",
    pending2:"Pending",
    resolved:"Resolved",
    allClaims:"All Claims",
    noClaims:"No claims yet",
    viewGallery:"View Gallery",
    addPhoto:"Add Photo",
    photoCaption:"Caption",
    photoAdded:"Photo added",
    galleryEmpty:"Gallery is empty",
    calendarEmpty:"No events in calendar",
    feedbackSent:"Feedback sent",
    sendFeedback:"Send Feedback",
    feedbackMsg:"Your message",
    aboutSchool:"About the School",
    schoolDesc:"Divine Grace College of Arts, Science and Technology - Excellence in Education since 2020",
    contactSchool:"Contact School",
    schoolPhone:"School Phone",
    schoolEmail:"School Email",
    schoolAddress:"Address",
    madeWith:"Made with ❤️ in Garoua"
  },
  fr: {
    chooseLang:"Choisissez votre langue", logout:"Déconnexion", login:"Connexion", email:"Email", password:"Mot de passe",
    matricule:"Matricule", secretCode:"Code Secret (4 chiffres)", parent:"Parent", teacher:"Enseignant",
    principal:"Directeur", superAdmin:"Super Admin", secretary:"Secrétaire",
    dashboard:"Tableau de Bord", myChildren:"Mes Enfants", grades:"Notes", attendance:"Présence",
    fees:"Frais", events:"Événements & Actualités", reportCard:"Bulletin",
    myClasses:"Mes Classes", enterGrades:"Saisir les Notes", enterAttendance:"Marquer la Présence",
    students:"Élèves", teachers:"Enseignants", classes:"Classes", subjects:"Matières",
    publishGrades:"Publier les Notes", subscriptions:"Abonnements", settings:"Paramètres",
    add:"Ajouter", edit:"Modifier", delete:"Supprimer", save:"Enregistrer", cancel:"Annuler", search:"Rechercher",
    filter:"Filtrer", all:"Tous", name:"Nom", code:"Code", coeff:"Coefficient", track:"Filière",
    classLevel:"Niveau", teacher:"Enseignant", general:"Général", technical:"Technique", both:"Les deux",
    firstTerm:"1er Trimestre", secondTerm:"2ème Trimestre", thirdTerm:"3ème Trimestre",
    seq1:"Séquence 1", seq2:"Séquence 2", termAverage:"Moyenne Trimestrielle", rank:"Rang",
    mark:"Note", average:"Moyenne", position:"Position", comment:"Commentaire",
    present:"Présent", absent:"Absent", late:"En retard",
    paid:"Payé", partial:"Partiel", unpaid:"Impayé",
    publish:"Publier", unpublish:"Dépublier", draft:"Brouillon", published:"Publié",
    downloadPDF:"Télécharger PDF", noData:"Aucune donnée",
    subscriptionExpired:"Votre abonnement a expiré", payToUnlock:"Payez pour débloquer les notes",
    amountToPay:"Montant à payer", children:"enfants", youHave:"Vous avez",
    momoPay:"MTN MoMo", orangePay:"Orange Money", sendTo:"Envoyer à", reference:"Référence",
    transactionId:"ID Transaction", verify:"Vérifier", unlock:"Débloquer",
    pending:"En attente", active:"Actif", expired:"Expiré",
    welcome:"Bienvenue", totalStudents:"Total Élèves", totalTeachers:"Total Enseignants",
    totalClasses:"Total Classes", totalSubjects:"Total Matières",
    addStudent:"Ajouter Élève", addTeacher:"Ajouter Enseignant", addClass:"Ajouter Classe", addSubject:"Ajouter Matière",
    addEvent:"Ajouter Événement/Actualité", studentName:"Nom de l'Élève", parentPhone:"Téléphone Parent",
    parentName:"Nom du Parent", photo:"Photo", generateMatricule:"Générer Matricule",
    secretCodeGen:"Générer Code Secret",
    copySubject:"Dupliquer", copyTo:"Copier vers la classe",
    searchFilter:"Recherche & Filtres", byTrack:"Par Filière", byClass:"Par Classe", byTeacher:"Par Enseignant",
    schoolMoMo:"Numéro MoMo de l'École", saveSettings:"Enregistrer",
    backup:"Sauvegarde Hebdo", exportCSV:"Exporter Toutes les Données (CSV)",
    eventTitle:"Titre", eventDesc:"Description", eventDate:"Date", eventCategory:"Catégorie",
    event:"Événement", announcement:"Annonce", exam:"Examen", holiday:"Vacances", urgent:"Urgent",
    selectClass:"Sélectionner Classe", selectSubject:"Sélectionner Matière", selectTerm:"Sélectionner Trimestre",
    allStudents:"Tous les Élèves", saveDraft:"Enregistrer Brouillon", publishTerm:"Publier Trimestre",
    locked:"Verrouillé", freeAccess:"Accès Gratuit",
    loginFailed:"Identifiants invalides", fieldRequired:"Ce champ est requis",
    success:"Succès", error:"Erreur", confirmDelete:"Êtes-vous sûr ?",
    form1:"6ème", form2:"5ème", form3:"4ème", form4:"3ème", form5:"2nde",
    lowerSixth:"1ère", upperSixth:"Terminale",
    offline:"Pas de connexion, réessayez.",
    paymentInstructions:"Instructions de Paiement",
    step1:"1. Envoyez le montant exact au numéro ci-dessous",
    step2:"2. Utilisez le Matricule de votre enfant comme référence",
    step3:"3. Entrez l'ID de Transaction ici",
    demoParent:"Démo Parent", demoTeacher:"Démo Enseignant", demoPrincipal:"Démo Directeur", demoSuperAdmin:"Démo Super Admin",
    feesStatus:"Statut Frais", markFees:"Marquer Frais", amount:"Montant",
    terms:"Trimestres", currentTerm:"Trimestre en Cours",
    noSubscription:"Aucun abonnement actif", renewNow:"Renouveler",
    attendanceRate:"Taux de Présence", avgGrade:"Moyenne Générale",
    schoolStamp:"Cachet de l'École", principalSign:"Signature du Directeur",
    reportFor:"Bulletin de", academicYear:"Année Scolaire",
    total:"Total", outOf:"sur", coeffTotal:"Coeff. Total",
    congratulations:"Félicitations", keepItUp:"Continuez ainsi !",
    needsImprovement:"Doit s'améliorer",
    selectChild:"Sélectionnez un enfant", noChildren:"Aucun enfant lié",
    momoNumber:"Numéro MoMo / Orange Money", configure:"Configurer",
    numberChildren:"Nombre d'Enfants", term:"Trimestre", expectedAmount:"Montant Attendu",
    status:"Statut", actions:"Actions",
    firstName:"Prénom", lastName:"Nom", dob:"Date de Naissance", gender:"Genre",
    male:"Masculin", female:"Féminin",
    assignTeacher:"Assigner Enseignant", noTeacher:"Aucun enseignant assigné",
    duplicateSuccess:"Matière dupliquée avec succès",
    publishSuccess:"Notes publiées avec succès",
    unpublishSuccess:"Notes dépubliées",
    saveSuccess:"Enregistré avec succès",
    deleteSuccess:"Supprimé avec succès",
    loginSuccess:"Connexion réussie",
    wrongCredentials:"Mauvais identifiants. Réessayez.",
    fillAll:"Veuillez remplir tous les champs requis",
    invalidMatricule:"Format matricule invalide. Utilisez DGCAST/AAAA/XXX",
    invalidCode:"Le code secret doit avoir 4 chiffres",
    noGradesYet:"Aucune note publiée",
    noEvents:"Aucun événement",
    viewAll:"Voir Tout",
    recentEvents:"Événements Récents",
    quickActions:"Actions Rapides",
    manageSchool:"Gérer l'École",
    schoolInfo:"Informations École",
    academicYear2025:"2025-2026",
    welcomeMsg:"Bienvenue sur My DGCAST",
    parentWelcome:"Tableau de Bord Parent",
    teacherWelcome:"Tableau de Bord Enseignant",
    adminWelcome:"Tableau de Bord Admin",
    selectRole:"Sélectionnez votre rôle",
    backToLogin:"Retour à la Connexion",
    autoGenerated:"Généré automatiquement",
    studentAdded:"Élève ajouté avec succès",
    credentials:"Identifiants",
    copyCredentials:"Copier les identifiants",
    load:"Charger",
    seq1Mark:"Séq. 1",
    seq2Mark:"Séq. 2",
    termAvg:"Moy",
    positionRank:"Rang",
    noStudentsInClass:"Aucun élève dans cette classe",
    selectClassFirst:"Veuillez sélectionner une classe",
    gradesFor:"Notes de",
    classOf:"Classe",
    termLabel:"Trimestre",
    quickAdd:"Ajout Rapide",
    onlyNameClass:"Seulement nom et classe requis",
    autoSort:"Tri alphabétique automatique",
    securityEnabled:"Sécurité Activée",
    accessDenied:"Accès Refusé",
    secretaryLimited:"La secrétaire peut ajouter élèves, événements et gérer abonnements",
    rateLimited:"Trop de tentatives. Attendez 5 minutes.",
    sessionExpired:"Session expirée. Veuillez vous reconnecter.",
    passwordChanged:"Mot de passe modifié avec succès",
    changePassword:"Changer le Mot de Passe",
    currentPassword:"Mot de Passe Actuel",
    newPassword:"Nouveau Mot de Passe",
    confirmPassword:"Confirmer le Mot de Passe",
    passwordMismatch:"Les mots de passe ne correspondent pas",
    auditLog:"Journal d'Audit",
    userActions:"Actions Utilisateur",
    lastLogin:"Dernière Connexion",
    ip:"Adresse IP",
    device:"Appareil",
    restricted:"Accès Restreint",
    // NOUVEAUX
    announcements:"Annonces", news:"Actualités", addAnnouncement:"Ajouter Annonce",
    photoEvent:"Photo de l'événement", uploadPhoto:"Télécharger Photo",
    activateSubscription:"Activer l'abonnement",
    subscriptionActivated:"Abonnement activé",
    expiresOn:"Expire le",
    activatedOn:"Activé le",
    daysLeft:"jours restants",
    expired:"Expiré",
    contactTeacher:"Contacter l'enseignant",
    teacherPhone:"WhatsApp Enseignant",
    claimGrade:"Réclamer/Contester une note",
    claimForm:"Formulaire de réclamation",
    claimSubject:"Matière",
    claimReason:"Raison de la réclamation",
    claimSent:"Réclamation envoyée avec succès",
    claims:"Réclamations",
    newClaim:"Nouvelle réclamation",
    resolveClaim:"Résoudre",
    claimResolved:"Réclamation résolue",
    dotation:"Dotation/Équipement",
    manageDotation:"Gérer la Dotation",
    addDotation:"Ajouter Équipement",
    dotationName:"Nom de l'équipement",
    dotationClass:"Classe",
    dotationQty:"Quantité",
    dotationStatus:"État",
    dotationGood:"Bon",
    dotationWorn:"Usé",
    dotationBroken:"Cassé",
    dotationAdded:"Équipement ajouté",
    lowAverageAlert:"Alerte moyenne faible",
    excellentStudent:"Excellent élève",
    badge:"Badge",
    darkMode:"Mode Sombre",
    lightMode:"Mode Clair",
    notifications:"Notifications",
    schoolCalendar:"Calendrier Scolaire",
    gallery:"Galerie Photos",
    feedback:"Commentaires",
    help:"Aide",
    about:"À propos",
    version:"Version",
    cameroonTime:"Heure Cameroun",
    autoExpiry:"Expire automatiquement après 3 mois",
    whatsapp:"WhatsApp",
    send:"Envoyer",
    message:"Message",
    parentMsg:"Message à l'enseignant",
    urgentClaim:"Réclamation urgente",
    normalClaim:"Demande normale",
    claimType:"Type de réclamation",
    resolve:"Résoudre",
    pending2:"En attente",
    resolved:"Résolu",
    allClaims:"Toutes les réclamations",
    noClaims:"Aucune réclamation",
    viewGallery:"Voir la galerie",
    addPhoto:"Ajouter Photo",
    photoCaption:"Légende",
    photoAdded:"Photo ajoutée",
    galleryEmpty:"Galerie vide",
    calendarEmpty:"Aucun événement dans le calendrier",
    feedbackSent:"Commentaire envoyé",
    sendFeedback:"Envoyer un commentaire",
    feedbackMsg:"Votre message",
    aboutSchool:"À propos de l'école",
    schoolDesc:"Divine Grace College of Arts, Science and Technology - L'excellence éducative depuis 2020",
    contactSchool:"Contacter l'école",
    schoolPhone:"Téléphone École",
    schoolEmail:"Email École",
    schoolAddress:"Adresse",
    madeWith:"Fait avec ❤️ à Garoua"
  }
};

let currentLang = localStorage.getItem('dgcast_lang') || 'fr';
let darkMode = localStorage.getItem('dgcast_dark') === 'true';
if (darkMode) document.body.classList.add('dark');

function t(key){ return I18N[currentLang][key] || I18N.en[key] || key; }
function setLang(l){ currentLang=l; localStorage.setItem('dgcast_lang',l); document.getElementById('langScreen').classList.add('hidden'); document.getElementById('app').classList.remove('hidden'); applyI18n(); render(); }
function toggleLang(){ setLang(currentLang==='en'?'fr':'en'); }
function applyI18n(){ document.querySelectorAll('[data-i18n]').forEach(el=>{ el.textContent=t(el.dataset.i18n); }); }
function toggleTheme(){
  darkMode = !darkMode;
  document.body.classList.toggle('dark', darkMode);
  localStorage.setItem('dgcast_dark', darkMode);
  document.getElementById('themeBtn').textContent = darkMode ? '☀️' : '🌙';
  render();
}

/* ==================== BASE DE DONNÉES ==================== */
const DB_KEY = 'dgcast_db_v3';
const CLASSES = ['Form 1 General','Form 2 General','Form 3 General','Form 4 General','Form 5 General','Lower Sixth General','Upper Sixth General','Form 1 Technical','Form 2 Technical','Form 3 Technical','Form 4 Technical','Form 5 Technical','Lower Sixth Technical','Upper Sixth Technical'];

function loadDB(){
  try{ const d=localStorage.getItem(DB_KEY); if(d) return SECURITY.decrypt(d) || JSON.parse(d); }catch(e){}
  return seedDemo();
}
function saveDB(){ localStorage.setItem(DB_KEY, SECURITY.encrypt(db)); }
let db = loadDB();

function seedDemo(){
  const d = {
    students:[
      {id:'s1',firstName:'Amina',lastName:'Bello',matricule:'DGCAST/2025/001',secretCode:'1234',classLevel:'Form 4 General',track:'General',parentPhone:'690000001',parentName:'Mr. Bello',gender:'female',dob:'2010-05-15',photo:null,createdAt:new Date().toISOString()},
      {id:'s2',firstName:'Yusuf',lastName:'Bello',matricule:'DGCAST/2025/002',secretCode:'1234',classLevel:'Form 2 General',track:'General',parentPhone:'690000001',parentName:'Mr. Bello',gender:'male',dob:'2013-08-22',photo:null,createdAt:new Date().toISOString()},
      {id:'s3',firstName:'Fatima',lastName:'Ibrahim',matricule:'DGCAST/2025/003',secretCode:'1234',classLevel:'Form 4 General',track:'General',parentPhone:'690000002',parentName:'Mrs. Ibrahim',gender:'female',dob:'2010-03-10',photo:null,createdAt:new Date().toISOString()}
    ],
    parents:[
      {id:'p1',name:'Mr. Bello',phone:'690000001',children:['s1','s2']},
      {id:'p2',name:'Mrs. Ibrahim',phone:'690000002',children:['s3']}
    ],
    teachers:[
      {id:'t1',name:'Mr. John Smith',email:'teacher@dgcast.cm',password:SECURITY.hashPassword('teacher123'),track:'General',classes:['Form 4 General'],subjects:['Mathematics'],whatsapp:'670123456',createdAt:new Date().toISOString()}
    ],
    admins:[
      {id:'a1',name:'Dr. Director',email:'director@dgcast.cm',password:SECURITY.hashPassword('director123'),role:'principal',createdAt:new Date().toISOString()},
      {id:'a2',name:'Super Admin',email:'admin@dgcast.cm',password:SECURITY.hashPassword('admin123'),role:'superadmin',createdAt:new Date().toISOString()},
      {id:'a3',name:'Ms. Secretary',email:'secretary@dgcast.cm',password:SECURITY.hashPassword('secretary123'),role:'secretary',createdAt:new Date().toISOString()}
    ],
    subjects:[
      {id:'sub1',name:'Mathematics',code:'MAT',coeff:4,track:'General',classLevel:'Form 4 General',teacherId:'t1',createdAt:new Date().toISOString()}
    ],
    grades:[
      {id:'g1',studentId:'s1',subjectId:'sub1',term:'first',seq1:14,seq2:16,comment:'Good work',published:true,createdAt:new Date().toISOString()}
    ],
    attendance:[],
    subscriptions:[
      {id:'sub_p1',parentId:'p1',term:'first',amount:1000,status:'active',transactionId:'TXN001',date:'2025-09-01',activatedAt:Date.now(),expiresAt:Date.now()+THREE_MONTHS_MS}
    ],
    events:[
      {id:'e1',title:'Inter-House Sports Competition',description:'Annual sports competition',date:'2025-12-15',category:'event',photo:null,createdAt:new Date().toISOString()}
    ],
    claims:[],
    dotations:[
      {id:'d1',name:'Projector',classLevel:'Form 4 General',quantity:1,status:'good',createdAt:new Date().toISOString()}
    ],
    gallery:[],
    feedback:[],
    settings:{momoNumber:'670000000',schoolName:'Divine Grace College',academicYear:'2025-2026',schoolPhone:'670000000',schoolEmail:'info@dgcast.cm',schoolAddress:'Garoua, Cameroon'},
    auditLog:[]
  };
  localStorage.setItem(DB_KEY, SECURITY.encrypt(d));
  return d;
}

/* ==================== AUTH ==================== */
let currentUser = null, currentRole = null, selectedChildId = null, sessionToken = null;

function login(role, creds){
  const loginKey = creds.email || creds.matricule || 'unknown';
  if (!SECURITY.checkRateLimit(loginKey)) { toast(t('rateLimited')); return false; }
  
  if(role==='parent'){
    const {matricule, code} = creds;
    if(!SECURITY.isValidMatricule(matricule)){ toast(t('invalidMatricule')); return false; }
    if(!SECURITY.isValidCode(code)){ toast(t('invalidCode')); return false; }
    const student = db.students.find(s=>s.matricule.toUpperCase()===matricule.toUpperCase() && s.secretCode===code);
    if(!student){ toast(t('wrongCredentials')); return false; }
    const parent = db.parents.find(p=>p.phone===student.parentPhone);
    currentUser = parent; currentRole = 'parent';
    selectedChildId = parent.children[0];
  } else if(role==='teacher'){
    const {email, password} = creds;
    if(!SECURITY.isValidEmail(email)){ toast('Invalid email'); return false; }
    const hashedPwd = SECURITY.hashPassword(password);
    const teacher = db.teachers.find(t=>t.email.toLowerCase()===email.toLowerCase() && t.password===hashedPwd);
    if(!teacher){ toast(t('wrongCredentials')); return false; }
    currentUser = teacher; currentRole = 'teacher';
  } else if(role==='principal' || role==='superadmin' || role==='secretary'){
    const {email, password} = creds;
    if(!SECURITY.isValidEmail(email)){ toast('Invalid email'); return false; }
    const hashedPwd = SECURITY.hashPassword(password);
    const admin = db.admins.find(a=>a.email.toLowerCase()===email.toLowerCase() && a.password===hashedPwd && a.role===role);
    if(!admin){ toast(t('wrongCredentials')); return false; }
    currentUser = admin; currentRole = role;
    db.auditLog.push({action:'login',userId:admin.id,role:admin.role,timestamp:new Date().toISOString(),device:navigator.userAgent});
    saveDB();
  }
  
  sessionToken = SECURITY.generateToken();
  localStorage.setItem('dgcast_session', SECURITY.encrypt({role:currentRole, userId:currentUser.id, token:sessionToken, timestamp:Date.now()}));
  toast(t('loginSuccess'));
  render();
  return true;
}

function logout(){
  if (currentUser && currentRole !== 'parent') {
    db.auditLog.push({action:'logout',userId:currentUser.id,role:currentRole,timestamp:new Date().toISOString()});
    saveDB();
  }
  currentUser = null; currentRole = null; selectedChildId = null; sessionToken = null;
  localStorage.removeItem('dgcast_session');
  render();
}

function restoreSession(){
  try{
    const s = SECURITY.decrypt(localStorage.getItem('dgcast_session'));
    if(!s || !s.token) return false;
    if (Date.now() - s.timestamp > 86400000) { localStorage.removeItem('dgcast_session'); toast(t('sessionExpired')); return false; }
    if(s.role==='parent'){ currentUser = db.parents.find(p=>p.id===s.userId); currentRole='parent'; selectedChildId=currentUser?.children?.[0]; }
    else if(s.role==='teacher'){ currentUser = db.teachers.find(t=>t.id===s.userId); currentRole='teacher'; }
    else if(['principal','superadmin','secretary'].includes(s.role)){ currentUser = db.admins.find(a=>a.id===s.userId); currentRole=s.role; }
    return !!currentUser;
  }catch(e){ return false; }
}

/* ==================== HELPERS ==================== */
function uid(){ return 'id_'+Math.random().toString(36).substr(2,9)+Date.now().toString(36); }
function genMatricule(){
  const year = new Date().getFullYear();
  const count = db.students.filter(s=>s.matricule.includes('/'+year+'/')).length + 1;
  return `DGCAST/${year}/${String(count).padStart(3,'0')}`;
}
function genSecretCode(){ return String(Math.floor(1000+Math.random()*9000)); }
function getSubscriptionPrice(numChildren){
  if(numChildren<=1) return 600;
  if(numChildren===2) return 1000;
  return 1200;
}
function getCurrentTerm(){
  const m = new Date().getMonth()+1;
  if(m>=9 && m<=12) return 'first';
  if(m>=1 && m<=3) return 'second';
  return 'third';
}
function toast(msg){
  const el = document.createElement('div');
  el.className='toast'; el.textContent=msg;
  document.body.appendChild(el);
  setTimeout(()=>el.remove(), 3000);
}
function modal(html){ document.getElementById('modalRoot').innerHTML = `<div class="modal-bg" onclick="if(event.target===this)closeModal()"><div class="modal">${html}</div></div>`; }
function closeModal(){ document.getElementById('modalRoot').innerHTML=''; }
function sortStudents(students){
  return [...students].sort((a,b) => (a.lastName+' '+a.firstName).toLowerCase().localeCompare((b.lastName+' '+b.firstName).toLowerCase()));
}
function formatDateCameroon(ts){
  return new Date(ts).toLocaleString('fr-FR', { timeZone: CAMEROON_TZ, dateStyle:'medium', timeStyle:'short' });
}
function daysLeft(expiresAt){
  const diff = expiresAt - Date.now();
  return Math.max(0, Math.ceil(diff / (1000*60*60*24)));
}
function checkSubscriptionExpiry(){
  // Vérifie et expire automatiquement les abonnements dépassés
  db.subscriptions.forEach(s => {
    if (s.status === 'active' && s.expiresAt && Date.now() > s.expiresAt) {
      s.status = 'expired';
    }
  });
  saveDB();
}

/* ==================== RENDER ==================== */
function render(){
  applyI18n();
  checkSubscriptionExpiry();
  const main = document.getElementById('main');
  const logoutBtn = document.getElementById('logoutBtn');
  document.getElementById('themeBtn').textContent = darkMode ? '☀️' : '🌙';
  
  if(!currentUser){
    logoutBtn.classList.add('hidden');
    main.innerHTML = renderLogin();
    return;
  }
  logoutBtn.classList.remove('hidden');
  
  if(currentRole==='parent') main.innerHTML = renderParentDashboard();
  else if(currentRole==='teacher') main.innerHTML = renderTeacherDashboard();
  else if(currentRole==='secretary') main.innerHTML = renderSecretaryDashboard();
  else main.innerHTML = renderAdminDashboard();
}

/* ==================== LOGIN ==================== */
let loginRole = 'parent';
function renderLogin(){
  return `
  <div id="loginScreen">
    <div class="login-header">
      <img src="logo.png" class="login-logo" alt="DGCAST" onerror="this.style.background='var(--gold)'">
      <div class="school-info">
        <h1>Divine Grace College<br>of Arts, Science and Technology</h1>
        <p>Garoua, Cameroon 🇨🇲</p>
      </div>
    </div>
    <div class="lang-btns">
      <button class="lang-btn en ios-btn" onclick="setLang('en')">🇬🇧 ENGLISH</button>
      <button class="lang-btn fr ios-btn" onclick="setLang('fr')">🇫🇷 FRANÇAIS</button>
    </div>
    <div class="role-tabs">
      <button class="role-tab ios-btn ${loginRole==='parent'?'active':''}" onclick="loginRole='parent';render()">👨‍👩‍👧 ${t('parent')}</button>
      <button class="role-tab ios-btn ${loginRole==='teacher'?'active':''}" onclick="loginRole='teacher';render()">👨‍🏫 ${t('teacher')}</button>
      <button class="role-tab ios-btn ${loginRole==='principal'?'active':''}" onclick="loginRole='principal';render()">🎓 ${t('principal')}</button>
      <button class="role-tab ios-btn ${loginRole==='superadmin'?'active':''}" onclick="loginRole='superadmin';render()">🔐 ${t('superAdmin')}</button>
      <button class="role-tab ios-btn ${loginRole==='secretary'?'active':''}" onclick="loginRole='secretary';render()">📋 ${t('secretary')}</button>
    </div>
    <div class="login-card">
      ${loginRole==='parent' ? `
        <div class="form-group"><label>${t('matricule')}</label><input id="loginMat" placeholder="DGCAST/YYYY/XXX" maxlength="17"></div>
        <div class="form-group"><label>${t('secretCode')}</label><input id="loginCode" type="password" maxlength="4" placeholder="••••" inputmode="numeric"></div>
      ` : `
        <div class="form-group"><label>${t('email')}</label><input id="loginEmail" type="email" autocomplete="email"></div>
        <div class="form-group"><label>${t('password')}</label><input id="loginPass" type="password" autocomplete="current-password"></div>
      `}
      <button class="btn-primary ios-btn" onclick="doLogin()">🔓 ${t('login')}</button>
      <div class="demo-box">
        <b>${t('demoParent')}:</b> DGCAST/2025/001 / 1234<br>
        <b>${t('demoTeacher')}:</b> teacher@dgcast.cm / teacher123<br>
        <b>${t('demoPrincipal')}:</b> director@dgcast.cm / director123<br>
        <b>${t('demoSuperAdmin')}:</b> admin@dgcast.cm / admin123<br>
        <b>${t('secretary')}:</b> secretary@dgcast.cm / secretary123
      </div>
    </div>
    <div class="footer-copy">© 2025 Divine Grace College - Garoua, Cameroon<br><span class="security-badge">🔒 ${t('securityEnabled')} | 🕐 ${t('cameroonTime')}: ${getCameroonTime()}</span></div>
  </div>`;
}

function doLogin(){
  if(loginRole==='parent'){
    const mat = SECURITY.sanitize(document.getElementById('loginMat').value.trim());
    const code = SECURITY.sanitize(document.getElementById('loginCode').value.trim());
    if(!mat || !code){ toast(t('fillAll')); return; }
    login('parent', {matricule:mat, code});
  } else {
    const email = SECURITY.sanitize(document.getElementById('loginEmail').value.trim().toLowerCase());
    const pass = document.getElementById('loginPass').value;
    if(!email || !pass){ toast(t('fillAll')); return; }
    login(loginRole, {email, password:pass});
  }
}

/* ==================== PARENT DASHBOARD ==================== */
let parentTab = 'grades';

function renderParentDashboard(){
  const parent = currentUser;
  const children = sortStudents(db.students.filter(s=>parent.children.includes(s.id)));
  const selectedChild = db.students.find(s=>s.id===selectedChildId) || children[0];
  if(selectedChild) selectedChildId = selectedChild.id;
  
  const currentTerm = getCurrentTerm();
  const sub = db.subscriptions.find(s=>s.parentId===parent.id && s.term===currentTerm && s.status==='active');
  const hasSubscription = !!sub;
  const price = getSubscriptionPrice(children.length);
  const days = sub ? daysLeft(sub.expiresAt) : 0;
  
  let html = `<div class="dashboard">`;
  
  // Child selector
  html += `<div class="child-sel">`;
  children.forEach(c=>{
    const initials = (c.firstName[0]+c.lastName[0]).toUpperCase();
    html += `<div class="child-chip ios-btn ${c.id===selectedChildId?'active':''}" onclick="selectedChildId='${c.id}';render()">
      <div class="av">${initials}</div>
      <div><div class="nm">${SECURITY.sanitize(c.firstName)} ${SECURITY.sanitize(c.lastName)}</div><div class="cl">${c.classLevel}</div></div>
    </div>`;
  });
  html += `</div>`;
  
  // Alerts innovantes
  if (hasSubscription && days <= 7) {
    html += `<div class="alert-box"><div class="icon">⚠️</div><div><b>${t('subscriptionExpired')}</b><br><small>${days} ${t('daysLeft')} - ${t('renewNow')}</small></div></div>`;
  }
  
  // Stats
  html += `<div class="stats">
    <div class="stat"><div class="n">${children.length}</div><div class="l">${t('children')}</div></div>
    <div class="stat ${hasSubscription?'green':'red'}"><div class="n">${hasSubscription?days+'j':'✗'}</div><div class="l">${t('subscriptions')}</div></div>
  </div>`;
  
  // Subscription banner
  if(!hasSubscription){
    html += `<div class="sub-banner">
      <h3>⚠ ${t('subscriptionExpired')}</h3>
      <div>${t('youHave')} ${children.length} ${t('children')} → ${t('amountToPay')}: <span class="price">${price} FCFA</span></div>
      <div class="expiry">🕐 ${t('autoExpiry')}</div>
      <button class="btn btn-navy btn-sm ios-btn" style="margin-top:10px" onclick="showPaymentModal()">${t('renewNow')}</button>
    </div>`;
  } else {
    html += `<div class="sub-banner" style="background:linear-gradient(135deg,#10b981,#059669);color:#fff">
      <h3>✅ ${t('active')}</h3>
      <div>${t('expiresOn')}: ${formatDateCameroon(sub.expiresAt)}</div>
      <div class="expiry">${days} ${t('daysLeft')}</div>
    </div>`;
  }
  
  // Tabs
  html += `<div class="tabs">
    <button class="tab ios-btn ${parentTab==='grades'?'active':''}" onclick="parentTab='grades';render()">📊 ${t('grades')}</button>
    <button class="tab ios-btn ${parentTab==='attendance'?'active':''}" onclick="parentTab='attendance';render()">📅 ${t('attendance')}</button>
    <button class="tab ios-btn ${parentTab==='events'?'active':''}" onclick="parentTab='events';render()">📢 ${t('events')}</button>
    <button class="tab ios-btn ${parentTab==='claims'?'active':''}" onclick="parentTab='claims';render()">⚠️ ${t('claims')}<span class="badge-new">NEW</span></button>
    <button class="tab ios-btn ${parentTab==='gallery'?'active':''}" onclick="parentTab='gallery';render()">📷 ${t('gallery')}</button>
    <button class="tab ios-btn ${parentTab==='report'?'active':''}" onclick="parentTab='report';render()">📄 ${t('reportCard')}</button>
    <button class="tab ios-btn ${parentTab==='about'?'active':''}" onclick="parentTab='about';render()">ℹ️ ${t('about')}</button>
  </div>`;
  
  if(parentTab==='grades'){
    if(!hasSubscription){
      html += `<div class="lock-overlay"><div class="icon">🔒</div><h3>${t('locked')}</h3><p>${t('youHave')} ${children.length} ${t('children')}. ${t('payToUnlock')}: ${price} FCFA</p><button class="btn btn-gold ios-btn" style="margin-top:12px" onclick="showPaymentModal()">${t('renewNow')}</button></div>`;
    } else {
      const grades = db.grades.filter(g=>g.studentId===selectedChildId && g.term===currentTerm && g.published);
      html += `<div class="section-title">📊 ${t('grades')} - ${SECURITY.sanitize(selectedChild.firstName)} ${SECURITY.sanitize(selectedChild.lastName)}</div>`;
      if(grades.length===0){
        html += `<div class="grade-card"><p style="color:var(--muted);text-align:center;padding:20px;width:100%">${t('noGradesYet')}</p></div>`;
      } else {
        grades.forEach(g=>{
          const sub = db.subjects.find(s=>s.id===g.subjectId);
          if(!sub) return;
          const avg = ((g.seq1||0) + (g.seq2||0)) / 2;
          const subjectGrades = db.grades.filter(grade=>{
            const student = db.students.find(s=>s.id===grade.studentId);
            return grade.subjectId===g.subjectId && grade.term===currentTerm && grade.published && student && student.classLevel===selectedChild.classLevel;
          }).map(grade=>({studentId:grade.studentId,avg:((grade.seq1||0)+(grade.seq2||0))/2})).sort((a,b)=>b.avg-a.avg);
          const rank = subjectGrades.findIndex(x=>x.studentId===g.studentId) + 1;
          
          // Alerte moyenne faible
          if (avg < 10) {
            html += `<div class="alert-box danger"><div class="icon">🚨</div><div><b>${t('lowAverageAlert')}</b>: ${SECURITY.sanitize(sub.name)} - ${avg.toFixed(1)}/20</div></div>`;
          }
          if (avg >= 16) {
            html += `<div class="alert-box success"><div class="icon">🏆</div><div><b>${t('excellentStudent')}</b>: ${SECURITY.sanitize(sub.name)} - ${avg.toFixed(1)}/20</div></div>`;
          }
          
          html += `<div class="grade-card">
            <div class="grade-icon">📚</div>
            <div class="grade-info">
              <h3>${SECURITY.sanitize(sub.name)}</h3>
              <p>${t('seq1')}: ${g.seq1||'-'} | ${t('seq2')}: ${g.seq2||'-'} | ${t('termAvg')}: ${avg.toFixed(1)}/20</p>
              <p style="font-size:10px;margin-top:4px">${SECURITY.sanitize(g.comment||'')}</p>
            </div>
            <div class="grade-mark">${avg.toFixed(1)}</div>
            <div class="rank-badge ${rank===1?'rank-1':rank===2?'rank-2':rank===3?'rank-3':''}">#${rank}</div>
          </div>`;
        });
      }
    }
  } else if(parentTab==='attendance'){
    const att = db.attendance.filter(a=>a.studentId===selectedChildId);
    const present = att.filter(a=>a.status==='present').length;
    const rate = att.length>0 ? Math.round((present/att.length)*100) : 0;
    html += `<div class="section-title">📅 ${t('attendance')}</div>
      <div class="stats">
        <div class="stat"><div class="n">${rate}%</div><div class="l">${t('attendanceRate')}</div></div>
        <div class="stat gold"><div class="n">${present}</div><div class="l">${t('present')}</div></div>
      </div>`;
  } else if(parentTab==='events'){
    html += `<div class="section-title">📢 ${t('events')} (${t('freeAccess')})</div>`;
    db.events.sort((a,b)=>new Date(b.date)-new Date(a.date)).forEach(e=>{
      html += `<div class="event ${e.category==='urgent'?'urgent':''}">
        <div class="cat">${t(e.category)}</div>
        <div class="ttl">${SECURITY.sanitize(e.title)}</div>
        <div>${SECURITY.sanitize(e.description)}</div>
        <div class="dt">📅 ${e.date}</div>
        ${e.photo?`<img src="${e.photo}" class="event-img" alt="${SECURITY.sanitize(e.title)}">`:''}
      </div>`;
    });
  } else if(parentTab==='claims'){
    html += `<div class="section-title">⚠️ ${t('claims')}</div>`;
    // Formulaire nouvelle réclamation
    html += `<div class="claim-form">
      <h4>📝 ${t('newClaim')}</h4>
      <div class="form-group"><label>${t('claimSubject')}</label><select id="claimSubj">
        <option value="">--</option>
        ${db.subjects.filter(s=>s.classLevel===selectedChild.classLevel).map(s=>`<option value="${s.id}">${SECURITY.sanitize(s.name)}</option>`).join('')}
      </select></div>
      <div class="form-group"><label>${t('claimType')}</label><select id="claimType">
        <option value="normal">${t('normalClaim')}</option>
        <option value="urgent">${t('urgentClaim')}</option>
      </select></div>
      <div class="form-group"><label>${t('claimReason')}</label><textarea id="claimReason" rows="3" placeholder="..."></textarea></div>
      <button class="btn btn-red ios-btn btn-block" onclick="submitClaim()">📤 ${t('send')}</button>
    </div>`;
    // Liste réclamations
    const myClaims = db.claims.filter(c=>c.studentId===selectedChildId).sort((a,b)=>new Date(b.createdAt)-new Date(a.createdAt));
    if (myClaims.length === 0) {
      html += `<div class="grade-card" style="margin-top:12px"><p style="color:var(--muted);text-align:center;width:100%">${t('noClaims')}</p></div>`;
    } else {
      myClaims.forEach(c=>{
        const sub = db.subjects.find(s=>s.id===c.subjectId);
        html += `<div class="grade-card" style="border-left:4px solid ${c.status==='resolved'?'var(--ok)':'var(--warn)'}">
          <div class="grade-icon" style="background:${c.type==='urgent'?'var(--err)':'var(--warn)'}">⚠️</div>
          <div class="grade-info">
            <h3>${sub?SECURITY.sanitize(sub.name):'-'}</h3>
            <p>${SECURITY.sanitize(c.reason)}</p>
            <p style="font-size:10px">${formatDateCameroon(c.createdAt)}</p>
          </div>
          <div class="rank-badge" style="background:${c.status==='resolved'?'var(--ok)':'var(--warn)'}">${t(c.status==='resolved'?'resolved':'pending2')}</div>
        </div>`;
      });
    }
  } else if(parentTab==='gallery'){
    html += `<div class="section-title">📷 ${t('gallery')}</div>`;
    if (db.gallery.length === 0) {
      html += `<div class="grade-card"><p style="color:var(--muted);text-align:center;width:100%">${t('galleryEmpty')}</p></div>`;
    } else {
      html += `<div style="display:grid;grid-template-columns:repeat(2,1fr);gap:10px">`;
      db.gallery.slice().reverse().forEach(g=>{
        html += `<div style="background:var(--card);border-radius:12px;overflow:hidden;box-shadow:0 4px 12px rgba(0,0,0,0.1)">
          <img src="${g.photo}" style="width:100%;height:120px;object-fit:cover" alt="">
          <div style="padding:8px;font-size:11px">${SECURITY.sanitize(g.caption||'')}</div>
        </div>`;
      });
      html += `</div>`;
    }
  } else if(parentTab==='report'){
    if(!hasSubscription){
      html += `<div class="lock-overlay"><div class="icon">🔒</div><h3>${t('locked')}</h3></div>`;
    } else {
      html += `<div class="section-title">📄 ${t('reportCard')}</div>
        <button class="btn btn-primary ios-btn" onclick="generateReportCard()">📥 ${t('downloadPDF')}</button>`;
    }
  } else if(parentTab==='about'){
    html += `<div class="section-title">ℹ️ ${t('aboutSchool')}</div>
      <div class="grade-card" style="flex-direction:column;align-items:flex-start">
        <p style="margin-bottom:12px">${t('schoolDesc')}</p>
        <p><b>📞 ${t('schoolPhone')}:</b> ${db.settings.schoolPhone}</p>
        <p><b>📧 ${t('schoolEmail')}:</b> ${db.settings.schoolEmail}</p>
        <p><b>📍 ${t('schoolAddress')}:</b> ${db.settings.schoolAddress}</p>
        <p style="margin-top:12px;font-size:11px;color:var(--muted)">${t('madeWith')} | v3.0</p>
      </div>`;
  }
  
  html += `</div>`;
  return html;
}

function submitClaim(){
  const subjId = document.getElementById('claimSubj').value;
  const type = document.getElementById('claimType').value;
  const reason = SECURITY.sanitize(document.getElementById('claimReason').value.trim());
  if(!subjId || !reason){ toast(t('fillAll')); return; }
  db.claims.push({
    id:uid(), studentId:selectedChildId, subjectId:subjId, type, reason,
    status:'pending', createdAt:new Date().toISOString(), parentId:currentUser.id
  });
  db.auditLog.push({action:'newClaim',userId:currentUser.id,role:'parent',studentId:selectedChildId,timestamp:new Date().toISOString()});
  saveDB();
  toast(t('claimSent'));
  render();
}

function showPaymentModal(){
  const parent = currentUser;
  const children = db.students.filter(s=>parent.children.includes(s.id));
  const price = getSubscriptionPrice(children.length);
  const term = getCurrentTerm();
  const momo = db.settings.momoNumber || '670000000';
  modal(`
    <h2>💳 ${t('paymentInstructions')}</h2>
    <div class="sub-banner">
      <div>${t('youHave')} ${children.length} ${t('children')}</div>
      <div class="price">${price} FCFA</div>
      <div class="expiry">🕐 ${t('autoExpiry')}</div>
    </div>
    <div style="background:#f0f9ff;padding:14px;border-radius:12px;margin:12px 0">
      <p><b>${t('step1')}</b></p>
      <p style="margin:8px 0"><b>${t('momoPay')}:</b> ${momo}</p>
      <p><b>${t('orangePay')}:</b> ${momo}</p>
      <p style="margin-top:8px"><b>${t('step2')}:</b> ${children[0]?.matricule||''}</p>
    </div>
    <div class="form-group"><label>${t('transactionId')}</label><input id="payTxn" placeholder="TXN..."></div>
    <div class="modal-actions">
      <button class="btn btn-outline ios-btn" onclick="closeModal()">${t('cancel')}</button>
      <button class="btn btn-navy ios-btn" onclick="submitPayment()">${t('submit')}</button>
    </div>
  `);
}

function submitPayment(){
  const txn = SECURITY.sanitize(document.getElementById('payTxn').value.trim());
  if(!txn){ toast(t('fillAll')); return; }
  const parent = currentUser;
  const children = db.students.filter(s=>parent.children.includes(s.id));
  const price = getSubscriptionPrice(children.length);
  const term = getCurrentTerm();
  db.subscriptions = db.subscriptions.filter(s=>!(s.parentId===parent.id && s.term===term));
  db.subscriptions.push({
    id:uid(), parentId:parent.id, term, amount:price, status:'pending',
    transactionId:txn, date:new Date().toISOString().split('T')[0],
    activatedAt:null, expiresAt:null
  });
  db.auditLog.push({action:'paymentSubmitted',userId:parent.id,role:'parent',amount:price,timestamp:new Date().toISOString()});
  saveDB();
  closeModal();
  toast(t('saveSuccess')+' - Admin will verify');
  render();
}

function generateReportCard(){
  const child = db.students.find(s=>s.id===selectedChildId);
  const currentTerm = getCurrentTerm();
  const grades = db.grades.filter(g=>g.studentId===child.id && g.term===currentTerm && g.published);
  let total=0, totalCoeff=0;
  grades.forEach(g=>{
    const sub = db.subjects.find(s=>s.id===g.subjectId);
    if(sub){ total += ((g.seq1||0)+(g.seq2||0))/2 * sub.coeff; totalCoeff += sub.coeff; }
  });
  const avg = totalCoeff>0 ? (total/totalCoeff).toFixed(2) : 0;
  const html = `
    <div style="padding:30px;font-family:Arial">
      <div style="text-align:center;border-bottom:3px solid #0A2A5E;padding-bottom:20px;margin-bottom:30px">
        <h1 style="color:#0A2A5E;margin:0">DIVINE GRACE COLLEGE</h1>
        <p style="color:#D4AF37;margin:5px 0">OF ARTS, SCIENCE AND TECHNOLOGY</p>
        <p style="margin:5px 0">Garoua, Cameroon</p>
        <h2 style="color:#0A2A5E;margin-top:20px">${t('reportFor')}: ${child.firstName} ${child.lastName}</h2>
        <p>Matricule: ${child.matricule} | Class: ${child.classLevel}</p>
        <p>${t('academicYear')}: ${db.settings.academicYear} | ${t('term')}: ${currentTerm==='first'?t('firstTerm'):currentTerm==='second'?t('secondTerm'):t('thirdTerm')}</p>
      </div>
      <table style="width:100%;border-collapse:collapse;margin:20px 0">
        <tr style="background:#0A2A5E;color:#fff">
          <th style="padding:12px;border:1px solid #ddd">Subject</th>
          <th style="padding:12px;border:1px solid #ddd">Coeff</th>
          <th style="padding:12px;border:1px solid #ddd">Seq. 1</th>
          <th style="padding:12px;border:1px solid #ddd">Seq. 2</th>
          <th style="padding:12px;border:1px solid #ddd">Average</th>
        </tr>
        ${grades.map(g=>{const s=db.subjects.find(x=>x.id===g.subjectId);const seqAvg=((g.seq1||0)+(g.seq2||0))/2;return s?`<tr><td style="padding:10px;border:1px solid #ddd">${s.name}</td><td style="padding:10px;border:1px solid #ddd">${s.coeff}</td><td style="padding:10px;border:1px solid #ddd">${g.seq1||'-'}</td><td style="padding:10px;border:1px solid #ddd">${g.seq2||'-'}</td><td style="padding:10px;border:1px solid #ddd"><b>${seqAvg.toFixed(1)}</b></td></tr>`:''}).join('')}
        <tr style="background:#f0f9ff"><td colspan="4" style="padding:12px;border:1px solid #ddd"><b>${t('average')}</b></td><td style="padding:12px;border:1px solid #ddd"><b>${avg}/20</b></td></tr>
      </table>
      <div style="display:flex;justify-content:space-between;margin-top:50px;padding-top:30px;border-top:2px solid #0A2A5E">
        <div style="text-align:center"><p>${t('principalSign')}</p><div style="height:80px;border-bottom:1px solid #333;width:180px;margin-top:40px"></div></div>
        <div style="text-align:center"><p>${t('schoolStamp')}</p><div style="height:80px;border:2px dashed #ccc;width:100px;border-radius:50%;margin-top:30px"></div></div>
      </div>
    </div>
  `;
  const win = window.open('','_blank');
  win.document.write(`<html><head><title>Report Card - ${child.firstName}</title></head><body>${html}<script>window.print();<\/script></body></html>`);
}

/* ==================== TEACHER DASHBOARD ==================== */
let teacherTab = 'classes';

function renderTeacherDashboard(){
  const teacher = currentUser;
  const myClasses = teacher.classes || [];
  const mySubjects = teacher.subjects || [];
  
  let html = `<div class="dashboard">
    <div class="stats">
      <div class="stat"><div class="n">${myClasses.length}</div><div class="l">${t('myClasses')}</div></div>
      <div class="stat gold"><div class="n">${mySubjects.length}</div><div class="l">${t('subjects')}</div></div>
    </div>
    <div class="tabs">
      <button class="tab ios-btn ${teacherTab==='classes'?'active':''}" onclick="teacherTab='classes';render()">📚 ${t('myClasses')}</button>
      <button class="tab ios-btn ${teacherTab==='grades'?'active':''}" onclick="teacherTab='grades';render()">✏️ ${t('enterGrades')}</button>
      <button class="tab ios-btn ${teacherTab==='claims'?'active':''}" onclick="teacherTab='claims';render()">⚠️ ${t('claims')} ${db.claims.filter(c=>{const g=db.grades.find(x=>x.id===c.subjectId);return false;}).length>0?'<span class="badge-new">NEW</span>':''}</button>
      <button class="tab ios-btn ${teacherTab==='settings'?'active':''}" onclick="teacherTab='settings';render()">⚙️ ${t('settings')}</button>
    </div>`;
  
  if(teacherTab==='classes'){
    html += `<div class="section-title">📚 ${t('myClasses')}</div>`;
    if(myClasses.length===0){
      html += `<div class="grade-card"><p style="color:var(--muted);text-align:center;padding:20px;width:100%">${t('noData')}</p></div>`;
    } else {
      myClasses.forEach(cls=>{
        const students = sortStudents(db.students.filter(s=>s.classLevel===cls));
        html += `<div class="grade-card">
          <div class="grade-icon">🎓</div>
          <div class="grade-info">
            <h3>${cls}</h3>
            <p>${students.length} ${t('students')} - ${t('autoSort')}</p>
          </div>
        </div>`;
      });
    }
  } else if(teacherTab==='grades'){
    html += `<div class="section-title">✏️ ${t('enterGrades')}</div>
      <div class="form-group"><label>${t('selectClass')}</label><select id="tgClass" onchange="renderTeacherGrades()">
        <option value="">--</option>${myClasses.map(c=>`<option value="${c}">${c}</option>`).join('')}
      </select></div>
      <div class="form-group"><label>${t('selectSubject')}</label><select id="tgSubject">
        <option value="">--</option>${mySubjects.map(s=>`<option value="${s}">${s}</option>`).join('')}
      </select></div>
      <div class="form-group"><label>${t('selectTerm')}</label><select id="tgTerm">
        <option value="first">${t('firstTerm')}</option>
        <option value="second">${t('secondTerm')}</option>
        <option value="third">${t('thirdTerm')}</option>
      </select></div>
      <button class="btn btn-primary ios-btn" onclick="loadTeacherGradeTable()">📥 ${t('load')}</button>
      <div id="teacherGradeTable"></div>`;
  } else if(teacherTab==='claims'){
    html += `<div class="section-title">⚠️ ${t('allClaims')}</div>`;
    const teacherSubjects = db.subjects.filter(s=>s.teacherId===teacher.id);
    const teacherClaims = db.claims.filter(c=>teacherSubjects.some(s=>s.id===c.subjectId)).sort((a,b)=>new Date(b.createdAt)-new Date(a.createdAt));
    if (teacherClaims.length === 0) {
      html += `<div class="grade-card"><p style="color:var(--muted);text-align:center;width:100%">${t('noClaims')}</p></div>`;
    } else {
      teacherClaims.forEach(c=>{
        const student = db.students.find(s=>s.id===c.studentId);
        const sub = db.subjects.find(s=>s.id===c.subjectId);
        html += `<div class="grade-card" style="border-left:4px solid ${c.type==='urgent'?'var(--err)':'var(--warn)'}">
          <div class="grade-icon" style="background:${c.type==='urgent'?'var(--err)':'var(--warn)'}">⚠️</div>
          <div class="grade-info">
            <h3>${student?SECURITY.sanitize(student.firstName+' '+student.lastName):'-'}</h3>
            <p><b>${sub?SECURITY.sanitize(sub.name):'-'}</b> - ${SECURITY.sanitize(c.reason)}</p>
            <p style="font-size:10px">${formatDateCameroon(c.createdAt)}</p>
          </div>
          ${c.status==='pending'?`<button class="btn btn-sm btn-ok ios-btn" onclick="resolveClaim('${c.id}')">${t('resolve')}</button>`:`<div class="rank-badge" style="background:var(--ok)">${t('resolved')}</div>`}
        </div>`;
      });
    }
  } else if(teacherTab==='settings'){
    html += `<div class="section-title">⚙️ ${t('teacherPhone')}</div>
      <div class="grade-card" style="flex-direction:column;align-items:stretch">
        <p style="font-size:12px;color:var(--muted);margin-bottom:10px">Parents can contact you via WhatsApp for grade claims</p>
        <div class="form-group"><label>WhatsApp Number</label><input id="tWa" value="${teacher.whatsapp||''}" placeholder="670123456"></div>
        <button class="btn btn-wa ios-btn" onclick="saveTeacherWhatsapp()">💾 ${t('save')}</button>
      </div>`;
  }
  
  html += `</div>`;
  return html;
}

function saveTeacherWhatsapp(){
  const wa = SECURITY.sanitize(document.getElementById('tWa').value.trim());
  if(!SECURITY.isValidPhone(wa)){ toast('Invalid phone'); return; }
  currentUser.whatsapp = wa;
  saveDB();
  toast(t('saveSuccess'));
}

function resolveClaim(id){
  const c = db.claims.find(x=>x.id===id);
  if(c){ c.status='resolved'; c.resolvedAt=new Date().toISOString(); saveDB(); toast(t('claimResolved')); render(); }
}

function loadTeacherGradeTable(){
  const cls = document.getElementById('tgClass').value;
  const subj = document.getElementById('tgSubject').value;
  const term = document.getElementById('tgTerm').value;
  if(!cls || !subj){ toast(t('fillAll')); return; }
  const students = sortStudents(db.students.filter(s=>s.classLevel===cls));
  const subject = db.subjects.find(s=>s.name===subj && s.classLevel===cls);
  if(!subject){ toast('Subject not found'); return; }
  let html = `<div class="tbl-wrap" style="margin-top:14px"><table>
    <tr><th>${t('name')}</th><th>${t('seq1Mark')}/20</th><th>${t('seq2Mark')}/20</th><th>${t('comment')}</th></tr>`;
  students.forEach(s=>{
    const existing = db.grades.find(g=>g.studentId===s.id && g.subjectId===subject.id && g.term===term);
    html += `<tr>
      <td><b>${SECURITY.sanitize(s.lastName)}</b> ${SECURITY.sanitize(s.firstName)}</td>
      <td><input type="number" min="0" max="20" class="seq-input" value="${existing?existing.seq1||'':''}" data-sid="${s.id}" data-seq="1"></td>
      <td><input type="number" min="0" max="20" class="seq-input" value="${existing?existing.seq2||'':''}" data-sid="${s.id}" data-seq="2"></td>
      <td><input type="text" value="${existing?SECURITY.sanitize(existing.comment):''}" data-cid="${s.id}" style="width:100%;padding:6px;border:1px solid var(--border);border-radius:8px"></td>
    </tr>`;
  });
  html += `</table></div>
    <button class="btn btn-gold ios-btn btn-block" style="margin-top:14px" onclick="saveTeacherGrades('${subject.id}','${term}')">💾 ${t('saveDraft')}</button>`;
  document.getElementById('teacherGradeTable').innerHTML = html;
}

function saveTeacherGrades(subjectId, term){
  const seq1Inputs = document.querySelectorAll('#teacherGradeTable input[data-seq="1"]');
  const seq2Inputs = document.querySelectorAll('#teacherGradeTable input[data-seq="2"]');
  const comments = document.querySelectorAll('#teacherGradeTable input[data-cid]');
  seq1Inputs.forEach((inp, i)=>{
    const sid = inp.dataset.sid;
    const seq1 = parseFloat(inp.value);
    const seq2 = parseFloat(seq2Inputs[i].value);
    const comment = SECURITY.sanitize(comments[i].value);
    if(isNaN(seq1) && isNaN(seq2)) return;
    const existing = db.grades.find(g=>g.studentId===sid && g.subjectId===subjectId && g.term===term);
    if(existing){ existing.seq1=isNaN(seq1)?existing.seq1:seq1; existing.seq2=isNaN(seq2)?existing.seq2:seq2; existing.comment=comment; }
    else { db.grades.push({id:uid(),studentId:sid,subjectId,term,seq1:isNaN(seq1)?null:seq1,seq2:isNaN(seq2)?null:seq2,comment,published:false,createdAt:new Date().toISOString()}); }
  });
  saveDB();
  toast(t('saveSuccess'));
}

/* ==================== SECRETARY DASHBOARD ==================== */
let secTab = 'students';

function renderSecretaryDashboard(){
  let html = `<div class="dashboard">
    <div class="security-badge" style="margin-bottom:16px">🔒 ${t('secretaryLimited')}</div>
    <div class="tabs">
      <button class="tab ios-btn ${secTab==='students'?'active':''}" onclick="secTab='students';render()">👥 ${t('students')}</button>
      <button class="tab ios-btn ${secTab==='events'?'active':''}" onclick="secTab='events';render()">📢 ${t('announcements')}</button>
      <button class="tab ios-btn ${secTab==='gallery'?'active':''}" onclick="secTab='gallery';render()">📷 ${t('gallery')}</button>
      <button class="tab ios-btn ${secTab==='subs'?'active':''}" onclick="secTab='subs';render()">💳 ${t('subscriptions')}</button>
      <button class="tab ios-btn ${secTab==='dotation'?'active':''}" onclick="secTab='dotation';render()">📦 ${t('dotation')}<span class="badge-new">NEW</span></button>
    </div>`;
  
  if(secTab==='students') html += renderSecStudents();
  else if(secTab==='events') html += renderSecEvents();
  else if(secTab==='gallery') html += renderSecGallery();
  else if(secTab==='subs') html += renderSecSubs();
  else if(secTab==='dotation') html += renderSecDotation();
  
  html += `</div>`;
  return html;
}

function renderSecStudents(){
  let html = `<div class="section-title">⚡ ${t('quickAdd')} - ${t('onlyNameClass')}</div>
    <div class="grade-card" style="flex-direction:column;align-items:stretch">
      <div class="form-group"><label>${t('firstName')} *</label><input id="secFirst" placeholder="Ex: Amina"></div>
      <div class="form-group"><label>${t('lastName')} *</label><input id="secLast" placeholder="Ex: Bello"></div>
      <div class="form-group"><label>${t('classLevel')} *</label><select id="secClass">
        <option value="">--</option>${CLASSES.map(c=>`<option value="${c}">${c}</option>`).join('')}
      </select></div>
      <div class="form-group"><label>${t('dob')}</label><input id="secDob" type="date"></div>
      <div class="form-group"><label>${t('gender')}</label><select id="secGender">
        <option value="female">${t('female')}</option>
        <option value="male">${t('male')}</option>
      </select></div>
      <button class="btn btn-primary ios-btn" onclick="secretaryAddStudent()">➕ ${t('addStudent')}</button>
      <p style="font-size:11px;color:var(--muted);margin-top:10px;text-align:center">✨ ${t('autoGenerated')}: ${t('matricule')}, ${t('secretCode')} | 📊 ${t('autoSort')}</p>
    </div>
    
    <div class="section-title" style="margin-top:24px">📋 ${t('students')} (${t('autoSort')})</div>
    <div class="search-bar">
      <input id="secSearch" placeholder="${t('search')}..." oninput="filterSecStudents()">
      <select id="secFilter" onchange="filterSecStudents()">
        <option value="">${t('all')}</option>
        ${CLASSES.map(c=>`<option value="${c}">${c}</option>`).join('')}
      </select>
    </div>
    <div id="secStudentList"></div>`;
  return html;
}

function secretaryAddStudent(){
  const first = SECURITY.sanitize(document.getElementById('secFirst').value.trim());
  const last = SECURITY.sanitize(document.getElementById('secLast').value.trim());
  const cls = document.getElementById('secClass').value;
  const dob = document.getElementById('secDob').value;
  const gender = document.getElementById('secGender').value;
  if(!first||!last||!cls){ toast(t('fillAll')); return; }
  const matricule = genMatricule();
  const code = genSecretCode();
  const track = cls.includes('Technical') ? 'Technical' : 'General';
  const student = {id:uid(),firstName:first,lastName:last,matricule,secretCode:code,classLevel:cls,track,parentPhone:'',parentName:'',gender,dob,photo:null,createdAt:new Date().toISOString(),addedBy:'secretary'};
  db.students.push(student);
  db.auditLog.push({action:'addStudent',userId:currentUser.id,role:'secretary',studentId:student.id,matricule,timestamp:new Date().toISOString()});
  saveDB();
  modal(`
    <h2>✅ ${t('studentAdded')}</h2>
    <div class="grade-card" style="margin:16px 0">
      <div class="grade-info">
        <h3>${first} ${last}</h3>
        <p><b>${t('matricule')}:</b> ${matricule}</p>
        <p><b>${t('secretCode')}:</b> ${code}</p>
        <p><b>${t('classLevel')}:</b> ${cls}</p>
      </div>
    </div>
    <p style="font-size:12px;color:var(--muted);margin-bottom:16px">📋 ${t('copyCredentials')} et donnez-les au parent.</p>
    <button class="btn btn-primary ios-btn" onclick="closeModal();render()">${t('done')}</button>
  `);
}

function filterSecStudents(){
  const q = document.getElementById('secSearch').value.toLowerCase();
  const cls = document.getElementById('secFilter').value;
  let students = sortStudents(db.students);
  if (q) students = students.filter(s => (s.firstName+' '+s.lastName).toLowerCase().includes(q) || s.matricule.toLowerCase().includes(q));
  if (cls) students = students.filter(s => s.classLevel === cls);
  let html = `<div class="tbl-wrap"><table>
    <tr><th>${t('name')}</th><th>${t('matricule')}</th><th>${t('classLevel')}</th></tr>`;
  students.forEach(s=>{
    html += `<tr><td><b>${SECURITY.sanitize(s.lastName)}</b> ${SECURITY.sanitize(s.firstName)}</td><td>${s.matricule}</td><td>${s.classLevel}</td></tr>`;
  });
  html += `</table></div>`;
  document.getElementById('secStudentList').innerHTML = html;
}

function renderSecEvents(){
  let html = `<div class="section-title">📢 ${t('announcements')}
    <button class="btn btn-gold btn-sm ios-btn" onclick="showSecAddEventModal()">+ ${t('add')}</button>
  </div>`;
  db.events.sort((a,b)=>new Date(b.date)-new Date(a.date)).forEach(e=>{
    html += `<div class="event ${e.category==='urgent'?'urgent':''}">
      <div style="display:flex;justify-content:space-between;align-items:start">
        <div>
          <div class="cat">${t(e.category)}</div>
          <div class="ttl">${SECURITY.sanitize(e.title)}</div>
          <div>${SECURITY.sanitize(e.description)}</div>
          <div class="dt">📅 ${e.date}</div>
          ${e.photo?`<img src="${e.photo}" class="event-img" alt="">`:''}
        </div>
        <button class="btn btn-sm btn-red ios-btn" onclick="deleteEvent('${e.id}')">🗑</button>
      </div>
    </div>`;
  });
  return html;
}

function showSecAddEventModal(){
  modal(`
    <h2>${t('addEvent')}</h2>
    <div class="form-group"><label>${t('eventTitle')} *</label><input id="aeTitle"></div>
    <div class="form-group"><label>${t('eventDesc')}</label><textarea id="aeDesc" rows="3"></textarea></div>
    <div class="form-group"><label>${t('eventDate')} *</label><input id="aeDate" type="date"></div>
    <div class="form-group"><label>${t('eventCategory')}</label><select id="aeCat">
      <option value="event">${t('event')}</option>
      <option value="announcement">${t('announcement')}</option>
      <option value="exam">${t('exam')}</option>
      <option value="holiday">${t('holiday')}</option>
      <option value="urgent">${t('urgent')}</option>
    </select></div>
    <div class="form-group"><label>${t('photoEvent')}</label><input id="aePhoto" type="file" accept="image/*" onchange="handleEventPhoto(event)"></div>
    <div id="photoPreview"></div>
    <div class="modal-actions">
      <button class="btn btn-outline ios-btn" onclick="closeModal()">${t('cancel')}</button>
      <button class="btn btn-navy ios-btn" onclick="saveSecEvent()">${t('save')}</button>
    </div>
  `);
}

let tempEventPhoto = null;
function handleEventPhoto(e){
  const file = e.target.files[0];
  if(!file) return;
  const reader = new FileReader();
  reader.onload = (ev) => {
    tempEventPhoto = ev.target.result;
    document.getElementById('photoPreview').innerHTML = `<img src="${tempEventPhoto}" style="width:100%;max-height:200px;object-fit:cover;border-radius:10px;margin-top:8px">`;
  };
  reader.readAsDataURL(file);
}

function saveSecEvent(){
  const title = SECURITY.sanitize(document.getElementById('aeTitle').value.trim());
  const desc = SECURITY.sanitize(document.getElementById('aeDesc').value.trim());
  const date = document.getElementById('aeDate').value;
  const cat = document.getElementById('aeCat').value;
  if(!title||!date){ toast(t('fillAll')); return; }
  db.events.push({id:uid(),title,description:desc,date,category:cat,photo:tempEventPhoto,createdAt:new Date().toISOString(),addedBy:'secretary'});
  db.auditLog.push({action:'addEvent',userId:currentUser.id,role:'secretary',eventTitle:title,timestamp:new Date().toISOString()});
  saveDB();
  tempEventPhoto = null;
  closeModal();
  toast(t('saveSuccess'));
  render();
}

function deleteEvent(id){
  if(!confirm(t('confirmDelete'))) return;
  db.events = db.events.filter(e=>e.id!==id);
  saveDB();
  toast(t('deleteSuccess'));
  render();
}

function renderSecGallery(){
  let html = `<div class="section-title">📷 ${t('gallery')}
    <button class="btn btn-gold btn-sm ios-btn" onclick="showAddPhotoModal()">+ ${t('addPhoto')}</button>
  </div>`;
  if (db.gallery.length === 0) {
    html += `<div class="grade-card"><p style="color:var(--muted);text-align:center;width:100%">${t('galleryEmpty')}</p></div>`;
  } else {
    html += `<div style="display:grid;grid-template-columns:repeat(2,1fr);gap:10px">`;
    db.gallery.slice().reverse().forEach(g=>{
      html += `<div style="background:var(--card);border-radius:12px;overflow:hidden;box-shadow:0 4px 12px rgba(0,0,0,0.1);position:relative">
        <img src="${g.photo}" style="width:100%;height:120px;object-fit:cover" alt="">
        <div style="padding:8px;font-size:11px">${SECURITY.sanitize(g.caption||'')}</div>
        <button class="btn btn-sm btn-red ios-btn" style="position:absolute;top:4px;right:4px" onclick="deletePhoto('${g.id}')">🗑</button>
      </div>`;
    });
    html += `</div>`;
  }
  return html;
}

function showAddPhotoModal(){
  modal(`
    <h2>${t('addPhoto')}</h2>
    <div class="form-group"><label>${t('photoEvent')}</label><input id="apPhoto" type="file" accept="image/*" onchange="handleGalleryPhoto(event)"></div>
    <div id="galPhotoPreview"></div>
    <div class="form-group"><label>${t('photoCaption')}</label><input id="apCaption" placeholder="..."></div>
    <div class="modal-actions">
      <button class="btn btn-outline ios-btn" onclick="closeModal()">${t('cancel')}</button>
      <button class="btn btn-navy ios-btn" onclick="saveGalleryPhoto()">${t('save')}</button>
    </div>
  `);
}

let tempGalleryPhoto = null;
function handleGalleryPhoto(e){
  const file = e.target.files[0];
  if(!file) return;
  const reader = new FileReader();
  reader.onload = (ev) => {
    tempGalleryPhoto = ev.target.result;
    document.getElementById('galPhotoPreview').innerHTML = `<img src="${tempGalleryPhoto}" style="width:100%;max-height:200px;object-fit:cover;border-radius:10px;margin-top:8px">`;
  };
  reader.readAsDataURL(file);
}

function saveGalleryPhoto(){
  const caption = SECURITY.sanitize(document.getElementById('apCaption').value.trim());
  if(!tempGalleryPhoto){ toast('Please select a photo'); return; }
  db.gallery.push({id:uid(),photo:tempGalleryPhoto,caption,createdAt:new Date().toISOString(),addedBy:'secretary'});
  saveDB();
  tempGalleryPhoto = null;
  closeModal();
  toast(t('photoAdded'));
  render();
}

function deletePhoto(id){
  if(!confirm(t('confirmDelete'))) return;
  db.gallery = db.gallery.filter(g=>g.id!==id);
  saveDB();
  toast(t('deleteSuccess'));
  render();
}

function renderSecSubs(){
  let html = `<div class="section-title">💳 ${t('subscriptions')} (${t('autoExpiry')})</div>
    <div class="tbl-wrap"><table>
      <tr><th>${t('parentName')}</th><th>${t('parentPhone')}</th><th>${t('term')}</th><th>${t('amount')}</th><th>${t('status')}</th><th>${t('actions')}</th></tr>`;
  db.subscriptions.forEach(s=>{
    const parent = db.parents.find(p=>p.id===s.parentId);
    const termLabel = s.term==='first'?t('firstTerm'):s.term==='second'?t('secondTerm'):t('thirdTerm');
    const statusColor = s.status==='active'?'var(--ok)':s.status==='pending'?'var(--warn)':'var(--err)';
    const days = s.expiresAt ? daysLeft(s.expiresAt) : 0;
    html += `<tr>
      <td>${parent?.name||'-'}</td>
      <td>${parent?.phone||'-'}</td>
      <td>${termLabel}</td>
      <td>${s.amount} FCFA</td>
      <td><span style="color:${statusColor};font-weight:600">${t(s.status)}</span>${s.status==='active'?`<br><small>${days} ${t('daysLeft')}</small>`:''}</td>
      <td>${s.status!=='active'?`<button class="btn btn-sm btn-ok ios-btn" onclick="activateSub('${s.id}')">${t('activateSubscription')}</button>`:'-'}</td>
    </tr>`;
  });
  html += `</table></div>`;
  return html;
}

function activateSub(id){
  const s = db.subscriptions.find(x=>x.id===id);
  if(s){
    s.status='active';
    s.activatedAt = Date.now();
    s.expiresAt = Date.now() + THREE_MONTHS_MS; // 3 mois automatiques
    db.auditLog.push({action:'activateSubscription',userId:currentUser.id,role:'secretary',subId:id,expiresAt:s.expiresAt,timestamp:new Date().toISOString()});
    saveDB();
    toast(t('subscriptionActivated')+' - '+t('expiresOn')+': '+formatDateCameroon(s.expiresAt));
    render();
  }
}

function renderSecDotation(){
  let html = `<div class="section-title">📦 ${t('manageDotation')}
    <button class="btn btn-gold btn-sm ios-btn" onclick="showAddDotationModal()">+ ${t('addDotation')}</button>
  </div>`;
  if (db.dotations.length === 0) {
    html += `<div class="grade-card"><p style="color:var(--muted);text-align:center;width:100%">${t('noData')}</p></div>`;
  } else {
    db.dotations.forEach(d=>{
      const statusClass = d.status==='good'?'ok':d.status==='worn'?'warn':'err';
      const statusLabel = d.status==='good'?t('dotationGood'):d.status==='worn'?t('dotationWorn'):t('dotationBroken');
      html += `<div class="dotation-card">
        <div style="display:flex;justify-content:space-between;align-items:start">
          <div>
            <h3 style="font-size:15px;color:var(--navy)">${SECURITY.sanitize(d.name)}</h3>
            <p style="font-size:12px;color:var(--muted)">${d.classLevel} • Qty: ${d.quantity}</p>
          </div>
          <button class="btn btn-sm btn-red ios-btn" onclick="deleteDotation('${d.id}')">🗑</button>
        </div>
        <div class="status ${statusClass}">${statusLabel}</div>
      </div>`;
    });
  }
  return html;
}

function showAddDotationModal(){
  modal(`
    <h2>${t('addDotation')}</h2>
    <div class="form-group"><label>${t('dotationName')} *</label><input id="dotName" placeholder="Projector, Desk, etc."></div>
    <div class="form-group"><label>${t('dotationClass')} *</label><select id="dotClass">
      <option value="">--</option>${CLASSES.map(c=>`<option value="${c}">${c}</option>`).join('')}
    </select></div>
    <div class="form-group"><label>${t('dotationQty')}</label><input id="dotQty" type="number" value="1" min="1"></div>
    <div class="form-group"><label>${t('dotationStatus')}</label><select id="dotStatus">
      <option value="good">${t('dotationGood')}</option>
      <option value="worn">${t('dotationWorn')}</option>
      <option value="broken">${t('dotationBroken')}</option>
    </select></div>
    <div class="modal-actions">
      <button class="btn btn-outline ios-btn" onclick="closeModal()">${t('cancel')}</button>
      <button class="btn btn-navy ios-btn" onclick="saveDotation()">${t('save')}</button>
    </div>
  `);
}

function saveDotation(){
  const name = SECURITY.sanitize(document.getElementById('dotName').value.trim());
  const cls = document.getElementById('dotClass').value;
  const qty = parseInt(document.getElementById('dotQty').value) || 1;
  const status = document.getElementById('dotStatus').value;
  if(!name||!cls){ toast(t('fillAll')); return; }
  db.dotations.push({id:uid(),name,classLevel:cls,quantity:qty,status,createdAt:new Date().toISOString(),addedBy:'secretary'});
  saveDB();
  closeModal();
  toast(t('dotationAdded'));
  render();
}

function deleteDotation(id){
  if(!confirm(t('confirmDelete'))) return;
  db.dotations = db.dotations.filter(d=>d.id!==id);
  saveDB();
  toast(t('deleteSuccess'));
  render();
}

/* ==================== ADMIN DASHBOARD ==================== */
let adminTab = 'students';

function renderAdminDashboard(){
  const isSuperAdmin = currentRole === 'superadmin';
  let html = `<div class="dashboard">
    <div class="stats">
      <div class="stat"><div class="n">${db.students.length}</div><div class="l">${t('totalStudents')}</div></div>
      <div class="stat"><div class="n">${db.teachers.length}</div><div class="l">${t('totalTeachers')}</div></div>
      <div class="stat gold"><div class="n">${CLASSES.length}</div><div class="l">${t('totalClasses')}</div></div>
      <div class="stat gold"><div class="n">${db.subjects.length}</div><div class="l">${t('totalSubjects')}</div></div>
    </div>
    <div class="tabs" style="overflow-x:auto">
      <button class="tab ios-btn ${adminTab==='students'?'active':''}" onclick="adminTab='students';render()">👥 ${t('students')}</button>
      <button class="tab ios-btn ${adminTab==='teachers'?'active':''}" onclick="adminTab='teachers';render()">👨‍🏫 ${t('teachers')}</button>
      <button class="tab ios-btn ${adminTab==='subjects'?'active':''}" onclick="adminTab='subjects';render()">📚 ${t('subjects')}</button>
      <button class="tab ios-btn ${adminTab==='publish'?'active':''}" onclick="adminTab='publish';render()">📢 ${t('publishGrades')}</button>
      <button class="tab ios-btn ${adminTab==='events'?'active':''}" onclick="adminTab='events';render()">📣 ${t('events')}</button>
      <button class="tab ios-btn ${adminTab==='subs'?'active':''}" onclick="adminTab='subs';render()">💳 ${t('subscriptions')}</button>
      <button class="tab ios-btn ${adminTab==='claims'?'active':''}" onclick="adminTab='claims';render()">⚠️ ${t('claims')} ${db.claims.filter(c=>c.status==='pending').length>0?'<span class="badge-new">'+db.claims.filter(c=>c.status==='pending').length+'</span>':''}</button>
      ${isSuperAdmin ? `<button class="tab ios-btn ${adminTab==='audit'?'active':''}" onclick="adminTab='audit';render()">🔍 ${t('auditLog')}</button>` : ''}
      <button class="tab ios-btn ${adminTab==='settings'?'active':''}" onclick="adminTab='settings';render()">⚙️ ${t('settings')}</button>
    </div>`;
  
  if(adminTab==='students') html += renderAdminStudents();
  else if(adminTab==='teachers') html += renderAdminTeachers();
  else if(adminTab==='subjects') html += renderAdminSubjects();
  else if(adminTab==='publish') html += renderAdminPublish();
  else if(adminTab==='events') html += renderAdminEvents();
  else if(adminTab==='subs') html += renderAdminSubs();
  else if(adminTab==='claims') html += renderAdminClaims();
  else if(adminTab==='audit' && isSuperAdmin) html += renderAuditLog();
  else if(adminTab==='settings') html += renderAdminSettings();
  
  html += `</div>`;
  return html;
}

function renderAdminStudents(){
  const sorted = sortStudents(db.students);
  let html = `<div class="section-title">👥 ${t('students')} (${t('autoSort')})
    <button class="btn btn-gold btn-sm ios-btn" onclick="showAddStudentModal()">+ ${t('add')}</button>
  </div>
    <div class="search-bar">
      <input id="stdSearch" placeholder="${t('search')}..." oninput="filterStudents()">
      <select id="stdFilter" onchange="filterStudents()">
        <option value="">${t('all')}</option>
        ${CLASSES.map(c=>`<option value="${c}">${c}</option>`).join('')}
      </select>
    </div>
    <div id="studentList"><div class="tbl-wrap"><table>
      <tr><th>${t('name')}</th><th>${t('matricule')}</th><th>${t('classLevel')}</th><th>${t('actions')}</th></tr>`;
  sorted.forEach(s=>{
    html += `<tr>
      <td><b>${SECURITY.sanitize(s.lastName)}</b> ${SECURITY.sanitize(s.firstName)}</td>
      <td>${s.matricule}</td>
      <td>${s.classLevel}</td>
      <td>
        <button class="btn btn-sm btn-outline ios-btn" onclick="showEditStudentModal('${s.id}')">${t('edit')}</button>
        <button class="btn btn-sm btn-red ios-btn" onclick="deleteStudent('${s.id}')">🗑</button>
      </td>
    </tr>`;
  });
  html += `</table></div></div>`;
  return html;
}

function filterStudents(){
  const q = document.getElementById('stdSearch').value.toLowerCase();
  const cls = document.getElementById('stdFilter').value;
  let students = sortStudents(db.students);
  if (q) students = students.filter(s => (s.firstName+' '+s.lastName).toLowerCase().includes(q) || s.matricule.toLowerCase().includes(q));
  if (cls) students = students.filter(s => s.classLevel === cls);
  let html = `<div class="tbl-wrap"><table>
    <tr><th>${t('name')}</th><th>${t('matricule')}</th><th>${t('classLevel')}</th><th>${t('actions')}</th></tr>`;
  students.forEach(s=>{
    html += `<tr>
      <td><b>${SECURITY.sanitize(s.lastName)}</b> ${SECURITY.sanitize(s.firstName)}</td>
      <td>${s.matricule}</td>
      <td>${s.classLevel}</td>
      <td>
        <button class="btn btn-sm btn-outline ios-btn" onclick="showEditStudentModal('${s.id}')">${t('edit')}</button>
        <button class="btn btn-sm btn-red ios-btn" onclick="deleteStudent('${s.id}')">🗑</button>
      </td>
    </tr>`;
  });
  html += `</table></div>`;
  document.getElementById('studentList').innerHTML = html;
}

function showAddStudentModal(){
  modal(`
    <h2>${t('addStudent')}</h2>
    <div class="form-group"><label>${t('firstName')} *</label><input id="asFirst"></div>
    <div class="form-group"><label>${t('lastName')} *</label><input id="asLast"></div>
    <div class="form-group"><label>${t('classLevel')} *</label><select id="asClass">
      <option value="">--</option>${CLASSES.map(c=>`<option value="${c}">${c}</option>`).join('')}
    </select></div>
    <div class="form-group"><label>${t('parentPhone')}</label><input id="asPhone" placeholder="690000000"></div>
    <div class="form-group"><label>${t('parentName')}</label><input id="asParent"></div>
    <div class="form-group"><label>${t('dob')}</label><input id="asDob" type="date"></div>
    <div class="form-group"><label>${t('gender')}</label><select id="asGender">
      <option value="female">${t('female')}</option>
      <option value="male">${t('male')}</option>
    </select></div>
    <p style="font-size:11px;color:var(--muted);margin-bottom:14px">✨ ${t('autoGenerated')}: ${t('matricule')}, ${t('secretCode')}</p>
    <div class="modal-actions">
      <button class="btn btn-outline ios-btn" onclick="closeModal()">${t('cancel')}</button>
      <button class="btn btn-navy ios-btn" onclick="saveNewStudent()">${t('save')}</button>
    </div>
  `);
}

function saveNewStudent(){
  const first = SECURITY.sanitize(document.getElementById('asFirst').value.trim());
  const last = SECURITY.sanitize(document.getElementById('asLast').value.trim());
  const cls = document.getElementById('asClass').value;
  const phone = SECURITY.sanitize(document.getElementById('asPhone').value.trim());
  const parent = SECURITY.sanitize(document.getElementById('asParent').value.trim());
  const dob = document.getElementById('asDob').value;
  const gender = document.getElementById('asGender').value;
  if(!first||!last||!cls){ toast(t('fillAll')); return; }
  const matricule = genMatricule();
  const code = genSecretCode();
  const track = cls.includes('Technical') ? 'Technical' : 'General';
  const student = {id:uid(),firstName:first,lastName:last,matricule,secretCode:code,classLevel:cls,track,parentPhone:phone,parentName:parent,gender,dob,photo:null,createdAt:new Date().toISOString(),addedBy:currentRole};
  db.students.push(student);
  if (phone) {
    let parentObj = db.parents.find(p=>p.phone===phone);
    if(parentObj){ if(!parentObj.children.includes(student.id)) parentObj.children.push(student.id); }
    else { db.parents.push({id:uid(),name:parent||'Pending',phone,children:[student.id]}); }
  }
  db.auditLog.push({action:'addStudent',userId:currentUser.id,role:currentRole,studentId:student.id,matricule,timestamp:new Date().toISOString()});
  saveDB();
  closeModal();
  toast(t('saveSuccess')+' - '+t('matricule')+': '+matricule);
  render();
}

function showEditStudentModal(id){
  const s = db.students.find(x=>x.id===id);
  if(!s) return;
  modal(`
    <h2>${t('edit')} ${t('studentName')}</h2>
    <div class="form-group"><label>${t('firstName')}</label><input id="esFirst" value="${SECURITY.sanitize(s.firstName)}"></div>
    <div class="form-group"><label>${t('lastName')}</label><input id="esLast" value="${SECURITY.sanitize(s.lastName)}"></div>
    <div class="form-group"><label>${t('classLevel')}</label><select id="esClass">
      ${CLASSES.map(c=>`<
