<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1">
<title>Sistem Umum dan Kepegawaian</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&family=Source+Serif+4:opsz,wght@8..60,400;8..60,600&display=swap" rel="stylesheet">
<style>
:root{
  --navy:#0f4069;
  --navy-deep:#082a47;
  --navy-mid:#1b91ce;
  --gold:#fdc32e;
  --gold-dark:#bb6328;
  --gold-soft:#fbe6ab;
  --green:#8ec643;
  --app-bg:#eef2f6;
  --paper:#fbf9f2;
  --paper-edge:#eee7d3;
  --ink:#241f18;
  --muted:#7c7365;
  --surface:#ffffff;
  --line:#dbe3ea;
  --danger:#a8402a;
  --ok:#3d6b4f;
  --radius:14px;
}
*{box-sizing:border-box;}
html,body{margin:0;padding:0;}
body{
  background:var(--navy-deep);
  color:var(--ink);
  font-family:'Plus Jakarta Sans',system-ui,sans-serif;
  -webkit-font-smoothing:antialiased;
  min-height:100vh;
}
button{font-family:inherit;}
#app{
  max-width:560px;
  margin:0 auto;
  min-height:100vh;
  background:var(--app-bg);
  display:flex;
  flex-direction:column;
  position:relative;
  box-shadow:0 0 60px rgba(0,0,0,.35);
  overflow-x:hidden;
}
.app-watermark{
  position:fixed; inset:0; max-width:560px; margin:0 auto; pointer-events:none; z-index:0;
  background-repeat:no-repeat; background-position:center 120px; background-size:340px;
  opacity:.06;
}
main{position:relative; z-index:1;}

/* ---------- Side menu (drawer) ---------- */
.drawer-backdrop{position:fixed; inset:0; background:rgba(5,20,35,.55); z-index:90;}
.drawer{
  position:fixed; top:0; left:0; bottom:0; width:78%; max-width:290px; z-index:91;
  background:linear-gradient(175deg,var(--navy-mid) 0%,var(--navy) 45%,var(--navy-deep) 100%);
  color:#fff; display:flex; flex-direction:column; box-shadow:6px 0 24px rgba(0,0,0,.35);
  animation:drawerIn .18s ease-out;
}
@keyframes drawerIn{from{transform:translateX(-100%);} to{transform:translateX(0);}}
.drawer-head{padding:22px 18px 16px; border-bottom:1px solid rgba(255,255,255,.15); display:flex; align-items:center; gap:12px;}
.drawer-head img{width:44px; height:44px; object-fit:contain; background:#fff; border-radius:10px; padding:4px; flex-shrink:0;}
.drawer-head .dh-text{min-width:0;}
.drawer-head .dh-text .dh-eyebrow{font-size:9.5px; font-weight:700; text-transform:uppercase; letter-spacing:.6px; color:var(--gold-soft); opacity:.9; line-height:1.3;}
.drawer-head .dh-text h2{margin:2px 0 0; font-size:14px; font-weight:800; line-height:1.3;}
.drawer-close{position:absolute; top:14px; right:12px; background:rgba(255,255,255,.14); border:none; color:#fff; width:28px; height:28px; border-radius:8px; display:flex; align-items:center; justify-content:center; cursor:pointer;}
.drawer-nav{flex:1; padding:10px 10px; overflow-y:auto;}
.drawer-item{
  display:flex; align-items:center; gap:12px; width:100%; background:none; border:none; color:#fff;
  padding:12px 12px; border-radius:10px; font-size:13.5px; font-weight:600; cursor:pointer; text-align:left;
}
.drawer-item:active, .drawer-item.active{background:rgba(255,255,255,.14);}
.drawer-item .di-icon{width:20px; flex-shrink:0; display:flex; align-items:center; justify-content:center; color:var(--gold-soft);}
.drawer-section{font-size:10px; font-weight:700; text-transform:uppercase; letter-spacing:1px; color:var(--gold-soft); opacity:.75; padding:14px 12px 6px;}
.drawer-subsection{font-size:9.5px; font-weight:700; text-transform:uppercase; letter-spacing:.6px; color:rgba(255,255,255,.5); padding:9px 12px 3px;}
.di-code{
  width:20px; height:20px; border-radius:5px; background:rgba(255,255,255,.14); color:var(--gold-soft);
  font-family:'Source Serif 4',serif; font-size:9.5px; font-weight:700; display:flex; align-items:center; justify-content:center;
}
.di-chevron{margin-left:auto; display:flex; align-items:center; justify-content:center; transition:transform .2s ease; color:rgba(255,255,255,.6); flex-shrink:0;}
.di-chevron.open{transform:rotate(180deg);}
.drawer-submenu{max-height:0; overflow:hidden; transition:max-height .25s ease;}
.drawer-submenu.open{max-height:600px;}
.drawer-foot{padding:14px 18px; border-top:1px solid rgba(255,255,255,.15); font-size:10.5px; color:rgba(255,255,255,.65); line-height:1.5;}

/* ---------- App bar ---------- */
.appbar{
  background:linear-gradient(160deg,var(--navy-mid) 0%,var(--navy) 55%,var(--navy-deep) 100%);
  color:#fff;
  padding:16px 18px 0;
  position:sticky; top:0; z-index:40;
  box-shadow:0 2px 10px rgba(0,0,0,.25);
}
.appbar-gold-strip{height:4px; margin:0 -18px 0; background:linear-gradient(90deg,var(--gold-dark),var(--gold) 45%,var(--green) 100%);}
.appbar-row{display:flex; align-items:center; gap:10px; padding-bottom:14px;}
.appbar-masthead{font-size:9.5px; font-weight:700; letter-spacing:.8px; text-transform:uppercase; color:var(--gold-soft); opacity:.9; margin:0 0 3px; white-space:nowrap; overflow:hidden; text-overflow:ellipsis;}
.appbar-logo{width:32px; height:32px; object-fit:contain; flex-shrink:0; background:#fff; border-radius:8px; padding:3px;}
.appbar-back{
  background:rgba(255,255,255,.12); border:none; color:#fff;
  width:34px; height:34px; border-radius:10px; display:flex; align-items:center; justify-content:center;
  cursor:pointer; flex-shrink:0;
}
.appbar-back:active{background:rgba(255,255,255,.24);}
.appbar-title{flex:1; min-width:0;}
.appbar-title h1{font-size:16px; margin:0; font-weight:800; letter-spacing:.2px;}
.appbar-title p{margin:2px 0 0; font-size:11.5px; color:var(--gold-soft); font-weight:500; letter-spacing:.3px; text-transform:uppercase;}
.appbar-icon{
  background:rgba(255,255,255,.14); border:1px solid rgba(255,255,255,.18); color:#fff;
  width:34px; height:34px; border-radius:10px; display:flex; align-items:center; justify-content:center;
  cursor:pointer; flex-shrink:0;
}
.appbar-icon:active{background:rgba(255,255,255,.26);}
.eyebrow{
  display:inline-block; font-size:10.5px; font-weight:700; letter-spacing:1px; text-transform:uppercase;
  color:var(--gold); margin-bottom:6px;
}

/* ---------- Main ---------- */
main{flex:1; padding:18px 16px 100px;}
.section-label{
  font-size:11px; font-weight:800; text-transform:uppercase; letter-spacing:1.1px;
  color:var(--navy); margin:24px 2px 10px; padding-left:10px;
  border-left:4px solid var(--gold); line-height:1.3;
}
.section-label:first-child{margin-top:2px;}
.cat-desc{font-size:12px; color:var(--muted); margin:-6px 2px 12px 12px; line-height:1.5;}

.type-grid{display:flex; flex-direction:column; gap:10px;}
.type-card{
  background:var(--surface); border:1px solid var(--line); border-radius:var(--radius);
  padding:14px 14px; display:flex; align-items:center; gap:13px; cursor:pointer;
  text-align:left; width:100%; transition:transform .12s ease, box-shadow .12s ease;
}
.type-card:active{transform:scale(.98);}
.type-badge{
  width:42px; height:42px; border-radius:10px; flex-shrink:0;
  background:linear-gradient(160deg,var(--navy-mid),var(--navy)); color:var(--gold-soft);
  display:flex; align-items:center; justify-content:center; border:1px solid var(--gold-dark);
  font-family:'Source Serif 4',serif; font-weight:600; font-size:14px;
}
.type-info{flex:1; min-width:0;}
.type-info h3{margin:0 0 2px; font-size:14.5px; font-weight:700; color:var(--ink);}
.type-info p{margin:0; font-size:12px; color:var(--muted); line-height:1.4;}
.chev{color:var(--line); flex-shrink:0;}

.hero{
  background:linear-gradient(135deg,var(--navy-mid) 0%,var(--navy) 55%,var(--navy-deep) 100%);
  border-radius:var(--radius);
  padding:18px 16px; margin-bottom:4px; position:relative; overflow:hidden;
  box-shadow:0 6px 18px rgba(10,61,102,.25);
}
.hero::after{content:''; position:absolute; right:-30px; top:-30px; width:120px; height:120px; border-radius:50%; background:radial-gradient(circle,rgba(217,161,37,.28),transparent 70%);}
.hero .eyebrow{color:var(--gold-soft); position:relative;}
.hero p{margin:0; font-size:12.5px; line-height:1.6; color:rgba(255,255,255,.88); position:relative;}
.hero strong{color:#fff;}

.welcome-hero{
  background:linear-gradient(160deg,var(--navy-mid) 0%,var(--navy) 55%,var(--navy-deep) 100%);
  border-radius:18px; padding:28px 20px 20px; margin-bottom:6px; position:relative; overflow:hidden;
  text-align:center; box-shadow:0 10px 26px rgba(8,42,71,.35); border:1px solid rgba(255,255,255,.08);
}
.welcome-hero::before{content:''; position:absolute; left:-40px; bottom:-50px; width:160px; height:160px; border-radius:50%; background:radial-gradient(circle,rgba(142,198,67,.22),transparent 70%);}
.welcome-hero::after{content:''; position:absolute; right:-36px; top:-36px; width:140px; height:140px; border-radius:50%; background:radial-gradient(circle,rgba(253,195,46,.25),transparent 70%);}
.wh-ring{
  width:72px; height:72px; margin:0 auto 14px; border-radius:50%; padding:5px; position:relative;
  background:conic-gradient(from 0deg,var(--gold),var(--green),var(--navy-mid),var(--gold));
  display:flex; align-items:center; justify-content:center;
}
.wh-logo{width:100%; height:100%; object-fit:contain; background:#fff; border-radius:50%; padding:8px;}
.wh-greeting{position:relative; font-size:10.5px; font-weight:700; letter-spacing:1.4px; text-transform:uppercase; color:var(--gold-soft);}
.wh-title{position:relative; margin:5px 0 0; font-size:21px; font-weight:800; color:#fff; letter-spacing:.2px;}
.wh-unit{position:relative; margin-top:3px; font-size:12.5px; font-weight:600; color:rgba(255,255,255,.85); text-transform:uppercase; letter-spacing:.3px;}
.wh-divider{position:relative; width:44px; height:3px; margin:14px auto 12px; border-radius:2px; background:linear-gradient(90deg,var(--gold),var(--green));}
.wh-date{position:relative; font-size:11.5px; color:rgba(255,255,255,.7); margin-bottom:16px;}
.wh-stats{position:relative; display:flex; justify-content:center; gap:10px;}
.wh-stat{
  flex:1; max-width:110px; background:rgba(255,255,255,.08); border:1px solid rgba(255,255,255,.14);
  border-radius:12px; padding:10px 6px; cursor:pointer; font-family:inherit;
}
.wh-stat:active{background:rgba(255,255,255,.16);}
.wh-num{font-size:18px; font-weight:800; color:var(--gold-soft); line-height:1;}
.wh-label{font-size:9.5px; color:rgba(255,255,255,.75); margin-top:4px; text-transform:uppercase; letter-spacing:.4px; line-height:1.3;}

/* ---------- Login ---------- */
.login-screen{
  min-height:100vh; display:flex; align-items:center; justify-content:center; padding:24px 20px;
  background:linear-gradient(160deg,var(--navy-mid) 0%,var(--navy) 55%,var(--navy-deep) 100%);
  position:relative; z-index:1;
}
.login-card{
  background:rgba(255,255,255,.07); border:1px solid rgba(255,255,255,.16); border-radius:20px;
  padding:34px 26px 28px; max-width:360px; width:100%; text-align:center;
  box-shadow:0 20px 50px rgba(0,0,0,.35); position:relative; z-index:1;
}
.login-eyebrow{font-size:10px; font-weight:700; letter-spacing:1px; text-transform:uppercase; color:var(--gold-soft); margin-bottom:5px; opacity:.9;}
.login-title{font-size:18px; font-weight:800; color:#fff; margin:0 0 6px; line-height:1.35;}
.login-sub{font-size:12.5px; color:rgba(255,255,255,.72); margin:0 0 20px; line-height:1.5;}
.login-error{background:rgba(200,80,60,.22); border:1px solid rgba(232,120,100,.45); color:#ffdcd3; font-size:12px; padding:9px 11px; border-radius:9px; margin-bottom:14px; text-align:left;}
.login-card .field{text-align:left; margin-bottom:14px;}
.login-card .field label{color:rgba(255,255,255,.85); font-size:12px; font-weight:600; display:block; margin-bottom:5px;}
.login-card .field input{width:100%; border:1px solid rgba(255,255,255,.25); border-radius:9px; padding:11px 12px; font-size:14px; background:rgba(255,255,255,.95); color:var(--ink); font-family:inherit;}
.login-foot{margin-top:16px; font-size:10.5px; color:rgba(255,255,255,.5); line-height:1.5;}

.alert-banner{
  display:flex; align-items:center; gap:11px; border-radius:12px; padding:12px 13px; margin:10px 0 4px; cursor:pointer;
  border:1px solid; text-align:left; width:100%; background:none; font-family:inherit;
}
.alert-banner.overdue{background:#fbe4de; border-color:#e8b6a8; color:#8a301c;}
.alert-banner.soon{background:#fdf1d6; border-color:#eecf8e; color:#7a5410;}
.alert-banner .ab-icon{width:34px; height:34px; border-radius:9px; flex-shrink:0; display:flex; align-items:center; justify-content:center; background:rgba(255,255,255,.55);}
.alert-banner .ab-text{flex:1; min-width:0;}
.alert-banner .ab-text strong{display:block; font-size:12.5px; font-weight:800;}
.alert-banner .ab-text span{display:block; font-size:11px; opacity:.85; margin-top:1px;}

.peg-alert-chip{display:inline-flex; align-items:center; font-size:9.5px; font-weight:700; padding:3px 8px; border-radius:20px; margin-top:5px; margin-right:5px;}
.peg-alert-chip.overdue{background:#fbdcd3; color:#a8402a;}
.peg-alert-chip.soon{background:#fdecc8; color:#8a5a10;}

.draft-card{
  background:var(--surface); border:1px solid var(--line); border-left:3px solid var(--gold); border-radius:12px;
  padding:12px 14px; display:flex; align-items:center; gap:10px; margin-bottom:8px;
}
.draft-info{flex:1; min-width:0;}
.draft-info h4{margin:0 0 2px; font-size:13.5px; font-weight:700; white-space:nowrap; overflow:hidden; text-overflow:ellipsis;}
.draft-info p{margin:0; font-size:11px; color:var(--muted);}
.icon-btn{
  background:var(--app-bg); border:1px solid var(--line); color:var(--navy);
  width:32px; height:32px; border-radius:8px; display:flex; align-items:center; justify-content:center; cursor:pointer;
}
.icon-btn.danger{color:var(--danger);}

/* ---------- Form ---------- */
.form-block{
  background:var(--surface); border:1px solid var(--line); border-radius:var(--radius);
  padding:16px; margin-bottom:14px;
}
.form-block h2{font-size:13px; margin:0 0 12px; font-weight:700; color:var(--navy); display:flex; align-items:center; gap:7px;}
.form-block h2 .num{
  width:20px; height:20px; border-radius:50%; background:var(--navy); color:#fff; font-size:11px;
  display:flex; align-items:center; justify-content:center; flex-shrink:0;
}
.field{margin-bottom:13px;}
.field:last-child{margin-bottom:0;}
.field label{display:block; font-size:12px; font-weight:600; color:var(--ink); margin-bottom:5px;}
.field .hint{display:block; font-size:11px; color:var(--muted); font-weight:400; margin-top:4px;}
.field input[type=text], .field input[type=date], .field textarea, .field select{
  width:100%; border:1px solid var(--line); border-radius:9px; padding:10px 11px;
  font-family:inherit; font-size:13.5px; color:var(--ink); background:#fff;
}
.field textarea{resize:vertical; min-height:64px; line-height:1.5;}
.field input:focus, .field textarea:focus, .field select:focus{outline:2px solid var(--navy); outline-offset:1px;}
.row2{display:flex; gap:10px;}
.row2 .field{flex:1;}

.list-editor .list-item{display:flex; gap:8px; align-items:flex-start; margin-bottom:7px;}
.list-editor .list-item span.bullet{
  width:22px; height:36px; display:flex; align-items:center; justify-content:center;
  font-size:12px; color:var(--muted); font-weight:700; flex-shrink:0;
}
.list-editor textarea{flex:1; min-height:36px;}
.list-remove{
  background:none; border:none; color:var(--danger); cursor:pointer; padding:6px; flex-shrink:0;
}
.add-btn{
  display:flex; align-items:center; gap:6px; background:none; border:1.5px dashed var(--line);
  color:var(--navy); font-weight:700; font-size:12.5px; padding:9px 12px; border-radius:9px; cursor:pointer; width:100%;
  justify-content:center; margin-top:2px;
}
.add-btn:active{background:var(--gold-soft);}

.petugas-card{border:1px solid var(--line); border-radius:10px; padding:11px; margin-bottom:9px; position:relative; background:#fcfbf8;}
.petugas-card .list-remove{position:absolute; top:8px; right:8px;}
.petugas-card .field{margin-bottom:8px;}

.helper-note{
  display:flex; gap:8px; background:#f1ede0; border:1px solid var(--gold-soft); border-radius:10px;
  padding:10px 11px; font-size:11.5px; color:#6b5a2c; line-height:1.5; margin-bottom:14px;
}

/* ---------- Buttons ---------- */
.btn{
  border:none; border-radius:11px; padding:13px 16px; font-weight:700; font-size:14px; cursor:pointer;
  display:flex; align-items:center; justify-content:center; gap:8px; width:100%;
}
.btn-primary{background:linear-gradient(135deg,var(--gold) 0%,var(--gold-dark) 100%); color:var(--navy-deep); box-shadow:0 3px 10px rgba(169,122,18,.35);}
.btn-primary:active{filter:brightness(.94);}
.btn-secondary{background:#fff; color:var(--navy); border:1.5px solid var(--navy);}
.btn-ghost{background:transparent; color:var(--muted); font-weight:600;}

.bottom-bar{
  position:sticky; bottom:0; background:linear-gradient(0deg,var(--app-bg) 60%,rgba(238,242,246,0));
  padding:16px 16px 18px; display:flex; gap:10px; z-index:30;
}
.bottom-bar .btn{width:auto; flex:1;}

/* ---------- Preview / paper ---------- */
.paper-wrap{padding:2px 2px 4px;}
.paper{
  background:var(--paper);
  border:1px solid var(--paper-edge);
  box-shadow:0 10px 30px rgba(23,50,79,.18);
  border-radius:4px;
  padding:26px 20px;
  font-family:'Bookman Old Style', 'URW Bookman', 'Bookman', Georgia, 'Times New Roman', serif;
  color:#1c1c1c;
  font-size:12pt;
  line-height:1.65;
}
.kop{padding-bottom:8px; margin-bottom:16px;}
.kop-row{display:flex; align-items:center; gap:12px; border-bottom:2.5px solid #1c1c1c; padding-bottom:7px;}
.kop-logo{width:62px; height:62px; object-fit:contain; flex-shrink:0;}
.kop-text{flex:1; text-align:center; padding-right:62px;}
.kop-text .kline{font-size:13pt; font-weight:700; letter-spacing:.2px; text-transform:uppercase; line-height:1.3;}
.kop-text .kline.sub{font-size:12pt;}
.kop-text .kaddr{font-size:9pt; color:#3a3a3a; margin-top:3px; font-weight:400; text-transform:none;}
.kop-row.no-logo .kop-text{padding-right:0;}
.doc-title{text-align:center; margin:4px 0 14px;}
.doc-title .t1{font-weight:700; font-size:13pt; text-decoration:underline; text-underline-offset:3px;}
.doc-title .t2{font-size:11pt; margin-top:2px;}
.doc-title .t3{font-weight:700; font-size:12pt; margin-top:6px; text-transform:uppercase; max-width:80%; margin-left:auto; margin-right:auto;}
.kv-table{width:100%; margin-bottom:12px;}
.kv-table tr td{vertical-align:top; padding:1.5px 0; font-size:12pt;}
.kv-table td.k{width:78px; white-space:nowrap;}
.kv-table td.sep{width:10px;}
.para{margin:0 0 11px; text-align:justify;}
.para.indent{text-indent:26px;}
.lettered{margin:0 0 11px; padding-left:22px;}
.lettered li{margin-bottom:5px; text-align:justify;}
.addr-block{margin-bottom:12px; font-size:12pt;}
.right-block{margin-left:auto; width:62%; text-align:left; font-size:12pt;}
.center-block{text-align:center; font-size:12pt; margin-bottom:12px;}
.sig-space{height:56px; display:flex; align-items:center; justify-content:center;}
.sig-elektronik{font-style:italic; color:#8a8a8a; font-size:10pt; line-height:1.5; margin:14px 0; text-align:center;}
.sig-name{font-weight:700;}
.tembusan{margin-top:16px; font-size:10pt;}
.tembusan .t-label{font-weight:700; margin-bottom:3px;}
.diktum-row{display:flex; gap:8px; margin-bottom:9px;}
.diktum-row .dk{font-weight:700; width:56px; flex-shrink:0;}
.diktum-row .dv{flex:1; text-align:justify;}
.ak-table{width:100%; border-collapse:collapse; font-size:9pt; margin:0 0 12px;}
.ak-table th, .ak-table td{border:1px solid #4a4a4a; padding:4px 5px; text-align:center; vertical-align:middle;}
.ak-table th{font-weight:700; background:rgba(0,0,0,.04);}
.ak-table tr.total td{font-weight:700;}
.print-footnote{margin-top:18px; padding-top:10px; border-top:1px dashed var(--paper-edge); font-size:8pt; color:#9a9382; text-align:center;}

/* ---------- Modal ---------- */
.modal-backdrop{
  position:fixed; inset:0; background:rgba(12,31,52,.55); z-index:100;
  display:flex; align-items:flex-end; justify-content:center;
}
.modal{
  background:var(--app-bg); width:100%; max-width:560px; border-radius:18px 18px 0 0;
  padding:18px 16px 22px; max-height:88vh; overflow-y:auto;
}
.modal-head{display:flex; align-items:center; justify-content:space-between; margin-bottom:14px;}
.modal-head h2{font-size:15px; margin:0; font-weight:800; color:var(--navy);}
.modal-close{background:none; border:none; color:var(--muted); cursor:pointer; padding:4px;}

.toast{
  position:fixed; left:50%; bottom:26px; transform:translateX(-50%);
  background:var(--navy-deep); color:#fff; padding:10px 18px; border-radius:30px;
  font-size:12.5px; font-weight:600; z-index:200; box-shadow:0 8px 24px rgba(0,0,0,.3);
  opacity:0; pointer-events:none; transition:opacity .25s ease, transform .25s ease;
}
.toast.show{opacity:1; transform:translateX(-50%) translateY(-4px);}

.empty{text-align:center; padding:26px 10px; color:var(--muted); font-size:12.5px;}

@media print{
  body *{visibility:hidden;}
  #print-area, #print-area *{visibility:visible;}
  #print-area{position:absolute; top:0; left:0; width:100%; padding:0; margin:0; box-shadow:none; border:none;}
  #app, .appbar, .bottom-bar, main > *:not(#print-host){display:none !important;}
  #print-host{display:block !important;}
}
#print-host{display:none;}
</style>
</head>
<body>
<div id="app"></div>
<div id="toast" class="toast"></div>

<script>
/* ============================================================
   DATA: struktur naskah dinas & konfigurasi jenis surat
   Pengelompokan mengikuti taksonomi umum Tata Naskah Dinas
   Instansi Pemerintah (naskah dinas arahan, penetapan, penugasan,
   korespondensi internal/eksternal, dan naskah dinas khusus).
   ============================================================ */


/* Lambang resmi Kementerian ATR/BPN (default), dipakai sebagai watermark
   latar aplikasi dan logo bawaan jika Profil Instansi belum mengunggah logo sendiri. */
const DEFAULT_LOGO = "data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIiB3aWR0aD0iNDY0LjU2cHQiIGhlaWdodD0iNDYzLjA4cHQiIHZpZXdCb3g9IjAgMCA0NjQuNTYgNDYzLjA4IiB2ZXJzaW9uPSIxLjEiPgo8ZGVmcz4KPGNsaXBQYXRoIGlkPSJjbGlwMSI+CiAgPHBhdGggZD0iTSAyNDEgNDQ4IEwgMjU3IDQ0OCBMIDI1NyA0NjMuMDc4MTI1IEwgMjQxIDQ2My4wNzgxMjUgWiBNIDI0MSA0NDggIi8+CjwvY2xpcFBhdGg+CjxjbGlwUGF0aCBpZD0iY2xpcDIiPgogIDxwYXRoIGQ9Ik0gMjU3IDQ0OSBMIDI3MSA0NDkgTCAyNzEgNDYzLjA3ODEyNSBMIDI1NyA0NjMuMDc4MTI1IFogTSAyNTcgNDQ5ICIvPgo8L2NsaXBQYXRoPgo8Y2xpcFBhdGggaWQ9ImNsaXAzIj4KICA8cGF0aCBkPSJNIDAgMjkgTCA0NjQuNTU4NTk0IDI5IEwgNDY0LjU1ODU5NCAzOTcgTCAwIDM5NyBaIE0gMCAyOSAiLz4KPC9jbGlwUGF0aD4KPC9kZWZzPgo8ZyBpZD0ic3VyZmFjZTEiPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDUuODk5MDQ4JSwyNS4wOTkxODIlLDQxLjE5ODczJSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDEzNS4yMjY1NjMgMTQ1LjQ2NDg0NCBDIDE0Mi40MTc5NjkgMTQ5Ljg1NTQ2OSAxNDkuOTgwNDY5IDE1My42OTE0MDYgMTU3LjgwNDY4OCAxNTcuMDIzNDM4IEMgMTY4LjAwNzgxMyAxMjguMjAzMTI1IDE4Mi4wNzAzMTMgMTA2Ljg3NSAxOTguMDYyNSA5MC43MTg3NSBDIDE5My4xOTE0MDYgODguMzYzMjgxIDE4OC43ODUxNTYgODUuNjk5MjE5IDE4NC45NzI2NTYgODIuNjk1MzEzIEMgMTg5Ljc4MTI1IDg0Ljk5NjA5NCAxOTQuODI4MTI1IDg3LjAwMzkwNiAyMDAuMDQyOTY5IDg4Ljc1NzgxMyBDIDIwOS4zNzUgNzkuNjYwMTU2IDIxOS4zMjgxMjUgNzIuMjUzOTA2IDIyOS41MjM0MzggNjYuMDkzNzUgQyAyMjkuNTg5ODQ0IDY2LjA4NTkzOCAyMjkuNjUyMzQ0IDY2LjA3NDIxOSAyMjkuNzE4NzUgNjYuMDcwMzEzIEMgMjI2LjUxMTcxOSA2NC4yNTM5MDYgMjI0LjY3OTY4OCA2Mi4xNjc5NjkgMjI0LjY3OTY4OCA1OS45NDE0MDYgQyAyMjQuNjc5Njg4IDU1LjUyNzM0NCAyMzEuODc4OTA2IDUxLjY0NDUzMSAyNDIuNzYxNzE5IDQ5LjQwMjM0NCBDIDE3Ny4xMDE1NjMgNTcuMjE4NzUgMTIyLjE4MzU5NCAxMDAuMDIzNDM4IDk3LjE3NTc4MSAxNTguNjQ4NDM4IEMgMTA3LjczODI4MSAxNzMuOTMzNTk0IDExNy4xMjEwOTQgMTkyLjgxMjUgMTE4LjgwMDc4MSAyMTAuMjQyMTg4IEMgMTIxLjg5NDUzMSAyNDIuNDgwNDY5IDEwNi43MTA5MzggMjYxLjM4NjcxOSAxMDYuNzEwOTM4IDI2MS4zODY3MTkgQyAxMDYuNzEwOTM4IDI2MS4zODY3MTkgMTA2LjcxMDkzOCAyNjEuMzg2NzE5IDEwOC41NzAzMTMgMjY0LjE3NTc4MSBDIDExMS4zNTkzNzUgMjU3LjA1MDc4MSAxMTguNDg4MjgxIDIzOC40NDkyMTkgMTI5Ljk1NzAzMSAyMjQuODE2NDA2IEMgMTMxLjUwNzgxMyAyMTkuMjM0Mzc1IDEyOS4wMjczNDQgMjEwLjg2NzE4OCAxMjAuNjU2MjUgMjA1LjkwNjI1IEMgMTI0Ljk5NjA5NCAyMDYuODM1OTM4IDEzNS4yMjY1NjMgMjExLjE3MTg3NSAxMzUuMjI2NTYzIDIyNS40MzM1OTQgQyAxMzUuMjI2NTYzIDIyNS40MzM1OTQgMTM4LjE0MDYyNSAyMjguOTQ5MjE5IDE0Mi4yNDIxODggMjM0LjgyNDIxOSBDIDE0Mi4zNzEwOTQgMjMzLjE5OTIxOSAxNDIuNTA3ODEzIDIzMS41NjY0MDYgMTQyLjY2MDE1NiAyMjkuOTI1NzgxIEMgMTQ1LjA4NTkzOCAyMDQuMDg1OTM4IDE0OS42MzI4MTMgMTgxLjk2NDg0NCAxNTUuNzk2ODc1IDE2Mi45NDkyMTkgQyAxNDUuODk0NTMxIDE1Ny40NjQ4NDQgMTM4LjY3OTY4OCAxNTEuNTA3ODEzIDEzNS4yMjY1NjMgMTQ1LjQ2NDg0NCAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYig1Ljg5OTA0OCUsMjUuMDk5MTgyJSw0MS4xOTg3MyUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAyMDQuMzQzNzUgOTMuNDc2NTYzIEMgMTg5LjgzOTg0NCAxMTAuMDI3MzQ0IDE3Ni44NTU0NjkgMTMzLjE3MTg3NSAxNjcuODgyODEzIDE2MC45ODQzNzUgQyAxOTUuODk4NDM4IDE3MS4xNDA2MjUgMjI2LjYzNjcxOSAxNzUuNDA2MjUgMjU1Ljg1OTM3NSAxNzUuOTYwOTM4IEMgMjU2LjcyNjU2MyAxNTEuODMyMDMxIDI1Ny44ODY3MTkgMTI4LjEzNjcxOSAyNTkuMjI2NTYzIDEwNC42Mjg5MDYgQyAyMzkuNDE0MDYzIDEwMy4yODkwNjMgMjIwLjAxNTYyNSA5OS43NSAyMDQuMzQzNzUgOTMuNDc2NTYzICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDUuODk5MDQ4JSwyNS4wOTkxODIlLDQxLjE5ODczJSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDMwNC4yNzczNDQgNTkuOTQxNDA2IEMgMzA0LjI3NzM0NCA2Mi4yNjE3MTkgMzAyLjI4NTE1NiA2NC40Mjk2ODggMjk4LjgyODEyNSA2Ni4yOTI5NjkgQyAzMTAuMTM2NzE5IDczLjE2MDE1NiAzMjEuMTM2NzE5IDgxLjU2MjUgMzMxLjMyMDMxMyA5Mi4xMTMyODEgQyAzMzUuOTYwOTM4IDkwLjg3MTA5NCAzMzkuNjQ4NDM4IDg5LjU2MjUgMzQyLjEyMTA5NCA4OC4yNzczNDQgQyAzNjAuNDg4MjgxIDc4Ljc0MjE4OCAzNDcuMzUxNTYzIDY4LjA1ODU5NCAzNDcuMzUxNTYzIDY4LjA1ODU5NCBDIDMyOC42MjEwOTQgNTguNDQ5MjE5IDMwOCA1MS45OTYwOTQgMjg2LjE5NTMxMyA0OS40MDIzNDQgQyAyOTcuMDc4MTI1IDUxLjY0NDUzMSAzMDQuMjc3MzQ0IDU1LjUyNzM0NCAzMDQuMjc3MzQ0IDU5Ljk0MTQwNiAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYig1Ljg5OTA0OCUsMjUuMDk5MTgyJSw0MS4xOTg3MyUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAyMDYuNzE4NzUgOTAuODM1OTM4IEMgMjIzLjYzMjgxMyA5NS42OTUzMTMgMjQxLjk1MzEyNSA5OC4wMzUxNTYgMjU5LjU3MDMxMyA5OC42OTUzMTMgQyAyNTkuOTE3OTY5IDkyLjc1NzgxMyAyNjAuMjc3MzQ0IDg2LjgyODEyNSAyNjAuNjQ0NTMxIDgwLjkxMDE1NiBMIDI2MC42NDQ1MzEgNzIuNTIzNDM4IEwgMjYxLjE3MTg3NSA3Mi41MTk1MzEgQyAyNjEuMTcxODc1IDcyLjUwMzkwNiAyNjEuMTcxODc1IDcyLjQ5MjE4OCAyNjEuMTcxODc1IDcyLjQ3NjU2MyBMIDI2MS4xOTUzMTMgNzIuNDc2NTYzIEMgMjUxLjYwNTQ2OSA3Mi4yMzA0NjkgMjQyLjk4MDQ2OSA3MC45MTAxNTYgMjM2LjUyMzQzOCA2OC44OTQ1MzEgQyAyMzYuNDIxODc1IDY4Ljk1MzEyNSAyMzYuMzYzMjgxIDY4Ljk4NDM3NSAyMzYuMzYzMjgxIDY4Ljk4NDM3NSBDIDIyNi4zNTE1NjMgNzMuMDg5ODQ0IDIxNi4yNDIxODggODAuNTUwNzgxIDIwNi43MTg3NSA5MC44MzU5MzggIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoNS44OTkwNDglLDI1LjA5OTE4MiUsNDEuMTk4NzMlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMzIzLjk5NjA5NCA5My44NDM3NSBDIDMxMy43NTc4MTMgODIuMDcwMzEzIDMwMi43NTM5MDYgNzMuNTg1OTM4IDI5MS44NTU0NjkgNjkuMDcwMzEzIEMgMjg0Ljg4MjgxMyA3MS4xNjAxNTYgMjc1LjUxOTUzMSA3Mi40NjA5MzggMjY1LjE5MTQwNiA3Mi41MTU2MjUgQyAyNjUuMTkxNDA2IDcyLjUxNTYyNSAyNjUuMTkxNDA2IDcyLjUxNTYyNSAyNjUuMTkxNDA2IDcyLjUxOTUzMSBMIDI2NS43MTg3NSA3Mi41MjM0MzggTCAyNjUuNzE4NzUgODAuOTEwMTU2IEMgMjY2LjA4OTg0NCA4Ni44OTA2MjUgMjY2LjQ0OTIxOSA5Mi44NzUgMjY2LjgwMDc4MSA5OC44NzEwOTQgQyAyODguOTIxODc1IDk5LjE0NDUzMSAzMDkuNDI5Njg4IDk2Ljg5MDYyNSAzMjMuOTk2MDk0IDkzLjg0Mzc1ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDUuODk5MDQ4JSwyNS4wOTkxODIlLDQxLjE5ODczJSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDMyOS4zMDA3ODEgMTAwLjMyNDIxOSBDIDMxMS43NzM0MzggMTA0LjA3ODEyNSAyODkuNDg4MjgxIDEwNS45MDYyNSAyNjcuMTU2MjUgMTA1LjA0Njg3NSBDIDI2OC40ODgyODEgMTI4LjQxMDE1NiAyNjkuNjQwNjI1IDE1MS45NjA5MzggMjcwLjUwMzkwNiAxNzUuOTM3NSBDIDMwNy4wNjY0MDYgMTc1LjEyNSAzMzkuOTc2NTYzIDE2OC44NTE1NjMgMzYwLjM2MzI4MSAxNjEuNjY0MDYzIEMgMzUyLjU1MDc4MSAxMzcuMjAzMTI1IDM0MS42MzI4MTMgMTE2LjMyODEyNSAzMjkuMzAwNzgxIDEwMC4zMjQyMTkgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoNS44OTkwNDglLDI1LjA5OTE4MiUsNDEuMTk4NzMlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMzYyLjkzMzU5NCA3Ny4wNTQ2ODggQyAzNjIuOTMzNTk0IDc3LjA1NDY4OCAzNjIuOTMzNTk0IDc3LjA1ODU5NCAzNjIuOTMzNTk0IDc3LjA1ODU5NCBDIDM2Ni44ODI4MTMgODUuODM5ODQ0IDM1NS43NSA5My4zNzUgMzM3LjEwMTU2MyA5OC40NDE0MDYgQyAzNTAuMjMwNDY5IDExMy42MzY3MTkgMzYxLjczODI4MSAxMzIuODYzMjgxIDM3MC40MTQwNjMgMTU3LjU3NDIxOSBDIDM3MC40MTc5NjkgMTU3LjU3NDIxOSAzNzAuNDE3OTY5IDE1Ny41NzQyMTkgMzcwLjQxNzk2OSAxNTcuNTc0MjE5IEMgNDE1LjE5NTMxMyAxMzYuMTY0MDYzIDM5Ni43ODUxNTYgMTA1LjIzMDQ2OSAzOTYuNzg1MTU2IDEwNS4yMzA0NjkgQyAzODYuNzAzMTI1IDk0LjUzNTE1NiAzNzUuMzM1OTM4IDg1LjA2MjUgMzYyLjkzMzU5NCA3Ny4wNTQ2ODggIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoNS44OTkwNDglLDI1LjA5OTE4MiUsNDEuMTk4NzMlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMTY1LjY5MTQwNiAzNzcuMzA4NTk0IEMgMTYyLjU0Njg3NSAzNzAuMzA4NTk0IDE1OC44NTU0NjkgMzYxLjEzMjgxMyAxNTUuMzA4NTk0IDM1MC4wMzEyNSBDIDE1MC41NDY4NzUgMzU3LjY1MjM0NCAxNDUuODc1IDM2Mi4yNSAxNDQgMzY0LjMwODU5NCBDIDE0OS40NDUzMTMgMzY5LjEyODkwNiAxNTUuMTc5Njg4IDM3My42Mjg5MDYgMTYxLjE3NTc4MSAzNzcuNzc3MzQ0IEMgMTYyLjcyMjY1NiAzNzcuNTk3NjU2IDE2NC4yMjY1NjMgMzc3LjQ0MTQwNiAxNjUuNjkxNDA2IDM3Ny4zMDg1OTQgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoNS44OTkwNDglLDI1LjA5OTE4MiUsNDEuMTk4NzMlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMzY5LjUzNTE1NiAzNzYuNTQ2ODc1IEMgNDAwLjc3MzQzOCAzNTQuMzkwNjI1IDQyNC43MTA5MzggMzIyLjYyMTA5NCA0MzcuMDM1MTU2IDI4NS41NTA3ODEgQyA0MzIuOTI5Njg4IDI4OC4yNTc4MTMgNDExLjg5NDUzMSAzMDEuNjUyMzQ0IDM4MS45OTYwOTQgMzEyLjQ5NjA5NCBDIDM3Ni45NTMxMjUgMzQwLjY5NTMxMyAzNjguODYzMjgxIDM2Mi42MTMyODEgMzYyLjcxMDkzOCAzNzYuNDYwOTM4IEMgMzY0Ljk2NDg0NCAzNzYuNDM3NSAzNjcuMjQyMTg4IDM3Ni40NjA5MzggMzY5LjUzNTE1NiAzNzYuNTQ2ODc1ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDUuODk5MDQ4JSwyNS4wOTkxODIlLDQxLjE5ODczJSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDQxNS4xOTUzMTMgMTI4LjIxMDkzOCBDIDQxMC45MTAxNTYgMTQ2LjUzMTI1IDM5Ny44NzUgMTYwLjU0Njg3NSAzNzQuNjE3MTg4IDE3MC43NjE3MTkgQyAzNzkuNTc0MjE5IDE4Ny45NjA5MzggMzgzLjI2NTYyNSAyMDcuNTQ2ODc1IDM4NS4zNjMyODEgMjI5LjkyNTc4MSBDIDM4Ny41MTk1MzEgMjUyLjk0OTIxOSAzODYuOTQ5MjE5IDI3NC4xNjQwNjMgMzg0LjgxMjUgMjkzLjE0ODQzOCBDIDQxMi4wMzUxNTYgMjgzLjE2Nzk2OSA0MzYuMDY2NDA2IDI2OC4wMjczNDQgNDQ1LjYxMzI4MSAyNDMuODg2NzE5IEMgNDQ2LjAzNTE1NiAyMzguOTg4MjgxIDQ0Ni4yNTc4MTMgMjM0LjAzNTE1NiA0NDYuMjgxMjUgMjI5LjAzMTI1IEMgNDQ2LjEwNTQ2OSAxOTEuNjkxNDA2IDQzNC42NzE4NzUgMTU3LjAxMTcxOSA0MTUuMTk1MzEzIDEyOC4yMTA5MzggIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoNS44OTkwNDglLDI1LjA5OTE4MiUsNDEuMTk4NzMlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMzY0LjE3NTc4MSAxNzQuODU1NDY5IEMgMzQ4LjE0NDUzMSAxODAuNDY0ODQ0IDMyOC4yMDMxMjUgMTg0LjY3NTc4MSAzMDMuOTk2MDk0IDE4Ny41OTc2NTYgQyAyOTMuMjQ2MDk0IDE4OC44OTg0MzggMjgyLjEyMTA5NCAxODkuNDA2MjUgMjcwLjk0OTIxOSAxODkuMjM4MjgxIEMgMjcyLjE4MzU5NCAyMjguOTMzNTk0IDI3Mi41ODIwMzEgMjY5LjkxMDE1NiAyNzEuNjUyMzQ0IDMxMy4yNjU2MjUgQyAyNzMuMTEzMjgxIDMxMy4yMzQzNzUgMjc0LjU3MDMxMyAzMTMuMTk1MzEzIDI3Ni4wMjM0MzggMzEzLjE0ODQzOCBMIDI3Ni4wMjM0MzggMjQyLjQwMjM0NCBMIDMwMi4wNjI1IDI0Mi40MDIzNDQgTCAzMDIuMDYyNSAyODEuNTM5MDYzIEwgMzE2LjY0ODQzOCAyNjcuNzI2NTYzIEwgMzQ1Ljc3NzM0NCAyOTIuNDYwOTM4IEwgMzM0LjkxNzk2OSAyOTIuNDYwOTM4IEwgMzM0LjkxNzk2OSAzMDYuMzQ3NjU2IEMgMzQ1LjY2MDE1NiAzMDQuMjg5MDYzIDM1Ni45NzI2NTYgMzAxLjc3MzQzOCAzNjguMTM2NzE5IDI5OC41NjI1IEMgMzcwLjgyODEyNSAyODMuMDcwMzEzIDM3Mi42MTMyODEgMjY1Ljc4MTI1IDM3Mi44MDg1OTQgMjQ2LjgyMDMxMyBDIDM3My4wNzQyMTkgMjIwLjkzNzUgMzY5Ljg1MTU2MyAxOTYuNjg3NSAzNjQuMTc1NzgxIDE3NC44NTU0NjkgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoNS44OTkwNDglLDI1LjA5OTE4MiUsNDEuMTk4NzMlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMjU4LjA1ODU5NCAzOTYuNjM2NzE5IEMgMjU2LjYzMjgxMyAzNzIuNDM3NSAyNTUuNjQ0NTMxIDM0OS4wNTA3ODEgMjU1LjAyMzQzOCAzMjYuMzM5ODQ0IEMgMjE4LjczODI4MSAzMjMuMzY3MTg4IDE5MS42OTE0MDYgMzE0LjU3NDIxOSAxNzIuODg2NzE5IDI5Ny45NjQ4NDQgQyAxNzUuMjE4NzUgMjk5LjAzMTI1IDE3Ny42NTIzNDQgMzAwLjAzNTE1NiAxODAuMTY3OTY5IDMwMC45ODQzNzUgQyAxODEuNjU2MjUgMjk2LjI3MzQzOCAxODIuMjQyMTg4IDI4Ny45NzY1NjMgMTgyLjQ2ODc1IDI4Mi44NTE1NjMgTCAxNzMuNjc1NzgxIDI4Mi44NTE1NjMgTCAxODEuMzA4NTk0IDI3Ny4zMjQyMTkgQyAxODAuOTQ1MzEzIDI3Ni43MjY1NjMgMTgwLjY3MTg3NSAyNzYuMTA5Mzc1IDE4MC42NzE4NzUgMjc2LjEwOTM3NSBDIDE3NS4yMTA5MzggMjc3Ljk3MjY1NiAxNzQuMTY0MDYzIDI3My4wODk4NDQgMTc0LjI4MTI1IDI3MS4yMzA0NjkgQyAxNzAuMjEwOTM4IDI3Mi4yNzczNDQgMTY3LjM4MjgxMyAyNjguMDg5ODQ0IDE2OC4zOTA2MjUgMjY0LjM3MTA5NCBDIDE2My4wMDM5MDYgMjY1LjMwMDc4MSAxNTkuMDU0Njg4IDI1NC45NTcwMzEgMTY3LjE5MTQwNiAyNTIuMjgxMjUgQyAxNjEuNDkyMTg4IDI0Ni43MDMxMjUgMTY5Ljk0MTQwNiAyNDAuODkwNjI1IDE3Mi41NzQyMTkgMjQ0LjI2MTcxOSBDIDE2OS43NDYwOTQgMjM3LjE3MTg3NSAxNzcuMDcwMzEzIDIzNS43ODEyNSAxNzggMjM3LjExNzE4OCBDIDE3Ni41NzQyMTkgMjI4LjEyMTA5NCAxOTMuMzEyNSAyMjIuMzI4MTI1IDE5NC4wMzkwNjMgMjM2LjY2NDA2MyBDIDE5OS41MDM5MDYgMjM1LjQyOTY4OCAyMDAuODk4NDM4IDI0MS43MDcwMzEgMTk5LjczNDM3NSAyNDMuNzk2ODc1IEMgMjA1Ljc4MTI1IDI0Mi4yODUxNTYgMjA4LjEwNTQ2OSAyNDguNDQ1MzEzIDIwNC45NjQ4NDQgMjUyLjc0NjA5NCBDIDIwNy43NDYwOTQgMjUyLjQ2MDkzOCAyMDguODc4OTA2IDI1NS40NjQ4NDQgMjA4LjkxNzk2OSAyNTcuMzMyMDMxIEwgMjEyLjQ1NzAzMSAyNTQuNzY5NTMxIEwgMjEzLjIxODc1IDI1NS4zODI4MTMgTCAyMTMuMjE4NzUgMjE3Ljk5MjE4OCBMIDI1MC45OTYwOTQgMjE3Ljk5MjE4OCBMIDI1MC45OTYwOTQgMzEzLjEyMTA5NCBDIDI1Mi4yMzA0NjkgMzEzLjE2NDA2MyAyNTMuNDY4NzUgMzEzLjIwMzEyNSAyNTQuNzA3MDMxIDMxMy4yMzQzNzUgQyAyNTMuNzc3MzQ0IDI2OS42NTIzNDQgMjU0LjE4MzU5NCAyMjguNDcyNjU2IDI1NS40MzM1OTQgMTg4LjU4MjAzMSBDIDIyMS43NDIxODggMTg2LjI2OTUzMSAxODguOTM3NSAxNzguMzA0Njg4IDE2NS43NjE3MTkgMTY3Ljg5ODQzOCBDIDE1OC45MDYyNSAxOTEuNDg4MjgxIDE1NC45MjE4NzUgMjE4LjE1MjM0NCAxNTUuMjE0ODQ0IDI0Ni44MjAzMTMgQyAxNTUuMjUgMjUwLjEyNSAxNTUuMzM1OTM4IDI1My4zNzUgMTU1LjQ2NDg0NCAyNTYuNTc4MTI1IEMgMTYyLjM3MTA5NCAyNjkuOTEwMTU2IDE2OC4zOTA2MjUgMjg1Ljg4MjgxMyAxNjguMzkwNjI1IDMwMS4wNjY0MDYgQyAxNjguMzkwNjI1IDMxMC4wNTQ2ODggMTY3LjM1MTU2MyAzMTcuOTc2NTYzIDE2NS42OTUzMTMgMzI0LjkxMDE1NiBDIDE3Mi4wMjM0MzggMzQ4LjQ0NTMxMyAxNzkuOTMzNTk0IDM2Ni4wNDI5NjkgMTg1LjY3MTg3NSAzNzYuOTcyNjU2IEMgMjA0LjY5MTQwNiAzNzguMzAwNzgxIDIxNy4zOTQ1MzEgMzg0LjYzNjcxOSAyMzYuMjY5NTMxIDM5MS44Nzg5MDYgQyAyNDMuNzY1NjI1IDM5NC43NTc4MTMgMjUxLjEwNTQ2OSAzOTYuMTc5Njg4IDI1OC4wNTg1OTQgMzk2LjYzNjcxOSAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYig1Ljg5OTA0OCUsMjUuMDk5MTgyJSw0MS4xOTg3MyUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAzNDEuNzgxMjUgMzc4LjA1MDc4MSBDIDM0OC4wNjY0MDYgMzY2LjI2NTYyNSAzNTcuMjY1NjI1IDM0NiAzNjQuMDE5NTMxIDMxOC4zMjAzMTMgQyAzNDguNzI2NTYzIDMyMi42NzE4NzUgMzMxLjg2MzI4MSAzMjUuOTM3NSAzMTQuMjI2NTYzIDMyNi43ODkwNjMgQyAyOTguODE2NDA2IDMyNy41MzUxNTYgMjg0LjUyNzM0NCAzMjcuNzE4NzUgMjcxLjMxMjUgMzI3LjI2NTYyNSBDIDI3MC42OTE0MDYgMzQ5LjY5MTQwNiAyNjkuNzA3MDMxIDM3Mi43Njk1MzEgMjY4LjMwNDY4OCAzOTYuNjQwNjI1IEMgMjg1LjkxMDE1NiAzOTUuNTM5MDYzIDI5OS44MTY0MDYgMzg5LjExMzI4MSAzMDUuMzk0NTMxIDM4Ni45MTc5NjkgQyAzMDkuOTMzNTk0IDM4NS4xNDA2MjUgMzIzLjkwMjM0NCAzODAuNTE1NjI1IDM0MS43ODEyNSAzNzguMDUwNzgxICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDU1LjY5OTE1OCUsNzcuNTk4NTcyJSwyNi4yOTg1MjMlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMjA0Ljk2NDg0NCAyNTIuNzQ2MDk0IEMgMjA4LjEwNTQ2OSAyNDguNDQ1MzEzIDIwNS43ODEyNSAyNDIuMjg1MTU2IDE5OS43MzQzNzUgMjQzLjc5Njg3NSBDIDIwMC44OTg0MzggMjQxLjcwNzAzMSAxOTkuNTAzOTA2IDIzNS40Mjk2ODggMTk0LjAzOTA2MyAyMzYuNjY0MDYzIEMgMTkzLjMxMjUgMjIyLjMyODEyNSAxNzYuNTc0MjE5IDIyOC4xMjEwOTQgMTc4IDIzNy4xMTcxODggQyAxNzcuMDcwMzEzIDIzNS43ODEyNSAxNjkuNzQ2MDk0IDIzNy4xNzE4NzUgMTcyLjU3NDIxOSAyNDQuMjYxNzE5IEMgMTY5Ljk0MTQwNiAyNDAuODkwNjI1IDE2MS40OTIxODggMjQ2LjcwMzEyNSAxNjcuMTkxNDA2IDI1Mi4yODEyNSBDIDE1OS4wNTQ2ODggMjU0Ljk1NzAzMSAxNjMuMDAzOTA2IDI2NS4zMDA3ODEgMTY4LjM5MDYyNSAyNjQuMzcxMDk0IEMgMTY3LjM4MjgxMyAyNjguMDg5ODQ0IDE3MC4yMTA5MzggMjcyLjI3NzM0NCAxNzQuMjgxMjUgMjcxLjIzMDQ2OSBDIDE3NC4xNjQwNjMgMjczLjA4OTg0NCAxNzUuMjEwOTM4IDI3Ny45NzI2NTYgMTgwLjY3MTg3NSAyNzYuMTA5Mzc1IEMgMTgwLjY3MTg3NSAyNzYuMTA5Mzc1IDE4MC45NDUzMTMgMjc2LjcyNjU2MyAxODEuMzA4NTk0IDI3Ny4zMjQyMTkgTCAyMDguOTE3OTY5IDI1Ny4zMzIwMzEgQyAyMDguODc4OTA2IDI1NS40NjQ4NDQgMjA3Ljc0NjA5NCAyNTIuNDYwOTM4IDIwNC45NjQ4NDQgMjUyLjc0NjA5NCAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYig1NS42OTkxNTglLDc3LjU5ODU3MiUsMjYuMjk4NTIzJSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDE4Mi40Njg3NSAyODIuODUxNTYzIEMgMTgyLjI0MjE4OCAyODcuOTc2NTYzIDE4MS42NTYyNSAyOTYuMjczNDM4IDE4MC4xNjc5NjkgMzAwLjk4NDM3NSBDIDE4Mi4zOTQ1MzEgMzAxLjgyMDMxMyAxODQuNjg3NSAzMDIuNjA5Mzc1IDE4Ny4wMzkwNjMgMzAzLjM1NTQ2OSBMIDE4Ny4wMzkwNjMgMjgyLjg1MTU2MyBMIDE4Mi40Njg3NSAyODIuODUxNTYzICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDMuNDk4ODQlLDI2LjY5OTgyOSUsNDEuNTk4NTExJSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDI0Mi44MjAzMTMgMjMwLjc0MjE4OCBMIDIzNy42Mjg5MDYgMjMwLjc0MjE4OCBMIDIzNy42Mjg5MDYgMjI1LjU1MDc4MSBMIDI0Mi44MjAzMTMgMjI1LjU1MDc4MSBaIE0gMjM0LjcwMzEyNSAyMzAuNzQyMTg4IEwgMjI5LjUxMTcxOSAyMzAuNzQyMTg4IEwgMjI5LjUxMTcxOSAyMjUuNTUwNzgxIEwgMjM0LjcwMzEyNSAyMjUuNTUwNzgxIFogTSAyMjYuMzE2NDA2IDIzMC43NDIxODggTCAyMjEuMTIxMDk0IDIzMC43NDIxODggTCAyMjEuMTIxMDk0IDIyNS41NTA3ODEgTCAyMjYuMzE2NDA2IDIyNS41NTA3ODEgWiBNIDIxNi40NzI2NTYgMjIxLjI0NjA5NCBMIDIxNi40NzI2NTYgMjU3Ljk5NjA5NCBMIDI0Ni4zMjAzMTMgMjgxLjk2ODc1IEwgMjMxLjY5OTIxOSAyODEuOTY4NzUgTCAyMzEuNjk5MjE5IDMxMS44NzEwOTQgQyAyMzYuOTg4MjgxIDMxMi4zNzUgMjQyLjM1MTU2MyAzMTIuNzQ2MDk0IDI0Ny43NDIxODggMzEyLjk4ODI4MSBMIDI0Ny43NDIxODggMjIxLjI0NjA5NCBMIDIxNi40NzI2NTYgMjIxLjI0NjA5NCAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMDAlLDEwMCUsMTAwJSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDIxMy4yMTg3NSAyMTcuOTkyMTg4IEwgMjEzLjIxODc1IDI1NS4zODI4MTMgTCAyMTIuNDU3MDMxIDI1NC43Njk1MzEgTCAyMDguOTE3OTY5IDI1Ny4zMzIwMzEgTCAxODEuMzA4NTk0IDI3Ny4zMjQyMTkgTCAxNzMuNjc1NzgxIDI4Mi44NTE1NjMgTCAxODcuMDM5MDYzIDI4Mi44NTE1NjMgTCAxODcuMDM5MDYzIDMwMy4zNTU0NjkgQyAxODguMTEzMjgxIDMwMy42OTUzMTMgMTg5LjE5NTMxMyAzMDQuMDIzNDM4IDE5MC4yOTI5NjkgMzA0LjM0NzY1NiBMIDE5MC4yOTI5NjkgMjc5LjU5NzY1NiBMIDE4My43MTg3NSAyNzkuNTk3NjU2IEwgMjEyLjM1NTQ2OSAyNTguODYzMjgxIEwgMjM3LjA3MDMxMyAyNzguNzEwOTM4IEwgMjI4LjQ0NTMxMyAyNzguNzEwOTM4IEwgMjI4LjQ0NTMxMyAzMTEuNTM5MDYzIEMgMjI5LjUyNzM0NCAzMTEuNjU2MjUgMjMwLjYxMzI4MSAzMTEuNzY1NjI1IDIzMS42OTkyMTkgMzExLjg3MTA5NCBMIDIzMS42OTkyMTkgMjgxLjk2ODc1IEwgMjQ2LjMyMDMxMyAyODEuOTY4NzUgTCAyMTYuNDcyNjU2IDI1Ny45OTYwOTQgTCAyMTYuNDcyNjU2IDIyMS4yNDYwOTQgTCAyNDcuNzQyMTg4IDIyMS4yNDYwOTQgTCAyNDcuNzQyMTg4IDMxMi45ODgyODEgQyAyNDguODI0MjE5IDMxMy4wMzkwNjMgMjQ5LjkxMDE1NiAzMTMuMDgyMDMxIDI1MC45OTYwOTQgMzEzLjEyMTA5NCBMIDI1MC45OTYwOTQgMjE3Ljk5MjE4OCBMIDIxMy4yMTg3NSAyMTcuOTkyMTg4ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDMuNDk4ODQlLDI2LjY5OTgyOSUsNDEuNTk4NTExJSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDI4Ny42ODc1IDI1NC42ODM1OTQgTCAyODIuNDk2MDk0IDI1NC42ODM1OTQgTCAyODIuNDk2MDk0IDI0OS40OTIxODggTCAyODcuNjg3NSAyNDkuNDkyMTg4IFogTSAyODcuNjg3NSAyNjIuODIwMzEzIEwgMjgyLjQ5NjA5NCAyNjIuODIwMzEzIEwgMjgyLjQ5NjA5NCAyNTcuNjI4OTA2IEwgMjg3LjY4NzUgMjU3LjYyODkwNiBaIE0gMjkwLjcxMDkzOCAyNTcuNjI4OTA2IEwgMjk1LjkwMjM0NCAyNTcuNjI4OTA2IEwgMjk1LjkwMjM0NCAyNjIuODIwMzEzIEwgMjkwLjcxMDkzOCAyNjIuODIwMzEzIFogTSAyOTAuNzEwOTM4IDI0OS40OTIxODggTCAyOTUuOTAyMzQ0IDI0OS40OTIxODggTCAyOTUuOTAyMzQ0IDI1NC42ODM1OTQgTCAyOTAuNzEwOTM4IDI1NC42ODM1OTQgWiBNIDI4OS4yMTg3NSAyOTMuNzAzMTI1IEwgMjk4LjgwNDY4OCAyODQuNjIxMDk0IEwgMjk4LjgwNDY4OCAyNDUuNjU2MjUgTCAyNzkuMjc3MzQ0IDI0NS42NTYyNSBMIDI3OS4yNzczNDQgMzEzLjAyNzM0NCBDIDI4NS45MTc5NjkgMzEyLjc1MzkwNiAyOTIuNDU3MDMxIDMxMi4zMDg1OTQgMjk4LjgwNDY4OCAzMTEuNzA3MDMxIEwgMjk4LjgwNDY4OCAyOTMuNzAzMTI1IEwgMjg5LjIxODc1IDI5My43MDMxMjUgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoMy40OTg4NCUsMjYuNjk5ODI5JSw0MS41OTg1MTElKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMzEwLjQ2ODc1IDI5NS41NjI1IEwgMzA1LjI3NzM0NCAyOTUuNTYyNSBMIDMwNS4yNzczNDQgMjkwLjM2NzE4OCBMIDMxMC40Njg3NSAyOTAuMzY3MTg4IFogTSAzMzYuOTE3OTY5IDI4OS4yMDcwMzEgTCAzMTYuNzY1NjI1IDI3Mi4wOTc2NTYgTCAyOTcuMzkwNjI1IDI5MC40NDUzMTMgTCAzMDIuMDYyNSAyOTAuNDQ1MzEzIEwgMzAyLjA2MjUgMzExLjM4MjgxMyBDIDMwOS4wNDY4NzUgMzEwLjY1NjI1IDMxNS43NzczNDQgMzA5LjczODI4MSAzMjIuMTMyODEzIDMwOC42NTYyNSBDIDMyNS4yMzQzNzUgMzA4LjEyODkwNiAzMjguNDIxODc1IDMwNy41NjY0MDYgMzMxLjY2MDE1NiAzMDYuOTY0ODQ0IEwgMzMxLjY2MDE1NiAyODkuMjA3MDMxIEwgMzM2LjkxNzk2OSAyODkuMjA3MDMxICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEwMCUsMTAwJSwxMDAlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMzQ1Ljc3NzM0NCAyOTIuNDYwOTM4IEwgMzE2LjY0ODQzOCAyNjcuNzI2NTYzIEwgMzAyLjA2MjUgMjgxLjUzOTA2MyBMIDMwMi4wNjI1IDI0Mi40MDIzNDQgTCAyNzYuMDIzNDM4IDI0Mi40MDIzNDQgTCAyNzYuMDIzNDM4IDMxMy4xNDg0MzggQyAyNzcuMTEzMjgxIDMxMy4xMTMyODEgMjc4LjE5NTMxMyAzMTMuMDcwMzEzIDI3OS4yNzczNDQgMzEzLjAyNzM0NCBMIDI3OS4yNzczNDQgMjQ1LjY1NjI1IEwgMjk4LjgwNDY4OCAyNDUuNjU2MjUgTCAyOTguODA0Njg4IDI4NC42MjEwOTQgTCAyODkuMjE4NzUgMjkzLjcwMzEyNSBMIDI5OC44MDQ2ODggMjkzLjcwMzEyNSBMIDI5OC44MDQ2ODggMzExLjcwNzAzMSBDIDI5OS44OTg0MzggMzExLjYwMTU2MyAzMDAuOTgwNDY5IDMxMS40OTYwOTQgMzAyLjA2MjUgMzExLjM4MjgxMyBMIDMwMi4wNjI1IDI5MC40NDUzMTMgTCAyOTcuMzkwNjI1IDI5MC40NDUzMTMgTCAzMTYuNzY1NjI1IDI3Mi4wOTc2NTYgTCAzMzYuOTE3OTY5IDI4OS4yMDcwMzEgTCAzMzEuNjYwMTU2IDI4OS4yMDcwMzEgTCAzMzEuNjYwMTU2IDMwNi45NjQ4NDQgQyAzMzIuNzQyMTg4IDMwNi43NjE3MTkgMzMzLjgyNDIxOSAzMDYuNTU4NTk0IDMzNC45MTc5NjkgMzA2LjM0NzY1NiBMIDMzNC45MTc5NjkgMjkyLjQ2MDkzOCBMIDM0NS43NzczNDQgMjkyLjQ2MDkzOCAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMy42OTkzNDElLDEyLjE5OTQwMiUsMTIuNSUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSA2OS44NzUgMTA4LjI2NTYyNSBDIDcwLjI0MjE4OCAxMDcuNzEwOTM4IDcwLjcxMDkzOCAxMDcuMTcxODc1IDcxLjUxOTUzMSAxMDcuNzA3MDMxIEwgNzkuNjM2NzE5IDExMy4wOTc2NTYgQyA4MC40NDE0MDYgMTEzLjYzMjgxMyA4MC4xMjg5MDYgMTE0LjI3MzQzOCA3OS43NTc4MTMgMTE0LjgyODEyNSBMIDc5LjYxMzI4MSAxMTUuMDQ2ODc1IEwgODAuMDc4MTI1IDExNS4zNTU0NjkgQyA4MC40OTIxODggMTE0LjczNDM3NSA4MS4wNDY4NzUgMTEzLjc2NTYyNSA4MS41NzAzMTMgMTEyLjk3NjU2MyBDIDgyLjEyNSAxMTIuMTM2NzE5IDgyLjg0NzY1NiAxMTEuMTg3NSA4My4yNjk1MzEgMTEwLjU1NDY4OCBMIDgyLjgwNDY4OCAxMTAuMjQyMTg4IEwgODIuNjc5Njg4IDExMC40Mjk2ODggQyA4Mi4zNzEwOTQgMTEwLjg5NDUzMSA4MS44MjAzMTMgMTExLjY5MTQwNiA4MC45NTMxMjUgMTExLjExMzI4MSBMIDcyLjgzNTkzOCAxMDUuNzIyNjU2IEMgNzEuOTY4NzUgMTA1LjE0ODQzOCA3Mi40ODQzNzUgMTA0LjMzMjAzMSA3Mi43OTI5NjkgMTAzLjg2NzE4OCBMIDcyLjkxNzk2OSAxMDMuNjc5Njg4IEwgNzIuNDUzMTI1IDEwMy4zNzEwOTQgQyA3Mi4wMzEyNSAxMDQuMDA3ODEzIDcxLjQzMzU5NCAxMDUuMDM5MDYzIDcwLjg3ODkwNiAxMDUuODc4OTA2IEMgNzAuMzU1NDY5IDEwNi42Njc5NjkgNjkuNjc1NzgxIDEwNy41NTQ2ODggNjkuMjY1NjI1IDEwOC4xNzU3ODEgTCA2OS43MzA0NjkgMTA4LjQ4NDM3NSBMIDY5Ljg3NSAxMDguMjY1NjI1ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEzLjY5OTM0MSUsMTIuMTk5NDAyJSwxMi41JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDc0LjAxOTUzMSAxMDIuMDIzNDM4IEMgNzQuMTUyMzQ0IDEwMS44MjAzMTMgNzQuNjA5Mzc1IDEwMS4xNjQwNjMgNzQuOTIxODc1IDEwMS4zNzEwOTQgQyA3NS4yNDYwOTQgMTAxLjU4NTkzOCA3NS40NTMxMjUgMTAyLjQxNzk2OSA3NS41MjM0MzggMTAyLjc1MzkwNiBMIDc2Ljk4ODI4MSAxMDguNDE0MDYzIEwgODMuMzk0NTMxIDEwNy44NDM3NSBDIDgzLjc4NTE1NiAxMDcuNzkyOTY5IDg0LjcwMzEyNSAxMDcuNzUzOTA2IDg1LjA4OTg0NCAxMDcuODA4NTk0IEMgODUuNDE3OTY5IDEwNy4zMTY0MDYgODUuNzA3MDMxIDEwNi44MTI1IDg2LjAzNTE1NiAxMDYuMzE2NDA2IEMgODYuMzg2NzE5IDEwNS43OTI5NjkgODYuNzc3MzQ0IDEwNS4yNjk1MzEgODcuMTE3MTg4IDEwNC43NTc4MTMgTCA4Ni42NTIzNDQgMTA0LjQ0OTIxOSBDIDg2LjI2MTcxOSAxMDUuMDM1MTU2IDg1LjU0Mjk2OSAxMDUuMjc3MzQ0IDg0Ljg2MzI4MSAxMDUuMjkyOTY5IEwgNzcuMjE0ODQ0IDEwNS45NTMxMjUgTCA3Ni4xOTE0MDYgMTAxLjc0NjA5NCBDIDc1LjkyOTY4OCAxMDAuNjU2MjUgNzUuNzg5MDYzIDk5LjM1NTQ2OSA3Ni40Njg3NSA5OC4zMzU5MzggTCA3Ni42MDE1NjMgOTguMTMyODEzIEwgNzYuMTM2NzE5IDk3LjgyNDIxOSBDIDc1LjY3MTg3NSA5OC41MjM0MzggNzUuMjgxMjUgOTkuMjQ2MDk0IDc0LjgyMDMxMyA5OS45NDE0MDYgQyA3NC4zNzg5MDYgMTAwLjYwOTM3NSA3My44ODI4MTMgMTAxLjIxODc1IDczLjQ0MTQwNiAxMDEuODg2NzE5IEwgNzMuOTA2MjUgMTAyLjE5MTQwNiBMIDc0LjAxOTUzMSAxMDIuMDIzNDM4ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEzLjY5OTM0MSUsMTIuMTk5NDAyJSwxMi41JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDc4LjAxNTYyNSA5Ni4xODM1OTQgQyA3OC40MTc5NjkgOTUuNjQ4NDM4IDc4LjkxNzk2OSA5NS4xNDA2MjUgNzkuNjkxNDA2IDk1LjcyMjY1NiBMIDg3LjQ3NjU2MyAxMDEuNTgyMDMxIEMgODguMjUgMTAyLjE2MDE1NiA4Ny45MDIzNDQgMTAyLjc4MTI1IDg3LjUgMTAzLjMxNjQwNiBMIDg3LjM0Mzc1IDEwMy41MjczNDQgTCA4Ny43ODkwNjMgMTAzLjg1OTM3NSBDIDg4LjQyNTc4MSAxMDMuMDE1NjI1IDg5LjY5NTMxMyAxMDEuMTk5MjE5IDkwLjcwMzEyNSA5OS44NjMyODEgQyA5MS43MDcwMzEgOTguNTI3MzQ0IDkzLjA1NDY4OCA5Ni44NjMyODEgOTMuNzY5NTMxIDk1LjkxMDE1NiBDIDkzLjA4MjAzMSA5NS4xODM1OTQgOTIuNDI5Njg4IDk0LjQxMDE1NiA5MS43ODUxNTYgOTMuNjI1IEwgOTEuMzY3MTg4IDkzLjk2NDg0NCBDIDkyLjcyNjU2MyA5NS42ODM1OTQgOTIuMjUzOTA2IDk2LjU2MjUgOTAuOTE0MDYzIDk4LjM0NzY1NiBDIDkwLjE5OTIxOSA5OS4yOTY4NzUgODkuNTQ2ODc1IDEwMC4xNjAxNTYgODguNTgyMDMxIDk5LjQzMzU5NCBMIDg1LjEyMTA5NCA5Ni44MjgxMjUgTCA4Ni40NjA5MzggOTUuMDQyOTY5IEMgODcuMjM0Mzc1IDk0LjAxOTUzMSA4Ny44NDM3NSA5NC40MTAxNTYgODguODA0Njg4IDk0Ljk5MjE4OCBMIDg5LjA1MDc4MSA5NC40NzY1NjMgQyA4OC40NjQ4NDQgOTQuMDg1OTM4IDg3Ljg4NjcxOSA5My42NzU3ODEgODcuMzI0MjE5IDkzLjI1IEMgODYuNzQyMTg4IDkyLjgxMjUgODYuMTc1NzgxIDkyLjM2MzI4MSA4NS42MTcxODggOTEuODk4NDM4IEwgODUuMjgxMjUgOTIuMzM5ODQ0IEMgODYuMDE5NTMxIDkzLjAzNTE1NiA4Ni4zNzg5MDYgOTMuNjA1NDY5IDg1LjcwNzAzMSA5NC41IEwgODQuMzc1IDk2LjI2OTUzMSBMIDgwLjQ4MDQ2OSA5My4zMzk4NDQgTCA4Mi4wMzUxNTYgOTEuMjczNDM4IEMgODMuMjEwOTM4IDg5LjcxMDkzOCA4NC4xMTcxODggOTAuMTEzMjgxIDg1LjE0MDYyNSA5MC43NjU2MjUgTCA4NS4zNTU0NjkgOTAuMjMwNDY5IEMgODQuNjY3OTY5IDg5Ljc4NTE1NiA4My42NzU3ODEgODkuMDYyNSA4My4wNTg1OTQgODguNTUwNzgxIEMgODIuMzAwNzgxIDg5LjU2MjUgODEuMTk1MzEzIDkxLjE1MjM0NCA4MC4yNTc4MTMgOTIuNDAyMzQ0IEMgNzkuMzE2NDA2IDkzLjY0ODQzOCA3OC4wOTM3NSA5NS4xNTIzNDQgNzcuNDE0MDYzIDk2LjA1ODU5NCBMIDc3Ljg1OTM3NSA5Ni4zOTA2MjUgTCA3OC4wMTU2MjUgOTYuMTgzNTk0ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEzLjY5OTM0MSUsMTIuMTk5NDAyJSwxMi41JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDg2LjEwNTQ2OSA4NS40NTcwMzEgQyA4Ni42NDA2MjUgODQuODM5ODQ0IDg3LjQzMzU5NCA4NC40Njg3NSA4OC4yMTg3NSA4NS4xNTIzNDQgQyA4OC43ODEyNSA4NS42NDA2MjUgODkuNjQ0NTMxIDg2LjQ4ODI4MSA5MC41NDI5NjkgODcuNDY4NzUgTCA5NC4wODIwMzEgOTEuMjgxMjUgQyA5NC45ODA0NjkgOTIuMjg1MTU2IDk1LjQyMTg3NSA5Mi43NDIxODggOTQuNSA5My44OTA2MjUgTCA5NC4zMzIwMzEgOTQuMDg1OTM4IEwgOTQuNzUgOTQuNDQ5MjE5IEMgOTUuMTk5MjE5IDkzLjg3ODkwNiA5NS42NjAxNTYgOTMuMjkyOTY5IDk2LjEzNjcxOSA5Mi43NDYwOTQgQyA5Ni42ODM1OTQgOTIuMTEzMjgxIDk3LjI3MzQzOCA5MS40OTIxODggOTcuODUxNTYzIDkwLjg4NjcxOSBMIDk3LjQyOTY4OCA5MC41MTk1MzEgTCA5Ny4yODUxNTYgOTAuNjg3NSBDIDk2LjkyNTc4MSA5MS4wNzAzMTMgOTYuNjU2MjUgOTEuMzUxNTYzIDk2LjM0NzY1NiA5MS40NTMxMjUgQyA5Ni4wNjI1IDkxLjUyMzQzOCA5NS43NDIxODggOTEuNDQxNDA2IDk1LjI5Mjk2OSA5MS4wNTA3ODEgTCA4OS41NDI5NjkgODUuMjE4NzUgTCA4OS41NjY0MDYgODUuMTg3NSBMIDEwMC4yNjk1MzEgODguNTI3MzQ0IEwgMTAwLjU2MjUgODguMTkxNDA2IEwgOTUuNzY5NTMxIDc3LjczODI4MSBMIDk1Ljc5Mjk2OSA3Ny43MTA5MzggTCAxMDIuMDYyNSA4Mi40Njg3NSBDIDEwMi40Mzc1IDgyLjc2OTUzMSAxMDIuNTkzNzUgODIuOTA2MjUgMTAyLjc2MTcxOSA4My4wNTA3ODEgQyAxMDMuMzc4OTA2IDgzLjU4OTg0NCAxMDIuOTY0ODQ0IDg0LjA2NjQwNiAxMDIuMzcxMDk0IDg0LjgzMjAzMSBMIDEwMi43OTI5NjkgODUuMTk5MjE5IEMgMTAzLjQzNzUgODQuNDAyMzQ0IDEwNC4wNzgxMjUgODMuNjA1NDY5IDEwNC43NSA4Mi44MzU5MzggQyAxMDUuMzM1OTM4IDgyLjE2MDE1NiAxMDUuOTYwOTM4IDgxLjQ5NjA5NCAxMDYuNTYyNSA4MC44NjMyODEgTCAxMDYuMTQwNjI1IDgwLjQ5NjA5NCBDIDEwNS4zODI4MTMgODEuMzEyNSAxMDUuMDE5NTMxIDgxLjYxMzI4MSAxMDQuMjY5NTMxIDgxLjA2MjUgTCA5Ny4zNzUgNzYuMDA3ODEzIEMgOTcuMDQyOTY5IDc1Ljc2NTYyNSA5Ni41NzQyMTkgNzUuNDUzMTI1IDk2LjIxODc1IDc1LjEyNSBDIDk1LjYyNSA3NC41NTg1OTQgOTYuMzQzNzUgNzMuNjc5Njg4IDk2LjcxMDkzOCA3My4yNTc4MTMgTCA5Ni44MjAzMTMgNzMuMTMyODEzIEwgOTYuMzk4NDM4IDcyLjc2NTYyNSBDIDk1Ljk2ODc1IDczLjI1NzgxMyA5NS41ODU5MzggNzMuODEyNSA5NS4xNjAxNTYgNzQuMzA0Njg4IEMgOTQuNzIyNjU2IDc0LjgwODU5NCA5NC4yMjY1NjMgNzUuMjY1NjI1IDkzLjg1OTM3NSA3NS42ODM1OTQgTCA5OC4zMDg1OTQgODUuMzk0NTMxIEwgODguMTEzMjgxIDgyLjI5Njg3NSBDIDg3Ljc0NjA5NCA4Mi43MTg3NSA4Ny40Mzc1IDgzLjE4NzUgODcuMDcwMzEzIDgzLjYwOTM3NSBDIDg2LjU3MDMxMyA4NC4xODc1IDg2LjAyNzM0NCA4NC42OTkyMTkgODUuNTI3MzQ0IDg1LjI3MzQzOCBMIDg1Ljk0NTMxMyA4NS42NDA2MjUgTCA4Ni4xMDU0NjkgODUuNDU3MDMxICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEzLjY5OTM0MSUsMTIuMTk5NDAyJSwxMi41JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDk4Ljc2MTcxOSA3MS4yMjI2NTYgQyA5OS4yMzQzNzUgNzAuNzUgOTkuODAwNzgxIDcwLjMxNjQwNiAxMDAuNDg0Mzc1IDcxIEwgMTA3LjM3MTA5NCA3Ny44OTQ1MzEgQyAxMDguMDU4NTk0IDc4LjU4MjAzMSAxMDcuNjIxMDk0IDc5LjE0NDUzMSAxMDcuMTQ4NDM4IDc5LjYxNzE4OCBMIDEwNi45NjQ4NDQgNzkuODA0Njg4IEwgMTA3LjM1OTM3NSA4MC4xOTkyMTkgQyAxMDguMTA5Mzc1IDc5LjQ0OTIxOSAxMDkuNjIxMDk0IDc3LjgzMjAzMSAxMTAuODA4NTk0IDc2LjY0ODQzOCBDIDExMS45OTIxODggNzUuNDY0ODQ0IDExMy41NTg1OTQgNzQuMDA3ODEzIDExNC4zOTg0MzggNzMuMTY0MDYzIEMgMTEzLjgyMDMxMyA3Mi4zNDc2NTYgMTEzLjI4MTI1IDcxLjQ5MjE4OCAxMTIuNzU3ODEzIDcwLjYyNSBMIDExMi4yOTY4NzUgNzAuOTAyMzQ0IEMgMTEzLjM5ODQzOCA3Mi43OTY4NzUgMTEyLjgwODU5NCA3My41OTc2NTYgMTExLjIyNjU2MyA3NS4xNzU3ODEgQyAxMTAuMzg2NzE5IDc2LjAxNTYyNSAxMDkuNjIxMDk0IDc2Ljc4MTI1IDEwOC43Njk1MzEgNzUuOTI1NzgxIEwgMTA1LjcwMzEyNSA3Mi44NTkzNzUgTCAxMDcuMjg1MTU2IDcxLjI4MTI1IEMgMTA4LjE5MTQwNiA3MC4zNzEwOTQgMTA4Ljc0NjA5NCA3MC44NDc2NTYgMTA5LjYxMzI4MSA3MS41NTg1OTQgTCAxMDkuOTI5Njg4IDcxLjA4NTkzOCBDIDEwOS40MDIzNDQgNzAuNjA5Mzc1IDEwOC44OTA2MjUgNzAuMTI1IDEwOC4zOTA2MjUgNjkuNjI1IEMgMTA3Ljg3ODkwNiA2OS4xMDkzNzUgMTA3LjM3ODkwNiA2OC41ODU5MzggMTA2Ljg5MDYyNSA2OC4wNDI5NjkgTCAxMDYuNDk2MDk0IDY4LjQzNzUgQyAxMDcuMTI4OTA2IDY5LjIyNjU2MyAxMDcuNDAyMzQ0IDY5Ljg0NzY1NiAxMDYuNjEzMjgxIDcwLjYzNjcxOSBMIDEwNS4wNTA3ODEgNzIuMTk5MjE5IEwgMTAxLjYwNTQ2OSA2OC43NTM5MDYgTCAxMDMuNDMzNTk0IDY2LjkyNTc4MSBDIDEwNC44MTY0MDYgNjUuNTQyOTY5IDEwNS42NTYyNSA2Ni4wNzAzMTMgMTA2LjU3ODEyNSA2Ni44NTkzNzUgTCAxMDYuODY3MTg4IDY2LjM1OTM3NSBDIDEwNi4yNSA2NS44MjAzMTMgMTA1LjM2NzE4OCA2NC45NjQ4NDQgMTA0LjgyODEyNSA2NC4zNzUgQyAxMDMuOTMzNTk0IDY1LjI2NTYyNSAxMDIuNjE3MTg4IDY2LjY4NzUgMTAxLjUxMTcxOSA2Ny43OTI5NjkgQyAxMDAuNDA2MjUgNjguODk0NTMxIDk4Ljk4NDM3NSA3MC4yMTA5MzggOTguMTgzNTk0IDcxLjAxMTcxOSBMIDk4LjU3ODEyNSA3MS40MDYyNSBMIDk4Ljc2MTcxOSA3MS4yMjI2NTYgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoMTMuNjk5MzQxJSwxMi4xOTk0MDIlLDEyLjUlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMTA3LjU3MDMxMyA2Mi40MzM1OTQgQyAxMDguMTk1MzEzIDYxLjg3ODkwNiAxMDkuMjU3ODEzIDYxLjc4OTA2MyAxMDkuOTQ1MzEzIDYyLjU3MDMxMyBMIDExNS4xMTcxODggNjguNDQ5MjE5IEMgMTE2LjEwMTU2MyA2OS41NjY0MDYgMTE2LjM4NjcxOSA3MC40ODA0NjkgMTE1LjQyMTg3NSA3MS4zMjgxMjUgTCAxMTUuMjI2NTYzIDcxLjUgTCAxMTUuNTk3NjU2IDcxLjkxNzk2OSBDIDExNi4yMjI2NTYgNzEuMzY3MTg4IDExNi44MTY0MDYgNzAuNzQ2MDk0IDExNy40NDUzMTMgNzAuMTkxNDA2IEMgMTE4LjA0Njg3NSA2OS42NjQwNjMgMTE4LjY5NTMxMyA2OS4xOTE0MDYgMTE5LjI5Njg3NSA2OC42NjQwNjMgTCAxMTguOTI1NzgxIDY4LjI0MjE4OCBMIDExOC42OTE0MDYgNjguNDUzMTI1IEMgMTE3LjYxMzI4MSA2OS4zOTg0MzggMTE3LjAwNzgxMyA2OS4xODc1IDExNS45NDE0MDYgNjcuOTc2NTYzIEwgMTEwLjg3ODkwNiA2Mi4yMjI2NTYgTCAxMjUuMTIxMDk0IDYzLjkxMDE1NiBMIDEyNS42NTIzNDQgNjMuNDQxNDA2IEMgMTI1LjE5OTIxOSA2My4wNzAzMTMgMTI0Ljc1NzgxMyA2Mi41OTM3NSAxMjQuMzI0MjE5IDYyLjEwNTQ2OSBMIDExOC43MzQzNzUgNTUuNzUzOTA2IEMgMTE3LjI3MzQzOCA1NC4wODk4NDQgMTE3LjgzMjAzMSA1My40MDIzNDQgMTE4LjQxNzk2OSA1Mi44ODY3MTkgTCAxMTguNjI4OTA2IDUyLjY5OTIxOSBMIDExOC4yNTc4MTMgNTIuMjgxMjUgQyAxMTcuNjg3NSA1Mi43ODUxNTYgMTE3LjE2MDE1NiA1My4zNDM3NSAxMTYuNTg5ODQ0IDUzLjg0NzY1NiBDIDExNS45MzM1OTQgNTQuNDI1NzgxIDExNS4yNDIxODggNTQuOTMzNTk0IDExNC41ODU5MzggNTUuNTExNzE5IEwgMTE0Ljk1MzEyNSA1NS45MzM1OTQgTCAxMTUuMjYxNzE5IDU1LjY2NDA2MyBDIDExNS42Nzk2ODggNTUuMjkyOTY5IDExNi42MjUgNTQuNzYxNzE5IDExNy42MzI4MTMgNTUuOTA2MjUgTCAxMjIuMjM4MjgxIDYxLjE0MDYyNSBMIDEyMi4yMzQzNzUgNjEuMTk1MzEzIEwgMTA5Ljg2NzE4OCA1OS42Njc5NjkgQyAxMDkuNDQ5MjE5IDYwLjAzNTE1NiAxMDkuMDkzNzUgNjAuNDQ1MzEzIDEwOC42NzU3ODEgNjAuODE2NDA2IEMgMTA4LjE0NDUzMSA2MS4yODEyNSAxMDcuNTUwNzgxIDYxLjcwNzAzMSAxMDcuMDE5NTMxIDYyLjE3MTg3NSBMIDEwNy4zODY3MTkgNjIuNTkzNzUgTCAxMDcuNTcwMzEzIDYyLjQzMzU5NCAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMy42OTkzNDElLDEyLjE5OTQwMiUsMTIuNSUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAxMjEuMjQyMTg4IDUzLjI2OTUzMSBMIDEyMS42ODc1IDUyLjkzMzU5NCBDIDEyMS4wODIwMzEgNTEuNjgzNTk0IDEyMC45MjE4NzUgNTEuMzgyODEzIDEyMi4wMzEyNSA1MC41MzUxNTYgTCAxMjQuNDQ5MjE5IDQ4LjY4MzU5NCBMIDEzMC40ODgyODEgNTYuNTY2NDA2IEMgMTMxLjM4MjgxMyA1Ny43MzA0NjkgMTMxLjAyNzM0NCA1OC4xMjEwOTQgMTMwLjIxNDg0NCA1OC43NDIxODggTCAxMjkuOTMzNTk0IDU4Ljk2MDkzOCBMIDEzMC4yNzM0MzggNTkuNDAyMzQ0IEMgMTMwLjg0NzY1NiA1OC45NjA5MzggMTMxLjgzNTkzOCA1OC4xMDkzNzUgMTMyLjcyMjY1NiA1Ny40MzM1OTQgQyAxMzMuNTE5NTMxIDU2LjgyMDMxMyAxMzQuNTk3NjU2IDU2LjA4OTg0NCAxMzUuMTc1NzgxIDU1LjY0ODQzOCBMIDEzNC44MzU5MzggNTUuMjAzMTI1IEwgMTM0LjU1NDY4OCA1NS40MTc5NjkgQyAxMzMuODQ3NjU2IDU1Ljk2MDkzOCAxMzMuMjI2NTYzIDU2LjIyNjU2MyAxMzIuMzU1NDY5IDU1LjA4OTg0NCBMIDEyNi4zMzk4NDQgNDcuMjM0Mzc1IEwgMTI4Ljc2MTcxOSA0NS4zNzg5MDYgQyAxMjkuNzUgNDQuNjIxMDk0IDEzMC40OTIxODggNDUuNDM3NSAxMzAuOTQxNDA2IDQ1Ljk2MDkzOCBMIDEzMS4yNTc4MTMgNDUuNDYwOTM4IEMgMTMwLjk1MzEyNSA0NS4wNTg1OTQgMTMwLjY0ODQzOCA0NC42NjAxNTYgMTMwLjM3MTA5NCA0NC4yMzgyODEgQyAxMzAuMTA5Mzc1IDQzLjgwODU5NCAxMjkuODYzMjgxIDQzLjM2MzI4MSAxMjkuNjE3MTg4IDQyLjkyMTg3NSBMIDEyOS4yMTg3NSA0My4xMzI4MTMgQyAxMjkuNTI3MzQ0IDQzLjU5NzY1NiAxMjkuMTcxODc1IDQzLjg5NDUzMSAxMjguNzczNDM4IDQ0LjE5OTIxOSBMIDEyMS4xNTIzNDQgNTAuMDM1MTU2IEMgMTIwLjc1NzgxMyA1MC4zMzk4NDQgMTIwLjM5ODQzOCA1MC42NDA2MjUgMTE5Ljk0MTQwNiA1MC4yODUxNTYgTCAxMTkuNTg1OTM4IDUwLjU1ODU5NCBDIDExOS45MTQwNjMgNTAuOTg0Mzc1IDEyMC4xOTkyMTkgNTEuNDIxODc1IDEyMC40NjA5MzggNTEuODc4OTA2IEMgMTIwLjc0MjE4OCA1Mi4zNDM3NSAxMjAuOTg0Mzc1IDUyLjgxMjUgMTIxLjI0MjE4OCA1My4yNjk1MzEgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoMTMuNjk5MzQxJSwxMi4xOTk0MDIlLDEyLjUlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMTMxLjkxNDA2MyA0Mi42MjUgQyAxMzIuNDY4NzUgNDIuMjUgMTMzLjEwNTQ2OSA0MS45Mjk2ODggMTMzLjY0ODQzOCA0Mi43MzA0NjkgTCAxMzkuMTA5Mzc1IDUwLjgwMDc4MSBDIDEzOS42NTIzNDQgNTEuNjAxNTYzIDEzOS4xMTcxODggNTIuMDc0MjE5IDEzOC41NjY0MDYgNTIuNDQ5MjE5IEwgMTM4LjM0NzY1NiA1Mi41OTc2NTYgTCAxMzguNjYwMTU2IDUzLjA1ODU5NCBDIDEzOS41MzkwNjMgNTIuNDY0ODQ0IDE0MS4zMzIwMzEgNTEuMTYwMTU2IDE0Mi43MTg3NSA1MC4yMjY1NjMgQyAxNDQuMTAxNTYzIDQ5LjI4NTE1NiAxNDUuOTE0MDYzIDQ4LjE0ODQzOCAxNDYuOTAyMzQ0IDQ3LjQ4NDM3NSBDIDE0Ni40ODgyODEgNDYuNTc0MjE5IDE0Ni4xMjEwOTQgNDUuNjMyODEzIDE0NS43Njk1MzEgNDQuNjc5Njg4IEwgMTQ1LjI2NTYyNSA0NC44NjMyODEgQyAxNDUuOTg4MjgxIDQ2LjkzMzU5NCAxNDUuMjU3ODEzIDQ3LjYwNTQ2OSAxNDMuNDEwMTU2IDQ4Ljg1OTM3NSBDIDE0Mi40MjE4NzUgNDkuNTIzNDM4IDE0MS41MzEyNSA1MC4xMjg5MDYgMTQwLjg1MTU2MyA0OS4xMjg5MDYgTCAxMzguNDI1NzgxIDQ1LjUzOTA2MyBMIDE0MC4yNzM0MzggNDQuMjg5MDYzIEMgMTQxLjMzNTkzOCA0My41NzAzMTMgMTQxLjc4OTA2MyA0NC4xNDA2MjUgMTQyLjUwNzgxMyA0NSBMIDE0Mi45MDYyNSA0NC41OTc2NTYgQyAxNDIuNDc2NTYzIDQ0LjAzMTI1IDE0Mi4wNjY0MDYgNDMuNDU3MDMxIDE0MS42NzE4NzUgNDIuODcxMDk0IEMgMTQxLjI2NTYyNSA0Mi4yNjk1MzEgMTQwLjg3MTA5NCA0MS42NjAxNTYgMTQwLjQ5NjA5NCA0MS4wMzkwNjMgTCAxNDAuMDM1MTU2IDQxLjM1MTU2MyBDIDE0MC41MDc4MTMgNDIuMjQ2MDk0IDE0MC42NjAxNTYgNDIuOTAyMzQ0IDEzOS43MzQzNzUgNDMuNTI3MzQ0IEwgMTM3LjkwMjM0NCA0NC43Njk1MzEgTCAxMzUuMTcxODc1IDQwLjczNDM3NSBMIDEzNy4zMTI1IDM5LjI4NTE1NiBDIDEzOC45Mjk2ODggMzguMTkxNDA2IDEzOS42NTYyNSAzOC44NjcxODggMTQwLjQxMDE1NiAzOS44MTY0MDYgTCAxNDAuNzg5MDYzIDM5LjM3ODkwNiBDIDE0MC4yODUxNTYgMzguNzM0Mzc1IDEzOS41ODIwMzEgMzcuNzI2NTYzIDEzOS4xNjQwNjMgMzcuMDQ2ODc1IEMgMTM4LjExNzE4OCAzNy43NTM5MDYgMTM2LjU1ODU5NCAzOC44OTg0MzggMTM1LjI2NTYyNSAzOS43NzM0MzggQyAxMzMuOTY4NzUgNDAuNjQ4NDM4IDEzMi4zMjQyMTkgNDEuNjcxODc1IDEzMS4zODY3MTkgNDIuMzA4NTk0IEwgMTMxLjY5OTIxOSA0Mi43Njk1MzEgTCAxMzEuOTE0MDYzIDQyLjYyNSAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMy42OTkzNDElLDEyLjE5OTQwMiUsMTIuNSUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAxNDYuNTgyMDMxIDMzLjIzNDM3NSBDIDE0OC4wMDc4MTMgMzIuMzkwNjI1IDE0OS40NjA5MzggMzIuNzYxNzE5IDE1MC4zMDQ2ODggMzQuMTgzNTk0IEMgMTUxLjQyNTc4MSAzNi4wNzAzMTMgMTUwLjkyMTg3NSAzNy4xOTE0MDYgMTQ5LjMyMDMxMyAzOC4xNDA2MjUgTCAxNDguNTM5MDYzIDM4LjYwNTQ2OSBMIDE0NS43MTA5MzggMzMuODM5ODQ0IEMgMTQ1LjkyNTc4MSAzMy42OTE0MDYgMTQ2LjEwNTQ2OSAzMy41MTk1MzEgMTQ2LjU4MjAzMSAzMy4yMzQzNzUgWiBNIDE0Mi40MzM1OTQgMzUuNTcwMzEzIEMgMTQyLjkyOTY4OCAzNS4yNzM0MzggMTQzLjU5NzY1NiAzNC45NDE0MDYgMTQ0LjI4OTA2MyAzNi4xMDkzNzUgTCAxNDkuMTEzMjgxIDQ0LjIzNDM3NSBDIDE0OS40NjQ4NDQgNDQuODI0MjE5IDE0OS4wODIwMzEgNDUuNDIxODc1IDE0OC40ODgyODEgNDUuNzY5NTMxIEwgMTQ4LjE5OTIxOSA0NS45NDE0MDYgTCAxNDguNDg0Mzc1IDQ2LjQyMTg3NSBDIDE0OS4yODUxNTYgNDUuOTQ5MjE5IDE1MCA0NS40Mzc1IDE1MC43NjU2MjUgNDQuOTgwNDY5IEMgMTUxLjY3OTY4OCA0NC40NDE0MDYgMTUyLjY0NDUzMSA0My45NTMxMjUgMTUzLjU1NDY4OCA0My40MTQwNjMgTCAxNTMuMjY5NTMxIDQyLjkzMzU5NCBMIDE1Mi45ODA0NjkgNDMuMTA1NDY5IEMgMTUyLjI0NjA5NCA0My41MzkwNjMgMTUxLjY0NDUzMSA0My44MzU5MzggMTUwLjkxMDE1NiA0Mi42MDE1NjMgTCAxNDguODc4OTA2IDM5LjE3OTY4OCBMIDE0OS45Mzc1IDM4LjU1NDY4OCBDIDE1Mi4wNjY0MDYgMzkuNzc3MzQ0IDE1NC4xNDg0MzggNDAuODc4OTA2IDE1Ni4zMzU5MzggNDEuNzYxNzE5IEMgMTU2LjgzMjAzMSA0MS40Njg3NSAxNTcuMzA4NTk0IDQxLjA5NzY1NiAxNTcuODA0Njg4IDQwLjgwNDY4OCBDIDE1OC4zMjgxMjUgNDAuNDkyMTg4IDE1OC44Nzg5MDYgNDAuMjUzOTA2IDE1OS40MDYyNSAzOS45Mzc1IEwgMTU5LjEyMTA5NCAzOS40NjA5MzggQyAxNTguMjgxMjUgMzkuODI4MTI1IDE1Ny44NDc2NTYgMzkuODI0MjE5IDE1Ny4wMDM5MDYgMzkuNDIxODc1IEwgMTUxLjgzOTg0NCAzNi45NDkyMTkgQyAxNTIuODA4NTk0IDM1LjcwMzEyNSAxNTMuMjQyMTg4IDM0LjI1MzkwNiAxNTIuMzkwNjI1IDMyLjgxNjQwNiBDIDE1MS4wNDI5NjkgMzAuNTQ2ODc1IDE0OC45Mjk2ODggMzEuMDY2NDA2IDE0Ni45MTQwNjMgMzIuMjYxNzE5IEMgMTQ2LjA2NjQwNiAzMi43NjE3MTkgMTQ1LjMzNTkzOCAzMy4yODEyNSAxNDQuMzc4OTA2IDMzLjg1MTU2MyBDIDE0My40MDIzNDQgMzQuNDI5Njg4IDE0Mi4zNzEwOTQgMzQuOTUzMTI1IDE0MS44NTkzNzUgMzUuMjU3ODEzIEwgMTQyLjE0NDUzMSAzNS43MzgyODEgTCAxNDIuNDMzNTk0IDM1LjU3MDMxMyAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMy42OTkzNDElLDEyLjE5OTQwMiUsMTIuNSUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAxNTQuNzM0Mzc1IDI4LjQyNTc4MSBDIDE1NS4zMjQyMTkgMjguMTA5Mzc1IDE1NS45OTIxODggMjcuODU5Mzc1IDE1Ni40NDUzMTMgMjguNzE0ODQ0IEwgMTYxLjAxNTYyNSAzNy4zMjAzMTMgQyAxNjEuNDcyNjU2IDM4LjE3NTc4MSAxNjAuODkwNjI1IDM4LjU4OTg0NCAxNjAuMzAwNzgxIDM4LjkwMjM0NCBMIDE2MC4wNzAzMTMgMzkuMDIzNDM4IEwgMTYwLjMzMjAzMSAzOS41MTU2MjUgQyAxNjAuOTcyNjU2IDM5LjE3NTc4MSAxNjEuOTA2MjUgMzguNTk3NjU2IDE2Mi43MTA5MzggMzguMTY3OTY5IEMgMTYzLjUzMTI1IDM3LjczMDQ2OSAxNjQuNTU0Njg4IDM3LjI3MzQzOCAxNjUuMzM5ODQ0IDM2Ljg1NTQ2OSBMIDE2NS4wNzgxMjUgMzYuMzYzMjgxIEwgMTY0Ljg0NzY1NiAzNi40ODQzNzUgQyAxNjQuMjU3ODEzIDM2LjgwMDc4MSAxNjMuNTg5ODQ0IDM3LjA1MDc4MSAxNjMuMTM2NzE5IDM2LjE5NTMxMyBMIDE1OC41NjI1IDI3LjU4OTg0NCBDIDE1OC4xMDkzNzUgMjYuNzM0Mzc1IDE1OC42OTE0MDYgMjYuMzIwMzEzIDE1OS4yODEyNSAyNi4wMDc4MTMgTCAxNTkuNTExNzE5IDI1Ljg4MjgxMyBMIDE1OS4yNSAyNS4zOTA2MjUgQyAxNTguNDc2NTYzIDI1LjgwNDY4OCAxNTcuNTI3MzQ0IDI2LjM5NDUzMSAxNTYuNzA3MDMxIDI2LjgyODEyNSBDIDE1NS45MDIzNDQgMjcuMjU3ODEzIDE1NC44ODI4MTMgMjcuNzE0ODQ0IDE1NC4yNDIxODggMjguMDU0Njg4IEwgMTU0LjUwMzkwNiAyOC41NDY4NzUgTCAxNTQuNzM0Mzc1IDI4LjQyNTc4MSAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMy42OTkzNDElLDEyLjE5OTQwMiUsMTIuNSUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAxNjYuNzE4NzUgMjQuMDMxMjUgTCAxNzAuNTExNzE5IDI4LjA2MjUgTCAxNjcuMzY3MTg4IDI5LjU0Njg3NSBMIDE2Ni42ODM1OTQgMjQuMDUwNzgxIFogTSAxNjYuOTQ5MjE5IDM0LjAyMzQzOCBDIDE2Ny4wMzEyNSAzNC44NDc2NTYgMTY2LjY1NjI1IDM1LjQ5NjA5NCAxNjYuMDAzOTA2IDM1LjgwODU5NCBMIDE2NS45MDIzNDQgMzUuODU1NDY5IEwgMTY2LjE0MDYyNSAzNi4zNTkzNzUgQyAxNjYuNzMwNDY5IDM2LjAzOTA2MyAxNjcuMzIwMzEzIDM1LjcxODc1IDE2Ny45MjU3ODEgMzUuNDMzNTk0IEMgMTY4LjU5NzY1NiAzNS4xMTcxODggMTY5LjMwMDc4MSAzNC44MjQyMTkgMTY5Ljk5MjE4OCAzNC41MzkwNjMgTCAxNjkuNzUzOTA2IDM0LjAzNTE1NiBMIDE2OS41NjY0MDYgMzQuMTIxMDk0IEMgMTY5LjAxMTcxOSAzNC4zODY3MTkgMTY4LjI2NTYyNSAzNC42MzY3MTkgMTY4LjAyNzM0NCAzNC4xMjg5MDYgQyAxNjcuODg2NzE5IDMzLjgyODEyNSAxNjcuODgyODEzIDMzLjI5Njg3NSAxNjcuNzgxMjUgMzIuNjQ0NTMxIEwgMTY3LjQ5MjE4OCAzMC42NDA2MjUgTCAxNzEuMzEyNSAyOC44Mzk4NDQgTCAxNzIuODg2NzE5IDMwLjQ4MDQ2OSBDIDE3My4zMjgxMjUgMzAuOTI5Njg4IDE3My42OTE0MDYgMzEuMzEyNSAxNzMuNzk2ODc1IDMxLjUzMTI1IEMgMTczLjk5MjE4OCAzMS45NTMxMjUgMTczLjM3MTA5NCAzMi4zMjgxMjUgMTcyLjk4NDM3NSAzMi41MTE3MTkgTCAxNzIuNzk2ODc1IDMyLjU5NzY1NiBMIDE3My4wMzUxNTYgMzMuMTA1NDY5IEMgMTczLjg3ODkwNiAzMi42NjQwNjMgMTc0LjcwMzEyNSAzMi4yMzQzNzUgMTc1LjUyNzM0NCAzMS44NDc2NTYgQyAxNzYuMzM1OTM4IDMxLjQ2NDg0NCAxNzcuMTA1NDY5IDMxLjE0MDYyNSAxNzcuODc4OTA2IDMwLjgxNjQwNiBMIDE3Ny42NDA2MjUgMzAuMzEyNSBMIDE3Ny41MzkwNjMgMzAuMzU5Mzc1IEMgMTc2Ljk4NDM3NSAzMC42MjEwOTQgMTc2LjUzOTA2MyAzMC41ODU5MzggMTc2LjExMzI4MSAzMC4yMTA5MzggQyAxNzUuNjU2MjUgMjkuODA4NTk0IDE3NS4xNjAxNTYgMjkuMjgxMjUgMTc0LjY3OTY4OCAyOC43ODkwNjMgTCAxNjcuNDMzNTk0IDIxLjQ1MzEyNSBDIDE2Ny4zMjAzMTMgMjEuMzQzNzUgMTY3LjE5OTIxOSAyMS4yMTQ4NDQgMTY3LjA4NTkzOCAyMS4xMDU0NjkgQyAxNjcuMDI3MzQ0IDIxLjA3MDMxMyAxNjYuOTkyMTg4IDIxLjA4NTkzOCAxNjYuOTQxNDA2IDIxLjEwOTM3NSBDIDE2Ni44OTA2MjUgMjEuMTMyODEzIDE2Ni44NjcxODggMjEuMTY0MDYzIDE2Ni44MjQyMTkgMjEuMjA3MDMxIEMgMTY2LjYwMTU2MyAyMS41NTg1OTQgMTY2LjA4NTkzOCAyMi4yMTQ4NDQgMTY1LjYzNjcxOSAyMi42NTIzNDQgQyAxNjUuODI4MTI1IDIzLjMyMDMxMyAxNjUuOTIxODc1IDI0LjMwNDY4OCAxNjUuOTk2MDk0IDI1LjAzMTI1IEwgMTY2Ljk0OTIxOSAzNC4wMjM0MzggIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoMTMuNjk5MzQxJSwxMi4xOTk0MDIlLDEyLjUlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMTc0LjM2NzE4OCAxOC43ODUxNTYgQyAxNzUuMTQ4NDM4IDE4LjQ4MDQ2OSAxNzYuMTc1NzgxIDE4Ljc2MTcxOSAxNzYuNTU0Njg4IDE5LjczMDQ2OSBMIDE3OS40MDIzNDQgMjcuMDIzNDM4IEMgMTc5Ljk0MTQwNiAyOC40MTAxNTYgMTc5Ljg5NDUzMSAyOS4zNjcxODggMTc4LjY5OTIxOSAyOS44MzIwMzEgTCAxNzguNDU3MDMxIDI5LjkyNTc4MSBMIDE3OC42NjAxNTYgMzAuNDQ1MzEzIEMgMTc5LjQ0MTQwNiAzMC4xNDA2MjUgMTgwLjIxMDkzOCAyOS43NjE3MTkgMTgwLjk4ODI4MSAyOS40NTcwMzEgQyAxODEuNzM0Mzc1IDI5LjE2Nzk2OSAxODIuNTA3ODEzIDI4Ljk0NTMxMyAxODMuMjUgMjguNjU2MjUgTCAxODMuMDUwNzgxIDI4LjEzNjcxOSBMIDE4Mi43NTM5MDYgMjguMjUgQyAxODEuNDIxODc1IDI4Ljc2OTUzMSAxODAuOTIxODc1IDI4LjM2NzE4OCAxODAuMzM1OTM4IDI2Ljg1OTM3NSBMIDE3Ny41NTA3ODEgMTkuNzIyNjU2IEwgMTkwLjM1MTU2MyAyNi4xODM1OTQgTCAxOTEuMDExNzE5IDI1LjkyNTc4MSBDIDE5MC43MTQ4NDQgMjUuNDIxODc1IDE5MC40NjA5MzggMjQuODI0MjE5IDE5MC4yMjI2NTYgMjQuMjE4NzUgTCAxODcuMTQ4NDM4IDE2LjMzNTkzOCBDIDE4Ni4zNDM3NSAxNC4yNzM0MzggMTg3LjEwMTU2MyAxMy44MTY0MDYgMTg3LjgzMjAzMSAxMy41MzEyNSBMIDE4OC4wODk4NDQgMTMuNDI5Njg4IEwgMTg3Ljg4NjcxOSAxMi45MTAxNTYgQyAxODcuMTc1NzgxIDEzLjE4NzUgMTg2LjQ5MjE4OCAxMy41MzUxNTYgMTg1Ljc4NTE1NiAxMy44MTI1IEMgMTg0Ljk2ODc1IDE0LjEyODkwNiAxODQuMTQ0NTMxIDE0LjM3MTA5NCAxODMuMzMyMDMxIDE0LjY5MTQwNiBMIDE4My41MzUxNTYgMTUuMjEwOTM4IEwgMTgzLjkxNDA2MyAxNS4wNTg1OTQgQyAxODQuNDMzNTk0IDE0Ljg1OTM3NSAxODUuNTAzOTA2IDE0LjY3OTY4OCAxODYuMDU4NTk0IDE2LjEwMTU2MyBMIDE4OC41OTM3NSAyMi41OTc2NTYgTCAxODguNTcwMzEzIDIyLjY0NDUzMSBMIDE3Ny40NzY1NjMgMTYuOTc2NTYzIEMgMTc2Ljk1NzAzMSAxNy4xNzk2ODggMTc2LjQ4MDQ2OSAxNy40NDE0MDYgMTc1Ljk2MDkzOCAxNy42NDQ1MzEgQyAxNzUuMzAwNzgxIDE3LjkwMjM0NCAxNzQuNjAxNTYzIDE4LjA5NzY1NiAxNzMuOTQxNDA2IDE4LjM1NTQ2OSBMIDE3NC4xNDQ1MzEgMTguODc1IEwgMTc0LjM2NzE4OCAxOC43ODUxNTYgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoMTMuNjk5MzQxJSwxMi4xOTk0MDIlLDEyLjUlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMjAxLjE3NTc4MSAxMC45NjQ4NDQgTCAyMDEuMjEwOTM4IDEwLjk1MzEyNSBMIDIwNC4zMDA3ODEgMTUuNTQ2ODc1IEwgMjAwLjk1MzEyNSAxNi41IFogTSAyMDAuNTQ2ODc1IDIyLjM5ODQzOCBDIDIwMS4yNjU2MjUgMjIuMTk1MzEzIDIwMi4wMDc4MTMgMjIuMDIzNDM4IDIwMi43MzQzNzUgMjEuODU1NDY5IEwgMjAyLjU3ODEyNSAyMS4zMTY0MDYgTCAyMDIuMzgyODEzIDIxLjM3NSBDIDIwMS43OTI5NjkgMjEuNTQyOTY5IDIwMS4wMTU2MjUgMjEuNjY3OTY5IDIwMC44NjMyODEgMjEuMTI4OTA2IEMgMjAwLjc2OTUzMSAyMC44MDg1OTQgMjAwLjg1MTU2MyAyMC4yODEyNSAyMDAuODU5Mzc1IDE5LjYyMTA5NCBMIDIwMC45MDIzNDQgMTcuNjAxNTYzIEwgMjA0Ljk2MDkzOCAxNi40NDE0MDYgTCAyMDYuMjUgMTguMzE2NDA2IEMgMjA2LjYwOTM3NSAxOC44MzU5MzggMjA2LjkwNjI1IDE5LjI2OTUzMSAyMDYuOTc2NTYzIDE5LjUwMzkwNiBDIDIwNy4xMDE1NjMgMTkuOTQ5MjE5IDIwNi40MjU3ODEgMjAuMjIyNjU2IDIwNi4wMTU2MjUgMjAuMzM5ODQ0IEwgMjA1LjgxNjQwNiAyMC4zOTQ1MzEgTCAyMDUuOTY4NzUgMjAuOTI5Njg4IEMgMjA2Ljg3MTA5NCAyMC42MzY3MTkgMjA3Ljc1NzgxMyAyMC4zNDM3NSAyMDguNjMyODEzIDIwLjA5Mzc1IEMgMjA5LjQ5MjE4OCAxOS44NTE1NjMgMjEwLjMwNDY4OCAxOS42NTYyNSAyMTEuMTIxMDk0IDE5LjQ2MDkzOCBMIDIxMC45Njg3NSAxOC45MjU3ODEgTCAyMTAuODU5Mzc1IDE4Ljk1NzAzMSBDIDIxMC4yNjk1MzEgMTkuMTI1IDIwOS44MzIwMzEgMTkuMDE1NjI1IDIwOS40NzY1NjMgMTguNTc4MTI1IEMgMjA5LjA4OTg0NCAxOC4xMDU0NjkgMjA4LjY4NzUgMTcuNTA3ODEzIDIwOC4yOTI5NjkgMTYuOTQxNDA2IEwgMjAyLjMzNTkzOCA4LjUyNzM0NCBDIDIwMi4yNDIxODggOC4zOTg0MzggMjAyLjE0MDYyNSA4LjI1MzkwNiAyMDIuMDQ2ODc1IDguMTI1IEMgMjAxLjk5NjA5NCA4LjA4MjAzMSAyMDEuOTYwOTM4IDguMDkzNzUgMjAxLjkwNjI1IDguMTA1NDY5IEMgMjAxLjg1MTU2MyA4LjEyMTA5NCAyMDEuODIwMzEzIDguMTQ4NDM4IDIwMS43NzM0MzggOC4xODM1OTQgQyAyMDEuNDk2MDk0IDguNDk2MDk0IDIwMC44ODI4MTMgOS4wNTg1OTQgMjAwLjM2MzI4MSA5LjQxNzk2OSBDIDIwMC40NDUzMTMgMTAuMTA5Mzc1IDIwMC4zNzg5MDYgMTEuMDk3NjU2IDIwMC4zMzU5MzggMTEuODI0MjE5IEwgMTk5LjgxNjQwNiAyMC44NDc2NTYgQyAxOTkuNzYxNzE5IDIxLjY3NTc4MSAxOTkuMjg5MDYzIDIyLjI1NzgxMyAxOTguNTg5ODQ0IDIyLjQ1MzEyNSBMIDE5OC40ODQzNzUgMjIuNDg0Mzc1IEwgMTk4LjYzNjcxOSAyMy4wMjM0MzggQyAxOTkuMjY5NTMxIDIyLjgwNDY4OCAxOTkuOTAyMzQ0IDIyLjU4NTkzOCAyMDAuNTQ2ODc1IDIyLjM5ODQzOCAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMy42OTkzNDElLDEyLjE5OTQwMiUsMTIuNSUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAyMTkuMzk4NDM4IDE3LjkyNTc4MSBDIDIyMS4yNzM0MzggMTcuNTIzNDM4IDIyMi43ODEyNSAxNi44NTU0NjkgMjI0LjMwNDY4OCAxNi4wNTA3ODEgTCAyMjQuMjM0Mzc1IDE1LjcyMjY1NiBMIDIyMy43NjU2MjUgMTUuNTc4MTI1IEwgMjIzLjE2Nzk2OSAxMi44MTI1IEMgMjIzLjAzMTI1IDEyLjE3NTc4MSAyMjMuMzEyNSAxMS44MTI1IDIyMy45NDkyMTkgMTEuNjc1NzgxIEwgMjI0LjE4NzUgMTEuNjIxMDk0IEwgMjI0LjA2NjQwNiAxMS4wNzgxMjUgQyAyMjMuMjU3ODEzIDExLjI4OTA2MyAyMjIuNDY0ODQ0IDExLjUgMjIxLjY0ODQzOCAxMS42NzU3ODEgQyAyMjAuNzM4MjgxIDExLjg3MTA5NCAyMTkuODIwMzEzIDEyLjAzMTI1IDIxOC45MDIzNDQgMTIuMTkxNDA2IEwgMjE5LjAxOTUzMSAxMi43MzgyODEgTCAyMTkuMjU3ODEzIDEyLjY4NzUgQyAyMTkuOTI5Njg4IDEyLjUzOTA2MyAyMjAuNjc5Njg4IDEyLjU3MDMxMyAyMjAuODM5ODQ0IDEzLjMxNjQwNiBMIDIyMS40ODA0NjkgMTYuMjgxMjUgQyAyMjEuMjg5MDYzIDE2LjU1MDc4MSAyMjAuNDEwMTU2IDE2Ljg5MDYyNSAyMTkuNTM1MTU2IDE3LjA1ODU5NCBDIDIxNi4wNjI1IDE3LjgwODU5NCAyMTMuOTM3NSAxNC45MTc5NjkgMjEzLjI4OTA2MyAxMS45MTc5NjkgQyAyMTIuNjMyODEzIDguODgyODEzIDIxMy43MTQ4NDQgNi4xMzY3MTkgMjE2Ljk2ODc1IDUuNDMzNTk0IEMgMjE5LjA5NzY1NiA0Ljk3NjU2MyAyMjAuODEyNSA1LjQyNTc4MSAyMjEuODM5ODQ0IDcuNTQyOTY5IEwgMjIyLjM3ODkwNiA3LjM5MDYyNSBDIDIyMS45MzM1OTQgNi4zODI4MTMgMjIxLjYzMjgxMyA1IDIyMS40ODgyODEgNC4zMjgxMjUgQyAyMjAuNzU3ODEzIDQuNDY0ODQ0IDIyMC4xMDU0NjkgNC40MzM1OTQgMjE5LjM1OTM3NSA0LjQyNTc4MSBDIDIxOC42MTMyODEgNC40MTQwNjMgMjE3Ljc5Njg3NSA0LjQxNzk2OSAyMTYuNjcxODc1IDQuNjYwMTU2IEMgMjEyLjk5NjA5NCA1LjQ1MzEyNSAyMDkuODcxMDk0IDguNDMzNTk0IDIxMC43ODEyNSAxMi42NTIzNDQgQyAyMTEuNzI2NTYzIDE3LjAzMTI1IDIxNS4zMjQyMTkgMTguODA0Njg4IDIxOS4zOTg0MzggMTcuOTI1NzgxICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEzLjY5OTM0MSUsMTIuMTk5NDAyJSwxMi41JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDIzMC4xMzY3MTkgMy4xOTkyMTkgQyAyMzEuNzczNDM4IDIuOTYwOTM4IDIzMi45NzI2NTYgMy44NTkzNzUgMjMzLjIxMDkzOCA1LjQ5NjA5NCBDIDIzMy41MjczNDQgNy42Njc5NjkgMjMyLjYzMjgxMyA4LjUxMTcxOSAyMzAuNzkyOTY5IDguNzc3MzQ0IEwgMjI5Ljg5MDYyNSA4LjkwNjI1IEwgMjI5LjA5NzY1NiAzLjQyNTc4MSBDIDIyOS4zNTE1NjMgMy4zNjcxODggMjI5LjU4MjAzMSAzLjI3NzM0NCAyMzAuMTM2NzE5IDMuMTk5MjE5IFogTSAyMjUuNDA2MjUgMy43Njk1MzEgQyAyMjUuOTc2NTYzIDMuNjg3NSAyMjYuNzIyNjU2IDMuNjM2NzE5IDIyNi45MTc5NjkgNC45ODA0NjkgTCAyMjguMjczNDM4IDE0LjMyODEyNSBDIDIyOC4zNzEwOTQgMTUuMDExNzE5IDIyNy43ODkwNjMgMTUuNDE0MDYzIDIyNy4xMDkzNzUgMTUuNTExNzE5IEwgMjI2Ljc3NzM0NCAxNS41NTg1OTQgTCAyMjYuODU5Mzc1IDE2LjExMzI4MSBDIDIyNy43NzczNDQgMTUuOTgwNDY5IDIyOC42MzI4MTMgMTUuNzgxMjUgMjI5LjUxNTYyNSAxNS42NTIzNDQgQyAyMzAuNTY2NDA2IDE1LjUgMjMxLjY0NDUzMSAxNS40MTc5NjkgMjMyLjY5MTQwNiAxNS4yNjU2MjUgTCAyMzIuNjEzMjgxIDE0LjcxNDg0NCBMIDIzMi4yODEyNSAxNC43NjE3MTkgQyAyMzEuNDMzNTk0IDE0Ljg4NjcxOSAyMzAuNzY1NjI1IDE0LjkyNTc4MSAyMzAuNTU4NTk0IDEzLjUwNzgxMyBMIDIyOS45ODgyODEgOS41NzAzMTMgTCAyMzEuMjAzMTI1IDkuMzk0NTMxIEMgMjMyLjcwMzEyNSAxMS4zMzk4NDQgMjM0LjIwNzAzMSAxMy4xNDg0MzggMjM1Ljg5NDUzMSAxNC44MDQ2ODggQyAyMzYuNDY0ODQ0IDE0LjcxODc1IDIzNy4wNDI5NjkgMTQuNTYyNSAyMzcuNjEzMjgxIDE0LjQ3NjU2MyBDIDIzOC4yMjI2NTYgMTQuMzkwNjI1IDIzOC44MjAzMTMgMTQuMzc4OTA2IDIzOS40Mjk2ODggMTQuMjg5MDYzIEwgMjM5LjM0NzY1NiAxMy43MzgyODEgQyAyMzguNDI5Njg4IDEzLjc1NzgxMyAyMzguMDMxMjUgMTMuNTg5ODQ0IDIzNy40MDIzNDQgMTIuODk0NTMxIEwgMjMzLjU3NDIxOSA4LjYzNjcxOSBDIDIzNC45NDUzMTMgNy44NTU0NjkgMjM1LjkwMjM0NCA2LjY4MzU5NCAyMzUuNjYwMTU2IDUuMDI3MzQ0IEMgMjM1LjI4MTI1IDIuNDE0MDYzIDIzMy4xMjg5MDYgMi4wODk4NDQgMjMwLjgxMjUgMi40MjU3ODEgQyAyMjkuODM1OTM4IDIuNTY2NDA2IDIyOC45NjQ4NDQgMi43Njk1MzEgMjI3Ljg1OTM3NSAyLjkyOTY4OCBDIDIyNi43MzgyODEgMy4wOTM3NSAyMjUuNTg1OTM4IDMuMTgzNTk0IDIyNC45OTYwOTQgMy4yNjk1MzEgTCAyMjUuMDc4MTI1IDMuODIwMzEzIEwgMjI1LjQwNjI1IDMuNzY5NTMxICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEzLjY5OTM0MSUsMTIuMTk5NDAyJSwxMi41JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDI0NS42NzE4NzUgMi44MjQyMTkgTCAyNDUuNzEwOTM4IDIuODIwMzEzIEwgMjQ3LjgyODEyNSA3LjkzMzU5NCBMIDI0NC4zNTkzNzUgOC4yMDMxMjUgWiBNIDI0Mi43OTI5NjkgMTMuOTAyMzQ0IEMgMjQzLjUzNTE1NiAxMy44NDc2NTYgMjQ0LjI5Njg3NSAxMy44MjQyMTkgMjQ1LjA0Mjk2OSAxMy44MDQ2ODggTCAyNDUgMTMuMjQ2MDk0IEwgMjQ0Ljc5Njg3NSAxMy4yNjE3MTkgQyAyNDQuMTgzNTk0IDEzLjMwODU5NCAyNDMuMzk4NDM4IDEzLjI3NzM0NCAyNDMuMzU1NDY5IDEyLjcyMjY1NiBDIDI0My4zMjgxMjUgMTIuMzkwNjI1IDI0My41MTE3MTkgMTEuODkwNjI1IDI0My42NDg0MzggMTEuMjQyMTg4IEwgMjQ0LjA4OTg0NCA5LjI2OTUzMSBMIDI0OC4yOTY4NzUgOC45NDE0MDYgTCAyNDkuMTkxNDA2IDExLjAzNTE1NiBDIDI0OS40NDE0MDYgMTEuNjA5Mzc1IDI0OS42NDQ1MzEgMTIuMDk3NjU2IDI0OS42NjQwNjMgMTIuMzM5ODQ0IEMgMjQ5LjcwMzEyNSAxMi44MDQ2ODggMjQ4Ljk4NDM3NSAxMi45MzM1OTQgMjQ4LjU1ODU5NCAxMi45Njg3NSBMIDI0OC4zNTU0NjkgMTIuOTg0Mzc1IEwgMjQ4LjM5ODQzOCAxMy41MzkwNjMgQyAyNDkuMzM5ODQ0IDEzLjQyOTY4OCAyNTAuMjY1NjI1IDEzLjMxNjQwNiAyNTEuMTcxODc1IDEzLjI0NjA5NCBDIDI1Mi4wNjI1IDEzLjE3NTc4MSAyNTIuODk4NDM4IDEzLjE0ODQzOCAyNTMuNzM4MjgxIDEzLjEyMTA5NCBMIDI1My42OTE0MDYgMTIuNTYyNSBMIDI1My41ODIwMzEgMTIuNTc0MjE5IEMgMjUyLjk2ODc1IDEyLjYyMTA5NCAyNTIuNTYyNSAxMi40Mjk2ODggMjUyLjMwMDc4MSAxMS45Mjk2ODggQyAyNTIuMDE1NjI1IDExLjM5MDYyNSAyNTEuNzM4MjgxIDEwLjcyMjY1NiAyNTEuNDY0ODQ0IDEwLjA4OTg0NCBMIDI0Ny4yOTI5NjkgMC42NjQwNjMgQyAyNDcuMjI2NTYzIDAuNTE5NTMxIDI0Ny4xNTYyNSAwLjM1NTQ2OSAyNDcuMDg5ODQ0IDAuMjEwOTM4IEMgMjQ3LjA1MDc4MSAwLjE2MDE1NiAyNDcuMDExNzE5IDAuMTYwMTU2IDI0Ni45NTcwMzEgMC4xNjc5NjkgQyAyNDYuOTAyMzQ0IDAuMTcxODc1IDI0Ni44NjcxODggMC4xOTE0MDYgMjQ2LjgxMjUgMC4yMTQ4NDQgQyAyNDYuNDc2NTYzIDAuNDY0ODQ0IDI0NS43NjU2MjUgMC44OTQ1MzEgMjQ1LjE4NzUgMS4xNDQ1MzEgQyAyNDUuMTI4OTA2IDEuODM5ODQ0IDI0NC44NjcxODggMi43OTI5NjkgMjQ0LjY4MzU5NCAzLjQ5NjA5NCBMIDI0Mi4zODI4MTMgMTIuMjM4MjgxIEMgMjQyLjE2NDA2MyAxMy4wMzkwNjMgMjQxLjU4OTg0NCAxMy41MTU2MjUgMjQwLjg2MzI4MSAxMy41NzAzMTMgTCAyNDAuNzUzOTA2IDEzLjU3ODEyNSBMIDI0MC43OTY4NzUgMTQuMTM2NzE5IEMgMjQxLjQ2MDkzOCAxNC4wNDY4NzUgMjQyLjEyNSAxMy45NTcwMzEgMjQyLjc5Mjk2OSAxMy45MDIzNDQgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoMTMuNjk5MzQxJSwxMi4xOTk0MDIlLDEyLjUlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMjYwLjE2Nzk2OSAwLjY4MzU5NCBDIDI2MS44MjAzMTMgMC42NjAxNTYgMjYyLjg5ODQzOCAxLjcwMzEyNSAyNjIuOTI1NzgxIDMuMzU1NDY5IEMgMjYyLjk2MDkzOCA1LjU1MDc4MSAyNjEuOTY4NzUgNi4yNzM0MzggMjYwLjEwOTM3NSA2LjMwNDY4OCBMIDI1OS4xOTUzMTMgNi4zMTY0MDYgTCAyNTkuMTA5Mzc1IDAuNzc3MzQ0IEMgMjU5LjM2NzE4OCAwLjc1MzkwNiAyNTkuNjA5Mzc1IDAuNjk1MzEzIDI2MC4xNjc5NjkgMC42ODM1OTQgWiBNIDI1NS40MDYyNSAwLjY0ODQzOCBDIDI1NS45ODA0NjkgMC42NDA2MjUgMjU2LjcyNjU2MyAwLjY4MzU5NCAyNTYuNzQ2MDk0IDIuMDQyOTY5IEwgMjU2Ljg5ODQzOCAxMS40ODgyODEgQyAyNTYuOTEwMTU2IDEyLjE3NTc4MSAyNTYuMjgxMjUgMTIuNTAzOTA2IDI1NS41OTM3NSAxMi41MTE3MTkgTCAyNTUuMjYxNzE5IDEyLjUxOTUzMSBMIDI1NS4yNjk1MzEgMTMuMDc0MjE5IEMgMjU2LjE5OTIxOSAxMy4wNjI1IDI1Ny4wNzAzMTMgMTIuOTcyNjU2IDI1Ny45NjQ4NDQgMTIuOTYwOTM4IEMgMjU5LjAyMzQzOCAxMi45NDE0MDYgMjYwLjEwNTQ2OSAxMyAyNjEuMTY0MDYzIDEyLjk4MDQ2OSBMIDI2MS4xNTIzNDQgMTIuNDI1NzgxIEwgMjYwLjgyMDMxMyAxMi40Mjk2ODggQyAyNTkuOTY0ODQ0IDEyLjQ0MTQwNiAyNTkuMjkyOTY5IDEyLjM5ODQzOCAyNTkuMjY5NTMxIDEwLjk2NDg0NCBMIDI1OS4yMDcwMzEgNi45ODgyODEgTCAyNjAuNDMzNTk0IDYuOTY4NzUgQyAyNjEuNjc1NzgxIDkuMDg1OTM4IDI2Mi45Mzc1IDExLjA3NDIxOSAyNjQuMzk4NDM4IDEyLjkyOTY4OCBDIDI2NC45NzY1NjMgMTIuOTIxODc1IDI2NS41NzAzMTMgMTIuODM1OTM4IDI2Ni4xNDQ1MzEgMTIuODI4MTI1IEMgMjY2Ljc1NzgxMyAxMi44MTY0MDYgMjY3LjM1NTQ2OSAxMi44ODI4MTMgMjY3Ljk2ODc1IDEyLjg3MTA5NCBMIDI2Ny45NjA5MzggMTIuMzE2NDA2IEMgMjY3LjA0Njg3NSAxMi4yMTg3NSAyNjYuNjcxODc1IDEyIDI2Ni4xMzY3MTkgMTEuMjI2NTYzIEwgMjYyLjg4MjgxMyA2LjUxOTUzMSBDIDI2NC4zNDM3NSA1LjkxNzk2OSAyNjUuNDQxNDA2IDQuODc4OTA2IDI2NS40MTQwNjMgMy4yMDMxMjUgQyAyNjUuMzcxMDk0IDAuNTY2NDA2IDI2My4yODEyNSAtMC4wMzUxNTYzIDI2MC45Mzc1IDAuMDAzOTA2MjUgQyAyNTkuOTUzMTI1IDAuMDE5NTMxMyAyNTkuMDU4NTk0IDAuMTA5Mzc1IDI1Ny45NDUzMTMgMC4xMjg5MDYgQyAyNTYuODA4NTk0IDAuMTQ0NTMxIDI1NS42NTYyNSAwLjA4OTg0MzggMjU1LjA2MjUgMC4wOTc2NTYzIEwgMjU1LjA3MDMxMyAwLjY1NjI1IEwgMjU1LjQwNjI1IDAuNjQ4NDM4ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEzLjY5OTM0MSUsMTIuMTk5NDAyJSwxMi41JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDI3Mi4xNjc5NjkgMTMuMDE1NjI1IEMgMjczLjA5NzY1NiAxMy4wNDY4NzUgMjc0LjIxMDkzOCAxMy4xNjAxNTYgMjc1LjEwMTU2MyAxMy4xOTE0MDYgTCAyNzUuMTIxMDk0IDEyLjYzMjgxMyBMIDI3NC44NjMyODEgMTIuNjI1IEMgMjc0LjE5MTQwNiAxMi42MDE1NjMgMjczLjQ4ODI4MSAxMi40ODQzNzUgMjczLjUyMzQzOCAxMS41MTU2MjUgTCAyNzMuODY3MTg4IDEuNzc3MzQ0IEMgMjczLjg5ODQzOCAwLjgxMjUgMjc0LjYwOTM3NSAwLjc0MjE4OCAyNzUuMjc3MzQ0IDAuNzY1NjI1IEwgMjc1LjUzOTA2MyAwLjc3MzQzOCBMIDI3NS41NTg1OTQgMC4yMTg3NSBDIDI3NC42ODM1OTQgMC4xODc1IDI3My41NjY0MDYgMC4yMjI2NTYgMjcyLjYzNjcxOSAwLjE4NzUgQyAyNzEuNzI2NTYzIDAuMTU2MjUgMjcwLjYxMzI4MSAwLjA0Mjk2ODggMjY5Ljg5MDYyNSAwLjAxNTYyNSBMIDI2OS44NzEwOTQgMC41NzQyMTkgTCAyNzAuMTI4OTA2IDAuNTg1OTM4IEMgMjcwLjgwMDc4MSAwLjYwOTM3NSAyNzEuNTAzOTA2IDAuNzI2NTYzIDI3MS40Njg3NSAxLjY5MTQwNiBMIDI3MS4xMjg5MDYgMTEuNDMzNTk0IEMgMjcxLjA5Mzc1IDEyLjM5ODQzOCAyNzAuMzgyODEzIDEyLjQ2ODc1IDI2OS43MTQ4NDQgMTIuNDQ1MzEzIEwgMjY5LjQ1MzEyNSAxMi40MzM1OTQgTCAyNjkuNDMzNTk0IDEyLjk5MjE4OCBDIDI3MC4xNjAxNTYgMTMuMDE5NTMxIDI3MS4yNTc4MTMgMTIuOTgwNDY5IDI3Mi4xNjc5NjkgMTMuMDE1NjI1ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEzLjY5OTM0MSUsMTIuMTk5NDAyJSwxMi41JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDI4My4xNDA2MjUgMi44MDg1OTQgTCAyODMuMTc1NzgxIDIuODEyNSBMIDI4NC40NDE0MDYgOC4xOTkyMTkgTCAyODAuOTc2NTYzIDcuOTA2MjUgWiBNIDI4MC43NDIxODggMTMuNTQyOTY5IEwgMjgwLjc4OTA2MyAxMi45ODgyODEgTCAyODAuNTg1OTM4IDEyLjk2ODc1IEMgMjc5Ljk3MjY1NiAxMi45MTc5NjkgMjc5LjIwMzEyNSAxMi43NjE3MTkgMjc5LjI1IDEyLjIwMzEyNSBDIDI3OS4yNzczNDQgMTEuODcxMDk0IDI3OS41NDI5NjkgMTEuNDA2MjUgMjc5Ljc4MTI1IDEwLjc5Mjk2OSBMIDI4MC41MzUxNTYgOC45MTQwNjMgTCAyODQuNzQyMTg4IDkuMjY5NTMxIEwgMjg1LjI4NTE1NiAxMS40ODA0NjkgQyAyODUuNDM3NSAxMi4wODk4NDQgMjg1LjU2MjUgMTIuNjA1NDY5IDI4NS41NDI5NjkgMTIuODQ3NjU2IEMgMjg1LjUwMzkwNiAxMy4zMDg1OTQgMjg0Ljc3MzQzOCAxMy4zMjQyMTkgMjg0LjM0NzY1NiAxMy4yODUxNTYgTCAyODQuMTQ0NTMxIDEzLjI2OTUzMSBMIDI4NC4wOTc2NTYgMTMuODI0MjE5IEMgMjg1LjA0Njg3NSAxMy44NjcxODggMjg1Ljk3NjU2MyAxMy45MTAxNTYgMjg2Ljg4MjgxMyAxMy45ODQzNzUgQyAyODcuNzczNDM4IDE0LjA2MjUgMjg4LjYwMTU2MyAxNC4xNjc5NjkgMjg5LjQzMzU5NCAxNC4yNzM0MzggTCAyODkuNDgwNDY5IDEzLjcxODc1IEwgMjg5LjM3MTA5NCAxMy43MTA5MzggQyAyODguNzU3ODEzIDEzLjY2MDE1NiAyODguMzg2NzE5IDEzLjQwMjM0NCAyODguMjEwOTM4IDEyLjg2NzE4OCBDIDI4OC4wMTU2MjUgMTIuMjg5MDYzIDI4Ny44NTE1NjMgMTEuNTg1OTM4IDI4Ny42ODM1OTQgMTAuOTE3OTY5IEwgMjg1LjA4OTg0NCAwLjkzNzUgQyAyODUuMDQ2ODc1IDAuNzg1MTU2IDI4NS4wMDM5MDYgMC42MTMyODEgMjg0Ljk2MDkzOCAwLjQ2MDkzOCBDIDI4NC45Mjk2ODggMC40MDIzNDQgMjg0Ljg5MDYyNSAwLjM5ODQzOCAyODQuODM1OTM4IDAuMzk0NTMxIEMgMjg0Ljc4MTI1IDAuMzkwNjI1IDI4NC43NDIxODggMC40MDYyNSAyODQuNjgzNTk0IDAuNDIxODc1IEMgMjg0LjMxMjUgMC42MTMyODEgMjgzLjU0Mjk2OSAwLjkyMTg3NSAyODIuOTMzNTk0IDEuMDc0MjE5IEMgMjgyLjc2MTcxOSAxLjc1IDI4Mi4zNTE1NjMgMi42NDg0MzggMjgyLjA1NDY4OCAzLjMxNjQwNiBMIDI3OC4zNzEwOTQgMTEuNTcwMzEzIEMgMjc4LjAyNzM0NCAxMi4zMjQyMTkgMjc3LjM3ODkwNiAxMi42OTkyMTkgMjc2LjY1NjI1IDEyLjY0MDYyNSBMIDI3Ni41NDY4NzUgMTIuNjI4OTA2IEwgMjc2LjUgMTMuMTg3NSBDIDI3Ny4xNzE4NzUgMTMuMjAzMTI1IDI3Ny44Mzk4NDQgMTMuMjIyNjU2IDI3OC41MDc4MTMgMTMuMjgxMjUgQyAyNzkuMjQ2MDk0IDEzLjM0Mzc1IDI4MC4wMDM5MDYgMTMuNDQ1MzEzIDI4MC43NDIxODggMTMuNTQyOTY5ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEzLjY5OTM0MSUsMTIuMTk5NDAyJSwxMi41JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDMwMS4yODUxNTYgMTMuODc1IEwgMzAzLjA5NzY1NiAzLjk2MDkzOCBDIDMwMy41MDc4MTMgMy45OTYwOTQgMzAzLjkzNzUgNC4wMTk1MzEgMzA0LjM1OTM3NSA0LjA5Mzc1IEMgMzA3LjI4NTE1NiA0LjYyODkwNiAzMDkuNTE5NTMxIDYuMjg1MTU2IDMwOC42MzY3MTkgMTEuMTEzMjgxIEMgMzA4LjEyMTA5NCAxMy45MzM1OTQgMzA2LjAzNTE1NiAxNi4yMzgyODEgMzAyLjkyNTc4MSAxNS42Njc5NjkgQyAzMDEuNjA5Mzc1IDE1LjQyOTY4OCAzMDEuMDU0Njg4IDE1LjE1NjI1IDMwMS4yODUxNTYgMTMuODc1IFogTSAzMDMuMzAwNzgxIDE2LjQxNzk2OSBDIDMwNi45NzI2NTYgMTcuMzE2NDA2IDMxMC41OTM3NSAxNC44OTQ1MzEgMzExLjI2MTcxOSAxMS4yMzQzNzUgQyAzMTEuOTYwOTM4IDcuNDEwMTU2IDMwOS42NTYyNSA0LjM4MjgxMyAzMDUuMTU2MjUgMy41NTg1OTQgQyAzMDQuMzcxMDk0IDMuNDE0MDYzIDMwMy4zNjcxODggMy4zMDg1OTQgMzAyLjE5OTIxOSAzLjA5Mzc1IEMgMzAxLjAyNzM0NCAyLjg4MjgxMyAyOTkuODMyMDMxIDIuNTg1OTM4IDI5OS4yODUxNTYgMi40ODgyODEgTCAyOTkuMTgzNTk0IDMuMDM1MTU2IEwgMjk5LjQzNzUgMy4wODIwMzEgQyAzMDAuMDk3NjU2IDMuMjAzMTI1IDMwMC43NzczNDQgMy40MjE4NzUgMzAwLjYwMTU2MyA0LjM3MTA5NCBMIDI5OC44NTE1NjMgMTMuOTYwOTM4IEMgMjk4LjY3OTY4OCAxNC45MTAxNTYgMjk3Ljk2NDg0NCAxNC44NzUgMjk3LjMwODU5NCAxNC43NTc4MTMgTCAyOTcuMDUwNzgxIDE0LjcxMDkzOCBMIDI5Ni45NDkyMTkgMTUuMjU3ODEzIEMgMjk3LjQyNTc4MSAxNS4zNDM3NSAyOTguNzM4MjgxIDE1LjUwNzgxMyAyOTkuOTg0Mzc1IDE1LjczODI4MSBDIDMwMS4yMjY1NjMgMTUuOTY0ODQ0IDMwMi41IDE2LjIzNDM3NSAzMDMuMzAwNzgxIDE2LjQxNzk2OSAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMy42OTkzNDElLDEyLjE5OTQwMiUsMTIuNSUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAzMTkuMTEzMjgxIDguNjUyMzQ0IEwgMzE5LjE1MjM0NCA4LjY2MDE1NiBMIDMxOS41MzUxNTYgMTQuMTgzNTk0IEwgMzE2LjE2NDA2MyAxMy4zMzk4NDQgWiBNIDMxMS4wMzUxNTYgMTcuMjg5MDYzIEwgMzEwLjkwMjM0NCAxNy44MzIwMzEgQyAzMTEuNTU4NTk0IDE3Ljk2MDkzOCAzMTIuMjE4NzUgMTguMDg1OTM4IDMxMi44NjcxODggMTguMjQ2MDk0IEMgMzEzLjU4OTg0NCAxOC40MjU3ODEgMzE0LjMyMDMxMyAxOC42NDg0MzggMzE1LjAzMTI1IDE4Ljg2MzI4MSBMIDMxNS4xNjc5NjkgMTguMzI0MjE5IEwgMzE0Ljk2ODc1IDE4LjI3MzQzOCBDIDMxNC4zNzEwOTQgMTguMTI1IDMxMy42MzY3MTkgMTcuODQzNzUgMzEzLjc3MzQzOCAxNy4zMDQ2ODggQyAzMTMuODU1NDY5IDE2Ljk4MDQ2OSAzMTQuMTg3NSAxNi41NjI1IDMxNC41MjM0MzggMTUuOTk2MDk0IEwgMzE1LjU2NjQwNiAxNC4yNjU2MjUgTCAzMTkuNjY0MDYzIDE1LjI4NTE1NiBMIDMxOS44NDM3NSAxNy41NTQ2ODggQyAzMTkuODk4NDM4IDE4LjE4MzU5NCAzMTkuOTM3NSAxOC43MTA5MzggMzE5Ljg3ODkwNiAxOC45NDUzMTMgQyAzMTkuNzY5NTMxIDE5LjM5NDUzMSAzMTkuMDQ2ODc1IDE5LjI5Mjk2OSAzMTguNjMyODEzIDE5LjE4NzUgTCAzMTguNDMzNTk0IDE5LjEzNjcxOSBMIDMxOC4yOTY4NzUgMTkuNjc5Njg4IEMgMzE5LjIyNjU2MyAxOS44NzEwOTQgMzIwLjEzNjcxOSAyMC4wNjI1IDMyMS4wMjM0MzggMjAuMjgxMjUgQyAzMjEuODg2NzE5IDIwLjUgMzIyLjY5MTQwNiAyMC43MzgyODEgMzIzLjQ5MjE4OCAyMC45NzY1NjMgTCAzMjMuNjI4OTA2IDIwLjQzNzUgTCAzMjMuNTE5NTMxIDIwLjQxMDE1NiBDIDMyMi45MjU3ODEgMjAuMjYxNzE5IDMyMi42MDE1NjMgMTkuOTQ5MjE5IDMyMi41MTE3MTkgMTkuMzkwNjI1IEMgMzIyLjQxMDE1NiAxOC43ODkwNjMgMzIyLjM1OTM3NSAxOC4wNjY0MDYgMzIyLjMwMDc4MSAxNy4zODI4MTMgTCAzMjEuMzM5ODQ0IDcuMTE3MTg4IEMgMzIxLjMyMDMxMyA2Ljk2MDkzOCAzMjEuMzA0Njg4IDYuNzg1MTU2IDMyMS4yODkwNjMgNi42Mjg5MDYgQyAzMjEuMjY1NjI1IDYuNTYyNSAzMjEuMjMwNDY5IDYuNTU0Njg4IDMyMS4xNzU3ODEgNi41MzkwNjMgQyAzMjEuMTIxMDk0IDYuNTI3MzQ0IDMyMS4wODIwMzEgNi41MzUxNTYgMzIxLjAyMzQzOCA2LjUzOTA2MyBDIDMyMC42MjUgNi42NzE4NzUgMzE5LjgxMjUgNi44NTE1NjMgMzE5LjE4NzUgNi45MDYyNSBDIDMxOC45MTAxNTYgNy41NDY4NzUgMzE4LjM2MzI4MSA4LjM2NzE4OCAzMTcuOTYwOTM4IDguOTc2NTYzIEwgMzEzLjAwNzgxMyAxNi41MzUxNTYgQyAzMTIuNTQ2ODc1IDE3LjIyNjU2MyAzMTEuODQ3NjU2IDE3LjQ5MjE4OCAzMTEuMTQ0NTMxIDE3LjMxNjQwNiBMIDMxMS4wMzUxNTYgMTcuMjg5MDYzICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEzLjY5OTM0MSUsMTIuMTk5NDAyJSwxMi41JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDMyOS40NjQ4NDQgMjIuODM5ODQ0IEwgMzI5LjY0MDYyNSAyMi4zMDg1OTQgTCAzMjkuMzM5ODQ0IDIyLjIxMDkzOCBDIDMyNy45NzY1NjMgMjEuNzY1NjI1IDMyNy44NTE1NjMgMjEuMTM2NzE5IDMyOC4zNTE1NjMgMTkuNjAxNTYzIEwgMzMwLjczMDQ2OSAxMi4zMTY0MDYgTCAzMzYuNTE5NTMxIDI1LjQzNzUgTCAzMzcuMTkxNDA2IDI1LjY1NjI1IEMgMzM3LjI4NTE1NiAyNS4wNzgxMjUgMzM3LjQ2ODc1IDI0LjQ1NzAzMSAzMzcuNjcxODc1IDIzLjgzNTkzOCBMIDM0MC4yOTY4NzUgMTUuNzkyOTY5IEMgMzQwLjk4NDM3NSAxMy42ODc1IDM0MS44NjMyODEgMTMuODIwMzEzIDM0Mi42MDU0NjkgMTQuMDYyNSBMIDM0Mi44NzEwOTQgMTQuMTQ4NDM4IEwgMzQzLjA0Mjk2OSAxMy42MTcxODggQyAzNDIuMzE2NDA2IDEzLjM4MjgxMyAzNDEuNTcwMzEzIDEzLjIxNDg0NCAzNDAuODQzNzUgMTIuOTgwNDY5IEMgMzQwLjAxNTYyNSAxMi43MDcwMzEgMzM5LjIyMjY1NiAxMi4zNzEwOTQgMzM4LjM5NDUzMSAxMi4xMDE1NjMgTCAzMzguMjE4NzUgMTIuNjI4OTA2IEwgMzM4LjYwOTM3NSAxMi43NTc4MTMgQyAzMzkuMTQwNjI1IDEyLjkyOTY4OCAzNDAuMDc4MTI1IDEzLjQ3MjY1NiAzMzkuNjA1NDY5IDE0LjkyMTg3NSBMIDMzNy40Mzc1IDIxLjU1MDc4MSBMIDMzNy4zOTA2MjUgMjEuNTc0MjE5IEwgMzMyLjQxNzk2OSAxMC4xNDg0MzggQyAzMzEuODg2NzE5IDkuOTc2NTYzIDMzMS4zNTE1NjMgOS44Nzg5MDYgMzMwLjgyMDMxMyA5LjcwMzEyNSBDIDMzMC4xNDg0MzggOS40ODQzNzUgMzI5LjQ4NDM3NSA5LjE4NzUgMzI4LjgxMjUgOC45Njg3NSBMIDMyOC42MzY3MTkgOS41IEwgMzI4Ljg2NzE4OCA5LjU3NDIxOSBDIDMyOS42NjQwNjMgOS44MzU5MzggMzMwLjI4MTI1IDEwLjY5OTIxOSAzMjkuOTU3MDMxIDExLjY5MTQwNiBMIDMyNy41MjM0MzggMTkuMTMyODEzIEMgMzI3LjA2MjUgMjAuNTUwNzgxIDMyNi40MjE4NzUgMjEuMjU3ODEzIDMyNS4xOTkyMTkgMjAuODU5Mzc1IEwgMzI0Ljk1MzEyNSAyMC43NzczNDQgTCAzMjQuNzgxMjUgMjEuMzA4NTk0IEMgMzI1LjU3NDIxOSAyMS41NzAzMTMgMzI2LjQxMDE1NiAyMS43NjU2MjUgMzI3LjIwNzAzMSAyMi4wMjM0MzggQyAzMjcuOTY4NzUgMjIuMjczNDM4IDMyOC43MDMxMjUgMjIuNTg5ODQ0IDMyOS40NjQ4NDQgMjIuODM5ODQ0ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEzLjY5OTM0MSUsMTIuMTk5NDAyJSwxMi41JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDM1NC4xNzE4NzUgMzIuMjgxMjUgTCAzNTQuMzk4NDM4IDMxLjc2OTUzMSBMIDM1NC4wNzQyMTkgMzEuNjI4OTA2IEMgMzUzLjI1MzkwNiAzMS4yNjk1MzEgMzUyLjcyNjU2MyAzMC44NTU0NjkgMzUzLjMwMDc4MSAyOS41NDI5NjkgTCAzNTcuMjYxNzE5IDIwLjQ3NjU2MyBMIDM2MC4wNTg1OTQgMjEuNjk5MjE5IEMgMzYxLjE5OTIxOSAyMi4xOTkyMTkgMzYwLjg0Mzc1IDIzLjI0MjE4OCAzNjAuNjAxNTYzIDIzLjg4NjcxOSBMIDM2MS4xOTUzMTMgMjMuOTIxODc1IEMgMzYxLjM5ODQzOCAyMy40NjA5MzggMzYxLjU5NzY1NiAyMy4wMDM5MDYgMzYxLjgzMjAzMSAyMi41NTg1OTQgQyAzNjIuMDg1OTM4IDIyLjExNzE4OCAzNjIuMzU1NDY5IDIxLjY4NzUgMzYyLjYyNSAyMS4yNTc4MTMgTCAzNjIuMjQ2MDk0IDIxLjAxMTcxOSBDIDM2MS45ODgyODEgMjEuNTA3ODEzIDM2MS41NTQ2ODggMjEuMzM5ODQ0IDM2MS4wOTM3NSAyMS4xMzY3MTkgTCAzNTIuMzAwNzgxIDE3LjI5Mjk2OSBDIDM1MS44Mzk4NDQgMTcuMDkzNzUgMzUxLjQwNjI1IDE2LjkyNTc4MSAzNTEuNDkyMTg4IDE2LjM1MTU2MyBMIDM1MS4wODU5MzggMTYuMTc1NzgxIEMgMzUwLjg2NzE4OCAxNi42Njc5NjkgMzUwLjYyODkwNiAxNy4xMjg5MDYgMzUwLjM1MTU2MyAxNy41NzgxMjUgQyAzNTAuMDgyMDMxIDE4LjA1MDc4MSAzNDkuNzg5MDYzIDE4LjQ4ODI4MSAzNDkuNTExNzE5IDE4LjkzNzUgTCAzNTAuMDIzNDM4IDE5LjE2MDE1NiBDIDM1MC44MjQyMTkgMTguMDI3MzQ0IDM1MS4wMDc4MTMgMTcuNzQyMTg4IDM1Mi4yODUxNTYgMTguMzA0Njg4IEwgMzU1LjA4MjAzMSAxOS41MjM0MzggTCAzNTEuMTAxNTYzIDI4LjYyNSBDIDM1MC41MTU2MjUgMjkuOTY4NzUgMzUwIDI5Ljg0NzY1NiAzNDkuMDYyNSAyOS40Mzc1IEwgMzQ4LjczODI4MSAyOS4yOTY4NzUgTCAzNDguNTE1NjI1IDI5LjgwODU5NCBDIDM0OS4xNzk2ODggMzAuMDk3NjU2IDM1MC40MDIzNDQgMzAuNTUwNzgxIDM1MS40MjU3ODEgMzAuOTk2MDk0IEMgMzUyLjM0Mzc1IDMxLjM5ODQzOCAzNTMuNTA3ODEzIDMxLjk4ODI4MSAzNTQuMTcxODc1IDMyLjI4MTI1ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEzLjY5OTM0MSUsMTIuMTk5NDAyJSwxMi41JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDM2Ny4yNzM0MzggMjYuNTA3ODEzIEwgMzY3LjMwODU5NCAyNi41MjM0MzggTCAzNjYuNDM3NSAzMS45ODgyODEgTCAzNjMuMzM5ODQ0IDMwLjQwNjI1IFogTSAzNTcuNTU0Njg4IDMzLjE1NjI1IEwgMzU3LjQ1MzEyNSAzMy4xMDU0NjkgTCAzNTcuMTk5MjE5IDMzLjYwMTU2MyBDIDM1Ny44MTI1IDMzLjg3MTA5NCAzNTguNDI1NzgxIDM0LjE0NDUzMSAzNTkuMDIzNDM4IDM0LjQ0OTIxOSBDIDM1OS42ODM1OTQgMzQuNzg1MTU2IDM2MC4zNDc2NTYgMzUuMTY0MDYzIDM2MC45OTIxODggMzUuNTM1MTU2IEwgMzYxLjI0NjA5NCAzNS4wMzkwNjMgTCAzNjEuMDY2NDA2IDM0Ljk0NTMxMyBDIDM2MC41MTk1MzEgMzQuNjY3OTY5IDM1OS44NjMyODEgMzQuMjMwNDY5IDM2MC4xMTcxODggMzMuNzM0Mzc1IEMgMzYwLjI2OTUzMSAzMy40MzM1OTQgMzYwLjY4NzUgMzMuMTA1NDY5IDM2MS4xNDA2MjUgMzIuNjI4OTA2IEwgMzYyLjU1MDc4MSAzMS4xNzU3ODEgTCAzNjYuMzEyNSAzMy4wOTM3NSBMIDM2NS45NzY1NjMgMzUuMzQ3NjU2IEMgMzY1Ljg5MDYyNSAzNS45Njg3NSAzNjUuODA4NTk0IDM2LjQ5MjE4OCAzNjUuNjk5MjE5IDM2LjcwNzAzMSBDIDM2NS40ODgyODEgMzcuMTIxMDk0IDM2NC44MDg1OTQgMzYuODU5Mzc1IDM2NC40MjU3ODEgMzYuNjY0MDYzIEwgMzY0LjI0NjA5NCAzNi41NzAzMTMgTCAzNjMuOTkyMTg4IDM3LjA2NjQwNiBDIDM2NC44NTE1NjMgMzcuNDY0ODQ0IDM2NS42OTkyMTkgMzcuODU1NDY5IDM2Ni41MTE3MTkgMzguMjY5NTMxIEMgMzY3LjMwNDY4OCAzOC42NzU3ODEgMzY4LjAzNTE1NiAzOS4wODk4NDQgMzY4Ljc2MTcxOSAzOS41MDM5MDYgTCAzNjkuMDE1NjI1IDM5LjAwNzgxMyBMIDM2OC45MTc5NjkgMzguOTU3MDMxIEMgMzY4LjM3MTA5NCAzOC42NzU3ODEgMzY4LjEyNSAzOC4zMDA3ODEgMzY4LjE2MDE1NiAzNy43MzQzNzUgQyAzNjguMTk5MjE5IDM3LjEyODkwNiAzNjguMzEyNSAzNi40MTQwNjMgMzY4LjQxMDE1NiAzNS43MzA0NjkgTCAzNjkuNzg1MTU2IDI1LjUxMTcxOSBDIDM2OS44MDQ2ODggMjUuMzU1NDY5IDM2OS44MjgxMjUgMjUuMTc5Njg4IDM2OS44NDc2NTYgMjUuMDIzNDM4IEMgMzY5LjgzOTg0NCAyNC45NTcwMzEgMzY5LjgwODU5NCAyNC45Mzc1IDM2OS43NTc4MTMgMjQuOTE0MDYzIEMgMzY5LjcwNzAzMSAyNC44ODY3MTkgMzY5LjY2Nzk2OSAyNC44ODY3MTkgMzY5LjYwOTM3NSAyNC44Nzg5MDYgQyAzNjkuMTkxNDA2IDI0LjkxNzk2OSAzNjguMzU5Mzc1IDI0LjkxMDE1NiAzNjcuNzM4MjgxIDI0LjgyMDMxMyBDIDM2Ny4zMjQyMTkgMjUuMzgyODEzIDM2Ni42MDU0NjkgMjYuMDU4NTk0IDM2Ni4wNzQyMTkgMjYuNTYyNSBMIDM1OS41NDI5NjkgMzIuODEyNSBDIDM1OC45NDE0MDYgMzMuMzgyODEzIDM1OC4xOTkyMTkgMzMuNDg0Mzc1IDM1Ny41NTQ2ODggMzMuMTU2MjUgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoMTMuNjk5MzQxJSwxMi4xOTk0MDIlLDEyLjUlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMzc3LjAxOTUzMSA0NC4zNTkzNzUgTCAzNzcuMzA0Njg4IDQzLjg3ODkwNiBMIDM3Ni45OTYwOTQgNDMuNjk5MjE5IEMgMzc2LjIyNjU2MyA0My4yNDYwOTQgMzc1Ljc1MzkwNiA0Mi43NzM0MzggMzc2LjQ3NjU2MyA0MS41MzkwNjMgTCAzODEuNDkyMTg4IDMzLjAwNzgxMyBMIDM4NC4xMjEwOTQgMzQuNTU0Njg4IEMgMzg1LjE5OTIxOSAzNS4xODc1IDM4NC43MjI2NTYgMzYuMTc5Njg4IDM4NC40MDYyNSAzNi43OTI5NjkgTCAzODQuOTg4MjgxIDM2Ljg5ODQzOCBDIDM4NS4yNDIxODggMzYuNDY0ODQ0IDM4NS41IDM2LjAzMTI1IDM4NS43ODUxNTYgMzUuNjE3MTg4IEMgMzg2LjA4OTg0NCAzNS4yMTQ4NDQgMzg2LjQwNjI1IDM0LjgyMDMxMyAzODYuNzI2NTYzIDM0LjQyNTc4MSBMIDM4Ni4zNzg5MDYgMzQuMTMyODEzIEMgMzg2LjA2MjUgMzQuNTkzNzUgMzg1LjY1MjM0NCAzNC4zNzUgMzg1LjIxODc1IDM0LjEyMTA5NCBMIDM3Ni45NDUzMTMgMjkuMjU3ODEzIEMgMzc2LjUxNTYyNSAyOSAzNzYuMTA1NDY5IDI4Ljc4MTI1IDM3Ni4yNTc4MTMgMjguMjI2NTYzIEwgMzc1Ljg3MTA5NCAyOCBDIDM3NS42MDE1NjMgMjguNDY0ODQ0IDM3NS4zMDQ2ODggMjguODk0NTMxIDM3NC45NzY1NjMgMjkuMzA0Njg4IEMgMzc0LjY1MjM0NCAyOS43NDIxODggMzc0LjMwODU5NCAzMC4xNDQ1MzEgMzczLjk4MDQ2OSAzMC41NTQ2ODggTCAzNzQuNDY0ODQ0IDMwLjgzOTg0NCBDIDM3NS4zOTA2MjUgMjkuODA4NTk0IDM3NS42MDkzNzUgMjkuNTQ2ODc1IDM3Ni44MTI1IDMwLjI1MzkwNiBMIDM3OS40NDE0MDYgMzEuODAwNzgxIEwgMzc0LjQwNjI1IDQwLjM2MzI4MSBDIDM3My42NjAxNTYgNDEuNjI4OTA2IDM3My4xNjQwNjMgNDEuNDQ1MzEzIDM3Mi4yODUxNTYgNDAuOTI5Njg4IEwgMzcxLjk4MDQ2OSA0MC43NSBMIDM3MS42OTUzMTMgNDEuMjMwNDY5IEMgMzcyLjMyMDMxMyA0MS41OTc2NTYgMzczLjQ4MDQ2OSA0Mi4xOTE0MDYgMzc0LjQ0NTMxMyA0Mi43NTc4MTMgQyAzNzUuMzA4NTk0IDQzLjI2OTUzMSAzNzYuMzk0NTMxIDQzLjk5MjE4OCAzNzcuMDE5NTMxIDQ0LjM1OTM3NSAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMy42OTkzNDElLDEyLjE5OTQwMiUsMTIuNSUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAzOTAuNzAzMTI1IDQwLjE3OTY4OCBMIDM5MC43MzQzNzUgNDAuMTk5MjE5IEwgMzg5LjIyMjY1NiA0NS41MjczNDQgTCAzODYuMzM1OTM4IDQzLjU4OTg0NCBaIE0gMzgwLjI2MTcxOSA0NS42Mjg5MDYgTCAzODAuMTY3OTY5IDQ1LjU2NjQwNiBMIDM3OS44NTkzNzUgNDYuMDI3MzQ0IEMgMzgwLjQzMzU5NCA0Ni4zNzEwOTQgMzgxLjAxMTcxOSA0Ni43MTQ4NDQgMzgxLjU2NjQwNiA0Ny4wODU5MzggQyAzODIuMTgzNTk0IDQ3LjUgMzgyLjc5Njg3NSA0Ny45NTcwMzEgMzgzLjM5NDUzMSA0OC40MDIzNDQgTCAzODMuNzA3MDMxIDQ3LjkzNzUgTCAzODMuNTM1MTU2IDQ3LjgyNDIxOSBDIDM4My4wMjczNDQgNDcuNDg0Mzc1IDM4Mi40Mjk2ODggNDYuOTY4NzUgMzgyLjczODI4MSA0Ni41MDc4MTMgQyAzODIuOTI1NzgxIDQ2LjIzMDQ2OSAzODMuMzgyODEzIDQ1Ljk0OTIxOSAzODMuODkwNjI1IDQ1LjUzMTI1IEwgMzg1LjQ2MDkzOCA0NC4yNTM5MDYgTCAzODguOTY4NzUgNDYuNjA5Mzc1IEwgMzg4LjM2NzE4OCA0OC44MDQ2ODggQyAzODguMjAzMTI1IDQ5LjQxMDE1NiAzODguMDYyNSA0OS45MjE4NzUgMzg3LjkyOTY4OCA1MC4xMjUgQyAzODcuNjcxODc1IDUwLjUxMTcxOSAzODcuMDI3MzQ0IDUwLjE2Nzk2OSAzODYuNjcxODc1IDQ5LjkyOTY4OCBMIDM4Ni41IDQ5LjgxNjQwNiBMIDM4Ni4xOTE0MDYgNTAuMjc3MzQ0IEMgMzg3IDUwLjc3NzM0NCAzODcuNzkyOTY5IDUxLjI2MTcxOSAzODguNTQ2ODc1IDUxLjc2OTUzMSBDIDM4OS4yODkwNjMgNTIuMjY5NTMxIDM4OS45NjQ4NDQgNTIuNzY1NjI1IDM5MC42MzY3MTkgNTMuMjYxNzE5IEwgMzkwLjk0OTIxOSA1Mi44MDA3ODEgTCAzOTAuODU1NDY5IDUyLjczODI4MSBDIDM5MC4zNDc2NTYgNTIuMzk0NTMxIDM5MC4xNDg0MzggNTEuOTkyMTg4IDM5MC4yNTM5MDYgNTEuNDM3NSBDIDM5MC4zNjMyODEgNTAuODM5ODQ0IDM5MC41NTg1OTQgNTAuMTQwNjI1IDM5MC43MzgyODEgNDkuNDc2NTYzIEwgMzkzLjMxNjQwNiAzOS40OTIxODggQyAzOTMuMzU1NDY5IDM5LjMzOTg0NCAzOTMuMzk4NDM4IDM5LjE2Nzk2OSAzOTMuNDM3NSAzOS4wMTE3MTkgQyAzOTMuNDM3NSAzOC45NDUzMTMgMzkzLjQwNjI1IDM4LjkyNTc4MSAzOTMuMzU5Mzc1IDM4Ljg5NDUzMSBDIDM5My4zMTI1IDM4Ljg2MzI4MSAzOTMuMjczNDM4IDM4Ljg1OTM3NSAzOTMuMjE0ODQ0IDM4Ljg0Mzc1IEMgMzkyLjc5Njg3NSAzOC44MjgxMjUgMzkxLjk3MjY1NiAzOC43MjY1NjMgMzkxLjM2MzI4MSAzOC41NjI1IEMgMzkwLjg4NjcxOSAzOS4wNzAzMTMgMzkwLjA5Mzc1IDM5LjY1NjI1IDM4OS41MDc4MTMgNDAuMDkzNzUgTCAzODIuMjc3MzQ0IDQ1LjUyMzQzOCBDIDM4MS42MTMyODEgNDYuMDE5NTMxIDM4MC44NjMyODEgNDYuMDMxMjUgMzgwLjI2MTcxOSA0NS42Mjg5MDYgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoMTMuNjk5MzQxJSwxMi4xOTk0MDIlLDEyLjUlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gNDEyLjY2Nzk2OSA1NS4wNDI5NjkgQyA0MTIuODc1IDU1LjE5OTIxOSA0MTMuMDkzNzUgNTUuMzEyNSA0MTMuNTE1NjI1IDU1LjY3OTY4OCBDIDQxNC43Njk1MzEgNTYuNzYxNzE5IDQxNC44Nzg5MDYgNTguMjU3ODEzIDQxMy43OTY4NzUgNTkuNTA3ODEzIEMgNDEyLjM1OTM3NSA2MS4xNjc5NjkgNDExLjEzNjcxOSA2MS4wNDY4NzUgNDA5LjczMDQ2OSA1OS44MjgxMjUgTCA0MDkuMDM5MDYzIDU5LjIzNDM3NSBaIE0gNDA2LjA2NjQwNiA2NS41MTU2MjUgTCA0MDYuNDMzNTk0IDY1LjA5Mzc1IEwgNDA2LjE3OTY4OCA2NC44NzUgQyA0MDUuNTMxMjUgNjQuMzE2NDA2IDQwNS4wNjI1IDYzLjgzNTkzOCA0MDYgNjIuNzUgTCA0MDguNjAxNTYzIDU5Ljc0MjE4OCBMIDQwOS41MzEyNSA2MC41NDI5NjkgQyA0MDkuMDQ2ODc1IDYyLjk1MzEyNSA0MDguNjYwMTU2IDY1LjI3MzQzOCA0MDguNTE1NjI1IDY3LjYzMjgxMyBDIDQwOC45NTMxMjUgNjguMDExNzE5IDQwOS40NDkyMTkgNjguMzQzNzUgNDA5Ljg4NjcxOSA2OC43MTg3NSBDIDQxMC4zNTE1NjMgNjkuMTIxMDk0IDQxMC43NTM5MDYgNjkuNTY2NDA2IDQxMS4yMTQ4NDQgNjkuOTY4NzUgTCA0MTEuNTgyMDMxIDY5LjU0Njg3NSBDIDQxMC45NjQ4NDQgNjguODY3MTg4IDQxMC44MjgxMjUgNjguNDUzMTI1IDQxMC45NDUzMTMgNjcuNTIzNDM4IEwgNDExLjY1NjI1IDYxLjgzOTg0NCBDIDQxMy4xNDQ1MzEgNjIuMzYzMjgxIDQxNC42NTYyNSA2Mi4zMjAzMTMgNDE1Ljc1MzkwNiA2MS4wNTQ2ODggQyA0MTcuNDgwNDY5IDU5LjA1ODU5NCA0MTYuMzIwMzEzIDU3LjIxODc1IDQxNC41NDY4NzUgNTUuNjgzNTk0IEMgNDEzLjgwMDc4MSA1NS4wMzkwNjMgNDEzLjA3NDIxOSA1NC41MTE3MTkgNDEyLjIzMDQ2OSA1My43ODEyNSBDIDQxMS4zNzUgNTMuMDM5MDYzIDQxMC41NTA3ODEgNTIuMjI2NTYzIDQxMC4xMDE1NjMgNTEuODM5ODQ0IEwgNDA5LjczNDM3NSA1Mi4yNjE3MTkgTCA0MDkuOTg4MjgxIDUyLjQ4MDQ2OSBDIDQxMC40MjU3ODEgNTIuODU1NDY5IDQxMC45NDkyMTkgNTMuMzg2NzE5IDQxMC4wNjI1IDU0LjQxNDA2MyBMIDQwMy44ODI4MTMgNjEuNTU4NTk0IEMgNDAzLjQzMzU5NCA2Mi4wNzgxMjUgNDAyLjc0NjA5NCA2MS45MDYyNSA0MDIuMjI2NTYzIDYxLjQ1MzEyNSBMIDQwMS45NzI2NTYgNjEuMjM4MjgxIEwgNDAxLjYwOTM3NSA2MS42NjAxNTYgQyA0MDIuMzEyNSA2Mi4yNjU2MjUgNDAzLjAxOTUzMSA2Mi43ODEyNSA0MDMuNjk1MzEzIDYzLjM2NzE4OCBDIDQwNC40OTYwOTQgNjQuMDU4NTk0IDQwNS4yNjU2MjUgNjQuODIwMzEzIDQwNi4wNjY0MDYgNjUuNTE1NjI1ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEzLjY5OTM0MSUsMTIuMTk5NDAyJSwxMi41JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDQyMC43NjE3MTkgNjMuNzc3MzQ0IEwgNDE2LjA1MDc4MSA2OC41NjI1IEMgNDEzLjcxNDg0NCA3MC45MzM1OTQgNDE0LjIxODc1IDczLjI2MTcxOSA0MTYuNzYxNzE5IDc1Ljc2NTYyNSBDIDQxOC43MzQzNzUgNzcuNzEwOTM4IDQyMS4xNzU3ODEgNzguNDE0MDYzIDQyNC4xMjUgNzUuNDIxODc1IEwgNDI4LjI4OTA2MyA3MS4xOTE0MDYgQyA0MjkuMjMwNDY5IDcwLjIzODI4MSA0MjkuNzM0Mzc1IDcwLjcxMDkzOCA0MzAuMDg5ODQ0IDcxLjA2MjUgTCA0MzAuMzY3MTg4IDcxLjMzNTkzOCBMIDQzMC43NjE3MTkgNzAuOTM3NSBDIDQzMC4yNDIxODggNzAuNDI1NzgxIDQyOS42ODc1IDY5Ljk4NDM3NSA0MjkuMTcxODc1IDY5LjQ3NjU2MyBDIDQyOC42NDA2MjUgNjguOTUzMTI1IDQyOC4xNDg0MzggNjguMzYzMjgxIDQyNy42MTcxODggNjcuODQzNzUgTCA0MjcuMjI2NTYzIDY4LjI0MjE4OCBMIDQyNy40OTIxODggNjguNTAzOTA2IEMgNDI3Ljk0MTQwNiA2OC45NDUzMTMgNDI4LjQzMzU5NCA2OS40NTcwMzEgNDI3LjQ5MjE4OCA3MC40MTAxNTYgTCA0MjMuMDQyOTY5IDc0LjkyOTY4OCBDIDQyMS4yODEyNSA3Ni43MTg3NSA0MTkuNDE0MDYzIDc3LjA3NDIxOSA0MTcuNjY0MDYzIDc1LjM1MTU2MyBDIDQxNS43Njk1MzEgNzMuNDg0Mzc1IDQxNi4yOTY4NzUgNzEuNzAzMTI1IDQxNy45NTMxMjUgNzAuMDIzNDM4IEwgNDIyLjQ1NzAzMSA2NS40NDkyMTkgQyA0MjMuMzk4NDM4IDY0LjQ5NjA5NCA0MjMuOTQxNDA2IDY1LjAwMzkwNiA0MjQuNDcyNjU2IDY1LjUyNzM0NCBMIDQyNC42Mjg5MDYgNjUuNjgzNTk0IEwgNDI1LjAyMzQzOCA2NS4yODUxNTYgQyA0MjQuNDkyMTg4IDY0Ljc2MTcxOSA0MjMuNzc3MzQ0IDY0LjE2MDE1NiA0MjIuOTgwNDY5IDYzLjM3ODkwNiBDIDQyMi4xNDg0MzggNjIuNTU4NTk0IDQyMS40OTYwOTQgNjEuODEyNSA0MjAuOTI1NzgxIDYxLjI1IEwgNDIwLjUzNTE1NiA2MS42NDg0MzggTCA0MjAuNjk1MzEzIDYxLjgwODU5NCBDIDQyMS4yMjI2NTYgNjIuMzI4MTI1IDQyMS43MDMxMjUgNjIuODI0MjE5IDQyMC43NjE3MTkgNjMuNzc3MzQ0ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEzLjY5OTM0MSUsMTIuMTk5NDAyJSwxMi41JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDQzMy42MjUgNzcuMjM0Mzc1IEwgNDMzLjY0ODQzOCA3Ny4yNjE3MTkgTCA0MzAuODc1IDgyLjA1MDc4MSBMIDQyOC41NTQ2ODggNzkuNDYwOTM4IFogTSA0MjIuMTY0MDYzIDc5Ljk0NTMxMyBMIDQyMi4wODk4NDQgNzkuODYzMjgxIEwgNDIxLjY3NTc4MSA4MC4yMzQzNzUgQyA0MjIuMTUyMzQ0IDgwLjcxMDkzOCA0MjIuNjI1IDgxLjE4MzU5NCA0MjMuMDc0MjE5IDgxLjY3OTY4OCBDIDQyMy41NzAzMTMgODIuMjM0Mzc1IDQyNC4wNTA3ODEgODIuODI0MjE5IDQyNC41MTk1MzEgODMuNDA2MjUgTCA0MjQuOTM3NSA4My4wMzEyNSBMIDQyNC44MDA3ODEgODIuODc4OTA2IEMgNDI0LjM5MDYyNSA4Mi40MjU3ODEgNDIzLjkzNzUgODEuNzgxMjUgNDI0LjM1MTU2MyA4MS40MDYyNSBDIDQyNC42MDE1NjMgODEuMTgzNTk0IDQyNS4xMDkzNzUgODEuMDI3MzQ0IDQyNS43MDMxMjUgODAuNzQyMTg4IEwgNDI3LjU0Mjk2OSA3OS44OTQ1MzEgTCA0MzAuMzYzMjgxIDgzLjAzNTE1NiBMIDQyOS4yNDIxODggODUuMDE1NjI1IEMgNDI4LjkzMzU5NCA4NS41NjY0MDYgNDI4LjY3MTg3NSA4Ni4wMjczNDQgNDI4LjQ5MjE4OCA4Ni4xODc1IEMgNDI4LjE0NDUzMSA4Ni41IDQyNy42MDU0NjkgODYuMDA3ODEzIDQyNy4zMjAzMTMgODUuNjkxNDA2IEwgNDI3LjE4MzU5NCA4NS41MzkwNjMgTCA0MjYuNzY5NTMxIDg1LjkxMDE1NiBDIDQyNy40Mjk2ODggODYuNTg5ODQ0IDQyOC4wNzgxMjUgODcuMjU3ODEzIDQyOC42ODc1IDg3LjkzMzU5NCBDIDQyOS4yODUxNTYgODguNTk3NjU2IDQyOS44MTY0MDYgODkuMjQ2MDk0IDQzMC4zNDc2NTYgODkuODk0NTMxIEwgNDMwLjc2MTcxOSA4OS41MjM0MzggTCA0MzAuNjg3NSA4OS40NDE0MDYgQyA0MzAuMjc3MzQ0IDg4Ljk4NDM3NSA0MzAuMTgzNTk0IDg4LjU0Njg3NSA0MzAuNDIxODc1IDg4LjAzMTI1IEMgNDMwLjY3NTc4MSA4Ny40NzY1NjMgNDMxLjAzOTA2MyA4Ni44NTE1NjMgNDMxLjM3MTA5NCA4Ni4yNSBMIDQzNi4zMjQyMTkgNzcuMjA3MDMxIEMgNDM2LjM5ODQzOCA3Ny4wNjY0MDYgNDM2LjQ4ODI4MSA3Ni45MTQwNjMgNDM2LjU2MjUgNzYuNzczNDM4IEMgNDM2LjU3ODEyNSA3Ni43MDcwMzEgNDM2LjU1NDY4OCA3Ni42Nzk2ODggNDM2LjUxNTYyNSA3Ni42NDA2MjUgQyA0MzYuNDc2NTYzIDc2LjU5NzY1NiA0MzYuNDM3NSA3Ni41ODIwMzEgNDM2LjM4NjcxOSA3Ni41NTQ2ODggQyA0MzUuOTg0Mzc1IDc2LjQzNzUgNDM1LjIxNDg0NCA3Ni4xMzI4MTMgNDM0LjY2NDA2MyA3NS44MjgxMjUgQyA0MzQuMDc0MjE5IDc2LjIwMzEyNSA0MzMuMTYwMTU2IDc2LjU3NDIxOSA0MzIuNDg4MjgxIDc2Ljg1NTQ2OSBMIDQyNC4xNDQ1MzEgODAuMzQzNzUgQyA0MjMuMzc4OTA2IDgwLjY1NjI1IDQyMi42NDg0MzggODAuNDg0Mzc1IDQyMi4xNjQwNjMgNzkuOTQ1MzEzICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEzLjY5OTM0MSUsMTIuMTk5NDAyJSwxMi41JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDQ0MC44OTg0MzggODUuODIwMzEzIEwgNDM0LjcxODc1IDkwLjYyODkwNiBDIDQzMy41NDY4NzUgOTEuNTQyOTY5IDQzMi42MTcxODggOTEuNzczNDM4IDQzMS44MjgxMjUgOTAuNzYxNzE5IEwgNDMxLjY2Nzk2OSA5MC41NTQ2ODggTCA0MzEuMjI2NTYzIDkwLjg5ODQzOCBDIDQzMS43NDIxODggOTEuNTU4NTk0IDQzMi4zMjQyMTkgOTIuMTg3NSA0MzIuODM5ODQ0IDkyLjg0NzY1NiBDIDQzMy4zMzIwMzEgOTMuNDc2NTYzIDQzMy43NjU2MjUgOTQuMTU2MjUgNDM0LjI1MzkwNiA5NC43ODUxNTYgTCA0MzQuNjk1MzEzIDk0LjQ0NTMxMyBMIDQzNC41IDk0LjE5NTMxMyBDIDQzMy42MjEwOTQgOTMuMDYyNSA0MzMuODY3MTg4IDkyLjQ3MjY1NiA0MzUuMTQ0NTMxIDkxLjQ3NjU2MyBMIDQ0MS4xOTE0MDYgODYuNzczNDM4IEwgNDM4LjY0ODQzOCAxMDAuODg2NzE5IEwgNDM5LjA4MjAzMSAxMDEuNDQ1MzEzIEMgNDM5LjQ4MDQ2OSAxMDEuMDE5NTMxIDQzOS45ODQzNzUgMTAwLjYwNTQ2OSA0NDAuNDk2MDk0IDEwMC4yMDMxMjUgTCA0NDcuMTc1NzgxIDk1LjAwNzgxMyBDIDQ0OC45MjE4NzUgOTMuNjQ4NDM4IDQ0OS41NzgxMjUgOTQuMjQ2MDk0IDQ1MC4wNTg1OTQgOTQuODYzMjgxIEwgNDUwLjIyNjU2MyA5NS4wODU5MzggTCA0NTAuNjY3OTY5IDk0Ljc0MjE4OCBDIDQ1MC4xOTkyMTkgOTQuMTM2NzE5IDQ0OS42NzE4NzUgOTMuNTgyMDMxIDQ0OS4yMDMxMjUgOTIuOTgwNDY5IEMgNDQ4LjY2Nzk2OSA5Mi4yODkwNjMgNDQ4LjE5OTIxOSA5MS41NzAzMTMgNDQ3LjY2NDA2MyA5MC44Nzg5MDYgTCA0NDcuMjIyNjU2IDkxLjIyMjY1NiBMIDQ0Ny40NzY1NjMgOTEuNTQ2ODc1IEMgNDQ3LjgxNjQwNiA5MS45ODQzNzUgNDQ4LjI5Mjk2OSA5Mi45NjA5MzggNDQ3LjA4OTg0NCA5My44OTQ1MzEgTCA0NDEuNTg1OTM4IDk4LjE3OTY4OCBMIDQ0MS41MzEyNSA5OC4xNzE4NzUgTCA0NDMuODA0Njg4IDg1LjkxNzk2OSBDIDQ0My40NjA5MzggODUuNDc2NTYzIDQ0My4wNzAzMTMgODUuMDk3NjU2IDQ0Mi43MjY1NjMgODQuNjU2MjUgQyA0NDIuMjkyOTY5IDg0LjEwMTU2MyA0NDEuOTA2MjUgODMuNDgwNDY5IDQ0MS40NzI2NTYgODIuOTI1NzgxIEwgNDQxLjAzMTI1IDgzLjI2NTYyNSBMIDQ0MS4xNzk2ODggODMuNDU3MDMxIEMgNDQxLjY5NTMxMyA4NC4xMTcxODggNDQxLjcyMjY1NiA4NS4xODM1OTQgNDQwLjg5ODQzOCA4NS44MjAzMTMgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoMTMuNjk5MzQxJSwxMi4xOTk0MDIlLDEyLjUlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gNDQ3LjA1MDc4MSAxMDAuNTMxMjUgQyA0NDMuMzI0MjE5IDEwMy4wMTk1MzEgNDQyLjk5NjA5NCAxMDcuMDE1NjI1IDQ0NS4zMDg1OTQgMTEwLjQ4MDQ2OSBDIDQ0Ni4zNzEwOTQgMTEyLjA3NDIxOSA0NDcuNTQ2ODc1IDExMy4yMzQzNzUgNDQ4Ljg1MTU2MyAxMTQuMzUxNTYzIEwgNDQ5LjEzMjgxMyAxMTQuMTY3OTY5IEwgNDQ5LjA5Mzc1IDExMy42NzU3ODEgTCA0NTEuNDQ1MzEzIDExMi4xMDkzNzUgQyA0NTEuOTg4MjgxIDExMS43NDYwOTQgNDUyLjQyOTY4OCAxMTEuODc1IDQ1Mi43OTI5NjkgMTEyLjQxNzk2OSBMIDQ1Mi45MjU3ODEgMTEyLjYxNzE4OCBMIDQ1My4zOTA2MjUgMTEyLjMwODU5NCBDIDQ1Mi44OTQ1MzEgMTExLjYzMjgxMyA0NTIuNDEwMTU2IDExMC45NzI2NTYgNDUxLjk0NTMxMyAxMTAuMjc3MzQ0IEMgNDUxLjQyOTY4OCAxMDkuNTAzOTA2IDQ1MC45NDE0MDYgMTA4LjcxMDkzOCA0NTAuNDU3MDMxIDEwNy45MTQwNjMgTCA0NDkuOTkyMTg4IDEwOC4yMjY1NjMgTCA0NTAuMTI4OTA2IDEwOC40MjU3ODEgQyA0NTAuNTExNzE5IDEwOSA0NTAuNzU3ODEzIDEwOS43MDMxMjUgNDUwLjEyNSAxMTAuMTI4OTA2IEwgNDQ3LjYwMTU2MyAxMTEuODEyNSBDIDQ0Ny4yODEyNSAxMTEuNzM0Mzc1IDQ0Ni42NDQ1MzEgMTExLjA0Mjk2OSA0NDYuMTY0MDYzIDExMC4yODkwNjMgQyA0NDQuMTkxNDA2IDEwNy4zMzU5MzggNDQ2LjA5NzY1NiAxMDQuMjk2ODc1IDQ0OC42NTIzNDQgMTAyLjU5Mzc1IEMgNDUxLjIzNDM3NSAxMDAuODcxMDk0IDQ1NC4xODM1OTQgMTAwLjg3MTA5NCA0NTYuMDMxMjUgMTAzLjYzNjcxOSBDIDQ1Ny4yMzgyODEgMTA1LjQ0NTMxMyA0NTcuNDQ5MjE5IDEwNy4yMDcwMzEgNDU1Ljg1OTM3NSAxMDguOTM3NSBMIDQ1Ni4xOTkyMTkgMTA5LjM4MjgxMyBDIDQ1Ni45NzI2NTYgMTA4LjU5NzY1NiA0NTguMTQ4NDM4IDEwNy44MTI1IDQ1OC43MTg3NSAxMDcuNDMzNTk0IEMgNDU4LjMyNDIxOSAxMDYuODA0Njg4IDQ1OC4xMDkzNzUgMTA2LjE4MzU5NCA0NTcuODQ3NjU2IDEwNS40ODgyODEgQyA0NTcuNTg1OTM4IDEwNC43OTI5NjkgNDU3LjI3NzM0NCAxMDQuMDM1MTU2IDQ1Ni42NDA2MjUgMTAzLjA3NDIxOSBDIDQ1NC41NTQ2ODggOTkuOTQ5MjE5IDQ1MC42NDA2MjUgOTguMTM2NzE5IDQ0Ny4wNTA3ODEgMTAwLjUzMTI1ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEzLjY5OTM0MSUsMTIuMTk5NDAyJSwxMi41JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDExOC4yMTQ4NDQgNDA2LjUxNTYyNSBDIDExNy4xNDA2MjUgNDA3Ljc3MzQzOCAxMTUuNDE3OTY5IDQwNy45OTIxODggMTE0LjIxNDg0NCA0MDYuOTY4NzUgQyAxMTMuMTI1IDQwNi4wMzkwNjMgMTEzLjEyMTA5NCA0MDUuNjcxODc1IDExMy45NjQ4NDQgNDA0LjY3OTY4OCBMIDExNi43OTY4NzUgNDAxLjM1MTU2MyBMIDExNy43MDMxMjUgNDAyLjEyNSBDIDExOS4xMTcxODggNDAzLjMyODEyNSAxMTkuNTUwNzgxIDQwNC45NDE0MDYgMTE4LjIxNDg0NCA0MDYuNTE1NjI1IFogTSAxMjAuNDg0Mzc1IDM5Ny4wMTk1MzEgTCAxMjEuMzM1OTM4IDM5Ny43NDIxODggQyAxMjIuMjk2ODc1IDM5OC41NjI1IDEyMi45NzI2NTYgMzk5Ljc0NjA5NCAxMjEuNTg1OTM4IDQwMS4zNzUgQyAxMjAuNDUzMTI1IDQwMi43MDcwMzEgMTE5LjEyODkwNiA0MDIuNDU3MDMxIDExNy45MjU3ODEgNDAxLjQzMzU5NCBMIDExNy4yMzA0NjkgNDAwLjg0Mzc1IFogTSAxMjAuMTYwMTU2IDQwOC4wNzQyMTkgQyAxMjEuNjE3MTg4IDQwNi4zNTkzNzUgMTIwLjczODI4MSA0MDQuMTIxMDk0IDExOS4xNjAxNTYgNDAyLjg1MTU2MyBMIDExOS4xODM1OTQgNDAyLjgyMDMxMyBDIDEyMC42MjUgNDAzLjY1NjI1IDEyMi40ODQzNzUgNDA0LjE2NDA2MyAxMjMuNzE0ODQ0IDQwMi43MjI2NTYgQyAxMjQuNzYxNzE5IDQwMS40ODgyODEgMTI0LjcxNDg0NCAzOTkuNzM4MjgxIDEyMi4zMzU5MzggMzk3LjcxNDg0NCBDIDEyMS42ODM1OTQgMzk3LjE2MDE1NiAxMjAuODI4MTI1IDM5Ni41MjczNDQgMTIwLjAxOTUzMSAzOTUuODQzNzUgQyAxMTkuMjMwNDY5IDM5NS4xNjc5NjkgMTE4LjQ4NDM3NSAzOTQuNDMzNTk0IDExNy44NTkzNzUgMzkzLjkwNjI1IEwgMTE3LjUgMzk0LjMzMjAzMSBMIDExNy42OTUzMTMgMzk0LjUgQyAxMTguMjA3MDMxIDM5NC45MzM1OTQgMTE4LjY4MzU5NCAzOTUuNDYwOTM4IDExOC4wNTg1OTQgMzk2LjE5OTIxOSBMIDExMS43NDIxODggNDAzLjYxNzE4OCBDIDExMS4xMTMyODEgNDA0LjM1NTQ2OSAxMTAuNTE1NjI1IDQwMy45Njg3NSAxMTAuMDA3ODEzIDQwMy41MzUxNTYgTCAxMDkuODA4NTk0IDQwMy4zNjMyODEgTCAxMDkuNDQ5MjE5IDQwMy43ODkwNjMgQyAxMTAuMDU4NTk0IDQwNC4zMDg1OTQgMTExLjEyNSA0MDUuMTE3MTg4IDExMi4wMDM5MDYgNDA1Ljg2NzE4OCBDIDExMi44Nzg5MDYgNDA2LjYxMzI4MSAxMTMuNzIyNjU2IDQwNy40Mjk2ODggMTE0LjQzMzU5NCA0MDguMDMxMjUgQyAxMTYuMjczNDM4IDQwOS41OTc2NTYgMTE4Ljg1OTM3NSA0MDkuNjAxNTYzIDEyMC4xNjAxNTYgNDA4LjA3NDIxOSAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMy42OTkzNDElLDEyLjE5OTQwMiUsMTIuNSUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAxMjUuOTQ5MjE5IDQxMC4xMTcxODggTCAxMzAuNTAzOTA2IDQwNi45NjA5MzggTCAxMzAuNTMxMjUgNDA2Ljk4NDM3NSBMIDEyOC43MjY1NjMgNDEyLjIxNDg0NCBaIE0gMTI5LjQyNTc4MSA0MTguMTcxODc1IEMgMTI5LjU2NjQwNiA0MTcuNTgyMDMxIDEyOS44MDQ2ODggNDE2Ljg5ODQzOCAxMzAuMDE5NTMxIDQxNi4yNDIxODggTCAxMzMuMTQ4NDM4IDQwNi40MTc5NjkgQyAxMzMuMTk1MzEzIDQwNi4yNjU2MjUgMTMzLjI1IDQwNi4wOTc2NTYgMTMzLjI5Njg3NSA0MDUuOTQ1MzEzIEMgMTMzLjMwMDc4MSA0MDUuODc4OTA2IDEzMy4yNjk1MzEgNDA1Ljg1NTQ2OSAxMzMuMjI2NTYzIDQwNS44MjQyMTkgQyAxMzMuMTc5Njg4IDQwNS43ODkwNjMgMTMzLjE0MDYyNSA0MDUuNzgxMjUgMTMzLjA4NTkzOCA0MDUuNzY1NjI1IEMgMTMyLjY2Nzk2OSA0MDUuNzMwNDY5IDEzMS44NTE1NjMgNDA1LjU3ODEyNSAxMzEuMjUzOTA2IDQwNS4zODI4MTMgQyAxMzAuNzQ2MDk0IDQwNS44NjMyODEgMTI5LjkyMTg3NSA0MDYuNDAyMzQ0IDEyOS4zMTI1IDQwNi44MDg1OTQgTCAxMjEuNzkyOTY5IDQxMS44MjQyMTkgQyAxMjEuMTAxNTYzIDQxMi4yODEyNSAxMjAuMzUxNTYzIDQxMi4yNTM5MDYgMTE5Ljc3MzQzOCA0MTEuODE2NDA2IEwgMTE5LjY4MzU5NCA0MTEuNzUgTCAxMTkuMzQ3NjU2IDQxMi4xOTUzMTMgQyAxMTkuOTA2MjUgNDEyLjU2NjQwNiAxMjAuNDYwOTM4IDQxMi45NDE0MDYgMTIwLjk5NjA5NCA0MTMuMzQzNzUgQyAxMjEuNTg5ODQ0IDQxMy43OTI5NjkgMTIyLjE3NTc4MSA0MTQuMjgxMjUgMTIyLjc0NjA5NCA0MTQuNzYxNzE5IEwgMTIzLjA4MjAzMSA0MTQuMzE2NDA2IEwgMTIyLjkyMTg3NSA0MTQuMTkxNDA2IEMgMTIyLjQyOTY4OCA0MTMuODIwMzEzIDEyMS44NjMyODEgNDEzLjI3NzM0NCAxMjIuMTk5MjE5IDQxMi44MzIwMzEgQyAxMjIuNDAyMzQ0IDQxMi41NjY0MDYgMTIyLjg3MTA5NCA0MTIuMzEyNSAxMjMuMzk4NDM4IDQxMS45MjE4NzUgTCAxMjUuMDM5MDYzIDQxMC43MzQzNzUgTCAxMjguNDEwMTU2IDQxMy4yODEyNSBMIDEyNy42ODc1IDQxNS40Mzc1IEMgMTI3LjQ5MjE4OCA0MTYuMDM5MDYzIDEyNy4zMjQyMTkgNDE2LjUzOTA2MyAxMjcuMTc5Njg4IDQxNi43MzA0NjkgQyAxMjYuODk4NDM4IDQxNy4xMDE1NjMgMTI2LjI3MzQzOCA0MTYuNzI2NTYzIDEyNS45MzM1OTQgNDE2LjQ2ODc1IEwgMTI1Ljc2OTUzMSA0MTYuMzQzNzUgTCAxMjUuNDMzNTk0IDQxNi43ODkwNjMgQyAxMjYuMjEwOTM4IDQxNy4zMzIwMzEgMTI2Ljk3NjU2MyA0MTcuODYzMjgxIDEyNy43MDMxMjUgNDE4LjQxMDE1NiBDIDEyOC40MTc5NjkgNDE4Ljk0OTIxOSAxMjkuMDYyNSA0MTkuNDg0Mzc1IDEyOS43MDcwMzEgNDIwLjAxOTUzMSBMIDEzMC4wNDI5NjkgNDE5LjU3NDIxOSBMIDEyOS45NTMxMjUgNDE5LjUwMzkwNiBDIDEyOS40NjQ4NDQgNDE5LjEzNjcxOSAxMjkuMjg5MDYzIDQxOC43MjI2NTYgMTI5LjQyNTc4MSA0MTguMTcxODc1ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEzLjY5OTM0MSUsMTIuMTk5NDAyJSwxMi41JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDE0My42NTIzNDQgNDIxLjg3ODkwNiBDIDE0Mi4wNzgxMjUgNDI0LjI3MzQzOCAxMzkuMjYxNzE5IDQyNS41ODIwMzEgMTM2LjYxNzE4OCA0MjMuODQ3NjU2IEMgMTM1LjUgNDIzLjExMzI4MSAxMzUuMDkzNzUgNDIyLjY0ODQzOCAxMzUuODA4NTk0IDQyMS41NTg1OTQgTCAxNDEuMzQzNzUgNDEzLjEzMjgxMyBDIDE0MS43MDMxMjUgNDEzLjMyODEyNSAxNDIuMDkzNzUgNDEzLjUxNTYyNSAxNDIuNDQ5MjE5IDQxMy43NSBDIDE0NC45Mzc1IDQxNS4zODI4MTMgMTQ2LjM0NzY1NiA0MTcuNzc3MzQ0IDE0My42NTIzNDQgNDIxLjg3ODkwNiBaIE0gMTQ2LjAxOTUzMSA0MjMuMDE1NjI1IEMgMTQ4LjE1MjM0NCA0MTkuNzY1NjI1IDE0Ny4yMTQ4NDQgNDE2LjA3ODEyNSAxNDMuMzkwNjI1IDQxMy41NzAzMTMgQyAxNDIuNzIyNjU2IDQxMy4xMjg5MDYgMTQxLjg0Mzc1IDQxMi42NDA2MjUgMTQwLjg0NzY1NiA0MTEuOTg4MjgxIEMgMTM5Ljg1NTQ2OSA0MTEuMzMyMDMxIDEzOC44NjcxODggNDEwLjU5NzY1NiAxMzguNDAyMzQ0IDQxMC4yODkwNjMgTCAxMzguMDk3NjU2IDQxMC43NTc4MTMgTCAxMzguMzEyNSA0MTAuOTAyMzQ0IEMgMTM4Ljg3NSA0MTEuMjY5NTMxIDEzOS40MTQwNjMgNDExLjczNDM3NSAxMzguODgyODEzIDQxMi41NDI5NjkgTCAxMzMuNTMxMjUgNDIwLjY4NzUgQyAxMzMuMDAzOTA2IDQyMS40OTYwOTQgMTMyLjM1OTM3NSA0MjEuMTg3NSAxMzEuODAwNzgxIDQyMC44MTY0MDYgTCAxMzEuNTgyMDMxIDQyMC42NzU3ODEgTCAxMzEuMjc3MzQ0IDQyMS4xNDA2MjUgQyAxMzEuNjc5Njg4IDQyMS40MDYyNSAxMzIuODI0MjE5IDQyMi4wNzAzMTMgMTMzLjg4MjgxMyA0MjIuNzYxNzE5IEMgMTM0Ljk0MTQwNiA0MjMuNDU3MDMxIDEzNi4wMDc4MTMgNDI0LjIwMzEyNSAxMzYuNjcxODc1IDQyNC42ODM1OTQgQyAxMzkuNzAzMTI1IDQyNi45NDE0MDYgMTQzLjk4MDQ2OSA0MjYuMTI1IDE0Ni4wMTk1MzEgNDIzLjAxNTYyNSAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMy42OTkzNDElLDEyLjE5OTQwMiUsMTIuNSUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAxNTIuODIwMzEzIDQyNy45Njg3NSBMIDE0OS44MDA3ODEgNDI2LjI0MjE4OCBMIDE1My45MTc5NjkgNDIyLjUzMTI1IEwgMTUzLjk0OTIxOSA0MjIuNTUwNzgxIFogTSAxNTQuMjY1NjI1IDQzMy43OTI5NjkgQyAxNTQuMzMyMDMxIDQzMy4xODc1IDE1NC40ODA0NjkgNDMyLjQ4MDQ2OSAxNTQuNjA5Mzc1IDQzMS44MDQ2ODggTCAxNTYuNDc2NTYzIDQyMS42NjAxNTYgQyAxNTYuNSA0MjEuNTAzOTA2IDE1Ni41MzUxNTYgNDIxLjMzMjAzMSAxNTYuNTYyNSA0MjEuMTc1NzgxIEMgMTU2LjU1ODU5NCA0MjEuMTA5Mzc1IDE1Ni41MjM0MzggNDIxLjA4OTg0NCAxNTYuNDc2NTYzIDQyMS4wNjI1IEMgMTU2LjQyOTY4OCA0MjEuMDM1MTU2IDE1Ni4zODY3MTkgNDIxLjAzMTI1IDE1Ni4zMjgxMjUgNDIxLjAxOTUzMSBDIDE1NS45MTAxNTYgNDIxLjAzOTA2MyAxNTUuMDc4MTI1IDQyMC45OTIxODggMTU0LjQ2MDkzOCA0MjAuODcxMDk0IEMgMTU0LjAyMzQzOCA0MjEuNDE0MDYzIDE1My4yNjk1MzEgNDIyLjA1NDY4OCAxNTIuNzE4NzUgNDIyLjUzMTI1IEwgMTQ1Ljg5NDUzMSA0MjguNDYwOTM4IEMgMTQ1LjI2MTcxOSA0MjkgMTQ0LjUxOTUzMSA0MjkuMDY2NDA2IDE0My44OTA2MjUgNDI4LjcwNzAzMSBMIDE0My43OTI5NjkgNDI4LjY1MjM0NCBMIDE0My41MTU2MjUgNDI5LjEzNjcxOSBDIDE0NC4xMTMyODEgNDI5LjQzNzUgMTQ0LjcxNDg0NCA0MjkuNzM0Mzc1IDE0NS4yOTI5NjkgNDMwLjA3MDMxMyBDIDE0NS45NDE0MDYgNDMwLjQzNzUgMTQ2LjU4MjAzMSA0MzAuODUxNTYzIDE0Ny4yMTA5MzggNDMxLjI1IEwgMTQ3LjQ4ODI4MSA0MzAuNzY5NTMxIEwgMTQ3LjMwODU5NCA0MzAuNjY0MDYzIEMgMTQ2Ljc3NzM0NCA0MzAuMzU5Mzc1IDE0Ni4xNDQ1MzEgNDI5Ljg5MDYyNSAxNDYuNDIxODc1IDQyOS40MDYyNSBDIDE0Ni41ODk4NDQgNDI5LjExNzE4OCAxNDcuMDIzNDM4IDQyOC44MDg1OTQgMTQ3LjUgNDI4LjM1MTU2MyBMIDE0OC45NzY1NjMgNDI2Ljk2ODc1IEwgMTUyLjY0MDYyNSA0MjkuMDY2NDA2IEwgMTUyLjE5OTIxOSA0MzEuMzAwNzgxIEMgMTUyLjA3ODEyNSA0MzEuOTE3OTY5IDE1MS45NzY1NjMgNDMyLjQzNzUgMTUxLjg1NTQ2OSA0MzIuNjQ4NDM4IEMgMTUxLjYyNSA0MzMuMDUwNzgxIDE1MC45NTcwMzEgNDMyLjc1MzkwNiAxNTAuNTg1OTM4IDQzMi41NDI5NjkgTCAxNTAuNDEwMTU2IDQzMi40NDE0MDYgTCAxNTAuMTMyODEzIDQzMi45MjU3ODEgQyAxNTAuOTcyNjU2IDQzMy4zNjMyODEgMTUxLjgwMDc4MSA0MzMuNzkyOTY5IDE1Mi41ODk4NDQgNDM0LjI0NjA5NCBDIDE1My4zNjMyODEgNDM0LjY5MTQwNiAxNTQuMDcwMzEzIDQzNS4xNDA2MjUgMTU0Ljc4MTI1IDQzNS41ODU5MzggTCAxNTUuMDU4NTk0IDQzNS4xMDE1NjMgTCAxNTQuOTYwOTM4IDQzNS4wNDY4NzUgQyAxNTQuNDI5Njg4IDQzNC43NDIxODggMTU0LjE5OTIxOSA0MzQuMzU1NDY5IDE1NC4yNjU2MjUgNDMzLjc5Mjk2OSAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMy42OTkzNDElLDEyLjE5OTQwMiUsMTIuNSUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAxNzEuMTU2MjUgNDI5LjIxMDkzOCBMIDE3MC45MTQwNjMgNDI5LjcxMDkzOCBMIDE3MS4yODEyNSA0MjkuODkwNjI1IEMgMTcxLjc4NTE1NiA0MzAuMTMyODEzIDE3Mi42NDA2MjUgNDMwLjc5Njg3NSAxNzEuOTc2NTYzIDQzMi4xNjc5NjkgTCAxNjguOTMzNTk0IDQzOC40NDUzMTMgTCAxNjguODgyODEzIDQzOC40NjA5MzggTCAxNjUuNSA0MjYuNDY0ODQ0IEMgMTY1IDQyNi4yMjI2NTYgMTY0LjQ4MDQ2OSA0MjYuMDU0Njg4IDE2My45ODA0NjkgNDI1LjgxMjUgQyAxNjMuMzQzNzUgNDI1LjUwMzkwNiAxNjIuNzIyNjU2IDQyNS4xMjEwOTQgMTYyLjA4NTkzOCA0MjQuODEyNSBMIDE2MS44NDM3NSA0MjUuMzEyNSBMIDE2Mi4wNjI1IDQyNS40MTc5NjkgQyAxNjIuODEyNSA0MjUuNzgxMjUgMTYzLjMwODU5NCA0MjYuNzI2NTYzIDE2Mi44NTE1NjMgNDI3LjY2MDE1NiBMIDE1OS40Mzc1IDQzNC43MDcwMzEgQyAxNTguNzg1MTU2IDQzNi4wNDY4NzUgMTU4LjA1NDY4OCA0MzYuNjY0MDYzIDE1Ni44OTg0MzggNDM2LjEwMTU2MyBMIDE1Ni42NjQwNjMgNDM1Ljk4ODI4MSBMIDE1Ni40MjE4NzUgNDM2LjQ5MjE4OCBDIDE1Ny4xNzU3ODEgNDM2Ljg1NTQ2OSAxNTcuOTc2NTYzIDQzNy4xNjQwNjMgMTU4LjczMDQ2OSA0MzcuNTI3MzQ0IEMgMTU5LjQ0OTIxOSA0MzcuODc1IDE2MC4xMzY3MTkgNDM4LjI5Mjk2OSAxNjAuODU1NDY5IDQzOC42NDA2MjUgTCAxNjEuMTAxNTYzIDQzOC4xNDA2MjUgTCAxNjAuODE2NDA2IDQzOC4wMDM5MDYgQyAxNTkuNTI3MzQ0IDQzNy4zNzUgMTU5LjQ4NDM3NSA0MzYuNzM4MjgxIDE2MC4xOTE0MDYgNDM1LjI4MTI1IEwgMTYzLjUzNTE1NiA0MjguMzg2NzE5IEwgMTY3LjQ5NjA5NCA0NDIuMTcxODc1IEwgMTY4LjEzMjgxMyA0NDIuNDgwNDY5IEMgMTY4LjMwMDc4MSA0NDEuOTIxODc1IDE2OC41NjY0MDYgNDQxLjMyODEyNSAxNjguODUxNTYzIDQ0MC43NDIxODggTCAxNzIuNTQyOTY5IDQzMy4xMjUgQyAxNzMuNTExNzE5IDQzMS4xMzY3MTkgMTc0LjM1OTM3NSA0MzEuMzgyODEzIDE3NS4wNjI1IDQzMS43MjI2NTYgTCAxNzUuMzE2NDA2IDQzMS44NDc2NTYgTCAxNzUuNTU4NTk0IDQzMS4zNDM3NSBDIDE3NC44NzEwOTQgNDMxLjAxMTcxOSAxNzQuMTUyMzQ0IDQzMC43NDYwOTQgMTczLjQ2ODc1IDQzMC40MTQwNjMgQyAxNzIuNjc5Njg4IDQzMC4wMzEyNSAxNzEuOTQ1MzEzIDQyOS41ODk4NDQgMTcxLjE1NjI1IDQyOS4yMTA5MzggIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoMTMuNjk5MzQxJSwxMi4xOTk0MDIlLDEyLjUlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMTg5Ljc2MTcxOSA0NDAuNzUzOTA2IEMgMTkwLjcyNjU2MyA0MzguMjE0ODQ0IDE4OS4zMDQ2ODggNDM2Ljc3NzM0NCAxODYuOTQxNDA2IDQzNS44Nzg5MDYgQyAxODYuMTYwMTU2IDQzNS41NzgxMjUgMTg1LjI4MTI1IDQzNS4zMjQyMTkgMTg0LjM3ODkwNiA0MzQuOTgwNDY5IEMgMTgzLjQ4ODI4MSA0MzQuNjQ0NTMxIDE4Mi41OTM3NSA0MzQuMjIyNjU2IDE4MS45Njg3NSA0MzMuOTg0Mzc1IEwgMTgxLjc2OTUzMSA0MzQuNTA3ODEzIEwgMTgxLjk4MDQ2OSA0MzQuNTg1OTM4IEMgMTgyLjgxMjUgNDM0LjkwMjM0NCAxODMuMDY2NDA2IDQzNS4yMzgyODEgMTgyLjYyMTA5NCA0MzYuNDAyMzQ0IEwgMTc5LjQ1NzAzMSA0NDQuNzEwOTM4IEMgMTc4LjkyOTY4OCA0NDYuMTAxNTYzIDE3OC4zNDc2NTYgNDQ1LjkwMjM0NCAxNzcuODI0MjE5IDQ0NS43MDMxMjUgTCAxNzcuNTQ2ODc1IDQ0NS41OTc2NTYgTCAxNzcuMzQ3NjU2IDQ0Ni4xMTcxODggQyAxNzguMzM5ODQ0IDQ0Ni40OTYwOTQgMTc5LjMwNDY4OCA0NDYuNzgxMjUgMTgwLjI2MTcxOSA0NDcuMTQ4NDM4IEMgMTgxLjE0ODQzOCA0NDcuNDg0Mzc1IDE4MS45OTIxODggNDQ3Ljg4NjcxOSAxODIuODc4OTA2IDQ0OC4yMjI2NTYgTCAxODMuMDc0MjE5IDQ0Ny42OTkyMTkgTCAxODIuNzk2ODc1IDQ0Ny41OTM3NSBDIDE4MS45MTAxNTYgNDQ3LjI1NzgxMyAxODEuMTYwMTU2IDQ0Ni45MzM1OTQgMTgxLjY5NTMxMyA0NDUuNTIzNDM4IEwgMTg1LjMyODEyNSA0MzUuOTgwNDY5IEwgMTg1LjgzNTkzOCA0MzYuMTcxODc1IEMgMTg3LjYyNSA0MzYuODU1NDY5IDE4OC4wMzkwNjMgNDM4LjI2OTUzMSAxODcuNDA2MjUgNDM5LjkzNzUgQyAxODYuNzUgNDQxLjY1NjI1IDE4NS42MzI4MTMgNDQyLjY2NDA2MyAxODQuMjIyNjU2IDQ0Mi4xMjg5MDYgTCAxODMuODU5Mzc1IDQ0MS45ODgyODEgTCAxODMuNjYwMTU2IDQ0Mi41MTE3MTkgQyAxODQuMDU4NTk0IDQ0Mi42NjAxNTYgMTg0LjUxMTcxOSA0NDIuODMyMDMxIDE4NS4wNjI1IDQ0My4wMDM5MDYgQyAxODcuMDQ2ODc1IDQ0My41NDI5NjkgMTg4Ljk4ODI4MSA0NDIuNzg1MTU2IDE4OS43NjE3MTkgNDQwLjc1MzkwNiAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMy42OTkzNDElLDEyLjE5OTQwMiUsMTIuNSUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAxOTYuNDMzNTk0IDQzOS4yOTY4NzUgQyAxOTQuOTQ1MzEzIDQzOC44MTY0MDYgMTkzLjEyODkwNiA0MzguMTUyMzQ0IDE5Mi4wNTA3ODEgNDM3LjgwNDY4OCBMIDE5MS44Nzg5MDYgNDM4LjMzNTkzOCBMIDE5Mi4xMjUgNDM4LjQxNzk2OSBDIDE5Mi43NjE3MTkgNDM4LjYyMTA5NCAxOTMuNDA2MjUgNDM4LjkyNTc4MSAxOTMuMTA5Mzc1IDQzOS44NDc2NTYgTCAxOTAuMTIxMDk0IDQ0OS4xMjEwOTQgQyAxODkuODI0MjE5IDQ1MC4wNDI5NjkgMTg5LjEyNSA0NDkuOTE0MDYzIDE4OC40ODQzNzUgNDQ5LjcxMDkzOCBMIDE4OC4yMzgyODEgNDQ5LjYyODkwNiBMIDE4OC4wNjY0MDYgNDUwLjE2MDE1NiBDIDE4OS4wNzQyMTkgNDUwLjQ4NDM3NSAxOTEuMjAzMTI1IDQ1MS4wOTM3NSAxOTIuODAwNzgxIDQ1MS42MDU0NjkgQyAxOTQuMzkwNjI1IDQ1Mi4xMjEwOTQgMTk2LjQwMjM0NCA0NTIuODQ3NjU2IDE5Ny41MzUxNTYgNDUzLjIxMDkzOCBDIDE5OCA0NTIuMzI0MjE5IDE5OC41MTU2MjUgNDUxLjQ1NzAzMSAxOTkuMDQ2ODc1IDQ1MC41OTM3NSBMIDE5OC41ODk4NDQgNDUwLjMwODU5NCBDIDE5Ny40MTAxNTYgNDUyLjE1NjI1IDE5Ni40MjU3ODEgNDUxLjk5MjE4OCAxOTQuMzAwNzgxIDQ1MS4zMDg1OTQgQyAxOTMuMTY3OTY5IDQ1MC45NDUzMTMgMTkyLjE0MDYyNSA0NTAuNjEzMjgxIDE5Mi41MTE3MTkgNDQ5LjQ2MDkzOCBMIDE5My44NDM3NSA0NDUuMzM5ODQ0IEwgMTk1Ljk2NDg0NCA0NDYuMDIzNDM4IEMgMTk3LjE4NzUgNDQ2LjQxNzk2OSAxOTcuMDE5NTMxIDQ0Ny4xMjUgMTk2Ljc4MTI1IDQ0OC4yMjI2NTYgTCAxOTcuMzQ3NjU2IDQ0OC4yODUxNTYgQyAxOTcuNTI3MzQ0IDQ0Ny42MDE1NjMgMTk3LjcyNjU2MyA0NDYuOTIxODc1IDE5Ny45NDUzMTMgNDQ2LjI1IEMgMTk4LjE2NDA2MyA0NDUuNTYyNSAxOTguNDA2MjUgNDQ0Ljg3NSAxOTguNjY0MDYzIDQ0NC4xOTUzMTMgTCAxOTguMTMyODEzIDQ0NC4wMjczNDQgQyAxOTcuNzE4NzUgNDQ0Ljk0OTIxOSAxOTcuMjk2ODc1IDQ0NS40NzY1NjMgMTk2LjIzNDM3NSA0NDUuMTMyODEzIEwgMTk0LjEyODkwNiA0NDQuNDUzMTI1IEwgMTk1LjYyMTA5NCA0MzkuODE2NDA2IEwgMTk4LjA4MjAzMSA0NDAuNjA5Mzc1IEMgMTk5Ljk0MTQwNiA0NDEuMjA3MDMxIDE5OS44NTU0NjkgNDQyLjE5NTMxMyAxOTkuNTc0MjE5IDQ0My4zNzUgTCAyMDAuMTQ4NDM4IDQ0My40MDYyNSBDIDIwMC4zNDc2NTYgNDQyLjYwOTM3NSAyMDAuNzA3MDMxIDQ0MS40Mzc1IDIwMC45ODgyODEgNDQwLjY4NzUgQyAxOTkuNzg1MTU2IDQ0MC4yOTY4NzUgMTk3LjkyMTg3NSA0MzkuNzc3MzQ0IDE5Ni40MzM1OTQgNDM5LjI5Njg3NSAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMy42OTkzNDElLDEyLjE5OTQwMiUsMTIuNSUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAyMTAuMTUyMzQ0IDQ0Ni42OTE0MDYgQyAyMDkuNjAxNTYzIDQ0OC44MTY0MDYgMjA4LjQ1MzEyNSA0NDkuMjUgMjA2LjY1MjM0NCA0NDguNzg1MTU2IEwgMjA1Ljc2OTUzMSA0NDguNTU4NTk0IEwgMjA3LjE1NjI1IDQ0My4xOTE0MDYgQyAyMDcuNDEwMTU2IDQ0My4yMzgyODEgMjA3LjY2MDE1NiA0NDMuMjQ2MDk0IDIwOC4xOTkyMTkgNDQzLjM4NjcxOSBDIDIwOS44MDQ2ODggNDQzLjgwMDc4MSAyMTAuNTYyNSA0NDUuMDg5ODQ0IDIxMC4xNTIzNDQgNDQ2LjY5MTQwNiBaIE0gMjEyLjU4OTg0NCA0NDcuMjA3MDMxIEMgMjEzLjI1IDQ0NC42NTIzNDQgMjExLjM5NDUzMSA0NDMuNTE5NTMxIDIwOS4xMjUgNDQyLjkzMzU5NCBDIDIwOC4xNjc5NjkgNDQyLjY4NzUgMjA3LjI4NTE1NiA0NDIuNTM1MTU2IDIwNi4yMDcwMzEgNDQyLjI1NzgxMyBDIDIwNS4xMDkzNzUgNDQxLjk3MjY1NiAyMDQuMDExNzE5IDQ0MS42MTMyODEgMjAzLjQzMzU5NCA0NDEuNDY0ODQ0IEwgMjAzLjI5Njg3NSA0NDIuMDAzOTA2IEwgMjAzLjYxNzE4OCA0NDIuMDg1OTM4IEMgMjA0LjE3NTc4MSA0NDIuMjMwNDY5IDIwNC44ODI4MTMgNDQyLjQ3MjY1NiAyMDQuNTQyOTY5IDQ0My43ODUxNTYgTCAyMDIuMTgzNTk0IDQ1Mi45MzM1OTQgQyAyMDIuMDExNzE5IDQ1My42MDE1NjMgMjAxLjMyMDMxMyA0NTMuNzQ2MDk0IDIwMC42NTIzNDQgNDUzLjU3NDIxOSBMIDIwMC4zMjgxMjUgNDUzLjQ5MjE4OCBMIDIwMC4xOTE0MDYgNDU0LjAzMTI1IEMgMjAxLjA4OTg0NCA0NTQuMjY1NjI1IDIwMS45NTcwMzEgNDU0LjQxMDE1NiAyMDIuODIwMzEzIDQ1NC42MzI4MTMgQyAyMDMuODQ3NjU2IDQ1NC44OTg0MzggMjA0Ljg3MTA5NCA0NTUuMjQyMTg4IDIwNS44OTg0MzggNDU1LjUwMzkwNiBMIDIwNi4wMzkwNjMgNDU0Ljk2NDg0NCBMIDIwNS43MTQ4NDQgNDU0Ljg4MjgxMyBDIDIwNC44ODY3MTkgNDU0LjY2Nzk2OSAyMDQuMjUgNDU0LjQ0NTMxMyAyMDQuNjA5Mzc1IDQ1My4wNTg1OTQgTCAyMDUuNjAxNTYzIDQ0OS4yMDcwMzEgTCAyMDYuNzkyOTY5IDQ0OS41MTE3MTkgQyAyMDcuNDI1NzgxIDQ1MS44ODY3MTkgMjA4LjExMzI4MSA0NTQuMTM2NzE5IDIwOS4wMzEyNSA0NTYuMzEyNSBDIDIwOS41ODk4NDQgNDU2LjQ1NzAzMSAyMTAuMTgzNTk0IDQ1Ni41MzUxNTYgMjEwLjc0MjE4OCA0NTYuNjc5Njg4IEMgMjExLjMzNTkzOCA0NTYuODMyMDMxIDIxMS44OTQ1MzEgNDU3LjA1NDY4OCAyMTIuNDg4MjgxIDQ1Ny4yMDcwMzEgTCAyMTIuNjI4OTA2IDQ1Ni42NjQwNjMgQyAyMTEuNzczNDM4IDQ1Ni4zMjgxMjUgMjExLjQ2ODc1IDQ1Ni4wMjM0MzggMjExLjE2MDE1NiA0NTUuMTM2NzE5IEwgMjA5LjI2OTUzMSA0NDkuNzMwNDY5IEMgMjEwLjgzNTkzOCA0NDkuNTM5MDYzIDIxMi4xNzE4NzUgNDQ4LjgyODEyNSAyMTIuNTg5ODQ0IDQ0Ny4yMDcwMzEgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoMTMuNjk5MzQxJSwxMi4xOTk0MDIlLDEyLjUlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMjI3LjI0MjE4OCA0NDkuNjUyMzQ0IEwgMjI3LjgzMjAzMSA0NDkuNTU4NTk0IEMgMjI3LjkyNTc4MSA0NDkuMDY2NDA2IDIyOC4wMjM0MzggNDQ4LjU3NDIxOSAyMjguMTU2MjUgNDQ4LjA4NTkzOCBDIDIyOC4zMDg1OTQgNDQ3LjYwNTQ2OSAyMjguNDc2NTYzIDQ0Ny4xMjUgMjI4LjY0NDUzMSA0NDYuNjQ4NDM4IEwgMjI4LjIyMjY1NiA0NDYuNDg4MjgxIEMgMjI4LjA3ODEyNSA0NDcuMDI3MzQ0IDIyNy42MTcxODggNDQ2Ljk1NzAzMSAyMjcuMTI1IDQ0Ni44NjMyODEgTCAyMTcuNzA3MDMxIDQ0NS4wMjM0MzggQyAyMTcuMjE0ODQ0IDQ0NC45Mjk2ODggMjE2Ljc1MzkwNiA0NDQuODU5Mzc1IDIxNi43MTQ4NDQgNDQ0LjI4MTI1IEwgMjE2LjI3NzM0NCA0NDQuMTk1MzEzIEMgMjE2LjE3MTg3NSA0NDQuNzI2NTYzIDIxNi4wMzUxNTYgNDQ1LjIzMDQ2OSAyMTUuODYzMjgxIDQ0NS43MjY1NjMgQyAyMTUuNzA3MDMxIDQ0Ni4yNDYwOTQgMjE1LjUxNTYyNSA0NDYuNzM4MjgxIDIxNS4zNDM3NSA0NDcuMjM0Mzc1IEwgMjE1Ljg5MDYyNSA0NDcuMzQzNzUgQyAyMTYuNDIxODc1IDQ0Ni4wNjI1IDIxNi41NDI5NjkgNDQ1Ljc0NjA5NCAyMTcuOTEwMTU2IDQ0Ni4wMTE3MTkgTCAyMjAuOTA2MjUgNDQ2LjU5NzY1NiBMIDIxOS4wMDM5MDYgNDU2LjM0Mzc1IEMgMjE4LjcyMjY1NiA0NTcuNzg1MTU2IDIxOC4xOTE0MDYgNDU3Ljc3NzM0NCAyMTcuMTg3NSA0NTcuNTgyMDMxIEwgMjE2Ljg0Mzc1IDQ1Ny41MTU2MjUgTCAyMTYuNzM0Mzc1IDQ1OC4wNjI1IEMgMjE3LjQ0NTMxMyA0NTguMTk5MjE5IDIxOC43MzgyODEgNDU4LjM3NSAyMTkuODM1OTM4IDQ1OC41ODk4NDQgQyAyMjAuODIwMzEzIDQ1OC43ODEyNSAyMjIuMDg1OTM4IDQ1OS4xMDU0NjkgMjIyLjc5Njg3NSA0NTkuMjQyMTg4IEwgMjIyLjkwMjM0NCA0NTguNjk1MzEzIEwgMjIyLjU1NDY4OCA0NTguNjI4OTA2IEMgMjIxLjY3OTY4OCA0NTguNDU3MDMxIDIyMS4wNzQyMTkgNDU4LjE2Nzk2OSAyMjEuMzQ3NjU2IDQ1Ni43NjE3MTkgTCAyMjMuMjQyMTg4IDQ0Ny4wNTA3ODEgTCAyMjYuMjM0Mzc1IDQ0Ny42MzY3MTkgQyAyMjcuNDU3MDMxIDQ0Ny44NzUgMjI3LjMzOTg0NCA0NDguOTY4NzUgMjI3LjI0MjE4OCA0NDkuNjUyMzQ0ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEzLjY5OTM0MSUsMTIuMTk5NDAyJSwxMi41JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDIzMS4xNTIzNDQgNDU0LjkwMjM0NCBMIDIzMy41NzgxMjUgNDQ5LjkyMTg3NSBMIDIzMy42MTMyODEgNDQ5LjkyNTc4MSBMIDIzNC41OTc2NTYgNDU1LjM3MTA5NCBaIE0gMjM4LjEyMTA5NCA0NjAuMjIyNjU2IEMgMjM3Ljk1NzAzMSA0NTkuNjM2NzE5IDIzNy44MjgxMjUgNDU4LjkyNTc4MSAyMzcuNjk1MzEzIDQ1OC4yNSBMIDIzNS42MjEwOTQgNDQ4LjE1MjM0NCBDIDIzNS41ODU5MzggNDQ4IDIzNS41NTQ2ODggNDQ3LjgyNDIxOSAyMzUuNTE1NjI1IDQ0Ny42Njc5NjkgQyAyMzUuNDg4MjgxIDQ0Ny42MDkzNzUgMjM1LjQ0OTIxOSA0NDcuNjA1NDY5IDIzNS4zOTQ1MzEgNDQ3LjU5NzY1NiBDIDIzNS4zMzk4NDQgNDQ3LjU4OTg0NCAyMzUuMzAwNzgxIDQ0Ny42MDE1NjMgMjM1LjI0MjE4OCA0NDcuNjEzMjgxIEMgMjM0Ljg2MzI4MSA0NDcuNzg5MDYzIDIzNC4wNzQyMTkgNDQ4LjA1NDY4OCAyMzMuNDYwOTM4IDQ0OC4xNzk2ODggQyAyMzMuMjU3ODEzIDQ0OC44NDM3NSAyMzIuNzk2ODc1IDQ0OS43MTg3NSAyMzIuNDY0ODQ0IDQ1MC4zNzEwOTQgTCAyMjguMzYzMjgxIDQ1OC40MjE4NzUgQyAyMjcuOTg0Mzc1IDQ1OS4xNjAxNTYgMjI3LjMxNjQwNiA0NTkuNSAyMjYuNTk3NjU2IDQ1OS40MDIzNDQgTCAyMjYuNDg4MjgxIDQ1OS4zODY3MTkgTCAyMjYuNDE0MDYzIDQ1OS45NDE0MDYgQyAyMjcuMDgyMDMxIDQ1OS45OTYwOTQgMjI3Ljc1IDQ2MC4wNDY4NzUgMjI4LjQxNDA2MyA0NjAuMTQwNjI1IEMgMjI5LjE0ODQzOCA0NjAuMjM4MjgxIDIyOS44OTg0MzggNDYwLjM3ODkwNiAyMzAuNjMyODEzIDQ2MC41MTU2MjUgTCAyMzAuNzA3MDMxIDQ1OS45NjQ4NDQgTCAyMzAuNTAzOTA2IDQ1OS45Mzc1IEMgMjI5Ljg5ODQzOCA0NTkuODUxNTYzIDIyOS4xMzY3MTkgNDU5LjY1NjI1IDIyOS4yMTA5MzggNDU5LjEwMTU2MyBDIDIyOS4yNTc4MTMgNDU4Ljc2OTUzMSAyMjkuNTQyOTY5IDQ1OC4zMjAzMTMgMjI5LjgxMjUgNDU3LjcyMjY1NiBMIDIzMC42NjQwNjMgNDU1Ljg4NjcxOSBMIDIzNC44NDM3NSA0NTYuNDUzMTI1IEwgMjM1LjI3MzQzOCA0NTguNjkxNDA2IEMgMjM1LjM5NDUzMSA0NTkuMzA4NTk0IDIzNS40OTIxODggNDU5LjgyODEyNSAyMzUuNDYwOTM4IDQ2MC4wNjY0MDYgQyAyMzUuMzk4NDM4IDQ2MC41MjczNDQgMjM0LjY2Nzk2OSA0NjAuNTAzOTA2IDIzNC4yNDYwOTQgNDYwLjQ0NTMxMyBMIDIzNC4wNDI5NjkgNDYwLjQxNzk2OSBMIDIzMy45Njg3NSA0NjAuOTcyNjU2IEMgMjM0LjkxMDE1NiA0NjEuMDYyNSAyMzUuODM5ODQ0IDQ2MS4xNTIzNDQgMjM2Ljc0MjE4OCA0NjEuMjczNDM4IEMgMjM3LjYyNSA0NjEuMzk0NTMxIDIzOC40NDkyMTkgNDYxLjU0Mjk2OSAyMzkuMjczNDM4IDQ2MS42OTUzMTMgTCAyMzkuMzQ3NjU2IDQ2MS4xNDA2MjUgTCAyMzkuMjM4MjgxIDQ2MS4xMjUgQyAyMzguNjI4OTA2IDQ2MS4wNDI5NjkgMjM4LjI3MzQzOCA0NjAuNzY5NTMxIDIzOC4xMjEwOTQgNDYwLjIyMjY1NiAiLz4KPGcgY2xpcC1wYXRoPSJ1cmwoI2NsaXAxKSIgY2xpcC1ydWxlPSJub256ZXJvIj4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMy42OTkzNDElLDEyLjE5OTQwMiUsMTIuNSUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAyNTIuMDU4NTk0IDQ0OS42NDQ1MzEgTCAyNTIuMDIzNDM4IDQ1MC4yMDMxMjUgTCAyNTIuNDI5Njg4IDQ1MC4yMzA0NjkgQyAyNTIuOTg4MjgxIDQ1MC4yNjk1MzEgMjU0LjAzMTI1IDQ1MC41NjI1IDI1My45MjU3ODEgNDUyLjA4MjAzMSBMIDI1My40NTcwMzEgNDU5LjAzOTA2MyBMIDI1My40MTc5NjkgNDU5LjA3NDIxOSBMIDI0NS43ODkwNjMgNDQ5LjIyMjY1NiBDIDI0NS4yMzQzNzUgNDQ5LjE4MzU5NCAyNDQuNjkxNDA2IDQ0OS4yMjI2NTYgMjQ0LjEzMjgxMyA0NDkuMTgzNTk0IEMgMjQzLjQyOTY4OCA0NDkuMTM2NzE5IDI0Mi43MTA5MzggNDQ5LjAxMTcxOSAyNDIuMDAzOTA2IDQ0OC45NjQ4NDQgTCAyNDEuOTY4NzUgNDQ5LjUyMzQzOCBMIDI0Mi4yMTA5MzggNDQ5LjUzOTA2MyBDIDI0My4wNDI5NjkgNDQ5LjU5Mzc1IDI0My44NTU0NjkgNDUwLjI4MTI1IDI0My43ODUxNTYgNDUxLjMyMDMxMyBMIDI0My4yNTc4MTMgNDU5LjEzMjgxMyBDIDI0My4xNTYyNSA0NjAuNjE3MTg4IDI0Mi43MDcwMzEgNDYxLjQ2MDkzOCAyNDEuNDI1NzgxIDQ2MS4zNzUgTCAyNDEuMTY0MDYzIDQ2MS4zNTkzNzUgTCAyNDEuMTI4OTA2IDQ2MS45MTQwNjMgQyAyNDEuOTY0ODQ0IDQ2MS45NzI2NTYgMjQyLjgyMDMxMyA0NjEuOTUzMTI1IDI0My42NTYyNSA0NjIuMDExNzE5IEMgMjQ0LjQ1MzEyNSA0NjIuMDY2NDA2IDI0NS4yNDYwOTQgNDYyLjE5MTQwNiAyNDYuMDQ2ODc1IDQ2Mi4yNDYwOTQgTCAyNDYuMDgyMDMxIDQ2MS42OTE0MDYgTCAyNDUuNzY1NjI1IDQ2MS42Njc5NjkgQyAyNDQuMzM5ODQ0IDQ2MS41NzQyMTkgMjQ0LjA2MjUgNDYwLjk5MjE4OCAyNDQuMTcxODc1IDQ1OS4zNzg5MDYgTCAyNDQuNjg3NSA0NTEuNzM4MjgxIEwgMjUzLjUxOTUzMSA0NjMuMDMxMjUgTCAyNTQuMjI2NTYzIDQ2My4wNzgxMjUgQyAyNTQuMTcxODc1IDQ2Mi41IDI1NC4xOTkyMTkgNDYxLjg0NzY1NiAyNTQuMjQyMTg4IDQ2MS4xOTkyMTkgTCAyNTQuODEyNSA0NTIuNzU3ODEzIEMgMjU0Ljk2NDg0NCA0NTAuNTUwNzgxIDI1NS44NDM3NSA0NTAuNDYwOTM4IDI1Ni42MjEwOTQgNDUwLjUxNTYyNSBMIDI1Ni45MDIzNDQgNDUwLjUzMTI1IEwgMjU2LjkzNzUgNDQ5Ljk3NjU2MyBDIDI1Ni4xNzk2ODggNDQ5LjkyNTc4MSAyNTUuNDE0MDYzIDQ0OS45NDUzMTMgMjU0LjY1MjM0NCA0NDkuODk0NTMxIEMgMjUzLjc4MTI1IDQ0OS44MzU5MzggMjUyLjkzMzU5NCA0NDkuNzAzMTI1IDI1Mi4wNTg1OTQgNDQ5LjY0NDUzMSAiLz4KPC9nPgo8ZyBjbGlwLXBhdGg9InVybCgjY2xpcDIpIiBjbGlwLXJ1bGU9Im5vbnplcm8iPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEzLjY5OTM0MSUsMTIuMTk5NDAyJSwxMi41JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDI2MS4yNjU2MjUgNDU3LjI3NzM0NCBMIDI2My4wNzgxMjUgNDUyLjA0Mjk2OSBMIDI2My4xMTMyODEgNDUyLjA0Mjk2OSBMIDI2NC43NDIxODggNDU3LjMzMjAzMSBaIE0gMjY4LjgxNjQwNiA0NjEuNzMwNDY5IEMgMjY4LjU4NTkzOCA0NjEuMTY3OTY5IDI2OC4zNzEwOTQgNDYwLjQ3NjU2MyAyNjguMTYwMTU2IDQ1OS44MjQyMTkgTCAyNjQuODk0NTMxIDQ1MC4wNDI5NjkgQyAyNjQuODQzNzUgNDQ5Ljg5NDUzMSAyNjQuNzg5MDYzIDQ0OS43MjY1NjMgMjY0LjczNDM3NSA0NDkuNTc0MjE5IEMgMjY0LjY5OTIxOSA0NDkuNTE5NTMxIDI2NC42NjAxNTYgNDQ5LjUxOTUzMSAyNjQuNjA1NDY5IDQ0OS41MTk1MzEgQyAyNjQuNTUwNzgxIDQ0OS41MTU2MjUgMjY0LjUxMTcxOSA0NDkuNTM1MTU2IDI2NC40NTcwMzEgNDQ5LjU1MDc4MSBDIDI2NC4xMDE1NjMgNDQ5Ljc2OTUzMSAyNjMuMzUxNTYzIDQ1MC4xMjg5MDYgMjYyLjc1MzkwNiA0NTAuMzI0MjE5IEMgMjYyLjYyODkwNiA0NTEuMDExNzE5IDI2Mi4yNzczNDQgNDUxLjkzMzU5NCAyNjIuMDI3MzQ0IDQ1Mi42MjEwOTQgTCAyNTguOTE0MDYzIDQ2MS4xMDU0NjkgQyAyNTguNjI1IDQ2MS44ODI4MTMgMjU4LjAwMzkwNiA0NjIuMzAwNzgxIDI1Ny4yNzczNDQgNDYyLjI4OTA2MyBMIDI1Ny4xNjQwNjMgNDYyLjI4OTA2MyBMIDI1Ny4xNTYyNSA0NjIuODQ3NjU2IEMgMjU3LjgyODEyNSA0NjIuODIwMzEzIDI1OC40OTYwOTQgNDYyLjc5Mjk2OSAyNTkuMTY3OTY5IDQ2Mi44MDQ2ODggQyAyNTkuOTEwMTU2IDQ2Mi44MTY0MDYgMjYwLjY3MTg3NSA0NjIuODYzMjgxIDI2MS40MTQwNjMgNDYyLjkxNDA2MyBMIDI2MS40MjU3ODEgNDYyLjM1NTQ2OSBMIDI2MS4yMTg3NSA0NjIuMzUxNTYzIEMgMjYwLjYwNTQ2OSA0NjIuMzQzNzUgMjU5LjgyODEyNSA0NjIuMjM4MjgxIDI1OS44MzU5MzggNDYxLjY3OTY4OCBDIDI1OS44Mzk4NDQgNDYxLjM0Mzc1IDI2MC4wNzAzMTMgNDYwLjg2MzI4MSAyNjAuMjY5NTMxIDQ2MC4yMzQzNzUgTCAyNjAuODk0NTMxIDQ1OC4zMTI1IEwgMjY1LjExMzI4MSA0NTguMzc4OTA2IEwgMjY1LjgwNDY4OCA0NjAuNTQ2ODc1IEMgMjY2IDQ2MS4xNDQ1MzEgMjY2LjE2MDE1NiA0NjEuNjUyMzQ0IDI2Ni4xNTYyNSA0NjEuODkwNjI1IEMgMjY2LjE0ODQzOCA0NjIuMzU1NDY5IDI2NS40MjE4NzUgNDYyLjQxNzk2OSAyNjQuOTkyMTg4IDQ2Mi40MTQwNjMgTCAyNjQuNzg5MDYzIDQ2Mi40MTAxNTYgTCAyNjQuNzgxMjUgNDYyLjk2ODc1IEMgMjY1LjczMDQ2OSA0NjIuOTQ1MzEzIDI2Ni42NjAxNTYgNDYyLjkyMTg3NSAyNjcuNTcwMzEzIDQ2Mi45Mzc1IEMgMjY4LjQ2NDg0NCA0NjIuOTUzMTI1IDI2OS4zMDA3ODEgNDYzLjAwMzkwNiAyNzAuMTM2NzE5IDQ2My4wNTQ2ODggTCAyNzAuMTQ0NTMxIDQ2Mi40OTYwOTQgTCAyNzAuMDM1MTU2IDQ2Mi40OTIxODggQyAyNjkuNDIxODc1IDQ2Mi40ODQzNzUgMjY5LjAzMTI1IDQ2Mi4yNTM5MDYgMjY4LjgxNjQwNiA0NjEuNzMwNDY5ICIvPgo8L2c+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoMTMuNjk5MzQxJSwxMi4xOTk0MDIlLDEyLjUlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMjg2LjcyNjU2MyA0NjEuNDQ5MjE5IEMgMjg2LjA1NDY4OCA0NjEuNDkyMTg4IDI4NS4zNDM3NSA0NjEuNDQ1MzEzIDI4NS4yODEyNSA0NjAuNDgwNDY5IEwgMjg0LjY1NjI1IDQ1MC43NTM5MDYgQyAyODQuNTkzNzUgNDQ5Ljc4OTA2MyAyODUuMjkyOTY5IDQ0OS42NTIzNDQgMjg1Ljk2MDkzOCA0NDkuNjA5Mzc1IEwgMjg2LjIxODc1IDQ0OS41ODk4NDQgTCAyODYuMTgzNTk0IDQ0OS4wMzUxNTYgQyAyODUuNDQxNDA2IDQ0OS4wODIwMzEgMjg0LjMzMjAzMSA0NDkuMjMwNDY5IDI4My4zODY3MTkgNDQ5LjI4OTA2MyBDIDI4Mi4zODI4MTMgNDQ5LjM1NTQ2OSAyODEuMTkxNDA2IDQ0OS4zNTU0NjkgMjgwLjM3NSA0NDkuNDEwMTU2IEwgMjgwLjQxMDE1NiA0NDkuOTY0ODQ0IEwgMjgwLjc2MTcxOSA0NDkuOTQxNDA2IEMgMjgxLjQyOTY4OCA0NDkuODk4NDM4IDI4Mi4yMTQ4NDQgNDQ5LjkwNjI1IDI4Mi4yNzczNDQgNDUwLjkwNjI1IEwgMjgyLjU0Mjk2OSA0NTQuOTcyNjU2IEwgMjc1LjgwNDY4OCA0NTUuNDA2MjUgTCAyNzUuNTQyOTY5IDQ1MS4zNDM3NSBDIDI3NS40NzY1NjMgNDUwLjMzOTg0NCAyNzYuMjUzOTA2IDQ1MC4yMzQzNzUgMjc2LjkyMTg3NSA0NTAuMTkxNDA2IEwgMjc3LjI3MzQzOCA0NTAuMTY3OTY5IEwgMjc3LjIzODI4MSA0NDkuNjEzMjgxIEMgMjc2LjQyMTg3NSA0NDkuNjY0MDYzIDI3NS4yMzgyODEgNDQ5LjgxNjQwNiAyNzQuMjM0Mzc1IDQ0OS44Nzg5MDYgQyAyNzMuMjg5MDYzIDQ0OS45NDE0MDYgMjcyLjE3MTg3NSA0NDkuOTQxNDA2IDI3MS40Mjk2ODggNDQ5Ljk4ODI4MSBMIDI3MS40NjQ4NDQgNDUwLjU0Mjk2OSBMIDI3MS43MjY1NjMgNDUwLjUyNzM0NCBDIDI3Mi4zOTQ1MzEgNDUwLjQ4NDM3NSAyNzMuMTA1NDY5IDQ1MC41MzEyNSAyNzMuMTY3OTY5IDQ1MS40OTYwOTQgTCAyNzMuNzk2ODc1IDQ2MS4yMjI2NTYgQyAyNzMuODU1NDY5IDQ2Mi4xODc1IDI3My4xNTYyNSA0NjIuMzI0MjE5IDI3Mi40ODgyODEgNDYyLjM2NzE4OCBMIDI3Mi4yMzA0NjkgNDYyLjM4NjcxOSBMIDI3Mi4yNjU2MjUgNDYyLjk0MTQwNiBDIDI3My4wMDc4MTMgNDYyLjg5NDUzMSAyNzQuMTE3MTg4IDQ2Mi43NDYwOTQgMjc1LjA2MjUgNDYyLjY4NzUgQyAyNzYuMDY2NDA2IDQ2Mi42MjEwOTQgMjc3LjI1NzgxMyA0NjIuNjE3MTg4IDI3OC4wNzQyMTkgNDYyLjU2NjQwNiBMIDI3OC4wMzkwNjMgNDYyLjAxMTcxOSBMIDI3Ny42ODc1IDQ2Mi4wMzEyNSBDIDI3Ny4wMTk1MzEgNDYyLjA3NDIxOSAyNzYuMjM0Mzc1IDQ2Mi4wNzAzMTMgMjc2LjE3MTg3NSA0NjEuMDY2NDA2IEwgMjc1Ljg3MTA5NCA0NTYuNDQ1MzEzIEwgMjgyLjYwOTM3NSA0NTYuMDExNzE5IEwgMjgyLjkwNjI1IDQ2MC42MzI4MTMgQyAyODIuOTcyNjU2IDQ2MS42MzY3MTkgMjgyLjE5NTMxMyA0NjEuNzQyMTg4IDI4MS41MjczNDQgNDYxLjc4NTE1NiBMIDI4MS4xNzU3ODEgNDYxLjgwODU5NCBMIDI4MS4yMTA5MzggNDYyLjM2MzI4MSBDIDI4Mi4wMjczNDQgNDYyLjMxMjUgMjgzLjIxMDkzOCA0NjIuMTYwMTU2IDI4NC4yMTQ4NDQgNDYyLjA5Mzc1IEMgMjg1LjE2MDE1NiA0NjIuMDM1MTU2IDI4Ni4yNzczNDQgNDYyLjAzNTE1NiAyODcuMDE5NTMxIDQ2MS45ODgyODEgTCAyODYuOTg0Mzc1IDQ2MS40MzM1OTQgTCAyODYuNzI2NTYzIDQ2MS40NDkyMTkgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoMTMuNjk5MzQxJSwxMi4xOTk0MDIlLDEyLjUlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMjkyLjIwMzEyNSA0NTUuNjUyMzQ0IEwgMjkzLjIyMjY1NiA0NTAuMjAzMTI1IEwgMjkzLjI2MTcxOSA0NTAuMTk5MjE5IEwgMjk1LjY1MjM0NCA0NTUuMTkxNDA2IFogTSAzMDEuNjQ4NDM4IDQ1OS41MTU2MjUgQyAzMDEuMDQyOTY5IDQ1OS41OTc2NTYgMzAwLjYyNSA0NTkuNDI5Njg4IDMwMC4zMzU5MzggNDU4Ljk0MTQwNiBDIDMwMC4wMjM0MzggNDU4LjQxNzk2OSAyOTkuNzEwOTM4IDQ1Ny43NjU2MjUgMjk5LjQwMjM0NCA0NTcuMTUyMzQ0IEwgMjk0LjcyNjU2MyA0NDcuOTYwOTM4IEMgMjk0LjY1MjM0NCA0NDcuODIwMzEzIDI5NC41NzQyMTkgNDQ3LjY2MDE1NiAyOTQuNSA0NDcuNTE5NTMxIEMgMjk0LjQ1MzEyNSA0NDcuNDY4NzUgMjk0LjQxNzk2OSA0NDcuNDc2NTYzIDI5NC4zNjMyODEgNDQ3LjQ4NDM3NSBDIDI5NC4zMDg1OTQgNDQ3LjQ4ODI4MSAyOTQuMjczNDM4IDQ0Ny41MTE3MTkgMjk0LjIxODc1IDQ0Ny41MzkwNjMgQyAyOTMuODk4NDM4IDQ0Ny44MDg1OTQgMjkzLjIxMDkzOCA0NDguMjczNDM4IDI5Mi42NDg0MzggNDQ4LjU1NDY4OCBDIDI5Mi42Mjg5MDYgNDQ5LjI1IDI5Mi40MTc5NjkgNDUwLjIxODc1IDI5Mi4yNjk1MzEgNDUwLjkzMzU5NCBMIDI5MC40NDUzMTMgNDU5Ljc4OTA2MyBDIDI5MC4yNzM0MzggNDYwLjYwMTU2MyAyODkuNzIyNjU2IDQ2MS4xMDU0NjkgMjg5LjAwMzkwNiA0NjEuMTk5MjE5IEwgMjg4Ljg5MDYyNSA0NjEuMjE0ODQ0IEwgMjg4Ljk2NDg0NCA0NjEuNzY5NTMxIEMgMjg5LjYyMTA5NCA0NjEuNjQ0NTMxIDI5MC4yODEyNSA0NjEuNTE5NTMxIDI5MC45NDUzMTMgNDYxLjQyOTY4OCBDIDI5MS42ODM1OTQgNDYxLjMzMjAzMSAyOTIuNDQ1MzEzIDQ2MS4yNjk1MzEgMjkzLjE4NzUgNDYxLjIwNzAzMSBMIDI5My4xMTMyODEgNDYwLjY1MjM0NCBMIDI5Mi45MTAxNTYgNDYwLjY3OTY4OCBDIDI5Mi4zMDA3ODEgNDYwLjc2MTcxOSAyOTEuNTE1NjI1IDQ2MC43NzM0MzggMjkxLjQ0MTQwNiA0NjAuMjE4NzUgQyAyOTEuMzk4NDM4IDQ1OS44ODY3MTkgMjkxLjU1NDY4OCA0NTkuMzc4OTA2IDI5MS42NTYyNSA0NTguNzI2NTYzIEwgMjkxLjk5MjE4OCA0NTYuNzMwNDY5IEwgMjk2LjE3NTc4MSA0NTYuMTcxODc1IEwgMjk3LjE3OTY4OCA0NTguMjE4NzUgQyAyOTcuNDYwOTM4IDQ1OC43ODEyNSAyOTcuNjkxNDA2IDQ1OS4yNTM5MDYgMjk3LjcyNjU2MyA0NTkuNDk2MDk0IEMgMjk3Ljc4NTE1NiA0NTkuOTU3MDMxIDI5Ny4wNzgxMjUgNDYwLjEyNSAyOTYuNjUyMzQ0IDQ2MC4xODM1OTQgTCAyOTYuNDQ5MjE5IDQ2MC4yMDcwMzEgTCAyOTYuNTIzNDM4IDQ2MC43NjE3MTkgQyAyOTcuNDYwOTM4IDQ2MC42MDE1NjMgMjk4LjM3ODkwNiA0NjAuNDQxNDA2IDI5OS4yODEyNSA0NjAuMzIwMzEzIEMgMzAwLjE2NDA2MyA0NjAuMjAzMTI1IDMwMSA0NjAuMTI4OTA2IDMwMS44MzU5MzggNDYwLjA1NDY4OCBMIDMwMS43NjE3MTkgNDU5LjUgTCAzMDEuNjQ4NDM4IDQ1OS41MTU2MjUgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoMTMuNjk5MzQxJSwxMi4xOTk0MDIlLDEyLjUlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMzE0LjQ2MDkzOCA0NDcuMzI0MjE5IEMgMzE0LjAxOTUzMSA0NDUuMTU2MjUgMzE0Ljg0NzY1NiA0NDQuODM1OTM4IDMxNS42MTMyODEgNDQ0LjY3OTY4OCBMIDMxNS44ODY3MTkgNDQ0LjYyNSBMIDMxNS43NzM0MzggNDQ0LjA3ODEyNSBDIDMxNS4wMjczNDQgNDQ0LjIzMDQ2OSAzMTQuMjkyOTY5IDQ0NC40NTMxMjUgMzEzLjU0Njg3NSA0NDQuNjA1NDY5IEMgMzEyLjY5MTQwNiA0NDQuNzgxMjUgMzExLjgzNTkzOCA0NDQuODc1IDMxMC45ODA0NjkgNDQ1LjA1MDc4MSBMIDMxMS4wOTM3NSA0NDUuNTk3NjU2IEwgMzExLjQ5MjE4OCA0NDUuNTE1NjI1IEMgMzEyLjAzOTA2MyA0NDUuNDA2MjUgMzEzLjEyMTA5NCA0NDUuNDE0MDYzIDMxMy40MjU3ODEgNDQ2LjkwNjI1IEwgMzE0LjgxNjQwNiA0NTMuNzQyMTg4IEwgMzE0Ljc4NTE1NiA0NTMuNzg1MTU2IEwgMzA0LjgyMDMxMyA0NDYuMzA0Njg4IEMgMzA0LjI3MzQzOCA0NDYuNDE0MDYzIDMwMy43NjE3MTkgNDQ2LjU5Mzc1IDMwMy4yMTQ4NDQgNDQ2LjcwNzAzMSBDIDMwMi41MTk1MzEgNDQ2Ljg0NzY1NiAzMDEuNzk2ODc1IDQ0Ni45MTc5NjkgMzAxLjEwMTU2MyA0NDcuMDU4NTk0IEwgMzAxLjIxNDg0NCA0NDcuNjA1NDY5IEwgMzAxLjQ0OTIxOSA0NDcuNTU4NTk0IEMgMzAyLjI2OTUzMSA0NDcuMzkwNjI1IDMwMy4yMzQzNzUgNDQ3LjgzOTg0NCAzMDMuNDQxNDA2IDQ0OC44NTkzNzUgTCAzMDUgNDU2LjUzNTE1NiBDIDMwNS4yOTY4NzUgNDU3Ljk5MjE4OCAzMDUuMDg5ODQ0IDQ1OC45MjU3ODEgMzAzLjgzMjAzMSA0NTkuMTgzNTk0IEwgMzAzLjU3NDIxOSA0NTkuMjM0Mzc1IEwgMzAzLjY4NzUgNDU5Ljc4MTI1IEMgMzA0LjUwNzgxMyA0NTkuNjEzMjgxIDMwNS4zMzIwMzEgNDU5LjM3MTA5NCAzMDYuMTUyMzQ0IDQ1OS4yMDMxMjUgQyAzMDYuOTMzNTk0IDQ1OS4wNDI5NjkgMzA3LjczNDM3NSA0NTguOTU3MDMxIDMwOC41MTU2MjUgNDU4Ljc5Njg3NSBMIDMwOC40MDYyNSA0NTguMjUgTCAzMDguMDk3NjU2IDQ1OC4zMTY0MDYgQyAzMDYuNjkxNDA2IDQ1OC42MDE1NjMgMzA2LjI3MzQzOCA0NTguMTE3MTg4IDMwNS45NDkyMTkgNDU2LjUzMTI1IEwgMzA0LjQyNTc4MSA0NDkuMDIzNDM4IEwgMzE1LjkzNzUgNDU3LjU3NDIxOSBMIDMxNi42Mjg5MDYgNDU3LjQzNzUgQyAzMTYuNDIxODc1IDQ1Ni44OTA2MjUgMzE2LjI3MzQzOCA0NTYuMjUzOTA2IDMxNi4xNDQ1MzEgNDU1LjYxNzE4OCBMIDMxNC40NjA5MzggNDQ3LjMyNDIxOSAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMy42OTkzNDElLDEyLjE5OTQwMiUsMTIuNSUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAzMzUuNjIxMDk0IDQ0MS4zMzk4NDQgQyAzMzQuOTY4NzUgNDM5LjIyNjU2MyAzMzUuNzYxNzE5IDQzOC44MjQyMTkgMzM2LjUwNzgxMyA0MzguNTk3NjU2IEwgMzM2Ljc3MzQzOCA0MzguNTExNzE5IEwgMzM2LjYwNTQ2OSA0MzcuOTgwNDY5IEMgMzM1Ljg3ODkwNiA0MzguMjA3MDMxIDMzNS4xNzE4NzUgNDM4LjUwMzkwNiAzMzQuNDQ1MzEzIDQzOC43MjY1NjMgQyAzMzMuNjA5Mzc1IDQzOC45ODQzNzUgMzMyLjc2OTUzMSA0MzkuMTY3OTY5IDMzMS45MzM1OTQgNDM5LjQyNTc4MSBMIDMzMi4xMDE1NjMgNDM5Ljk1NzAzMSBMIDMzMi40OTIxODggNDM5LjgzNTkzOCBDIDMzMy4wMjM0MzggNDM5LjY3MTg3NSAzMzQuMTAxNTYzIDQzOS41NzQyMTkgMzM0LjU1NDY4OCA0NDEuMDMxMjUgTCAzMzYuNjEzMjgxIDQ0Ny42OTE0MDYgTCAzMzYuNTg5ODQ0IDQ0Ny43MzgyODEgTCAzMjUuOTI5Njg4IDQ0MS4yODUxNTYgQyAzMjUuMzk4NDM4IDQ0MS40NDkyMTkgMzI0LjkwNjI1IDQ0MS42Nzk2ODggMzI0LjM3MTA5NCA0NDEuODQ3NjU2IEMgMzIzLjY5NTMxMyA0NDIuMDU0Njg4IDMyMi45ODA0NjkgNDQyLjE5OTIxOSAzMjIuMzA4NTk0IDQ0Mi40MDYyNSBMIDMyMi40NzI2NTYgNDQyLjkzNzUgTCAzMjIuNzAzMTI1IDQ0Mi44NjcxODggQyAzMjMuNTAzOTA2IDQ0Mi42MjEwOTQgMzI0LjUwNzgxMyA0NDIuOTcyNjU2IDMyNC44MTI1IDQ0My45NjQ4NDQgTCAzMjcuMTI4OTA2IDQ1MS40NDUzMTMgQyAzMjcuNTcwMzEzIDQ1Mi44NjcxODggMzI3LjQ1MzEyNSA0NTMuODE2NDA2IDMyNi4yMjY1NjMgNDU0LjE5NTMxMyBMIDMyNS45ODA0NjkgNDU0LjI3MzQzOCBMIDMyNi4xNDQ1MzEgNDU0LjgwNDY4OCBDIDMyNi45NDUzMTMgNDU0LjU1ODU5NCAzMjcuNzM4MjgxIDQ1NC4yMzQzNzUgMzI4LjUzOTA2MyA0NTMuOTg4MjgxIEMgMzI5LjMwNDY4OCA0NTMuNzUgMzMwLjA4OTg0NCA0NTMuNTg1OTM4IDMzMC44NTE1NjMgNDUzLjM0NzY1NiBMIDMzMC42ODc1IDQ1Mi44MTY0MDYgTCAzMzAuMzg2NzE5IDQ1Mi45MTAxNTYgQyAzMjkuMDE1NjI1IDQ1My4zMzIwMzEgMzI4LjU1MDc4MSA0NTIuODk0NTMxIDMyOC4wNzAzMTMgNDUxLjM0NzY1NiBMIDMyNS44MDg1OTQgNDQ0LjAyNzM0NCBMIDMzOC4xMDkzNzUgNDUxLjM5NDUzMSBMIDMzOC43ODUxNTYgNDUxLjE4MzU5NCBDIDMzOC41MjczNDQgNDUwLjY2MDE1NiAzMzguMzE2NDA2IDQ1MC4wNDY4NzUgMzM4LjEyNSA0NDkuNDIxODc1IEwgMzM1LjYyMTA5NCA0NDEuMzM5ODQ0ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEzLjY5OTM0MSUsMTIuMTk5NDAyJSwxMi41JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDM0My4zODY3MTkgNDQzLjIyNjU2MyBMIDM0My4xMTMyODEgNDM3LjY5MTQwNiBMIDM0My4xNDg0MzggNDM3LjY3OTY4OCBMIDM0Ni42MzI4MTMgNDQxLjk4MDQ2OSBaIE0gMzUzLjQ2ODc1IDQ0NC43OTI5NjkgQyAzNTIuODk0NTMxIDQ0NS4wMTU2MjUgMzUyLjQ0OTIxOSA0NDQuOTQ1MzEzIDM1Mi4wNTQ2ODggNDQ0LjUzOTA2MyBDIDM1MS42Mjg5MDYgNDQ0LjEwNTQ2OSAzNTEuMTc1NzgxIDQ0My41NDI5NjkgMzUwLjczNDM3NSA0NDMuMDE1NjI1IEwgMzQ0LjA1NDY4OCA0MzUuMTYwMTU2IEMgMzQzLjk0OTIxOSA0MzUuMDQyOTY5IDM0My44Mzk4NDQgNDM0LjkwNjI1IDM0My43MzQzNzUgNDM0Ljc4NTE1NiBDIDM0My42Nzk2ODggNDM0Ljc1IDM0My42NDQ1MzEgNDM0Ljc2MTcxOSAzNDMuNTg5ODQ0IDQzNC43ODEyNSBDIDM0My41MzkwNjMgNDM0LjgwMDc4MSAzNDMuNTExNzE5IDQzNC44MzIwMzEgMzQzLjQ2NDg0NCA0MzQuODcxMDk0IEMgMzQzLjIxNDg0NCA0MzUuMjAzMTI1IDM0Mi42NTYyNSA0MzUuODIwMzEzIDM0Mi4xNzE4NzUgNDM2LjIyMjY1NiBDIDM0Mi4zMTY0MDYgNDM2LjkwNjI1IDM0Mi4zMzU5MzggNDM3Ljg5NDUzMSAzNDIuMzU1NDY5IDQzOC42MjEwOTQgTCAzNDIuNjM2NzE5IDQ0Ny42NTYyNSBDIDM0Mi42NTYyNSA0NDguNDg0Mzc1IDM0Mi4yMzQzNzUgNDQ5LjEwNTQ2OSAzNDEuNTU4NTk0IDQ0OS4zNjMyODEgTCAzNDEuNDUzMTI1IDQ0OS40MDIzNDQgTCAzNDEuNjU2MjUgNDQ5LjkyNTc4MSBDIDM0Mi4yNjU2MjUgNDQ5LjY0ODQzOCAzNDIuODc4OTA2IDQ0OS4zNzUgMzQzLjUwMzkwNiA0NDkuMTM2NzE5IEMgMzQ0LjE5NTMxMyA0NDguODY3MTg4IDM0NC45MjE4NzUgNDQ4LjYyODkwNiAzNDUuNjI4OTA2IDQ0OC4zOTg0MzggTCAzNDUuNDI5Njg4IDQ0Ny44Nzg5MDYgTCAzNDUuMjM4MjgxIDQ0Ny45NTMxMjUgQyAzNDQuNjY3OTY5IDQ0OC4xNzE4NzUgMzQzLjkwMjM0NCA0NDguMzYzMjgxIDM0My43MDMxMjUgNDQ3Ljg0Mzc1IEMgMzQzLjU4NTkzOCA0NDcuNTMxMjUgMzQzLjYxNzE4OCA0NDcgMzQzLjU2NjQwNiA0NDYuMzQzNzUgTCAzNDMuNDI5Njg4IDQ0NC4zMjQyMTkgTCAzNDcuMzcxMDk0IDQ0Mi44MTI1IEwgMzQ4LjgyMDMxMyA0NDQuNTY2NDA2IEMgMzQ5LjIyMjY1NiA0NDUuMDQ2ODc1IDM0OS41NTg1OTQgNDQ1LjQ1NzAzMSAzNDkuNjQ0NTMxIDQ0NS42ODM1OTQgQyAzNDkuODEyNSA0NDYuMTE3MTg4IDM0OS4xNjQwNjMgNDQ2LjQ0NTMxMyAzNDguNzYxNzE5IDQ0Ni41OTc2NTYgTCAzNDguNTc0MjE5IDQ0Ni42NzE4NzUgTCAzNDguNzczNDM4IDQ0Ny4xOTE0MDYgQyAzNDkuNjQ0NTMxIDQ0Ni44MjAzMTMgMzUwLjUgNDQ2LjQ0OTIxOSAzNTEuMzUxNTYzIDQ0Ni4xMjUgQyAzNTIuMTgzNTk0IDQ0NS44MDQ2ODggMzUyLjk3NjU2MyA0NDUuNTM5MDYzIDM1My43NzM0MzggNDQ1LjI3MzQzOCBMIDM1My41NzAzMTMgNDQ0Ljc1MzkwNiBMIDM1My40Njg3NSA0NDQuNzkyOTY5ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEzLjY5OTM0MSUsMTIuMTk5NDAyJSwxMi41JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDM1My42MDE1NjMgNDM0LjEwOTM3NSBDIDM1My4wMDM5MDYgNDMyLjc2OTUzMSAzNTMuMzkwNjI1IDQzMS42MzY3MTkgMzU0LjczNDM3NSA0MzEuMDM5MDYzIEMgMzU1LjkwNjI1IDQzMC41MTU2MjUgMzU3LjA4OTg0NCA0MzEuMjQ2MDk0IDM1Ny43MDMxMjUgNDMyLjI5Njg3NSBMIDM1OC4xNDA2MjUgNDMyIEMgMzU3LjY3MTg3NSA0MzEuMjMwNDY5IDM1Ny4yMzgyODEgNDMwLjQ0NTMxMyAzNTYuODgyODEzIDQyOS42NDg0MzggQyAzNTYuMzI0MjE5IDQyOS44MTY0MDYgMzU0LjgwMDc4MSA0MzAuMjczNDM4IDM1NC4zMjQyMTkgNDMwLjQ4ODI4MSBDIDM1Mi4xMzI4MTMgNDMxLjQ2ODc1IDM1MS4xNTYyNSA0MzMuNDcyNjU2IDM1Mi4xNDQ1MzEgNDM1LjY3OTY4OCBDIDM1My45NzY1NjMgNDM5Ljc3MzQzOCAzNTguNTUwNzgxIDQzNi42MDU0NjkgMzU5Ljg5NDUzMSA0MzkuNjA5Mzc1IEMgMzYwLjQzMzU5NCA0NDAuODE2NDA2IDM1OS44MjgxMjUgNDQxLjk2MDkzOCAzNTguNjcxODc1IDQ0Mi40ODA0NjkgQyAzNTcuMDU4NTk0IDQ0My4xOTkyMTkgMzU1LjY4MzU5NCA0NDIuMzA4NTk0IDM1NC44MzIwMzEgNDQwLjk1NzAzMSBMIDM1NC40MDIzNDQgNDQxLjI3MzQzOCBDIDM1NC44NzUgNDQyLjEwMTU2MyAzNTUuMzc1IDQ0Mi44OTQ1MzEgMzU1Ljg0NzY1NiA0NDMuNzIyNjU2IEMgMzU2Ljg2NzE4OCA0NDMuNzc3MzQ0IDM1Ny45Mzc1IDQ0My43MDMxMjUgMzU4Ljg4NjcxOSA0NDMuMjc3MzQ0IEMgMzYxLjA2MjUgNDQyLjMwODU5NCAzNjIuNDQ5MjE5IDQ0MC4yMTg3NSAzNjEuNDAyMzQ0IDQzNy44NzUgQyAzNTkuNTc4MTI1IDQzMy44MDA3ODEgMzU0Ljg2MzI4MSA0MzYuOTI5Njg4IDM1My42MDE1NjMgNDM0LjEwOTM3NSAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMy42OTkzNDElLDEyLjE5OTQwMiUsMTIuNSUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAzNjkuMzQzNzUgNDM3LjM5MDYyNSBDIDM2OC43NDYwOTQgNDM3LjY4NzUgMzY4LjA3MDMxMyA0MzcuOTE3OTY5IDM2Ny42NDA2MjUgNDM3LjA1MDc4MSBMIDM2My4zMjQyMTkgNDI4LjMxNjQwNiBDIDM2Mi44OTg0MzggNDI3LjQ0OTIxOSAzNjMuNDg4MjgxIDQyNy4wNTA3ODEgMzY0LjA4OTg0NCA0MjYuNzUzOTA2IEwgMzY0LjMyNDIxOSA0MjYuNjQwNjI1IEwgMzY0LjA3NDIxOSA0MjYuMTQwNjI1IEMgMzYzLjI5Mjk2OSA0MjYuNTI3MzQ0IDM2Mi4zMjQyMTkgNDI3LjA4OTg0NCAzNjEuNDkyMTg4IDQyNy41IEMgMzYwLjY3NTc4MSA0MjcuOTA2MjUgMzU5LjY0MDYyNSA0MjguMzMyMDMxIDM1OC45OTIxODggNDI4LjY1MjM0NCBMIDM1OS4yMzgyODEgNDI5LjE1MjM0NCBMIDM1OS40NzI2NTYgNDI5LjAzNTE1NiBDIDM2MC4wNzAzMTMgNDI4LjczODI4MSAzNjAuNzQ2MDk0IDQyOC41MTE3MTkgMzYxLjE3NTc4MSA0MjkuMzc4OTA2IEwgMzY1LjQ5MjE4OCA0MzguMTEzMjgxIEMgMzY1LjkxNzk2OSA0MzguOTgwNDY5IDM2NS4zMjgxMjUgNDM5LjM3NSAzNjQuNzI2NTYzIDQzOS42NzE4NzUgTCAzNjQuNDkyMTg4IDQzOS43ODkwNjMgTCAzNjQuNzQyMTg4IDQ0MC4yODkwNjMgQyAzNjUuMzkwNjI1IDQzOS45Njg3NSAzNjYuMzQzNzUgNDM5LjQxNDA2MyAzNjcuMTU2MjUgNDM5LjAxMTcxOSBDIDM2Ny45OTIxODggNDM4LjYwMTU2MyAzNjkuMDIzNDM4IDQzOC4xNzE4NzUgMzY5LjgyNDIxOSA0MzcuNzc3MzQ0IEwgMzY5LjU3ODEyNSA0MzcuMjc3MzQ0IEwgMzY5LjM0Mzc1IDQzNy4zOTA2MjUgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoMTMuNjk5MzQxJSwxMi4xOTk0MDIlLDEyLjUlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMzc3LjgwNDY4OCA0MzIuODc1IEMgMzc1LjE3OTY4OCA0MzQuMzQ3NjU2IDM3Mi4yOTI5NjkgNDMyLjMyMDMxMyAzNzAuNjY0MDYzIDQyOS40MTQwNjMgQyAzNjkuNDQ1MzEzIDQyNy4yNDIxODggMzY4Ljg3MTA5NCA0MjQuMjM4MjgxIDM3MS43MTA5MzggNDIyLjY0NDUzMSBDIDM3NC40MDIzNDQgNDIxLjEzNjcxOSAzNzcuMjkyOTY5IDQyMy4yODkwNjMgMzc4LjYyMTA5NCA0MjUuNjU2MjUgQyAzNzkuOTQ5MjE5IDQyOC4wMjczNDQgMzgwLjk1MzEyNSA0MzEuMTA5Mzc1IDM3Ny44MDQ2ODggNDMyLjg3NSBaIE0gMzcxLjM0Mzc1IDQyMS45MTQwNjMgQyAzNjcuOTY4NzUgNDIzLjgwNDY4OCAzNjYuODIwMzEzIDQyNy44ODI4MTMgMzY4LjcxMDkzOCA0MzEuMjU3ODEzIEMgMzcwLjY2NDA2MyA0MzQuNzQ2MDk0IDM3NC42MDU0NjkgNDM1LjYwOTM3NSAzNzguMDQyOTY5IDQzMy42Nzk2ODggQyAzODEuNSA0MzEuNzQyMTg4IDM4Mi43ODUxNTYgNDI3Ljc2MTcxOSAzODAuNjk1MzEzIDQyNC4wMjczNDQgQyAzNzguNzU3ODEzIDQyMC41NzAzMTMgMzc0Ljc5Njg3NSA0MTkuOTc2NTYzIDM3MS4zNDM3NSA0MjEuOTE0MDYzICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEzLjY5OTM0MSUsMTIuMTk5NDAyJSwxMi41JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDM5MS40NzY1NjMgNDEzLjE1NjI1IEMgMzkwLjI1NzgxMyA0MTEuMzEyNSAzOTAuOTA2MjUgNDEwLjcwMzEyNSAzOTEuNTU4NTk0IDQxMC4yNzM0MzggTCAzOTEuNzg5MDYzIDQxMC4xMjEwOTQgTCAzOTEuNDgwNDY5IDQwOS42NTYyNSBDIDM5MC44NDc2NTYgNDEwLjA3ODEyNSAzOTAuMjUgNDEwLjU1ODU5NCAzODkuNjEzMjgxIDQxMC45ODA0NjkgQyAzODguODg2NzE5IDQxMS40NjA5MzggMzg4LjEzMjgxMyA0MTEuODcxMDk0IDM4Ny40MDIzNDQgNDEyLjM1MTU2MyBMIDM4Ny43MTA5MzggNDEyLjgxNjQwNiBMIDM4OC4wNTA3ODEgNDEyLjU5Mzc1IEMgMzg4LjUxNTYyNSA0MTIuMjg1MTU2IDM4OS41MjM0MzggNDExLjg4NjcxOSAzOTAuMzYzMjgxIDQxMy4xNTYyNSBMIDM5NC4yMDcwMzEgNDE4Ljk3NjU2MyBMIDM5NC4xOTkyMTkgNDE5LjAyNzM0NCBMIDM4Mi4xNTYyNSA0MTUuODE2NDA2IEMgMzgxLjY5MTQwNiA0MTYuMTI1IDM4MS4yODEyNSA0MTYuNDg0Mzc1IDM4MC44MTY0MDYgNDE2Ljc5Mjk2OSBDIDM4MC4yMjY1NjMgNDE3LjE4MzU5NCAzNzkuNTgyMDMxIDQxNy41MTk1MzEgMzc4Ljk5MjE4OCA0MTcuOTEwMTU2IEwgMzc5LjMwMDc4MSA0MTguMzcxMDk0IEwgMzc5LjUwMzkwNiA0MTguMjM4MjgxIEMgMzgwLjE5OTIxOSA0MTcuNzc3MzQ0IDM4MS4yNjE3MTkgNDE3LjgzNTkzOCAzODEuODM1OTM4IDQxOC43MDMxMjUgTCAzODYuMTUyMzQ0IDQyNS4yMzQzNzUgQyAzODYuOTcyNjU2IDQyNi40NzY1NjMgMzg3LjEyODkwNiA0MjcuNDIxODc1IDM4Ni4wNTg1OTQgNDI4LjEyODkwNiBMIDM4NS44Mzk4NDQgNDI4LjI3MzQzOCBMIDM4Ni4xNDg0MzggNDI4LjczODI4MSBDIDM4Ni44NDc2NTYgNDI4LjI3NzM0NCAzODcuNTE5NTMxIDQyNy43NDIxODggMzg4LjIxODc1IDQyNy4yODEyNSBDIDM4OC44ODI4MTMgNDI2LjgzOTg0NCAzODkuNTkzNzUgNDI2LjQ2MDkzOCAzOTAuMjYxNzE5IDQyNi4wMTk1MzEgTCAzODkuOTUzMTI1IDQyNS41NTQ2ODggTCAzODkuNjg3NSA0MjUuNzMwNDY5IEMgMzg4LjQ5MjE4OCA0MjYuNTE5NTMxIDM4Ny45MjE4NzUgNDI2LjIyNjU2MyAzODcuMDMxMjUgNDI0Ljg3ODkwNiBMIDM4Mi44MDg1OTQgNDE4LjQ4NDM3NSBMIDM5Ni42ODM1OTQgNDIyLjExMzI4MSBMIDM5Ny4yNjk1MzEgNDIxLjcyMjY1NiBDIDM5Ni44NzUgNDIxLjI5Mjk2OSAzOTYuNSA0MjAuNzYxNzE5IDM5Ni4xNDQ1MzEgNDIwLjIxODc1IEwgMzkxLjQ3NjU2MyA0MTMuMTU2MjUgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoMTMuNjk5MzQxJSwxMi4xOTk0MDIlLDEyLjUlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMzk5LjQ2MDkzOCA0MTIuODAwNzgxIEwgMzk3LjY1NjI1IDQwNy41NjI1IEwgMzk3LjY4MzU5NCA0MDcuNTQyOTY5IEwgNDAyLjIzMDQ2OSA0MTAuNjk5MjE5IFogTSA0MDkuNTgyMDMxIDQxMS40OTIxODggQyA0MDkuMDkzNzUgNDExLjg2MzI4MSA0MDguNjQ0NTMxIDQxMS45MjE4NzUgNDA4LjE1MjM0NCA0MTEuNjQ0NTMxIEMgNDA3LjYyNSA0MTEuMzQ3NjU2IDQwNy4wMzEyNSA0MTAuOTMzNTk0IDQwNi40NjA5MzggNDEwLjU0Njg3NSBMIDM5Ny44NTE1NjMgNDA0Ljg3MTA5NCBDIDM5Ny43MTg3NSA0MDQuNzg1MTU2IDM5Ny41NzAzMTMgNDA0LjY4NzUgMzk3LjQzNzUgNDA0LjYwMTU2MyBDIDM5Ny4zNzUgNDA0LjU3ODEyNSAzOTcuMzQzNzUgNDA0LjYwMTU2MyAzOTcuMzAwNzgxIDQwNC42MzY3MTkgQyAzOTcuMjU3ODEzIDQwNC42Njc5NjkgMzk3LjIzODI4MSA0MDQuNzA3MDMxIDM5Ny4yMDMxMjUgNDA0Ljc1MzkwNiBDIDM5Ny4wNTg1OTQgNDA1LjE0ODQzOCAzOTYuNjkxNDA2IDQwNS44OTQ1MzEgMzk2LjMzOTg0NCA0MDYuNDE0MDYzIEMgMzk2LjY2Nzk2OSA0MDcuMDMxMjUgMzk2Ljk2MDkzOCA0MDcuOTcyNjU2IDM5Ny4xODc1IDQwOC42Njc5NjkgTCAzOTkuOTc2NTYzIDQxNy4yNjU2MjUgQyA0MDAuMjI2NTYzIDQxOC4wNTg1OTQgMzk5Ljk5NjA5NCA0MTguNzY5NTMxIDM5OS40MTc5NjkgNDE5LjIwNzAzMSBMIDM5OS4zMzIwMzEgNDE5LjI3MzQzOCBMIDM5OS42Njc5NjkgNDE5LjcxODc1IEMgNDAwLjE3OTY4OCA0MTkuMjg1MTU2IDQwMC42ODc1IDQxOC44NTE1NjMgNDAxLjIyMjY1NiA0MTguNDQ1MzEzIEMgNDAxLjgxNjQwNiA0MTcuOTk2MDk0IDQwMi40NDUzMTMgNDE3LjU2NjQwNiA0MDMuMDU4NTk0IDQxNy4xNDQ1MzEgTCA0MDIuNzIyNjU2IDQxNi42OTkyMTkgTCA0MDIuNTU4NTk0IDQxNi44MjQyMTkgQyA0MDIuMDcwMzEzIDQxNy4xOTUzMTMgNDAxLjM5MDYyNSA0MTcuNTkzNzUgNDAxLjA1NDY4OCA0MTcuMTQ4NDM4IEMgNDAwLjg1MTU2MyA0MTYuODgyODEzIDQwMC43MzgyODEgNDE2LjM2MzI4MSA0MDAuNTAzOTA2IDQxNS43NDYwOTQgTCAzOTkuODA4NTk0IDQxMy44NDc2NTYgTCA0MDMuMTcxODc1IDQxMS4yOTI5NjkgTCA0MDUuMDU0Njg4IDQxMi41NzQyMTkgQyA0MDUuNTc0MjE5IDQxMi45MjE4NzUgNDA2LjAxMTcxOSA0MTMuMjIyNjU2IDQwNi4xNjAxNTYgNDEzLjQxNDA2MyBDIDQwNi40NDE0MDYgNDEzLjc4NTE1NiA0MDUuOTA2MjUgNDE0LjI4MTI1IDQwNS41NjY0MDYgNDE0LjUzOTA2MyBMIDQwNS40MDIzNDQgNDE0LjY2NDA2MyBMIDQwNS43NDIxODggNDE1LjEwOTM3NSBDIDQwNi40NzI2NTYgNDE0LjUwMzkwNiA0MDcuMTkxNDA2IDQxMy45MTQwNjMgNDA3LjkxNzk2OSA0MTMuMzYzMjgxIEMgNDA4LjYyODkwNiA0MTIuODI0MjE5IDQwOS4zMTY0MDYgNDEyLjM0NzY1NiA0MTAuMDA3ODEzIDQxMS44NzEwOTQgTCA0MDkuNjcxODc1IDQxMS40MjU3ODEgTCA0MDkuNTgyMDMxIDQxMS40OTIxODggIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoMTMuNjk5MzQxJSwxMi4xOTk0MDIlLDEyLjUlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gNDE3LjAwNzgxMyA0MDEuNzUzOTA2IEMgNDE3LjE4NzUgNDAyLjEzNjcxOSA0MTcuMzk4NDM4IDQwMi42NDA2MjUgNDE3LjQzNzUgNDAzLjE0NDUzMSBDIDQxNy40ODQzNzUgNDAzLjcxODc1IDQxNy4yNjU2MjUgNDA0LjQ5MjE4OCA0MTYuNzM0Mzc1IDQwNS4wNzAzMTMgQyA0MTYuMTQ0NTMxIDQwNS42OTUzMTMgNDE1LjUwNzgxMyA0MDYuMjM4MjgxIDQxNC44OTA2MjUgNDA2LjY5NTMxMyBDIDQxNC4zOTA2MjUgNDA3LjAyMzQzOCA0MTMuODUxNTYzIDQwNy4xOTE0MDYgNDEzLjM2NzE4OCA0MDYuNjI4OTA2IEwgNDA3LjEyODkwNiAzOTkuMzM1OTM4IEMgNDA2LjQ4ODI4MSAzOTguNTg1OTM4IDQwNi45MDIzNDQgMzk4LjIxMDkzOCA0MDcuNDM3NSAzOTcuNzUgTCA0MDcuNzg5MDYzIDM5Ny40NDkyMTkgTCA0MDcuNDI5Njg4IDM5Ny4wMjM0MzggQyA0MDYuNzA3MDMxIDM5Ny42NDQ1MzEgNDA2LjA1MDc4MSAzOTguMzA0Njg4IDQwNS4zMjgxMjUgMzk4LjkxNzk2OSBDIDQwNC41NzgxMjUgMzk5LjU2MjUgNDAzLjc5Njg3NSA0MDAuMTMyODEzIDQwMy4wNDY4NzUgNDAwLjc3MzQzOCBMIDQwMy40MTAxNTYgNDAxLjE5NTMxMyBMIDQwMy42MDkzNzUgNDAxLjAyNzM0NCBDIDQwNC4xMTcxODggNDAwLjU4OTg0NCA0MDQuNzMwNDY5IDQwMC4xOTE0MDYgNDA1LjM1NTQ2OSA0MDAuOTI1NzgxIEwgNDExLjU3MDMxMyA0MDguMTg3NSBDIDQxMi4zMjAzMTMgNDA5LjA2NjQwNiA0MTEuODI4MTI1IDQwOS42MDkzNzUgNDExLjMyMDMxMyA0MTAuMDQyOTY5IEwgNDExLjEyMTA5NCA0MTAuMjEwOTM4IEwgNDExLjQ4NDM3NSA0MTAuNjM2NzE5IEMgNDEyLjczMDQ2OSA0MDkuNTcwMzEzIDQxMy45MjU3ODEgNDA4LjQ1MzEyNSA0MTUuMTY3OTY5IDQwNy4zODY3MTkgQyA0MTYuNDEwMTU2IDQwNi4zMjQyMTkgNDE3LjcwMzEyNSA0MDUuMzE2NDA2IDQxOC45NDUzMTMgNDA0LjI1MzkwNiBDIDQxOC40Mjk2ODggNDAzLjMwMDc4MSA0MTcuOTQ5MjE5IDQwMi4zNDM3NSA0MTcuNDE0MDYzIDQwMS40MDIzNDQgTCA0MTcuMDA3ODEzIDQwMS43NTM5MDYgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoOTkuMTk4OTE0JSw3Ni40OTk5MzklLDE3Ljk5OTI2OCUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAzMDIuMTg3NSA0MDguNzE0ODQ0IEMgMzAyLjM3NSA0MDguNjUyMzQ0IDMwMi41NTg1OTQgNDA4LjU5Mzc1IDMwMi43NDIxODggNDA4LjUzMTI1IEMgMzAyLjU1ODU5NCA0MDguNTkzNzUgMzAyLjM3NSA0MDguNjUyMzQ0IDMwMi4xODc1IDQwOC43MTQ4NDQgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoOTkuMTk4OTE0JSw3Ni40OTk5MzklLDE3Ljk5OTI2OCUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAzMDQuNjI1IDQwNy45MDYyNSBDIDMwNC43MTQ4NDQgNDA3Ljg3NSAzMDQuODA0Njg4IDQwNy44NDc2NTYgMzA0Ljg5NDUzMSA0MDcuODE2NDA2IEMgMzA0LjgwNDY4OCA0MDcuODQ3NjU2IDMwNC43MTQ4NDQgNDA3Ljg3NSAzMDQuNjI1IDQwNy45MDYyNSAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYig5OS4xOTg5MTQlLDc2LjQ5OTkzOSUsMTcuOTk5MjY4JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDMwMy40MDIzNDQgNDA4LjMxNjQwNiBDIDMwMy41NTg1OTQgNDA4LjI2NTYyNSAzMDMuNzE0ODQ0IDQwOC4yMTA5MzggMzAzLjg2NzE4OCA0MDguMTYwMTU2IEMgMzAzLjcxNDg0NCA0MDguMjEwOTM4IDMwMy41NTg1OTQgNDA4LjI2NTYyNSAzMDMuNDAyMzQ0IDQwOC4zMTY0MDYgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoOTkuMTk4OTE0JSw3Ni40OTk5MzklLDE3Ljk5OTI2OCUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAzMDAuOTQ1MzEzIDQwOS4xMDkzNzUgQyAzMDEuMTUyMzQ0IDQwOS4wNDY4NzUgMzAxLjM1MTU2MyA0MDguOTgwNDY5IDMwMS41NTQ2ODggNDA4LjkxNzk2OSBDIDMwMS4zNTE1NjMgNDA4Ljk4MDQ2OSAzMDEuMTUyMzQ0IDQwOS4wNDY4NzUgMzAwLjk0NTMxMyA0MDkuMTA5Mzc1ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDk5LjE5ODkxNCUsNzYuNDk5OTM5JSwxNy45OTkyNjglKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMzEzLjY4MzU5NCA0MDQuOTk2MDk0IEMgMzEzLjY1NjI1IDQwNS4wMDM5MDYgMzEzLjYzMjgxMyA0MDUuMDExNzE5IDMxMy42MDkzNzUgNDA1LjAxOTUzMSBDIDMxMy42Nzk2ODggNDA1IDMxMy43NTM5MDYgNDA0Ljk3NjU2MyAzMTMuODI4MTI1IDQwNC45NjA5MzggQyAzMTMuNzgxMjUgNDA0Ljk3MjY1NiAzMTMuNzMwNDY5IDQwNC45ODQzNzUgMzEzLjY4MzU5NCA0MDQuOTk2MDk0ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDk5LjE5ODkxNCUsNzYuNDk5OTM5JSwxNy45OTkyNjglKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMjk5LjY2Nzk2OSA0MDkuNTAzOTA2IEMgMjk5Ljg4NjcxOSA0MDkuNDQxNDA2IDMwMC4wOTc2NTYgNDA5LjM3NSAzMDAuMzEyNSA0MDkuMzA4NTk0IEMgMzAwLjA5NzY1NiA0MDkuMzc1IDI5OS44ODY3MTkgNDA5LjQ0MTQwNiAyOTkuNjY3OTY5IDQwOS41MDM5MDYgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoOTkuMTk4OTE0JSw3Ni40OTk5MzklLDE3Ljk5OTI2OCUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAyOTYuNTE5NTMxIDQxMC40MTQwNjMgQyAyOTYuOTAyMzQ0IDQxMC4zMTI1IDI5Ny4yNzM0MzggNDEwLjIwNzAzMSAyOTcuNjQwNjI1IDQxMC4xMDE1NjMgQyAyOTcuMjczNDM4IDQxMC4yMDcwMzEgMjk2LjkwMjM0NCA0MTAuMzEyNSAyOTYuNTE5NTMxIDQxMC40MTQwNjMgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoOTkuMTk4OTE0JSw3Ni40OTk5MzklLDE3Ljk5OTI2OCUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAyOTguMzQ3NjU2IDQwOS44OTg0MzggQyAyOTguNTc0MjE5IDQwOS44MzIwMzEgMjk4Ljc5Njg3NSA0MDkuNzY1NjI1IDI5OS4wMTk1MzEgNDA5LjY5OTIxOSBDIDI5OC43OTY4NzUgNDA5Ljc2NTYyNSAyOTguNTc0MjE5IDQwOS44MzIwMzEgMjk4LjM0NzY1NiA0MDkuODk4NDM4ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDk5LjE5ODkxNCUsNzYuNDk5OTM5JSwxNy45OTkyNjglKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMzY3LjQ2NDg0NCAzOTQuNDYwOTM4IEMgMzY3LjYxNzE4OCAzOTQuNDc2NTYzIDM2Ny43NzM0MzggMzk0LjQ5MjE4OCAzNjcuOTI5Njg4IDM5NC41MTE3MTkgQyAzNjcuNzczNDM4IDM5NC40OTIxODggMzY3LjYxNzE4OCAzOTQuNDc2NTYzIDM2Ny40NjQ4NDQgMzk0LjQ2MDkzOCAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYig5OS4xOTg5MTQlLDc2LjQ5OTkzOSUsMTcuOTk5MjY4JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDM3MC4zMjAzMTMgMzk0Ljc5Mjk2OSBDIDM3MC40ODgyODEgMzk0LjgxNjQwNiAzNzAuNjYwMTU2IDM5NC44MzU5MzggMzcwLjgyODEyNSAzOTQuODU5Mzc1IEMgMzcwLjY2MDE1NiAzOTQuODM1OTM4IDM3MC40ODgyODEgMzk0LjgxNjQwNiAzNzAuMzIwMzEzIDM5NC43OTI5NjkgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoOTkuMTk4OTE0JSw3Ni40OTk5MzklLDE3Ljk5OTI2OCUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAyOTQuOTQxNDA2IDQxMC44MzU5MzggQyAyOTUuMTYwMTU2IDQxMC43NzczNDQgMjk1LjM4MjgxMyA0MTAuNzIyNjU2IDI5NS41OTc2NTYgNDEwLjY2Nzk2OSBDIDI5NS4zODI4MTMgNDEwLjcyMjY1NiAyOTUuMTYwMTU2IDQxMC43NzczNDQgMjk0Ljk0MTQwNiA0MTAuODM1OTM4ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDk5LjE5ODkxNCUsNzYuNDk5OTM5JSwxNy45OTkyNjglKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMzYyLjI4NTE1NiAzOTQuMDU0Njg4IEMgMzYyLjM3ODkwNiAzOTQuMDU4NTk0IDM2Mi40NzI2NTYgMzk0LjA2NjQwNiAzNjIuNTY2NDA2IDM5NC4wNzAzMTMgQyAzNjIuNDcyNjU2IDM5NC4wNjY0MDYgMzYyLjM3ODkwNiAzOTQuMDU4NTk0IDM2Mi4yODUxNTYgMzk0LjA1NDY4OCAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYig5OS4xOTg5MTQlLDc2LjQ5OTkzOSUsMTcuOTk5MjY4JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDM3My4zMjgxMjUgMzk1LjIyMjY1NiBDIDM3My40NjQ4NDQgMzk1LjI0MjE4OCAzNzMuNjAxNTYzIDM5NS4yNjU2MjUgMzczLjczODI4MSAzOTUuMjg1MTU2IEMgMzczLjYwMTU2MyAzOTUuMjY1NjI1IDM3My40NjQ4NDQgMzk1LjI0MjE4OCAzNzMuMzI4MTI1IDM5NS4yMjI2NTYgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoOTkuMTk4OTE0JSw3Ni40OTk5MzklLDE3Ljk5OTI2OCUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAzNTQuNzk2ODc1IDM5My45NDkyMTkgQyAzNTQuODY3MTg4IDM5My45NDkyMTkgMzU0LjkzNzUgMzkzLjk0NTMxMyAzNTUuMDA3ODEzIDM5My45NDUzMTMgQyAzNTQuOTM3NSAzOTMuOTQ1MzEzIDM1NC44NjcxODggMzkzLjk0OTIxOSAzNTQuNzk2ODc1IDM5My45NDkyMTkgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoOTkuMTk4OTE0JSw3Ni40OTk5MzklLDE3Ljk5OTI2OCUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAzNTkuNjQwNjI1IDM5My45NDkyMTkgQyAzNTkuNzczNDM4IDM5My45NTMxMjUgMzU5LjkwNjI1IDM5My45NTcwMzEgMzYwLjAzOTA2MyAzOTMuOTYwOTM4IEMgMzU5LjkwNjI1IDM5My45NTcwMzEgMzU5Ljc3MzQzOCAzOTMuOTUzMTI1IDM1OS42NDA2MjUgMzkzLjk0OTIxOSAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYig5OS4xOTg5MTQlLDc2LjQ5OTkzOSUsMTcuOTk5MjY4JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDMxMy44MjgxMjUgNDA0Ljk2MDkzOCBDIDMxNC4xNzk2ODggNDA0Ljg3MTA5NCAzMTQuNTM5MDYzIDQwNC43NjU2MjUgMzE0LjkxMDE1NiA0MDQuNjQ4NDM4IEMgMzE0LjU0Mjk2OSA0MDQuNzY1NjI1IDMxNC4xNzk2ODggNDA0Ljg3MTA5NCAzMTMuODI4MTI1IDQwNC45NjA5MzggIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoOTkuMTk4OTE0JSw3Ni40OTk5MzklLDE3Ljk5OTI2OCUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAzNjQuODMyMDMxIDM5NC4yMjI2NTYgQyAzNjQuOTE0MDYzIDM5NC4yMjY1NjMgMzY0Ljk5NjA5NCAzOTQuMjM0Mzc1IDM2NS4wNzgxMjUgMzk0LjIzODI4MSBDIDM2NC45OTYwOTQgMzk0LjIzNDM3NSAzNjQuOTE0MDYzIDM5NC4yMjY1NjMgMzY0LjgzMjAzMSAzOTQuMjIyNjU2ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDk5LjE5ODkxNCUsNzYuNDk5OTM5JSwxNy45OTkyNjglKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMjcyLjczMDQ2OSA0MTQuMjM4MjgxIEMgMjczLjA1NDY4OCA0MTQuMjE4NzUgMjczLjM3NSA0MTQuMTk1MzEzIDI3My42OTUzMTMgNDE0LjE3NTc4MSBDIDI3My4zNzUgNDE0LjE5NTMxMyAyNzMuMDU0Njg4IDQxNC4yMTg3NSAyNzIuNzMwNDY5IDQxNC4yMzgyODEgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoOTkuMTk4OTE0JSw3Ni40OTk5MzklLDE3Ljk5OTI2OCUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAyNzQuOTc2NTYzIDQxNC4wODU5MzggQyAyNzUuMjkyOTY5IDQxNC4wNjI1IDI3NS42MDU0NjkgNDE0LjAzNTE1NiAyNzUuOTIxODc1IDQxNC4wMDc4MTMgQyAyNzUuNjA1NDY5IDQxNC4wMzUxNTYgMjc1LjI5Mjk2OSA0MTQuMDYyNSAyNzQuOTc2NTYzIDQxNC4wODU5MzggIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoOTkuMTk4OTE0JSw3Ni40OTk5MzklLDE3Ljk5OTI2OCUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAyNzcuMTM2NzE5IDQxMy45MDIzNDQgQyAyNzcuNDQ5MjE5IDQxMy44NzEwOTQgMjc3Ljc1NzgxMyA0MTMuODM5ODQ0IDI3OC4wNjY0MDYgNDEzLjgwODU5NCBDIDI3Ny43NTc4MTMgNDEzLjgzOTg0NCAyNzcuNDQ5MjE5IDQxMy44NzEwOTQgMjc3LjEzNjcxOSA0MTMuOTAyMzQ0ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDk5LjE5ODkxNCUsNzYuNDk5OTM5JSwxNy45OTkyNjglKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMjkzLjQyOTY4OCA0MTEuMjE0ODQ0IEMgMjkzLjY2MDE1NiA0MTEuMTU2MjUgMjkzLjg5NDUzMSA0MTEuMTAxNTYzIDI5NC4xMjUgNDExLjA0Mjk2OSBDIDI5My44OTQ1MzEgNDExLjEwMTU2MyAyOTMuNjYwMTU2IDQxMS4xNTYyNSAyOTMuNDI5Njg4IDQxMS4yMTQ4NDQgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoOTkuMTk4OTE0JSw3Ni40OTk5MzklLDE3Ljk5OTI2OCUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAyNjUuNTA3ODEzIDQxNC40OTYwOTQgQyAyNjUuNzgxMjUgNDE0LjQ5NjA5NCAyNjYuMDQyOTY5IDQxNC40ODgyODEgMjY2LjMxMjUgNDE0LjQ4MDQ2OSBDIDI2Ni4wNDI5NjkgNDE0LjQ4ODI4MSAyNjUuNzgxMjUgNDE0LjQ5NjA5NCAyNjUuNTA3ODEzIDQxNC40OTYwOTQgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoOTkuMTk4OTE0JSw3Ni40OTk5MzklLDE3Ljk5OTI2OCUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAyNzkuMjIyNjU2IDQxMy42ODc1IEMgMjc5LjUyNzM0NCA0MTMuNjU2MjUgMjc5LjgzMjAzMSA0MTMuNjIxMDk0IDI4MC4xMzI4MTMgNDEzLjU4MjAzMSBDIDI3OS44MzIwMzEgNDEzLjYyMTA5NCAyNzkuNTI3MzQ0IDQxMy42NTYyNSAyNzkuMjIyNjU2IDQxMy42ODc1ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDk5LjE5ODkxNCUsNzYuNDk5OTM5JSwxNy45OTkyNjglKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMjY4LjAwMzkwNiA0MTQuNDQ1MzEzIEMgMjY4LjMxMjUgNDE0LjQzNzUgMjY4LjYxNzE4OCA0MTQuNDI1NzgxIDI2OC45MjU3ODEgNDE0LjQxNDA2MyBDIDI2OC42MTcxODggNDE0LjQyNTc4MSAyNjguMzEyNSA0MTQuNDM3NSAyNjguMDAzOTA2IDQxNC40NDUzMTMgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoOTkuMTk4OTE0JSw3Ni40OTk5MzklLDE3Ljk5OTI2OCUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAyNzAuNDEwMTU2IDQxNC4zNTkzNzUgQyAyNzAuNzM0Mzc1IDQxNC4zNDc2NTYgMjcxLjA1MDc4MSA0MTQuMzI4MTI1IDI3MS4zNjcxODggNDE0LjMxMjUgQyAyNzEuMDUwNzgxIDQxNC4zMjgxMjUgMjcwLjczNDM3NSA0MTQuMzQ3NjU2IDI3MC40MTAxNTYgNDE0LjM1OTM3NSAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYig5OS4xOTg5MTQlLDc2LjQ5OTkzOSUsMTcuOTk5MjY4JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDI4My4xNzE4NzUgNDEzLjE4NzUgQyAyODMuNDYwOTM4IDQxMy4xNDQ1MzEgMjgzLjc1IDQxMy4xMDE1NjMgMjg0LjAzNTE1NiA0MTMuMDU4NTk0IEMgMjgzLjc1IDQxMy4xMDE1NjMgMjgzLjQ2MDkzOCA0MTMuMTQ0NTMxIDI4My4xNzE4NzUgNDEzLjE4NzUgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoOTkuMTk4OTE0JSw3Ni40OTk5MzklLDE3Ljk5OTI2OCUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAyOTAuMjUzOTA2IDQxMS45MzM1OTQgQyAyOTAuNTA3ODEzIDQxMS44Nzg5MDYgMjkwLjc2MTcxOSA0MTEuODI4MTI1IDI5MS4wMTE3MTkgNDExLjc3MzQzOCBDIDI5MC43NjE3MTkgNDExLjgyODEyNSAyOTAuNTA3ODEzIDQxMS44Nzg5MDYgMjkwLjI1MzkwNiA0MTEuOTMzNTk0ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDk5LjE5ODkxNCUsNzYuNDk5OTM5JSwxNy45OTkyNjglKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMjg2Ljg0NzY1NiA0MTIuNTk3NjU2IEMgMjg3LjExNzE4OCA0MTIuNTQ2ODc1IDI4Ny4zODY3MTkgNDEyLjUgMjg3LjY1MjM0NCA0MTIuNDQ5MjE5IEMgMjg3LjM4NjcxOSA0MTIuNSAyODcuMTE3MTg4IDQxMi41NDY4NzUgMjg2Ljg0NzY1NiA0MTIuNTk3NjU2ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDk5LjE5ODkxNCUsNzYuNDk5OTM5JSwxNy45OTkyNjglKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMjg1LjA0Mjk2OSA0MTIuOTAyMzQ0IEMgMjg1LjMyMDMxMyA0MTIuODU1NDY5IDI4NS42MDE1NjMgNDEyLjgxMjUgMjg1Ljg3NSA0MTIuNzY1NjI1IEMgMjg1LjYwMTU2MyA0MTIuODEyNSAyODUuMzIwMzEzIDQxMi44NTU0NjkgMjg1LjA0Mjk2OSA0MTIuOTAyMzQ0ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDk5LjE5ODkxNCUsNzYuNDk5OTM5JSwxNy45OTkyNjglKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMjkxLjg2NzE4OCA0MTEuNTgyMDMxIEMgMjkyLjEwOTM3NSA0MTEuNTI3MzQ0IDI5Mi4zNTU0NjkgNDExLjQ3MjY1NiAyOTIuNTk3NjU2IDQxMS40MTQwNjMgQyAyOTIuMzU1NDY5IDQxMS40NzI2NTYgMjkyLjEwOTM3NSA0MTEuNTI3MzQ0IDI5MS44NjcxODggNDExLjU4MjAzMSAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYig5OS4xOTg5MTQlLDc2LjQ5OTkzOSUsMTcuOTk5MjY4JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDI4OC41ODIwMzEgNDEyLjI3MzQzOCBDIDI4OC44NDM3NSA0MTIuMjIyNjU2IDI4OS4xMDU0NjkgNDEyLjE3MTg3NSAyODkuMzYzMjgxIDQxMi4xMjEwOTQgQyAyODkuMTA1NDY5IDQxMi4xNzE4NzUgMjg4Ljg0Mzc1IDQxMi4yMjI2NTYgMjg4LjU4MjAzMSA0MTIuMjczNDM4ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDk5LjE5ODkxNCUsNzYuNDk5OTM5JSwxNy45OTkyNjglKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMjgxLjIzNDM3NSA0MTMuNDQ5MjE5IEMgMjgxLjUzMTI1IDQxMy40MTAxNTYgMjgxLjgyODEyNSA0MTMuMzcxMDk0IDI4Mi4xMjEwOTQgNDEzLjMzMjAzMSBDIDI4MS44MjgxMjUgNDEzLjM3MTA5NCAyODEuNTMxMjUgNDEzLjQxMDE1NiAyODEuMjM0Mzc1IDQxMy40NDkyMTkgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoOTkuMTk4OTE0JSw3Ni40OTk5MzklLDE3Ljk5OTI2OCUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAzMzYuNDY4NzUgMzk2LjU0Mjk2OSBDIDMzNi40NzY1NjMgMzk2LjU0Mjk2OSAzMzYuNDg0Mzc1IDM5Ni41MzkwNjMgMzM2LjQ5MjE4OCAzOTYuNTM5MDYzIEMgMzM2LjQ4NDM3NSAzOTYuNTM5MDYzIDMzNi40NzY1NjMgMzk2LjU0Mjk2OSAzMzYuNDY4NzUgMzk2LjU0Mjk2OSAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYig5OS4xOTg5MTQlLDc2LjQ5OTkzOSUsMTcuOTk5MjY4JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDMzOC41MzEyNSAzOTYuMDI3MzQ0IEMgMzM4LjUyMzQzOCAzOTYuMDMxMjUgMzM4LjUxNTYyNSAzOTYuMDMxMjUgMzM4LjUwNzgxMyAzOTYuMDMxMjUgQyAzMzguNDk2MDk0IDM5Ni4wMzUxNTYgMzM4LjQ4ODI4MSAzOTYuMDM5MDYzIDMzOC40NzY1NjMgMzk2LjAzOTA2MyBDIDMzOC40OTYwOTQgMzk2LjAzNTE1NiAzMzguNTExNzE5IDM5Ni4wMzEyNSAzMzguNTMxMjUgMzk2LjAyNzM0NCAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYig5OS4xOTg5MTQlLDc2LjQ5OTkzOSUsMTcuOTk5MjY4JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDM0Ni4wNzQyMTkgMzk0LjY0MDYyNSBDIDM0Ni4xMDkzNzUgMzk0LjYzNjcxOSAzNDYuMTQ0NTMxIDM5NC42Mjg5MDYgMzQ2LjE3OTY4OCAzOTQuNjI1IEMgMzQ2LjE0NDUzMSAzOTQuNjI4OTA2IDM0Ni4xMDkzNzUgMzk0LjYzNjcxOSAzNDYuMDc0MjE5IDM5NC42NDA2MjUgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoOTkuMTk4OTE0JSw3Ni40OTk5MzklLDE3Ljk5OTI2OCUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAzNDguMTI1IDM5NC4zOTQ1MzEgQyAzNDguMTkxNDA2IDM5NC4zODY3MTkgMzQ4LjI2MTcxOSAzOTQuMzc4OTA2IDM0OC4zMjgxMjUgMzk0LjM3MTA5NCBDIDM0OC4yNjE3MTkgMzk0LjM3ODkwNiAzNDguMTkxNDA2IDM5NC4zODY3MTkgMzQ4LjEyNSAzOTQuMzk0NTMxICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDk5LjE5ODkxNCUsNzYuNDk5OTM5JSwxNy45OTkyNjglKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMzQwLjI3NzM0NCAzOTUuNjM2NzE5IEMgMzQwLjMwMDc4MSAzOTUuNjI4OTA2IDM0MC4zMjgxMjUgMzk1LjYyNSAzNDAuMzU1NDY5IDM5NS42MjEwOTQgQyAzNDAuMzI4MTI1IDM5NS42MjUgMzQwLjMwMDc4MSAzOTUuNjMyODEzIDM0MC4yNzczNDQgMzk1LjYzNjcxOSAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYig5OS4xOTg5MTQlLDc2LjQ5OTkzOSUsMTcuOTk5MjY4JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDM1MC4zMjAzMTMgMzk0LjE4NzUgQyAzNTAuMzc4OTA2IDM5NC4xODM1OTQgMzUwLjQ0MTQwNiAzOTQuMTc5Njg4IDM1MC41MDM5MDYgMzk0LjE3NTc4MSBDIDM1MC40NDE0MDYgMzk0LjE3OTY4OCAzNTAuMzc4OTA2IDM5NC4xODM1OTQgMzUwLjMyMDMxMyAzOTQuMTg3NSAiLz4KPGcgY2xpcC1wYXRoPSJ1cmwoI2NsaXAzKSIgY2xpcC1ydWxlPSJub256ZXJvIj4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYig5OS4xOTg5MTQlLDc2LjQ5OTkzOSUsMTcuOTk5MjY4JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDMyLjkzNzUgMzA0LjQ3MjY1NiBDIDQ0Ljc5Mjk2OSAzMDQuMjM4MjgxIDc4LjExMzI4MSAzMDIuODY3MTg4IDEwMy4xNDQ1MzEgMzE5LjExNzE4OCBDIDEwMy4xNDQ1MzEgMzE5LjExNzE4OCAxMDMuOTY0ODQ0IDMyNi4wNjI1IDEwNi45NjA5MzggMzM1LjQ5MjE4OCBDIDEwMS40NjQ4NDQgMzM0LjE2Nzk2OSA5My45NDkyMTkgMzM0LjAyNzM0NCA4OC4yNjU2MjUgMzQxLjY2Nzk2OSBDIDEwNS40NDkyMTkgMzM5LjYwOTM3NSAxMTMuOTY4NzUgMzUyLjM5MDYyNSAxMTQuMjEwOTM4IDM1Mi43NTc4MTMgQyAxMTQuMjE0ODQ0IDM1Mi43NjE3MTkgMTE0LjIxNDg0NCAzNTIuNzY1NjI1IDExNC4yMTQ4NDQgMzUyLjc2NTYyNSBDIDExNS45MjE4NzUgMzU1LjkyMTg3NSAxMTcuODcxMDk0IDM1OS4wNzgxMjUgMTIwLjExMzI4MSAzNjIuMTI1IEMgNjguNTA3ODEzIDM2Ny40NzI2NTYgNDEuMzA4NTk0IDMzMS45MDIzNDQgMzIuOTM3NSAzMDQuNDcyNjU2IFogTSAyMy44NzEwOTQgMjI0LjczNDM3NSBDIDIzLjg3MTA5NCAyMjQuNzM0Mzc1IDUyLjIzNDM3NSAyMjcuNzU3ODEzIDc0LjA4NTkzOCAyNDEuMDA3ODEzIEMgOTUuOTM3NSAyNTQuMjU3ODEzIDEwNS42OTkyMTkgMjcyLjg1NTQ2OSAxMDUuNjk5MjE5IDI3Mi44NTU0NjkgQyAxMDUuNjk5MjE5IDI3Mi44NTU0NjkgMTAzLjE0NDUzMSAyNzkuMTMyODEzIDEwMy4xNDQ1MzEgMjgzLjU1MDc4MSBDIDk4LjQ5NjA5NCAyNzIuODU1NDY5IDgyLjY2Nzk2OSAyNjEuOTI5Njg4IDcxLjI5Njg3NSAyNzEuMjMwNDY5IEMgNzcuMTA1NDY5IDI3Mi4zOTA2MjUgOTcuMzMyMDMxIDI3OS44MzIwMzEgOTcuMzMyMDMxIDI5Ny4wMzUxNTYgQyA5Ny4zMzIwMzEgMjk3LjAzNTE1NiA3Mi4yMjY1NjMgMjkzLjMxMjUgNTkuMjA3MDMxIDI4NC44MDg1OTQgQyA0Ni4xODc1IDI3Ni4zMDA3ODEgMjkuOTE0MDYzIDI1Ny45ODA0NjkgMjMuODcxMDk0IDIyNC43MzQzNzUgWiBNIDc0LjMxNjQwNiAxNTAuNTc4MTI1IEMgMTAzLjE0NDUzMSAxNzguMDA3ODEzIDEwNi4xNTIzNDQgMjAxLjQ5NjA5NCAxMDYuNjMyODEzIDIxMy4zNDM3NSBDIDEwNy4zMjgxMjUgMjMwLjU0Njg3NSA5OC4wMzEyNSAyNDguOTEwMTU2IDk4LjAzMTI1IDI0OC45MTAxNTYgQyA5NC42NDg0MzggMjQ0LjI2OTUzMSA5MC42Nzk2ODggMjQwLjI2MTcxOSA4Ni42MTcxODggMjM2Ljg2NzE4OCBDIDg1LjAzMTI1IDIzMC44MDg1OTQgODMuNTExNzE5IDIyMC45NjA5MzggODguMjY1NjI1IDIxNS40Mzc1IEMgNzcuNTc0MjE5IDIxOC42OTE0MDYgNzcuMDcwMzEzIDIyOS45MjU3ODEgNzcuMDcwMzEzIDIyOS45MjU3ODEgQyA3MS4yMDMxMjUgMjI2LjE5OTIxOSA2Ni4wNTA3ODEgMjIzLjgxNjQwNiA2My4zOTA2MjUgMjIyLjY0NDUzMSBDIDU3LjU4MjAzMSAxOTIuMTkxNDA2IDYxLjMwMDc4MSAxNzIuNjYwMTU2IDc0LjMxNjQwNiAxNTAuNTc4MTI1IFogTSA0NDUuNjEzMjgxIDI0My44ODY3MTkgQyA0MzYuMDY2NDA2IDI2OC4wMjczNDQgNDEyLjAzNTE1NiAyODMuMTY3OTY5IDM4NC44MTI1IDI5My4xNDg0MzggQyAzODYuOTQ5MjE5IDI3NC4xNjQwNjMgMzg3LjUxOTUzMSAyNTIuOTQ5MjE5IDM4NS4zNjMyODEgMjI5LjkyNTc4MSBDIDM4My4yNjU2MjUgMjA3LjU0Njg3NSAzNzkuNTc0MjE5IDE4Ny45NjA5MzggMzc0LjYxNzE4OCAxNzAuNzYxNzE5IEMgMzk3Ljg3NSAxNjAuNTQ2ODc1IDQxMC45MTAxNTYgMTQ2LjUzMTI1IDQxNS4xOTUzMTMgMTI4LjIxMDkzOCBDIDQzNC42NzE4NzUgMTU3LjAxMTcxOSA0NDYuMTA1NDY5IDE5MS42OTE0MDYgNDQ2LjI4MTI1IDIyOS4wMzEyNSBDIDQ0Ni4yODUxNTYgMjI5LjMyODEyNSA0NDYuMjg5MDYzIDIyOS42Mjg5MDYgNDQ2LjI4OTA2MyAyMjkuOTI1NzgxIEMgNDQ2LjI4OTA2MyAyMzQuNDYwOTM4IDQ0Ni4xMTcxODggMjM4Ljk2MDkzOCA0NDUuNzkyOTY5IDI0My40MTQwNjMgQyA0NDUuNzMwNDY5IDI0My41NzAzMTMgNDQ1LjY3NTc4MSAyNDMuNzMwNDY5IDQ0NS42MTMyODEgMjQzLjg4NjcxOSBaIE0gMzM0LjkxNzk2OSAzMDYuMzQ3NjU2IEMgMzMzLjgyNDIxOSAzMDYuNTU4NTk0IDMzMi43NDIxODggMzA2Ljc2MTcxOSAzMzEuNjYwMTU2IDMwNi45NjQ4NDQgQyAzMjguNDIxODc1IDMwNy41NjY0MDYgMzI1LjIzNDM3NSAzMDguMTI4OTA2IDMyMi4xMzI4MTMgMzA4LjY1NjI1IEMgMzE1Ljc3NzM0NCAzMDkuNzM4MjgxIDMwOS4wNDY4NzUgMzEwLjY1NjI1IDMwMi4wNjI1IDMxMS4zODI4MTMgQyAzMDAuOTgwNDY5IDMxMS40OTYwOTQgMjk5Ljg5ODQzOCAzMTEuNjAxNTYzIDI5OC44MDQ2ODggMzExLjcwNzAzMSBDIDI5Mi40NTcwMzEgMzEyLjMwODU5NCAyODUuOTE3OTY5IDMxMi43NTM5MDYgMjc5LjI3NzM0NCAzMTMuMDI3MzQ0IEMgMjc4LjE5NTMxMyAzMTMuMDcwMzEzIDI3Ny4xMTMyODEgMzEzLjExMzI4MSAyNzYuMDIzNDM4IDMxMy4xNDg0MzggQyAyNzQuNTcwMzEzIDMxMy4xOTUzMTMgMjczLjExMzI4MSAzMTMuMjM0Mzc1IDI3MS42NTIzNDQgMzEzLjI2NTYyNSBDIDI3Mi41ODIwMzEgMjY5LjkxMDE1NiAyNzIuMTgzNTk0IDIyOC45MzM1OTQgMjcwLjk0OTIxOSAxODkuMjM4MjgxIEMgMjgyLjEyMTA5NCAxODkuNDA2MjUgMjkzLjI0NjA5NCAxODguODk4NDM4IDMwMy45OTYwOTQgMTg3LjU5NzY1NiBDIDMyOC4yMDMxMjUgMTg0LjY3NTc4MSAzNDguMTQ0NTMxIDE4MC40NjQ4NDQgMzY0LjE3NTc4MSAxNzQuODU1NDY5IEMgMzY5Ljg1MTU2MyAxOTYuNjg3NSAzNzMuMDc0MjE5IDIyMC45Mzc1IDM3Mi44MDg1OTQgMjQ2LjgyMDMxMyBDIDM3Mi42MTMyODEgMjY1Ljc4MTI1IDM3MC44MjgxMjUgMjgzLjA3MDMxMyAzNjguMTM2NzE5IDI5OC41NjI1IEMgMzU2Ljk3MjY1NiAzMDEuNzczNDM4IDM0NS42NjAxNTYgMzA0LjI4OTA2MyAzMzQuOTE3OTY5IDMwNi4zNDc2NTYgWiBNIDE2Ny44ODI4MTMgMTYwLjk4NDM3NSBDIDE3Ni44NTU0NjkgMTMzLjE3MTg3NSAxODkuODM5ODQ0IDExMC4wMjczNDQgMjA0LjM0Mzc1IDkzLjQ3NjU2MyBDIDIyMC4wMTU2MjUgOTkuNzUgMjM5LjQxNDA2MyAxMDMuMjg5MDYzIDI1OS4yMjY1NjMgMTA0LjYyODkwNiBDIDI1Ny44ODY3MTkgMTI4LjEzNjcxOSAyNTYuNzI2NTYzIDE1MS44MzIwMzEgMjU1Ljg1OTM3NSAxNzUuOTYwOTM4IEMgMjI2LjYzNjcxOSAxNzUuNDA2MjUgMTk1Ljg5ODQzOCAxNzEuMTQwNjI1IDE2Ny44ODI4MTMgMTYwLjk4NDM3NSBaIE0gMzQ3LjM1MTU2MyA2OC4wNTg1OTQgQyAzNDcuMzUxNTYzIDY4LjA1ODU5NCAzNjAuNDg4MjgxIDc4Ljc0MjE4OCAzNDIuMTIxMDk0IDg4LjI3NzM0NCBDIDMzOS42NDg0MzggODkuNTYyNSAzMzUuOTYwOTM4IDkwLjg3MTA5NCAzMzEuMzIwMzEzIDkyLjExMzI4MSBDIDMyMS4xMzY3MTkgODEuNTYyNSAzMTAuMTM2NzE5IDczLjE2MDE1NiAyOTguODI4MTI1IDY2LjI5Mjk2OSBDIDMwMi4yODUxNTYgNjQuNDI5Njg4IDMwNC4yNzczNDQgNjIuMjYxNzE5IDMwNC4yNzczNDQgNTkuOTQxNDA2IEMgMzA0LjI3NzM0NCA1NS41MjczNDQgMjk3LjA3ODEyNSA1MS42NDQ1MzEgMjg2LjE5NTMxMyA0OS40MDIzNDQgQyAzMDggNTEuOTk2MDk0IDMyOC42MjEwOTQgNTguNDQ5MjE5IDM0Ny4zNTE1NjMgNjguMDU4NTk0IFogTSAyNjUuNzE4NzUgODAuOTEwMTU2IEwgMjY1LjcxODc1IDcyLjUyMzQzOCBMIDI2NS4xOTE0MDYgNzIuNTE5NTMxIEMgMjY1LjE5MTQwNiA3Mi41MTU2MjUgMjY1LjE5MTQwNiA3Mi41MTU2MjUgMjY1LjE5MTQwNiA3Mi41MTU2MjUgQyAyNzUuNTE5NTMxIDcyLjQ2MDkzOCAyODQuODgyODEzIDcxLjE2MDE1NiAyOTEuODU1NDY5IDY5LjA3MDMxMyBDIDMwMi43NTM5MDYgNzMuNTg1OTM4IDMxMy43NTc4MTMgODIuMDcwMzEzIDMyMy45OTYwOTQgOTMuODQzNzUgQyAzMDkuNDI5Njg4IDk2Ljg5MDYyNSAyODguOTIxODc1IDk5LjE0NDUzMSAyNjYuODAwNzgxIDk4Ljg3MTA5NCBDIDI2Ni40NDkyMTkgOTIuODc1IDI2Ni4wODk4NDQgODYuODkwNjI1IDI2NS43MTg3NSA4MC45MTAxNTYgWiBNIDIzNi41MjM0MzggNjguODk0NTMxIEMgMjQyLjk4MDQ2OSA3MC45MTAxNTYgMjUxLjYwNTQ2OSA3Mi4yMzA0NjkgMjYxLjE5NTMxMyA3Mi40NzY1NjMgTCAyNjEuMTcxODc1IDcyLjQ3NjU2MyBDIDI2MS4xNzE4NzUgNzIuNDkyMTg4IDI2MS4xNzE4NzUgNzIuNTAzOTA2IDI2MS4xNzE4NzUgNzIuNTE5NTMxIEwgMjYwLjY0NDUzMSA3Mi41MjM0MzggTCAyNjAuNjQ0NTMxIDgwLjkxMDE1NiBDIDI2MC4yNzczNDQgODYuODI4MTI1IDI1OS45MTc5NjkgOTIuNzU3ODEzIDI1OS41NzAzMTMgOTguNjk1MzEzIEMgMjQxLjk1MzEyNSA5OC4wMzUxNTYgMjIzLjYzMjgxMyA5NS42OTUzMTMgMjA2LjcxODc1IDkwLjgzNTkzOCBDIDIxNi4yNDIxODggODAuNTUwNzgxIDIyNi4zNTE1NjMgNzMuMDg5ODQ0IDIzNi4zNjMyODEgNjguOTg0Mzc1IEMgMjM2LjM2MzI4MSA2OC45ODQzNzUgMjM2LjQyMTg3NSA2OC45NTMxMjUgMjM2LjUyMzQzOCA2OC44OTQ1MzEgWiBNIDI2Ny4xNTYyNSAxMDUuMDQ2ODc1IEMgMjg5LjQ4ODI4MSAxMDUuOTA2MjUgMzExLjc3MzQzOCAxMDQuMDc4MTI1IDMyOS4zMDA3ODEgMTAwLjMyNDIxOSBDIDM0MS42MzI4MTMgMTE2LjMyODEyNSAzNTIuNTUwNzgxIDEzNy4yMDMxMjUgMzYwLjM2MzI4MSAxNjEuNjY0MDYzIEMgMzM5Ljk3NjU2MyAxNjguODUxNTYzIDMwNy4wNjY0MDYgMTc1LjEyNSAyNzAuNTAzOTA2IDE3NS45Mzc1IEMgMjY5LjY0MDYyNSAxNTEuOTYwOTM4IDI2OC40ODgyODEgMTI4LjQxMDE1NiAyNjcuMTU2MjUgMTA1LjA0Njg3NSBaIE0gMzcwLjQxNzk2OSAxNTcuNTc0MjE5IEMgMzcwLjQxNzk2OSAxNTcuNTc0MjE5IDM3MC40MTc5NjkgMTU3LjU3NDIxOSAzNzAuNDE0MDYzIDE1Ny41NzQyMTkgQyAzNjEuNzM4MjgxIDEzMi44NjMyODEgMzUwLjIzMDQ2OSAxMTMuNjM2NzE5IDMzNy4xMDE1NjMgOTguNDQxNDA2IEMgMzU1Ljc1IDkzLjM3NSAzNjYuODgyODEzIDg1LjgzOTg0NCAzNjIuOTMzNTk0IDc3LjA1ODU5NCBDIDM2Mi45MzM1OTQgNzcuMDU4NTk0IDM2Mi45MzM1OTQgNzcuMDU0Njg4IDM2Mi45MzM1OTQgNzcuMDU0Njg4IEMgMzc1LjMzNTkzOCA4NS4wNjI1IDM4Ni43MDMxMjUgOTQuNTM1MTU2IDM5Ni43ODUxNTYgMTA1LjIzMDQ2OSBDIDM5Ni43ODUxNTYgMTA1LjIzMDQ2OSA0MTUuMTk1MzEzIDEzNi4xNjQwNjMgMzcwLjQxNzk2OSAxNTcuNTc0MjE5IFogTSAxNDIuNjYwMTU2IDIyOS45MjU3ODEgQyAxNDIuNTA3ODEzIDIzMS41NjY0MDYgMTQyLjM3MTA5NCAyMzMuMTk5MjE5IDE0Mi4yNDIxODggMjM0LjgyNDIxOSBDIDEzOC4xNDA2MjUgMjI4Ljk0OTIxOSAxMzUuMjI2NTYzIDIyNS40MzM1OTQgMTM1LjIyNjU2MyAyMjUuNDMzNTk0IEMgMTM1LjIyNjU2MyAyMTEuMTcxODc1IDEyNC45OTYwOTQgMjA2LjgzNTkzOCAxMjAuNjU2MjUgMjA1LjkwNjI1IEMgMTI5LjAyNzM0NCAyMTAuODY3MTg4IDEzMS41MDc4MTMgMjE5LjIzNDM3NSAxMjkuOTU3MDMxIDIyNC44MTY0MDYgQyAxMTguNDg4MjgxIDIzOC40NDkyMTkgMTExLjM1OTM3NSAyNTcuMDUwNzgxIDEwOC41NzAzMTMgMjY0LjE3NTc4MSBDIDEwNi43MTA5MzggMjYxLjM4NjcxOSAxMDYuNzEwOTM4IDI2MS4zODY3MTkgMTA2LjcxMDkzOCAyNjEuMzg2NzE5IEMgMTA2LjcxMDkzOCAyNjEuMzg2NzE5IDEyMS44OTQ1MzEgMjQyLjQ4MDQ2OSAxMTguODAwNzgxIDIxMC4yNDIxODggQyAxMTcuMTIxMDk0IDE5Mi44MTI1IDEwNy43MzgyODEgMTczLjkzMzU5NCA5Ny4xNzU3ODEgMTU4LjY0ODQzOCBDIDEyMi4xODM1OTQgMTAwLjAyMzQzOCAxNzcuMTAxNTYzIDU3LjIxODc1IDI0Mi43NjE3MTkgNDkuNDAyMzQ0IEMgMjMxLjg3ODkwNiA1MS42NDQ1MzEgMjI0LjY3OTY4OCA1NS41MjczNDQgMjI0LjY3OTY4OCA1OS45NDE0MDYgQyAyMjQuNjc5Njg4IDYyLjE2Nzk2OSAyMjYuNTExNzE5IDY0LjI1MzkwNiAyMjkuNzE4NzUgNjYuMDcwMzEzIEMgMjI5LjY1MjM0NCA2Ni4wNzQyMTkgMjI5LjU4OTg0NCA2Ni4wODU5MzggMjI5LjUyMzQzOCA2Ni4wOTM3NSBDIDIxOS4zMjgxMjUgNzIuMjUzOTA2IDIwOS4zNzUgNzkuNjYwMTU2IDIwMC4wNDI5NjkgODguNzU3ODEzIEMgMTk0LjgyODEyNSA4Ny4wMDM5MDYgMTg5Ljc4MTI1IDg0Ljk5NjA5NCAxODQuOTcyNjU2IDgyLjY5NTMxMyBDIDE4OC43ODUxNTYgODUuNjk5MjE5IDE5My4xOTE0MDYgODguMzYzMjgxIDE5OC4wNjI1IDkwLjcxODc1IEMgMTgyLjA3MDMxMyAxMDYuODc1IDE2OC4wMDc4MTMgMTI4LjIwMzEyNSAxNTcuODA0Njg4IDE1Ny4wMjM0MzggQyAxNDkuOTgwNDY5IDE1My42OTE0MDYgMTQyLjQxNzk2OSAxNDkuODU1NDY5IDEzNS4yMjY1NjMgMTQ1LjQ2NDg0NCBDIDEzOC42Nzk2ODggMTUxLjUwNzgxMyAxNDUuODk0NTMxIDE1Ny40NjQ4NDQgMTU1Ljc5Njg3NSAxNjIuOTQ5MjE5IEMgMTQ5LjYzMjgxMyAxODEuOTY0ODQ0IDE0NS4wODU5MzggMjA0LjA4NTkzOCAxNDIuNjYwMTU2IDIyOS45MjU3ODEgWiBNIDEzOC43ODkwNjMgMzQ4LjQ4ODI4MSBDIDEzMC4xMDkzNzUgMzQxLjA1MDc4MSAxMjcuMTY3OTY5IDMxOS4zNTE1NjMgMTM2Ljc3MzQzOCAzMTEuOTEwMTU2IEMgMTIxLjY4NzUgMzEzLjcxODc1IDExMy45NDE0MDYgMzM0LjMzOTg0NCAxMzUuMDAzOTA2IDM3MC44OTQ1MzEgQyAxMzQuODEyNSAzNzEuMDE5NTMxIDEzNC42MTcxODggMzcxLjE0MDYyNSAxMzQuNDEwMTU2IDM3MS4yNjU2MjUgQyAxMTAuMDY2NDA2IDM0My4xNDQ1MzEgMTA5LjgwODU5NCAzMTEuODM1OTM4IDEwOS44MDg1OTQgMzA5LjQzMzU5NCBDIDEwOS44MDg1OTQgMzA2Ljk0OTIxOSAxMTMuMjE4NzUgMjY5LjEzNjcxOSAxMzMuMDU0Njg4IDI0NC45NjA5MzggQyAxNDEuNzM0Mzc1IDI1My42NDA2MjUgMTUzLjI4OTA2MyAyNzMuNjEzMjgxIDE1NS4wNjI1IDI5Mi4zODI4MTMgQyAxNTYuODQzNzUgMzExLjIxNDg0NCAxNTUuMjE4NzUgMzI0IDEzOC43ODkwNjMgMzQ4LjQ4ODI4MSBaIE0gMTI3LjMzNTkzOCAzNzUuNjA1NDY5IEwgMTI3LjMzNTkzOCAzNzUuNjAxNTYzIEMgMTI5Ljc4NTE1NiAzNzcuOTEwMTU2IDEzMi4yOTI5NjkgMzgwLjE1NjI1IDEzNC44NTkzNzUgMzgyLjMzOTg0NCBDIDE0My45MjU3ODEgMzgwLjM1NTQ2OSAxNTEuODk0NTMxIDM3OC45NDkyMTkgMTU5LjAxNTYyNSAzNzguMDM5MDYzIEMgMTUzLjQ5NjA5NCAzNzQuMTAxNTYzIDE0OC4yMTA5MzggMzY5Ljg2MzI4MSAxNDMuMTcxODc1IDM2NS4zNDc2NTYgQyAxNDMuMjY5NTMxIDM2NS4xMzY3MTkgMTQzLjU1ODU5NCAzNjQuNzkyOTY5IDE0NCAzNjQuMzA4NTk0IEMgMTQ1Ljg3NSAzNjIuMjUgMTUwLjU0Njg3NSAzNTcuNjUyMzQ0IDE1NS4zMDg1OTQgMzUwLjAzMTI1IEMgMTU4Ljg1NTQ2OSAzNjEuMTMyODEzIDE2Mi41NDY4NzUgMzcwLjMwODU5NCAxNjUuNjkxNDA2IDM3Ny4zMDg1OTQgQyAxNzMuMjE4NzUgMzc2LjYyODkwNiAxNzkuNzUgMzc2LjU1ODU5NCAxODUuNjcxODc1IDM3Ni45NzI2NTYgQyAxNzkuOTMzNTk0IDM2Ni4wNDI5NjkgMTcyLjAyMzQzOCAzNDguNDQ1MzEzIDE2NS42OTUzMTMgMzI0LjkxMDE1NiBDIDE2Ny4zNTE1NjMgMzE3Ljk3NjU2MyAxNjguMzkwNjI1IDMxMC4wNTQ2ODggMTY4LjM5MDYyNSAzMDEuMDY2NDA2IEMgMTY4LjM5MDYyNSAyODUuODgyODEzIDE2Mi4zNzEwOTQgMjY5LjkxMDE1NiAxNTUuNDY0ODQ0IDI1Ni41NzgxMjUgQyAxNTUuMzM1OTM4IDI1My4zNzUgMTU1LjI1IDI1MC4xMjUgMTU1LjIxNDg0NCAyNDYuODIwMzEzIEMgMTU0LjkyMTg3NSAyMTguMTUyMzQ0IDE1OC45MDYyNSAxOTEuNDg4MjgxIDE2NS43NjE3MTkgMTY3Ljg5ODQzOCBDIDE4OC45Mzc1IDE3OC4zMDQ2ODggMjIxLjc0MjE4OCAxODYuMjY5NTMxIDI1NS40MzM1OTQgMTg4LjU4MjAzMSBDIDI1NC4xODM1OTQgMjI4LjQ3MjY1NiAyNTMuNzc3MzQ0IDI2OS42NTIzNDQgMjU0LjcwNzAzMSAzMTMuMjM0Mzc1IEMgMjUzLjQ2ODc1IDMxMy4yMDMxMjUgMjUyLjIzMDQ2OSAzMTMuMTY0MDYzIDI1MC45OTYwOTQgMzEzLjEyMTA5NCBDIDI0OS45MTAxNTYgMzEzLjA4MjAzMSAyNDguODI0MjE5IDMxMy4wMzkwNjMgMjQ3Ljc0MjE4OCAzMTIuOTg4MjgxIEMgMjQyLjM1MTU2MyAzMTIuNzQ2MDk0IDIzNi45ODgyODEgMzEyLjM3NSAyMzEuNjk5MjE5IDMxMS44NzEwOTQgQyAyMzAuNjEzMjgxIDMxMS43NjU2MjUgMjI5LjUyNzM0NCAzMTEuNjU2MjUgMjI4LjQ0NTMxMyAzMTEuNTM5MDYzIEMgMjE0LjkxNDA2MyAzMTAuMDk3NjU2IDIwMS45MzM1OTQgMzA3Ljc0NjA5NCAxOTAuMjkyOTY5IDMwNC4zNDc2NTYgQyAxODkuMTk1MzEzIDMwNC4wMjM0MzggMTg4LjExMzI4MSAzMDMuNjk1MzEzIDE4Ny4wMzkwNjMgMzAzLjM1NTQ2OSBDIDE4NC42ODc1IDMwMi42MDkzNzUgMTgyLjM5NDUzMSAzMDEuODIwMzEzIDE4MC4xNjc5NjkgMzAwLjk4NDM3NSBDIDE3Ny42NTIzNDQgMzAwLjAzNTE1NiAxNzUuMjE4NzUgMjk5LjAzMTI1IDE3Mi44ODY3MTkgMjk3Ljk2NDg0NCBDIDE5MS42OTE0MDYgMzE0LjU3NDIxOSAyMTguNzM4MjgxIDMyMy4zNjcxODggMjU1LjAyMzQzOCAzMjYuMzM5ODQ0IEMgMjU1LjY0NDUzMSAzNDkuMDUwNzgxIDI1Ni42MzI4MTMgMzcyLjQzNzUgMjU4LjA1ODU5NCAzOTYuNjM2NzE5IEMgMjYxLjU4MjAzMSAzOTYuODYzMjgxIDI2NS4wMDc4MTMgMzk2Ljg0NzY1NiAyNjguMzA0Njg4IDM5Ni42NDA2MjUgQyAyNjkuNzA3MDMxIDM3Mi43Njk1MzEgMjcwLjY5MTQwNiAzNDkuNjkxNDA2IDI3MS4zMTI1IDMyNy4yNjU2MjUgQyAyODQuNTI3MzQ0IDMyNy43MTg3NSAyOTguODE2NDA2IDMyNy41MzUxNTYgMzE0LjIyNjU2MyAzMjYuNzg5MDYzIEMgMzMxLjg2MzI4MSAzMjUuOTM3NSAzNDguNzI2NTYzIDMyMi42NzE4NzUgMzY0LjAxOTUzMSAzMTguMzIwMzEzIEMgMzU3LjI2NTYyNSAzNDYgMzQ4LjA2NjQwNiAzNjYuMjY1NjI1IDM0MS43ODEyNSAzNzguMDUwNzgxIEMgMzQ4LjMyNDIxOSAzNzcuMTQ4NDM4IDM1NS4zOTA2MjUgMzc2LjUzOTA2MyAzNjIuNzEwOTM4IDM3Ni40NjA5MzggQyAzNjguODYzMjgxIDM2Mi42MTMyODEgMzc2Ljk1MzEyNSAzNDAuNjk1MzEzIDM4MS45OTYwOTQgMzEyLjQ5NjA5NCBDIDQxMS44OTQ1MzEgMzAxLjY1MjM0NCA0MzIuOTI5Njg4IDI4OC4yNTc4MTMgNDM3LjAzNTE1NiAyODUuNTUwNzgxIEMgNDM3LjUxMTcxOSAyODUuMjM0Mzc1IDQzNy43NjU2MjUgMjg1LjA2MjUgNDM3Ljc3MzQzOCAyODUuMDU0Njg4IEMgNDI1Ljk3NjU2MyAzMjIuMTc1NzgxIDQwMi41ODk4NDQgMzU0LjEyNSAzNzEuODU1NDY5IDM3Ni42NDg0MzggQyAzNzkuOTMzNTk0IDM3Ny4wODU5MzggMzg4LjE3NTc4MSAzNzguMjY5NTMxIDM5Ni4yNDIxODggMzgwLjQ4ODI4MSBDIDQzOC4xMjEwOTQgMzQzLjgyMDMxMyA0NjQuNTYyNSAyODkuOTU3MDMxIDQ2NC41NjI1IDIyOS45MjU3ODEgQyA0NjQuNTYyNSAxMTkuNDI1NzgxIDM3NC45ODA0NjkgMjkuODQ3NjU2IDI2NC40NzY1NjMgMjkuODQ3NjU2IEMgMTg1LjMyODEyNSAyOS44NDc2NTYgMTE2LjkxNDA2MyA3NS44MDg1OTQgODQuNDY0ODQ0IDE0Mi40OTIxODggQyA3OS43MTQ4NDQgMTM3LjIxODc1IDc1LjI1IDEzMy4wODk4NDQgNzEuNjc5Njg4IDEzMC41ODU5MzggQyA3MS4zNzUgMTE2LjAxOTUzMSA1Ny40MjU3ODEgMTEyLjYwNTQ2OSA1MC42MDU0NjkgMTEzLjg0NzY1NiBDIDYzLjkzNzUgMTE1LjM5NDUzMSA2Ny4zNDM3NSAxMzEuODI0MjE5IDY3LjM0Mzc1IDEzMS44MjQyMTkgQyA0OS4wNTg1OTQgMTU5LjcyMjY1NiA0Ny4xOTkyMTkgMjA3LjE0ODQzOCA1My4wODU5MzggMjE3LjY4MzU5NCBDIDM1LjcyNjU2MyAyMTEuMTcxODc1IDkuNjkxNDA2IDIwOC42OTUzMTMgOS42OTE0MDYgMjA4LjY5NTMxMyBDIDIuMjUzOTA2IDIwMi40OTYwOTQgMi4yNTM5MDYgMTkxLjY0NDUzMSA0LjExMzI4MSAxODUuMTM2NzE5IEMgLTIuNzA3MDMxIDE5MS4zMzk4NDQgLTAuNTM5MDYzIDIwOC4wNzgxMjUgNi45MDIzNDQgMjEzLjM0Mzc1IEMgMTAuMDAzOTA2IDI0NC4zNDM3NSAzMy44MzIwMzEgMjgyLjc4MTI1IDQ1Ljk1NzAzMSAyOTAuMjE0ODQ0IEMgMzMuODY3MTg4IDI4OS41OTM3NSAxNC45NjA5MzggMjkwLjUyMzQzOCAxNC45NjA5MzggMjkwLjUyMzQzOCBDIDUuOTcyNjU2IDI4NC44MDg1OTQgNC4xMTMyODEgMjc5LjY3NTc4MSA1LjA0Mjk2OSAyNzAuMzc4OTA2IEMgLTEuNDY4NzUgMjc2LjU3NDIxOSAxLjk0MTQwNiAyODguNjY0MDYzIDEzLjA5NzY1NiAyOTUuMTc1NzgxIEMgMjUuODA4NTk0IDMzMC44MjAzMTMgNDYuODg2NzE5IDM0OC43OTY4NzUgNTguMzU1NDY5IDM1OS4zMzU5MzggQyA2OS44MjAzMTMgMzY5Ljg3NSAxMDQuODU1NDY5IDM4MC4xODc1IDEyNy4zMzU5MzggMzc1LjYwNTQ2OSAiLz4KPC9nPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDczLjI5ODY0NSUsMzguNzk4NTIzJSwxNS42OTk3NjglKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMTU1LjA2MjUgMjkyLjM4MjgxMyBDIDE1My4yODkwNjMgMjczLjYxMzI4MSAxNDEuNzM0Mzc1IDI1My42NDA2MjUgMTMzLjA1NDY4OCAyNDQuOTYwOTM4IEMgMTEzLjIxODc1IDI2OS4xMzY3MTkgMTA5LjgwODU5NCAzMDYuOTQ5MjE5IDEwOS44MDg1OTQgMzA5LjQzMzU5NCBDIDEwOS44MDg1OTQgMzExLjgzNTkzOCAxMTAuMDY2NDA2IDM0My4xNDQ1MzEgMTM0LjQxMDE1NiAzNzEuMjY1NjI1IEMgMTM0LjYxNzE4OCAzNzEuMTQwNjI1IDEzNC44MTI1IDM3MS4wMTk1MzEgMTM1LjAwMzkwNiAzNzAuODk0NTMxIEMgMTEzLjk0MTQwNiAzMzQuMzM5ODQ0IDEyMS42ODc1IDMxMy43MTg3NSAxMzYuNzczNDM4IDMxMS45MTAxNTYgQyAxMjcuMTY3OTY5IDMxOS4zNTE1NjMgMTMwLjEwOTM3NSAzNDEuMDUwNzgxIDEzOC43ODkwNjMgMzQ4LjQ4ODI4MSBDIDE1NS4yMTg3NSAzMjQgMTU2Ljg0Mzc1IDMxMS4yMTQ4NDQgMTU1LjA2MjUgMjkyLjM4MjgxMyAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYig3My4yOTg2NDUlLDM4Ljc5ODUyMyUsMTUuNjk5NzY4JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDc3LjA3MDMxMyAyMjkuOTI1NzgxIEMgNzcuMDcwMzEzIDIyOS45MjU3ODEgNzcuNTc0MjE5IDIxOC42OTE0MDYgODguMjY1NjI1IDIxNS40Mzc1IEMgODMuNTExNzE5IDIyMC45NjA5MzggODUuMDMxMjUgMjMwLjgwODU5NCA4Ni42MTcxODggMjM2Ljg2NzE4OCBDIDkwLjY3OTY4OCAyNDAuMjYxNzE5IDk0LjY0ODQzOCAyNDQuMjY5NTMxIDk4LjAzMTI1IDI0OC45MTAxNTYgQyA5OC4wMzEyNSAyNDguOTEwMTU2IDEwNy4zMjgxMjUgMjMwLjU0Njg3NSAxMDYuNjMyODEzIDIxMy4zNDM3NSBDIDEwNi4xNTIzNDQgMjAxLjQ5NjA5NCAxMDMuMTQ0NTMxIDE3OC4wMDc4MTMgNzQuMzE2NDA2IDE1MC41NzgxMjUgQyA2MS4zMDA3ODEgMTcyLjY2MDE1NiA1Ny41ODIwMzEgMTkyLjE5MTQwNiA2My4zOTA2MjUgMjIyLjY0NDUzMSBDIDY2LjA1MDc4MSAyMjMuODE2NDA2IDcxLjIwMzEyNSAyMjYuMTk5MjE5IDc3LjA3MDMxMyAyMjkuOTI1NzgxICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDczLjI5ODY0NSUsMzguNzk4NTIzJSwxNS42OTk3NjglKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gNTkuMjA3MDMxIDI4NC44MDg1OTQgQyA3Mi4yMjY1NjMgMjkzLjMxMjUgOTcuMzMyMDMxIDI5Ny4wMzUxNTYgOTcuMzMyMDMxIDI5Ny4wMzUxNTYgQyA5Ny4zMzIwMzEgMjc5LjgzMjAzMSA3Ny4xMDU0NjkgMjcyLjM5MDYyNSA3MS4yOTY4NzUgMjcxLjIzMDQ2OSBDIDgyLjY2Nzk2OSAyNjEuOTI5Njg4IDk4LjQ5NjA5NCAyNzIuODU1NDY5IDEwMy4xNDQ1MzEgMjgzLjU1MDc4MSBDIDEwMy4xNDQ1MzEgMjc5LjEzMjgxMyAxMDUuNjk5MjE5IDI3Mi44NTU0NjkgMTA1LjY5OTIxOSAyNzIuODU1NDY5IEMgMTA1LjY5OTIxOSAyNzIuODU1NDY5IDk1LjkzNzUgMjU0LjI1NzgxMyA3NC4wODU5MzggMjQxLjAwNzgxMyBDIDUyLjIzNDM3NSAyMjcuNzU3ODEzIDIzLjg3MTA5NCAyMjQuNzM0Mzc1IDIzLjg3MTA5NCAyMjQuNzM0Mzc1IEMgMjkuOTE0MDYzIDI1Ny45ODA0NjkgNDYuMTg3NSAyNzYuMzAwNzgxIDU5LjIwNzAzMSAyODQuODA4NTk0ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDczLjI5ODY0NSUsMzguNzk4NTIzJSwxNS42OTk3NjglKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMTIwLjExMzI4MSAzNjIuMTI1IEMgMTE3Ljg3MTA5NCAzNTkuMDc4MTI1IDExNS45MjE4NzUgMzU1LjkyMTg3NSAxMTQuMjE0ODQ0IDM1Mi43NjU2MjUgQyAxMTQuMjE0ODQ0IDM1Mi43NjU2MjUgMTE0LjIxNDg0NCAzNTIuNzYxNzE5IDExNC4yMTA5MzggMzUyLjc1NzgxMyBDIDExMy45Njg3NSAzNTIuMzkwNjI1IDEwNS40NDkyMTkgMzM5LjYwOTM3NSA4OC4yNjU2MjUgMzQxLjY2Nzk2OSBDIDkzLjk0OTIxOSAzMzQuMDI3MzQ0IDEwMS40NjQ4NDQgMzM0LjE2Nzk2OSAxMDYuOTYwOTM4IDMzNS40OTIxODggQyAxMDMuOTY0ODQ0IDMyNi4wNjI1IDEwMy4xNDQ1MzEgMzE5LjExNzE4OCAxMDMuMTQ0NTMxIDMxOS4xMTcxODggQyA3OC4xMTMyODEgMzAyLjg2NzE4OCA0NC43OTI5NjkgMzA0LjIzODI4MSAzMi45Mzc1IDMwNC40NzI2NTYgQyA0MS4zMDg1OTQgMzMxLjkwMjM0NCA2OC41MDc4MTMgMzY3LjQ3MjY1NiAxMjAuMTEzMjgxIDM2Mi4xMjUgIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoMTAwJSwxMDAlLDEwMCUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAyMjEuMTIxMDk0IDIzMC43NDIxODggTCAyMjYuMzE2NDA2IDIzMC43NDIxODggTCAyMjYuMzE2NDA2IDIyNS41NTA3ODEgTCAyMjEuMTIxMDk0IDIyNS41NTA3ODEgTCAyMjEuMTIxMDk0IDIzMC43NDIxODggIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoMTAwJSwxMDAlLDEwMCUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAyMzcuNjI4OTA2IDIzMC43NDIxODggTCAyNDIuODIwMzEzIDIzMC43NDIxODggTCAyNDIuODIwMzEzIDIyNS41NTA3ODEgTCAyMzcuNjI4OTA2IDIyNS41NTA3ODEgTCAyMzcuNjI4OTA2IDIzMC43NDIxODggIi8+CjxwYXRoIHN0eWxlPSIgc3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOm5vbnplcm87ZmlsbDpyZ2IoMTAwJSwxMDAlLDEwMCUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAyODIuNDk2MDk0IDI1NC42ODM1OTQgTCAyODcuNjg3NSAyNTQuNjgzNTk0IEwgMjg3LjY4NzUgMjQ5LjQ5MjE4OCBMIDI4Mi40OTYwOTQgMjQ5LjQ5MjE4OCBMIDI4Mi40OTYwOTQgMjU0LjY4MzU5NCAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMDAlLDEwMCUsMTAwJSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDI5NS45MDIzNDQgMjQ5LjQ5MjE4OCBMIDI5MC43MTA5MzggMjQ5LjQ5MjE4OCBMIDI5MC43MTA5MzggMjU0LjY4MzU5NCBMIDI5NS45MDIzNDQgMjU0LjY4MzU5NCBMIDI5NS45MDIzNDQgMjQ5LjQ5MjE4OCAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMDAlLDEwMCUsMTAwJSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDI4Mi40OTYwOTQgMjYyLjgyMDMxMyBMIDI4Ny42ODc1IDI2Mi44MjAzMTMgTCAyODcuNjg3NSAyNTcuNjI4OTA2IEwgMjgyLjQ5NjA5NCAyNTcuNjI4OTA2IEwgMjgyLjQ5NjA5NCAyNjIuODIwMzEzICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEwMCUsMTAwJSwxMDAlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMjk1LjkwMjM0NCAyNTcuNjI4OTA2IEwgMjkwLjcxMDkzOCAyNTcuNjI4OTA2IEwgMjkwLjcxMDkzOCAyNjIuODIwMzEzIEwgMjk1LjkwMjM0NCAyNjIuODIwMzEzIEwgMjk1LjkwMjM0NCAyNTcuNjI4OTA2ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDEwMCUsMTAwJSwxMDAlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMzA1LjI3NzM0NCAyOTUuNTYyNSBMIDMxMC40Njg3NSAyOTUuNTYyNSBMIDMxMC40Njg3NSAyOTAuMzY3MTg4IEwgMzA1LjI3NzM0NCAyOTAuMzY3MTg4IEwgMzA1LjI3NzM0NCAyOTUuNTYyNSAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMDAlLDEwMCUsMTAwJSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDIyOS41MTE3MTkgMjMwLjc0MjE4OCBMIDIzNC43MDMxMjUgMjMwLjc0MjE4OCBMIDIzNC43MDMxMjUgMjI1LjU1MDc4MSBMIDIyOS41MTE3MTkgMjI1LjU1MDc4MSBMIDIyOS41MTE3MTkgMjMwLjc0MjE4OCAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMC41OTg3NTUlLDU2Ljg5ODQ5OSUsODAuNzk5ODY2JSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDM3My4zMjgxMjUgMzk1LjIyMjY1NiBDIDM3Mi40ODQzNzUgMzk1LjA4OTg0NCAzNzEuNjUyMzQ0IDM5NC45NzI2NTYgMzcwLjgyODEyNSAzOTQuODU5Mzc1IEMgMzcwLjY2MDE1NiAzOTQuODM1OTM4IDM3MC40ODgyODEgMzk0LjgxNjQwNiAzNzAuMzIwMzEzIDM5NC43OTI5NjkgQyAzNjkuNTExNzE5IDM5NC42ODc1IDM2OC43MTQ4NDQgMzk0LjU5Mzc1IDM2Ny45Mjk2ODggMzk0LjUxMTcxOSBDIDM2Ny43NzM0MzggMzk0LjQ5MjE4OCAzNjcuNjE3MTg4IDM5NC40NzY1NjMgMzY3LjQ2NDg0NCAzOTQuNDYwOTM4IEMgMzY2LjY1NjI1IDM5NC4zNzg5MDYgMzY1Ljg2MzI4MSAzOTQuMzA0Njg4IDM2NS4wNzgxMjUgMzk0LjIzODI4MSBDIDM2NC45OTYwOTQgMzk0LjIzNDM3NSAzNjQuOTE0MDYzIDM5NC4yMjY1NjMgMzY0LjgzMjAzMSAzOTQuMjIyNjU2IEMgMzY0LjA2NjQwNiAzOTQuMTYwMTU2IDM2My4zMDg1OTQgMzk0LjExMzI4MSAzNjIuNTY2NDA2IDM5NC4wNzAzMTMgQyAzNjIuNDcyNjU2IDM5NC4wNjY0MDYgMzYyLjM3ODkwNiAzOTQuMDU4NTk0IDM2Mi4yODUxNTYgMzk0LjA1NDY4OCBDIDM2MS41MjczNDQgMzk0LjAxMTcxOSAzNjAuNzc3MzQ0IDM5My45ODQzNzUgMzYwLjAzOTA2MyAzOTMuOTYwOTM4IEMgMzU5LjkwNjI1IDM5My45NTcwMzEgMzU5Ljc3MzQzOCAzOTMuOTUzMTI1IDM1OS42NDA2MjUgMzkzLjk0OTIxOSBDIDM1OC45MTc5NjkgMzkzLjkyOTY4OCAzNTguMjAzMTI1IDM5My45MjE4NzUgMzU3LjUgMzkzLjkxNzk2OSBDIDM1Ny4zNzUgMzkzLjkxNzk2OSAzNTcuMjUzOTA2IDM5My45MTc5NjkgMzU3LjEzMjgxMyAzOTMuOTE3OTY5IEMgMzU2LjQxNDA2MyAzOTMuOTE3OTY5IDM1NS43MDMxMjUgMzkzLjkyOTY4OCAzNTUuMDA3ODEzIDM5My45NDUzMTMgQyAzNTQuOTM3NSAzOTMuOTQ1MzEzIDM1NC44NjcxODggMzkzLjk0OTIxOSAzNTQuNzk2ODc1IDM5My45NDkyMTkgQyAzNTMuMzIwMzEzIDM5My45OTIxODggMzUxLjg4NjcxOSAzOTQuMDY2NDA2IDM1MC41MDM5MDYgMzk0LjE3NTc4MSBDIDM1MC40NDE0MDYgMzk0LjE3OTY4OCAzNTAuMzc4OTA2IDM5NC4xODM1OTQgMzUwLjMyMDMxMyAzOTQuMTg3NSBDIDM0OS42NDQ1MzEgMzk0LjI0MjE4OCAzNDguOTg0Mzc1IDM5NC4zMDQ2ODggMzQ4LjMyODEyNSAzOTQuMzcxMDk0IEMgMzQ4LjI2MTcxOSAzOTQuMzc4OTA2IDM0OC4xOTE0MDYgMzk0LjM4NjcxOSAzNDguMTI1IDM5NC4zOTQ1MzEgQyAzNDcuNDY0ODQ0IDM5NC40NjQ4NDQgMzQ2LjgxNjQwNiAzOTQuNTQyOTY5IDM0Ni4xNzk2ODggMzk0LjYyNSBDIDM0Ni4xNDQ1MzEgMzk0LjYyODkwNiAzNDYuMTA5Mzc1IDM5NC42MzY3MTkgMzQ2LjA3NDIxOSAzOTQuNjQwNjI1IEMgMzQ0LjA2NjQwNiAzOTQuOTA2MjUgMzQyLjE2MDE1NiAzOTUuMjM4MjgxIDM0MC4zNTU0NjkgMzk1LjYyMTA5NCBDIDM0MC4zMjgxMjUgMzk1LjYyNSAzNDAuMzAwNzgxIDM5NS42Mjg5MDYgMzQwLjI3NzM0NCAzOTUuNjM2NzE5IEMgMzM5LjY4MzU5NCAzOTUuNzYxNzE5IDMzOS4xMDE1NjMgMzk1Ljg5NDUzMSAzMzguNTMxMjUgMzk2LjAyNzM0NCBDIDMzOC41MTE3MTkgMzk2LjAzMTI1IDMzOC40OTYwOTQgMzk2LjAzNTE1NiAzMzguNDc2NTYzIDM5Ni4wMzkwNjMgQyAzMzcuODAwNzgxIDM5Ni4xOTkyMTkgMzM3LjE0MDYyNSAzOTYuMzY3MTg4IDMzNi40OTIxODggMzk2LjUzOTA2MyBDIDMzNi40ODQzNzUgMzk2LjUzOTA2MyAzMzYuNDc2NTYzIDM5Ni41NDI5NjkgMzM2LjQ2ODc1IDM5Ni41NDI5NjkgQyAzMjkuNjc5Njg4IDM5OC4zNTE1NjMgMzI0LjQyOTY4OCA0MDAuNzM0Mzc1IDMyMC4yMDMxMjUgNDAyLjU2NjQwNiBDIDMxOS45NzI2NTYgNDAyLjY2Nzk2OSAzMTkuNzM4MjgxIDQwMi43Njk1MzEgMzE5LjUxMTcxOSA0MDIuODY3MTg4IEMgMzE5LjQwNjI1IDQwMi45MTAxNTYgMzE5LjMwNDY4OCA0MDIuOTUzMTI1IDMxOS4xOTkyMTkgNDAzIEMgMzE4Ljg3NSA0MDMuMTM2NzE5IDMxOC41NTQ2ODggNDAzLjI3MzQzOCAzMTguMjM4MjgxIDQwMy40MDIzNDQgQyAzMTguMTkxNDA2IDQwMy40MjU3ODEgMzE4LjE0NDUzMSA0MDMuNDQxNDA2IDMxOC4wOTc2NTYgNDAzLjQ2MDkzOCBDIDMxNy43NjE3MTkgNDAzLjYwMTU2MyAzMTcuNDI5Njg4IDQwMy43MzgyODEgMzE3LjEwNTQ2OSA0MDMuODYzMjgxIEMgMzE3LjA3NDIxOSA0MDMuODc1IDMxNy4wNDY4NzUgNDAzLjg4NjcxOSAzMTcuMDE1NjI1IDQwMy44OTg0MzggQyAzMTYuNjgzNTk0IDQwNC4wMjczNDQgMzE2LjM1NTQ2OSA0MDQuMTUyMzQ0IDMxNi4wMzEyNSA0MDQuMjY5NTMxIEMgMzE2LjAxMTcxOSA0MDQuMjc3MzQ0IDMxNS45OTIxODggNDA0LjI4NTE1NiAzMTUuOTcyNjU2IDQwNC4yODkwNjMgQyAzMTUuNjQ0NTMxIDQwNC40MTAxNTYgMzE1LjMyNDIxOSA0MDQuNTE1NjI1IDMxNS4wMTE3MTkgNDA0LjYxNzE4OCBDIDMxNS4wMDc4MTMgNDA0LjYyMTA5NCAzMTQuOTk2MDk0IDQwNC42MjEwOTQgMzE0Ljk4ODI4MSA0MDQuNjI1IEMgMzE0Ljk3NjU2MyA0MDQuNjI4OTA2IDMxNC45NjA5MzggNDA0LjYzNjcxOSAzMTQuOTQ5MjE5IDQwNC42NDA2MjUgQyAzMTQuOTMzNTk0IDQwNC42NDQ1MzEgMzE0LjkyNTc4MSA0MDQuNjQ0NTMxIDMxNC45MTAxNTYgNDA0LjY0ODQzOCBDIDMxNC41MzkwNjMgNDA0Ljc2NTYyNSAzMTQuMTc5Njg4IDQwNC44NzEwOTQgMzEzLjgyODEyNSA0MDQuOTYwOTM4IEMgMzEzLjc1MzkwNiA0MDQuOTc2NTYzIDMxMy42Nzk2ODggNDA1IDMxMy42MDkzNzUgNDA1LjAxOTUzMSBDIDMxMy4xMzI4MTMgNDA1LjE1NjI1IDMxMi42NTIzNDQgNDA1LjI4OTA2MyAzMTIuMTcxODc1IDQwNS40MTQwNjMgQyAzMDkuOTY4NzUgNDA2LjA1ODU5NCAzMDcuNTg5ODQ0IDQwNi45MDIzNDQgMzA0Ljg5NDUzMSA0MDcuODE2NDA2IEMgMzA0LjgwNDY4OCA0MDcuODQ3NjU2IDMwNC43MTQ4NDQgNDA3Ljg3NSAzMDQuNjI1IDQwNy45MDYyNSBDIDMwNC4zNzUgNDA3Ljk5MjE4OCAzMDQuMTIxMDk0IDQwOC4wNzQyMTkgMzAzLjg2NzE4OCA0MDguMTYwMTU2IEMgMzAzLjcxNDg0NCA0MDguMjEwOTM4IDMwMy41NTg1OTQgNDA4LjI2NTYyNSAzMDMuNDAyMzQ0IDQwOC4zMTY0MDYgQyAzMDMuMTgzNTk0IDQwOC4zODY3MTkgMzAyLjk2NDg0NCA0MDguNDYwOTM4IDMwMi43NDIxODggNDA4LjUzMTI1IEMgMzAyLjU1ODU5NCA0MDguNTkzNzUgMzAyLjM3NSA0MDguNjUyMzQ0IDMwMi4xODc1IDQwOC43MTQ4NDQgQyAzMDEuOTgwNDY5IDQwOC43ODEyNSAzMDEuNzY1NjI1IDQwOC44NDc2NTYgMzAxLjU1NDY4OCA0MDguOTE3OTY5IEMgMzAxLjM1MTU2MyA0MDguOTgwNDY5IDMwMS4xNTIzNDQgNDA5LjA0Njg3NSAzMDAuOTQ1MzEzIDQwOS4xMDkzNzUgQyAzMDAuNzM4MjgxIDQwOS4xNzU3ODEgMzAwLjUyMzQzOCA0MDkuMjQyMTg4IDMwMC4zMTI1IDQwOS4zMDg1OTQgQyAzMDAuMDk3NjU2IDQwOS4zNzUgMjk5Ljg4NjcxOSA0MDkuNDQxNDA2IDI5OS42Njc5NjkgNDA5LjUwMzkwNiBDIDI5OS40NTcwMzEgNDA5LjU3MDMxMyAyOTkuMjM0Mzc1IDQwOS42MzY3MTkgMjk5LjAxOTUzMSA0MDkuNjk5MjE5IEMgMjk4Ljc5Njg3NSA0MDkuNzY1NjI1IDI5OC41NzQyMTkgNDA5LjgzMjAzMSAyOTguMzQ3NjU2IDQwOS44OTg0MzggQyAyOTguMTE3MTg4IDQwOS45Njg3NSAyOTcuODc4OTA2IDQxMC4wMzUxNTYgMjk3LjY0MDYyNSA0MTAuMTAxNTYzIEMgMjk3LjI3MzQzOCA0MTAuMjA3MDMxIDI5Ni45MDIzNDQgNDEwLjMxMjUgMjk2LjUxOTUzMSA0MTAuNDE0MDYzIEMgMjk2LjIxNDg0NCA0MTAuNSAyOTUuOTEwMTU2IDQxMC41ODIwMzEgMjk1LjU5NzY1NiA0MTAuNjY3OTY5IEMgMjk1LjM4MjgxMyA0MTAuNzIyNjU2IDI5NS4xNjAxNTYgNDEwLjc3NzM0NCAyOTQuOTQxNDA2IDQxMC44MzU5MzggQyAyOTQuNjcxODc1IDQxMC45MDYyNSAyOTQuNDAyMzQ0IDQxMC45NzY1NjMgMjk0LjEyNSA0MTEuMDQyOTY5IEMgMjkzLjg5NDUzMSA0MTEuMTAxNTYzIDI5My42NjAxNTYgNDExLjE1NjI1IDI5My40Mjk2ODggNDExLjIxNDg0NCBDIDI5My4xNTIzNDQgNDExLjI4MTI1IDI5Mi44Nzg5MDYgNDExLjM0NzY1NiAyOTIuNTk3NjU2IDQxMS40MTQwNjMgQyAyOTIuMzU1NDY5IDQxMS40NzI2NTYgMjkyLjEwOTM3NSA0MTEuNTI3MzQ0IDI5MS44NjcxODggNDExLjU4MjAzMSBDIDI5MS41ODIwMzEgNDExLjY0NDUzMSAyOTEuMzAwNzgxIDQxMS43MTA5MzggMjkxLjAxMTcxOSA0MTEuNzczNDM4IEMgMjkwLjc2MTcxOSA0MTEuODI4MTI1IDI5MC41MDc4MTMgNDExLjg3ODkwNiAyOTAuMjUzOTA2IDQxMS45MzM1OTQgQyAyODkuOTYwOTM4IDQxMS45OTYwOTQgMjg5LjY2NDA2MyA0MTIuMDU4NTk0IDI4OS4zNjMyODEgNDEyLjEyMTA5NCBDIDI4OS4xMDU0NjkgNDEyLjE3MTg3NSAyODguODQzNzUgNDEyLjIyMjY1NiAyODguNTgyMDMxIDQxMi4yNzM0MzggQyAyODguMjczNDM4IDQxMi4zMzIwMzEgMjg3Ljk2NDg0NCA0MTIuMzk0NTMxIDI4Ny42NTIzNDQgNDEyLjQ0OTIxOSBDIDI4Ny4zODY3MTkgNDEyLjUgMjg3LjExNzE4OCA0MTIuNTQ2ODc1IDI4Ni44NDc2NTYgNDEyLjU5NzY1NiBDIDI4Ni41MjM0MzggNDEyLjY1MjM0NCAyODYuMjAzMTI1IDQxMi43MTA5MzggMjg1Ljg3NSA0MTIuNzY1NjI1IEMgMjg1LjYwMTU2MyA0MTIuODEyNSAyODUuMzIwMzEzIDQxMi44NTU0NjkgMjg1LjA0Mjk2OSA0MTIuOTAyMzQ0IEMgMjg0LjcxMDkzOCA0MTIuOTU3MDMxIDI4NC4zNzUgNDEzLjAwNzgxMyAyODQuMDM1MTU2IDQxMy4wNTg1OTQgQyAyODMuNzUgNDEzLjEwMTU2MyAyODMuNDYwOTM4IDQxMy4xNDQ1MzEgMjgzLjE3MTg3NSA0MTMuMTg3NSBDIDI4Mi44MjQyMTkgNDEzLjIzODI4MSAyODIuNDc2NTYzIDQxMy4yODUxNTYgMjgyLjEyMTA5NCA0MTMuMzMyMDMxIEMgMjgxLjgyODEyNSA0MTMuMzcxMDk0IDI4MS41MzEyNSA0MTMuNDEwMTU2IDI4MS4yMzQzNzUgNDEzLjQ0OTIxOSBDIDI4MC44NzEwOTQgNDEzLjQ5NjA5NCAyODAuNTAzOTA2IDQxMy41MzkwNjMgMjgwLjEzMjgxMyA0MTMuNTgyMDMxIEMgMjc5LjgzMjAzMSA0MTMuNjIxMDk0IDI3OS41MjczNDQgNDEzLjY1NjI1IDI3OS4yMjI2NTYgNDEzLjY4NzUgQyAyNzguODQzNzUgNDEzLjczMDQ2OSAyNzguNDUzMTI1IDQxMy43Njk1MzEgMjc4LjA2NjQwNiA0MTMuODA4NTk0IEMgMjc3Ljc1NzgxMyA0MTMuODM5ODQ0IDI3Ny40NDkyMTkgNDEzLjg3MTA5NCAyNzcuMTM2NzE5IDQxMy45MDIzNDQgQyAyNzYuNzM4MjgxIDQxMy45Mzc1IDI3Ni4zMjgxMjUgNDEzLjk3MjY1NiAyNzUuOTIxODc1IDQxNC4wMDc4MTMgQyAyNzUuNjA1NDY5IDQxNC4wMzUxNTYgMjc1LjI5Mjk2OSA0MTQuMDYyNSAyNzQuOTc2NTYzIDQxNC4wODU5MzggQyAyNzQuNTU0Njg4IDQxNC4xMTcxODggMjc0LjEyNSA0MTQuMTQ0NTMxIDI3My42OTUzMTMgNDE0LjE3NTc4MSBDIDI3My4zNzUgNDE0LjE5NTMxMyAyNzMuMDU0Njg4IDQxNC4yMTg3NSAyNzIuNzMwNDY5IDQxNC4yMzgyODEgQyAyNzIuMjgxMjUgNDE0LjI2NTYyNSAyNzEuODI0MjE5IDQxNC4yODkwNjMgMjcxLjM2NzE4OCA0MTQuMzEyNSBDIDI3MS4wNTA3ODEgNDE0LjMyODEyNSAyNzAuNzM0Mzc1IDQxNC4zNDc2NTYgMjcwLjQxMDE1NiA0MTQuMzU5Mzc1IEMgMjY5LjkyMTg3NSA0MTQuMzgyODEzIDI2OS40MjE4NzUgNDE0LjM5ODQzOCAyNjguOTI1NzgxIDQxNC40MTQwNjMgQyAyNjguNjE3MTg4IDQxNC40MjU3ODEgMjY4LjMxMjUgNDE0LjQzNzUgMjY4LjAwMzkwNiA0MTQuNDQ1MzEzIEMgMjY3LjQ0OTIxOSA0MTQuNDYwOTM4IDI2Ni44Nzg5MDYgNDE0LjQ3MjY1NiAyNjYuMzEyNSA0MTQuNDgwNDY5IEMgMjY2LjA0Mjk2OSA0MTQuNDg4MjgxIDI2NS43ODEyNSA0MTQuNDk2MDk0IDI2NS41MDc4MTMgNDE0LjQ5NjA5NCBDIDI2NC42NjQwNjMgNDE0LjUwNzgxMyAyNjMuODA0Njg4IDQxNC41MTE3MTkgMjYyLjkyOTY4OCA0MTQuNTExNzE5IEMgMjI5LjY5NTMxMyA0MTQuMzk4NDM4IDIxMC4wNzQyMTkgNDAzLjIyMjY1NiAxOTEuNjIxMDk0IDM5Ni45MDYyNSBDIDE3OSAzOTIuNTgyMDMxIDE1Ni41MjczNDQgMzk4LjA1NDY4OCAxNTYuMTI4OTA2IDM5OC4xNTIzNDQgQyAxODcuMzU1NDY5IDQxOC4zMDg1OTQgMjI0LjU1MDc4MSA0MzAuMDAzOTA2IDI2NC40NzY1NjMgNDMwLjAwMzkwNiBDIDMwNS45NzI2NTYgNDMwLjAwMzkwNiAzNDQuNTE5NTMxIDQxNy4zNzUgMzc2LjQ3MjY1NiAzOTUuNzUgQyAzNzUuNTQ2ODc1IDM5NS41ODIwMzEgMzc0LjYzNjcxOSAzOTUuNDI5Njg4IDM3My43MzgyODEgMzk1LjI4NTE1NiBDIDM3My42MDE1NjMgMzk1LjI2NTYyNSAzNzMuNDY0ODQ0IDM5NS4yNDIxODggMzczLjMyODEyNSAzOTUuMjIyNjU2ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDU1LjY5OTE1OCUsNzcuNTk4NTcyJSwyNi4yOTg1MjMlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gMzY5LjUzNTE1NiAzNzYuNTQ2ODc1IEMgMzY3LjI0MjE4OCAzNzYuNDYwOTM4IDM2NC45NjQ4NDQgMzc2LjQzNzUgMzYyLjcxMDkzOCAzNzYuNDYwOTM4IEMgMzU1LjM5MDYyNSAzNzYuNTM5MDYzIDM0OC4zMjQyMTkgMzc3LjE0ODQzOCAzNDEuNzgxMjUgMzc4LjA1MDc4MSBDIDMyMy45MDIzNDQgMzgwLjUxNTYyNSAzMDkuOTMzNTk0IDM4NS4xNDA2MjUgMzA1LjM5NDUzMSAzODYuOTE3OTY5IEMgMjk5LjgxNjQwNiAzODkuMTEzMjgxIDI4NS45MTAxNTYgMzk1LjUzOTA2MyAyNjguMzA0Njg4IDM5Ni42NDA2MjUgQyAyNjUuMDA3ODEzIDM5Ni44NDc2NTYgMjYxLjU4MjAzMSAzOTYuODYzMjgxIDI1OC4wNTg1OTQgMzk2LjYzNjcxOSBDIDI1MS4xMDU0NjkgMzk2LjE3OTY4OCAyNDMuNzY1NjI1IDM5NC43NTc4MTMgMjM2LjI2OTUzMSAzOTEuODc4OTA2IEMgMjE3LjM5NDUzMSAzODQuNjM2NzE5IDIwNC42OTE0MDYgMzc4LjMwMDc4MSAxODUuNjcxODc1IDM3Ni45NzI2NTYgQyAxNzkuNzUgMzc2LjU1ODU5NCAxNzMuMjE4NzUgMzc2LjYyODkwNiAxNjUuNjkxNDA2IDM3Ny4zMDg1OTQgQyAxNjQuMjI2NTYzIDM3Ny40NDE0MDYgMTYyLjcyMjY1NiAzNzcuNTk3NjU2IDE2MS4xNzU3ODEgMzc3Ljc3NzM0NCBDIDE2MC40NjQ4NDQgMzc3Ljg1OTM3NSAxNTkuNzQ2MDk0IDM3Ny45NDUzMTMgMTU5LjAxNTYyNSAzNzguMDM5MDYzIEMgMTUxLjg5NDUzMSAzNzguOTQ5MjE5IDE0My45MjU3ODEgMzgwLjM1NTQ2OSAxMzQuODU5Mzc1IDM4Mi4zMzk4NDQgQyAxMzkuMDM5MDYzIDM4NS45MDIzNDQgMTQzLjM2NzE4OCAzODkuMjkyOTY5IDE0Ny44MjgxMjUgMzkyLjUgQyAxNTAuNTQ2ODc1IDM5NC40NTMxMjUgMTUzLjMxMjUgMzk2LjMzNTkzOCAxNTYuMTI1IDM5OC4xNTIzNDQgQyAxNTYuMTI1IDM5OC4xNTIzNDQgMTU2LjEyNSAzOTguMTUyMzQ0IDE1Ni4xMjg5MDYgMzk4LjE1MjM0NCBDIDE1Ni41MjczNDQgMzk4LjA1NDY4OCAxNzkgMzkyLjU4MjAzMSAxOTEuNjIxMDk0IDM5Ni45MDYyNSBDIDIxMC4wNzQyMTkgNDAzLjIyMjY1NiAyMjkuNjk1MzEzIDQxNC4zOTg0MzggMjYyLjkyOTY4OCA0MTQuNTExNzE5IEMgMjYzLjgwNDY4OCA0MTQuNTExNzE5IDI2NC42NjQwNjMgNDE0LjUwNzgxMyAyNjUuNTA3ODEzIDQxNC40OTYwOTQgQyAyNjUuNzgxMjUgNDE0LjQ5NjA5NCAyNjYuMDQyOTY5IDQxNC40ODgyODEgMjY2LjMxMjUgNDE0LjQ4MDQ2OSBDIDI2Ni44Nzg5MDYgNDE0LjQ3MjY1NiAyNjcuNDQ5MjE5IDQxNC40NjA5MzggMjY4LjAwMzkwNiA0MTQuNDQ1MzEzIEMgMjY4LjMxMjUgNDE0LjQzNzUgMjY4LjYxNzE4OCA0MTQuNDI1NzgxIDI2OC45MjU3ODEgNDE0LjQxNDA2MyBDIDI2OS40MjE4NzUgNDE0LjM5ODQzOCAyNjkuOTIxODc1IDQxNC4zODI4MTMgMjcwLjQxMDE1NiA0MTQuMzU5Mzc1IEMgMjcwLjczNDM3NSA0MTQuMzQ3NjU2IDI3MS4wNTA3ODEgNDE0LjMyODEyNSAyNzEuMzY3MTg4IDQxNC4zMTI1IEMgMjcxLjgyNDIxOSA0MTQuMjg5MDYzIDI3Mi4yODEyNSA0MTQuMjY1NjI1IDI3Mi43MzA0NjkgNDE0LjIzODI4MSBDIDI3My4wNTQ2ODggNDE0LjIxODc1IDI3My4zNzUgNDE0LjE5NTMxMyAyNzMuNjk1MzEzIDQxNC4xNzU3ODEgQyAyNzQuMTI1IDQxNC4xNDQ1MzEgMjc0LjU1NDY4OCA0MTQuMTE3MTg4IDI3NC45NzY1NjMgNDE0LjA4NTkzOCBDIDI3NS4yOTI5NjkgNDE0LjA2MjUgMjc1LjYwNTQ2OSA0MTQuMDM1MTU2IDI3NS45MjE4NzUgNDE0LjAwNzgxMyBDIDI3Ni4zMjgxMjUgNDEzLjk3MjY1NiAyNzYuNzM4MjgxIDQxMy45Mzc1IDI3Ny4xMzY3MTkgNDEzLjkwMjM0NCBDIDI3Ny40NDkyMTkgNDEzLjg3MTA5NCAyNzcuNzU3ODEzIDQxMy44Mzk4NDQgMjc4LjA2NjQwNiA0MTMuODA4NTk0IEMgMjc4LjQ1MzEyNSA0MTMuNzY5NTMxIDI3OC44NDM3NSA0MTMuNzMwNDY5IDI3OS4yMjI2NTYgNDEzLjY4NzUgQyAyNzkuNTI3MzQ0IDQxMy42NTYyNSAyNzkuODMyMDMxIDQxMy42MjEwOTQgMjgwLjEzMjgxMyA0MTMuNTgyMDMxIEMgMjgwLjUwMzkwNiA0MTMuNTM5MDYzIDI4MC44NzEwOTQgNDEzLjQ5NjA5NCAyODEuMjM0Mzc1IDQxMy40NDkyMTkgQyAyODEuNTMxMjUgNDEzLjQxMDE1NiAyODEuODI4MTI1IDQxMy4zNzEwOTQgMjgyLjEyMTA5NCA0MTMuMzMyMDMxIEMgMjgyLjQ3NjU2MyA0MTMuMjg1MTU2IDI4Mi44MjQyMTkgNDEzLjIzODI4MSAyODMuMTcxODc1IDQxMy4xODc1IEMgMjgzLjQ2MDkzOCA0MTMuMTQ0NTMxIDI4My43NSA0MTMuMTAxNTYzIDI4NC4wMzUxNTYgNDEzLjA1ODU5NCBDIDI4NC4zNzUgNDEzLjAwNzgxMyAyODQuNzEwOTM4IDQxMi45NTcwMzEgMjg1LjA0Mjk2OSA0MTIuOTAyMzQ0IEMgMjg1LjMyMDMxMyA0MTIuODU1NDY5IDI4NS42MDE1NjMgNDEyLjgxMjUgMjg1Ljg3NSA0MTIuNzY1NjI1IEMgMjg2LjIwMzEyNSA0MTIuNzEwOTM4IDI4Ni41MjM0MzggNDEyLjY1MjM0NCAyODYuODQ3NjU2IDQxMi41OTc2NTYgQyAyODcuMTE3MTg4IDQxMi41NDY4NzUgMjg3LjM4NjcxOSA0MTIuNSAyODcuNjUyMzQ0IDQxMi40NDkyMTkgQyAyODcuOTY0ODQ0IDQxMi4zOTQ1MzEgMjg4LjI3MzQzOCA0MTIuMzMyMDMxIDI4OC41ODIwMzEgNDEyLjI3MzQzOCBDIDI4OC44NDM3NSA0MTIuMjIyNjU2IDI4OS4xMDU0NjkgNDEyLjE3MTg3NSAyODkuMzYzMjgxIDQxMi4xMjEwOTQgQyAyODkuNjY0MDYzIDQxMi4wNTg1OTQgMjg5Ljk2MDkzOCA0MTEuOTk2MDk0IDI5MC4yNTM5MDYgNDExLjkzMzU5NCBDIDI5MC41MDc4MTMgNDExLjg3ODkwNiAyOTAuNzYxNzE5IDQxMS44MjgxMjUgMjkxLjAxMTcxOSA0MTEuNzczNDM4IEMgMjkxLjMwMDc4MSA0MTEuNzEwOTM4IDI5MS41ODIwMzEgNDExLjY0NDUzMSAyOTEuODY3MTg4IDQxMS41ODIwMzEgQyAyOTIuMTA5Mzc1IDQxMS41MjczNDQgMjkyLjM1NTQ2OSA0MTEuNDcyNjU2IDI5Mi41OTc2NTYgNDExLjQxNDA2MyBDIDI5Mi44Nzg5MDYgNDExLjM0NzY1NiAyOTMuMTUyMzQ0IDQxMS4yODEyNSAyOTMuNDI5Njg4IDQxMS4yMTQ4NDQgQyAyOTMuNjYwMTU2IDQxMS4xNTYyNSAyOTMuODk0NTMxIDQxMS4xMDE1NjMgMjk0LjEyNSA0MTEuMDQyOTY5IEMgMjk0LjQwMjM0NCA0MTAuOTc2NTYzIDI5NC42NzE4NzUgNDEwLjkwNjI1IDI5NC45NDE0MDYgNDEwLjgzNTkzOCBDIDI5NS4xNjAxNTYgNDEwLjc3NzM0NCAyOTUuMzgyODEzIDQxMC43MjI2NTYgMjk1LjU5NzY1NiA0MTAuNjY3OTY5IEMgMjk1LjkxMDE1NiA0MTAuNTgyMDMxIDI5Ni4yMTQ4NDQgNDEwLjUgMjk2LjUxOTUzMSA0MTAuNDE0MDYzIEMgMjk2LjkwMjM0NCA0MTAuMzEyNSAyOTcuMjczNDM4IDQxMC4yMDcwMzEgMjk3LjY0MDYyNSA0MTAuMTAxNTYzIEMgMjk3Ljg3ODkwNiA0MTAuMDM1MTU2IDI5OC4xMTcxODggNDA5Ljk2ODc1IDI5OC4zNDc2NTYgNDA5Ljg5ODQzOCBDIDI5OC41NzQyMTkgNDA5LjgzMjAzMSAyOTguNzk2ODc1IDQwOS43NjU2MjUgMjk5LjAxOTUzMSA0MDkuNjk5MjE5IEMgMjk5LjIzNDM3NSA0MDkuNjM2NzE5IDI5OS40NTcwMzEgNDA5LjU3MDMxMyAyOTkuNjY3OTY5IDQwOS41MDM5MDYgQyAyOTkuODg2NzE5IDQwOS40NDE0MDYgMzAwLjA5NzY1NiA0MDkuMzc1IDMwMC4zMTI1IDQwOS4zMDg1OTQgQyAzMDAuNTIzNDM4IDQwOS4yNDIxODggMzAwLjczODI4MSA0MDkuMTc1NzgxIDMwMC45NDUzMTMgNDA5LjEwOTM3NSBDIDMwMS4xNTIzNDQgNDA5LjA0Njg3NSAzMDEuMzUxNTYzIDQwOC45ODA0NjkgMzAxLjU1NDY4OCA0MDguOTE3OTY5IEMgMzAxLjc2NTYyNSA0MDguODQ3NjU2IDMwMS45ODA0NjkgNDA4Ljc4MTI1IDMwMi4xODc1IDQwOC43MTQ4NDQgQyAzMDIuMzc1IDQwOC42NTIzNDQgMzAyLjU1ODU5NCA0MDguNTkzNzUgMzAyLjc0MjE4OCA0MDguNTMxMjUgQyAzMDIuOTY0ODQ0IDQwOC40NjA5MzggMzAzLjE4MzU5NCA0MDguMzg2NzE5IDMwMy40MDIzNDQgNDA4LjMxNjQwNiBDIDMwMy41NTg1OTQgNDA4LjI2NTYyNSAzMDMuNzE0ODQ0IDQwOC4yMTA5MzggMzAzLjg2NzE4OCA0MDguMTYwMTU2IEMgMzA0LjEyMTA5NCA0MDguMDc0MjE5IDMwNC4zNzUgNDA3Ljk5MjE4OCAzMDQuNjI1IDQwNy45MDYyNSBDIDMwNC43MTQ4NDQgNDA3Ljg3NSAzMDQuODA0Njg4IDQwNy44NDc2NTYgMzA0Ljg5NDUzMSA0MDcuODE2NDA2IEMgMzA3LjU4OTg0NCA0MDYuOTAyMzQ0IDMwOS45Njg3NSA0MDYuMDU4NTk0IDMxMi4xNzE4NzUgNDA1LjQxNDA2MyBDIDMxMi42NTIzNDQgNDA1LjI4OTA2MyAzMTMuMTMyODEzIDQwNS4xNTYyNSAzMTMuNjA5Mzc1IDQwNS4wMTk1MzEgQyAzMTMuNjMyODEzIDQwNS4wMTE3MTkgMzEzLjY1NjI1IDQwNS4wMDM5MDYgMzEzLjY4MzU5NCA0MDQuOTk2MDk0IEMgMzEzLjczMDQ2OSA0MDQuOTg0Mzc1IDMxMy43ODEyNSA0MDQuOTcyNjU2IDMxMy44MjgxMjUgNDA0Ljk2MDkzOCBDIDMxNC4xNzk2ODggNDA0Ljg3MTA5NCAzMTQuNTQyOTY5IDQwNC43NjU2MjUgMzE0LjkxMDE1NiA0MDQuNjQ4NDM4IEMgMzE0LjkyNTc4MSA0MDQuNjQ0NTMxIDMxNC45MzM1OTQgNDA0LjY0NDUzMSAzMTQuOTQ5MjE5IDQwNC42NDA2MjUgQyAzMTQuOTYwOTM4IDQwNC42MzY3MTkgMzE0Ljk3NjU2MyA0MDQuNjI4OTA2IDMxNC45ODgyODEgNDA0LjYyNSBDIDMxNC45OTYwOTQgNDA0LjYyMTA5NCAzMTUuMDA3ODEzIDQwNC42MjEwOTQgMzE1LjAxMTcxOSA0MDQuNjE3MTg4IEMgMzE1LjMyNDIxOSA0MDQuNTE1NjI1IDMxNS42NDQ1MzEgNDA0LjQwNjI1IDMxNS45NzI2NTYgNDA0LjI4OTA2MyBDIDMxNS45OTIxODggNDA0LjI4NTE1NiAzMTYuMDExNzE5IDQwNC4yNzczNDQgMzE2LjAzMTI1IDQwNC4yNjk1MzEgQyAzMTYuMzU1NDY5IDQwNC4xNTIzNDQgMzE2LjY4MzU5NCA0MDQuMDI3MzQ0IDMxNy4wMTU2MjUgNDAzLjg5ODQzOCBDIDMxNy4wNDY4NzUgNDAzLjg4NjcxOSAzMTcuMDc0MjE5IDQwMy44NzUgMzE3LjEwNTQ2OSA0MDMuODYzMjgxIEMgMzE3LjQyOTY4OCA0MDMuNzM4MjgxIDMxNy43NjE3MTkgNDAzLjYwMTU2MyAzMTguMDk3NjU2IDQwMy40NjA5MzggQyAzMTguMTQ0NTMxIDQwMy40NDE0MDYgMzE4LjE5MTQwNiA0MDMuNDI1NzgxIDMxOC4yMzgyODEgNDAzLjQwMjM0NCBDIDMxOC41NTQ2ODggNDAzLjI3MzQzOCAzMTguODc1IDQwMy4xMzY3MTkgMzE5LjE5OTIxOSA0MDMgQyAzMTkuMzA0Njg4IDQwMi45NTMxMjUgMzE5LjQwNjI1IDQwMi45MTAxNTYgMzE5LjUxMTcxOSA0MDIuODY3MTg4IEMgMzE5LjczODI4MSA0MDIuNzY5NTMxIDMxOS45NzI2NTYgNDAyLjY2Nzk2OSAzMjAuMjAzMTI1IDQwMi41NjY0MDYgQyAzMjQuNDI5Njg4IDQwMC43MzQzNzUgMzI5LjY3OTY4OCAzOTguMzUxNTYzIDMzNi40Njg3NSAzOTYuNTQyOTY5IEMgMzM2LjQ3NjU2MyAzOTYuNTQyOTY5IDMzNi40ODQzNzUgMzk2LjUzOTA2MyAzMzYuNDkyMTg4IDM5Ni41MzkwNjMgQyAzMzcuMTQwNjI1IDM5Ni4zNjcxODggMzM3LjgwMDc4MSAzOTYuMTk5MjE5IDMzOC40NzY1NjMgMzk2LjAzOTA2MyBDIDMzOC40ODgyODEgMzk2LjAzOTA2MyAzMzguNDk2MDk0IDM5Ni4wMzUxNTYgMzM4LjUwNzgxMyAzOTYuMDMxMjUgQyAzMzguNTE1NjI1IDM5Ni4wMzEyNSAzMzguNTIzNDM4IDM5Ni4wMzEyNSAzMzguNTMxMjUgMzk2LjAyNzM0NCBDIDMzOS4xMDE1NjMgMzk1Ljg5NDUzMSAzMzkuNjgzNTk0IDM5NS43NjE3MTkgMzQwLjI3NzM0NCAzOTUuNjM2NzE5IEMgMzQwLjMwMDc4MSAzOTUuNjMyODEzIDM0MC4zMjgxMjUgMzk1LjYyNSAzNDAuMzU1NDY5IDM5NS42MjEwOTQgQyAzNDIuMTYwMTU2IDM5NS4yMzgyODEgMzQ0LjA2NjQwNiAzOTQuOTA2MjUgMzQ2LjA3NDIxOSAzOTQuNjQwNjI1IEMgMzQ2LjEwOTM3NSAzOTQuNjM2NzE5IDM0Ni4xNDQ1MzEgMzk0LjYyODkwNiAzNDYuMTc5Njg4IDM5NC42MjUgQyAzNDYuODE2NDA2IDM5NC41NDI5NjkgMzQ3LjQ2NDg0NCAzOTQuNDY0ODQ0IDM0OC4xMjUgMzk0LjM5NDUzMSBDIDM0OC4xOTE0MDYgMzk0LjM4NjcxOSAzNDguMjYxNzE5IDM5NC4zNzg5MDYgMzQ4LjMyODEyNSAzOTQuMzcxMDk0IEMgMzQ4Ljk4NDM3NSAzOTQuMzA0Njg4IDM0OS42NDQ1MzEgMzk0LjI0MjE4OCAzNTAuMzIwMzEzIDM5NC4xODc1IEMgMzUwLjM3ODkwNiAzOTQuMTgzNTk0IDM1MC40NDE0MDYgMzk0LjE3OTY4OCAzNTAuNTAzOTA2IDM5NC4xNzU3ODEgQyAzNTEuODg2NzE5IDM5NC4wNjY0MDYgMzUzLjMyMDMxMyAzOTMuOTkyMTg4IDM1NC43OTY4NzUgMzkzLjk0OTIxOSBDIDM1NC44NjcxODggMzkzLjk0OTIxOSAzNTQuOTM3NSAzOTMuOTQ1MzEzIDM1NS4wMDc4MTMgMzkzLjk0NTMxMyBDIDM1NS43MDMxMjUgMzkzLjkyOTY4OCAzNTYuNDE0MDYzIDM5My45MTc5NjkgMzU3LjEzMjgxMyAzOTMuOTE3OTY5IEMgMzU3LjI1MzkwNiAzOTMuOTE3OTY5IDM1Ny4zNzUgMzkzLjkxNzk2OSAzNTcuNSAzOTMuOTE3OTY5IEMgMzU4LjIwMzEyNSAzOTMuOTIxODc1IDM1OC45MTc5NjkgMzkzLjkyOTY4OCAzNTkuNjQwNjI1IDM5My45NDkyMTkgQyAzNTkuNzczNDM4IDM5My45NTMxMjUgMzU5LjkwNjI1IDM5My45NTcwMzEgMzYwLjAzOTA2MyAzOTMuOTYwOTM4IEMgMzYwLjc3NzM0NCAzOTMuOTg0Mzc1IDM2MS41MjczNDQgMzk0LjAxMTcxOSAzNjIuMjg1MTU2IDM5NC4wNTQ2ODggQyAzNjIuMzc4OTA2IDM5NC4wNTg1OTQgMzYyLjQ3MjY1NiAzOTQuMDY2NDA2IDM2Mi41NjY0MDYgMzk0LjA3MDMxMyBDIDM2My4zMDg1OTQgMzk0LjExMzI4MSAzNjQuMDY2NDA2IDM5NC4xNjAxNTYgMzY0LjgzMjAzMSAzOTQuMjIyNjU2IEMgMzY0LjkxNDA2MyAzOTQuMjI2NTYzIDM2NC45OTYwOTQgMzk0LjIzNDM3NSAzNjUuMDc4MTI1IDM5NC4yMzgyODEgQyAzNjUuODYzMjgxIDM5NC4zMDQ2ODggMzY2LjY1NjI1IDM5NC4zNzg5MDYgMzY3LjQ2NDg0NCAzOTQuNDYwOTM4IEMgMzY3LjYxNzE4OCAzOTQuNDc2NTYzIDM2Ny43NzM0MzggMzk0LjQ5MjE4OCAzNjcuOTI5Njg4IDM5NC41MTE3MTkgQyAzNjguNzE0ODQ0IDM5NC41OTM3NSAzNjkuNTExNzE5IDM5NC42ODc1IDM3MC4zMjAzMTMgMzk0Ljc5Mjk2OSBDIDM3MC40ODgyODEgMzk0LjgxNjQwNiAzNzAuNjYwMTU2IDM5NC44MzU5MzggMzcwLjgyODEyNSAzOTQuODU5Mzc1IEMgMzcxLjY1MjM0NCAzOTQuOTcyNjU2IDM3Mi40ODQzNzUgMzk1LjA4OTg0NCAzNzMuMzI4MTI1IDM5NS4yMjI2NTYgQyAzNzMuNDY0ODQ0IDM5NS4yNDIxODggMzczLjYwMTU2MyAzOTUuMjY1NjI1IDM3My43MzgyODEgMzk1LjI4NTE1NiBDIDM3NC42MzY3MTkgMzk1LjQyOTY4OCAzNzUuNTQ2ODc1IDM5NS41ODIwMzEgMzc2LjQ3MjY1NiAzOTUuNzUgQyAzNzkuMTk5MjE5IDM5My45MDIzNDQgMzgxLjg3NSAzOTEuOTkyMTg4IDM4NC41MDM5MDYgMzkwLjAyMzQzOCBDIDM4OC41MzkwNjMgMzg2Ljk4ODI4MSAzOTIuNDUzMTI1IDM4My44MTY0MDYgMzk2LjI0MjE4OCAzODAuNDg4MjgxIEMgMzg4LjE3NTc4MSAzNzguMjY5NTMxIDM3OS45MzM1OTQgMzc3LjA4NTkzOCAzNzEuODU1NDY5IDM3Ni42NDg0MzggQyAzNzEuMDgyMDMxIDM3Ni42MDkzNzUgMzcwLjMwODU5NCAzNzYuNTc0MjE5IDM2OS41MzUxNTYgMzc2LjU0Njg3NSAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigzLjQ5ODg0JSwyNi42OTk4MjklLDQxLjU5ODUxMSUpO2ZpbGwtb3BhY2l0eToxOyIgZD0iTSAyMDcuNjAxNTYzIDI4NC43MTQ4NDQgTCAyMDIuNDEwMTU2IDI4NC43MTQ4NDQgTCAyMDIuNDEwMTU2IDI3OS41MTk1MzEgTCAyMDcuNjAxNTYzIDI3OS41MTk1MzEgWiBNIDIwNy42MDE1NjMgMjkxLjg0Mzc1IEwgMjAyLjQxMDE1NiAyOTEuODQzNzUgTCAyMDIuNDEwMTU2IDI4Ni42NDg0MzggTCAyMDcuNjAxNTYzIDI4Ni42NDg0MzggWiBNIDIwMC4zOTQ1MzEgMjg0LjcxNDg0NCBMIDE5NS4yMDMxMjUgMjg0LjcxNDg0NCBMIDE5NS4yMDMxMjUgMjc5LjUxOTUzMSBMIDIwMC4zOTQ1MzEgMjc5LjUxOTUzMSBaIE0gMjAwLjM5NDUzMSAyOTEuODQzNzUgTCAxOTUuMjAzMTI1IDI5MS44NDM3NSBMIDE5NS4yMDMxMjUgMjg2LjY0ODQzOCBMIDIwMC4zOTQ1MzEgMjg2LjY0ODQzOCBaIE0gMjM3LjA3MDMxMyAyNzguNzEwOTM4IEwgMjEyLjM1NTQ2OSAyNTguODYzMjgxIEwgMTgzLjcxODc1IDI3OS41OTc2NTYgTCAxOTAuMjkyOTY5IDI3OS41OTc2NTYgTCAxOTAuMjkyOTY5IDMwNC4zNDc2NTYgQyAyMDEuOTMzNTk0IDMwNy43NDYwOTQgMjE0LjkxNDA2MyAzMTAuMDk3NjU2IDIyOC40NDUzMTMgMzExLjUzOTA2MyBMIDIyOC40NDUzMTMgMjc4LjcxMDkzOCBMIDIzNy4wNzAzMTMgMjc4LjcxMDkzOCAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMDAlLDEwMCUsMTAwJSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDE5NS4yMDMxMjUgMjg0LjcxNDg0NCBMIDIwMC4zOTQ1MzEgMjg0LjcxNDg0NCBMIDIwMC4zOTQ1MzEgMjc5LjUxOTUzMSBMIDE5NS4yMDMxMjUgMjc5LjUxOTUzMSBMIDE5NS4yMDMxMjUgMjg0LjcxNDg0NCAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMDAlLDEwMCUsMTAwJSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDIwMi40MTAxNTYgMjg0LjcxNDg0NCBMIDIwNy42MDE1NjMgMjg0LjcxNDg0NCBMIDIwNy42MDE1NjMgMjc5LjUxOTUzMSBMIDIwMi40MTAxNTYgMjc5LjUxOTUzMSBMIDIwMi40MTAxNTYgMjg0LjcxNDg0NCAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMDAlLDEwMCUsMTAwJSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDE5NS4yMDMxMjUgMjkxLjg0Mzc1IEwgMjAwLjM5NDUzMSAyOTEuODQzNzUgTCAyMDAuMzk0NTMxIDI4Ni42NDg0MzggTCAxOTUuMjAzMTI1IDI4Ni42NDg0MzggTCAxOTUuMjAzMTI1IDI5MS44NDM3NSAiLz4KPHBhdGggc3R5bGU9IiBzdHJva2U6bm9uZTtmaWxsLXJ1bGU6bm9uemVybztmaWxsOnJnYigxMDAlLDEwMCUsMTAwJSk7ZmlsbC1vcGFjaXR5OjE7IiBkPSJNIDIwMi40MTAxNTYgMjkxLjg0Mzc1IEwgMjA3LjYwMTU2MyAyOTEuODQzNzUgTCAyMDcuNjAxNTYzIDI4Ni42NDg0MzggTCAyMDIuNDEwMTU2IDI4Ni42NDg0MzggTCAyMDIuNDEwMTU2IDI5MS44NDM3NSAiLz4KPC9nPgo8L3N2Zz4K";
function getLogoUrl(){ return state.instansi.logo || DEFAULT_LOGO; }

const CATEGORIES = [
  {
    id:'korespondensi',
    label:'Naskah Dinas Korespondensi',
    desc:'Surat menyurat untuk komunikasi kedinasan, ke dalam maupun ke luar instansi.',
    types:['dinas','nota']
  },
  {
    id:'penugasan',
    label:'Naskah Dinas Penugasan',
    desc:'Menugaskan pejabat/pegawai melaksanakan kegiatan kedinasan tertentu.',
    types:['tugas','spd']
  },
  {
    id:'penetapan',
    label:'Naskah Dinas Penetapan',
    desc:'Menetapkan status, kebijakan, atau kedudukan hukum secara resmi.',
    types:['sk']
  },
  {
    id:'arahan',
    label:'Naskah Dinas Arahan',
    desc:'Memuat kebijakan atau instruksi yang bersifat mengatur dan berlaku umum.',
    types:['edaran']
  },
  {
    id:'khusus',
    label:'Naskah Dinas Khusus',
    desc:'Bentuk naskah dinas lain di luar kategori korespondensi, penetapan, dan penugasan.',
    types:['undangan','pengumuman']
  },
  {
    id:'kepegawaian',
    label:'Naskah Kepegawaian',
    desc:'Naskah terkait pengelolaan karier dan penggajian pegawai.',
    types:['pak','kgb','pltplh']
  },
];

const TYPES = {
  dinas:{ name:'Surat Dinas', short:'SD', desc:'Surat resmi kepada pihak eksternal (permohonan, pemberitahuan, konfirmasi, dsb.)' },
  nota:{ name:'Nota Dinas', short:'ND', desc:'Komunikasi tertulis internal antar pejabat atau unit kerja' },
  tugas:{ name:'Surat Tugas', short:'ST', desc:'Penugasan pegawai untuk melaksanakan kegiatan tertentu' },
  spd:{ name:'Surat Perjalanan Dinas (SPD)', short:'SPD', desc:'Otorisasi resmi perjalanan dinas pegawai beserta rincian pembiayaannya' },
  sk:{ name:'Surat Keputusan', short:'SK', desc:'Penetapan kebijakan, status, atau susunan secara resmi' },
  edaran:{ name:'Surat Edaran', short:'SE', desc:'Pemberitahuan atau instruksi yang berlaku umum bagi banyak pihak' },
  undangan:{ name:'Surat Undangan', short:'SU', desc:'Mengundang pihak lain untuk hadir pada acara kedinasan' },
  pengumuman:{ name:'Pengumuman', short:'PU', desc:'Informasi resmi untuk diketahui secara luas' },
  pak:{ name:'Penetapan Angka Kredit', short:'PAK', desc:'Penetapan angka kredit sebagai dasar kenaikan pangkat/jabatan fungsional' },
  kgb:{ name:'Kenaikan Gaji Berkala', short:'KGB', desc:'Pemberitahuan kenaikan gaji berkala pegawai sesuai masa kerja golongan' },
  pltplh:{ name:'Usulan Plt./Plh.', short:'PLT', desc:'Usulan penunjukan Pelaksana Tugas atau Pelaksana Harian pada jabatan yang lowong/berhalangan' },
};

/* Kode jenis naskah dinas sesuai Permen ATR/BPN No. 9 Tahun 2018 tentang
   Pedoman Tata Naskah Dinas di Lingkungan Kementerian ATR/BPN (kode
   penomoran: ND=Nota Dinas, ST=Surat Tugas, SK=Keputusan, SE=Surat Edaran).
   Surat Dinas/Undangan/Pengumuman/PAK/KGB tidak memiliki kode baku pada
   lampiran tersebut, sehingga hanya memakai kode wilayah & klasifikasi. */
const KODE_JENIS_BPN = { dinas:'', nota:'ND', tugas:'ST', sk:'SK', edaran:'SE', undangan:'', pengumuman:'', pak:'', kgb:'', pltplh:'' };
const BULAN_ROMAWI = ['I','II','III','IV','V','VI','VII','VIII','IX','X','XI','XII'];

/* Definisi field per jenis surat. type: text | textarea | date | select | list | petugas */
const FIELD_DEFS = {
  dinas:[
    {k:'nomor', label:'Nomor Surat', type:'text', ph:'37/33.20.UM.01.01/VIII/2026', required:true},
    {k:'sifat', label:'Sifat', type:'select', options:['Biasa','Penting','Segera','Rahasia'], required:true},
    {k:'lampiran', label:'Lampiran (opsional)', type:'text', ph:'Kosongkan bila tidak ada lampiran', hint:'Baris Lampiran hanya muncul di surat bila diisi.'},
    {k:'hal', label:'Perihal', type:'text', ph:'Permohonan Informasi Data Aset Pemerintah Daerah', required:true},
    {k:'tanggal', label:'Tanggal Surat', type:'date', required:true},
    {k:'tujuanJabatan', label:'Ditujukan kepada (Yth.)', type:'text', ph:'Sekretaris Daerah Kabupaten Jepara', required:true},
    {k:'tujuanAlamat', label:'Kota/Alamat Tujuan', type:'text', ph:'Kosongkan jika ingin memakai "di Tempat"'},
    {k:'konteks', label:'Konteks / Latar Belakang Singkat', type:'textarea', ph:'mis. dalam upaya mewujudkan Data Spasial Pertanahan berbasis elektronik yang up to date', hint:'Disusun menjadi kalimat pembuka: "Sehubungan (konteks), bersama ini kami sampaikan hal-hal sebagai berikut :"', required:true},
    {k:'poinIsi', label:'Poin Isi Surat', type:'list', ph:'mis. Mendasari Surat Keputusan ... tentang ...', hint:'Setiap poin akan disusun menjadi paragraf berpenomoran 1, 2, 3 ...', required:true},
    {k:'penutup', label:'Kalimat Penutup (opsional)', type:'textarea', ph:'Kosongkan untuk memakai kalimat penutup baku'},
    {k:'tembusan', label:'Tembusan (opsional)', type:'list', ph:'mis. Bupati Kabupaten Jepara'},
  ],
  nota:[
    {k:'kepada', label:'Kepada', type:'text', ph:'Daftar Petugas Terlampir', required:true},
    {k:'dari', label:'Dari', type:'text', ph:'Kepala Kantor Pertanahan Kabupaten Jepara', required:true},
    {k:'tanggal', label:'Tanggal', type:'text', ph:'April 2026', hint:'Boleh berupa tanggal lengkap atau periode singkat (mis. "April 2026").', required:true},
    {k:'nomor', label:'Nomor', type:'text', ph:'47/ND-33.20.UP.02.03/III/2026', required:true},
    {k:'hal', label:'Perihal', type:'text', ph:'Jadwal APEL Bulan April 2026', required:true},
    {k:'sifat', label:'Sifat (opsional)', type:'select', options:['','Biasa','Penting','Segera','Rahasia'], hint:'Kosongkan bila tidak perlu dicantumkan.'},
    {k:'lampiran', label:'Lampiran (opsional)', type:'text', ph:'Kosongkan bila tidak ada lampiran'},
    {k:'poinIsi', label:'Isi Nota Dinas', type:'list', ph:'mis. Sehubungan dengan pelaksanaan Kegiatan APEL pagi bulan April Tahun 2026 bersama ini disampaikan Jadwal Petugas APEL, agar semua petugas dapat melaksanakan kegiatan dimaksud.', hint:'Isi satu poin saja untuk paragraf mengalir biasa, atau beberapa poin untuk daftar berhuruf a, b, c ...', required:true},
    {k:'penutup', label:'Kalimat Penutup (opsional)', type:'textarea', ph:'Kosongkan untuk memakai kalimat penutup baku "Demikian untuk dapat ditaati dan dilaksanakan. Terima kasih."'},
  ],
  tugas:[
    {k:'nomor', label:'Nomor Surat Tugas', type:'text', ph:'176/ST-33.20.PP.02.03/VI/2026', required:true, group:'Data Surat'},
    {k:'tanggal', label:'Tanggal Surat Diterbitkan', type:'date', required:true, group:'Data Surat'},

    {k:'menimbang', label:'Menimbang', type:'list', ph:'mis. berdasarkan Surat dari ... Nomor ... tanggal ... perihal ...', hint:'Setiap poin diberi huruf a, b, c.', group:'Menimbang & Dasar'},
    {k:'dasar', label:'Dasar Hukum', type:'list', ph:'mis. Peraturan Presiden Nomor ... Tahun ... tentang ...', hint:'Setiap poin diberi angka 1, 2, 3.', group:'Menimbang & Dasar'},

    {k:'petugas', label:'Pegawai yang Ditugaskan', type:'petugas', required:true, group:'Memberi Tugas'},
    {k:'tugasPoin', label:'Untuk (Uraian Tugas)', type:'list', ph:'mis. Mengikuti Pelatihan ... selama 5 (lima) hari kerja pada tanggal ... bertempat di ...', hint:'Setiap poin diberi angka 1, 2, 3 — uraian kegiatan, pembebanan biaya, kewajiban pelaporan, dsb.', required:true, group:'Memberi Tugas'},

    {k:'anJabatan', label:'Atas Nama (An.) — opsional', type:'text', ph:'Kepala Kantor Pertanahan Kabupaten Jepara', hint:'Isi bila surat ditandatangani atas nama pejabat lain (pola "An. ...").', group:'Penandatangan'},
    {k:'penandatanganJabatan', label:'Jabatan Penandatangan', type:'text', ph:'Kepala Sub Bagian Tata Usaha', hint:'Kosongkan untuk memakai Jabatan Penandatangan default dari Profil Instansi.', group:'Penandatangan'},
    {k:'penandatanganNama', label:'Nama Penandatangan (opsional)', type:'text', hint:'Kosongkan untuk memakai default Profil Instansi.', group:'Penandatangan'},
    {k:'penandatanganNip', label:'NIP Penandatangan (opsional)', type:'text', group:'Penandatangan'},
  ],
  spd:[
    {k:'nomor', label:'Nomor SPD', type:'text', ph:'SPD/176/2026', required:true, group:'Data Umum'},
    {k:'lembarKe', label:'Lembar Ke', type:'text', ph:'1', group:'Data Umum'},
    {k:'kodeNomor', label:'Kode Nomor (opsional)', type:'text', group:'Data Umum'},
    {k:'satuanKerja', label:'Satuan Kerja', type:'text', ph:'Kantor Pertanahan Kabupaten Jepara', required:true, group:'Data Umum'},
    {k:'tanggal', label:'Tanggal Dikeluarkan', type:'date', required:true, group:'Data Umum'},

    {k:'ppkNama', label:'Nama Pejabat Pembuat Komitmen', type:'text', ph:'INDAH SETYO MARTIYANTI, S.SiT', required:true, group:'Pejabat Pembuat Komitmen'},
    {k:'ppkNip', label:'NIP PPK', type:'text', ph:'19730314 199403 2 002', group:'Pejabat Pembuat Komitmen'},
    {k:'ppkJabatan', label:'Jabatan PPK (opsional)', type:'text', ph:'Kepala Sub Bagian Tata Usaha', group:'Pejabat Pembuat Komitmen'},
    {k:'anJabatan', label:'Atas Nama (An.) — opsional', type:'text', ph:'Kepala Kantor Pertanahan Kabupaten Jepara', hint:'Isi bila PPK menandatangani atas nama pejabat lain.', group:'Pejabat Pembuat Komitmen'},

    {k:'_pegawaiPicker', label:'Pegawai yang Melaksanakan Perjalanan', type:'pegawaiFill', group:'Data Pegawai'},
    {k:'pegawaiNama', label:'Nama', type:'text', required:true, group:'Data Pegawai'},
    {k:'pegawaiNip', label:'NIP', type:'text', group:'Data Pegawai'},
    {k:'pegawaiPangkat', label:'Pangkat', type:'text', group:'Data Pegawai'},
    {k:'pegawaiGolongan', label:'Golongan', type:'text', group:'Data Pegawai'},
    {k:'pegawaiJabatan', label:'Jabatan/Instansi', type:'text', group:'Data Pegawai'},
    {k:'tingkatBiaya', label:'Tingkat Biaya Perjalanan Dinas', type:'text', ph:'C', group:'Data Pegawai'},

    {k:'maksud', label:'Maksud Perjalanan Dinas', type:'textarea', ph:'Mengikuti Pelatihan Penguatan Kapasitas Bendahara Pengeluaran ...', required:true, group:'Perjalanan'},
    {k:'alatAngkutan', label:'Alat Angkutan yang Dipergunakan', type:'text', ph:'Kendaraan Umum', group:'Perjalanan'},
    {k:'tempatBerangkat', label:'Tempat Berangkat', type:'text', ph:'Jepara', required:true, group:'Perjalanan'},
    {k:'tempatTujuan', label:'Tempat Tujuan', type:'text', ph:'Jakarta', required:true, group:'Perjalanan'},
    {k:'lamanya', label:'Lamanya Perjalanan Dinas', type:'text', ph:'5 (lima) hari', group:'Perjalanan'},
    {k:'tanggalBerangkat', label:'Tanggal Berangkat', type:'date', required:true, group:'Perjalanan'},
    {k:'tanggalKembali', label:'Tanggal Harus Kembali/Tiba di Tempat Baru', type:'date', required:true, group:'Perjalanan'},

    {k:'pengikut', label:'Pengikut (opsional)', type:'list', ph:'mis. Nama — Tanggal Lahir — Keterangan/hubungan', group:'Pengikut & Pembiayaan'},
    {k:'pembebananInstansi', label:'Pembebanan Anggaran — Instansi', type:'text', ph:'DIPA Kantor Pertanahan Kabupaten Jepara', group:'Pengikut & Pembiayaan'},
    {k:'pembebananAkun', label:'Pembebanan Anggaran — Akun (opsional)', type:'text', group:'Pengikut & Pembiayaan'},
    {k:'keteranganLain', label:'Keterangan Lain-Lain (opsional)', type:'textarea', group:'Pengikut & Pembiayaan'},
    {k:'catatanLain', label:'Catatan Lain-Lain — Bagian VII (opsional)', type:'textarea', group:'Pengikut & Pembiayaan'},
  ],
  sk:[
    {k:'judul', label:'Tentang (Judul Keputusan)', type:'text', ph:'Pembentukan Tim Kerja Digitalisasi Arsip', required:true},
    {k:'nomor', label:'Nomor Keputusan', type:'text', ph:'188/SK-33.20.UP.03.02/VIII/2026', required:true},
    {k:'menimbang', label:'Menimbang', type:'list', ph:'mis. bahwa dalam rangka ... perlu ditetapkan Tim Kerja ...', hint:'Setiap poin diawali "bahwa ..." dan diberi huruf a, b, c.', required:true},
    {k:'mengingat', label:'Mengingat (Dasar Hukum)', type:'list', ph:'mis. Undang-Undang Nomor ... Tahun ... tentang ...', required:true},
    {k:'diktum', label:'Diktum Keputusan', type:'list', ph:'mis. Membentuk Tim Kerja Digitalisasi Arsip dengan susunan sebagaimana Lampiran ...', hint:'Setiap poin menjadi KESATU, KEDUA, KETIGA, dst.', required:true},
    {k:'tanggal', label:'Tanggal Penetapan', type:'date', required:true},
    {k:'tembusan', label:'Tembusan (opsional)', type:'list', ph:'mis. Arsip'},
  ],
  edaran:[
    {k:'nomor', label:'Nomor Surat Edaran', type:'text', ph:'8/SE-33.20.UM.01.01/VIII/2026', required:true},
    {k:'tentang', label:'Tentang', type:'text', ph:'Ketentuan Jam Kerja Selama Bulan ...', required:true},
    {k:'tujuan', label:'Ditujukan kepada', type:'text', ph:'Seluruh Kepala Bidang di Lingkungan ...', required:true},
    {k:'latar', label:'Latar Belakang / Dasar', type:'textarea', ph:'mis. dalam rangka meningkatkan tertib administrasi ...', required:true},
    {k:'poinIsi', label:'Isi Edaran', type:'list', ph:'mis. Seluruh pegawai wajib ...', required:true},
    {k:'tanggal', label:'Tanggal Surat', type:'date', required:true},
  ],
  undangan:[
    {k:'nomor', label:'Nomor Surat', type:'text', ph:'5/33.20.UM.01.02/VIII/2026', required:true},
    {k:'lampiran', label:'Lampiran', type:'text', ph:'1 (satu) lembar / -'},
    {k:'acara', label:'Nama Acara', type:'text', ph:'Rapat Koordinasi Persiapan Akreditasi', required:true},
    {k:'tujuanJabatan', label:'Ditujukan kepada (Yth.)', type:'text', ph:'Para Kepala Unit Kerja', required:true},
    {k:'tujuanAlamat', label:'Alamat Tujuan', type:'text', ph:'Kosongkan jika ingin memakai "di Tempat"'},
    {k:'hari', label:'Hari, Tanggal', type:'text', ph:'Kamis, 27 Agustus 2026', required:true},
    {k:'waktu', label:'Waktu', type:'text', ph:'09.00 WIB s.d. selesai', required:true},
    {k:'tempat', label:'Tempat', type:'text', ph:'Ruang Rapat Utama, Lantai 2', required:true},
    {k:'agenda', label:'Agenda Acara', type:'list', ph:'mis. Pemaparan progres akreditasi'},
    {k:'tanggal', label:'Tanggal Surat', type:'date', required:true},
  ],
  pengumuman:[
    {k:'nomor', label:'Nomor Pengumuman', type:'text', ph:'27/33.20.UM.01.03/VIII/2026', required:true},
    {k:'tentang', label:'Tentang', type:'text', ph:'Jadwal Libur dan Cuti Bersama', required:true},
    {k:'poinIsi', label:'Isi Pengumuman', type:'list', ph:'mis. Kantor tidak melayani administrasi pada tanggal ...', required:true},
    {k:'tanggal', label:'Tanggal Pengumuman', type:'date', required:true},
  ],
  pak:[
    {k:'_pegawaiPicker', label:'Data Pegawai yang Dinilai', type:'pegawaiFill', group:'I. Keterangan Perorangan'},
    {k:'pegawaiNama', label:'Nama', type:'text', ph:'Eko Budi Setiawan', required:true, group:'I. Keterangan Perorangan'},
    {k:'pegawaiNip', label:'NIP', type:'text', ph:'198406162014081002', group:'I. Keterangan Perorangan'},
    {k:'karpeg', label:'Nomor Seri KARPEG', type:'text', ph:'B 01001436', group:'I. Keterangan Perorangan'},
    {k:'ttl', label:'Tempat dan Tanggal Lahir', type:'text', ph:'Jepara, 16 Juni 1984', group:'I. Keterangan Perorangan'},
    {k:'jenisKelamin', label:'Jenis Kelamin', type:'select', options:['Laki-Laki','Perempuan'], group:'I. Keterangan Perorangan'},
    {k:'pegawaiPangkat', label:'Pangkat', type:'text', ph:'Pengatur', group:'I. Keterangan Perorangan'},
    {k:'pegawaiGolongan', label:'Golongan Ruang', type:'text', ph:'II/c', group:'I. Keterangan Perorangan'},
    {k:'pegawaiTmtPangkat', label:'TMT Pangkat', type:'date', group:'I. Keterangan Perorangan'},
    {k:'pegawaiJabatan', label:'Jabatan Fungsional', type:'text', ph:'Surveyor Pemetaan Pemula', required:true, group:'I. Keterangan Perorangan'},
    {k:'pegawaiTmtJabatan', label:'TMT Jabatan', type:'date', group:'I. Keterangan Perorangan'},
    {k:'pegawaiUnitKerja', label:'Unit Kerja', type:'text', ph:'Kantor Pertanahan Kabupaten Jepara', group:'I. Keterangan Perorangan'},
    {k:'instansiInduk', label:'Instansi', type:'text', ph:'Kementerian Agraria dan Tata Ruang/BPN', group:'I. Keterangan Perorangan'},

    {k:'nomor', label:'Nomor Penetapan', type:'text', ph:'67.1/SK-33.20.UP.02.03/VII/2026', required:true, group:'Data Penetapan'},
    {k:'masaPenilaian', label:'Masa Penilaian', type:'text', ph:'1 Januari 2023 - 31 Juli 2026', required:true, group:'Data Penetapan'},

    {k:'akDasar', label:'AK Dasar yang diberikan', type:'akRow', group:'II. Penetapan Angka Kredit'},
    {k:'akJfLama', label:'AK JF Lama', type:'akRow', group:'II. Penetapan Angka Kredit'},
    {k:'akPenyesuaian', label:'AK Penyesuaian/Penyetaraan', type:'akRow', group:'II. Penetapan Angka Kredit'},
    {k:'akKonversi', label:'AK Konversi', type:'akRow', group:'II. Penetapan Angka Kredit'},
    {k:'akPendidikan', label:'AK dari Peningkatan Pendidikan', type:'akRow', group:'II. Penetapan Angka Kredit'},
    {k:'akLainLabel', label:'Label Komponen Lainnya (opsional)', type:'text', ph:'....**)', group:'II. Penetapan Angka Kredit'},
    {k:'akLain', label:'Komponen Lainnya', type:'akRow', group:'II. Penetapan Angka Kredit'},
    {k:'jumlahKumulatifLama', label:'Jumlah Angka Kredit Kumulatif — Lama', type:'text', ph:'38.000', group:'II. Penetapan Angka Kredit'},
    {k:'jumlahKumulatifBaru', label:'Jumlah Angka Kredit Kumulatif — Baru', type:'text', ph:'68.318', group:'II. Penetapan Angka Kredit'},
    {k:'jumlahKumulatifJumlah', label:'Jumlah Angka Kredit Kumulatif — Total', type:'text', ph:'106.318', required:true, group:'II. Penetapan Angka Kredit'},
    {k:'jumlahKumulatifKet', label:'Keterangan (opsional)', type:'text', group:'II. Penetapan Angka Kredit'},

    {k:'akMinimalPangkat', label:'AK Minimal untuk Kenaikan Pangkat', type:'text', ph:'20', group:'Keterangan Kenaikan'},
    {k:'akMinimalJenjang', label:'AK Minimal untuk Jenjang Jabatan', type:'text', ph:'60', group:'Keterangan Kenaikan'},
    {k:'akKelebihanPangkat', label:'Kelebihan AK untuk Kenaikan Pangkat', type:'text', ph:'48.318', group:'Keterangan Kenaikan'},
    {k:'akKelebihanJenjang', label:'Kelebihan AK untuk Jenjang Jabatan', type:'text', ph:'46.318', group:'Keterangan Kenaikan'},
    {k:'pertimbangan', label:'III. Pertimbangan (opsional)', type:'textarea', ph:'Dapat Dipertimbangkan untuk diberikan Kenaikan Jenjang Jabatan ... dalam Pangkat ... Golongan Ruang ...', group:'Keterangan Kenaikan'},

    {k:'pejabatPenilaiJabatan', label:'Jabatan Pejabat Penilai', type:'text', ph:'Pejabat Penilai Kinerja', default:'Pejabat Penilai Kinerja', group:'Pejabat Penilai & Tanggal'},
    {k:'pejabatPenilaiNama', label:'Nama Pejabat Penilai', type:'text', ph:'R. Drianto Eko Witjaksono Putra, S.ST., M.M.', group:'Pejabat Penilai & Tanggal'},
    {k:'pejabatPenilaiNip', label:'NIP Pejabat Penilai', type:'text', ph:'19791026 200003 1 001', group:'Pejabat Penilai & Tanggal'},
    {k:'tembusan', label:'Tembusan (opsional)', type:'list', ph:'mis. Kepala Badan Kepegawaian Negara ...', group:'Pejabat Penilai & Tanggal'},
    {k:'tanggal', label:'Tanggal Penetapan', type:'date', required:true, group:'Pejabat Penilai & Tanggal'},
  ],
  kgb:[
    {k:'_pegawaiPicker', label:'Data Pegawai', type:'pegawaiFill', group:'Data Pegawai'},
    {k:'pegawaiNama', label:'Nama', type:'text', ph:'Agus Dwi Yanto, A.Md.Kom.', required:true, group:'Data Pegawai'},
    {k:'pegawaiNip', label:'NIP', type:'text', ph:'199908272022041001', group:'Data Pegawai'},
    {k:'pegawaiPangkat', label:'Pangkat', type:'text', ph:'Pengatur', group:'Data Pegawai'},
    {k:'pegawaiGolongan', label:'Golongan', type:'text', ph:'II/c', group:'Data Pegawai'},
    {k:'pegawaiUnitKerja', label:'Unit Kerja', type:'text', ph:'Kantor Pertanahan Kabupaten Jepara', group:'Data Pegawai'},

    {k:'nomor', label:'Nomor Surat', type:'text', ph:'18/SK-33.20.UP.02.03/III/2026', required:true, group:'Data Surat'},
    {k:'sifat', label:'Sifat', type:'select', options:['Biasa','Penting','Segera','Rahasia'], group:'Data Surat'},
    {k:'lampiran', label:'Lampiran', type:'text', ph:'-', group:'Data Surat'},
    {k:'tanggal', label:'Tanggal Surat', type:'date', required:true, group:'Data Surat'},
    {k:'tujuanJabatan', label:'Ditujukan kepada (Yth.)', type:'text', ph:'Kepala Kantor Pelayanan Perbendaharaan Negara Kudus', required:true, group:'Data Surat'},
    {k:'tujuanKota', label:'Kota Tujuan (baris "Di –")', type:'text', ph:'Kudus', required:true, group:'Data Surat'},

    {k:'gajiLama', label:'Gaji Pokok Lama', type:'text', ph:'Rp. 2.564.200,-', required:true, group:'Gaji Lama & Dasar SK'},
    {k:'skLamaPejabat', label:'SK Lama — Oleh Pejabat', type:'text', ph:'Kepala Kantor Pertanahan Kabupaten Banyumas', group:'Gaji Lama & Dasar SK'},
    {k:'skLamaTglNomor', label:'SK Lama — Tanggal dan Nomor', type:'text', ph:'13 Maret 2024 dan B/UP.02/154-33.02/III/2024', group:'Gaji Lama & Dasar SK'},
    {k:'skLamaMulaiBerlaku', label:'SK Lama — Tanggal Mulai Berlaku', type:'date', group:'Gaji Lama & Dasar SK'},
    {k:'masaKerjaGolLama', label:'Masa Kerja Gol. pada Tanggal Tersebut', type:'text', ph:'5 th 0 bln', group:'Gaji Lama & Dasar SK'},

    {k:'gajiBaru', label:'Gaji Pokok Baru', type:'text', ph:'Rp. 2.645.000,-', required:true, group:'Gaji Baru'},
    {k:'masaKerjaBaru', label:'Berdasarkan Masa Kerja', type:'text', ph:'7 th 0 bln', group:'Gaji Baru'},
    {k:'tmtBaru', label:'Mulai Tanggal', type:'date', required:true, group:'Gaji Baru'},

    {k:'dasarPp', label:'Dasar Peraturan', type:'text', ph:'Peraturan Pemerintah Republik Indonesia Nomor 5 Tahun 2024 Tanggal 26 Januari 2024', default:'Peraturan Pemerintah Republik Indonesia Nomor 5 Tahun 2024 Tanggal 26 Januari 2024', group:'Dasar Hukum & Tembusan'},
    {k:'tembusan', label:'Tembusan', type:'list', defaultItems:['Bendaharawan Gaji Kantor Pertanahan Kabupaten ..., di ...','Pegawai yang bersangkutan Sdr./Sdri. ...','Arsip.'], group:'Dasar Hukum & Tembusan'},
  ],
  pltplh:[
    {k:'jenis', label:'Jenis Penunjukan', type:'select', options:['Pelaksana Tugas (Plt.)','Pelaksana Harian (Plh.)'], group:'Data Surat'},
    {k:'tipePengajuan', label:'Jenis Pengajuan', type:'select', options:['Penunjukan Awal','Perpanjangan'], hint:'Perpanjangan dipakai saat Plt./Plh. sebelumnya akan berakhir masa berlakunya — tidak memerlukan data pejabat lama.', group:'Data Surat'},
    {k:'nomor', label:'Nomor Surat', type:'text', ph:'B/UP.02.03/342-33.20/VIII/2026', required:true, group:'Data Surat'},
    {k:'sifat', label:'Sifat', type:'select', options:['Biasa','Penting','Segera','Rahasia'], hint:'Sifat "Biasa" tidak dapat dipakai untuk usulan penunjukan Plt./Plh. — pilih Penting, Segera, atau Rahasia.', group:'Data Surat'},
    {k:'lampiran', label:'Lampiran (opsional)', type:'text', ph:'1 (satu) Eksemplar', group:'Data Surat'},
    {k:'jabatanLowong', label:'Jabatan yang Diusulkan Plt./Plh.-nya', type:'text', ph:'Kepala Seksi Pengendalian dan Penanganan Sengketa Kantor Pertanahan Kabupaten Jepara', hint:'Dipakai pada baris Perihal (multi-baris otomatis).', required:true, group:'Data Surat'},
    {k:'tanggal', label:'Tanggal Surat', type:'date', required:true, group:'Data Surat'},
    {k:'tujuanJabatan', label:'Ditujukan kepada (Yth.)', type:'text', ph:'Kepala Kantor Wilayah Badan Pertanahan Nasional Provinsi Jawa Tengah', required:true, group:'Data Surat'},
    {k:'tujuanKota', label:'Kota Tujuan (baris "di –")', type:'text', ph:'Semarang', required:true, group:'Data Surat'},

    {k:'dasarSk', label:'Dasar Pengajuan', type:'textarea', ph:'Penunjukan awal, mis. "Surat Keputusan ... tentang Pemberian Pensiun ..."\nPerpanjangan, mis. "Surat Perintah Pelaksana Tugas ... Nomor ... terkait Pelaksana Tugas ... yang berakhir pertanggal ..."', hint:'Untuk penunjukan awal: SK/dasar yang menyebabkan jabatan lowong. Untuk perpanjangan: Surat Perintah Plt./Plh. sebelumnya yang akan berakhir.', required:true, group:'Dasar Pengajuan'},

    {k:'tmtLowong', label:'Terhitung Mulai Tanggal (lowong/berhalangan)', type:'date', hideWhen: d=>d.tipePengajuan==='Perpanjangan', group:'Jabatan yang Lowong/Berhalangan (Penunjukan Awal)'},
    {k:'_pegawaiPickerLama', label:'Pilih Pejabat Lama dari Data Pegawai', type:'pegawaiFill', target:'lama', hideWhen: d=>d.tipePengajuan==='Perpanjangan', group:'Jabatan yang Lowong/Berhalangan (Penunjukan Awal)'},
    {k:'lamaNama', label:'Nama', type:'text', ph:'Siti Sulistiyah, S.SiT.,M.H.', hideWhen: d=>d.tipePengajuan==='Perpanjangan', group:'Jabatan yang Lowong/Berhalangan (Penunjukan Awal)'},
    {k:'lamaNip', label:'NIP', type:'text', ph:'19680507 198903 2 005', hideWhen: d=>d.tipePengajuan==='Perpanjangan', group:'Jabatan yang Lowong/Berhalangan (Penunjukan Awal)'},
    {k:'lamaPangkat', label:'Pangkat', type:'text', ph:'Pembina Tingkat I', hideWhen: d=>d.tipePengajuan==='Perpanjangan', group:'Jabatan yang Lowong/Berhalangan (Penunjukan Awal)'},
    {k:'lamaGolongan', label:'Golongan', type:'text', ph:'IV/b', hideWhen: d=>d.tipePengajuan==='Perpanjangan', group:'Jabatan yang Lowong/Berhalangan (Penunjukan Awal)'},
    {k:'lamaJabatan', label:'Jabatan', type:'text', ph:'Kepala Seksi Pengendalian dan Penanganan Sengketa', hideWhen: d=>d.tipePengajuan==='Perpanjangan', group:'Jabatan yang Lowong/Berhalangan (Penunjukan Awal)'},

    {k:'tmtUsulan', label:'Pertanggal (mulai berlaku penunjukan)', type:'date', required:true, group:'Diusulkan sebagai Plt./Plh.'},
    {k:'_pegawaiPickerBaru', label:'Pilih Pegawai yang Diusulkan dari Data Pegawai', type:'pegawaiFill', target:'baru', group:'Diusulkan sebagai Plt./Plh.'},
    {k:'baruNama', label:'Nama', type:'text', ph:'Budiana, S.Kom.', required:true, group:'Diusulkan sebagai Plt./Plh.'},
    {k:'baruNip', label:'NIP', type:'text', ph:'197807302006041020', group:'Diusulkan sebagai Plt./Plh.'},
    {k:'baruPangkat', label:'Pangkat', type:'text', ph:'Penata Tk.I', group:'Diusulkan sebagai Plt./Plh.'},
    {k:'baruGolongan', label:'Golongan', type:'text', ph:'III/d', group:'Diusulkan sebagai Plt./Plh.'},
    {k:'baruJabatan', label:'Jabatan Asal', type:'text', ph:'Penata Pertanahan Ahli Pertama', group:'Diusulkan sebagai Plt./Plh.'},

    {k:'penutup', label:'Kalimat Penutup (opsional)', type:'textarea', ph:'Kosongkan untuk memakai kalimat baku "Demikian usulan ini kami sampaikan dan mohon petunjuk lebih lanjut."', group:'Penutup'},
  ],
};

const INSTANSI_FIELDS = [
  {k:'logo', label:'Logo Instansi (opsional)', type:'logo', group:'Kop Surat'},
  {k:'namaInstansi', label:'Nama Instansi (baris pertama kop)', type:'textarea', ph:'KEMENTERIAN AGRARIA DAN TATA RUANG/\nBADAN PERTANAHAN NASIONAL', hint:'Boleh lebih dari satu baris. Tekan Enter untuk baris baru, mengikuti hierarki instansi.', required:true, group:'Kop Surat'},
  {k:'unit', label:'Nama Unit / Satuan Kerja (opsional)', ph:'KANTOR PERTANAHAN KABUPATEN JEPARA', group:'Kop Surat'},
  {k:'wilayah', label:'Baris Tambahan / Wilayah (opsional)', ph:'PROVINSI JAWA TENGAH', group:'Kop Surat'},
  {k:'alamat', label:'Alamat', ph:'Jl. KH Ahmad Fauzan No.2 Jepara – 59415', group:'Kop Surat'},
  {k:'kontak', label:'Telepon / Email / Laman', ph:'Telp (0291) 591089 email : bpnjepara@yahoo.co.uk', group:'Kop Surat'},
  {k:'kota', label:'Kota (untuk tanggal & tempat)', ph:'Jepara', required:true, group:'Kop Surat'},
  {k:'kodeWilayah', label:'Kode Wilayah/Satker ATR-BPN (opsional)', ph:'33.20', hint:'Kode kantor wilayah.kabupaten sesuai penomoran internal ATR/BPN, mis. 33.20 untuk Kabupaten Jepara. Dipakai oleh alat bantu susun nomor surat.', group:'Kode Penomoran'},
  {k:'jenisTtd', label:'Gaya Tanda Tangan', type:'select', options:['Ditandatangani secara elektronik','Tanda tangan & cap basah'], group:'Tanda Tangan'},
  {k:'jabatanPenandatangan', label:'Jabatan Penandatangan Default', ph:'Kepala Kantor Pertanahan Kabupaten Jepara', group:'Tanda Tangan'},
  {k:'namaPenandatangan', label:'Nama Penandatangan Default', ph:'Muh. Nurdin, S.T.,M.T.,QRMP.', group:'Tanda Tangan'},
  {k:'nipPenandatangan', label:'NIP Penandatangan Default', ph:'196806021996031002', group:'Tanda Tangan'},
];

/* ============================================================
   STATE + STORAGE
   ============================================================ */
const state = {
  screen:'home',      // home | form | preview | pegawai | pegawaiTable
  activeType:null,
  formData:{},
  instansi:{},
  drafts:[],
  showInstansiModal:false,
  currentDraftId:null,
  nomorHelperOpen:false,
  pegawaiList:[],
  showPegawaiModal:false,
  editingPegawaiId:null,
  pegawaiPickerFor:null, // field key when picking pegawai into a form (mis. 'petugas')
  pegawaiPickerMode:null, // 'petugas' (isi array) | 'single' (isi field pegawai tunggal)
  showSideMenu:false,
  sideMenuNaskahOpen:false,
  showResetConfirm:false,
  pegawaiTableFilter:'',
  loginConfigured:false,
  isLoggedIn:false,
  loginError:'',
  showLoginSetup:false,
};

/* Penyimpanan ganda: memakai window.storage bila berjalan di dalam Claude,
   dan otomatis beralih ke localStorage browser saat aplikasi ini di-hosting
   sendiri di luar Claude (domain sendiri, GitHub Pages, dll). */
const LS_PREFIX = 'sukp:'; // Sistem Umum & Kepegawaian
const hasClaudeStorage = (typeof window!=='undefined' && !!window.storage && typeof window.storage.get==='function');

async function storageGet(key){
  if(hasClaudeStorage){
    try{ const r = await window.storage.get(key,false); return r? JSON.parse(r.value): null; }
    catch(e){ /* jatuh ke localStorage di bawah bila error */ }
  }
  try{
    const raw = localStorage.getItem(LS_PREFIX+key);
    return raw ? JSON.parse(raw) : null;
  }catch(e){ return null; }
}
async function storageSet(key,val){
  if(hasClaudeStorage){
    try{ await window.storage.set(key, JSON.stringify(val), false); return true; }
    catch(e){ /* jatuh ke localStorage di bawah bila error */ }
  }
  try{ localStorage.setItem(LS_PREFIX+key, JSON.stringify(val)); return true; }
  catch(e){ return false; }
}
async function storageDelete(key){
  if(hasClaudeStorage){
    try{ await window.storage.delete(key,false); return; }catch(e){ /* jatuh ke localStorage */ }
  }
  try{ localStorage.removeItem(LS_PREFIX+key); }catch(e){}
}

/* ============================================================
   LOGIN / PROTEKSI APLIKASI
   Gerbang akses sederhana berbasis kata sandi tunggal (bukan akun
   per-pengguna). Kata sandi disimpan sebagai hash SHA-256, bukan
   teks polos. Ini bukan keamanan tingkat server — hanya mencegah
   orang lain yang kebetulan memegang perangkat membuka data begitu
   saja.
   ============================================================ */
async function sha256Hex(text){
  if(window.crypto && window.crypto.subtle && window.crypto.subtle.digest){
    try{
      const enc = new TextEncoder().encode(text);
      const buf = await window.crypto.subtle.digest('SHA-256', enc);
      return Array.from(new Uint8Array(buf)).map(b=>b.toString(16).padStart(2,'0')).join('');
    }catch(e){ /* jatuh ke fallback di bawah, mis. konteks tidak aman (http biasa) */ }
  }
  // Fallback non-kriptografis untuk konteks yang tidak mendukung crypto.subtle
  // (mis. hosting tanpa HTTPS). Tetap cukup untuk mencegah kata sandi tersimpan polos.
  let h1=0, h2=5381;
  for(let i=0;i<text.length;i++){
    const c=text.charCodeAt(i);
    h1=((h1<<5)-h1+c)|0;
    h2=((h2*33)^c)|0;
  }
  return 'fb'+(h1>>>0).toString(16).padStart(8,'0')+(h2>>>0).toString(16).padStart(8,'0');
}
async function attemptLogin(){
  const el = document.querySelector('[data-login="password"]');
  const val = el ? el.value : '';
  if(!val.trim()){ state.loginError='Masukkan kata sandi.'; render(); return; }
  const cfg = await storageGet('app-login');
  const hash = await sha256Hex(val);
  if(cfg && cfg.passwordHash===hash){
    state.isLoggedIn=true;
    state.loginError='';
    state.screen='home';
    render();
  } else {
    state.loginError='Kata sandi salah. Coba lagi.';
    render();
  }
}
function lockApp(){
  state.showSideMenu=false;
  state.isLoggedIn=false;
  state.loginError='';
  state.screen='login';
  render();
}
function openLoginSetup(){ state.showSideMenu=false; state.showLoginSetup=true; render(); }
function closeLoginSetup(){ state.showLoginSetup=false; render(); }
async function saveLoginSetup(){
  const pw1 = (document.querySelector('[data-login="new1"]')||{}).value || '';
  const pw2 = (document.querySelector('[data-login="new2"]')||{}).value || '';
  if(pw1.length<4){ showToast('Kata sandi minimal 4 karakter'); return; }
  if(pw1!==pw2){ showToast('Konfirmasi kata sandi tidak cocok'); return; }
  const hash = await sha256Hex(pw1);
  const ok = await storageSet('app-login', {passwordHash:hash});
  if(ok){
    state.loginConfigured=true;
    state.showLoginSetup=false;
    showToast('Kata sandi aplikasi tersimpan');
    render();
  } else {
    showToast('Gagal menyimpan kata sandi');
  }
}
async function removeLoginProtection(){
  await storageDelete('app-login');
  state.loginConfigured=false;
  state.showLoginSetup=false;
  showToast('Proteksi login dihapus');
  render();
}

function renderLoginScreen(){
  const eyebrow = state.instansi.namaInstansi ? String(state.instansi.namaInstansi).split('\n')[0] : 'Sistem Umum dan Kepegawaian';
  const title = state.instansi.unit || 'Sistem Umum dan Kepegawaian';
  return `
    <div class="app-watermark" style="background-image:url('${getLogoUrl()}');"></div>
    <div class="login-screen">
      <div class="login-card">
        <div class="wh-ring" style="margin:0 auto 16px;"><img class="wh-logo" src="${getLogoUrl()}"></div>
        <div class="login-eyebrow">${esc(eyebrow)}</div>
        <h1 class="login-title">${esc(title)}</h1>
        <p class="login-sub">Aplikasi terkunci. Masukkan kata sandi untuk melanjutkan.</p>
        ${state.loginError? `<div class="login-error">${esc(state.loginError)}</div>` : ''}
        <div class="field">
          <label>Kata Sandi Aplikasi</label>
          <input type="password" data-login="password" placeholder="Kata sandi" autofocus onkeydown="if(event.key==='Enter') attemptLogin()">
        </div>
        <button class="btn btn-primary" onclick="attemptLogin()">${ICON.check} Masuk</button>
        <div class="login-foot">Kata sandi ini mengunci akses di perangkat ini saja — bukan akun per-pengguna.</div>
      </div>
    </div>`;
}
function renderLoginSetupModal(){
  return `<div class="modal-backdrop" onclick="if(event.target===this) closeLoginSetup()">
    <div class="modal">
      <div class="modal-head"><h2>${state.loginConfigured?'Ubah':'Atur'} Kata Sandi Aplikasi</h2><button class="modal-close" onclick="closeLoginSetup()">${ICON.x}</button></div>
      <div class="cat-desc" style="margin-top:-4px;">Kata sandi ini mengunci akses ke aplikasi di perangkat ini — cocok untuk perangkat yang dipakai bersama. Disimpan sebagai hash, bukan teks polos, namun ini bukan keamanan tingkat server: siapa pun yang mengubah kode aplikasi tetap bisa melewatinya.</div>
      <div class="form-block">
        <div class="field"><label>Kata Sandi Baru</label><input type="password" data-login="new1" placeholder="Minimal 4 karakter"></div>
        <div class="field"><label>Ulangi Kata Sandi</label><input type="password" data-login="new2" placeholder="Ulangi kata sandi"></div>
      </div>
      <button class="btn btn-primary" onclick="saveLoginSetup()">${ICON.check} Simpan Kata Sandi</button>
      ${state.loginConfigured? `<button class="btn btn-ghost" style="margin-top:8px; color:var(--danger); width:100%;" onclick="removeLoginProtection()">${ICON.trash} Hapus Proteksi Login</button>` : ''}
    </div>
  </div>`;
}

async function loadInitial(){
  const instansi = await storageGet('profil-instansi');
  if(instansi) state.instansi = instansi;
  const idx = await storageGet('drafts-index');
  if(idx) state.drafts = idx;
  const peg = await storageGet('pegawai-list');
  if(peg) state.pegawaiList = peg;
  const loginCfg = await storageGet('app-login');
  if(loginCfg && loginCfg.passwordHash){
    state.loginConfigured = true;
    state.isLoggedIn = false;
    state.screen = 'login';
  } else {
    state.isLoggedIn = true;
  }
  render();
}

function emptyFormFor(type){
  const data = {};
  FIELD_DEFS[type].forEach(f=>{
    if(f.type==='list') data[f.k]= f.defaultItems ? [...f.defaultItems] : [''];
    else if(f.type==='petugas') data[f.k]=[{nama:'',jabatan:'',nip:'',pangkat:'',golongan:''}];
    else if(f.type==='akRow'){ ['Lama','Baru','Jumlah','Ket'].forEach(s=>{ data[f.k+s]=''; }); }
    else if(f.type==='date') data[f.k]= f.required ? todayISO() : '';
    else if(f.type==='pegawaiFill'){ /* tidak menyimpan nilai sendiri */ }
    else data[f.k]= f.default!==undefined ? f.default : '';
  });
  return data;
}

function todayISO(){
  const d=new Date();
  return d.toISOString().slice(0,10);
}

const BULAN=['Januari','Februari','Maret','April','Mei','Juni','Juli','Agustus','September','Oktober','November','Desember'];
function formatTanggalIndo(iso){
  if(!iso) return '...';
  const [y,m,d]=iso.split('-').map(Number);
  if(!y) return iso;
  return `${d} ${BULAN[m-1]} ${y}`;
}
function formatTanggalCompact(iso){
  if(!iso) return '';
  const [y,m,d]=iso.split('-');
  if(!y) return iso;
  return `${d}-${m}-${y}`;
}
function formatTanggalIndoPadded(iso){
  if(!iso) return '...';
  const [y,m,d]=iso.split('-').map(Number);
  if(!y) return iso;
  return `${String(d).padStart(2,'0')} ${BULAN[m-1]} ${y}`;
}

/* ============================================================
   PERINGATAN KEPEGAWAIAN
   Kenaikan Pangkat reguler: setiap 4 tahun sejak TMT Pangkat.
   Kenaikan Gaji Berkala: setiap 2 tahun sejak TMT Gaji Berkala.
   Peringatan muncul mulai H-90 hari sebelum jatuh tempo.
   ============================================================ */
const ALERT_WINDOW_DAYS = 90;
function addYearsISO(iso, years){
  if(!iso) return null;
  const [y,m,d] = iso.split('-').map(Number);
  if(!y) return null;
  const dt = new Date(y, (m||1)-1, d||1);
  dt.setFullYear(dt.getFullYear()+years);
  return dt.toISOString().slice(0,10);
}
function daysUntil(iso){
  if(!iso) return null;
  const [y,m,d]=iso.split('-').map(Number);
  const target = new Date(y,(m||1)-1,d||1);
  const now = new Date(); now.setHours(0,0,0,0);
  return Math.round((target-now)/86400000);
}
function getPegawaiAlerts(p){
  const alerts=[];
  if(p.tmtPangkat){
    const due = addYearsISO(p.tmtPangkat,4);
    const days = daysUntil(due);
    if(days!==null && days<=ALERT_WINDOW_DAYS) alerts.push({jenis:'Kenaikan Pangkat', due, days, status: days<0?'overdue':'soon'});
  }
  if(p.tmtGajiBerkala){
    const due = addYearsISO(p.tmtGajiBerkala,2);
    const days = daysUntil(due);
    if(days!==null && days<=ALERT_WINDOW_DAYS) alerts.push({jenis:'Gaji Berkala', due, days, status: days<0?'overdue':'soon'});
  }
  const saty = getSatyalancanaAlert(p);
  if(saty) alerts.push(saty);
  const jumlahPlt = parseInt(p.jumlahPengajuanPltPlh,10)||0;
  if(jumlahPlt>=2){
    alerts.push({jenis:'Plt./Plh.', status:'overdue', days:0, label:`Pengajuan Plt./Plh. sudah ${jumlahPlt}x — batas maksimal 2 kali`});
  }
  alerts.push(...getPakAlerts(p));
  return alerts;
}
function yearsBetween(iso, todayDate){
  const [y,m,d] = iso.split('-').map(Number);
  if(!y) return null;
  const start = new Date(y,(m||1)-1,d||1);
  let years = todayDate.getFullYear()-start.getFullYear();
  const anniversaryThisYear = new Date(todayDate.getFullYear(), start.getMonth(), start.getDate());
  if(todayDate < anniversaryThisYear) years--;
  return years;
}
function getMasaKerjaTahun(tgl){
  if(!tgl) return null;
  const now = new Date(); now.setHours(0,0,0,0);
  return yearsBetween(tgl, now);
}
function getSatyalancanaAlert(p){
  if(!p.tanggalPengangkatan) return null;
  const masaKerja = getMasaKerjaTahun(p.tanggalPengangkatan);
  if(masaKerja===null) return null;
  const lower = Math.floor(masaKerja/10)*10;
  for(const dec of [lower, lower+10]){
    if(dec<10) continue;
    const due = addYearsISO(p.tanggalPengangkatan, dec);
    const days = daysUntil(due);
    if(days!==null && days<=ALERT_WINDOW_DAYS && days>=-ALERT_WINDOW_DAYS){
      return {jenis:'Pengajuan Satyalancana Karya Satya '+dec+' Tahun', due, days, status: days<0?'overdue':'soon'};
    }
  }
  return null;
}
/* Ambang kumulatif Angka Kredit per jenjang Jabatan Fungsional,
   sesuai Peraturan Menteri PANRB Nomor 1 Tahun 2023 tentang Jabatan
   Fungsional, Lampiran A (Angka Kredit JF). jenjang:null berarti
   jenjang tertinggi pada kelompoknya (tidak ada kenaikan jenjang lagi). */
const AK_JENJANG_TABLE = {
  'Ahli Utama':  {pangkat:200, jenjang:null},
  'Ahli Madya':  {pangkat:150, jenjang:450},
  'Ahli Muda':   {pangkat:100, jenjang:200},
  'Ahli Pertama':{pangkat:50,  jenjang:100},
  'Penyelia':    {pangkat:100, jenjang:null},
  'Mahir':       {pangkat:50,  jenjang:100},
  'Terampil':    {pangkat:20,  jenjang:60},
  'Pemula':      {pangkat:15,  jenjang:15},
};
function getPakAlerts(p){
  const alerts=[];
  if(p.jenisJabatan!=='Jabatan Fungsional') return alerts;
  const ambang = AK_JENJANG_TABLE[p.jenjangJf];
  if(!ambang) return alerts;
  const nilai = parseFloat(p.nilaiPak);
  if(isNaN(nilai)) return alerts;
  if(nilai>=ambang.pangkat){
    alerts.push({jenis:'PAK', status:'soon', days:0, label:`Angka Kredit ${nilai} sudah memenuhi syarat Kenaikan Pangkat (min. ${ambang.pangkat})`});
  }
  if(ambang.jenjang!==null && nilai>=ambang.jenjang){
    alerts.push({jenis:'PAK', status:'soon', days:0, label:`Angka Kredit ${nilai} sudah memenuhi syarat Pengajuan Uji Kompetensi Kenaikan Jenjang (min. ${ambang.jenjang})`});
  }
  return alerts;
}
function getAllPegawaiAlerts(){
  let all=[];
  state.pegawaiList.forEach(p=>{
    getPegawaiAlerts(p).forEach(a=>all.push({...a, pegawaiId:p.id, nama:p.nama}));
  });
  all.sort((a,b)=>a.days-b.days);
  return all;
}
function alertChipHtml(a){
  const label = a.label || (a.status==='overdue'
    ? `${a.jenis} lewat ${Math.abs(a.days)} hari`
    : `${a.jenis} H-${a.days} hari`);
  return `<span class="peg-alert-chip ${a.status}">${esc(label)}</span>`;
}

/* ============================================================
   NAVIGATION
   ============================================================ */
function goHome(){ state.screen='home'; state.activeType=null; state.currentDraftId=null; state.showSideMenu=false; render(); }
function goPegawai(){ state.screen='pegawai'; state.showSideMenu=false; render(); window.scrollTo(0,0); }
function toggleSideMenu(){ state.showSideMenu=!state.showSideMenu; render(); }
function closeSideMenu(){ state.showSideMenu=false; render(); }
function toggleNaskahDrawer(){ state.sideMenuNaskahOpen=!state.sideMenuNaskahOpen; render(); }
function openNaskahMenu(){ state.showSideMenu=true; state.sideMenuNaskahOpen=true; render(); }
function sideMenuOpenInstansi(){ state.showSideMenu=false; openInstansiModal(); }
function openResetConfirm(){ state.showSideMenu=false; state.showResetConfirm=true; render(); }
function closeResetConfirm(){ state.showResetConfirm=false; render(); }
async function confirmResetAll(){
  for(const dr of state.drafts){ await storageDelete('draft:'+dr.id); }
  await storageDelete('drafts-index');
  await storageDelete('profil-instansi');
  await storageDelete('pegawai-list');
  await storageDelete('app-login');
  state.instansi={};
  state.drafts=[];
  state.pegawaiList=[];
  state.formData={};
  state.activeType=null;
  state.currentDraftId=null;
  state.showResetConfirm=false;
  state.loginConfigured=false;
  state.isLoggedIn=true;
  state.loginError='';
  state.screen='home';
  render();
  showToast('Semua data telah dikosongkan');
}
function renderResetConfirm(){
  return `<div class="modal-backdrop" onclick="if(event.target===this) closeResetConfirm()">
    <div class="modal">
      <div class="modal-head"><h2>Kosongkan Semua Data?</h2><button class="modal-close" onclick="closeResetConfirm()">${ICON.x}</button></div>
      <div class="cat-desc" style="margin-top:-4px;">Tindakan ini akan menghapus <strong>Profil Instansi</strong>, seluruh <strong>Data Pegawai</strong> (${state.pegawaiList.length} pegawai), dan semua <strong>Draf tersimpan</strong> (${state.drafts.length} draf) dari perangkat/akun ini. Tindakan ini tidak dapat dibatalkan.</div>
      <div style="display:flex; gap:10px; margin-top:16px;">
        <button class="btn btn-secondary" onclick="closeResetConfirm()">Batal</button>
        <button class="btn btn-primary" style="background:linear-gradient(135deg,#c0503a,#8f3624); color:#fff;" onclick="confirmResetAll()">${ICON.trash} Ya, Kosongkan</button>
      </div>
    </div>
  </div>`;
}
function openType(typeId){
  state.activeType=typeId;
  state.formData=emptyFormFor(typeId);
  state.currentDraftId=null;
  state.nomorHelperOpen=false;
  state.screen='form';
  state.showSideMenu=false;
  render();
  window.scrollTo(0,0);
}
function openDraft(id){
  const draftKey='draft:'+id;
  storageGet(draftKey).then(d=>{
    if(!d) return showToast('Draf tidak ditemukan');
    state.activeType=d.type;
    state.formData=d.formData;
    state.currentDraftId=id;
    state.nomorHelperOpen=false;
    state.screen='form';
    render();
    window.scrollTo(0,0);
  });
}
function goPreview(){
  const missing = FIELD_DEFS[state.activeType].filter(f=>f.required && !(f.hideWhen && f.hideWhen(state.formData))).find(f=>{
    const v=state.formData[f.k];
    if(f.type==='list') return !v || v.filter(x=>x && x.trim()).length===0;
    if(f.type==='petugas') return !v || v.filter(p=>p.nama && p.nama.trim()).length===0;
    return !v || !String(v).trim();
  });
  if(missing){ showToast('Lengkapi dulu: '+missing.label); return; }
  if(state.activeType==='pltplh' && (!state.formData.sifat || state.formData.sifat==='Biasa')){
    showToast('Pilih Sifat surat (Penting/Segera/Rahasia) — "Biasa" tidak dapat dipakai untuk Usulan Plt./Plh.');
    return;
  }
  state.screen='preview';
  render();
  window.scrollTo(0,0);
}
function backToForm(){ state.screen='form'; render(); window.scrollTo(0,0); }

/* ============================================================
   TOAST
   ============================================================ */
let toastTimer=null;
function showToast(msg){
  const el=document.getElementById('toast');
  el.textContent=msg;
  el.classList.add('show');
  clearTimeout(toastTimer);
  toastTimer=setTimeout(()=>el.classList.remove('show'),2200);
}

/* ============================================================
   LIST / PETUGAS FIELD HELPERS
   ============================================================ */
function addListItem(key){ state.formData[key].push(''); render(); }
function removeListItem(key,i){ state.formData[key].splice(i,1); if(state.formData[key].length===0) state.formData[key].push(''); render(); }
function addPetugas(key){ state.formData[key].push({nama:'',jabatan:'',nip:'',pangkat:'',golongan:''}); render(); }
function removePetugas(key,i){ state.formData[key].splice(i,1); if(state.formData[key].length===0) state.formData[key].push({nama:'',jabatan:'',nip:'',pangkat:'',golongan:''}); render(); }

function toggleNomorHelper(){ state.nomorHelperOpen = !state.nomorHelperOpen; render(); }
function applyNomorHelper(){
  const urutEl = document.querySelector('[data-nh="urut"]');
  const klasEl = document.querySelector('[data-nh="klas"]');
  const urut = urutEl ? urutEl.value.trim() : '';
  const klas = klasEl ? klasEl.value.trim() : '';
  if(!urut){ showToast('Isi nomor urut terlebih dahulu'); return; }
  const tgl = state.formData.tanggal || todayISO();
  const [y,m] = tgl.split('-').map(Number);
  const bulanRomawi = BULAN_ROMAWI[(m||1)-1];
  const kodeJenis = KODE_JENIS_BPN[state.activeType] || '';
  const wilayah = (state.instansi.kodeWilayah||'').trim();
  let seg2 = kodeJenis;
  if(wilayah || klas){
    const combo = wilayah + (klas ? (wilayah?'.':'')+klas : '');
    seg2 = seg2 ? seg2+'-'+combo : combo;
  }
  if(!seg2){ showToast('Isi kode klasifikasi arsip agar nomor lengkap'); return; }
  state.formData.nomor = `${urut}/${seg2}/${bulanRomawi}/${y||'....'}`;
  state.nomorHelperOpen = false;
  render();
  showToast('Nomor surat disusun otomatis');
}

/* ============================================================
   TEXT COMPOSITION HELPERS (narasi baku Bahasa Indonesia)
   ============================================================ */
function alpha(i){ return String.fromCharCode(97+i); } // a,b,c...
function ROMAN_LIKE(i){ return (i+1)+'.'; }

function cleanList(arr){ return (arr||[]).map(s=>String(s||'').trim()).filter(Boolean); }

function joinLettered(items, closerPunct){
  // returns array of {label, text} with proper trailing punctuation
  const list = cleanList(items);
  return list.map((t,i)=>{
    const isLast = i===list.length-1;
    let text = t.replace(/[.;]\s*$/,'');
    text += isLast ? '.' : ';';
    return {label: alpha(i)+'.', text};
  });
}
function joinNumbered(items){
  const list = cleanList(items);
  return list.map((t,i)=>{
    const isLast = i===list.length-1;
    let text = t.replace(/[.;]\s*$/,'');
    text += isLast ? '.' : ';';
    return {label:(i+1)+'.', text};
  });
}
function capFirst(s){ if(!s) return s; return s.charAt(0).toUpperCase()+s.slice(1); }

/* ============================================================
   SURAT BUILDERS -> mengembalikan array "blocks" untuk dirender
   Setiap block: {kind, ...}
   ============================================================ */
function buildKop(instansi){
  return {kind:'kop', instansi};
}

function buildDinas(d, ins){
  const blocks=[];
  blocks.push(buildKop(ins));
  const headRows = [['Nomor', d.nomor], ['Sifat', d.sifat]];
  if(d.lampiran && d.lampiran.trim()) headRows.push(['Lampiran', d.lampiran.trim()]);
  headRows.push(['Perihal', capFirst(d.hal)]);
  blocks.push({kind:'kv', rows:headRows});
  blocks.push({kind:'placedate', text:`${ins.kota||'...'}, ${formatTanggalIndoPadded(d.tanggal)}`});
  blocks.push({kind:'addr', jabatan:d.tujuanJabatan, alamat:d.tujuanAlamat});
  const opening = `Sehubungan ${lower1(d.konteks)}, bersama ini kami sampaikan hal-hal sebagai berikut :`;
  blocks.push({kind:'para', indent:true, text:opening});
  blocks.push({kind:'numbered', items:joinNumbered(d.poinIsi)});
  const closing = d.penutup && d.penutup.trim() ? d.penutup.trim() : 'Demikian surat ini kami sampaikan. Atas perhatian dan kerja sama Bapak/Ibu/Saudara, kami ucapkan terima kasih.';
  blocks.push({kind:'para', indent:true, text:closing});
  blocks.push({kind:'signature', place:ins.kota, date:d.tanggal, jabatan:ins.jabatanPenandatangan, nama:ins.namaPenandatangan, nip:ins.nipPenandatangan, noPlaceDate:true});
  if(cleanList(d.tembusan).length) blocks.push({kind:'tembusan', items:cleanList(d.tembusan)});
  return blocks;
}

function buildNota(d, ins){
  const blocks=[];
  blocks.push(buildKop(ins));
  blocks.push({kind:'doctitle', t1:'NOTA DINAS', t2:'NOMOR : '+d.nomor});
  const rows = [
    ['Kepada', d.kepada],
    ['Dari', d.dari],
    ['Tanggal', d.tanggal],
  ];
  if(d.sifat && d.sifat.trim()) rows.push(['Sifat', d.sifat]);
  if(d.lampiran && d.lampiran.trim()) rows.push(['Lampiran', d.lampiran.trim()]);
  rows.push(['Perihal', capFirst(d.hal)]);
  blocks.push({kind:'kv', rows});
  blocks.push({kind:'rule'});
  const poin = cleanList(d.poinIsi);
  if(poin.length<=1){
    blocks.push({kind:'para', indent:true, text: poin[0] || ''});
  } else {
    blocks.push({kind:'lettered', items:joinLettered(poin)});
  }
  const closing = d.penutup && d.penutup.trim() ? d.penutup.trim() : 'Demikian untuk dapat ditaati dan dilaksanakan. Terima kasih.';
  blocks.push({kind:'para', indent:true, marginTop:true, text:closing});
  blocks.push({kind:'signature', place:ins.kota, date:d.tanggal, jabatan:d.dari, nama:ins.namaPenandatangan, nip:ins.nipPenandatangan, noPlaceDate:true});
  const elektronik = (ins.jenisTtd||'Ditandatangani secara elektronik') !== 'Tanda tangan & cap basah';
  if(elektronik){
    blocks.push({kind:'footnote', text:`Dokumen ini sah dan telah ditandatangani secara elektronik melalui e-Office ${insName(ins)||'instansi'} menggunakan sertifikat elektronik BSrE, BSSN. Untuk memastikan keasliannya, silakan pindai Kode QR pada dokumen final menggunakan fitur 'Validasi Surat'.`, tagline:'Melayani, Profesional, Terpercaya'});
  }
  return blocks;
}

function buildTugas(d, ins){
  const blocks=[];
  blocks.push(buildKop(ins));
  blocks.push({kind:'doctitle', t1:'SURAT TUGAS', t2:'NOMOR : '+d.nomor, spaced:true});
  if(cleanList(d.menimbang).length){
    blocks.push({kind:'para', indent:false, bold:true, text:'Menimbang :'});
    blocks.push({kind:'lettered', items:joinLettered(d.menimbang)});
  }
  if(cleanList(d.dasar).length){
    blocks.push({kind:'para', indent:false, bold:true, marginTop:true, text:'Dasar :'});
    blocks.push({kind:'numbered', items:joinNumbered(d.dasar)});
  }
  blocks.push({kind:'centerbold', text:'MEMBERI TUGAS :'});
  blocks.push({kind:'para', indent:false, bold:true, text:'Kepada :'});
  blocks.push({kind:'petugasTable', items:d.petugas});
  blocks.push({kind:'para', indent:false, bold:true, marginTop:true, text:'untuk :'});
  blocks.push({kind:'numbered', items:joinNumbered(d.tugasPoin)});
  blocks.push({kind:'signature', place:ins.kota, date:d.tanggal, atasNama:d.anJabatan, jabatan:d.penandatanganJabatan||ins.jabatanPenandatangan, nama:d.penandatanganNama||ins.namaPenandatangan, nip:d.penandatanganNip||ins.nipPenandatangan});
  return blocks;
}

function buildSpd(d, ins){
  const blocks=[];
  blocks.push(buildKop(ins));
  const klLabel = String(ins.namaInstansi||'').split('\n').filter(Boolean).join(' ').trim() || insName(ins);
  blocks.push({kind:'kv', rows:[
    ['Kementerian Negara/Lembaga', klLabel],
    ['Satuan Kerja', d.satuanKerja||ins.unit||'-'],
    ['Nomor', d.nomor],
    ['Lembar Ke', d.lembarKe||'-'],
    ['Kode Nomor', d.kodeNomor||'-'],
  ]});
  blocks.push({kind:'centerbold', text:'SURAT PERJALANAN DINAS (SPD)'});
  const pengikutLines = cleanList(d.pengikut).length ? cleanList(d.pengikut) : ['-'];
  blocks.push({kind:'spdGrid', rows:[
    {no:'1', label:'Pejabat Pembuat Komitmen', lines:[d.ppkNama, d.ppkJabatan].filter(Boolean)},
    {no:'2', label:'Nama / NIP Pegawai yang Melaksanakan Perjalanan Dinas', lines:[d.pegawaiNama, 'NIP. '+(d.pegawaiNip||'-')]},
    {no:'3', label:'a. Pangkat dan Golongan\nb. Jabatan/Instansi\nc. Tingkat Biaya Perjalanan Dinas', lines:[
      'a. '+[d.pegawaiPangkat,d.pegawaiGolongan].filter(Boolean).join(' / '),
      'b. '+(d.pegawaiJabatan||'-'),
      'c. '+(d.tingkatBiaya||'-'),
    ]},
    {no:'4', label:'Maksud Perjalanan Dinas', lines:[d.maksud]},
    {no:'5', label:'Alat Angkutan yang Dipergunakan', lines:[d.alatAngkutan||'-']},
    {no:'6', label:'a. Tempat Berangkat\nb. Tempat Tujuan', lines:['a. '+(d.tempatBerangkat||'-'), 'b. '+(d.tempatTujuan||'-')]},
    {no:'7', label:'a. Lamanya Perjalanan Dinas\nb. Tanggal Berangkat\nc. Tanggal Harus Kembali/Tiba di Tempat Baru', lines:[
      'a. '+(d.lamanya||'-'),
      'b. '+formatTanggalIndoPadded(d.tanggalBerangkat),
      'c. '+formatTanggalIndoPadded(d.tanggalKembali),
    ]},
    {no:'8', label:'Pengikut', lines:pengikutLines},
    {no:'9', label:'Pembebanan Anggaran\na. Instansi\nb. Akun', lines:['a. '+(d.pembebananInstansi||'-'), 'b. '+(d.pembebananAkun||'-')]},
    {no:'10', label:'Keterangan Lain-Lain', lines:[d.keteranganLain && d.keteranganLain.trim() ? d.keteranganLain.trim() : '-']},
  ]});
  blocks.push({kind:'placedate', text:`Dikeluarkan di : ${ins.kota||'...'}\nTanggal : ${formatTanggalIndoPadded(d.tanggal)}`, twoLine:true});
  blocks.push({kind:'signature', jabatan:'Pejabat Pembuat Komitmen', nama:d.ppkNama, nip:d.ppkNip, noPlaceDate:true});

  blocks.push({kind:'para', indent:false, bold:true, marginTop:true, text:'I.'});
  blocks.push({kind:'kv', rows:[
    ['Berangkat Dari', (d.tempatBerangkat||'-')+' (Tempat Kedudukan)'],
    ['Ke', d.tempatTujuan||'-'],
    ['Pada Tanggal', formatTanggalIndoPadded(d.tanggalBerangkat)],
  ]});
  blocks.push({kind:'signature', atasNama:d.anJabatan, jabatan:d.ppkJabatan||'Pejabat Pembuat Komitmen', nama:d.ppkNama, nip:d.ppkNip, noPlaceDate:true});

  blocks.push({kind:'para', indent:false, bold:true, marginTop:true, text:'II.'});
  blocks.push({kind:'kv', rows:[['Tiba di', d.tempatTujuan||'-'], ['Pada Tanggal', formatTanggalIndoPadded(d.tanggalBerangkat)]]});
  blocks.push({kind:'blankSig'});
  blocks.push({kind:'kv', rows:[['Berangkat dari', d.tempatTujuan||'-'], ['Ke', d.tempatBerangkat||'-'], ['Pada Tanggal', formatTanggalIndoPadded(d.tanggalKembali)]]});
  blocks.push({kind:'blankSig'});

  ['III','IV','V'].forEach(roman=>{
    blocks.push({kind:'para', indent:false, bold:true, marginTop:true, text:roman+'.'});
    blocks.push({kind:'kv', rows:[['Tiba di', ''], ['Pada Tanggal', '']]});
    blocks.push({kind:'blankSig'});
    blocks.push({kind:'kv', rows:[['Berangkat dari', ''], ['Ke', ''], ['Pada Tanggal', '']]});
    blocks.push({kind:'blankSig'});
  });

  blocks.push({kind:'para', indent:false, bold:true, marginTop:true, text:'VI.'});
  blocks.push({kind:'kv', rows:[['Tiba di', (d.tempatBerangkat||'-')+' (Tempat Kedudukan)'], ['Pada Tanggal', formatTanggalIndoPadded(d.tanggalKembali)]]});
  blocks.push({kind:'signature', jabatan:'Pejabat Pembuat Komitmen', nama:d.ppkNama, nip:d.ppkNip, noPlaceDate:true});
  blocks.push({kind:'para', indent:true, text:'Telah diperiksa dengan keterangan bahwa perjalanan tersebut atas perintahnya dan semata-mata untuk kepentingan jabatan dalam waktu yang sesingkat-singkatnya.'});
  blocks.push({kind:'signature', jabatan:'Pejabat Pembuat Komitmen', nama:d.ppkNama, nip:d.ppkNip, noPlaceDate:true});

  blocks.push({kind:'para', indent:false, bold:true, marginTop:true, text:'VII. Catatan Lain-Lain :'});
  blocks.push({kind:'para', indent:true, text: d.catatanLain && d.catatanLain.trim() ? d.catatanLain.trim() : '-'});

  blocks.push({kind:'para', indent:false, bold:true, marginTop:true, text:'VIII. PERHATIAN :'});
  blocks.push({kind:'para', indent:true, text:'PPK yang menerbitkan SPD, pegawai yang melakukan perjalanan dinas, para pejabat yang mengesahkan tanggal berangkat/tiba, serta bendahara pengeluaran bertanggung jawab berdasarkan peraturan-peraturan Keuangan Negara apabila Negara menderita rugi akibat kesalahan, kelalaian dan kealpaannya.'});

  return blocks;
}

function buildSk(d, ins){
  const blocks=[];
  blocks.push(buildKop(ins));
  blocks.push({kind:'sktitle', instansi:insName(ins), nomor:d.nomor, judul:d.judul});
  blocks.push({kind:'para', indent:false, bold:false, text:capFirst(ins.jabatanPenandatangan||'Pimpinan Instansi')+','});
  blocks.push({kind:'para', indent:false, text:'Menimbang', bold:true, marginTop:true});
  blocks.push({kind:'lettered', items:joinLettered((d.menimbang||[]).map(t=>{
    const clean=t.trim();
    return /^bahwa/i.test(clean) ? clean : 'bahwa '+lower1(clean);
  }))});
  blocks.push({kind:'para', indent:false, text:'Mengingat', bold:true, marginTop:true});
  blocks.push({kind:'numbered', items:joinNumbered(d.mengingat)});
  blocks.push({kind:'centerbold', text:'MEMUTUSKAN:'});
  blocks.push({kind:'diktum', label:'Menetapkan', text:'KEPUTUSAN '+(insName(ins)||'INSTANSI').toUpperCase()+' TENTANG '+String(d.judul||'').toUpperCase()+'.'});
  const diktumList = cleanList(d.diktum);
  const romanLabels=['KESATU','KEDUA','KETIGA','KEEMPAT','KELIMA','KEENAM','KETUJUH','KEDELAPAN','KESEMBILAN','KESEPULUH'];
  diktumList.forEach((t,i)=>{
    let text=t.replace(/[.;]\s*$/,'');
    text += (i===diktumList.length-1) ? '.' : ';';
    blocks.push({kind:'diktum', label:romanLabels[i]||('DIKTUM '+(i+1)), text});
  });
  blocks.push({kind:'signature', place:ins.kota, date:d.tanggal, jabatan:ins.jabatanPenandatangan, nama:ins.namaPenandatangan, nip:ins.nipPenandatangan, ditetapkan:true});
  if(cleanList(d.tembusan).length) blocks.push({kind:'tembusan', items:cleanList(d.tembusan)});
  return blocks;
}

function buildEdaran(d, ins){
  const blocks=[];
  blocks.push(buildKop(ins));
  blocks.push({kind:'doctitle', t1:'SURAT EDARAN', t2:'Nomor: '+d.nomor, t3:'TENTANG', t4:String(d.tentang||'').toUpperCase()});
  blocks.push({kind:'addr', jabatan:d.tujuan, alamat:''});
  const opening = capFirst(lower1(d.latar));
  blocks.push({kind:'para', indent:true, text:opening.replace(/[.;]\s*$/,'')+', dengan ini disampaikan hal-hal sebagai berikut:'});
  blocks.push({kind:'lettered', items:joinLettered(d.poinIsi)});
  blocks.push({kind:'para', indent:true, text:'Demikian Surat Edaran ini disampaikan untuk diketahui dan dilaksanakan sebagaimana mestinya.'});
  blocks.push({kind:'signature', place:ins.kota, date:d.tanggal, jabatan:ins.jabatanPenandatangan, nama:ins.namaPenandatangan, nip:ins.nipPenandatangan});
  return blocks;
}

function buildUndangan(d, ins){
  const blocks=[];
  blocks.push(buildKop(ins));
  blocks.push({kind:'kv', rows:[
    ['Nomor', d.nomor],
    ['Lampiran', d.lampiran||'-'],
    ['Hal', 'Undangan '+d.acara],
  ]});
  blocks.push({kind:'placedate', text:`${ins.kota||'...'}, ${formatTanggalIndo(d.tanggal)}`});
  blocks.push({kind:'addr', jabatan:d.tujuanJabatan, alamat:d.tujuanAlamat});
  blocks.push({kind:'para', indent:false, text:'Dengan hormat,'});
  blocks.push({kind:'para', indent:true, text:`Sehubungan dengan pelaksanaan ${d.acara}, kami mengharapkan kehadiran Bapak/Ibu/Saudara pada:`});
  blocks.push({kind:'kv', rows:[
    ['Hari, Tanggal', d.hari],
    ['Waktu', d.waktu],
    ['Tempat', d.tempat],
  ]});
  if(cleanList(d.agenda).length){
    blocks.push({kind:'para', indent:false, text:'Agenda:'});
    blocks.push({kind:'numbered', items:joinNumbered(d.agenda)});
  }
  blocks.push({kind:'para', indent:true, text:'Mengingat pentingnya acara tersebut, kami mengharapkan kehadiran Bapak/Ibu/Saudara tepat waktu. Atas perhatian dan kerja sama yang baik, kami ucapkan terima kasih.'});
  blocks.push({kind:'signature', place:ins.kota, date:d.tanggal, jabatan:ins.jabatanPenandatangan, nama:ins.namaPenandatangan, nip:ins.nipPenandatangan});
  return blocks;
}

function buildPengumuman(d, ins){
  const blocks=[];
  blocks.push(buildKop(ins));
  blocks.push({kind:'doctitle', t1:'PENGUMUMAN', t2:'Nomor: '+d.nomor, t3:'TENTANG', t4:String(d.tentang||'').toUpperCase()});
  blocks.push({kind:'para', indent:true, text:'Dengan ini disampaikan hal-hal sebagai berikut:'});
  blocks.push({kind:'lettered', items:joinLettered(d.poinIsi)});
  blocks.push({kind:'para', indent:true, text:'Demikian pengumuman ini disampaikan untuk diketahui dan dilaksanakan sebagaimana mestinya.'});
  blocks.push({kind:'signature', place:ins.kota, date:d.tanggal, jabatan:ins.jabatanPenandatangan, nama:ins.namaPenandatangan, nip:ins.nipPenandatangan});
  return blocks;
}

function buildPak(d, ins){
  const blocks=[];
  blocks.push(buildKop(ins));
  blocks.push({kind:'doctitle', t1:'PENETAPAN ANGKA KREDIT', t2:'Nomor : '+d.nomor});
  const instansiLabel = d.instansiInduk && d.instansiInduk.trim() ? d.instansiInduk.trim() : insName(ins);
  blocks.push({kind:'kv', rows:[
    ['Instansi', instansiLabel],
    ['Masa Penilaian', d.masaPenilaian],
  ]});
  blocks.push({kind:'para', indent:false, bold:true, text:'I. KETERANGAN PERORANGAN'});
  const pangkatGolTmt = [d.pegawaiPangkat, d.pegawaiGolongan].filter(Boolean).join('/ ') + (d.pegawaiTmtPangkat? '/'+formatTanggalCompact(d.pegawaiTmtPangkat) : '');
  const jabatanTmt = [d.pegawaiJabatan, d.pegawaiTmtJabatan? formatTanggalCompact(d.pegawaiTmtJabatan): ''].filter(Boolean).join('/ ');
  blocks.push({kind:'kv', rows:[
    ['Nama', d.pegawaiNama],
    ['NIP', d.pegawaiNip||'-'],
    ['Nomor Seri KARPEG', d.karpeg||'-'],
    ['Tempat/Tgl Lahir', d.ttl||'-'],
    ['Jenis Kelamin', d.jenisKelamin||'-'],
    ['Pangkat/Gol Ruang/TMT', pangkatGolTmt||'-'],
    ['Jabatan Fungsional/TMT', jabatanTmt||'-'],
    ['Unit Kerja', d.pegawaiUnitKerja||ins.unit||'-'],
    ['Instansi', instansiLabel],
  ]});
  blocks.push({kind:'para', indent:false, bold:true, marginTop:true, text:'II. PENETAPAN ANGKA KREDIT'});
  const akRows = [
    ['AK Dasar yang diberikan', d.akDasarLama, d.akDasarBaru, d.akDasarJumlah, d.akDasarKet],
    ['AK JF Lama', d.akJfLamaLama, d.akJfLamaBaru, d.akJfLamaJumlah, d.akJfLamaKet],
    ['AK Penyesuaian/Penyetaraan', d.akPenyesuaianLama, d.akPenyesuaianBaru, d.akPenyesuaianJumlah, d.akPenyesuaianKet],
    ['AK Konversi', d.akKonversiLama, d.akKonversiBaru, d.akKonversiJumlah, d.akKonversiKet],
    ['AK dari Peningkatan Pendidikan', d.akPendidikanLama, d.akPendidikanBaru, d.akPendidikanJumlah, d.akPendidikanKet],
  ];
  const lainLabel = d.akLainLabel && d.akLainLabel.trim() ? d.akLainLabel.trim() : null;
  if(lainLabel || d.akLainLama || d.akLainBaru || d.akLainJumlah){
    akRows.push([lainLabel||'Lainnya', d.akLainLama, d.akLainBaru, d.akLainJumlah, d.akLainKet]);
  }
  blocks.push({kind:'aktable', rows:akRows, total:[d.jumlahKumulatifLama, d.jumlahKumulatifBaru, d.jumlahKumulatifJumlah, d.jumlahKumulatifKet]});
  blocks.push({kind:'keteranganTable', rows:[
    ['Angka Kredit minimal yang harus dicapai', d.akMinimalPangkat, d.akMinimalJenjang],
    ['Kelebihan Angka Kredit yang dicapai', d.akKelebihanPangkat, d.akKelebihanJenjang],
  ]});
  if(d.pertimbangan && d.pertimbangan.trim()){
    blocks.push({kind:'para', indent:false, bold:true, marginTop:true, text:'III.'});
    blocks.push({kind:'para', indent:true, text:d.pertimbangan.trim()});
  }
  const sapaan = d.jenisKelamin==='Perempuan' ? 'Sdri. ' : 'Sdr. ';
  blocks.push({kind:'asliBlock', nama: sapaan+(d.pegawaiNama||'')});
  blocks.push({kind:'signature', place:ins.kota, date:d.tanggal, jabatan:d.pejabatPenilaiJabatan||'Pejabat Penilai Kinerja', nama:d.pejabatPenilaiNama||ins.namaPenandatangan, nip:d.pejabatPenilaiNip||ins.nipPenandatangan, ditetapkan:true});
  if(cleanList(d.tembusan).length) blocks.push({kind:'tembusan', items:cleanList(d.tembusan)});
  return blocks;
}

function buildKgb(d, ins){
  const blocks=[];
  blocks.push(buildKop(ins));
  blocks.push({kind:'kv', rows:[
    ['Nomor', d.nomor],
    ['Sifat', d.sifat],
    ['Lampiran', d.lampiran||'-'],
    ['Hal', 'Kenaikan Gaji Berkala'],
  ]});
  blocks.push({kind:'placedate', text:`${ins.kota||'...'}, ${formatTanggalIndo(d.tanggal)}`});
  blocks.push({kind:'addrDi', jabatan:d.tujuanJabatan, kota:d.tujuanKota});
  blocks.push({kind:'para', indent:true, text:'Dengan ini diberitahukan bahwa sehubungan dengan telah dipenuhinya masa kerja dan syarat-syarat lainnya, kepada :'});
  const pangkatGol = [d.pegawaiPangkat, d.pegawaiGolongan].filter(Boolean).join(' / ');
  blocks.push({kind:'numberedKv', startAt:1, rows:[
    ['Nama', d.pegawaiNama],
    ['NIP.', d.pegawaiNip],
    ['Pangkat/Gol.', pangkatGol],
    ['Unit Kerja', d.pegawaiUnitKerja||ins.unit],
    ['Gaji Pokok Lama', d.gajiLama],
  ]});
  blocks.push({kind:'para', indent:false, text:'(Berdasarkan Surat Keputusan tentang gaji / pangkat yang ditetapkan)'});
  blocks.push({kind:'letteredKv', rows:[
    ['Oleh Pejabat', d.skLamaPejabat],
    ['Tanggal dan Nomor', d.skLamaTglNomor],
    ['Tanggal mulai berlaku', formatTanggalIndoPadded(d.skLamaMulaiBerlaku)],
    ['Masa kerja gol. pada tanggal tersebut', d.masaKerjaGolLama],
  ]});
  blocks.push({kind:'para', indent:false, text:'diberikan kenaikan gaji sehingga memperoleh :'});
  blocks.push({kind:'numberedKv', startAt:6, rows:[
    ['Gaji Pokok Baru', d.gajiBaru],
    ['Berdasarkan masa kerja', d.masaKerjaBaru],
    ['Golongan ruang', d.pegawaiGolongan],
    ['Mulai tanggal', formatTanggalIndoPadded(d.tmtBaru)],
  ]});
  const dasar = d.dasarPp && d.dasarPp.trim() ? d.dasarPp.trim() : 'Peraturan Pemerintah Republik Indonesia Nomor 5 Tahun 2024 Tanggal 26 Januari 2024';
  blocks.push({kind:'para', indent:true, text:`Dengan ini harap agar diproses sesuai dengan ${dasar}, dan kepada pegawai tersebut dapat dibayarkan penghasilannya berdasarkan gaji pokoknya yang baru.`});
  blocks.push({kind:'signature', place:ins.kota, date:d.tanggal, jabatan:ins.jabatanPenandatangan, nama:ins.namaPenandatangan, nip:ins.nipPenandatangan, noPlaceDate:true});
  if(cleanList(d.tembusan).length) blocks.push({kind:'tembusan', items:cleanList(d.tembusan)});
  return blocks;
}

function buildPltplh(d, ins){
  const blocks=[];
  blocks.push(buildKop(ins));
  const jenisPenuh = d.jenis || 'Pelaksana Tugas (Plt.)';
  const isPerpanjangan = d.tipePengajuan==='Perpanjangan';
  const headRows = [['Nomor', d.nomor], ['Sifat', d.sifat]];
  if(d.lampiran && d.lampiran.trim()) headRows.push(['Lampiran', d.lampiran.trim()]);
  headRows.push(['Perihal', `Usulan Penunjukan ${jenisPenuh}\n${d.jabatanLowong||''}`]);
  blocks.push({kind:'kv', rows:headRows});
  blocks.push({kind:'placedate', text:`${ins.kota||'...'}, ${formatTanggalIndoPadded(d.tanggal)}`});
  blocks.push({kind:'addrDi', jabatan:d.tujuanJabatan, kota:d.tujuanKota});
  if(isPerpanjangan){
    blocks.push({kind:'para', indent:true, text:`Berdasarkan ${lower1(d.dasarSk)}.`});
  } else {
    blocks.push({kind:'para', indent:true, text:`Berdasarkan ${lower1(d.dasarSk)}, terhitung mulai tanggal ${formatTanggalIndoPadded(d.tmtLowong)} yang bersangkutan sebagai berikut :`});
    blocks.push({kind:'kv', rows:[
      ['Nama', d.lamaNama],
      ['NIP', d.lamaNip||'-'],
      ['Pangkat/Gol', [d.lamaPangkat,d.lamaGolongan].filter(Boolean).join(' / ')||'-'],
      ['Jabatan', d.lamaJabatan||'-'],
    ]});
  }
  blocks.push({kind:'para', indent:true, marginTop:true, text:`Sehubungan dengan hal tersebut dan menunggu pejabat definitif, bersama ini kami mengajukan usulan penunjukan ${jenisPenuh} ${d.jabatanLowong||''} di Lingkungan ${insName(ins)} pertanggal ${formatTanggalIndoPadded(d.tmtUsulan)}. Adapun Aparatur Sipil Negara yang kami usulkan sebagai berikut :`});
  blocks.push({kind:'kv', rows:[
    ['Nama', d.baruNama],
    ['NIP', d.baruNip||'-'],
    ['Pangkat/Gol', [d.baruPangkat,d.baruGolongan].filter(Boolean).join(' / ')||'-'],
    ['Jabatan', d.baruJabatan||'-'],
  ]});
  const closing = d.penutup && d.penutup.trim() ? d.penutup.trim() : 'Demikian usulan ini kami sampaikan dan mohon petunjuk lebih lanjut.';
  blocks.push({kind:'para', indent:true, marginTop:true, text:closing});
  blocks.push({kind:'signature', place:ins.kota, date:d.tanggal, jabatan:ins.jabatanPenandatangan, nama:ins.namaPenandatangan, nip:ins.nipPenandatangan, noPlaceDate:true});
  return blocks;
}

function lower1(s){ s=String(s||'').trim(); if(!s) return '...'; return s.charAt(0).toLowerCase()+s.slice(1); }
function insName(ins){
  const first = String(ins.namaInstansi||'').split('\n').filter(Boolean)[0] || '';
  return (ins.unit && ins.unit.trim()) ? ins.unit.trim() : first.trim();
}

function buildLetter(type, d, ins){
  switch(type){
    case 'dinas': return buildDinas(d,ins);
    case 'nota': return buildNota(d,ins);
    case 'tugas': return buildTugas(d,ins);
    case 'spd': return buildSpd(d,ins);
    case 'sk': return buildSk(d,ins);
    case 'edaran': return buildEdaran(d,ins);
    case 'undangan': return buildUndangan(d,ins);
    case 'pengumuman': return buildPengumuman(d,ins);
    case 'pak': return buildPak(d,ins);
    case 'kgb': return buildKgb(d,ins);
    case 'pltplh': return buildPltplh(d,ins);
    default: return [];
  }
}

/* ============================================================
   RENDER BLOCKS -> HTML (untuk preview) & TEXT (untuk salin)
   ============================================================ */
function esc(s){ return String(s==null?'':s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;'); }

function blocksToHtml(blocks){
  let h='';
  blocks.forEach(b=>{
    if(b.kind==='kop'){
      const ins=b.instansi;
      const namaLines = String(ins.namaInstansi||'NAMA INSTANSI BELUM DIISI').split('\n').filter(Boolean);
      const nameHtml = namaLines.map(l=>`<div class="kline">${esc(l)}</div>`).join('');
      const unitHtml = ins.unit? `<div class="kline sub">${esc(ins.unit)}</div>` : '';
      const wilayahHtml = ins.wilayah? `<div class="kline sub">${esc(ins.wilayah)}</div>` : '';
      const addrParts=[ins.alamat,ins.kontak].filter(Boolean).join('   ');
      const addrHtml = addrParts? `<div class="kaddr">${esc(addrParts)}</div>` : '';
      const logoHtml = ins.logo? `<img class="kop-logo" src="${ins.logo}">` : '';
      h+=`<div class="kop">
        <div class="kop-row${ins.logo?'':' no-logo'}">
          ${logoHtml}
          <div class="kop-text">${nameHtml}${unitHtml}${wilayahHtml}${addrHtml}</div>
        </div>
      </div>`;
    } else if(b.kind==='kv'){
      h+='<table class="kv-table"><tbody>';
      b.rows.forEach(r=>{
        h+=`<tr><td class="k">${esc(r[0])}</td><td class="sep">:</td><td>${esc(r[1]||'-').replace(/\n/g,'<br>')}</td></tr>`;
      });
      h+='</tbody></table>';
    } else if(b.kind==='placedate'){
      h+=`<div class="right-block" style="margin-bottom:12px;">${esc(b.text).replace(/\n/g,'<br>')}</div>`;
    } else if(b.kind==='addr'){
      h+=`<div class="addr-block">Yth.<br>${esc(b.jabatan||'...')}<br>di<br>${b.alamat && b.alamat.trim() ? esc(b.alamat) : 'Tempat'}</div>`;
    } else if(b.kind==='addrDi'){
      h+=`<div class="addr-block">Yth. ${esc(b.jabatan||'...')}<br>Di &ndash;<br>&nbsp;&nbsp;&nbsp;&nbsp;${esc(b.kota||'...')}</div>`;
    } else if(b.kind==='numberedKv'){
      h+='<table class="kv-table"><tbody>';
      b.rows.forEach((r,i)=>{
        h+=`<tr><td style="width:20px; vertical-align:top;">${(b.startAt||1)+i}.</td><td style="width:150px; vertical-align:top;">${esc(r[0])}</td><td class="sep" style="vertical-align:top;">:</td><td>${esc(r[1]||'-')}</td></tr>`;
      });
      h+='</tbody></table>';
    } else if(b.kind==='letteredKv'){
      h+='<table class="kv-table" style="margin-left:18px;"><tbody>';
      b.rows.forEach((r,i)=>{
        h+=`<tr><td style="width:16px; vertical-align:top;">${alpha(i)}.</td><td style="width:190px; vertical-align:top;">${esc(r[0])}</td><td class="sep" style="vertical-align:top;">:</td><td>${esc(r[1]||'-')}</td></tr>`;
      });
      h+='</tbody></table>';
    } else if(b.kind==='para'){
      const cls='para'+(b.indent?' indent':'');
      const style=b.bold?'font-weight:700;':'';
      const mt=b.marginTop?'margin-top:14px;':'';
      h+=`<p class="${cls}" style="${style}${mt}">${esc(b.text)}</p>`;
    } else if(b.kind==='lettered'){
      h+='<ol class="lettered" style="list-style:none; padding-left:0;">';
      b.items.forEach(it=>{
        h+=`<li style="display:flex; gap:6px;"><span style="width:18px;flex-shrink:0;">${it.label}</span><span style="text-align:justify;">${esc(it.text)}</span></li>`;
      });
      h+='</ol>';
    } else if(b.kind==='numbered'){
      h+='<ol class="lettered" style="list-style:none; padding-left:0;">';
      b.items.forEach(it=>{
        h+=`<li style="display:flex; gap:6px;"><span style="width:22px;flex-shrink:0;">${it.label}</span><span style="text-align:justify;">${esc(it.text)}</span></li>`;
      });
      h+='</ol>';
    } else if(b.kind==='doctitle'){
      h+=`<div class="doc-title">
        <div class="t1" style="${b.spaced?'letter-spacing:3px;':''}">${esc(b.t1)}</div>
        <div class="t2">${esc(b.t2)}</div>
        ${b.t3? `<div class="t2" style="margin-top:6px;">${esc(b.t3)}</div>`:''}
        ${b.t4? `<div class="t3">${esc(b.t4)}</div>`:''}
      </div>`;
    } else if(b.kind==='sktitle'){
      h+=`<div class="doc-title">
        <div class="t1">KEPUTUSAN ${esc((b.instansi||'INSTANSI').toUpperCase())}</div>
        <div class="t2">NOMOR ${esc(b.nomor)}</div>
        <div class="t2" style="margin-top:6px;">TENTANG</div>
        <div class="t3">${esc(String(b.judul||'').toUpperCase())}</div>
      </div>`;
    } else if(b.kind==='centerbold'){
      h+=`<div class="center-block" style="font-weight:700; margin:14px 0;">${esc(b.text)}</div>`;
    } else if(b.kind==='diktum'){
      h+=`<div class="diktum-row"><div class="dk">${esc(b.label)}</div><div class="dv">: ${esc(b.text)}</div></div>`;
    } else if(b.kind==='petugasTable'){
      h+='<div style="margin-bottom:11px;">';
      (b.items||[]).filter(p=>p.nama&&p.nama.trim()).forEach((p,i)=>{
        const pgol = [p.pangkat, p.golongan].filter(Boolean).join(' / ');
        h+=`<table class="kv-table" style="margin-bottom:6px;"><tbody>
          <tr><td class="k">${i+1}. Nama</td><td class="sep">:</td><td>${esc(p.nama)}</td></tr>
          <tr><td class="k">&nbsp;&nbsp;&nbsp;NIP</td><td class="sep">:</td><td>${esc(p.nip||'-')}</td></tr>
          <tr><td class="k">&nbsp;&nbsp;&nbsp;Pangkat/Gol.</td><td class="sep">:</td><td>${esc(pgol||'-')}</td></tr>
          <tr><td class="k">&nbsp;&nbsp;&nbsp;Jabatan</td><td class="sep">:</td><td>${esc(p.jabatan||'-')}</td></tr>
        </tbody></table>`;
      });
      h+='</div>';
    } else if(b.kind==='aktable'){
      let rowsHtml = b.rows.map((r,i)=>`<tr><td>${i+1}</td><td style="text-align:left;">${esc(r[0])}</td><td>${esc(r[1]||'-')}</td><td>${esc(r[2]||'-')}</td><td>${esc(r[3]||'-')}</td><td>${esc(r[4]||'-')}</td></tr>`).join('');
      h+=`<table class="ak-table"><thead><tr><th>No</th><th style="text-align:left;">Uraian</th><th>Lama</th><th>Baru</th><th>Jumlah</th><th>Ket.</th></tr></thead><tbody>${rowsHtml}
        <tr class="total"><td colspan="2">JUMLAH ANGKA KREDIT KUMULATIF</td><td>${esc(b.total[0]||'-')}</td><td>${esc(b.total[1]||'-')}</td><td>${esc(b.total[2]||'-')}</td><td>${esc(b.total[3]||'-')}</td></tr>
      </tbody></table>`;
    } else if(b.kind==='keteranganTable'){
      let rowsHtml = b.rows.map(r=>`<tr><td style="text-align:left;">${esc(r[0])}</td><td>${esc(r[1]||'-')}</td><td>${esc(r[2]||'-')}</td></tr>`).join('');
      h+=`<table class="ak-table"><thead><tr><th style="text-align:left;">Keterangan</th><th>Pangkat</th><th>Jenjang Jabatan</th></tr></thead><tbody>${rowsHtml}</tbody></table>`;
    } else if(b.kind==='spdGrid'){
      let rowsHtml = b.rows.map(r=>`<tr><td style="width:20px;">${esc(r.no)}</td><td style="text-align:left; width:36%;">${esc(r.label).replace(/\n/g,'<br>')}</td><td style="text-align:left;">${(r.lines&&r.lines.length?r.lines:['-']).map(l=>esc(l||'-')).join('<br>')}</td></tr>`).join('');
      h+=`<table class="ak-table">${rowsHtml}</table>`;
    } else if(b.kind==='blankSig'){
      h+=`<div style="text-align:center; margin:10px 0; font-size:12pt;">.................................<br>NIP.</div>`;
    } else if(b.kind==='asliBlock'){
      h+=`<div style="margin:12px 0; font-size:12pt;"><strong>ASLI</strong> Penetapan Angka Kredit untuk:<br>${esc(b.nama)}</div>`;
    } else if(b.kind==='signature'){
      const placeDate = b.ditetapkan
        ? `Ditetapkan di ${esc(b.place||'...')}<br>pada tanggal ${esc(formatTanggalIndo(b.date))}`
        : (b.noPlaceDate ? '' : `${esc(b.place||'...')}, ${esc(formatTanggalIndo(b.date))}`);
      const elektronik = (state.instansi.jenisTtd||'Ditandatangani secara elektronik') !== 'Tanda tangan & cap basah';
      const sigMiddle = elektronik
        ? `<div class="sig-elektronik">Ditandatangani secara<br>elektronik</div>`
        : `<div class="sig-space"><div class="stamp" style="width:64px;height:64px;border:1.5px dashed #9a9382;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:8.5px;color:#9a9382;text-align:center;line-height:1.3;">tanda tangan<br>&amp; cap dinas</div></div>`;
      h+=`<div class="right-block" style="margin-top:16px; text-align:center;">
        ${placeDate? `<div style="text-align:${b.ditetapkan?'left':'center'};">${placeDate}</div>`:''}
        ${b.atasNama && b.atasNama.trim() ? `<div style="margin-top:${placeDate?'4px':'0'};">An. ${esc(b.atasNama.trim())}</div>` : ''}
        <div style="margin-top:${placeDate||( b.atasNama&&b.atasNama.trim())?'2px':'0'};">${esc(b.jabatan||'...')},</div>
        ${sigMiddle}
        <div class="sig-name">${esc(b.nama||'( ......................... )')}</div>
        ${b.nip? `<div>NIP. ${esc(b.nip)}</div>`:''}
      </div>`;
    } else if(b.kind==='tembusan'){
      h+=`<div class="tembusan"><div class="t-label">Tembusan:</div><ol style="margin:0; padding-left:18px;">`;
      b.items.forEach(t=>{ h+=`<li>${esc(t)}</li>`; });
      h+='</ol></div>';
    } else if(b.kind==='rule'){
      h+=`<hr style="border:none; border-top:1px solid #444; margin:10px 0 12px;">`;
    } else if(b.kind==='footnote'){
      h+=`<div class="print-footnote">${esc(b.text)}${b.tagline? `<br><em>${esc(b.tagline)}</em>`:''}</div>`;
    }
  });
  return h;
}

function blocksToText(blocks){
  let lines=[];
  blocks.forEach(b=>{
    if(b.kind==='kop'){
      const ins=b.instansi;
      String(ins.namaInstansi||'NAMA INSTANSI').split('\n').filter(Boolean).forEach(l=>lines.push(l.toUpperCase()));
      if(ins.unit) lines.push(ins.unit.toUpperCase());
      if(ins.wilayah) lines.push(ins.wilayah.toUpperCase());
      const addrParts=[ins.alamat,ins.kontak].filter(Boolean).join('   ');
      if(addrParts) lines.push(addrParts);
      lines.push('='.repeat(40));
    } else if(b.kind==='kv'){
      b.rows.forEach(r=>lines.push(`${r[0]} : ${r[1]||'-'}`));
      lines.push('');
    } else if(b.kind==='placedate'){
      lines.push(b.text); lines.push('');
    } else if(b.kind==='addr'){
      lines.push('Yth.');
      lines.push(b.jabatan||'...');
      lines.push('di');
      lines.push(b.alamat && b.alamat.trim() ? b.alamat : 'Tempat');
      lines.push('');
    } else if(b.kind==='addrDi'){
      lines.push(`Yth. ${b.jabatan||'...'}`);
      lines.push('Di \u2013');
      lines.push('    '+(b.kota||'...'));
      lines.push('');
    } else if(b.kind==='numberedKv'){
      b.rows.forEach((r,i)=>lines.push(`${(b.startAt||1)+i}. ${r[0]} : ${r[1]||'-'}`));
      lines.push('');
    } else if(b.kind==='letteredKv'){
      b.rows.forEach((r,i)=>lines.push(`   ${alpha(i)}. ${r[0]} : ${r[1]||'-'}`));
      lines.push('');
    } else if(b.kind==='para'){
      lines.push(b.text); lines.push('');
    } else if(b.kind==='lettered' || b.kind==='numbered'){
      b.items.forEach(it=>lines.push(`${it.label} ${it.text}`));
      lines.push('');
    } else if(b.kind==='doctitle'){
      lines.push(b.t1); lines.push(b.t2);
      if(b.t3) lines.push(b.t3);
      if(b.t4) lines.push(b.t4);
      lines.push('');
    } else if(b.kind==='sktitle'){
      lines.push(`KEPUTUSAN ${(b.instansi||'INSTANSI').toUpperCase()}`);
      lines.push(`NOMOR ${b.nomor}`);
      lines.push('TENTANG');
      lines.push(String(b.judul||'').toUpperCase());
      lines.push('');
    } else if(b.kind==='centerbold'){
      lines.push(b.text); lines.push('');
    } else if(b.kind==='diktum'){
      lines.push(`${b.label} : ${b.text}`);
    } else if(b.kind==='petugasTable'){
      (b.items||[]).filter(p=>p.nama&&p.nama.trim()).forEach((p,i)=>{
        const pgol = [p.pangkat, p.golongan].filter(Boolean).join(' / ');
        lines.push(`${i+1}. Nama         : ${p.nama}`);
        lines.push(`   NIP          : ${p.nip||'-'}`);
        lines.push(`   Pangkat/Gol. : ${pgol||'-'}`);
        lines.push(`   Jabatan      : ${p.jabatan||'-'}`);
      });
      lines.push('');
    } else if(b.kind==='aktable'){
      lines.push('PENETAPAN ANGKA KREDIT (Lama / Baru / Jumlah / Ket.)');
      b.rows.forEach((r,i)=>lines.push(`${i+1}. ${r[0]}: ${r[1]||'-'} / ${r[2]||'-'} / ${r[3]||'-'} / ${r[4]||'-'}`));
      lines.push(`JUMLAH ANGKA KREDIT KUMULATIF: ${b.total[0]||'-'} / ${b.total[1]||'-'} / ${b.total[2]||'-'} / ${b.total[3]||'-'}`);
      lines.push('');
    } else if(b.kind==='keteranganTable'){
      lines.push('Keterangan (Pangkat / Jenjang Jabatan)');
      b.rows.forEach(r=>lines.push(`${r[0]}: ${r[1]||'-'} / ${r[2]||'-'}`));
      lines.push('');
    } else if(b.kind==='spdGrid'){
      b.rows.forEach(r=>{
        const lbl = r.label.replace(/\n/g,' / ');
        const val = (r.lines&&r.lines.length?r.lines:['-']).map(l=>l||'-').join(' | ');
        lines.push(`${r.no}. ${lbl} : ${val}`);
      });
      lines.push('');
    } else if(b.kind==='blankSig'){
      lines.push('.................................');
      lines.push('NIP.');
      lines.push('');
    } else if(b.kind==='asliBlock'){
      lines.push('ASLI Penetapan Angka Kredit untuk:');
      lines.push(b.nama);
      lines.push('');
    } else if(b.kind==='signature'){
      if(b.ditetapkan){
        lines.push(`Ditetapkan di ${b.place||'...'}`);
        lines.push(`pada tanggal ${formatTanggalIndo(b.date)}`);
      } else if(!b.noPlaceDate){
        lines.push(`${b.place||'...'}, ${formatTanggalIndo(b.date)}`);
      }
      if(b.atasNama && b.atasNama.trim()) lines.push(`An. ${b.atasNama.trim()}`);
      lines.push(`${b.jabatan||'...'},`);
      const elektronik = (state.instansi.jenisTtd||'Ditandatangani secara elektronik') !== 'Tanda tangan & cap basah';
      if(elektronik){
        lines.push(''); lines.push('Ditandatangani secara elektronik'); lines.push('');
      } else {
        lines.push(''); lines.push(''); lines.push('');
      }
      lines.push(b.nama||'( ......................... )');
      if(b.nip) lines.push(`NIP. ${b.nip}`);
      lines.push('');
    } else if(b.kind==='tembusan'){
      lines.push('Tembusan:');
      b.items.forEach((t,i)=>lines.push(`${i+1}. ${t}`));
    } else if(b.kind==='rule'){
      lines.push('----------------------------------------');
    } else if(b.kind==='footnote'){
      lines.push('');
      lines.push(b.text);
      if(b.tagline) lines.push(b.tagline);
    }
  });
  return lines.join('\n');
}

/* ============================================================
   ACTIONS: simpan draf, salin, cetak
   ============================================================ */
async function saveDraft(){
  const id = state.currentDraftId || ('d'+Date.now());
  const def=FIELD_DEFS[state.activeType];
  const titleField = state.formData.hal || state.formData.judul || state.formData.tentang || state.formData.acara || state.formData.pegawaiNama || TYPES[state.activeType].name;
  const draft = {type:state.activeType, formData:state.formData, updatedAt:Date.now()};
  const ok = await storageSet('draft:'+id, draft);
  if(!ok){ showToast('Gagal menyimpan draf'); return; }
  state.drafts = state.drafts.filter(x=>x.id!==id);
  state.drafts.unshift({id, type:state.activeType, title:titleField, updatedAt:Date.now()});
  await storageSet('drafts-index', state.drafts);
  state.currentDraftId=id;
  showToast('Draf tersimpan');
  render();
}
async function deleteDraft(id, ev){
  if(ev) ev.stopPropagation();
  await storageDelete('draft:'+id);
  state.drafts = state.drafts.filter(x=>x.id!==id);
  await storageSet('drafts-index', state.drafts);
  showToast('Draf dihapus');
  render();
}
function copyText(){
  const blocks = buildLetter(state.activeType, state.formData, state.instansi);
  const text = blocksToText(blocks);
  navigator.clipboard.writeText(text).then(()=>showToast('Teks surat disalin')).catch(()=>{
    showToast('Gagal menyalin — salin manual dari pratinjau');
  });
}
function printLetter(){
  const blocks = buildLetter(state.activeType, state.formData, state.instansi);
  const html = blocksToHtml(blocks);
  const host = document.getElementById('print-host');
  const useF4 = state.activeType==='sk' || state.activeType==='kgb'; // F4/Folio: Surat Keputusan & Kenaikan Gaji Berkala
  const pageSize = useF4 ? '215mm 330mm' : 'A4';
  host.innerHTML = `
    <style>@page{ size:${pageSize}; margin:20mm 20mm 20mm 25mm; }</style>
    <div id="print-area" class="paper" style="box-shadow:none;border:none;max-width:720px;margin:0 auto;">${html}</div>`;
  setTimeout(()=>window.print(), 80);
}

/* ============================================================
   RENDER: HOME
   ============================================================ */
function getGreeting(){
  const h = new Date().getHours();
  if(h<11) return 'Selamat Pagi';
  if(h<15) return 'Selamat Siang';
  if(h<18) return 'Selamat Sore';
  return 'Selamat Malam';
}
function renderHome(){
  let h='';
  const unitName = state.instansi.unit || (state.instansi.namaInstansi ? String(state.instansi.namaInstansi).split('\n')[0] : '');
  const todayLong = formatTanggalIndo(todayISO());
  h+=`<div class="welcome-hero">
    <div class="wh-ring"><img class="wh-logo" src="${getLogoUrl()}"></div>
    <div class="wh-greeting">${getGreeting()}</div>
    <h2 class="wh-title">Selamat Datang${unitName? ',' : ''}</h2>
    ${unitName? `<div class="wh-unit">${esc(unitName)}</div>` : ''}
    <div class="wh-divider"></div>
    <div class="wh-date">${esc(todayLong)}</div>
    <div class="wh-stats">
      <button type="button" class="wh-stat" onclick="void(0)"><div class="wh-num">${state.drafts.length}</div><div class="wh-label">Draf Tersimpan</div></button>
      <button type="button" class="wh-stat" onclick="goPegawai()"><div class="wh-num">${state.pegawaiList.length}</div><div class="wh-label">Data Pegawai</div></button>
      <button type="button" class="wh-stat" onclick="openNaskahMenu()"><div class="wh-num">${Object.keys(TYPES).length}</div><div class="wh-label">Jenis Naskah</div></button>
    </div>
  </div>`;

  const alerts = getAllPegawaiAlerts();
  if(alerts.length){
    const hasOverdue = alerts.some(a=>a.status==='overdue');
    const overdueCount = alerts.filter(a=>a.status==='overdue').length;
    const soonCount = alerts.length-overdueCount;
    const summaryParts=[];
    if(overdueCount) summaryParts.push(overdueCount+' lewat jatuh tempo');
    if(soonCount) summaryParts.push(soonCount+' akan jatuh tempo');
    h+=`<button type="button" class="alert-banner ${hasOverdue?'overdue':'soon'}" onclick="goPegawai()">
      <div class="ab-icon">${ICON.alert}</div>
      <div class="ab-text">
        <strong>${alerts.length} Peringatan Kepegawaian</strong>
        <span>${esc(summaryParts.join(' · '))} — kenaikan pangkat/gaji berkala</span>
      </div>
      <div class="chev">${ICON.chevron}</div>
    </button>`;
  }

  if(state.drafts.length){
    h+=`<div class="section-label">Draf Tersimpan</div>`;
    state.drafts.slice(0,6).forEach(dr=>{
      h+=`<div class="draft-card" onclick="openDraft('${dr.id}')">
        <div class="draft-info">
          <h4>${esc(dr.title||TYPES[dr.type].name)}</h4>
          <p>${esc(TYPES[dr.type].name)} · ${new Date(dr.updatedAt).toLocaleDateString('id-ID',{day:'numeric',month:'short',year:'numeric'})}</p>
        </div>
        <button class="icon-btn danger" onclick="deleteDraft('${dr.id}', event)">${ICON.trash}</button>
      </div>`;
    });
  } else {
    h+=`<div class="empty">Belum ada draf tersimpan. Buka menu ☰ untuk mulai membuat naskah dinas.</div>`;
  }

  return h;
}

/* ============================================================
   RENDER: DATA PEGAWAI
   ============================================================ */
function renderPegawai(){
  let h=`<div class="cat-desc" style="margin-top:2px;">Daftar pegawai tersimpan di perangkat/akun Anda, lengkap dengan status, pangkat, golongan, dan TMT. Peringatan otomatis muncul H-90 hari sebelum kenaikan pangkat (4 tahun), gaji berkala (2 tahun), dan pengajuan Satyalancana Karya Satya setiap kelipatan 10 tahun masa kerja.</div>`;
  h+=`<button type="button" class="add-btn" onclick="goPegawaiTable()" style="margin-bottom:10px;">${ICON.doc} Lihat sebagai Tabel / Unduh PDF</button>`;
  if(state.pegawaiList.length===0){
    h+=`<div class="empty">Belum ada data pegawai. Ketuk "Tambah Pegawai" di bawah untuk mulai.</div>`;
  } else {
    state.pegawaiList.forEach(p=>{
      const statusLine = p.status==='Honorer' && p.statusHonorer ? `${p.status} — ${p.statusHonorer}` : p.status;
      const pg = [statusLine, p.jenisJabatan, p.pangkat, p.golongan].filter(Boolean).join(' · ');
      const pendidikanLabel = p.pendidikanTerakhir ? (p.jurusanPendidikan ? `${p.pendidikanTerakhir} ${p.jurusanPendidikan}` : p.pendidikanTerakhir) : '';
      const line2 = [p.jabatan||'-', p.nip? 'NIP '+p.nip : '', pendidikanLabel].filter(Boolean).join(' · ');
      const jfLine = p.jenisJabatan==='Jabatan Fungsional' ? [p.jenjangJf, p.nilaiPak? 'AK '+p.nilaiPak : ''].filter(Boolean).join(' · ') : '';
      const alerts = getPegawaiAlerts(p);
      const masaKerja = getMasaKerjaTahun(p.tanggalPengangkatan);
      h+=`<div class="draft-card" onclick="openPegawaiModal('${p.id}')" style="align-items:flex-start;">
        <div class="type-badge" style="width:38px;height:38px;flex-shrink:0;">${ICON.users}</div>
        <div class="draft-info" style="margin-left:2px;">
          <h4>${esc(p.nama)}</h4>
          <p>${esc(line2)}</p>
          ${p.seksi? `<p style="margin-top:1px;">${esc(p.seksi)}</p>` : ''}
          ${pg? `<p style="margin-top:1px;">${esc(pg)}</p>` : ''}
          ${jfLine? `<p style="margin-top:1px;">${esc(jfLine)}</p>` : ''}
          ${masaKerja!==null? `<p style="margin-top:1px;">Masa kerja: ${masaKerja} tahun</p>` : ''}
          ${(p.tmtJabatan||p.tmtPangkat||p.tmtGajiBerkala)? `<p style="margin-top:3px; font-size:10.5px; color:var(--muted);">${[
              p.tmtJabatan? 'TMT Jabatan '+formatTanggalIndo(p.tmtJabatan): '',
              p.tmtPangkat? 'TMT Pangkat '+formatTanggalIndo(p.tmtPangkat): '',
              p.tmtGajiBerkala? 'TMT Gaji Berkala '+formatTanggalIndo(p.tmtGajiBerkala): '',
            ].filter(Boolean).join(' · ')}</p>` : ''}
          ${(p.statusTambahan && p.statusTambahan!=='-')? `<p style="margin-top:1px; font-weight:600; color:var(--navy);">${esc(p.statusTambahan)}${p.jabatanPltPlh? ' — '+esc(p.jabatanPltPlh):''}${p.jumlahPengajuanPltPlh? ' · Diusulkan '+esc(p.jumlahPengajuanPltPlh)+'x':''}</p>` : ''}
          ${alerts.length? `<div>${alerts.map(alertChipHtml).join('')}</div>` : ''}
        </div>
        <button class="icon-btn" onclick="event.stopPropagation(); openPegawaiModal('${p.id}')">${ICON.edit}</button>
        <button class="icon-btn danger" onclick="deletePegawaiEntry('${p.id}', event)">${ICON.trash}</button>
      </div>`;
    });
  }
  return h;
}

/* ============================================================
   RENDER: TABEL PEGAWAI (untuk cetak/unduh PDF)
   ============================================================ */
function goPegawaiTable(){ state.screen='pegawaiTable'; state.pegawaiTableFilter=''; render(); window.scrollTo(0,0); }
function setPegawaiTableFilter(val){ state.pegawaiTableFilter=val; render(); }
function renderPegawaiTableScreen(){
  if(state.pegawaiList.length===0){
    return `<div class="empty">Belum ada data pegawai untuk ditampilkan sebagai tabel.</div>`;
  }
  const seksiList = [...new Set(state.pegawaiList.map(p=>p.seksi).filter(Boolean))].sort();
  const filtered = state.pegawaiTableFilter ? state.pegawaiList.filter(p=>p.seksi===state.pegawaiTableFilter) : state.pegawaiList;
  const filterHtml = seksiList.length ? `<div class="field no-print" style="margin-bottom:10px;">
      <label>Filter per Seksi/Sub Bagian</label>
      <select onchange="setPegawaiTableFilter(this.value)">
        <option value="">Semua Seksi/Sub Bagian</option>
        ${seksiList.map(s=>`<option value="${esc(s)}" ${s===state.pegawaiTableFilter?'selected':''}>${esc(s)}</option>`).join('')}
      </select>
    </div>` : '';
  if(filtered.length===0){
    return `${filterHtml}<div class="empty">Tidak ada pegawai pada seksi/sub bagian ini.</div>`;
  }
  let rows = filtered.map((p,i)=>{
    const statusLine = p.status==='Honorer' && p.statusHonorer ? `${p.status} - ${p.statusHonorer}` : (p.status||'-');
    return `<tr>
      <td>${i+1}</td>
      <td style="text-align:left;">${esc(p.nama)}</td>
      <td>${esc(p.nip||'-')}</td>
      <td style="text-align:left;">${esc(statusLine)}</td>
      <td>${esc(p.jenisJabatan||'-')}</td>
      <td style="text-align:left;">${esc(p.seksi||'-')}</td>
      <td style="text-align:left;">${esc(p.jabatan||'-')}</td>
      <td>${esc([p.pangkat,p.golongan].filter(Boolean).join(' / ')||'-')}</td>
      <td>${esc(p.pendidikanTerakhir||'-')}</td>
      <td>${p.tmtJabatan? esc(formatTanggalIndo(p.tmtJabatan)) : '-'}</td>
      <td>${p.tmtPangkat? esc(formatTanggalIndo(p.tmtPangkat)) : '-'}</td>
      <td>${p.tmtGajiBerkala? esc(formatTanggalIndo(p.tmtGajiBerkala)) : '-'}</td>
    </tr>`;
  }).join('');
  return `<div class="cat-desc no-print" style="margin-top:2px;">Tabel seluruh Data Pegawai. Ketuk "Cetak / Unduh PDF" untuk membuka dialog cetak — pilih "Simpan sebagai PDF" pada tujuan cetak.</div>
    ${filterHtml}
    <div style="overflow-x:auto; -webkit-overflow-scrolling:touch;">
    <table class="ak-table" id="pegawai-table-view" style="font-size:10.5px; min-width:1000px; font-family:'Bookman Old Style','URW Bookman',Georgia,serif;">
      <thead><tr>
        <th>No</th><th style="text-align:left;">Nama</th><th>NIP</th><th style="text-align:left;">Status</th>
        <th>Jenis Jabatan</th><th style="text-align:left;">Seksi/Sub Bagian</th><th style="text-align:left;">Jabatan</th><th>Pangkat/Gol.</th><th>Pendidikan</th>
        <th>TMT Jabatan</th><th>TMT Pangkat</th><th>TMT KGB</th>
      </tr></thead>
      <tbody>${rows}</tbody>
    </table>
    </div>`;
}
function printPegawaiTable(){
  const html = renderPegawaiTableScreen();
  const host = document.getElementById('print-host');
  host.innerHTML = `
    <style>@page{ size:A4 landscape; margin:14mm; }
      #print-area table{width:100%; border-collapse:collapse;}
      #print-area .no-print{display:none;}
    </style>
    <div id="print-area" class="paper" style="box-shadow:none;border:none;max-width:100%;margin:0 auto;">
      <h2 style="font-family:'Bookman Old Style',Georgia,serif; text-align:center; margin-bottom:14px;">DAFTAR PEGAWAI${state.pegawaiTableFilter? ' — '+esc(state.pegawaiTableFilter) : ''}</h2>
      ${html}
    </div>`;
  setTimeout(()=>window.print(), 80);
}

/* ============================================================
   RENDER: FORM
   ============================================================ */
function fieldHtml(f, path){
  const val = state.formData[f.k];
  const idAttr = `data-field="${f.k}"`;
  if(f.type==='pegawaiFill'){
    const target = f.target || 'pegawai';
    return `<div class="field"><label>${esc(f.label)}</label>
      <button type="button" class="add-btn" onclick="openPegawaiPicker('${target}','single')">${ICON.users} Pilih dari Data Pegawai</button>
      <span class="hint">Mengisi otomatis field Nama, NIP, Pangkat, Golongan, TMT, Jabatan &amp; Unit Kerja di bawah — bisa disunting manual bila perlu.</span>
    </div>`;
  }
  if(f.type==='akRow'){
    const subs = [['Lama','Lama'],['Baru','Baru'],['Jumlah','Jumlah'],['Ket','Ket.']];
    const inputs = subs.map(([suf,lbl])=>{
      const key = f.k+suf;
      const v = state.formData[key]||'';
      return `<div style="flex:1; min-width:0;">
        <label style="font-size:9.5px; color:var(--muted); display:block; margin-bottom:3px; font-weight:600;">${lbl}</label>
        <input type="text" data-field="${key}" value="${esc(v)}" style="width:100%; border:1px solid var(--line); border-radius:7px; padding:7px 6px; font-size:12px; font-family:inherit;">
      </div>`;
    }).join('');
    const labelText = f.k==='akLain' ? (state.formData.akLainLabel && state.formData.akLainLabel.trim() ? state.formData.akLainLabel.trim() : f.label) : f.label;
    return `<div class="field"><label>${esc(labelText)}</label><div style="display:flex; gap:6px;">${inputs}</div></div>`;
  }
  if(f.type==='text'){
    const isNomor = f.k==='nomor' && state.activeType!=='spd';
    let helper='';
    if(isNomor){
      helper = `<button type="button" class="add-btn" style="margin-top:7px;" onclick="toggleNomorHelper()">${ICON.plus} Bantu Susun Nomor (Format ATR/BPN)</button>`;
      if(state.nomorHelperOpen){
        helper += `<div class="petugas-card" style="margin-top:8px;">
          <div class="field"><label>Nomor Urut</label><input type="text" data-nh="urut" placeholder="mis. 37"></div>
          <div class="field"><label>Kode Klasifikasi Arsip (opsional)</label><input type="text" data-nh="klas" placeholder="mis. UP.03.02"></div>
          <span class="hint" style="display:block; margin-bottom:8px;">Disusun sebagai: nomor urut / kode jenis-kode wilayah.kode klasifikasi / bulan romawi / tahun — mengikuti kaidah Permen ATR/BPN No. 9/2018. Kode wilayah diambil dari Profil Instansi; bulan &amp; tahun diambil dari Tanggal Surat di bawah.</span>
          <button type="button" class="btn btn-primary" style="padding:10px;" onclick="applyNomorHelper()">${ICON.check} Terapkan ke Nomor Surat</button>
        </div>`;
      }
    }
    return `<div class="field"><label>${esc(f.label)}${f.required?' *':''}</label>
      <input type="text" ${idAttr} value="${esc(val)}" placeholder="${esc(f.ph||'')}">
      ${f.hint?`<span class="hint">${esc(f.hint)}</span>`:''}${helper}</div>`;
  }
  if(f.type==='textarea'){
    return `<div class="field"><label>${esc(f.label)}${f.required?' *':''}</label>
      <textarea ${idAttr} placeholder="${esc(f.ph||'')}">${esc(val)}</textarea>
      ${f.hint?`<span class="hint">${esc(f.hint)}</span>`:''}</div>`;
  }
  if(f.type==='date'){
    return `<div class="field"><label>${esc(f.label)}${f.required?' *':''}</label>
      <input type="date" ${idAttr} value="${esc(val)}"></div>`;
  }
  if(f.type==='select'){
    const opts=f.options.map(o=>`<option value="${esc(o)}" ${o===val?'selected':''}>${o? esc(o) : '(Tidak dicantumkan)'}</option>`).join('');
    return `<div class="field"><label>${esc(f.label)}${f.required?' *':''}</label>
      <select ${idAttr}>${opts}</select></div>`;
  }
  if(f.type==='list'){
    let items = (val||['']).map((v,i)=>`
      <div class="list-item">
        <span class="bullet">${i+1}.</span>
        <textarea data-list="${f.k}" data-idx="${i}" placeholder="${esc(f.ph||'')}">${esc(v)}</textarea>
        <button class="list-remove" onclick="removeListItem('${f.k}',${i})">${ICON.x}</button>
      </div>`).join('');
    return `<div class="field"><label>${esc(f.label)}${f.required?' *':''}</label>
      <div class="list-editor">${items}
        <button type="button" class="add-btn" onclick="addListItem('${f.k}')">${ICON.plus} Tambah Poin</button>
      </div>
      ${f.hint?`<span class="hint">${esc(f.hint)}</span>`:''}</div>`;
  }
  if(f.type==='petugas'){
    let cards=(val||[]).map((p,i)=>`
      <div class="petugas-card">
        <button class="list-remove" onclick="removePetugas('${f.k}',${i})">${ICON.x}</button>
        <div class="field"><label>Nama Lengkap</label><input type="text" data-petugas="${f.k}" data-idx="${i}" data-pf="nama" value="${esc(p.nama)}" placeholder="Nama pegawai"></div>
        <div class="field"><label>NIP</label><input type="text" data-petugas="${f.k}" data-idx="${i}" data-pf="nip" value="${esc(p.nip)}" placeholder="NIP (jika ada)"></div>
        <div class="row2">
          <div class="field"><label>Pangkat</label><input type="text" data-petugas="${f.k}" data-idx="${i}" data-pf="pangkat" value="${esc(p.pangkat||'')}" placeholder="mis. Penata Muda"></div>
          <div class="field"><label>Golongan</label><input type="text" data-petugas="${f.k}" data-idx="${i}" data-pf="golongan" value="${esc(p.golongan||'')}" placeholder="mis. III/a"></div>
        </div>
        <div class="field"><label>Jabatan</label><input type="text" data-petugas="${f.k}" data-idx="${i}" data-pf="jabatan" value="${esc(p.jabatan)}" placeholder="Jabatan"></div>
      </div>`).join('');
    return `<div class="field"><label>${esc(f.label)}${f.required?' *':''}</label>
      ${cards}
      <div style="display:flex; gap:8px;">
        <button type="button" class="add-btn" style="flex:1;" onclick="addPetugas('${f.k}')">${ICON.plus} Tambah Manual</button>
        <button type="button" class="add-btn" style="flex:1;" onclick="openPegawaiPicker('${f.k}')">${ICON.users} Dari Data Pegawai</button>
      </div></div>`;
  }
  return '';
}

function renderForm(){
  const t=TYPES[state.activeType];
  const defs=FIELD_DEFS[state.activeType];
  let h=`<div class="helper-note">${ICON.info} Data instansi (kop surat, penandatangan) diambil dari <strong>Profil Instansi</strong>. Ketuk ikon gerigi di pojok atas untuk mengatur atau melengkapinya.</div>`;

  if(state.activeType==='pltplh' && (!state.formData.sifat || state.formData.sifat==='Biasa')){
    h+=`<div class="alert-banner soon" style="cursor:default;">
      <div class="ab-icon">${ICON.alert}</div>
      <div class="ab-text"><strong>Sifat Surat Belum Valid</strong><span>Sifat "Biasa" tidak dapat dipakai untuk Usulan Plt./Plh. Pilih Penting, Segera, atau Rahasia pada bagian Data Surat sebelum melanjutkan.</span></div>
    </div>`;
  }
  if(state.activeType==='pltplh' && state.formData.baruNip){
    const match = state.pegawaiList.find(p=> p.nip && p.nip===state.formData.baruNip);
    const jumlahPlt = match ? (parseInt(match.jumlahPengajuanPltPlh,10)||0) : 0;
    if(jumlahPlt>=2){
      h+=`<div class="alert-banner overdue" style="cursor:default;">
        <div class="ab-icon">${ICON.alert}</div>
        <div class="ab-text"><strong>Batas Pengajuan Tercapai</strong><span>${esc(state.formData.baruNama||'Pegawai ini')} sudah diusulkan Plt./Plh. ${jumlahPlt}x. Sesuai ketentuan, pengajuan/perpanjangan maksimal 2 kali untuk jabatan yang sama.</span></div>
      </div>`;
    }
  }

  const groups=[];
  defs.filter(f=> !(f.hideWhen && f.hideWhen(state.formData))).forEach(f=>{
    const g = f.group || null;
    const last = groups[groups.length-1];
    if(last && last.name===g) last.fields.push(f);
    else groups.push({name:g, fields:[f]});
  });
  groups.forEach((grp,i)=>{
    h+=`<div class="form-block"><h2><span class="num">${i+1}</span>${esc(grp.name || ('Data '+t.name))}</h2>`;
    grp.fields.forEach(f=>{ h+=fieldHtml(f); });
    h+='</div>';
  });
  return h;
}

/* ============================================================
   RENDER: PREVIEW
   ============================================================ */
function renderPreview(){
  const blocks = buildLetter(state.activeType, state.formData, state.instansi);
  const html = blocksToHtml(blocks);
  return `
    <div class="section-label" style="margin-top:2px;">Pratinjau Naskah</div>
    <div class="cat-desc">Periksa kembali sebelum dicetak. Bagian tanda tangan &amp; cap perlu ditandatangani secara fisik atau digital sesuai kewenangan.</div>
    <div class="paper-wrap"><div class="paper">${html}</div></div>
  `;
}

/* ============================================================
   RENDER: INSTANSI MODAL
   ============================================================ */
function instansiFieldHtml(f){
  const val = state.instansi[f.k]||'';
  if(f.type==='logo'){
    const preview = val ? `
      <div style="display:flex; align-items:center; gap:10px; margin-bottom:8px;">
        <img src="${val}" style="width:56px; height:56px; object-fit:contain; border:1px solid var(--line); border-radius:8px; background:#fff;">
        <button type="button" class="icon-btn danger" onclick="removeLogo()">${ICON.trash}</button>
      </div>` : '';
    return `<div class="field"><label>${esc(f.label)}</label>
      ${preview}
      <input type="file" accept="image/*" onchange="onLogoSelected(event)">
      <span class="hint">Logo instansi/lembaga (PNG/JPG). Ditampilkan di sisi kiri kop surat.</span>
    </div>`;
  }
  if(f.type==='textarea'){
    return `<div class="field"><label>${esc(f.label)}${f.required?' *':''}</label>
      <textarea data-instansi="${f.k}" placeholder="${esc(f.ph||'')}">${esc(val)}</textarea>
      ${f.hint?`<span class="hint">${esc(f.hint)}</span>`:''}</div>`;
  }
  if(f.type==='select'){
    const opts=f.options.map(o=>`<option value="${esc(o)}" ${o===val?'selected':''}>${esc(o)}</option>`).join('');
    return `<div class="field"><label>${esc(f.label)}${f.required?' *':''}</label>
      <select data-instansi="${f.k}">${opts}</select>
      ${f.hint?`<span class="hint">${esc(f.hint)}</span>`:''}</div>`;
  }
  return `<div class="field"><label>${esc(f.label)}${f.required?' *':''}</label>
    <input type="text" data-instansi="${f.k}" value="${esc(val)}" placeholder="${esc(f.ph||'')}">
  </div>`;
}
function renderInstansiModal(){
  const groups=[];
  INSTANSI_FIELDS.forEach(f=>{
    const g = f.group || null;
    const last = groups[groups.length-1];
    if(last && last.name===g) last.fields.push(f);
    else groups.push({name:g, fields:[f]});
  });
  let blocksHtml = groups.map((grp,i)=>`
    <div class="form-block"><h2><span class="num">${i+1}</span>${esc(grp.name||'Data Instansi')}</h2>
      ${grp.fields.map(instansiFieldHtml).join('')}
    </div>`).join('');
  return `<div class="modal-backdrop" onclick="if(event.target===this) closeInstansiModal()">
    <div class="modal">
      <div class="modal-head"><h2>Profil Instansi, Kop &amp; Tanda Tangan</h2><button class="modal-close" onclick="closeInstansiModal()">${ICON.x}</button></div>
      <div class="cat-desc" style="margin-top:-4px;">Satu data terpadu: logo &amp; nama instansi untuk kop surat, serta jabatan/nama/NIP dan gaya tanda tangan untuk penandatangan naskah dinas. Tersimpan pribadi di perangkat/akun Anda.</div>
      ${blocksHtml}
      <button class="btn btn-primary" onclick="saveInstansi()">${ICON.check} Simpan Profil</button>
    </div>
  </div>`;
}
function openInstansiModal(){ state.showInstansiModal=true; render(); }
function closeInstansiModal(){ state.showInstansiModal=false; render(); }
function onLogoSelected(ev){
  const file = ev.target.files && ev.target.files[0];
  if(!file) return;
  if(file.size > 900000){ showToast('Ukuran logo terlalu besar, pilih gambar yang lebih kecil'); return; }
  const reader = new FileReader();
  reader.onload = ()=>{ state.instansi.logo = reader.result; render(); };
  reader.readAsDataURL(file);
}
function removeLogo(){ delete state.instansi.logo; render(); }
async function saveInstansi(){
  const ok = await storageSet('profil-instansi', state.instansi);
  showToast(ok?'Profil instansi tersimpan':'Gagal menyimpan');
  state.showInstansiModal=false;
  render();
}

/* ============================================================
   DATA PEGAWAI (CRUD)
   ============================================================ */
const PEGAWAI_FIELDS = [
  {k:'nama', label:'Nama Lengkap', ph:'Hariyoko, S.ST.,M.H.', required:true},
  {k:'nip', label:'NIP', ph:'197808222002121005'},
  {k:'status', label:'Status Kepegawaian', type:'select', options:['PNS','CPNS','PPPK','Honorer']},
  {k:'statusHonorer', label:'Kategori Honorer', type:'select', options:['Surveyor Kadastral','Asisten Surveyor Kadastral','Outsourcing','Admin Support/Field Staff'], onlyIfHonorer:true, hint:'Hanya berlaku bila Status Kepegawaian adalah Honorer.'},
  {k:'jenisJabatan', label:'Jenis Jabatan', type:'select', options:['Jabatan Fungsional','Pelaksana','Kontrak','Pejabat Pengawas','Eselon III']},
  {k:'jenjangJf', label:'Jenjang Jabatan Fungsional', type:'select', options:['Ahli Utama','Ahli Madya','Ahli Muda','Ahli Pertama','Penyelia','Mahir','Terampil','Pemula'], onlyIfJf:true, hint:'Kelompok Keahlian: Ahli Utama/Madya/Muda/Pertama. Kelompok Keterampilan: Penyelia/Mahir/Terampil/Pemula. Hanya berlaku bila Jenis Jabatan adalah Jabatan Fungsional.'},
  {k:'nilaiPak', label:'Nilai Angka Kredit (PAK) Saat Ini', ph:'150', onlyIfJf:true, hint:'Nilai kumulatif angka kredit terakhir. Dipakai untuk notifikasi otomatis kenaikan pangkat/pengajuan uji kompetensi sesuai Permenpan RB No. 1 Tahun 2023.'},
  {k:'seksi', label:'Seksi/Sub Bagian', ph:'Seksi Survei dan Pemetaan'},
  {k:'jabatan', label:'Jabatan', ph:'Kepala Seksi Survei dan Pemetaan'},
  {k:'pendidikanTerakhir', label:'Pendidikan Terakhir', type:'select', options:['SD','SMP','SMA/SMK','D1','D2','D3','D4','S1','S2','S3']},
  {k:'jurusanPendidikan', label:'Jurusan/Program Studi', ph:'Teknik Geodesi', onlyIfEducated:true, hint:'Berlaku untuk pendidikan SMA/SMK ke atas.'},
  {k:'pangkat', label:'Pangkat', ph:'Penata Tk. I'},
  {k:'golongan', label:'Golongan', ph:'III/d'},
  {k:'tanggalPengangkatan', label:'Tanggal Pengangkatan Pertama (TMT CPNS/PNS)', type:'date', hint:'Dipakai untuk menghitung masa kerja dan peringatan pengajuan Satyalancana Karya Satya setiap kelipatan 10 tahun.'},
  {k:'tmtJabatan', label:'TMT Jabatan', type:'date'},
  {k:'tmtPangkat', label:'TMT Pangkat', type:'date'},
  {k:'tmtGajiBerkala', label:'TMT Gaji Berkala', type:'date'},
  {k:'statusTambahan', label:'Status Tambahan', type:'select', options:['-','Sedang Menjabat Plt.','Sedang Menjabat Plh.']},
  {k:'jabatanPltPlh', label:'Jabatan yang Diampu sebagai Plt./Plh.', ph:'Kepala Seksi Pengendalian dan Penanganan Sengketa'},
  {k:'jumlahPengajuanPltPlh', label:'Jumlah Pengajuan/Perpanjangan Plt./Plh.', ph:'0', hint:'Sesuai ketentuan, pengajuan/perpanjangan Plt./Plh. untuk jabatan yang sama maksimal 2 kali. Naikkan angka ini setiap kali surat usulan diajukan.'},
];

function toggleHonorerSubStatus(){
  const sel = document.querySelector('[data-peg="status"]');
  const wrap = document.getElementById('honorer-sub-wrap');
  if(wrap) wrap.style.display = (sel && sel.value==='Honorer') ? '' : 'none';
}
function toggleJfSubFields(){
  const sel = document.querySelector('[data-peg="jenisJabatan"]');
  const wrap = document.getElementById('jf-sub-wrap');
  if(wrap) wrap.style.display = (sel && sel.value==='Jabatan Fungsional') ? '' : 'none';
}
function isPendidikanSmaKeAtas(val){
  return !!val && val!=='SD' && val!=='SMP';
}
function toggleJurusanField(){
  const sel = document.querySelector('[data-peg="pendidikanTerakhir"]');
  const wrap = document.getElementById('jurusan-wrap');
  if(wrap) wrap.style.display = (sel && isPendidikanSmaKeAtas(sel.value)) ? '' : 'none';
}
function openPegawaiModal(id){
  state.editingPegawaiId = id || null;
  state.showPegawaiModal = true;
  render();
}
function closePegawaiModal(){ state.showPegawaiModal=false; state.editingPegawaiId=null; render(); }

function pegawaiFieldHtmlSingle(f, val){
  if(f.type==='select'){
    const opts = f.options.map(o=>`<option value="${esc(o)}" ${o===val?'selected':''}>${esc(o)}</option>`).join('');
    const extraAttr = f.k==='status' ? ' onchange="toggleHonorerSubStatus()"' : (f.k==='jenisJabatan' ? ' onchange="toggleJfSubFields()"' : (f.k==='pendidikanTerakhir' ? ' onchange="toggleJurusanField()"' : ''));
    return `<div class="field"><label>${esc(f.label)}${f.required?' *':''}</label><select data-peg="${f.k}"${extraAttr}>${opts}</select>
      ${f.hint?`<span class="hint">${esc(f.hint)}</span>`:''}</div>`;
  }
  return `<div class="field"><label>${esc(f.label)}${f.required?' *':''}</label>
    <input type="${f.type==='date'?'date':'text'}" data-peg="${f.k}" value="${esc(val)}" placeholder="${esc(f.ph||'')}">
    ${f.hint?`<span class="hint">${esc(f.hint)}</span>`:''}</div>`;
}
function renderPegawaiModal(){
  const editing = state.editingPegawaiId ? state.pegawaiList.find(p=>p.id===state.editingPegawaiId) : null;
  const initialHonorer = editing? editing.status==='Honorer' : false;
  const initialJf = editing? editing.jenisJabatan==='Jabatan Fungsional' : false;
  const initialJurusan = editing? isPendidikanSmaKeAtas(editing.pendidikanTerakhir) : false;
  const condMap = { honorer:{flag:'onlyIfHonorer', wrapId:'honorer-sub-wrap', visible:initialHonorer}, jf:{flag:'onlyIfJf', wrapId:'jf-sub-wrap', visible:initialJf}, jurusan:{flag:'onlyIfEducated', wrapId:'jurusan-wrap', visible:initialJurusan} };
  let fields='';
  let i=0;
  while(i<PEGAWAI_FIELDS.length){
    const f = PEGAWAI_FIELDS[i];
    const condKey = f.onlyIfHonorer ? 'honorer' : (f.onlyIfJf ? 'jf' : (f.onlyIfEducated ? 'jurusan' : null));
    if(condKey){
      const groupFields=[];
      while(i<PEGAWAI_FIELDS.length && (PEGAWAI_FIELDS[i][condMap[condKey].flag])){
        groupFields.push(PEGAWAI_FIELDS[i]); i++;
      }
      const { wrapId, visible } = condMap[condKey];
      fields += `<div id="${wrapId}" style="display:${visible?'':'none'};">${groupFields.map(gf=>pegawaiFieldHtmlSingle(gf, editing?(editing[gf.k]||''):'')).join('')}</div>`;
    } else {
      fields += pegawaiFieldHtmlSingle(f, editing?(editing[f.k]||''):'');
      i++;
    }
  }
  return `<div class="modal-backdrop" onclick="if(event.target===this) closePegawaiModal()">
    <div class="modal">
      <div class="modal-head"><h2>${editing?'Ubah Data Pegawai':'Tambah Pegawai'}</h2><button class="modal-close" onclick="closePegawaiModal()">${ICON.x}</button></div>
      <div class="form-block">${fields}</div>
      <button class="btn btn-primary" onclick="savePegawaiEntry()">${ICON.check} Simpan</button>
    </div>
  </div>`;
}
async function savePegawaiEntry(){
  const data={};
  PEGAWAI_FIELDS.forEach(f=>{
    const el=document.querySelector(`[data-peg="${f.k}"]`);
    data[f.k]= el? el.value.trim() : '';
  });
  if(!data.nama){ showToast('Nama pegawai wajib diisi'); return; }
  if(data.status!=='Honorer') data.statusHonorer='';
  if(data.jenisJabatan!=='Jabatan Fungsional'){ data.jenjangJf=''; data.nilaiPak=''; }
  if(!isPendidikanSmaKeAtas(data.pendidikanTerakhir)) data.jurusanPendidikan='';
  if(state.editingPegawaiId){
    const idx=state.pegawaiList.findIndex(p=>p.id===state.editingPegawaiId);
    if(idx>-1) state.pegawaiList[idx]={...state.pegawaiList[idx], ...data};
  } else {
    state.pegawaiList.unshift({id:'p'+Date.now(), ...data});
  }
  const ok = await storageSet('pegawai-list', state.pegawaiList);
  showToast(ok? 'Data pegawai tersimpan' : 'Gagal menyimpan');
  state.showPegawaiModal=false;
  state.editingPegawaiId=null;
  render();
}
async function deletePegawaiEntry(id, ev){
  if(ev) ev.stopPropagation();
  state.pegawaiList = state.pegawaiList.filter(p=>p.id!==id);
  await storageSet('pegawai-list', state.pegawaiList);
  showToast('Data pegawai dihapus');
  render();
}

/* Picker: memilih pegawai tersimpan untuk mengisi field petugas (mode 'petugas')
   atau mengisi satu set field pegawai tunggal seperti pada PAK/KGB (mode 'single') */
function openPegawaiPicker(fieldKey, mode){
  if(state.pegawaiList.length===0){ showToast('Belum ada Data Pegawai tersimpan'); return; }
  state.pegawaiPickerFor = fieldKey;
  state.pegawaiPickerMode = mode || 'petugas';
  render();
}
function closePegawaiPicker(){ state.pegawaiPickerFor=null; state.pegawaiPickerMode=null; render(); }
function pickPegawaiInto(pegId){
  const key = state.pegawaiPickerFor;
  const mode = state.pegawaiPickerMode || 'petugas';
  const p = state.pegawaiList.find(x=>x.id===pegId);
  if(!key || !p) return;
  if(mode==='single'){
    const set=(suf,val)=>{ if((key+suf) in state.formData) state.formData[key+suf]=val; };
    set('Nama', p.nama||'');
    set('Nip', p.nip||'');
    set('Pangkat', p.pangkat||'');
    set('Golongan', p.golongan||'');
    set('Jabatan', p.jabatan||'');
    set('TmtPangkat', p.tmtPangkat||'');
    set('TmtJabatan', p.tmtJabatan||'');
    if((key+'UnitKerja') in state.formData && !state.formData[key+'UnitKerja']) state.formData[key+'UnitKerja'] = state.instansi.unit||'';
    state.pegawaiPickerFor=null; state.pegawaiPickerMode=null;
    render();
    const jumlahPlt = parseInt(p.jumlahPengajuanPltPlh,10)||0;
    if(jumlahPlt>=2) showToast(p.nama+' sudah diusulkan Plt./Plh. '+jumlahPlt+'x — sudah mencapai batas maksimal 2 kali');
    else showToast(p.nama+' dipilih');
    return;
  }
  const arr = state.formData[key];
  const emptySlotIdx = arr.findIndex(x=> x && typeof x==='object' && !x.nama);
  const entry = {nama:p.nama, jabatan:p.jabatan||'', nip:p.nip||'', pangkat:p.pangkat||'', golongan:p.golongan||''};
  if(emptySlotIdx>-1) arr[emptySlotIdx]=entry; else arr.push(entry);
  state.pegawaiPickerFor=null;
  state.pegawaiPickerMode=null;
  render();
  showToast(p.nama+' ditambahkan');
}
function renderPegawaiPicker(){
  const items = state.pegawaiList.map(p=>`
    <button type="button" class="type-card" style="width:100%;" onclick="pickPegawaiInto('${p.id}')">
      <div class="type-badge">${ICON.users}</div>
      <div class="type-info"><h3>${esc(p.nama)}</h3><p>${esc(p.jabatan||'-')}${p.nip? ' · NIP '+esc(p.nip):''}</p></div>
    </button>`).join('');
  return `<div class="modal-backdrop" onclick="if(event.target===this) closePegawaiPicker()">
    <div class="modal">
      <div class="modal-head"><h2>Pilih Pegawai</h2><button class="modal-close" onclick="closePegawaiPicker()">${ICON.x}</button></div>
      <div class="type-grid">${items}</div>
    </div>
  </div>`;
}

/* ============================================================
   SIDE MENU (DRAWER)
   ============================================================ */
function renderSideMenu(){
  const eyebrow = state.instansi.namaInstansi ? String(state.instansi.namaInstansi).split('\n')[0] : 'Sistem Umum dan Kepegawaian';
  const heading = state.instansi.unit || 'Naskah Dinas Digital';
  const naskahItems = CATEGORIES.map(cat=>{
    const items = cat.types.map(tid=>{
      const t=TYPES[tid];
      const isActive = state.screen==='form' && state.activeType===tid;
      return `<button class="drawer-item ${isActive?'active':''}" onclick="openType('${tid}')"><span class="di-icon di-code">${t.short}</span> ${esc(t.name)}</button>`;
    }).join('');
    return `<div class="drawer-subsection">${esc(cat.label)}</div>${items}`;
  }).join('');

  return `<div class="drawer-backdrop" onclick="closeSideMenu()"></div>
  <div class="drawer">
    <div class="drawer-head">
      <img src="${getLogoUrl()}">
      <div class="dh-text">
        <div class="dh-eyebrow">${esc(eyebrow)}</div>
        <h2>${esc(heading)}</h2>
      </div>
      <button class="drawer-close" onclick="closeSideMenu()">${ICON.x}</button>
    </div>
    <div class="drawer-nav">
      <div class="drawer-section">Menu Utama</div>
      <button class="drawer-item ${state.screen==='home'?'active':''}" onclick="goHome()"><span class="di-icon">${ICON.home}</span> Beranda</button>
      <button class="drawer-item ${state.screen==='pegawai'?'active':''}" onclick="goPegawai()"><span class="di-icon">${ICON.users}</span> Data Pegawai</button>
      <button class="drawer-item" onclick="toggleNaskahDrawer()">
        <span class="di-icon">${ICON.doc}</span> Surat Dinas
        <span class="di-chevron ${state.sideMenuNaskahOpen?'open':''}">${ICON.chevronDown}</span>
      </button>
      <div class="drawer-submenu ${state.sideMenuNaskahOpen?'open':''}">${naskahItems}</div>
      <div class="drawer-section">Pengaturan</div>
      <button class="drawer-item" onclick="sideMenuOpenInstansi()"><span class="di-icon">${ICON.building}</span> Profil Instansi, Kop &amp; Tanda Tangan</button>
      <button class="drawer-item" onclick="openLoginSetup()"><span class="di-icon">${ICON.lock}</span> ${state.loginConfigured?'Ubah Kata Sandi Aplikasi':'Aktifkan Kata Sandi Aplikasi'}</button>
      ${state.loginConfigured? `<button class="drawer-item" onclick="lockApp()"><span class="di-icon">${ICON.lock}</span> Kunci Aplikasi Sekarang</button>` : ''}
      <button class="drawer-item" onclick="openResetConfirm()" style="color:#ffb4a3;"><span class="di-icon" style="color:#ffb4a3;">${ICON.trash}</span> Kosongkan Semua Data</button>
    </div>
    <div class="drawer-foot">Sistem Umum dan Kepegawaian<br>Naskah dinas &amp; data pegawai internal</div>
  </div>`;
}

/* ============================================================
   ICONS (inline SVG, minimal)
   ============================================================ */
const ICON = {
  back:'<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"><path d="M15 18l-6-6 6-6"/></svg>',
  gear:'<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="3"/><path d="M19.4 15a1.7 1.7 0 00.3 1.9l.1.1a2 2 0 11-2.8 2.8l-.1-.1a1.7 1.7 0 00-1.9-.3 1.7 1.7 0 00-1 1.5V21a2 2 0 11-4 0v-.1a1.7 1.7 0 00-1-1.6 1.7 1.7 0 00-1.9.3l-.1.1a2 2 0 11-2.8-2.8l.1-.1a1.7 1.7 0 00.3-1.9 1.7 1.7 0 00-1.5-1H3a2 2 0 110-4h.1a1.7 1.7 0 001.5-1 1.7 1.7 0 00-.3-1.9l-.1-.1a2 2 0 112.8-2.8l.1.1a1.7 1.7 0 001.9.3H9a1.7 1.7 0 001-1.5V3a2 2 0 114 0v.1a1.7 1.7 0 001 1.5 1.7 1.7 0 001.9-.3l.1-.1a2 2 0 112.8 2.8l-.1.1a1.7 1.7 0 00-.3 1.9V9a1.7 1.7 0 001.5 1H21a2 2 0 110 4h-.1a1.7 1.7 0 00-1.5 1z"/></svg>',
  chevron:'<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"><path d="M9 18l6-6-6-6"/></svg>',
  x:'<svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.3" stroke-linecap="round" stroke-linejoin="round"><path d="M18 6L6 18M6 6l12 12"/></svg>',
  plus:'<svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.3" stroke-linecap="round" stroke-linejoin="round"><path d="M12 5v14M5 12h14"/></svg>',
  trash:'<svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 6h18M8 6V4a1 1 0 011-1h6a1 1 0 011 1v2m3 0l-1 14a1 1 0 01-1 1H6a1 1 0 01-1-1L4 6"/></svg>',
  copy:'<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="9" y="9" width="12" height="12" rx="2"/><path d="M5 15H4a1 1 0 01-1-1V4a1 1 0 011-1h10a1 1 0 011 1v1"/></svg>',
  print:'<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M6 9V2h12v7M6 18H4a1 1 0 01-1-1v-5a1 1 0 011-1h16a1 1 0 011 1v5a1 1 0 01-1 1h-2M6 14h12v8H6z"/></svg>',
  save:'<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M19 21H5a2 2 0 01-2-2V5a2 2 0 012-2h11l5 5v11a2 2 0 01-2 2z"/><path d="M17 21v-8H7v8M7 3v5h8"/></svg>',
  check:'<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.3" stroke-linecap="round" stroke-linejoin="round"><path d="M20 6L9 17l-5-5"/></svg>',
  info:'<svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="flex-shrink:0;margin-top:1px;"><circle cx="12" cy="12" r="10"/><path d="M12 16v-4M12 8h.01"/></svg>',
  users:'<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 21v-2a4 4 0 00-4-4H5a4 4 0 00-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 00-3-3.87M16 3.13a4 4 0 010 7.75"/></svg>',
  edit:'<svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M11 4H4a2 2 0 00-2 2v14a2 2 0 002 2h14a2 2 0 002-2v-7"/><path d="M18.5 2.5a2.12 2.12 0 013 3L12 15l-4 1 1-4 9.5-9.5z"/></svg>',
  menu:'<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.3" stroke-linecap="round" stroke-linejoin="round"><path d="M4 6h16M4 12h16M4 18h16"/></svg>',
  doc:'<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M14 2H6a2 2 0 00-2 2v16a2 2 0 002 2h12a2 2 0 002-2V8z"/><path d="M14 2v6h6M8 13h8M8 17h8M8 9h2"/></svg>',
  chevronDown:'<svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.3" stroke-linecap="round" stroke-linejoin="round"><path d="M6 9l6 6 6-6"/></svg>',
  alert:'<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M10.29 3.86L1.82 18a2 2 0 001.71 3h16.94a2 2 0 001.71-3L13.71 3.86a2 2 0 00-3.42 0z"/><path d="M12 9v4M12 17h.01"/></svg>',
  home:'<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 9l9-7 9 7v11a2 2 0 01-2 2H5a2 2 0 01-2-2z"/><path d="M9 22V12h6v10"/></svg>',
  building:'<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 21h18M6 21V4a1 1 0 011-1h10a1 1 0 011 1v17M9 8h1M9 12h1M9 16h1M14 8h1M14 12h1M14 16h1"/></svg>',
  lock:'<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="11" width="18" height="11" rx="2"/><path d="M7 11V7a5 5 0 0110 0v4"/></svg>',
};

/* ============================================================
   MASTER RENDER
   ============================================================ */
function render(){
  const app=document.getElementById('app');
  if(state.screen==='login' || !state.isLoggedIn){
    app.innerHTML = renderLoginScreen();
    return;
  }
  let barLeft='', title='Sistem Umum dan Kepegawaian', subtitle='Naskah Dinas & Data Pegawai';

  if(state.screen==='form'){ barLeft=`<button class="appbar-back" onclick="goHome()">${ICON.back}</button>`; title=TYPES[state.activeType].name; subtitle='Isi Data Surat'; }
  if(state.screen==='preview'){ barLeft=`<button class="appbar-back" onclick="backToForm()">${ICON.back}</button>`; title=TYPES[state.activeType].name; subtitle='Pratinjau & Ekspor'; }
  if(state.screen==='pegawai'){ barLeft=`<button class="appbar-back" onclick="goHome()">${ICON.back}</button>`; title='Data Pegawai'; subtitle='Kepegawaian'; }
  if(state.screen==='pegawaiTable'){ barLeft=`<button class="appbar-back" onclick="goPegawai()">${ICON.back}</button>`; title='Tabel Pegawai'; subtitle='Kepegawaian'; }
  if(state.screen==='home'){ barLeft=`<button class="appbar-back" onclick="toggleSideMenu()">${ICON.menu}</button>`; }

  let body='';
  if(state.screen==='home') body=renderHome();
  else if(state.screen==='form') body=renderForm();
  else if(state.screen==='preview') body=renderPreview();
  else if(state.screen==='pegawai') body=renderPegawai();
  else if(state.screen==='pegawaiTable') body=renderPegawaiTableScreen();

  let bottomBar='';
  if(state.screen==='form'){
    bottomBar=`<div class="bottom-bar">
      <button class="btn btn-secondary" onclick="saveDraft()">${ICON.save} Simpan Draf</button>
      <button class="btn btn-primary" onclick="goPreview()">Lihat Pratinjau ${ICON.chevron}</button>
    </div>`;
  } else if(state.screen==='preview'){
    bottomBar=`<div class="bottom-bar" style="flex-wrap:wrap;">
      <button class="btn btn-secondary" onclick="copyText()">${ICON.copy} Salin Teks</button>
      <button class="btn btn-primary" onclick="printLetter()">${ICON.print} Cetak / PDF</button>
    </div>`;
  } else if(state.screen==='pegawai'){
    bottomBar=`<div class="bottom-bar">
      <button class="btn btn-primary" onclick="openPegawaiModal()">${ICON.plus} Tambah Pegawai</button>
    </div>`;
  } else if(state.screen==='pegawaiTable'){
    bottomBar=`<div class="bottom-bar">
      <button class="btn btn-primary" onclick="printPegawaiTable()">${ICON.print} Cetak / Unduh PDF</button>
    </div>`;
  }

  const masthead = (state.screen==='home' && state.instansi.namaInstansi)
    ? `<p class="appbar-masthead">${esc(String(state.instansi.namaInstansi).split('\n')[0])}</p>` : '';

  app.innerHTML = `
    <div class="app-watermark" style="background-image:url('${getLogoUrl()}');"></div>
    <div class="appbar">
      <div class="appbar-row">
        ${barLeft}
        <div class="appbar-title">${masthead}<h1>${esc(title)}</h1><p>${esc(subtitle)}</p></div>
        ${state.screen==='home'? `<button class="appbar-icon" onclick="openInstansiModal()">${ICON.gear}</button>` : ''}
      </div>
      <div class="appbar-gold-strip"></div>
    </div>
    <main>${body}</main>
    ${bottomBar}
    <div id="print-host"></div>
    ${state.showInstansiModal? renderInstansiModal() : ''}
    ${state.showPegawaiModal? renderPegawaiModal() : ''}
    ${state.pegawaiPickerFor? renderPegawaiPicker() : ''}
    ${state.showSideMenu? renderSideMenu() : ''}
    ${state.showResetConfirm? renderResetConfirm() : ''}
    ${state.showLoginSetup? renderLoginSetupModal() : ''}
  `;
}

/* ============================================================
   GLOBAL INPUT LISTENERS (event delegation, sekali pasang)
   ============================================================ */
document.addEventListener('input', (e)=>{
  const t=e.target;
  if(t.dataset.field){ state.formData[t.dataset.field]=t.value; return; }
  if(t.dataset.list){ state.formData[t.dataset.list][+t.dataset.idx]=t.value; return; }
  if(t.dataset.petugas){ state.formData[t.dataset.petugas][+t.dataset.idx][t.dataset.pf]=t.value; return; }
  if(t.dataset.instansi){ state.instansi[t.dataset.instansi]=t.value; return; }
});
document.addEventListener('change', (e)=>{
  const t=e.target;
  if(t.tagName==='SELECT' && t.dataset.field){ state.formData[t.dataset.field]=t.value; render(); }
  if(t.tagName==='SELECT' && t.dataset.instansi){ state.instansi[t.dataset.instansi]=t.value; render(); }
});

/* ============================================================
   INIT
   ============================================================ */
loadInitial();
</script>
</body>
</html>
