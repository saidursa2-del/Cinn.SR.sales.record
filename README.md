# Cinn.SR.sales.record
Sales Data records 
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>Smart Sales Reporter Pro | SAIDUR RAHAMAN</title>
<meta name="theme-color" content="#0a1628">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=JetBrains+Mono:wght@400;600&family=Syne:wght@700;800&display=swap" rel="stylesheet">
<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.0/dist/chart.umd.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>
<style>
:root {
  --bg: #07101f;
  --surface: #0d1b2e;
  --surface2: #142036;
  --surface3: #1a2844;
  --border: rgba(255,255,255,0.07);
  --border2: rgba(255,255,255,0.12);
  --accent: #00e5a0;
  --accent2: #0066ff;
  --accent3: #ff6b35;
  --gold: #ffd166;
  --text: #e8eef7;
  --text2: #8899b0;
  --text3: #4a5a72;
  --danger: #ff4d6d;
  --success: #00e5a0;
  --warning: #ffd166;
  --radius: 16px;
  --radius-sm: 10px;
  --shadow: 0 8px 32px rgba(0,0,0,0.4);
  --shadow-accent: 0 0 24px rgba(0,229,160,0.15);
  --font: 'Space Grotesk', sans-serif;
  --font-mono: 'JetBrains Mono', monospace;
  --font-display: 'Syne', sans-serif;
}
*{margin:0;padding:0;box-sizing:border-box;}
body{font-family:var(--font);background:var(--bg);color:var(--text);min-height:100vh;padding-bottom:100px;-webkit-tap-highlight-color:transparent;overflow-x:hidden;}
body::before{content:'';position:fixed;top:-50%;left:-50%;width:200%;height:200%;background:radial-gradient(ellipse 60% 40% at 70% 20%, rgba(0,102,255,0.06) 0%, transparent 60%),radial-gradient(ellipse 40% 30% at 20% 80%, rgba(0,229,160,0.04) 0%, transparent 50%);pointer-events:none;z-index:0;}

/* ===== LOGIN ===== */
.login-screen{display:flex;align-items:center;justify-content:center;min-height:100vh;padding:20px;position:relative;z-index:10;}
.login-bg{position:fixed;inset:0;background:var(--bg);overflow:hidden;}
.login-bg::before{content:'';position:absolute;top:20%;left:10%;width:500px;height:500px;background:radial-gradient(circle,rgba(0,102,255,0.12) 0%,transparent 70%);border-radius:50%;}
.login-bg::after{content:'';position:absolute;bottom:10%;right:10%;width:400px;height:400px;background:radial-gradient(circle,rgba(0,229,160,0.08) 0%,transparent 70%);border-radius:50%;}
.login-card{background:var(--surface);border:1px solid var(--border2);border-radius:24px;padding:40px 36px;width:100%;max-width:440px;box-shadow:var(--shadow),0 0 60px rgba(0,229,160,0.05);position:relative;z-index:1;animation:slideUp 0.5s ease;}
@keyframes slideUp{from{opacity:0;transform:translateY(30px);}to{opacity:1;transform:translateY(0);}}
.login-logo{width:64px;height:64px;background:linear-gradient(135deg,var(--accent2),var(--accent));border-radius:18px;display:flex;align-items:center;justify-content:center;font-size:28px;margin:0 auto 20px;box-shadow:0 8px 24px rgba(0,229,160,0.3);}
.login-title{font-family:var(--font-display);font-size:1.6rem;font-weight:800;text-align:center;background:linear-gradient(135deg,var(--text),var(--accent));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;margin-bottom:4px;}
.login-sub{text-align:center;color:var(--text2);font-size:0.85rem;margin-bottom:28px;}
.field-group{margin-bottom:14px;}
.field-group label{display:block;font-size:0.7rem;font-weight:600;letter-spacing:0.08em;color:var(--text2);text-transform:uppercase;margin-bottom:7px;}
.field-group input{width:100%;padding:14px 16px;background:var(--surface2);border:1.5px solid var(--border);border-radius:var(--radius-sm);color:var(--text);font-family:var(--font);font-size:0.95rem;transition:border-color 0.2s,box-shadow 0.2s;}
.field-group input:focus{outline:none;border-color:var(--accent);box-shadow:0 0 0 3px rgba(0,229,160,0.1);}
.field-group input::placeholder{color:var(--text3);}
.btn-login{width:100%;padding:15px;background:linear-gradient(135deg,var(--accent2),var(--accent));border:none;border-radius:var(--radius-sm);color:#07101f;font-family:var(--font);font-weight:700;font-size:1rem;cursor:pointer;margin-top:8px;transition:transform 0.15s,box-shadow 0.15s;box-shadow:0 4px 20px rgba(0,229,160,0.3);}
.btn-login:active{transform:scale(0.98);}
.login-error{color:var(--danger);font-size:0.82rem;text-align:center;margin-top:10px;display:none;}
.login-footer{text-align:center;margin-top:16px;color:var(--text3);font-size:0.75rem;}
.login-footer a{color:var(--accent);text-decoration:none;}

/* ===== HEADER ===== */
.app-header{background:rgba(13,27,46,0.95);backdrop-filter:blur(20px);border-bottom:1px solid var(--border);padding:0 16px;display:flex;align-items:center;justify-content:space-between;height:60px;position:sticky;top:0;z-index:200;}
.app-header-brand{display:flex;align-items:center;gap:10px;}
.app-header-logo{width:36px;height:36px;background:linear-gradient(135deg,var(--accent2),var(--accent));border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:16px;flex-shrink:0;}
.app-header-title{font-family:var(--font-display);font-weight:800;font-size:1rem;color:var(--text);}
.app-header-sub{font-size:0.68rem;color:var(--text2);}
.app-header-actions{display:flex;align-items:center;gap:6px;}
.store-badge{background:rgba(0,229,160,0.12);border:1px solid rgba(0,229,160,0.2);color:var(--accent);padding:5px 12px;border-radius:20px;font-size:0.75rem;font-weight:600;max-width:130px;overflow:hidden;text-overflow:ellipsis;white-space:nowrap;}
.icon-btn{background:var(--surface2);border:1px solid var(--border);color:var(--text2);padding:8px 10px;border-radius:var(--radius-sm);cursor:pointer;font-size:0.85rem;transition:all 0.15s;line-height:1;}
.icon-btn:hover{border-color:var(--border2);color:var(--text);}

/* ===== CONTAINER ===== */
.container{max-width:1000px;margin:0 auto;padding:16px;}

/* ===== STAT STRIP ===== */
.stat-strip{display:grid;grid-template-columns:repeat(4,1fr);gap:10px;margin-bottom:14px;}
@media(max-width:700px){.stat-strip{grid-template-columns:repeat(2,1fr);}}
.stat-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);padding:16px;position:relative;overflow:hidden;transition:border-color 0.2s;}
.stat-card::before{content:'';position:absolute;inset:0;background:linear-gradient(135deg,rgba(255,255,255,0.02),transparent);pointer-events:none;}
.stat-card:nth-child(1){border-top:2px solid var(--accent2);}
.stat-card:nth-child(2){border-top:2px solid var(--accent);}
.stat-card:nth-child(3){border-top:2px solid var(--gold);}
.stat-card:nth-child(4){border-top:2px solid var(--accent3);}
.stat-value{font-family:var(--font-display);font-size:1.6rem;font-weight:800;color:var(--text);line-height:1;}
.stat-label{font-size:0.7rem;color:var(--text2);font-weight:500;margin-top:5px;text-transform:uppercase;letter-spacing:0.05em;}
.stat-icon{position:absolute;right:14px;top:12px;font-size:1.2rem;opacity:0.3;}

/* ===== TABS ===== */
.tab-bar{display:flex;background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);padding:5px;gap:3px;margin-bottom:14px;overflow-x:auto;scrollbar-width:none;}
.tab-bar::-webkit-scrollbar{display:none;}
.tab-btn{flex:1;min-width:80px;padding:9px 10px;background:transparent;border:none;border-radius:var(--radius-sm);color:var(--text2);font-family:var(--font);font-weight:600;font-size:0.72rem;cursor:pointer;white-space:nowrap;transition:all 0.2s;display:flex;align-items:center;justify-content:center;gap:5px;}
.tab-btn.active{background:var(--accent);color:#07101f;box-shadow:0 2px 12px rgba(0,229,160,0.3);}
.tab-btn:not(.active):hover{background:var(--surface2);color:var(--text);}
.tab-content{display:none;}
.tab-content.active{display:block;animation:fadeIn 0.2s ease;}
@keyframes fadeIn{from{opacity:0;transform:translateY(6px);}to{opacity:1;transform:translateY(0);}}

/* ===== CARDS ===== */
.card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);padding:20px;margin-bottom:12px;}
.card-title{font-family:var(--font-display);font-size:0.9rem;font-weight:800;color:var(--text);margin-bottom:16px;display:flex;align-items:center;gap:8px;}
.card-title-dot{width:8px;height:8px;border-radius:50%;background:var(--accent);flex-shrink:0;}

/* ===== FORM ELEMENTS ===== */
.grid{display:grid;grid-template-columns:1fr 1fr;gap:10px;}
@media(max-width:600px){.grid{grid-template-columns:1fr;}}
.grid-3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px;}
@media(max-width:600px){.grid-3{grid-template-columns:1fr;}}
.field{display:flex;flex-direction:column;gap:6px;}
.field label{font-size:0.68rem;font-weight:600;color:var(--text2);text-transform:uppercase;letter-spacing:0.07em;}
.field input,.field select{padding:11px 13px;background:var(--surface2);border:1.5px solid var(--border);border-radius:var(--radius-sm);color:var(--text);font-family:var(--font);font-size:0.9rem;transition:border-color 0.2s,box-shadow 0.2s;width:100%;}
.field input:focus,.field select:focus{outline:none;border-color:var(--accent);box-shadow:0 0 0 3px rgba(0,229,160,0.08);}
.field input::placeholder{color:var(--text3);}
.field select option{background:var(--surface2);}
.field input.readonly{background:rgba(0,229,160,0.06);border-color:rgba(0,229,160,0.15);color:var(--accent);font-family:var(--font-mono);font-size:0.85rem;}
.field input.editable-auto{background:rgba(255,209,102,0.06);border-color:rgba(255,209,102,0.2);color:var(--gold);}

/* ===== BUTTONS ===== */
.btn{padding:12px 18px;border:none;border-radius:var(--radius-sm);font-family:var(--font);font-weight:700;font-size:0.85rem;cursor:pointer;transition:all 0.15s;display:inline-flex;align-items:center;gap:6px;justify-content:center;}
.btn:active{transform:scale(0.97);}
.btn-primary{background:linear-gradient(135deg,var(--accent2),#0088ff);color:white;box-shadow:0 4px 16px rgba(0,102,255,0.3);}
.btn-success{background:linear-gradient(135deg,#00b87a,var(--accent));color:#07101f;box-shadow:0 4px 16px rgba(0,229,160,0.25);}
.btn-warning{background:linear-gradient(135deg,#e67e00,var(--gold));color:#07101f;box-shadow:0 4px 16px rgba(255,209,102,0.25);}
.btn-danger{background:linear-gradient(135deg,#cc0033,var(--danger));color:white;box-shadow:0 4px 16px rgba(255,77,109,0.25);}
.btn-secondary{background:var(--surface2);border:1px solid var(--border);color:var(--text);}
.btn-ghost{background:transparent;border:1px solid var(--border2);color:var(--text2);}
.btn-whatsapp{background:linear-gradient(135deg,#075e54,#25D366);color:white;box-shadow:0 4px 16px rgba(37,211,102,0.3);}
.btn-full{width:100%;}
.btn-group{display:flex;gap:8px;flex-wrap:wrap;margin-top:10px;}
.btn-group .btn{flex:1;}

/* ===== SECTION DIVIDER ===== */
.section-divider{display:flex;align-items:center;gap:12px;margin:16px 0;}
.section-divider-line{flex:1;height:1px;background:var(--border);}
.section-divider-text{font-size:0.7rem;color:var(--text3);font-weight:600;text-transform:uppercase;letter-spacing:0.08em;}

/* ===== PREVIEW ===== */
.preview-box{background:#060e1a;border:1px solid var(--border);border-radius:var(--radius);padding:20px;font-family:var(--font-mono);font-size:0.8rem;color:#a8c0d6;white-space:pre-wrap;line-height:1.7;max-height:460px;overflow-y:auto;}
.preview-box::-webkit-scrollbar{width:4px;}
.preview-box::-webkit-scrollbar-track{background:transparent;}
.preview-box::-webkit-scrollbar-thumb{background:var(--border2);border-radius:4px;}

/* ===== HISTORY ===== */
.history-item{background:var(--surface2);border:1px solid var(--border);border-radius:var(--radius-sm);padding:14px;margin-bottom:8px;display:flex;align-items:center;gap:12px;transition:border-color 0.2s;}
.history-item:hover{border-color:var(--border2);}
.history-item-date{font-family:var(--font-display);font-weight:700;font-size:0.9rem;color:var(--text);white-space:nowrap;}
.history-item-shift{font-size:0.68rem;color:var(--text2);background:var(--surface3);padding:2px 8px;border-radius:20px;border:1px solid var(--border);}
.history-item-info{flex:1;display:flex;flex-wrap:wrap;gap:8px;align-items:center;}
.history-chip{font-size:0.7rem;color:var(--text2);background:var(--surface3);padding:3px 9px;border-radius:20px;}
.history-chip.good{color:var(--accent);background:rgba(0,229,160,0.08);}
.history-chip.bad{color:var(--danger);background:rgba(255,77,109,0.08);}
.history-item-actions{display:flex;gap:5px;flex-shrink:0;}
.history-item-actions .btn{padding:7px 10px;font-size:0.75rem;}

/* ===== KPI CARDS ===== */
.kpi-grid{display:flex;flex-wrap:wrap;gap:8px;margin-bottom:14px;}
.kpi-card{background:var(--surface2);border:1px solid var(--border);border-radius:var(--radius-sm);padding:14px 18px;flex:1;min-width:130px;}
.kpi-card small{display:block;font-size:0.67rem;color:var(--text2);text-transform:uppercase;letter-spacing:0.07em;margin-bottom:5px;}
.kpi-card b{font-family:var(--font-display);font-size:1.1rem;color:var(--text);}
.kpi-card.highlight{border-color:rgba(0,229,160,0.2);background:rgba(0,229,160,0.05);}
.kpi-card.highlight b{color:var(--accent);}

/* ===== DASHBOARD CHARTS ===== */
.chart-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);padding:20px;margin-bottom:12px;}
.chart-title{font-size:0.8rem;font-weight:600;color:var(--text2);margin-bottom:14px;text-transform:uppercase;letter-spacing:0.07em;}

/* ===== BUDGET ===== */
.progress-track{height:10px;background:var(--surface2);border-radius:10px;overflow:hidden;margin:8px 0;}
.progress-fill{height:100%;border-radius:10px;transition:width 0.5s ease;}
.budget-row{display:flex;justify-content:space-between;align-items:center;padding:8px 0;border-bottom:1px solid var(--border);font-size:0.82rem;}
.budget-row:last-child{border-bottom:none;}

/* ===== MODAL ===== */
.modal{position:fixed;inset:0;background:rgba(0,0,0,0.7);backdrop-filter:blur(4px);display:none;align-items:center;justify-content:center;z-index:500;padding:16px;}
.modal.active{display:flex;}
.modal-box{background:var(--surface);border:1px solid var(--border2);border-radius:24px;padding:28px;width:100%;max-width:920px;max-height:92vh;overflow-y:auto;position:relative;}
.modal-box::-webkit-scrollbar{width:4px;}
.modal-box::-webkit-scrollbar-thumb{background:var(--border2);border-radius:4px;}
.modal-close{position:absolute;top:16px;right:16px;background:var(--surface2);border:1px solid var(--border);color:var(--text2);width:36px;height:36px;border-radius:50%;cursor:pointer;font-size:1rem;display:flex;align-items:center;justify-content:center;}
.modal-close:hover{color:var(--text);}

/* ===== REPORT TABLE ===== */
.report-table{width:100%;border-collapse:collapse;font-size:0.72rem;margin:10px 0;overflow-x:auto;display:block;}
.report-table th{background:var(--surface3);color:var(--text2);padding:9px 10px;text-align:center;font-weight:600;font-size:0.65rem;text-transform:uppercase;letter-spacing:0.06em;white-space:nowrap;}
.report-table td{padding:8px 10px;border-bottom:1px solid var(--border);text-align:right;white-space:nowrap;color:var(--text);}
.report-table td:first-child{text-align:left;color:var(--text2);}
.report-table tr:hover td{background:var(--surface2);}

/* ===== TOAST ===== */
.toast{position:fixed;bottom:24px;left:50%;transform:translateX(-50%) translateY(20px);background:var(--surface2);border:1px solid var(--border2);color:var(--text);padding:12px 22px;border-radius:30px;z-index:999;opacity:0;transition:all 0.3s;font-size:0.85rem;font-weight:500;white-space:nowrap;box-shadow:var(--shadow);}
.toast.show{opacity:1;transform:translateX(-50%) translateY(0);}

/* ===== TEXTAREA ===== */
textarea{width:100%;padding:13px;background:var(--surface2);border:1.5px solid var(--border);border-radius:var(--radius-sm);color:var(--text);font-family:var(--font-mono);font-size:0.82rem;resize:vertical;line-height:1.5;}
textarea:focus{outline:none;border-color:var(--accent);box-shadow:0 0 0 3px rgba(0,229,160,0.08);}

/* ===== USER MANAGEMENT ===== */
.user-row{display:flex;align-items:center;padding:12px;border-bottom:1px solid var(--border);gap:12px;}
.user-row:last-child{border-bottom:none;}
.user-info{flex:1;}
.user-name{font-weight:600;font-size:0.9rem;}
.user-meta{font-size:0.72rem;color:var(--text2);margin-top:2px;}
.status-pill{padding:2px 9px;border-radius:20px;font-size:0.65rem;font-weight:600;}
.status-pill.active{background:rgba(0,229,160,0.12);color:var(--accent);}
.status-pill.pending{background:rgba(255,209,102,0.12);color:var(--gold);}

/* ===== INSTALL BANNER ===== */
.install-banner{background:linear-gradient(135deg,var(--accent2),#0055dd);padding:10px 16px;text-align:center;font-size:0.8rem;color:white;display:none;position:sticky;top:60px;z-index:150;}

/* ===== SMART LOAD BTN ===== */
.smart-btn{display:flex;align-items:center;gap:8px;background:rgba(255,209,102,0.08);border:1px solid rgba(255,209,102,0.2);border-radius:var(--radius-sm);padding:10px 14px;color:var(--gold);font-size:0.82rem;font-weight:600;cursor:pointer;width:100%;margin-bottom:12px;transition:background 0.2s;}
.smart-btn:hover{background:rgba(255,209,102,0.14);}

/* ===== EMPTY STATE ===== */
.empty-state{text-align:center;padding:40px 20px;color:var(--text3);}
.empty-state-icon{font-size:2.5rem;margin-bottom:10px;}
.empty-state p{font-size:0.85rem;}

/* ===== HIGHLIGHT NUMBERS ===== */
.num-positive{color:var(--success);}
.num-negative{color:var(--danger);}

/* ===== BULK MODE ===== */
.mode-toggle{display:flex;background:var(--surface2);border-radius:var(--radius-sm);padding:3px;gap:3px;margin-bottom:12px;}
.mode-toggle button{flex:1;padding:8px;border:none;border-radius:8px;background:transparent;color:var(--text2);font-family:var(--font);font-weight:600;font-size:0.8rem;cursor:pointer;transition:all 0.2s;}
.mode-toggle button.active{background:var(--accent);color:#07101f;}
.bulk-hint{font-size:0.75rem;color:var(--text3);margin-bottom:8px;padding:8px 12px;background:var(--surface2);border-radius:var(--radius-sm);border-left:3px solid var(--accent2);}

/* ===== SCROLLBAR ===== */
::-webkit-scrollbar{width:6px;height:6px;}
::-webkit-scrollbar-track{background:transparent;}
::-webkit-scrollbar-thumb{background:var(--border2);border-radius:4px;}
</style>
</head>
<body>

<!-- Install Banner -->
<div class="install-banner" id="installBanner">
  📲 Add to home screen for offline use.
  <button onclick="installApp()" style="background:rgba(255,255,255,0.25);border:none;color:white;padding:5px 14px;border-radius:20px;margin-left:10px;cursor:pointer;font-weight:600;">Install</button>
</div>

<!-- ===== LOGIN ===== -->
<div class="login-screen" id="loginScreen">
  <div class="login-bg"></div>
  <div class="login-card">
    <div class="login-logo">📊</div>
    <div class="login-title">Smart Sales Pro</div>
    <div class="login-sub">Daily Sales Reporting System · by SAIDUR RAHAMAN</div>
    <div class="field-group">
      <label>Store Name / Username</label>
      <input type="text" id="loginUsername" placeholder="Enter store name or admin" autocomplete="username">
    </div>
    <div class="field-group">
      <label>Store Code / Password</label>
      <input type="password" id="loginPassword" placeholder="Enter your code" autocomplete="current-password">
    </div>
    <button class="btn-login" onclick="handleLogin()">Sign In →</button>
    <div class="login-error" id="loginError">❌ Invalid store name or code. Please try again.</div>
    <div class="login-footer">
      <a href="#" onclick="forgotPassword()">Admin forgot password?</a>
    </div>
  </div>
</div>

<!-- ===== APP ===== -->
<div id="appScreen" style="display:none;">
  <div class="app-header">
    <div class="app-header-brand">
      <div class="app-header-logo">📊</div>
      <div>
        <div class="app-header-title">Sales Reporter Pro</div>
        <div class="app-header-sub">by SAIDUR RAHAMAN</div>
      </div>
    </div>
    <div class="app-header-actions">
      <div class="store-badge" id="headerUserBadge">Store</div>
      <button id="settingsBtn" class="icon-btn" onclick="openSettings()">⚙️</button>
      <button class="icon-btn" onclick="handleLogout()">↗</button>
    </div>
  </div>

  <div class="container">
    <!-- Stats -->
    <div class="stat-strip">
      <div class="stat-card"><div class="stat-icon">📁</div><div class="stat-value" id="statReports">0</div><div class="stat-label">Total Reports</div></div>
      <div class="stat-card"><div class="stat-icon">💰</div><div class="stat-value" id="statSales">0</div><div class="stat-label">Monthly Sales</div></div>
      <div class="stat-card"><div class="stat-icon">🎯</div><div class="stat-value" id="statAchievement">0%</div><div class="stat-label">Achievement</div></div>
      <div class="stat-card"><div class="stat-icon">👥</div><div class="stat-value" id="statGuests">0</div><div class="stat-label">Guest Count</div></div>
    </div>

    <!-- Tabs -->
    <div class="tab-bar">
      <button class="tab-btn active" onclick="switchTab('entry')">📝 Entry</button>
      <button class="tab-btn" onclick="switchTab('bulk')">📥 Bulk</button>
      <button class="tab-btn" onclick="switchTab('preview')">👁 Preview</button>
      <button class="tab-btn" onclick="switchTab('dashboard')">📊 Dashboard</button>
      <button class="tab-btn" onclick="switchTab('budget')">🎯 Budget</button>
      <button class="tab-btn" onclick="switchTab('history')">📚 History</button>
    </div>

    <!-- ===== ENTRY TAB ===== -->
    <div id="tab-entry" class="tab-content active">
      <div class="card">
        <div class="card-title"><span class="card-title-dot"></span>Store Information</div>
        <div class="grid">
          <div class="field"><label>Store Code</label><input id="storeCode" readonly class="readonly"></div>
          <div class="field"><label>Store Name</label><input id="storeName" readonly class="readonly"></div>
          <div class="field"><label>Date</label><input type="date" id="dateInput" onchange="recalc()"></div>
          <div class="field"><label>Shift</label>
            <select id="shiftInput" onchange="recalc()">
              <option>Morning</option><option>Night</option><option>Full Day</option>
            </select>
          </div>
        </div>
      </div>

      <button class="smart-btn" onclick="smartLoadMTD()">⚡ Smart Load MTD — auto-calculate from saved reports</button>

      <div class="card">
        <div class="card-title"><span class="card-title-dot" style="background:var(--gold)"></span>Today's Sales</div>
        <div class="grid">
          <div class="field"><label>Net Sales</label><input type="number" id="netSales" step="0.01" placeholder="0.00" oninput="liveCalc()"></div>
          <div class="field"><label>Budget Sale</label><input type="number" id="budgetSale" step="0.01" placeholder="0.00" oninput="liveCalc()"></div>
          <div class="field"><label>Home Delivery</label><input type="number" id="homeDelivery" step="0.01" placeholder="0.00" oninput="liveCalc()"></div>
          <div class="field"><label>Guest Count</label><input type="number" id="guestCount" placeholder="0" oninput="liveCalc()"></div>
          <div class="field"><label>Dine IN (auto)</label><input class="editable-auto" id="dineIn" onchange="overrideDineIn()"></div>
          <div class="field"><label>Variance</label><input readonly class="readonly" id="variance"></div>
          <div class="field"><label>% Achievement</label><input readonly class="readonly" id="percentage"></div>
          <div class="field"><label>AVG Check</label><input readonly class="readonly" id="avgCheck"></div>
        </div>
        <div class="section-divider"><div class="section-divider-line"></div><div class="section-divider-text">LTO & Mocha</div><div class="section-divider-line"></div></div>
        <div class="grid">
          <div class="field"><label>LTO Sale</label><input type="number" id="ltoSale" step="0.01" placeholder="0.00" oninput="liveCalc()"></div>
          <div class="field"><label>Mocha Sales Qty</label><input type="number" id="mochaQty" placeholder="0" oninput="liveCalc()"></div>
          <div class="field"><label>Mocha % (auto)</label><input readonly class="readonly" id="mochaPct"></div>
        </div>
      </div>

      <div class="card">
        <div class="card-title"><span class="card-title-dot" style="background:var(--accent2)"></span>Month-To-Date (Auto-Calculated)</div>
        <div class="grid">
          <div class="field"><label>MTD Net Sales</label><input readonly class="readonly" id="mtdNetSales"></div>
          <div class="field"><label>MTD Budget</label><input readonly class="readonly" id="mtdBudget"></div>
          <div class="field"><label>MTD Variance</label><input readonly class="readonly" id="mtdVariance"></div>
          <div class="field"><label>MTD % Achievement</label><input readonly class="readonly" id="mtdPercentage"></div>
          <div class="field"><label>MTD Dine IN</label><input readonly class="readonly" id="mtdDineIn"></div>
          <div class="field"><label>MTD Home Delivery</label><input readonly class="readonly" id="mtdHomeDelivery"></div>
          <div class="field"><label>MTD Guest Count</label><input readonly class="readonly" id="mtdGuestCount"></div>
          <div class="field"><label>MTD AVG Check</label><input readonly class="readonly" id="mtdAvgCheck"></div>
          <div class="field"><label>MTD LTO Sale</label><input readonly class="readonly" id="mtdLtoSale"></div>
          <div class="field"><label>MTD Mocha Qty</label><input readonly class="readonly" id="mtdMochaQty"></div>
          <div class="field"><label>MTD Mocha %</label><input readonly class="readonly" id="mtdMochaPct"></div>
          <div class="field"><label>Customer Feedback (out of 5)</label><input class="editable-auto" id="mtdFeedback" placeholder="e.g. 4.5" onchange="liveCalc()"></div>
        </div>
      </div>

      <div class="btn-group">
        <button class="btn btn-success" id="saveBtn" onclick="saveReport()">💾 Save Report</button>
        <button class="btn btn-primary" id="updateBtn" style="display:none;" onclick="updateReport()">✅ Update</button>
        <button class="btn btn-ghost" id="cancelEditBtn" style="display:none;" onclick="cancelEdit()">↩ Cancel</button>
        <button class="btn btn-danger" onclick="clearForm()">🗑 Clear</button>
      </div>
    </div>

    <!-- ===== BULK TAB ===== -->
    <div id="tab-bulk" class="tab-content">
      <div class="card">
        <div class="card-title"><span class="card-title-dot" style="background:var(--accent2)"></span>Bulk Import</div>
        <div class="mode-toggle">
          <button id="csvModeBtn" class="active" onclick="setBulkMode('csv')">📄 CSV Format</button>
          <button id="waModeBtn" onclick="setBulkMode('whatsapp')">💬 WhatsApp Paste</button>
        </div>
        <div class="bulk-hint" id="bulkInstructions">CSV columns: Date, Shift, Net Sales, Budget, Dine IN, Delivery, Guests, LTO Sale, Mocha Qty</div>
        <textarea id="bulkData" rows="8" placeholder="Paste your data here..."></textarea>
        <div style="margin-top:8px;">
          <button class="btn btn-primary btn-full" onclick="parseAndImport()">🔍 Parse & Preview</button>
        </div>
        <div id="bulkPreview" style="margin-top:10px;"></div>
      </div>
    </div>

    <!-- ===== PREVIEW TAB ===== -->
    <div id="tab-preview" class="tab-content">
      <div class="card">
        <div class="card-title"><span class="card-title-dot"></span>WhatsApp Report Preview</div>
        <div class="preview-box" id="previewOutput"></div>
      </div>
      <div class="btn-group">
        <button class="btn btn-whatsapp" onclick="shareWhatsApp()">📤 WhatsApp</button>
        <button class="btn btn-secondary" onclick="copyToClipboard()">📋 Copy</button>
        <button class="btn btn-secondary" onclick="downloadReportTxt()">💾 .txt</button>
        <button class="btn btn-primary" onclick="downloadPDF()">📄 PDF</button>
      </div>
    </div>

    <!-- ===== DASHBOARD TAB ===== -->
    <div id="tab-dashboard" class="tab-content">
      <div class="card">
        <div class="card-title"><span class="card-title-dot" style="background:var(--accent2)"></span>Monthly Performance</div>
        <div id="dashSummary"></div>
      </div>
      <div class="chart-card">
        <div class="chart-title">📈 Daily Sales Trend</div>
        <canvas id="salesChart" style="max-height:220px;"></canvas>
      </div>
      <div class="chart-card">
        <div class="chart-title">🎯 Sales vs Budget</div>
        <canvas id="budgetChart" style="max-height:200px;"></canvas>
      </div>
      <div class="btn-group">
        <button class="btn btn-primary btn-full" onclick="showManagementReport()">📋 Full Month-End Report</button>
        <button class="btn btn-secondary btn-full" onclick="showExecutivePresentation()">📊 Executive View</button>
      </div>
    </div>

    <!-- ===== BUDGET TAB ===== -->
    <div id="tab-budget" class="tab-content">
      <div class="card">
        <div class="card-title"><span class="card-title-dot" style="background:var(--gold)"></span>Budget Planner</div>
        <div class="grid">
          <div class="field"><label>Month</label><input type="month" id="budgetMonth" onchange="loadBudget()"></div>
          <div class="field"><label>Monthly Target</label><input type="number" id="budgetTarget" step="0.01" placeholder="0.00" onchange="saveBudget()"></div>
          <div class="field"><label>Working Days</label><input type="number" id="budgetDays" placeholder="30" onchange="saveBudget()"></div>
        </div>
        <div style="display:flex;gap:8px;margin-top:12px;">
          <button class="btn btn-ghost" onclick="uploadBudgetCSV()" style="flex:1;">📤 Upload CSV</button>
          <button class="btn btn-ghost" onclick="downloadBudgetTemplate()" style="flex:1;">📥 Template</button>
        </div>
        <div style="margin-top:16px;">
          <div style="display:flex;justify-content:space-between;font-size:0.75rem;color:var(--text2);margin-bottom:6px;">
            <span>Progress</span>
            <span><b id="budgetPercent" style="color:var(--accent)">0</b>% achieved</span>
          </div>
          <div class="progress-track">
            <div class="progress-fill" id="budgetProgressFill" style="width:0%;background:linear-gradient(90deg,var(--accent2),var(--accent));"></div>
          </div>
          <div style="display:flex;justify-content:space-between;font-size:0.78rem;color:var(--text2);margin-top:5px;">
            <span>Achieved: <b style="color:var(--accent)" id="budgetAchieved">0.00</b></span>
            <span>Target: <b id="budgetTargetDisplay">0.00</b></span>
          </div>
        </div>
      </div>
      <div class="card">
        <div class="card-title"><span class="card-title-dot" style="background:var(--accent3)"></span>Daily vs Target</div>
        <div id="budgetDailyComparison"></div>
      </div>
    </div>

    <!-- ===== HISTORY TAB ===== -->
    <div id="tab-history" class="tab-content">
      <div class="card" id="historyCard">
        <div class="card-title"><span class="card-title-dot" style="background:var(--accent3)"></span>Saved Reports</div>
        <div id="historyList"></div>
      </div>
      <div class="btn-group">
        <button class="btn btn-primary" onclick="exportCSV()">📥 Export CSV</button>
        <button class="btn btn-secondary" onclick="downloadHistoryPDF()">📄 Download PDF</button>
      </div>
    </div>
  </div>
</div>

<!-- ===== SETTINGS MODAL ===== -->
<div class="modal" id="settingsModal">
  <div class="modal-box" style="max-width:540px;">
    <button class="modal-close" onclick="closeModal('settingsModal')">✕</button>
    <h3 style="font-family:var(--font-display);margin-bottom:20px;">⚙️ Settings</h3>
    <div id="normalSettings">
      <div class="card-title" style="margin-bottom:10px;"><span class="card-title-dot"></span>Change Password</div>
      <div class="field" style="margin-bottom:10px;"><label>Current Password</label><input type="password" id="oldPass" placeholder="Current password"></div>
      <div class="field" style="margin-bottom:14px;"><label>New Password</label><input type="password" id="newPass" placeholder="New password"></div>
      <button class="btn btn-primary btn-full" onclick="changePassword()">Update Password</button>
    </div>
    <div id="adminSettings" style="display:none;">
      <div class="section-divider"><div class="section-divider-line"></div><div class="section-divider-text">Admin Panel</div><div class="section-divider-line"></div></div>
      <div class="card-title" style="margin-bottom:10px;"><span class="card-title-dot" style="background:var(--accent2)"></span>User Management</div>
      <div id="userManagementList"></div>
      <div style="margin-top:16px;display:flex;flex-wrap:wrap;gap:8px;">
        <button class="btn btn-secondary" onclick="backupData()" style="flex:1;">📥 Backup Data</button>
        <label class="btn btn-secondary" style="flex:1;cursor:pointer;">📤 Restore <input type="file" id="restoreFile" onchange="restoreData()" accept=".json" style="display:none;"></label>
        <button class="btn btn-danger btn-full" onclick="resetSystem()">🗑 Reset Everything</button>
      </div>
    </div>
  </div>
</div>

<!-- ===== MANAGEMENT REPORT MODAL ===== -->
<div class="modal" id="managementReportModal">
  <div class="modal-box" id="managementReportContent">
    <button class="modal-close" onclick="closeModal('managementReportModal')">✕</button>
    <div id="reportContainer"></div>
    <button class="btn btn-primary btn-full" style="margin-top:16px;" onclick="downloadManagementPDF()">📥 Download PDF</button>
  </div>
</div>

<!-- ===== EXECUTIVE MODAL ===== -->
<div class="modal" id="executiveModal">
  <div class="modal-box" id="executiveContent">
    <button class="modal-close" onclick="closeModal('executiveModal')">✕</button>
    <div id="executiveContainer"></div>
    <button class="btn btn-primary btn-full" style="margin-top:16px;" onclick="downloadExecutivePDF()">📥 Download PDF</button>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
// ===== STATE =====
let store = JSON.parse(localStorage.getItem('store') || '{"code":"#337#","name":"Al Hasa Mall"}');
let reports = JSON.parse(localStorage.getItem('reports') || '[]');
let budgets = JSON.parse(localStorage.getItem('budgets') || '{}');
let users = JSON.parse(localStorage.getItem('users') || JSON.stringify([
  {username:"admin",password:"saidur337",role:"admin",status:"active"},
  {username:"Khalediya",password:"348",role:"user",status:"active"},
  {username:"Othaim",password:"329",role:"user",status:"active"},
  {username:"Panda",password:"346",role:"user",status:"active"}
]));
let currentUser = JSON.parse(sessionStorage.getItem('user') || 'null');
let editId = null, manualDineIn = false, bulkMode = 'csv';
let chartInstance = null, budgetChartInstance = null;

const $ = id => document.getElementById(id);
const val = id => parseFloat($(id).value) || 0;
const int = id => parseInt($(id).value) || 0;
const fmt = (n, dec=2) => isNaN(n) ? '0.00' : n.toLocaleString('en-US',{minimumFractionDigits:dec,maximumFractionDigits:dec});
const saveAll = () => {
  localStorage.setItem('store', JSON.stringify(store));
  localStorage.setItem('reports', JSON.stringify(reports));
  localStorage.setItem('budgets', JSON.stringify(budgets));
};
const saveUsers = () => localStorage.setItem('users', JSON.stringify(users));
const toast = msg => {
  const t = $('toast'); t.textContent = msg; t.classList.add('show');
  setTimeout(() => t.classList.remove('show'), 2200);
};

// ===== PWA =====
let deferredPrompt;
window.addEventListener('beforeinstallprompt', e => {
  e.preventDefault(); deferredPrompt = e; $('installBanner').style.display = 'block';
});
window.installApp = () => {
  if (deferredPrompt) { deferredPrompt.prompt(); deferredPrompt.userChoice.then(() => { deferredPrompt = null; $('installBanner').style.display = 'none'; }); }
};
if ('serviceWorker' in navigator) {
  const swCode = `const C='sales-v3';self.addEventListener('install',e=>{e.waitUntil(caches.open(C).then(c=>c.addAll(['./'])))});self.addEventListener('fetch',e=>{e.respondWith(caches.match(e.request).then(r=>r||fetch(e.request)))});`;
  navigator.serviceWorker.register(URL.createObjectURL(new Blob([swCode], {type:'application/javascript'}))).catch(()=>{});
}

// ===== AUTH =====
function handleLogin() {
  const u = $('loginUsername').value.trim();
  const p = $('loginPassword').value.trim();
  const user = users.find(x => x.username === u && x.password === p);
  if (!user || user.status !== 'active') { $('loginError').style.display = 'block'; return; }
  $('loginError').style.display = 'none';
  currentUser = {username: user.username, role: user.role};
  sessionStorage.setItem('user', JSON.stringify(currentUser));
  if (user.role === 'user') { store.name = user.username; store.code = '#' + user.password + '#'; }
  else { store.name = 'Admin Store'; store.code = '#337#'; }
  $('loginScreen').style.display = 'none';
  $('appScreen').style.display = 'block';
  $('headerUserBadge').textContent = '🏬 ' + store.name;
  if (user.role === 'admin') { $('settingsBtn').style.display = 'inline-flex'; $('adminSettings').style.display = 'block'; }
  else { $('settingsBtn').style.display = 'none'; }
  refreshUI();
}
function forgotPassword() {
  const code = prompt('Enter master code:');
  if (code === '#337#') {
    let admin = users.find(u => u.username === 'admin');
    if (admin) admin.password = 'saidur337'; else users.push({username:'admin',password:'saidur337',role:'admin',status:'active'});
    saveUsers(); toast('✅ Admin password reset to: saidur337');
  } else toast('❌ Invalid master code');
}
function handleLogout() { currentUser = null; sessionStorage.removeItem('user'); location.reload(); }

// ===== REFRESH =====
function refreshUI() {
  $('storeCode').value = store.code;
  $('storeName').value = store.name;
  $('dateInput').value = new Date().toISOString().slice(0,10);
  $('budgetMonth').value = new Date().toISOString().slice(0,7);
  editId = null; toggleEditMode(false); manualDineIn = false;
  liveCalc(); loadHistory(); updateDashboard(); loadBudget(); drawCharts();
  if (currentUser?.role === 'admin') renderUserManagement();
}
function toggleEditMode(on) {
  $('saveBtn').style.display = on ? 'none' : 'flex';
  $('updateBtn').style.display = on ? 'flex' : 'none';
  $('cancelEditBtn').style.display = on ? 'flex' : 'none';
}

// ===== CALCULATIONS =====
function liveCalc() {
  if (!manualDineIn) $('dineIn').value = fmt(Math.max(0, val('netSales') - val('homeDelivery')));
  const variance = val('netSales') - val('budgetSale');
  $('variance').value = (variance >= 0 ? '+' : '') + fmt(variance);
  $('percentage').value = val('budgetSale') > 0 ? Math.round(val('netSales') / val('budgetSale') * 100) + '%' : '0%';
  $('avgCheck').value = fmt(int('guestCount') > 0 ? val('netSales') / int('guestCount') : 0);
  const net = val('netSales'), mocha = int('mochaQty');
  $('mochaPct').value = net > 0 ? (mocha / net * 100).toFixed(1) + '%' : '0.0%';
  autoMTD(); updateMTDFields(); updatePreview();
}
function autoMTD() {
  const date = $('dateInput').value;
  if (!date) return;
  const cd = new Date(date + 'T00:00:00');
  const cm = cd.getMonth(), cy = cd.getFullYear();
  let sN=0, sB=0, sG=0, sD=0, sL=0, sM=0;
  reports.forEach(r => {
    const rd = new Date(r.date + 'T00:00:00');
    if (rd.getMonth()===cm && rd.getFullYear()===cy && rd <= cd) {
      if (editId && r.id === editId) return;
      if (r.date === date && !editId) return;
      sN += r.netSales||0; sB += r.budgetSale||0; sG += r.guestCount||0;
      sD += r.homeDelivery||0; sL += r.ltoSale||0; sM += r.mochaQty||0;
    }
  });
  const mtdN = sN + val('netSales'), mtdM = sM + int('mochaQty');
  $('mtdNetSales').value = mtdN.toFixed(2);
  $('mtdBudget').value = (sB + val('budgetSale')).toFixed(2);
  $('mtdGuestCount').value = sG + int('guestCount');
  $('mtdHomeDelivery').value = (sD + val('homeDelivery')).toFixed(2);
  $('mtdLtoSale').value = (sL + val('ltoSale')).toFixed(2);
  $('mtdMochaQty').value = mtdM;
  $('mtdMochaPct').value = mtdN > 0 ? (mtdM / mtdN * 100).toFixed(1) + '%' : '0.0%';
}
function updateMTDFields() {
  const mn=val('mtdNetSales'), mb=val('mtdBudget'), mg=int('mtdGuestCount'), mhd=val('mtdHomeDelivery');
  $('mtdDineIn').value = fmt(Math.max(0, mn - mhd));
  $('mtdVariance').value = (mn-mb >= 0 ? '+' : '') + fmt(mn - mb);
  $('mtdPercentage').value = mb > 0 ? Math.round(mn / mb * 100) + '%' : '0%';
  $('mtdAvgCheck').value = fmt(mg > 0 ? mn / mg : 0);
  const mtdM = int('mtdMochaQty');
  $('mtdMochaPct').value = mn > 0 ? (mtdM / mn * 100).toFixed(1) + '%' : '0.0%';
}
function overrideDineIn() { manualDineIn = true; liveCalc(); }
function recalc() { manualDineIn = false; liveCalc(); }
function smartLoadMTD() { autoMTD(); updateMTDFields(); updatePreview(); toast('⚡ MTD recalculated from saved reports'); }

// ===== PREVIEW TEXT =====
function generateText() {
  const sc=store.code, sn=store.name, dv=$('dateInput').value, sh=$('shiftInput').value;
  const dp=dv.split('-'), fd=dp[2]+'/ '+dp[1]+' /'+dp[0];
  const ns=val('netSales'), bs=val('budgetSale'), v=ns-bs, pct=bs>0?Math.round(ns/bs*100):0;
  const di=val('dineIn'), hd=val('homeDelivery'), gc=int('guestCount'), ac=gc>0?ns/gc:0;
  const lto=val('ltoSale'), mocha=int('mochaQty'), mochaPct=$('mochaPct').value;
  const mn=val('mtdNetSales'), mb=val('mtdBudget'), mv=mn-mb, mPct=mb>0?Math.round(mn/mb*100):0;
  const mdi=val('mtdDineIn'), mhd=val('mtdHomeDelivery'), mgc=int('mtdGuestCount'), mac=mgc>0?mn/mgc:0;
  const mlto=val('mtdLtoSale'), mmocha=int('mtdMochaQty'), mmochaPct=$('mtdMochaPct').value;
  const mtdFeedback = parseFloat($('mtdFeedback').value) || 0;
  return `${sn}\nStore code${sc}\nDate: *_${fd}_*\nShift : *${sh}*\n________________________\n*Today'Sales*\n\n*Net  Sales* :${fmt(ns)}\n*Budget  sale* : ${fmt(bs)}\n*Variance* :${fmt(v)}\n*Percentage* :${pct}%\n\n*Dine IN Sales* :${fmt(di)}\n*Home Delivery Sales* :${fmt(hd)}\n\n*Guest Count* :${gc}\n *AVG Check* :${fmt(ac)}\n\n*LTO Sale* :${fmt(lto)}\n*Mocha Sales Qty* :${mocha}\n*Mocha %* :${mochaPct}\n________________________\n*Month Today*\n\n*MTD Net Sales* :${fmt(mn)}\n*MTD Budget* :${fmt(mb)}\n*MTD Variance* :${fmt(mv)}\n*MTD Percentage* : ${mPct}%\n\n*Dine IN Sales* :${fmt(mdi)}\n*Home Delivery Sales* :${fmt(mhd)}\n\n*Guest Count* :${mgc}\n *AVG Check* :${fmt(mac)}\n\n*MTD LTO Sale* :${fmt(mlto)}\n*MTD Mocha Qty* :${mmocha}\n*MTD Mocha %* :${mmochaPct}\n\n*Customer Feedback* :${mtdFeedback} out of 5`;
}
function updatePreview() { if($('previewOutput')) $('previewOutput').textContent = generateText(); }

// ===== SAVE / UPDATE =====
function saveReport() {
  if (val('netSales') === 0) return toast('⚠️ Enter Net Sales first');
  const duplicate = reports.find(r => r.date === $('dateInput').value && r.shift === $('shiftInput').value && r.storeCode === store.code);
  if (duplicate && !editId) {
    if (!confirm('A report for this date & shift already exists. Save anyway?')) return;
  }
  const r = {
    id: Date.now().toString(), date: $('dateInput').value, shift: $('shiftInput').value,
    netSales: val('netSales'), budgetSale: val('budgetSale'), dineIn: val('dineIn'),
    homeDelivery: val('homeDelivery'), guestCount: int('guestCount'),
    ltoSale: val('ltoSale'), mochaQty: int('mochaQty'), mochaPct: $('mochaPct').value,
    mtdNetSales: val('mtdNetSales'), mtdBudget: val('mtdBudget'),
    mtdDineIn: val('mtdDineIn'), mtdHomeDelivery: val('mtdHomeDelivery'), mtdGuestCount: int('mtdGuestCount'),
    mtdLtoSale: val('mtdLtoSale'), mtdMochaQty: int('mtdMochaQty'), mtdMochaPct: $('mtdMochaPct').value,
    mtdFeedback: parseFloat($('mtdFeedback').value) || 0,
    createdBy: currentUser?.username, storeCode: store.code,
    savedAt: new Date().toISOString()
  };
  reports.unshift(r); saveAll(); clearForm(); loadHistory(); updateDashboard(); drawCharts(); loadBudget();
  toast('✅ Report saved! Switch to Preview to share.');
  switchTab('preview');
}
function updateReport() {
  if (!editId) return;
  const idx = reports.findIndex(r => r.id === editId);
  if (idx === -1) return;
  Object.assign(reports[idx], {
    date: $('dateInput').value, shift: $('shiftInput').value,
    netSales: val('netSales'), budgetSale: val('budgetSale'), dineIn: val('dineIn'),
    homeDelivery: val('homeDelivery'), guestCount: int('guestCount'),
    ltoSale: val('ltoSale'), mochaQty: int('mochaQty'), mochaPct: $('mochaPct').value,
    mtdNetSales: val('mtdNetSales'), mtdBudget: val('mtdBudget'),
    mtdDineIn: val('mtdDineIn'), mtdHomeDelivery: val('mtdHomeDelivery'), mtdGuestCount: int('mtdGuestCount'),
    mtdLtoSale: val('mtdLtoSale'), mtdMochaQty: int('mtdMochaQty'), mtdMochaPct: $('mtdMochaPct').value,
    mtdFeedback: parseFloat($('mtdFeedback').value) || 0, updatedAt: new Date().toISOString()
  });
  saveAll(); clearForm(); editId = null; toggleEditMode(false);
  loadHistory(); updateDashboard(); drawCharts(); loadBudget(); toast('✅ Report updated');
}
function cancelEdit() { clearForm(); editId = null; toggleEditMode(false); liveCalc(); }
function clearForm() {
  ['netSales','budgetSale','homeDelivery','guestCount','ltoSale','mochaQty'].forEach(id => $(id).value = '');
  $('mtdFeedback').value = ''; manualDineIn = false; liveCalc();
}

// ===== EXPORT =====
function shareWhatsApp() { window.open('https://wa.me/?text=' + encodeURIComponent(generateText())); }
function copyToClipboard() { navigator.clipboard.writeText(generateText()).then(() => toast('📋 Copied — paste in WhatsApp!')); }
function downloadReportTxt() {
  const b = new Blob([generateText()], {type:'text/plain'});
  const a = document.createElement('a'); a.href = URL.createObjectURL(b); a.download = 'sales_report.txt'; a.click();
}
function downloadPDF() {
  const {jsPDF} = window.jspdf;
  const doc = new jsPDF();
  doc.setFontSize(16); doc.text('Smart Sales Reporter Pro', 20, 20);
  doc.setFontSize(10); doc.text(generateText(), 20, 32, {maxWidth: 170}); doc.save('sales_report.pdf');
}

// ===== BULK IMPORT =====
function setBulkMode(mode) {
  bulkMode = mode;
  $('csvModeBtn').className = mode === 'csv' ? 'active' : '';
  $('waModeBtn').className = mode === 'whatsapp' ? 'active' : '';
  $('bulkInstructions').textContent = mode === 'csv'
    ? 'CSV columns: Date, Shift, Net Sales, Budget, Dine IN, Delivery, Guests, LTO Sale, Mocha Qty'
    : 'Paste one or more WhatsApp report blocks separated by blank lines';
}
function parseWhatsAppText(text) {
  const res = {date:null,shift:null,netSales:0,budgetSale:0,dineIn:0,homeDelivery:0,guestCount:0,ltoSale:0,mochaQty:0,mtdNetSales:0,mtdBudget:0,mtdDineIn:0,mtdHomeDelivery:0,mtdGuestCount:0,mtdLtoSale:0,mtdMochaQty:0,mtdFeedback:0};
  const dm = text.match(/Date\s*:\s*\*?_?\s*(\d{1,2})\s*\/\s*(\d{1,2})\s*\/\s*(\d{4})/i);
  if (dm) res.date = `${dm[3]}-${dm[2].padStart(2,'0')}-${dm[1].padStart(2,'0')}`;
  const sm = text.match(/Shift\s*:\s*\*?\s*(Morning|Night|Full\s*Day)/i);
  if (sm) res.shift = sm[1].replace(/\s+/g,' ').trim();
  const extr = (label, section=text) => { const m = section.match(new RegExp(`\\*?${label}\\*?\\s*:?\\s*([+-]?[\\d,]+\\.?\\d*)`, 'i')); return m ? parseFloat(m[1].replace(/,/g,''))||0 : 0; };
  res.netSales = extr('Net\\s*Sales'); res.budgetSale = extr('Budget\\s*sale');
  res.dineIn = extr('Dine\\s*IN\\s*Sales'); res.homeDelivery = extr('Home\\s*Delivery\\s*Sales');
  res.guestCount = Math.round(extr('Guest\\s*Count')); res.ltoSale = extr('LTO\\s*Sale'); res.mochaQty = Math.round(extr('Mocha\\s*Sales\\s*Qty'));
  const mtd = text.split(/Month\s*Today/i)[1] || '';
  if (mtd) {
    res.mtdNetSales = extr('MTD\\s*Net\\s*Sales', mtd)||extr('Net\\s*Sales', mtd);
    res.mtdBudget = extr('MTD\\s*Budget', mtd)||extr('Budget\\s*sale', mtd);
    res.mtdDineIn = extr('Dine\\s*IN\\s*Sales', mtd); res.mtdHomeDelivery = extr('Home\\s*Delivery\\s*Sales', mtd);
    res.mtdGuestCount = Math.round(extr('Guest\\s*Count', mtd));
    res.mtdLtoSale = extr('MTD\\s*LTO\\s*Sale', mtd)||extr('LTO\\s*Sale', mtd);
    res.mtdMochaQty = Math.round(extr('MTD\\s*Mocha\\s*Qty', mtd)||extr('Mocha\\s*Sales\\s*Qty', mtd));
    const fb = mtd.match(/Customer\s*Feedback\s*:\s*([\d.]+)\s*out\s*of\s*5/i);
    if (fb) res.mtdFeedback = parseFloat(fb[1])||0;
  }
  return res;
}
function parseAndImport() {
  const raw = $('bulkData').value.trim(); if (!raw) return toast('Paste data first');
  let parsed = [];
  if (bulkMode === 'whatsapp') {
    raw.split(/\n\s*\n/).filter(b=>b.trim()).forEach(b => { const d=parseWhatsAppText(b); if(d.date&&d.shift&&d.netSales>0) parsed.push(d); });
  } else {
    raw.split('\n').forEach(line => {
      const p = line.split(',').map(s=>s.trim());
      if (p.length >= 7 && p[0] && p[1] && parseFloat(p[2]) > 0)
        parsed.push({date:p[0],shift:p[1],netSales:parseFloat(p[2]),budgetSale:parseFloat(p[3])||0,dineIn:parseFloat(p[4])||0,homeDelivery:parseFloat(p[5])||0,guestCount:parseInt(p[6])||0,ltoSale:parseFloat(p[7])||0,mochaQty:parseInt(p[8])||0});
    });
  }
  if (!parsed.length) { $('bulkPreview').innerHTML = '<p style="color:var(--danger);font-size:0.85rem;">❌ No valid records found. Check your format.</p>'; return; }
  window._parsed = parsed;
  $('bulkPreview').innerHTML = `<div style="background:rgba(0,229,160,0.08);border:1px solid rgba(0,229,160,0.2);border-radius:10px;padding:12px;margin-top:10px;font-size:0.85rem;"><b style="color:var(--accent)">✅ ${parsed.length} records ready to import</b><br><span style="color:var(--text2)">Dates: ${parsed.map(r=>r.date).join(', ')}</span></div><button class="btn btn-success btn-full" style="margin-top:8px;" onclick="confirmImport()">✅ Confirm Import</button>`;
}
function confirmImport() {
  if (!window._parsed) return;
  window._parsed.forEach(r => {
    reports.push({
      id: Date.now() + Math.random().toString(), ...r,
      mochaPct: r.netSales > 0 ? (r.mochaQty/r.netSales*100).toFixed(1)+'%' : '0.0%',
      mtdNetSales: r.mtdNetSales||r.netSales, mtdBudget: r.mtdBudget||r.budgetSale,
      mtdDineIn: r.mtdDineIn||r.dineIn, mtdHomeDelivery: r.mtdHomeDelivery||r.homeDelivery,
      mtdGuestCount: r.mtdGuestCount||r.guestCount, mtdLtoSale: r.mtdLtoSale||r.ltoSale,
      mtdMochaQty: r.mtdMochaQty||r.mochaQty, mtdMochaPct: '', mtdFeedback: r.mtdFeedback||0,
      createdBy: currentUser?.username, storeCode: store.code, savedAt: new Date().toISOString()
    });
  });
  recalcAllMTDs(); saveAll(); loadHistory(); updateDashboard(); drawCharts(); loadBudget();
  toast(`✅ ${window._parsed.length} records imported`); $('bulkPreview').innerHTML = ''; window._parsed = null;
}
function recalcAllMTDs() {
  reports.sort((a,b) => new Date(a.date) - new Date(b.date));
  const map = {};
  reports.forEach(r => {
    const d = new Date(r.date), k = d.getFullYear()+'-'+(d.getMonth()+1);
    if (!map[k]) map[k] = {n:0,b:0,d:0,del:0,g:0,l:0,m:0};
    map[k].n+=r.netSales||0; map[k].b+=r.budgetSale||0; map[k].d+=r.dineIn||0;
    map[k].del+=r.homeDelivery||0; map[k].g+=r.guestCount||0; map[k].l+=r.ltoSale||0; map[k].m+=r.mochaQty||0;
    r.mtdNetSales=map[k].n; r.mtdBudget=map[k].b; r.mtdDineIn=map[k].d; r.mtdHomeDelivery=map[k].del;
    r.mtdGuestCount=map[k].g; r.mtdLtoSale=map[k].l; r.mtdMochaQty=map[k].m;
    r.mtdMochaPct = map[k].n > 0 ? (map[k].m/map[k].n*100).toFixed(1)+'%' : '0.0%';
    r.mochaPct = r.netSales > 0 ? (r.mochaQty/r.netSales*100).toFixed(1)+'%' : '0.0%';
  });
}

// ===== DASHBOARD =====
function getMonthReports(monthKey) {
  const key = monthKey || new Date().toISOString().slice(0,7);
  const reps = reports.filter(r => r.storeCode === store.code && r.date.startsWith(key));
  const map = {}; reps.forEach(r => { if (!map[r.date] || r.shift === 'Full Day') map[r.date] = r; });
  return Object.values(map).sort((a,b) => new Date(a.date) - new Date(b.date));
}
function updateDashboard() {
  const reps = getMonthReports();
  let tN=0, tB=0, tG=0, tDi=0, tDel=0, tLto=0, tM=0;
  reps.forEach(r => { tN+=r.netSales||0; tB+=r.budgetSale||0; tG+=r.guestCount||0; tDi+=r.dineIn||0; tDel+=r.homeDelivery||0; tLto+=r.ltoSale||0; tM+=r.mochaQty||0; });
  const variance = tN - tB, ach = tB > 0 ? Math.round(tN/tB*100) : 0;
  const bgt = budgets[new Date().toISOString().slice(0,7)] || {target:0};
  const tAch = bgt.target > 0 ? Math.round(tN/bgt.target*100) : 0;
  const achColor = ach >= 100 ? 'var(--accent)' : ach >= 80 ? 'var(--gold)' : 'var(--danger)';
  $('dashSummary').innerHTML = `
    <div class="kpi-grid">
      <div class="kpi-card highlight"><small>MTD Net Sales</small><b>${fmt(tN)}</b></div>
      <div class="kpi-card"><small>MTD Budget</small><b>${fmt(tB)}</b></div>
      <div class="kpi-card"><small>Variance</small><b style="color:${variance>=0?'var(--accent)':'var(--danger)'}">${variance>=0?'+':''}${fmt(variance)}</b></div>
      <div class="kpi-card"><small>Achievement</small><b style="color:${achColor}">${ach}%</b></div>
      <div class="kpi-card"><small>Monthly Target</small><b>${fmt(bgt.target)}</b></div>
      <div class="kpi-card"><small>Target Ach.</small><b style="color:${tAch>=100?'var(--accent)':tAch>=80?'var(--gold)':'var(--danger)'}">${tAch}%</b></div>
      <div class="kpi-card"><small>Total Guests</small><b>${tG}</b></div>
      <div class="kpi-card"><small>Mocha Qty</small><b>${tM}</b></div>
    </div>`;
  $('statReports').textContent = reports.filter(r => r.storeCode === store.code).length;
  $('statSales').textContent = tN >= 1000 ? (tN/1000).toFixed(1)+'K' : tN.toFixed(0);
  $('statAchievement').textContent = ach + '%';
  $('statGuests').textContent = tG;
  drawCharts(reps);
}
function drawCharts(reps) {
  if (!reps) reps = getMonthReports();
  const labels = reps.map(r => r.date.slice(5));
  const salesData = reps.map(r => r.netSales || 0);
  const budgetData = reps.map(r => r.budgetSale || 0);

  // Sales trend chart
  const c1 = $('salesChart');
  if (c1) {
    if (chartInstance) chartInstance.destroy();
    chartInstance = new Chart(c1.getContext('2d'), {
      type: 'line',
      data: { labels, datasets: [{
        label:'Net Sales', data: salesData,
        borderColor:'#00e5a0', backgroundColor:'rgba(0,229,160,0.08)',
        tension: 0.35, fill: true, pointBackgroundColor:'#00e5a0', pointRadius: 4
      }]},
      options: { responsive:true, maintainAspectRatio:true, plugins:{legend:{display:false}},
        scales:{ x:{grid:{color:'rgba(255,255,255,0.04)'},ticks:{color:'#8899b0',font:{size:10}}}, y:{grid:{color:'rgba(255,255,255,0.04)'},ticks:{color:'#8899b0',font:{size:10}}} } }
    });
  }

  // Budget comparison chart
  const c2 = $('budgetChart');
  if (c2) {
    if (budgetChartInstance) budgetChartInstance.destroy();
    budgetChartInstance = new Chart(c2.getContext('2d'), {
      type: 'bar',
      data: { labels, datasets: [
        { label:'Sales', data:salesData, backgroundColor:'rgba(0,229,160,0.7)', borderRadius:4 },
        { label:'Budget', data:budgetData, backgroundColor:'rgba(0,102,255,0.4)', borderRadius:4 }
      ]},
      options: { responsive:true, maintainAspectRatio:true,
        plugins:{legend:{labels:{color:'#8899b0',font:{size:10}}}},
        scales:{ x:{grid:{color:'rgba(255,255,255,0.04)'},ticks:{color:'#8899b0',font:{size:10}}}, y:{grid:{color:'rgba(255,255,255,0.04)'},ticks:{color:'#8899b0',font:{size:10}}} } }
    });
  }
}

// ===== MANAGEMENT REPORT =====
function showManagementReport() {
  const reps = getMonthReports(); if (!reps.length) return toast('No data for this month');
  let tN=0,tB=0,tDi=0,tDel=0,tG=0,tLto=0,tM=0;
  reps.forEach(r=>{tN+=r.netSales;tB+=r.budgetSale;tDi+=r.dineIn;tDel+=r.homeDelivery;tG+=r.guestCount;tLto+=r.ltoSale||0;tM+=r.mochaQty||0;});
  const v=tN-tB, ach=tB>0?Math.round(tN/tB*100):0, ac=tG>0?tN/tG:0;
  const best=reps.reduce((a,b)=>(a.netSales||0)>(b.netSales||0)?a:b);
  const worst=reps.reduce((a,b)=>(a.netSales||0)<(b.netSales||0)?a:b);
  const tMP=tN>0?(tM/tN*100).toFixed(1)+'%':'0.0%';
  const fb=reps.length>0?(reps[reps.length-1].mtdFeedback||0):0;
  const monthLabel = new Date().toLocaleDateString('en-US',{month:'long',year:'numeric'});

  $('reportContainer').innerHTML = `
    <h2 style="font-family:var(--font-display);color:var(--text);margin-bottom:4px;">📊 ${store.name}</h2>
    <p style="color:var(--text2);font-size:0.8rem;margin-bottom:16px;">${monthLabel} · Store ${store.code} · by SAIDUR RAHAMAN</p>
    <div class="kpi-grid">
      <div class="kpi-card highlight"><small>Total Net Sales</small><b>${fmt(tN)}</b></div>
      <div class="kpi-card"><small>Total Budget</small><b>${fmt(tB)}</b></div>
      <div class="kpi-card"><small>Variance</small><b style="color:${v>=0?'var(--accent)':'var(--danger)'}">${v>=0?'+':''}${fmt(v)}</b></div>
      <div class="kpi-card"><small>Achievement</small><b style="color:${ach>=100?'var(--accent)':ach>=80?'var(--gold)':'var(--danger)'}">${ach}%</b></div>
    </div>
    <h3 style="font-size:0.85rem;color:var(--text2);margin:16px 0 10px;text-transform:uppercase;letter-spacing:0.07em;">Channel Breakdown</h3>
    <table class="report-table">
      <tr><td>Dine IN</td><td>${fmt(tDi)} (${tN>0?Math.round(tDi/tN*100):0}%)</td></tr>
      <tr><td>Home Delivery</td><td>${fmt(tDel)} (${tN>0?Math.round(tDel/tN*100):0}%)</td></tr>
      <tr><td>Total Guests</td><td>${tG}</td></tr>
      <tr><td>AVG Check</td><td>${fmt(ac)}</td></tr>
      <tr><td>Total LTO Sale</td><td>${fmt(tLto)}</td></tr>
      <tr><td>Total Mocha Qty</td><td>${tM}</td></tr>
      <tr><td>Total Mocha %</td><td>${tMP}</td></tr>
      <tr><td>Customer Feedback</td><td>${fb} / 5.0</td></tr>
    </table>
    <h3 style="font-size:0.85rem;color:var(--text2);margin:16px 0 10px;text-transform:uppercase;letter-spacing:0.07em;">Highlights</h3>
    <p style="font-size:0.85rem;margin-bottom:6px;">🌟 Best day: <b>${best.date} (${best.shift})</b> — ${fmt(best.netSales)}</p>
    <p style="font-size:0.85rem;margin-bottom:16px;">📉 Lowest day: <b>${worst.date} (${worst.shift})</b> — ${fmt(worst.netSales)}</p>
    <h3 style="font-size:0.85rem;color:var(--text2);margin:16px 0 10px;text-transform:uppercase;letter-spacing:0.07em;">Daily Log with MTD</h3>
    <div style="overflow-x:auto;">
    <table class="report-table">
      <tr><th>Date</th><th>Shift</th><th>Net</th><th>Budget</th><th>Var</th><th>%</th><th>Dine IN</th><th>Delivery</th><th>Guests</th><th>AVG</th><th>LTO</th><th>Mocha</th><th>MTD Net</th><th>MTD Bud</th><th>MTD %</th><th>Feedback</th></tr>
      ${reps.map(r=>{const v2=(r.netSales||0)-(r.budgetSale||0);const p=r.budgetSale>0?Math.round(r.netSales/r.budgetSale*100):0;const a=r.guestCount>0?r.netSales/r.guestCount:0;return `<tr><td>${r.date}</td><td>${r.shift}</td><td>${fmt(r.netSales)}</td><td>${fmt(r.budgetSale)}</td><td style="color:${v2>=0?'#00e5a0':'#ff4d6d'}">${v2>=0?'+':''}${fmt(v2)}</td><td>${p}%</td><td>${fmt(r.dineIn)}</td><td>${fmt(r.homeDelivery)}</td><td>${r.guestCount}</td><td>${fmt(a)}</td><td>${fmt(r.ltoSale||0)}</td><td>${r.mochaQty||0} (${r.mochaPct||''})</td><td>${fmt(r.mtdNetSales)}</td><td>${fmt(r.mtdBudget)}</td><td>${r.mtdBudget>0?Math.round(r.mtdNetSales/r.mtdBudget*100):0}%</td><td>${r.mtdFeedback||0}/5</td></tr>`;}).join('')}
    </table></div>`;
  $('managementReportModal').classList.add('active');
}
function showExecutivePresentation() {
  const reps = getMonthReports(); if (!reps.length) return toast('No data');
  let tN = 0; reps.forEach(r => tN += r.netSales);
  const bgt = budgets[new Date().toISOString().slice(0,7)]||{target:0,days:30};
  const tAch = bgt.target > 0 ? Math.round(tN/bgt.target*100) : 0;
  const avgD = tN / reps.length, proj = avgD * (bgt.days||30);
  $('executiveContainer').innerHTML = `
    <h2 style="font-family:var(--font-display);color:var(--text);margin-bottom:4px;">📊 Executive Presentation</h2>
    <p style="color:var(--text2);font-size:0.8rem;margin-bottom:16px;">${store.name} · Prepared by SAIDUR RAHAMAN · ${new Date().toLocaleDateString()}</p>
    <div class="kpi-grid">
      <div class="kpi-card highlight"><small>Current MTD Sales</small><b>${fmt(tN)}</b></div>
      <div class="kpi-card"><small>Monthly Target</small><b>${fmt(bgt.target)}</b></div>
      <div class="kpi-card"><small>Achievement</small><b style="color:${tAch>=100?'var(--accent)':tAch>=80?'var(--gold)':'var(--danger)'}">${tAch}%</b></div>
      <div class="kpi-card"><small>Projected EOM</small><b>${fmt(proj)}</b></div>
    </div>
    <h3 style="font-size:0.85rem;color:var(--text2);margin:16px 0 10px;text-transform:uppercase;letter-spacing:0.07em;">Daily Performance</h3>
    ${reps.map(r => {
      const dailyT = bgt.target > 0 && bgt.days > 0 ? bgt.target/bgt.days : 0;
      const pct = dailyT > 0 ? Math.min(100,(r.netSales||0)/dailyT*100) : Math.min(100,(r.netSales||0)/5000*100);
      const color = pct >= 100 ? 'var(--accent)' : pct >= 80 ? 'var(--gold)' : 'var(--danger)';
      return `<div style="margin-bottom:8px;">
        <div style="display:flex;justify-content:space-between;font-size:0.75rem;color:var(--text2);margin-bottom:4px;"><span>${r.date} · ${r.shift}</span><span style="color:${color}">${fmt(r.netSales)}</span></div>
        <div class="progress-track"><div class="progress-fill" style="width:${pct}%;background:${color};"></div></div>
      </div>`;
    }).join('')}`;
  $('executiveModal').classList.add('active');
}
function downloadManagementPDF() { html2pdf().set({filename:'Monthly_Report.pdf',margin:8}).from($('managementReportContent')).save(); }
function downloadExecutivePDF() { html2pdf().set({filename:'Executive_Presentation.pdf',margin:8}).from($('executiveContent')).save(); }

// ===== BUDGET =====
function loadBudget() {
  const key = $('budgetMonth').value;
  const b = budgets[key] || {target:0,days:30};
  $('budgetTarget').value = b.target;
  $('budgetDays').value = b.days;
  const reps = getMonthReports(key);
  let achieved = 0; reps.forEach(r => achieved += r.netSales||0);
  const pct = b.target > 0 ? Math.min(100, Math.round(achieved/b.target*100)) : 0;
  const fillColor = pct >= 100 ? 'linear-gradient(90deg,#00b87a,var(--accent))' : pct >= 80 ? 'linear-gradient(90deg,#e67e00,var(--gold))' : 'linear-gradient(90deg,#cc0033,var(--danger))';
  $('budgetProgressFill').style.width = pct + '%';
  $('budgetProgressFill').style.background = fillColor;
  $('budgetAchieved').textContent = fmt(achieved);
  $('budgetTargetDisplay').textContent = fmt(b.target);
  $('budgetPercent').textContent = pct;
  const dailyTarget = b.target > 0 && b.days > 0 ? b.target/b.days : 0;
  if (!reps.length) { $('budgetDailyComparison').innerHTML = '<div class="empty-state"><div class="empty-state-icon">📋</div><p>No reports for this month</p></div>'; return; }
  $('budgetDailyComparison').innerHTML = reps.map(r => {
    const vs = (r.netSales||0) - dailyTarget;
    const vp = dailyTarget > 0 ? Math.round((r.netSales||0)/dailyTarget*100) : 0;
    const color = vs >= 0 ? 'var(--accent)' : 'var(--danger)';
    const barW = Math.min(100, vp);
    return `<div class="budget-row">
      <span style="color:var(--text2);font-size:0.78rem;">${r.date}</span>
      <span style="font-family:var(--font-mono);font-size:0.8rem;">${fmt(r.netSales)}</span>
      <span style="color:${color};font-size:0.78rem;font-weight:600;">${vs>=0?'+':''}${fmt(vs)} (${vp}%)</span>
    </div>`;
  }).join('');
}
function saveBudget() {
  const key = $('budgetMonth').value;
  budgets[key] = {target: val('budgetTarget'), days: int('budgetDays')||30};
  saveAll(); loadBudget();
}
function uploadBudgetCSV() {
  const inp = document.createElement('input'); inp.type='file'; inp.accept='.csv';
  inp.onchange = e => {
    const r = new FileReader();
    r.onload = ev => {
      ev.target.result.split('\n').forEach(line => { const [m,t,d]=line.split(','); if(m&&t) budgets[m.trim()]={target:parseFloat(t),days:parseInt(d)||30}; });
      saveAll(); loadBudget(); toast('✅ Budget uploaded');
    };
    r.readAsText(e.target.files[0]);
  };
  inp.click();
}
function downloadBudgetTemplate() {
  const blob = new Blob(['Month,Target,Days\n2026-05,50000,30'], {type:'text/csv'});
  const a = document.createElement('a'); a.href=URL.createObjectURL(blob); a.download='budget_template.csv'; a.click();
}

// ===== HISTORY =====
function loadHistory() {
  const storeReps = reports.filter(r => r.storeCode === store.code).slice(0, 50);
  if (!storeReps.length) { $('historyList').innerHTML = '<div class="empty-state"><div class="empty-state-icon">📋</div><p>No reports yet. Add your first report!</p></div>'; return; }
  $('historyList').innerHTML = storeReps.map(r => {
    const ach = r.budgetSale > 0 ? Math.round(r.netSales/r.budgetSale*100) : 0;
    const achClass = ach >= 100 ? 'good' : ach >= 80 ? '' : 'bad';
    const v = r.netSales - r.budgetSale;
    return `<div class="history-item">
      <div style="min-width:70px;">
        <div class="history-item-date">${r.date.slice(5)}</div>
        <div style="margin-top:4px;"><span class="history-item-shift">${r.shift}</span></div>
      </div>
      <div class="history-item-info">
        <span class="history-chip">💰 ${fmt(r.netSales)}</span>
        <span class="history-chip ${achClass}">🎯 ${ach}%</span>
        <span class="history-chip ${v>=0?'good':'bad'}">${v>=0?'▲':'▼'} ${fmt(Math.abs(v))}</span>
        <span class="history-chip">👥 ${r.guestCount}</span>
        <span class="history-chip">☕ ${r.mochaQty||0}</span>
        ${r.mtdFeedback ? `<span class="history-chip">⭐ ${r.mtdFeedback}/5</span>` : ''}
      </div>
      <div class="history-item-actions">
        <button class="btn btn-ghost" onclick="editReport('${r.id}')">✏️</button>
        <button class="btn btn-whatsapp" onclick="shareSaved('${r.id}')">📤</button>
        <button class="btn btn-danger" onclick="deleteReport('${r.id}')">🗑</button>
      </div>
    </div>`;
  }).join('');
}
function editReport(id) {
  const r = reports.find(x => x.id===id && x.storeCode===store.code); if (!r) return;
  $('dateInput').value=r.date; $('shiftInput').value=r.shift;
  $('netSales').value=r.netSales; $('budgetSale').value=r.budgetSale;
  $('homeDelivery').value=r.homeDelivery; $('guestCount').value=r.guestCount;
  $('ltoSale').value=r.ltoSale||0; $('mochaQty').value=r.mochaQty||0;
  $('mtdFeedback').value=r.mtdFeedback||0;
  manualDineIn = true; liveCalc(); editId = id; toggleEditMode(true); switchTab('entry');
  toast('📝 Editing report — make changes and click Update');
}
function shareSaved(id) {
  const r = reports.find(x => x.id===id && x.storeCode===store.code); if (!r) return;
  const snap = {date:$('dateInput').value,shift:$('shiftInput').value,net:$('netSales').value,bud:$('budgetSale').value,del:$('homeDelivery').value,guest:$('guestCount').value,lto:$('ltoSale').value,mocha:$('mochaQty').value,fb:$('mtdFeedback').value};
  $('dateInput').value=r.date; $('shiftInput').value=r.shift; $('netSales').value=r.netSales; $('budgetSale').value=r.budgetSale; $('homeDelivery').value=r.homeDelivery; $('guestCount').value=r.guestCount; $('ltoSale').value=r.ltoSale||0; $('mochaQty').value=r.mochaQty||0; $('mtdFeedback').value=r.mtdFeedback||0;
  liveCalc(); shareWhatsApp();
  $('dateInput').value=snap.date; $('shiftInput').value=snap.shift; $('netSales').value=snap.net; $('budgetSale').value=snap.bud; $('homeDelivery').value=snap.del; $('guestCount').value=snap.guest; $('ltoSale').value=snap.lto; $('mochaQty').value=snap.mocha; $('mtdFeedback').value=snap.fb;
  liveCalc();
}
function deleteReport(id) {
  if (!confirm('Delete this report? This cannot be undone.')) return;
  reports = reports.filter(r => r.id !== id); saveAll();
  if (editId === id) { editId = null; toggleEditMode(false); }
  loadHistory(); updateDashboard(); drawCharts(); loadBudget(); toast('🗑 Report deleted');
}
function exportCSV() {
  let csv = 'Date,Shift,Net Sales,Budget,Variance,Dine IN,Delivery,Guests,AVG Check,LTO,Mocha Qty,Mocha %,MTD Net,MTD Budget,MTD %,Feedback\n';
  reports.filter(r=>r.storeCode===store.code).forEach(r => {
    const v=r.netSales-r.budgetSale, ac=r.guestCount>0?r.netSales/r.guestCount:0;
    const mp=r.mtdBudget>0?Math.round(r.mtdNetSales/r.mtdBudget*100):0;
    csv += `${r.date},${r.shift},${r.netSales},${r.budgetSale},${v},${r.dineIn},${r.homeDelivery},${r.guestCount},${ac.toFixed(2)},${r.ltoSale||0},${r.mochaQty||0},${r.mochaPct||''},${r.mtdNetSales||0},${r.mtdBudget||0},${mp}%,${r.mtdFeedback||0}\n`;
  });
  const blob = new Blob([csv], {type:'text/csv'});
  const a = document.createElement('a'); a.href=URL.createObjectURL(blob); a.download='sales_history.csv'; a.click();
}
function downloadHistoryPDF() { html2pdf().set({filename:'Sales_History.pdf',margin:8}).from($('historyCard')).save(); }

// ===== USER MANAGEMENT =====
function renderUserManagement() {
  const list = $('userManagementList'); if (!list) return;
  list.innerHTML = users.map(u => `
    <div class="user-row">
      <div class="user-info">
        <div class="user-name">${u.username} <span class="status-pill ${u.status}">${u.status}</span></div>
        <div class="user-meta">Role: ${u.role} · Code: ${u.password}</div>
      </div>
      <div style="display:flex;gap:5px;">
        ${u.status === 'pending' ? `<button class="btn btn-success" style="padding:6px 10px;font-size:0.72rem;" onclick="approveUser('${u.username}')">✅</button>` : ''}
        ${u.username !== 'admin' ? `<button class="btn btn-danger" style="padding:6px 10px;font-size:0.72rem;" onclick="removeUser('${u.username}')">🗑</button>` : ''}
      </div>
    </div>`).join('');
}
function approveUser(username) { const u=users.find(x=>x.username===username); if(u){u.status='active';saveUsers();renderUserManagement();toast('✅ User approved');} }
function removeUser(username) { if(!confirm('Remove user '+username+'?')) return; users=users.filter(u=>u.username!==username); saveUsers(); renderUserManagement(); toast('User removed'); }

// ===== SETTINGS =====
function openSettings() { if(currentUser?.role!=='admin') return; $('settingsModal').classList.add('active'); renderUserManagement(); }
function closeModal(id) { $(id).classList.remove('active'); }
function changePassword() {
  const old=$('oldPass').value, np=$('newPass').value;
  const user=users.find(u=>u.username===currentUser.username);
  if(!user||user.password!==old) return toast('❌ Wrong current password');
  if(!np||np.length<3) return toast('⚠️ New password too short');
  user.password=np; saveUsers(); toast('✅ Password updated'); closeModal('settingsModal');
}
function backupData() {
  const blob=new Blob([JSON.stringify({store,reports,budgets,users,exportedAt:new Date().toISOString()})],{type:'application/json'});
  const a=document.createElement('a'); a.href=URL.createObjectURL(blob); a.download=`sales_backup_${new Date().toISOString().slice(0,10)}.json`; a.click();
}
function restoreData() {
  const file=$('restoreFile').files[0]; if(!file) return;
  const r=new FileReader();
  r.onload=e=>{
    try {
      const d=JSON.parse(e.target.result);
      if(d.store) store=d.store; if(d.reports) reports=d.reports;
      if(d.budgets) budgets=d.budgets; if(d.users) users=d.users;
      saveAll(); saveUsers(); refreshUI(); toast('✅ Data restored successfully');
    } catch { toast('❌ Invalid backup file'); }
  };
  r.readAsText(file);
}
function resetSystem() { if(confirm('⚠️ Delete ALL data permanently? This cannot be undone!')) { localStorage.clear(); location.reload(); } }

// ===== TABS =====
function switchTab(name) {
  document.querySelectorAll('.tab-content').forEach(el => el.classList.remove('active'));
  document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
  const tab = $(`tab-${name}`); if(tab) tab.classList.add('active');
  const btn = document.querySelector(`.tab-btn[onclick="switchTab('${name}')"]`); if(btn) btn.classList.add('active');
  if (name === 'dashboard') { updateDashboard(); drawCharts(); }
  if (name === 'budget') loadBudget();
  if (name === 'history') loadHistory();
  if (name === 'preview') updatePreview();
}

// ===== EXPOSE GLOBALS =====
Object.assign(window, {handleLogin,forgotPassword,handleLogout,openSettings,closeModal,approveUser,removeUser,recalc,liveCalc,overrideDineIn,smartLoadMTD,saveReport,updateReport,cancelEdit,clearForm,shareWhatsApp,copyToClipboard,downloadReportTxt,downloadPDF,setBulkMode,parseAndImport,confirmImport,showManagementReport,showExecutivePresentation,downloadManagementPDF,downloadExecutivePDF,loadBudget,saveBudget,uploadBudgetCSV,downloadBudgetTemplate,editReport,shareSaved,deleteReport,exportCSV,downloadHistoryPDF,changePassword,backupData,restoreData,resetSystem,switchTab,installApp});

// ===== INIT =====
if (currentUser) {
  $('loginScreen').style.display = 'none';
  $('appScreen').style.display = 'block';
  $('headerUserBadge').textContent = '🏬 ' + store.name;
  if (currentUser.role === 'admin') { $('settingsBtn').style.display = 'inline-flex'; $('adminSettings').style.display = 'block'; }
  refreshUI();
}
</script>
</body>
</html>
