<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Fast News — Media</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Hind+Siliguri:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">
<style>
:root{
  --paper:#F1F1EF;
  --paper-2:#E6E6E2;
  --ink:#1A1A1A;
  --ink-soft:#5B5B58;
  --crimson:#9B090D;
  --crimson-dark:#6E0509;
  --crimson-light:#FBEAEA;
  --forest:#33475B;
  --forest-light:#E7ECF2;
  --brass:#A87C2B;
  --brass-light:#F2E6C9;
  --rule:#DEDEDA;
  --white:#FFFFFF;
  --danger:#9B090D;
  --shadow:0 1px 2px rgba(0,0,0,0.07);
  --radius:3px;
}
*{box-sizing:border-box;}
html{scroll-behavior:smooth;}
body{
  margin:0;
  background:var(--paper);
  color:var(--ink);
  font-family:'Hind Siliguri', sans-serif;
  font-size:16px;
  line-height:1.6;
  -webkit-font-smoothing:antialiased;
}
h1,h2,h3,h4{font-family:'Hind Siliguri', sans-serif; font-weight:600; margin:0; color:var(--ink);}
a{color:inherit; text-decoration:none;}
button{font-family:inherit; cursor:pointer;}
.mono{font-family:'JetBrains Mono', monospace; letter-spacing:0.02em;}
img{max-width:100%; display:block;}
::selection{background:var(--crimson-light);}
:focus-visible{outline:2px solid var(--crimson); outline-offset:2px;}
@media (prefers-reduced-motion: reduce){*{animation-duration:0.01ms !important; transition-duration:0.01ms !important;}}

/* ===== Masthead (Jamuna-style red identity bar) ===== */
.topstrip{background:var(--crimson); color:var(--white); font-size:12px;}
.topstrip-inner{max-width:1180px; margin:0 auto; padding:5px 20px; display:flex; justify-content:space-between; align-items:center; gap:8px; flex-wrap:wrap;}
.topstrip .mono{opacity:.9;}
.masthead{background:var(--crimson); padding:12px 20px 0;}
.masthead-inner{max-width:1180px; margin:0 auto; display:flex; align-items:center; justify-content:space-between; gap:16px; flex-wrap:wrap; padding-bottom:14px; position:relative;}
.nameplate{display:flex; align-items:baseline; gap:10px;}
.nameplate h1{font-size:30px; letter-spacing:-0.01em; color:var(--white); font-weight:700;}
.nameplate .sub{font-size:11.5px; color:rgba(255,255,255,.78); font-family:'JetBrains Mono',monospace; letter-spacing:0.1em; text-transform:uppercase; border-left:1px solid rgba(255,255,255,.35); padding-left:10px;}
.masthead-actions{display:flex; align-items:center; gap:8px; flex-wrap:wrap;}
.live-badge{display:inline-flex; align-items:center; gap:6px; background:rgba(0,0,0,.22); color:var(--white); padding:7px 14px; border-radius:2px; font-size:13px; font-weight:600; border:none;}
.live-dot{width:7px; height:7px; border-radius:50%; background:#FF4B4B; animation:pulse 1.4s infinite;}
@keyframes pulse{0%,100%{opacity:1;}50%{opacity:.25;}}
.btn{border:1px solid var(--ink); background:transparent; color:var(--ink); padding:8px 16px; font-size:14px; border-radius:var(--radius); transition:background .15s,color .15s;}
.btn:hover{background:var(--ink); color:var(--white);}
.btn-primary{background:var(--crimson); border-color:var(--crimson); color:var(--white);}
.btn-primary:hover{background:var(--crimson-dark); border-color:var(--crimson-dark); color:var(--white);}
.btn-ghost{border-color:var(--rule); color:var(--ink-soft); background:var(--white);}
.btn-ghost:hover{background:var(--paper-2); color:var(--ink);}
.btn-sm{padding:5px 10px; font-size:12.5px;}
.btn-danger{border-color:var(--crimson); color:var(--crimson);}
.btn-danger:hover{background:var(--crimson); color:var(--white);}
.masthead-actions .btn-ghost{background:rgba(255,255,255,.94); border-color:transparent;}
.masthead-actions .btn-primary{background:var(--ink); border-color:var(--ink);}
.masthead-actions .btn-primary:hover{background:#000;}

/* ===== Ticker (breaking strip) ===== */
.ticker-bar{background:var(--ink); color:var(--white); display:flex; align-items:center; overflow:hidden; white-space:nowrap;}
.ticker-tag{background:#000; padding:8px 14px; font-family:'JetBrains Mono',monospace; font-size:12px; letter-spacing:0.08em; text-transform:uppercase; flex-shrink:0; display:flex; align-items:center; gap:6px; color:#FF4B4B;}
.ticker-dot{width:7px; height:7px; border-radius:50%; background:#FF4B4B; animation:pulse 1.6s infinite;}
.ticker-track{display:inline-block; padding-left:100%; animation:scroll-left 32s linear infinite;}
.ticker-track span{margin-right:60px; font-size:13.5px;}
@keyframes scroll-left{from{transform:translateX(0);}to{transform:translateX(-100%);}}

/* ===== Category nav ===== */
.catnav{background:var(--white); border-bottom:2px solid var(--crimson); position:sticky; top:0; z-index:20; box-shadow:var(--shadow);}
.catnav-inner{max-width:1180px; margin:0 auto; display:flex; overflow-x:auto; scrollbar-width:none; align-items:center;}
.catnav-inner::-webkit-scrollbar{display:none;}
.catnav a{padding:12px 15px; font-size:14.5px; font-weight:500; white-space:nowrap; border-bottom:3px solid transparent; color:var(--ink); flex-shrink:0;}
.catnav a.active,.catnav a:hover{border-bottom-color:var(--crimson); color:var(--crimson);}
.catnav .search-toggle{margin-left:auto; padding:0 16px; color:var(--ink-soft); flex-shrink:0;}

/* ===== Layout ===== */
.wrap{max-width:1180px; margin:0 auto; padding:28px 20px 60px;}
.grid{display:grid; grid-template-columns:2fr 1fr; gap:30px;}
@media(max-width:860px){.grid{grid-template-columns:1fr;}}

/* ===== Cards ===== */
.card{background:var(--white); border:1px solid var(--rule); border-radius:var(--radius); overflow:hidden;}
.article-card{display:flex; flex-direction:column; margin-bottom:26px; padding-bottom:22px; border-bottom:1px solid var(--rule);}
.article-card:last-child{border-bottom:none;}
.article-card .thumb{width:100%; aspect-ratio:16/9; object-fit:cover; border-radius:var(--radius); background:var(--paper-2); margin-bottom:12px;}
.badge{display:inline-block; color:var(--crimson); font-size:13px; font-weight:600; margin-bottom:6px;}
.badge.brass{color:var(--brass); text-transform:uppercase; letter-spacing:0.05em; font-size:11.5px; font-family:'JetBrains Mono',monospace;}
.article-card h2{font-size:21px; line-height:1.35; margin-bottom:6px; font-weight:600;}
.article-card h2 a:hover{color:var(--crimson);}
.excerpt{color:var(--ink-soft); font-size:15px; margin-bottom:8px;}
.byline{font-family:'JetBrains Mono',monospace; font-size:11.5px; color:var(--ink-soft); display:flex; gap:14px; flex-wrap:wrap; align-items:center;}
.byline i{font-style:normal;}

.hero{display:grid; grid-template-columns:1.3fr 1fr; gap:22px; margin-bottom:24px; padding-bottom:20px; border-bottom:1px solid var(--rule);}
@media(max-width:700px){.hero{grid-template-columns:1fr;}}
.hero .thumb{width:100%; aspect-ratio:16/10; object-fit:cover; border-radius:var(--radius); background:var(--paper-2);}
.hero h2{font-size:27px; line-height:1.28; margin-bottom:8px; font-weight:700;}
.hero .excerpt{font-size:15.5px;}
.hero-list{display:flex; flex-direction:column; gap:0;}
.hero-list .side-item{padding:11px 0;}

.section-block{background:var(--white); border:1px solid var(--rule); border-radius:var(--radius); padding:18px 20px 8px; margin-bottom:22px;}
.section-head{display:flex; align-items:center; justify-content:space-between; border-bottom:2px solid var(--crimson); padding-bottom:9px; margin-bottom:14px;}
.section-head h3{font-size:17px; font-weight:700; color:var(--ink);}
.section-head a{font-size:12.5px; color:var(--ink-soft); font-family:'JetBrains Mono',monospace;}
.section-head a:hover{color:var(--crimson);}
.section-grid{display:grid; grid-template-columns:1.1fr 1fr; gap:20px;}
@media(max-width:600px){.section-grid{grid-template-columns:1fr;}}
.section-feature .thumb{width:100%; aspect-ratio:16/10; object-fit:cover; border-radius:var(--radius); background:var(--paper-2); margin-bottom:10px;}
.section-feature h4{font-size:17px; font-weight:600; line-height:1.35;}
.section-feature h4 a:hover{color:var(--crimson);}
.section-list .headline-item{display:block; padding:9px 0; border-bottom:1px solid var(--rule); font-size:14.5px; line-height:1.4;}
.section-list .headline-item:last-child{border-bottom:none;}
.section-list .headline-item a:hover{color:var(--crimson);}

.side-box{margin-bottom:26px; background:var(--white); border:1px solid var(--rule); border-radius:var(--radius); padding:16px 18px;}
.side-box h3{font-size:14px; letter-spacing:0.02em; color:var(--ink); border-bottom:2px solid var(--crimson); padding-bottom:9px; margin-bottom:10px; font-weight:700;}
.side-tabs{display:flex; gap:4px; margin-bottom:6px;}
.side-tabs button{background:none; border:none; font-size:12.5px; padding:6px 10px; color:var(--ink-soft); border-bottom:2px solid transparent;}
.side-tabs button.active{color:var(--crimson); border-bottom-color:var(--crimson); font-weight:600;}
.side-item{display:flex; gap:10px; padding:10px 0; border-bottom:1px solid var(--rule);}
.side-item:last-child{border-bottom:none;}
.side-item .num{font-family:'JetBrains Mono',monospace; font-size:19px; color:var(--rule); font-weight:600; flex-shrink:0; width:24px;}
.side-item .t{font-size:14px; line-height:1.4;}
.side-item .t a:hover{color:var(--crimson);}

.search-box{display:flex; gap:8px; margin-bottom:22px;}
.search-box input{flex:1;}

input,select,textarea{width:100%; padding:10px 12px; border:1px solid var(--rule); border-radius:var(--radius); background:var(--white); font-family:'Hind Siliguri',sans-serif; font-size:15px; color:var(--ink);}
input:focus,select:focus,textarea:focus{border-color:var(--crimson);}
label{display:block; font-size:13.5px; color:var(--ink-soft); margin-bottom:5px; font-weight:500;}
.field{margin-bottom:16px;}
textarea{resize:vertical; min-height:120px;}

.auth-shell{max-width:420px; margin:40px auto; background:var(--white); border:1px solid var(--rule); border-radius:var(--radius); padding:32px;}
.auth-shell h2{font-size:26px; margin-bottom:6px; text-align:center;}
.auth-shell .lead{text-align:center; color:var(--ink-soft); font-size:14px; margin-bottom:24px;}
.auth-switch{text-align:center; margin-top:16px; font-size:14px; color:var(--ink-soft);}
.auth-switch a{color:var(--crimson); font-weight:500;}
.hint-box{background:var(--brass-light); border:1px solid var(--brass); border-radius:var(--radius); padding:10px 14px; font-size:13px; color:#5f461c; margin-bottom:18px;}
.code-reveal{background:var(--forest-light); border:1px dashed var(--forest); padding:14px; text-align:center; border-radius:var(--radius); margin-bottom:16px;}
.code-reveal .code{font-family:'JetBrains Mono',monospace; font-size:26px; letter-spacing:0.2em; color:var(--forest); font-weight:600;}

.form-shell{max-width:760px; margin:0 auto; background:var(--white); border:1px solid var(--rule); border-radius:var(--radius); padding:30px;}
.form-shell h2{font-size:26px; margin-bottom:20px; border-bottom:2px solid var(--ink); padding-bottom:14px;}
.row2{display:grid; grid-template-columns:1fr 1fr; gap:14px;}
@media(max-width:560px){.row2{grid-template-columns:1fr;}}

.tabs{display:flex; gap:4px; border-bottom:1px solid var(--rule); margin-bottom:22px; flex-wrap:wrap;}
.tabs button{background:none; border:none; padding:10px 16px; font-size:14.5px; color:var(--ink-soft); border-bottom:3px solid transparent;}
.tabs button.active{color:var(--crimson); border-bottom-color:var(--crimson); font-weight:500;}

table{width:100%; border-collapse:collapse; font-size:14px;}
th,td{text-align:right; padding:9px 8px; border-bottom:1px solid var(--rule);}
th:first-child,td:first-child{text-align:right;}
th{font-family:'JetBrains Mono',monospace; font-size:11px; text-transform:uppercase; letter-spacing:0.05em; color:var(--ink-soft); font-weight:500;}
table td,table th{text-align:right;}
.table-wrap{overflow-x:auto;}
tr:hover{background:var(--paper-2);}
.pill{display:inline-block; padding:2px 9px; border-radius:10px; font-size:11.5px; font-family:'JetBrains Mono',monospace;}
.pill.admin{background:var(--crimson); color:var(--white);}
.pill.user{background:var(--forest-light); color:var(--forest);}
.pill.banned{background:#efd9d9; color:var(--crimson);}
.pill.active{background:var(--forest-light); color:var(--forest);}

.stat-grid{display:grid; grid-template-columns:repeat(auto-fit,minmax(140px,1fr)); gap:14px; margin-bottom:26px;}
.stat{background:var(--white); border:1px solid var(--rule); border-radius:var(--radius); padding:16px;}
.stat .n{font-family:'JetBrains Mono',monospace; font-size:28px; font-weight:600; color:var(--crimson);}
.stat .l{font-size:12.5px; color:var(--ink-soft); text-transform:uppercase; letter-spacing:0.04em; margin-top:2px;}

.detail-hero-img{width:100%; max-height:440px; object-fit:cover; border-radius:var(--radius); margin-bottom:18px; background:var(--paper-2);}
.detail-body{font-size:17px; line-height:1.85; white-space:pre-wrap; margin:20px 0;}
.detail-dateline{font-family:'JetBrains Mono',monospace; font-size:12px; color:var(--crimson); text-transform:uppercase; letter-spacing:0.04em; margin-bottom:10px;}
.tag-row{display:flex; gap:8px; flex-wrap:wrap; margin:14px 0;}
.tag-chip{background:var(--paper-2); color:var(--ink-soft); padding:4px 11px; border-radius:12px; font-size:12.5px;}
.share-row{display:flex; gap:8px; flex-wrap:wrap; margin:20px 0; padding:16px 0; border-top:1px solid var(--rule); border-bottom:1px solid var(--rule);}

.comment{padding:14px 0; border-bottom:1px solid var(--rule);}
.comment:last-child{border-bottom:none;}
.comment .who{font-weight:500; font-size:14px; margin-bottom:3px;}
.comment .when{font-family:'JetBrains Mono',monospace; font-size:11px; color:var(--ink-soft); margin-right:8px;}
.comment .txt{font-size:14.5px; color:var(--ink);}

.empty{text-align:center; padding:50px 20px; color:var(--ink-soft);}
.empty i{font-size:15px;}

.toast{position:fixed; bottom:24px; left:50%; transform:translateX(-50%); background:var(--ink); color:var(--white); padding:12px 22px; border-radius:var(--radius); font-size:14px; z-index:100; box-shadow:var(--shadow); animation:toast-in .2s ease;}
@keyframes toast-in{from{opacity:0; transform:translate(-50%,10px);}to{opacity:1; transform:translate(-50%,0);}}

.notif-item,.msg-item{padding:12px 14px; border:1px solid var(--rule); border-radius:var(--radius); margin-bottom:10px; font-size:14px;}
.notif-item.unread{border-left:3px solid var(--crimson); background:#FDF6F6;}
.msg-item.admin{border-left:3px solid var(--forest); background:var(--forest-light);}
.notif-item .when,.msg-item .when{font-family:'JetBrains Mono',monospace; font-size:11px; color:var(--ink-soft); display:block; margin-top:6px;}

footer{background:var(--crimson); margin-top:40px; padding:28px 20px 20px; text-align:center; font-size:12.5px; color:rgba(255,255,255,.85);}
footer .foot-name{font-size:20px; font-weight:700; color:var(--white); margin-bottom:10px;}
footer .foot-links{display:flex; justify-content:center; gap:16px; flex-wrap:wrap; margin:12px 0; font-size:12.5px;}
footer .foot-links a:hover{color:var(--white); text-decoration:underline;}
footer .disclaimer{max-width:640px; margin:14px auto 0; font-size:11.5px; line-height:1.6; color:rgba(255,255,255,.75); border-top:1px solid rgba(255,255,255,.25); padding-top:14px;}

.section-title{font-size:20px; margin:34px 0 16px; padding-bottom:8px; border-bottom:2px solid var(--crimson); display:flex; align-items:center; gap:10px; font-weight:700;}
.section-title .dot{width:9px; height:9px; background:var(--crimson); border-radius:50%; display:inline-block;}

.like-btn{display:flex; align-items:center; gap:6px; border:1px solid var(--rule); background:var(--white); padding:8px 16px; border-radius:var(--radius); font-size:14px;}
.like-btn.liked{border-color:var(--crimson); color:var(--crimson); background:#FDF6F6;}

.action-icons{display:flex; gap:10px;}
.icon-btn{border:1px solid var(--rule); background:var(--white); border-radius:var(--radius); padding:5px 9px; font-size:12px; color:var(--ink-soft);}
.icon-btn:hover{border-color:var(--crimson); color:var(--crimson);}

/* ===== Director badge ===== */
.director-badge{position:absolute; top:0; right:0; display:flex; flex-direction:column; align-items:center; gap:5px; z-index:6;}
.director-badge .d-photo{width:60px; height:60px; object-fit:cover; border-radius:5px; border:2px solid rgba(255,255,255,.9); box-shadow:0 2px 8px rgba(0,0,0,.3); display:block; background:var(--white);}
.director-badge .d-name{font-size:11px; color:var(--white); font-weight:600; text-align:center; line-height:1.3; max-width:120px;}
.director-badge .d-role{display:block; font-size:10px; color:rgba(255,255,255,.8); font-weight:400; margin-top:1px;}
@media(max-width:700px){.director-badge{position:static; margin:0 auto 8px; order:-1;}}

/* ===== Card-level quick actions ===== */
.card-actions{display:flex; align-items:center; gap:12px; flex-wrap:wrap; margin-top:10px; padding-top:10px; border-top:1px solid var(--rule);}
.card-actions .like-btn.small{padding:5px 11px; font-size:12.5px; gap:4px;}
.card-action-link{display:inline-flex; align-items:center; gap:4px; font-size:12.5px; color:var(--ink-soft); border:1px solid var(--rule); background:var(--white); padding:5px 10px; border-radius:var(--radius);}
.card-action-link:hover{border-color:var(--crimson); color:var(--crimson);}
.card-views{font-size:11.5px; color:var(--ink-soft); margin-left:auto;}

/* ===== Complaint status pills ===== */
.pill.pending{background:var(--brass-light); color:#7a5a17;}
.pill.resolved{background:var(--forest-light); color:var(--forest);}
.complaint-msg{max-width:280px; white-space:pre-wrap; font-size:13px; line-height:1.5;}

/* ===== Theme toggle ===== */
.theme-toggle{border:1px solid var(--rule); background:var(--white); color:var(--ink-soft); padding:8px 12px; border-radius:var(--radius); font-size:13px;}
.theme-toggle:hover{border-color:var(--crimson); color:var(--crimson);}
html[data-theme="dark"]{--paper:#17181A; --paper-2:#1E2023; --ink:#EDEDEC; --ink-soft:#A8A8A5; --rule:#2E2F32; --white:#232427; --forest-light:#1B2732; --brass-light:#332A17;}
html[data-theme="dark"] .thumb,html[data-theme="dark"] .detail-hero-img{opacity:.92;}
html[data-theme="dark"] .btn{color:var(--ink);}
html[data-theme="dark"] .masthead-actions .btn-ghost{background:rgba(255,255,255,.12); color:var(--white);}

/* ===== Reading meta ===== */
.read-meta{display:flex; gap:14px; flex-wrap:wrap; font-family:'JetBrains Mono',monospace; font-size:11.5px; color:var(--ink-soft); margin:8px 0 4px;}
</style>
</head>
<body>
<div id="app"></div>

<script>
(function(){
"use strict";

var CATEGORIES = [
  {id:"national", name:"জাতীয়"},
  {id:"international", name:"আন্তর্জাতিক"},
  {id:"politics", name:"রাজনীতি"},
  {id:"economy", name:"অর্থনীতি"},
  {id:"sports", name:"খেলাধুলা"},
  {id:"entertainment", name:"বিনোদন"},
  {id:"technology", name:"প্রযুক্তি"},
  {id:"opinion", name:"মতামত"},
  {id:"lifestyle", name:"লাইফস্টাইল"}
];
function catName(id){ var c=CATEGORIES.filter(function(x){return x.id===id;})[0]; return c?c.name:id; }

var DB = { users: [], news: [] };
var SESSION_THEME = "light";
var DIRECTOR_IMG = "data:image/jpeg;base64,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";

var SESSION = null;

function uid(){ return Date.now().toString(36)+Math.random().toString(36).slice(2,8); }
function esc(s){ if(s===undefined||s===null) return ""; return String(s).replace(/[&<>"']/g,function(c){return {"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c];}); }
function nl2br(s){ return esc(s); }
function fmtDate(iso){
  try{
    var d = new Date(iso);
    return d.toLocaleDateString('bn-BD',{year:'numeric',month:'long',day:'numeric'}) + " · " + d.toLocaleTimeString('bn-BD',{hour:'2-digit',minute:'2-digit'});
  }catch(e){ return iso; }
}
function hashPw(pw){ try{ return btoa(unescape(encodeURIComponent("np_salt_"+pw))); }catch(e){ return pw; } }
var toastTimer;
function toast(msg){
  var old = document.querySelector('.toast');
  if(old) old.remove();
  var t = document.createElement('div');
  t.className='toast'; t.textContent=msg;
  document.body.appendChild(t);
  clearTimeout(toastTimer);
  toastTimer = setTimeout(function(){ t.remove(); }, 2600);
}

/* ---------- storage helpers ---------- */
async function sGet(key){
  try{ var r = await window.storage.get(key, true); return r ? JSON.parse(r.value) : null; }
  catch(e){ return null; }
}
async function sSet(key, val){
  try{ return await window.storage.set(key, JSON.stringify(val), true); }
  catch(e){ console.error("storage set failed", e); return null; }
}
async function sGetPersonal(key){
  try{ var r = await window.storage.get(key, false); return r ? JSON.parse(r.value) : null; }
  catch(e){ return null; }
}
async function sSetPersonal(key, val){
  try{ return await window.storage.set(key, JSON.stringify(val), false); }
  catch(e){ console.error("storage set failed", e); return null; }
}

/* ---------- seed / init ---------- */
async function initData(){
  var users = await sGet('users');
  if(!users || !users.length){
    users = [{
      id: uid(), username:"admin", displayName:"প্রশাসক", email:"admin@sangbadpatra.demo",
      password: hashPw("admin123"), role:"admin", joined:new Date().toISOString(), banned:false
    },{
      id: uid(), username:"rahim", displayName:"রহিম উদ্দিন", email:"rahim@demo.com",
      password: hashPw("rahim123"), role:"user", joined:new Date().toISOString(), banned:false
    }];
    await sSet('users', users);
  }
  DB.users = users;

  var news = await sGet('news');
  if(!news || !news.length){
    var now = Date.now();
    news = [
      {id:uid(), title:"চট্টগ্রামে বন্যা ও পাহাড়ধসে প্রাণহানি বেড়ে ৫৪, ক্ষতিগ্রস্ত ছয় লাখের বেশি মানুষ", excerpt:"টানা ভারী বর্ষণ ও পাহাড়ি ঢলে চট্টগ্রাম বিভাগের পাঁচ জেলায় ভয়াবহ বন্যা পরিস্থিতি তৈরি হয়েছে। সবচেয়ে বেশি ক্ষতিগ্রস্ত হয়েছে কক্সবাজার জেলা।", content:"গত এক সপ্তাহ ধরে চলা টানা ভারী বৃষ্টি, পাহাড়ি ঢল ও পাহাড়ধসে চট্টগ্রাম, কক্সবাজার, বান্দরবান, রাঙামাটি ও খাগড়াছড়ি জেলায় মানবিক বিপর্যয় দেখা দিয়েছে। সবচেয়ে বেশি প্রাণহানি ঘটেছে কক্সবাজারে, যেখানে রোহিঙ্গা শরণার্থী শিবিরেও বেশ কয়েকজনের মৃত্যুর খবর পাওয়া গেছে। জেলা প্রশাসনের হিসাবে, দুর্যোগে ঘরবাড়ি হারিয়ে বা পানিবন্দি হয়ে ক্ষতিগ্রস্ত হয়েছেন প্রায় ছয় লাখের বেশি মানুষ। বহু এলাকায় বিদ্যুৎ ও মোবাইল নেটওয়ার্ক দীর্ঘ সময় বিচ্ছিন্ন থাকায় প্রকৃত ক্ষয়ক্ষতির চিত্র নিরূপণ করাই কঠিন হয়ে পড়েছে বলে স্থানীয়রা জানিয়েছেন। চট্টগ্রাম-কক্সবাজার মহাসড়কের একাংশ এখনো পানির নিচে থাকায় যোগাযোগ ব্যবস্থাও মারাত্মকভাবে ব্যাহত হচ্ছে। প্রশাসন শত শত আশ্রয়কেন্দ্র খুলে উদ্ধার ও ত্রাণ তৎপরতা চালিয়ে যাচ্ছে, তবে দুর্গম উপকূলীয় অঞ্চলে এখনো ত্রাণ পৌঁছায়নি বলে অভিযোগ উঠেছে।", category:"national", tags:["বন্যা","চট্টগ্রাম","পাহাড়ধস","কক্সবাজার"], imageUrl:"https://images.unsplash.com/photo-1547683905-f686c993aae5?w=1200", author:"admin", authorDisplay:"প্রশাসক", date:new Date(Date.now()-3600000*3).toISOString(), comments:[], likedBy:[], shares:34},
      {id:uid(), title:"গণভোট ও নির্বাচনের ফল নিয়ে রাজনৈতিক মহলে বাড়ছে বিতর্ক", excerpt:"সাম্প্রতিক জাতীয় সংসদ নির্বাচনের পাশাপাশি অনুষ্ঠিত গণভোটের প্রাপ্ত ভোটের ব্যবধান নিয়ে বিভিন্ন রাজনৈতিক দলের মধ্যে মতপার্থক্য তীব্র হয়ে উঠেছে।", content:"সদ্য অনুষ্ঠিত ত্রয়োদশ জাতীয় সংসদ নির্বাচনের সঙ্গে একই দিনে হওয়া সাংবিধানিক সংস্কার সংক্রান্ত গণভোটের ফল নিয়ে রাজনৈতিক অঙ্গনে নতুন করে বিতর্ক শুরু হয়েছে। একাধিক দলের শীর্ষ নেতা জনমত জরিপে প্রাপ্ত সমর্থনের হার এবং সংসদে আসনসংখ্যার ভিত্তিতে সংস্কার বাস্তবায়নের অগ্রাধিকার নিয়ে ভিন্নমত পোষণ করছেন। কিছু দলের নেতৃত্ব বলছেন, গণভোটে বিপুল সংখ্যাগরিষ্ঠতার রায়কে উপেক্ষা করলে তা রাজপথের আন্দোলনে রূপ নিতে পারে। অন্তর্বর্তী সরকারের ভূমিকা নিয়েও সংসদে কড়া সমালোচনা হয়েছে, বিশেষ করে অতীতের কিছু সিদ্ধান্তের জবাবদিহি চাওয়া হচ্ছে। বিশ্লেষকরা মনে করছেন, এই বিতর্কের সুরাহা কীভাবে হয় তার ওপর নির্ভর করবে আগামী দিনের রাজনৈতিক স্থিতিশীলতা।", category:"politics", tags:["নির্বাচন","গণভোট","রাজনীতি"], imageUrl:"https://images.unsplash.com/photo-1541872703-74c5e44368f9?w=1200", author:"rahim", authorDisplay:"রহিম উদ্দিন", date:new Date(Date.now()-3600000*5).toISOString(), comments:[], likedBy:[], shares:27},
      {id:uid(), title:"দেশের বাজারে আরও কমলো সোনার দাম", excerpt:"আন্তর্জাতিক বাজারের প্রবণতার সঙ্গে সামঞ্জস্য রেখে দেশের বাজারে ভরিপ্রতি সোনার দাম দুই হাজারের বেশি টাকা কমিয়েছে জুয়েলার্স সমিতি।", content:"বাংলাদেশ জুয়েলার্স অ্যাসোসিয়েশন সবচেয়ে ভালো মানের সোনার ভরিপ্রতি দাম প্রায় দুই হাজার ১৫৮ টাকা কমানোর সিদ্ধান্ত জানিয়েছে। সংগঠনটি বলছে, বিশ্ববাজারে সোনার দামে সাম্প্রতিক ওঠানামার প্রেক্ষিতে স্থানীয় বাজারও সমন্বয় করা হয়েছে। এর আগে কয়েক দফায় সোনার দাম বাড়ানো হলেও চলতি সপ্তাহে তা কিছুটা নিম্নমুখী প্রবণতায় ফিরেছে। ব্যবসায়ীরা বলছেন, ডলারের বিনিময় হার ও আন্তর্জাতিক বুলিয়ন মার্কেটের গতিবিধির ওপর ভিত্তি করে আগামী দিনগুলোতেও দামে পরিবর্তন আসতে পারে। গয়না কিনতে আসা ক্রেতাদের মধ্যে এই মূল্যহ্রাসে কিছুটা স্বস্তি দেখা গেছে।", category:"economy", tags:["সোনার দাম","বাজার","অর্থনীতি"], imageUrl:"https://images.unsplash.com/photo-1610375461369-d613b564f4c4?w=1200", author:"admin", authorDisplay:"প্রশাসক", date:new Date(Date.now()-3600000*8).toISOString(), comments:[], likedBy:[], shares:9},
      {id:uid(), title:"সপ্তাহজুড়ে চাঙ্গা শেয়ারবাজার, বাজার মূলধন বাড়লো কয়েক হাজার কোটি টাকা", excerpt:"ঢাকা স্টক এক্সচেঞ্জে গত সপ্তাহে সূচক ও লেনদেন দুটোই ঊর্ধ্বমুখী থেকেছে, বেড়েছে বাজার মূলধনও।", content:"দেশের প্রধান শেয়ারবাজার ঢাকা স্টক এক্সচেঞ্জে (ডিএসই) গত সপ্তাহজুড়ে ইতিবাচক প্রবণতা অব্যাহত ছিল। সপ্তাহের ব্যবধানে ডিএসইর প্রধান সূচক বেশ কিছুটা বেড়ে নতুন উচ্চতায় পৌঁছেছে, পাশাপাশি ডিএসই শরিয়াহ ও ডিএসই৩০ সূচকও ঊর্ধ্বমুখী ছিল। সপ্তাহে গড় দৈনিক লেনদেনের পরিমাণও আগের সপ্তাহের তুলনায় উল্লেখযোগ্য হারে বেড়েছে। বাজার বিশ্লেষকরা বলছেন, ভালো মৌলভিত্তিসম্পন্ন ও বড় মূলধনি কোম্পানিগুলোর শেয়ারদর বৃদ্ধিই এই ইতিবাচক ধারার মূল চালিকাশক্তি। তবে একই সঙ্গে সতর্ক করে বলা হচ্ছে, স্বল্প মূলধনি কিছু কোম্পানির শেয়ারে অস্বাভাবিক দর বৃদ্ধি নিয়ন্ত্রক সংস্থার নজরদারিতে রয়েছে।", category:"economy", tags:["শেয়ারবাজার","ডিএসই","অর্থনীতি"], imageUrl:"https://images.unsplash.com/photo-1611974789855-9c2a0a7236a3?w=1200", author:"rahim", authorDisplay:"রহিম উদ্দিন", date:new Date(Date.now()-3600000*11).toISOString(), comments:[], likedBy:[], shares:6},
      {id:uid(), title:"আট জেলায় ঝড়ো হাওয়া ও বজ্রবৃষ্টির সতর্কতা দিলো আবহাওয়া অধিদপ্তর", excerpt:"দেশের আট জেলায় ঘণ্টায় ৬০ কিলোমিটার বেগে ঝড়ো হাওয়াসহ বৃষ্টি বা বজ্রবৃষ্টি হতে পারে বলে সতর্কবার্তা জারি করেছে আবহাওয়া অধিদপ্তর।", content:"আবহাওয়া অধিদপ্তরের সবশেষ পূর্বাভাসে বলা হয়েছে, মৌসুমি বায়ুর প্রভাবে দেশের বিভিন্ন অঞ্চলে অস্থায়ীভাবে দমকা ও ঝড়ো হাওয়াসহ বৃষ্টিপাত হতে পারে। নির্দিষ্ট আটটি জেলায় দুপুরের মধ্যে সর্বোচ্চ ৬০ কিলোমিটার বেগে ঝড়ো হাওয়া বয়ে যাওয়ার সম্ভাবনা রয়েছে বলে জানানো হয়েছে। সমুদ্রবন্দরগুলোকে সতর্কসংকেত বজায় রাখতে বলা হয়েছে এবং জেলে ও নৌযান চলাচলকারীদের সতর্ক থাকার পরামর্শ দেওয়া হয়েছে। ইতিমধ্যে চট্টগ্রাম অঞ্চলে চলমান বন্যা পরিস্থিতির মধ্যে নতুন এই সতর্কবার্তা দুর্যোগ ব্যবস্থাপনা কর্তৃপক্ষের জন্য বাড়তি উদ্বেগের কারণ হয়ে দাঁড়িয়েছে।", category:"national", tags:["আবহাওয়া","ঝড়","বৃষ্টি"], imageUrl:"https://images.unsplash.com/photo-1500674425229-f692875b0ab7?w=1200", author:"admin", authorDisplay:"প্রশাসক", date:new Date(Date.now()-3600000*14).toISOString(), comments:[], likedBy:[], shares:4},
      {id:uid(), title:"হরমুজ প্রণালী ঘিরে যুক্তরাষ্ট্র-ইরান সংঘাত তীব্র আকার ধারণ করেছে", excerpt:"পারস্য উপসাগরীয় অঞ্চলে টানা কয়েক দিনের হামলা-পাল্টা হামলায় বাড়ছে যুদ্ধ বিস্তৃতির শঙ্কা, প্রভাব পড়ছে জ্বালানি বাজারেও।", content:"যুক্তরাষ্ট্র ও ইরানের মধ্যে চলমান সামরিক উত্তেজনা গত এক সপ্তাহে আরও তীব্র হয়েছে। ইরান কৌশলগত হরমুজ প্রণালী বন্ধ ঘোষণার পর দুই পক্ষের হামলা ও পাল্টা হামলার পরিধি বেড়েছে, যার আঁচ লেগেছে প্রতিবেশী উপসাগরীয় দেশগুলোতেও। বাহরাইন, জর্ডান, কুয়েত, ওমান, সিরিয়া ও কাতারেও ক্ষেপণাস্ত্র বা ড্রোন হামলার খবর পাওয়া গেছে। রেলপথ, সেতু ও জ্বালানি অবকাঠামোয় হামলার প্রভাবে ইরানের বিদ্যুৎ ব্যবস্থাপনায় বড় ধরনের চাপ তৈরি হয়েছে, ফলে কর্তৃপক্ষ নাগরিকদের বিদ্যুৎ ব্যবহারে সংযমী হতে বলেছে। জাতিসংঘসহ আন্তর্জাতিক মহল থেকে সংযম প্রদর্শনের আহ্বান জানানো হলেও উভয় পক্ষ এখনো পিছু হটার লক্ষণ দেখাচ্ছে না, যা বৈশ্বিক জ্বালানি বাজারে অস্থিরতা আরও বাড়িয়ে দিচ্ছে।", category:"international", tags:["ইরান","যুক্তরাষ্ট্র","হরমুজ প্রণালী","যুদ্ধ"], imageUrl:"https://images.unsplash.com/photo-1519501025264-65ba15a82390?w=1200", author:"rahim", authorDisplay:"রহিম উদ্দিন", date:new Date(Date.now()-3600000*4).toISOString(), comments:[], likedBy:[], shares:41},
      {id:uid(), title:"মেক্সিকো উপকূলে ৭.৩ মাত্রার শক্তিশালী ভূমিকম্প, সুনামি সতর্কতা জারি", excerpt:"মেক্সিকোর চিয়াপাস প্রদেশের উপকূলে শুক্রবার আঘাত হানা শক্তিশালী ভূমিকম্পে প্রশান্ত মহাসাগরীয় উপকূল এলাকায় সুনামি সতর্কতা দেওয়া হয়েছে।", content:"যুক্তরাষ্ট্রের ভূতাত্ত্বিক জরিপ সংস্থার তথ্য অনুযায়ী, মেক্সিকোর পুয়ের্তো মাদেরো উপকূলে অগভীর গভীরতায় শক্তিশালী এই ভূমিকম্পের উৎপত্তি হয়। অগভীর গভীরতার কারণে আশপাশের এলাকায় ভূকম্পনের তীব্রতা তুলনামূলক বেশি অনুভূত হয়েছে। সুনামি সতর্কীকরণ ব্যবস্থা থেকে জানানো হয়েছে, মেক্সিকো ও গুয়াতেমালার উপকূলীয় এলাকায় বিপজ্জনক ঢেউ আছড়ে পড়তে পারে। দক্ষিণ মেক্সিকোর ওয়াহাকাসহ প্রতিবেশী গুয়াতেমালা ও এল সালভাদরেও কম্পন অনুভূত হয়েছে বলে জানা গেছে। স্থানীয় কর্তৃপক্ষ উপকূলীয় বাসিন্দাদের সরিয়ে নেওয়ার প্রস্তুতি নিচ্ছে এবং ক্ষয়ক্ষতির প্রাথমিক তথ্য সংগ্রহের কাজ চলছে।", category:"international", tags:["ভূমিকম্প","মেক্সিকো","সুনামি"], imageUrl:"https://images.unsplash.com/photo-1524661135-423995f22d0b?w=1200", author:"admin", authorDisplay:"প্রশাসক", date:new Date(Date.now()-3600000*16).toISOString(), comments:[], likedBy:[], shares:18},
      {id:uid(), title:"বিশ্বকাপ ফাইনালে মুখোমুখি স্পেন-আর্জেন্টিনা, শিরোপা ধরে রাখার লড়াইয়ে মেসিরা", excerpt:"ইংল্যান্ডকে সেমিফাইনালে হারিয়ে টানা দ্বিতীয় শিরোপার লক্ষ্যে ফাইনালে পৌঁছেছে আর্জেন্টিনা, প্রতিপক্ষ ২০১০ সালের চ্যাম্পিয়ন স্পেন।", content:"যুক্তরাষ্ট্র, কানাডা ও মেক্সিকোর যৌথ আয়োজনে অনুষ্ঠিত এবারের বিস্তৃত আসরের ফাইনাল নির্ধারিত হয়েছে নিউ ইয়র্কের কাছে এক বিশাল স্টেডিয়ামে। শিরোপাধারী আর্জেন্টিনা সেমিফাইনালে ইংল্যান্ডকে হারিয়ে টানা দ্বিতীয় বিশ্বকাপ জয়ের স্বপ্ন নিয়ে ফাইনালে জায়গা করে নিয়েছে। অন্যদিকে তরুণ প্রতিভাবান খেলোয়াড়দের নিয়ে গড়া স্পেন দলও দুর্দান্ত ফর্মে থেকে ফাইনালে পৌঁছেছে। আয়োজকদের প্রত্যাশা, আশি হাজারের বেশি দর্শক গ্যালারিতে বসে উপভোগ করবেন এই মহারণ। বিশ্বজুড়ে ফুটবলপ্রেমীদের মধ্যে এই ম্যাচ নিয়ে চলছে জোর আলোচনা ও পূর্বাভাস।", category:"sports", tags:["বিশ্বকাপ","ফুটবল","আর্জেন্টিনা","স্পেন"], imageUrl:"https://images.unsplash.com/photo-1522778119026-d647f0596c20?w=1200", author:"rahim", authorDisplay:"রহিম উদ্দিন", date:new Date(Date.now()-3600000*6).toISOString(), comments:[], likedBy:[], shares:52},
      {id:uid(), title:"মিয়ানমার উপকূলে পরপর দুটি জাহাজডুবি, পাঁচ শতাধিক মানুষের প্রাণহানির শঙ্কা", excerpt:"জুনের শেষদিক থেকে মিয়ানমার উপকূলে দুটি বড় ধরনের জাহাজডুবির ঘটনায় বিপুলসংখ্যক যাত্রীর প্রাণহানি হতে পারে বলে যৌথ বিবৃতিতে জানানো হয়েছে।", content:"আন্তর্জাতিক ত্রাণ সংস্থাগুলোর যৌথ বিবৃতি অনুযায়ী, মিয়ানমার উপকূলে গত কয়েক সপ্তাহে ঘটে যাওয়া দুটি পৃথক জাহাজডুবির ঘটনায় পাঁচ শতাধিক মানুষ নিখোঁজ বা নিহত হতে পারেন বলে আশঙ্কা করা হচ্ছে। জাহাজ দুটিতে মূলত অভিবাসনপ্রত্যাশী ও শ্রমিকেরা ছিলেন বলে প্রাথমিক তথ্যে জানা গেছে। উদ্ধারকারী দলগুলো প্রতিকূল আবহাওয়া ও সমুদ্রের উত্তাল পরিস্থিতির কারণে অনুসন্ধান কাজ চালিয়ে যেতে হিমশিম খাচ্ছে। মানবাধিকার সংগঠনগুলো অনিয়মিত পথে সমুদ্রযাত্রার ঝুঁকি নিয়ে নতুন করে সতর্কবার্তা দিয়েছে এবং সংশ্লিষ্ট দেশগুলোকে সমন্বিত উদ্ধার তৎপরতা জোরদারের আহ্বান জানিয়েছে।", category:"international", tags:["মিয়ানমার","জাহাজডুবি","অভিবাসন"], imageUrl:"https://images.unsplash.com/photo-1544551763-46a013bb70d5?w=1200", author:"admin", authorDisplay:"প্রশাসক", date:new Date(Date.now()-3600000*19).toISOString(), comments:[], likedBy:[], shares:15},
      {id:uid(), title:"হরমুজ সংকটের মধ্যে বিকল্প তেল রপ্তানি পথ নিয়ে ইরাকের সঙ্গে চুক্তির পথে যুক্তরাষ্ট্রের কোম্পানি", excerpt:"পারস্য উপসাগরের বাইরে দিয়ে তেল রপ্তানির বিকল্প পথ তৈরিতে ইরাকের তেলক্ষেত্র ও পাইপলাইনে বিনিয়োগের বিষয়ে একটি মার্কিন জ্বালানি কোম্পানি চুক্তির কাছাকাছি পৌঁছেছে।", content:"হরমুজ প্রণালী ঘিরে চলমান সংঘাতের কারণে তেল রপ্তানিতে বড় ধাক্কা খাওয়া ইরাক এখন বিকল্প রপ্তানি পথ খুঁজতে মরিয়া। এই প্রেক্ষাপটে একটি বড় মার্কিন জ্বালানি কোম্পানি ইরাকের দুটি বড় তেলক্ষেত্রে বিনিয়োগ এবং ভূমধ্যসাগর পর্যন্ত বিস্তৃত একটি পাইপলাইন নির্মাণ নিয়ে ইরাক সরকারের সঙ্গে প্রাথমিক সমঝোতার কাছাকাছি পৌঁছেছে। প্রণালী অবরুদ্ধ থাকার কারণে ইরাকের তেল উৎপাদন উল্লেখযোগ্য হারে কমাতে বাধ্য হয়েছে দেশটি, যার প্রভাব পড়েছে সরকারের রাজস্ব আয়ে। ইরাকের প্রধানমন্ত্রী সম্প্রতি ওয়াশিংটন সফরে গিয়ে এ বিষয়ে আলোচনা করেছেন বলে জানা গেছে। বিশ্লেষকদের মতে, এই ধরনের বিকল্প রপ্তানি করিডোর বাস্তবায়িত হলে তা মধ্যপ্রাচ্যের জ্বালানি সরবরাহ কাঠামোয় দীর্ঘমেয়াদি প্রভাব ফেলতে পারে।", category:"international", tags:["ইরাক","জ্বালানি","তেল","যুক্তরাষ্ট্র"], imageUrl:"https://images.unsplash.com/photo-1518709268805-4e9042af2176?w=1200", author:"rahim", authorDisplay:"রহিম উদ্দিন", date:new Date(Date.now()-3600000*22).toISOString(), comments:[], likedBy:[], shares:11},
      {id:uid(), title:"রাজধানীতে নতুন মেট্রোরেল রুট উদ্বোধন, যাত্রীদের ভিড়", excerpt:"রাজধানীর যানজট নিরসনে চালু হলো নতুন একটি মেট্রোরেল রুট। প্রথম দিনেই যাত্রীদের ব্যাপক সাড়া লক্ষ্য করা গেছে।", content:"রাজধানী ঢাকার যানজট নিরসনে দীর্ঘদিনের প্রতীক্ষার অবসান ঘটিয়ে আজ চালু হলো নতুন মেট্রোরেল রুট। সকাল থেকেই স্টেশনগুলোতে যাত্রীদের দীর্ঘ সারি দেখা গেছে। কর্তৃপক্ষ জানিয়েছে, প্রাথমিকভাবে প্রতি ১০ মিনিট অন্তর ট্রেন চলাচল করবে এবং যাত্রীসংখ্যা বিবেচনায় শিডিউল আরও ঘন করা হবে। নগর পরিকল্পনাবিদরা বলছেন, এই রুট চালুর ফলে সংশ্লিষ্ট এলাকায় সড়ক যানজট উল্লেখযোগ্য হারে কমে আসবে।", category:"national", tags:["মেট্রোরেল","ঢাকা","যোগাযোগ"], imageUrl:"https://images.unsplash.com/photo-1544620347-c4fd4a3d5957?w=1200", author:"admin", authorDisplay:"প্রশাসক", date:new Date(now-3600000*2).toISOString(), comments:[], likedBy:[], shares:12},
      {id:uid(), title:"বিশ্ব অর্থনীতিতে প্রবৃদ্ধির নতুন পূর্বাভাস প্রকাশ", excerpt:"আন্তর্জাতিক অর্থ সংস্থার সাম্প্রতিক প্রতিবেদনে চলতি বছরের বৈশ্বিক প্রবৃদ্ধির হার নিয়ে নতুন পূর্বাভাস দেওয়া হয়েছে।", content:"আন্তর্জাতিক অর্থ সংস্থার সাম্প্রতিক এক প্রতিবেদনে বলা হয়েছে, চলতি অর্থবছরে বৈশ্বিক প্রবৃদ্ধির হার আগের পূর্বাভাসের তুলনায় সামান্য বাড়তে পারে। জ্বালানি মূল্যের স্থিতিশীলতা ও সরবরাহ ব্যবস্থার উন্নতিকে এর প্রধান কারণ হিসেবে চিহ্নিত করা হয়েছে। তবে উদীয়মান অর্থনীতিগুলোতে মুদ্রাস্ফীতি এখনও একটি চ্যালেঞ্জ হিসেবে রয়ে গেছে বলে প্রতিবেদনে উল্লেখ করা হয়।", category:"economy", tags:["অর্থনীতি","প্রবৃদ্ধি"], imageUrl:"https://images.unsplash.com/photo-1526304640581-d334cdbbf45e?w=1200", author:"admin", authorDisplay:"প্রশাসক", date:new Date(now-3600000*6).toISOString(), comments:[], likedBy:[], shares:5},
      {id:uid(), title:"জাতীয় ফুটবল দলের প্রীতি ম্যাচে দুর্দান্ত জয়", excerpt:"প্রীতি ম্যাচে প্রতিপক্ষকে তিন গোলে হারিয়ে আত্মবিশ্বাস বাড়িয়ে নিলো জাতীয় দল।", content:"একাদশে বেশ কিছু পরিবর্তন নিয়ে মাঠে নেমেও প্রতিপক্ষকে উড়িয়ে দিলো জাতীয় ফুটবল দল। ম্যাচের শুরু থেকেই আক্রমণাত্মক ফুটবল খেলে প্রথমার্ধেই দুই গোলের ব্যবধান তৈরি করে নেয় দলটি। দ্বিতীয়ার্ধে আরও একটি গোল যোগ করে ব্যবধান তিনে নিয়ে যান আক্রমণভাগের খেলোয়াড়রা। কোচ ম্যাচ শেষে খেলোয়াড়দের পারফরম্যান্সে সন্তোষ প্রকাশ করেছেন।", category:"sports", tags:["ফুটবল","জাতীয় দল"], imageUrl:"https://images.unsplash.com/photo-1508098682722-e99c43a406b2?w=1200", author:"rahim", authorDisplay:"রহিম উদ্দিন", date:new Date(now-3600000*10).toISOString(), comments:[], likedBy:[], shares:20},
      {id:uid(), title:"নতুন প্রযুক্তিতে গ্রামীণ ইন্টারনেট সংযোগে বৈপ্লবিক পরিবর্তন", excerpt:"দুর্গম অঞ্চলে দ্রুতগতির ইন্টারনেট পৌঁছে দিতে নতুন প্রযুক্তি ব্যবহারের উদ্যোগ নেওয়া হয়েছে।", content:"দেশের প্রত্যন্ত অঞ্চলগুলোতে দ্রুতগতির ইন্টারনেট সেবা পৌঁছে দিতে নতুন এক উদ্যোগ হাতে নিয়েছে সংশ্লিষ্ট কর্তৃপক্ষ। স্যাটেলাইটভিত্তিক প্রযুক্তির মাধ্যমে যেসব এলাকায় ফাইবার অপটিক সংযোগ পৌঁছানো কঠিন, সেসব স্থানে সহজে সংযোগ দেওয়া সম্ভব হবে বলে জানানো হয়েছে। বিশেষজ্ঞরা বলছেন, এর ফলে শিক্ষা ও ডিজিটাল সেবা গ্রামীণ জনগোষ্ঠীর কাছে আরও সহজলভ্য হবে।", category:"technology", tags:["ইন্টারনেট","প্রযুক্তি","গ্রাম"], imageUrl:"https://images.unsplash.com/photo-1451187580459-43490279c0fa?w=1200", author:"admin", authorDisplay:"প্রশাসক", date:new Date(now-3600000*20).toISOString(), comments:[], likedBy:[], shares:8}
    ];
    await sSet('news', news);
  }
  DB.news = news;

  SESSION = await sGetPersonal('session');
  if(SESSION){
    var u = DB.users.filter(function(x){return x.username===SESSION.username;})[0];
    if(!u || u.banned){ SESSION=null; await sSetPersonal('session', null); }
  }
}

async function refreshUsers(){ DB.users = await sGet('users') || DB.users; }
async function refreshNews(){ DB.news = await sGet('news') || DB.news; }
async function saveUsers(){ await sSet('users', DB.users); }
async function saveNews(){ await sSet('news', DB.news); }

function currentUser(){
  if(!SESSION) return null;
  return DB.users.filter(function(x){return x.username===SESSION.username;})[0] || null;
}
function isAdmin(){ var u=currentUser(); return u && u.role==='admin' && !u.banned; }

/* ---------- notifications & messages ---------- */
async function getNotifs(username){ return await sGet('notif:'+username) || []; }
async function pushNotif(username, text){
  var list = await getNotifs(username);
  list.unshift({id:uid(), text:text, date:new Date().toISOString(), read:false});
  await sSet('notif:'+username, list);
}
async function getMsgs(username){ return await sGet('msgs:'+username) || []; }
async function pushMsg(username, text, fromAdmin){
  var list = await getMsgs(username);
  list.push({id:uid(), text:text, date:new Date().toISOString(), fromAdmin:!!fromAdmin});
  await sSet('msgs:'+username, list);
}

/* ---------- auth actions ---------- */
async function doRegister(data){
  await refreshUsers();
  if(DB.users.some(function(u){return u.username.toLowerCase()===data.username.toLowerCase();})){
    throw new Error("এই ইউজারনেমটি ইতিমধ্যে ব্যবহৃত হয়েছে।");
  }
  if(DB.users.some(function(u){return u.email.toLowerCase()===data.email.toLowerCase();})){
    throw new Error("এই ইমেইল দিয়ে আগেই একটি অ্যাকাউন্ট খোলা হয়েছে।");
  }
  var user = {id:uid(), username:data.username, displayName:data.displayName, email:data.email, password:hashPw(data.password), role:'user', joined:new Date().toISOString(), banned:false};
  DB.users.push(user);
  await saveUsers();
  SESSION = {username:user.username};
  await sSetPersonal('session', SESSION);
  await pushNotif(user.username, "সংবাদপত্র-এ স্বাগতম, "+user.displayName+"! এখন থেকে আপনি সংবাদ প্রকাশ করতে পারবেন।");
}
async function doLogin(username, password){
  await refreshUsers();
  var u = DB.users.filter(function(x){return x.username.toLowerCase()===username.toLowerCase();})[0];
  if(!u || u.password !== hashPw(password)) throw new Error("ইউজারনেম অথবা পাসওয়ার্ড সঠিক নয়।");
  if(u.banned) throw new Error("এই অ্যাকাউন্টটি নিষিদ্ধ করা হয়েছে। বিস্তারিত জানতে প্রশাসকের সাথে যোগাযোগ করুন।");
  SESSION = {username:u.username};
  await sSetPersonal('session', SESSION);
}
async function doLogout(){ SESSION=null; await sSetPersonal('session', null); }

async function requestReset(identifier){
  await refreshUsers();
  var u = DB.users.filter(function(x){return x.username.toLowerCase()===identifier.toLowerCase() || x.email.toLowerCase()===identifier.toLowerCase();})[0];
  if(!u) throw new Error("এই তথ্য দিয়ে কোনো অ্যাকাউন্ট খুঁজে পাওয়া যায়নি।");
  var code = Math.floor(100000+Math.random()*900000).toString();
  u.resetCode = code;
  u.resetExpiry = Date.now()+15*60000;
  await saveUsers();
  return {username:u.username, code:code};
}
async function doReset(username, code, newPassword){
  await refreshUsers();
  var u = DB.users.filter(function(x){return x.username.toLowerCase()===username.toLowerCase();})[0];
  if(!u) throw new Error("ইউজারনেম খুঁজে পাওয়া যায়নি।");
  if(!u.resetCode || u.resetCode!==code || Date.now()>u.resetExpiry) throw new Error("কোডটি সঠিক নয় অথবা মেয়াদোত্তীর্ণ হয়ে গেছে।");
  u.password = hashPw(newPassword);
  delete u.resetCode; delete u.resetExpiry;
  await saveUsers();
}

/* ---------- news actions ---------- */
async function createArticle(data){
  await refreshNews();
  var u = currentUser();
  var art = {
    id:uid(), title:data.title, excerpt:data.excerpt || (data.content.slice(0,120)+"..."), content:data.content,
    category:data.category, tags:data.tags, imageUrl:data.imageUrl,
    author:u.username, authorDisplay:u.displayName, date:new Date().toISOString(),
    comments:[], likedBy:[], shares:0
  };
  DB.news.unshift(art);
  await saveNews();
  return art;
}
async function deleteArticle(id){
  await refreshNews();
  DB.news = DB.news.filter(function(a){return a.id!==id;});
  await saveNews();
}
async function addComment(articleId, text){
  await refreshNews();
  var a = DB.news.filter(function(x){return x.id===articleId;})[0];
  if(!a) return;
  var u = currentUser();
  a.comments.push({id:uid(), user:u.username, displayName:u.displayName, text:text, date:new Date().toISOString()});
  await saveNews();
  if(a.author!==u.username) await pushNotif(a.author, u.displayName+" আপনার '"+a.title+"' সংবাদে মন্তব্য করেছেন।");
}
async function toggleLike(articleId){
  await refreshNews();
  var a = DB.news.filter(function(x){return x.id===articleId;})[0];
  if(!a) return;
  var u = currentUser();
  a.likedBy = a.likedBy || [];
  var idx = a.likedBy.indexOf(u.username);
  if(idx>=0) a.likedBy.splice(idx,1); else a.likedBy.push(u.username);
  await saveNews();
}
async function bumpShare(articleId){
  await refreshNews();
  var a = DB.news.filter(function(x){return x.id===articleId;})[0];
  if(!a) return;
  a.shares = (a.shares||0)+1;
  await saveNews();
}
async function bumpView(articleId){
  await refreshNews();
  var a = DB.news.filter(function(x){return x.id===articleId;})[0];
  if(!a) return;
  a.views = (a.views||0)+1;
  await saveNews();
}

/* ---------- complaint box ---------- */
async function getComplaints(){ return await sGet('complaints') || []; }
async function saveComplaints(list){ await sSet('complaints', list); }
async function submitComplaint(data){
  var list = await getComplaints();
  list.unshift({id:uid(), name:data.name, contact:data.contact, subject:data.subject, message:data.message, date:new Date().toISOString(), status:'pending'});
  await saveComplaints(list);
}
async function adminSetComplaintStatus(id, status){
  var list = await getComplaints();
  var c = list.filter(function(x){return x.id===id;})[0];
  if(!c) return;
  c.status = status;
  await saveComplaints(list);
}
async function adminDeleteComplaint(id){
  var list = await getComplaints();
  list = list.filter(function(x){return x.id!==id;});
  await saveComplaints(list);
}

/* ---------- admin actions ---------- */
async function adminSetBan(username, banned){
  await refreshUsers();
  var u = DB.users.filter(function(x){return x.username===username;})[0];
  if(!u) return;
  u.banned = banned;
  await saveUsers();
}
async function adminSetRole(username, role){
  await refreshUsers();
  var u = DB.users.filter(function(x){return x.username===username;})[0];
  if(!u) return;
  u.role = role;
  await saveUsers();
}
async function adminDeleteUser(username){
  await refreshUsers();
  DB.users = DB.users.filter(function(x){return x.username!==username;});
  await saveUsers();
  await refreshNews();
  DB.news = DB.news.filter(function(a){return a.author!==username;});
  await saveNews();
}
async function adminBroadcast(text){
  await refreshUsers();
  for(var i=0;i<DB.users.length;i++){
    await pushNotif(DB.users[i].username, text);
  }
}
async function adminMessage(username, text){
  await pushMsg(username, text, true);
  await pushNotif(username, "প্রশাসকের কাছ থেকে একটি নতুন বার্তা এসেছে।");
}

/* =========================================================
   ROUTER & RENDER
   ========================================================= */
var app = document.getElementById('app');

function route(){ return location.hash.replace(/^#\/?/,'') || ''; }

async function render(){
  var r = route();
  var parts = r.split('/');
  var view = parts[0] || 'home';
  var html = "";

  if(view==='home') html = viewHome();
  else if(view==='category') html = viewHome(parts[1]);
  else if(view==='search') html = viewHome(null, decodeURIComponent(parts[1]||''));
  else if(view==='article') html = await viewArticle(parts[1]);
  else if(view==='login') html = viewLogin();
  else if(view==='register') html = viewRegister();
  else if(view==='forgot') html = viewForgot();
  else if(view==='reset') html = viewReset(parts[1], parts[2]);
  else if(view==='complaint') html = viewComplaint();
  else if(view==='new') html = SESSION ? viewNewPost() : viewLoginRequired();
  else if(view==='profile') html = SESSION ? await viewProfile() : viewLoginRequired();
  else if(view==='admin') html = isAdmin() ? await viewAdmin(parts[1]||'overview') : viewNoAccess();
  else html = viewHome();

  app.innerHTML = shell(html);
  bindEvents();
  window.scrollTo({top:0, behavior:'instant' in window ? 'instant':'auto'});
}

function shell(inner){
  var u = currentUser();
  return ''+
  '<header class="masthead"><div class="masthead-inner">'+
    '<div class="masthead-top">'+
      '<span>প্রথম প্রকাশ · ২০২৬</span>'+
      '<span class="mono">'+new Date().toLocaleDateString('bn-BD',{weekday:'long',year:'numeric',month:'long',day:'numeric'})+'</span>'+
    '</div>'+
    '<div class="director-badge"><img class="d-photo" src="'+DIRECTOR_IMG+'" alt="Md. Emdadul Haque Milon">'+
      '<div class="d-name">Md. Emdadul Haque Milon<span class="d-role">(পরিচালক)</span></div>'+
    '</div>'+
    '<div class="nameplate"><h1><a href="#/">সংবাদপত্র</a></h1><div class="sub">সত্য অনুসন্ধানের একটি প্ল্যাটফর্ম</div></div>'+
    '<div class="masthead-actions">'+
      '<button class="theme-toggle" data-action="toggle-theme" title="থিম পরিবর্তন করুন">'+(SESSION_THEME==='dark'?'☀ লাইট মোড':'🌙 ডার্ক মোড')+'</button>'+
      (u ? (
        '<a class="btn btn-primary" href="#/new"><i>+</i> সংবাদ প্রকাশ করুন</a>'+
        '<a class="btn btn-ghost" href="#/profile">'+esc(u.displayName)+'</a>'+
        (u.role==='admin' ? '<a class="btn btn-ghost" href="#/admin">প্রশাসন প্যানেল</a>' : '')+
        '<button class="btn btn-ghost" data-action="logout">লগআউট</button>'
      ) : (
        '<a class="btn btn-ghost" href="#/login">লগইন</a>'+
        '<a class="btn btn-primary" href="#/register">রেজিস্ট্রেশন</a>'
      ))+
    '</div>'+
  '</div></header>'+
  '<div class="ticker-bar"><span class="ticker-tag"><span class="ticker-dot"></span>এই মুহূর্তে</span>'+
    '<div class="ticker-track"><span>'+tickerText()+'</span><span>'+tickerText()+'</span></div>'+
  '</div>'+
  '<nav class="catnav"><div class="catnav-inner">'+
    '<a href="#/" class="'+(route()===''||route()==='home'?'active':'')+'">সর্বশেষ</a>'+
    CATEGORIES.map(function(c){
      var active = route()==='category/'+c.id;
      return '<a href="#/category/'+c.id+'" class="'+(active?'active':'')+'">'+c.name+'</a>';
    }).join('')+
    '<a href="#/complaint" class="'+(route()==='complaint'?'active':'')+'" style="margin-left:auto;color:var(--crimson);font-weight:600">⚠ অভিযোগ করুন</a>'+
  '</div></nav>'+
  '<main class="wrap">'+inner+'</main>'+
  '<footer><div class="foot-name">সংবাদপত্র</div><div>একটি নমুনা সংবাদ প্রকাশনা প্ল্যাটফর্ম</div>'+
    '<div class="foot-links"><a href="#/">প্রচ্ছদ</a><a href="#/complaint">অভিযোগ করুন</a><a href="#/register">রেজিস্ট্রেশন</a></div>'+
    '<div class="disclaimer">এটি একটি প্রদর্শনী (ডেমো) প্রকল্প। এই সাইটে প্রকাশিত সকল সংবাদ, ব্যবহারকারী ও তথ্য সবার জন্য উন্মুক্ত সংরক্ষণাগারে (shared storage) জমা থাকে — অর্থাৎ এই পেজটি যারাই খুলবেন, তারা একই তথ্যভাণ্ডার দেখবেন ও পরিবর্তন করতে পারবেন। বাস্তব ব্যক্তিগত তথ্য বা পাসওয়ার্ড ব্যবহার করবেন না। ডেমো প্রশাসক প্রবেশ তথ্য: admin / admin123</div>'+
  '</footer>';
}

function tickerText(){
  var latest = DB.news.slice(0,6).map(function(a){ return catName(a.category)+" · "+a.title; });
  return latest.join('&nbsp;&nbsp;&nbsp;///&nbsp;&nbsp;&nbsp;') || "সংবাদপত্র-এ স্বাগতম";
}

function viewLoginRequired(){
  return '<div class="empty"><h3>এই সুবিধা পেতে লগইন করুন</h3><p>সংবাদ প্রকাশ, মন্তব্য ও প্রোফাইল দেখতে আপনাকে লগইন করতে হবে।</p>'+
  '<a class="btn btn-primary" href="#/login">লগইন করুন</a></div>';
}
function viewNoAccess(){
  return '<div class="empty"><h3>প্রবেশাধিকার নেই</h3><p>এই পাতাটি শুধুমাত্র প্রশাসকদের জন্য সংরক্ষিত।</p><a class="btn btn-ghost" href="#/">প্রচ্ছদে ফিরুন</a></div>';
}

/* ---- Complaint box ---- */
function viewComplaint(){
  var u = currentUser();
  return '<div class="form-shell" style="max-width:640px;margin:0 auto">'+
    '<h2>অভিযোগ ও পরামর্শ</h2>'+
    '<p style="color:var(--ink-soft);font-size:14px;margin-bottom:20px;margin-top:-10px">কোনো সংবাদ, ব্যবহারকারী বা সাইট সংক্রান্ত অভিযোগ, ভুল তথ্যের প্রতিবেদন কিংবা পরামর্শ থাকলে নিচের ফর্মটি পূরণ করুন। প্রশাসক টিম প্রতিটি অভিযোগ পর্যালোচনা করে যথাযথ ব্যবস্থা নেবে।</p>'+
    '<form data-form="complaint">'+
      '<div class="field"><label>আপনার নাম</label><input type="text" name="name" value="'+(u?esc(u.displayName):'')+'" required></div>'+
      '<div class="field"><label>ইমেইল অথবা ফোন নম্বর</label><input type="text" name="contact" value="'+(u?esc(u.email):'')+'" required></div>'+
      '<div class="field"><label>বিষয়</label><input type="text" name="subject" placeholder="যেমন: ভুল তথ্য, অনুপযুক্ত মন্তব্য, প্রযুক্তিগত সমস্যা..." required></div>'+
      '<div class="field"><label>বিস্তারিত বিবরণ</label><textarea name="message" style="min-height:150px" placeholder="আপনার অভিযোগ বিস্তারিত লিখুন..." required></textarea></div>'+
      '<button class="btn btn-primary" type="submit">অভিযোগ জমা দিন</button>'+
    '</form>'+
  '</div>';
}

/* ---- Home ---- */
function viewHome(catFilter, searchQ){
  var list = DB.news.slice().sort(function(a,b){return new Date(b.date)-new Date(a.date);});
  if(catFilter) list = list.filter(function(a){return a.category===catFilter;});
  if(searchQ) list = list.filter(function(a){return (a.title+a.excerpt+(a.tags||[]).join(' ')).toLowerCase().indexOf(searchQ.toLowerCase())>=0;});

  var html = '<form class="search-box" data-form="search">'+
    '<input type="text" name="q" placeholder="সংবাদ অনুসন্ধান করুন..." value="'+esc(searchQ||'')+'">'+
    '<button class="btn btn-ghost" type="submit">খুঁজুন</button>'+
  '</form>';

  if(!list.length){
    html += '<div class="empty"><h3>কোনো সংবাদ পাওয়া যায়নি</h3><p>ভিন্ন বিভাগ বা শব্দ দিয়ে আবার চেষ্টা করুন।</p></div>';
    return html;
  }

  if(!catFilter && !searchQ){
    var hero = list[0];
    var rest = list.slice(1);
    html += '<div class="hero">'+
      '<a href="#/article/'+hero.id+'">'+(hero.imageUrl?'<img class="thumb" src="'+esc(hero.imageUrl)+'" alt="">':'')+'</a>'+
      '<div><span class="badge brass">'+catName(hero.category)+' · প্রধান খবর</span>'+
      '<h2><a href="#/article/'+hero.id+'">'+esc(hero.title)+'</a></h2>'+
      '<p class="excerpt">'+esc(hero.excerpt)+'</p>'+
      '<div class="byline"><span>প্রতিবেদক: '+esc(hero.authorDisplay)+'</span><span class="mono">'+fmtDate(hero.date)+'</span></div>'+
      '</div></div>';
    list = rest;
  } else {
    html += '<div class="section-title"><span class="dot"></span>'+(catFilter?catName(catFilter):'অনুসন্ধান ফলাফল')+'</div>';
  }

  html += '<div class="grid"><div>';
  if(!list.length){
    html += '<div class="empty">আর কোনো সংবাদ নেই।</div>';
  } else {
    list.forEach(function(a){
      html += renderCard(a);
    });
  }
  html += '</div><div>'+sidebar()+'</div></div>';
  return html;
}

function renderCard(a){
  var u = currentUser();
  var liked = u && (a.likedBy||[]).indexOf(u.username)>=0;
  return '<article class="article-card">'+
    (a.imageUrl?'<a href="#/article/'+a.id+'"><img class="thumb" src="'+esc(a.imageUrl)+'" alt="" onerror="this.style.display=\'none\'"></a>':'')+
    '<span class="badge">'+catName(a.category)+'</span>'+
    '<h2><a href="#/article/'+a.id+'">'+esc(a.title)+'</a></h2>'+
    '<p class="excerpt">'+esc(a.excerpt)+'</p>'+
    '<div class="byline"><span>'+esc(a.authorDisplay)+'</span><span class="mono">'+fmtDate(a.date)+'</span></div>'+
    '<div class="card-actions">'+
      '<button class="like-btn small '+(liked?'liked':'')+'" data-action="like" data-id="'+a.id+'">♥ '+(a.likedBy?a.likedBy.length:0)+'</button>'+
      '<a class="card-action-link" href="#/article/'+a.id+'">💬 মন্তব্য '+(a.comments?a.comments.length:0)+'</a>'+
      '<button class="card-action-link" data-action="share-copy" data-id="'+a.id+'">🔗 শেয়ার</button>'+
      '<button class="card-action-link" data-action="share-fb" data-id="'+a.id+'">Facebook</button>'+
      '<button class="card-action-link" data-action="share-wa" data-id="'+a.id+'">WhatsApp</button>'+
      '<span class="mono card-views">👁 '+(a.views||0)+'</span>'+
    '</div>'+
  '</article>';
}

function sidebar(){
  var trending = DB.news.slice().sort(function(a,b){return ((b.likedBy||[]).length+b.shares)-((a.likedBy||[]).length+a.shares);}).slice(0,5);
  var html = '<div class="side-box"><h3>জনপ্রিয় সংবাদ</h3>';
  trending.forEach(function(a,i){
    html += '<div class="side-item"><span class="num mono">'+String(i+1).padStart(2,'0')+'</span><span class="t"><a href="#/article/'+a.id+'">'+esc(a.title)+'</a></span></div>';
  });
  html += '</div>';
  html += '<div class="side-box"><h3>বিভাগসমূহ</h3>';
  CATEGORIES.forEach(function(c){
    var count = DB.news.filter(function(a){return a.category===c.id;}).length;
    html += '<div class="side-item"><span class="t"><a href="#/category/'+c.id+'">'+c.name+' <span class="mono" style="color:var(--ink-soft)">('+count+')</span></a></span></div>';
  });
  html += '</div>';
  return html;
}

/* ---- Article ---- */
async function viewArticle(id){
  await refreshNews();
  var a = DB.news.filter(function(x){return x.id===id;})[0];
  if(!a) return '<div class="empty"><h3>সংবাদটি খুঁজে পাওয়া যায়নি</h3><a class="btn btn-ghost" href="#/">প্রচ্ছদে ফিরুন</a></div>';
  await bumpView(id);
  var u = currentUser();
  var liked = u && (a.likedBy||[]).indexOf(u.username)>=0;
  var canManage = u && (u.username===a.author || u.role==='admin');
  var wordCount = (a.content||'').split(/\s+/).filter(Boolean).length;
  var readMin = Math.max(1, Math.round(wordCount/180));

  var html = '<div class="grid"><div>';
  html += '<span class="badge brass">'+catName(a.category)+'</span>';
  html += '<h1 style="font-size:32px;line-height:1.3;margin:8px 0 10px">'+esc(a.title)+'</h1>';
  html += '<div class="detail-dateline">ঢাকা প্রতিবেদক · '+esc(a.authorDisplay)+' · '+fmtDate(a.date)+'</div>';
  html += '<div class="read-meta"><span>⏱ পড়তে সময় লাগবে প্রায় '+readMin+' মিনিট</span><span>👁 দেখা হয়েছে '+((a.views||0))+' বার</span></div>';
  if(a.imageUrl) html += '<img class="detail-hero-img" src="'+esc(a.imageUrl)+'" alt="" onerror="this.style.display=\'none\'">';
  html += '<div class="detail-body">'+nl2br(a.content)+'</div>';
  if(a.tags && a.tags.length){
    html += '<div class="tag-row">'+a.tags.map(function(t){return '<span class="tag-chip">#'+esc(t)+'</span>';}).join('')+'</div>';
  }
  html += '<div class="share-row">'+
    '<button class="like-btn '+(liked?'liked':'')+'" data-action="like" data-id="'+a.id+'">♥ পছন্দ ('+(a.likedBy?a.likedBy.length:0)+')</button>'+
    '<button class="btn btn-ghost btn-sm" data-action="share-copy" data-id="'+a.id+'">লিংক কপি করুন</button>'+
    '<button class="btn btn-ghost btn-sm" data-action="share-fb" data-id="'+a.id+'">ফেসবুকে শেয়ার</button>'+
    '<button class="btn btn-ghost btn-sm" data-action="share-wa" data-id="'+a.id+'">হোয়াটসঅ্যাপে শেয়ার</button>'+
    '<span class="mono" style="align-self:center;font-size:12px;color:var(--ink-soft)">মোট শেয়ার: '+(a.shares||0)+'</span>'+
  '</div>';
  if(canManage){
    html += '<div style="margin-bottom:20px"><button class="btn btn-danger btn-sm" data-action="delete-article" data-id="'+a.id+'">এই সংবাদটি মুছে ফেলুন</button></div>';
  }

  html += '<div class="section-title"><span class="dot"></span>মন্তব্য ('+a.comments.length+')</div>';
  if(u){
    html += '<form data-form="comment" data-id="'+a.id+'" class="field" style="margin-bottom:20px">'+
      '<textarea name="text" placeholder="আপনার মন্তব্য লিখুন..." required style="min-height:70px"></textarea>'+
      '<button class="btn btn-primary btn-sm" style="margin-top:8px" type="submit">মন্তব্য করুন</button>'+
    '</form>';
  } else {
    html += '<div class="hint-box">মন্তব্য করতে <a href="#/login" style="color:var(--crimson);font-weight:500">লগইন</a> করুন।</div>';
  }
  if(!a.comments.length){
    html += '<div class="empty" style="padding:20px">এখনো কোনো মন্তব্য নেই। প্রথম মন্তব্যটি করুন।</div>';
  } else {
    a.comments.slice().reverse().forEach(function(c){
      html += '<div class="comment"><div class="who">'+esc(c.displayName)+'</div><div class="txt">'+esc(c.text)+'</div><span class="when">'+fmtDate(c.date)+'</span></div>';
    });
  }
  html += '</div><div>'+sidebar()+'</div></div>';
  return html;
}

/* ---- Auth views ---- */
function viewLogin(){
  return '<div class="auth-shell"><h2>লগইন করুন</h2><p class="lead">আপনার অ্যাকাউন্টে প্রবেশ করুন</p>'+
    '<div class="hint-box">ডেমো প্রশাসক: <b class="mono">admin</b> / <b class="mono">admin123</b></div>'+
    '<form data-form="login">'+
    '<div class="field"><label>ইউজারনেম</label><input type="text" name="username" required autofocus></div>'+
    '<div class="field"><label>পাসওয়ার্ড</label><input type="password" name="password" required></div>'+
    '<button class="btn btn-primary" style="width:100%" type="submit">লগইন করুন</button>'+
    '</form>'+
    '<div class="auth-switch"><a href="#/forgot">পাসওয়ার্ড ভুলে গেছেন?</a></div>'+
    '<div class="auth-switch">অ্যাকাউন্ট নেই? <a href="#/register">রেজিস্ট্রেশন করুন</a></div>'+
  '</div>';
}
function viewRegister(){
  return '<div class="auth-shell"><h2>রেজিস্ট্রেশন করুন</h2><p class="lead">নতুন অ্যাকাউন্ট খুলুন এবং সংবাদ প্রকাশ শুরু করুন</p>'+
    '<form data-form="register">'+
    '<div class="field"><label>পুরো নাম</label><input type="text" name="displayName" required></div>'+
    '<div class="field"><label>ইউজারনেম</label><input type="text" name="username" pattern="[a-zA-Z0-9_]{3,20}" title="৩-২০ অক্ষর, শুধু ইংরেজি অক্ষর/সংখ্যা/আন্ডারস্কোর" required></div>'+
    '<div class="field"><label>ইমেইল</label><input type="email" name="email" required></div>'+
    '<div class="field"><label>পাসওয়ার্ড</label><input type="password" name="password" minlength="6" required></div>'+
    '<div class="field"><label>পাসওয়ার্ড নিশ্চিত করুন</label><input type="password" name="password2" minlength="6" required></div>'+
    '<button class="btn btn-primary" style="width:100%" type="submit">রেজিস্ট্রেশন করুন</button>'+
    '</form>'+
    '<div class="auth-switch">ইতিমধ্যে অ্যাকাউন্ট আছে? <a href="#/login">লগইন করুন</a></div>'+
  '</div>';
}
function viewForgot(){
  return '<div class="auth-shell"><h2>পাসওয়ার্ড রিসেট</h2><p class="lead">ইউজারনেম বা ইমেইল দিন, আমরা একটি রিসেট কোড দেব</p>'+
    '<div class="hint-box">এই ডেমোতে সত্যিকারের ইমেইল পাঠানো হয় না — কোডটি সরাসরি স্ক্রিনে দেখানো হবে।</div>'+
    '<form data-form="forgot">'+
    '<div class="field"><label>ইউজারনেম অথবা ইমেইল</label><input type="text" name="identifier" required autofocus></div>'+
    '<button class="btn btn-primary" style="width:100%" type="submit">কোড পাঠান</button>'+
    '</form>'+
    '<div class="auth-switch"><a href="#/login">লগইনে ফিরে যান</a></div>'+
  '</div>';
}
function viewReset(username, code){
  return '<div class="auth-shell"><h2>নতুন পাসওয়ার্ড সেট করুন</h2><p class="lead">প্রাপ্ত কোড ও নতুন পাসওয়ার্ড দিন</p>'+
    '<form data-form="reset">'+
    '<div class="field"><label>ইউজারনেম</label><input type="text" name="username" value="'+esc(username||'')+'" required></div>'+
    '<div class="field"><label>রিসেট কোড</label><input type="text" name="code" value="'+esc(code||'')+'" required></div>'+
    '<div class="field"><label>নতুন পাসওয়ার্ড</label><input type="password" name="password" minlength="6" required></div>'+
    '<button class="btn btn-primary" style="width:100%" type="submit">পাসওয়ার্ড পরিবর্তন করুন</button>'+
    '</form>'+
    '<div class="auth-switch"><a href="#/login">লগইনে ফিরে যান</a></div>'+
  '</div>';
}

/* ---- New post ---- */
function viewNewPost(){
  return '<div class="form-shell"><h2>নতুন সংবাদ প্রকাশ করুন</h2>'+
    '<form data-form="newpost">'+
    '<div class="field"><label>শিরোনাম</label><input type="text" name="title" required></div>'+
    '<div class="row2">'+
      '<div class="field"><label>বিভাগ</label><select name="category" required>'+
        CATEGORIES.map(function(c){return '<option value="'+c.id+'">'+c.name+'</option>';}).join('')+
      '</select></div>'+
      '<div class="field"><label>ট্যাগ (কমা দিয়ে আলাদা করুন)</label><input type="text" name="tags" placeholder="যেমন: ঢাকা, নির্বাচন"></div>'+
    '</div>'+
    '<div class="field"><label>ছবির লিংক (URL)</label><input type="url" name="imageUrl" placeholder="https://..."></div>'+
    '<div class="field"><label>সংক্ষিপ্ত বিবরণ (ঐচ্ছিক)</label><textarea name="excerpt" style="min-height:60px" placeholder="খালি রাখলে বিস্তারিত থেকে স্বয়ংক্রিয়ভাবে তৈরি হবে"></textarea></div>'+
    '<div class="field"><label>বিস্তারিত সংবাদ</label><textarea name="content" style="min-height:220px" required></textarea></div>'+
    '<button class="btn btn-primary" type="submit">প্রকাশ করুন</button>'+
    '</form></div>';
}

/* ---- Profile ---- */
async function viewProfile(){
  var u = currentUser();
  var q = route().split('/')[1] || 'posts';
  await refreshNews();
  var myPosts = DB.news.filter(function(a){return a.author===u.username;});
  var notifs = await getNotifs(u.username);
  var msgs = await getMsgs(u.username);

  var html = '<h2 style="font-size:28px;margin-bottom:4px">'+esc(u.displayName)+'</h2>'+
    '<p style="color:var(--ink-soft);font-size:14px;margin-bottom:20px">@'+esc(u.username)+' · '+esc(u.email)+' · যোগদান: '+fmtDate(u.joined)+'</p>'+
    '<div class="tabs">'+
      '<button data-tab="posts" class="'+(q==='posts'?'active':'')+'">আমার সংবাদ ('+myPosts.length+')</button>'+
      '<button data-tab="notifs" class="'+(q==='notifs'?'active':'')+'">নোটিফিকেশন ('+notifs.filter(function(n){return !n.read;}).length+')</button>'+
      '<button data-tab="msgs" class="'+(q==='msgs'?'active':'')+'">প্রশাসকের বার্তা ('+msgs.length+')</button>'+
    '</div>';

  if(q==='notifs'){
    if(!notifs.length) html += '<div class="empty">কোনো নোটিফিকেশন নেই।</div>';
    else notifs.forEach(function(n){ html += '<div class="notif-item '+(n.read?'':'unread')+'">'+esc(n.text)+'<span class="when">'+fmtDate(n.date)+'</span></div>'; });
  } else if(q==='msgs'){
    if(!msgs.length) html += '<div class="empty">প্রশাসকের কাছ থেকে কোনো বার্তা আসেনি।</div>';
    else msgs.slice().reverse().forEach(function(m){ html += '<div class="msg-item admin"><b>প্রশাসক:</b> '+esc(m.text)+'<span class="when">'+fmtDate(m.date)+'</span></div>'; });
  } else {
    if(!myPosts.length){
      html += '<div class="empty"><h3>এখনো কোনো সংবাদ প্রকাশ করেননি</h3><a class="btn btn-primary" href="#/new">প্রথম সংবাদ প্রকাশ করুন</a></div>';
    } else {
      myPosts.forEach(function(a){
        html += '<article class="article-card"><span class="badge">'+catName(a.category)+'</span>'+
          '<h2><a href="#/article/'+a.id+'">'+esc(a.title)+'</a></h2>'+
          '<div class="byline"><span class="mono">'+fmtDate(a.date)+'</span><span>মন্তব্য '+a.comments.length+'</span><span>পছন্দ '+(a.likedBy?a.likedBy.length:0)+'</span></div>'+
          '<div style="margin-top:8px"><button class="btn btn-danger btn-sm" data-action="delete-article" data-id="'+a.id+'">মুছে ফেলুন</button></div>'+
        '</article>';
      });
    }
  }
  return html;
}

/* ---- Admin ---- */
async function viewAdmin(tab){
  await refreshUsers(); await refreshNews();
  var complaints = await getComplaints();
  var pendingComplaints = complaints.filter(function(c){return c.status!=='resolved';}).length;
  var totalComments = DB.news.reduce(function(s,a){return s+a.comments.length;},0);
  var html = '<h2 style="font-size:28px;margin-bottom:16px">প্রশাসন প্যানেল</h2>';
  html += '<div class="stat-grid">'+
    '<div class="stat"><div class="n mono">'+DB.users.length+'</div><div class="l">মোট ব্যবহারকারী</div></div>'+
    '<div class="stat"><div class="n mono">'+DB.news.length+'</div><div class="l">মোট সংবাদ</div></div>'+
    '<div class="stat"><div class="n mono">'+totalComments+'</div><div class="l">মোট মন্তব্য</div></div>'+
    '<div class="stat"><div class="n mono">'+DB.users.filter(function(u){return u.banned;}).length+'</div><div class="l">নিষিদ্ধ ব্যবহারকারী</div></div>'+
    '<div class="stat"><div class="n mono">'+pendingComplaints+'</div><div class="l">অমীমাংসিত অভিযোগ</div></div>'+
  '</div>';
  html += '<div class="tabs">'+
    ['users','news','complaints','notify','message'].map(function(t){
      var labels={users:'ব্যবহারকারী',news:'সংবাদ ব্যবস্থাপনা',complaints:'অভিযোগসমূহ ('+pendingComplaints+')',notify:'নোটিফিকেশন পাঠান',message:'ব্যক্তিগত বার্তা'};
      return '<button data-admin-tab="'+t+'" class="'+(tab===t?'active':'')+'">'+labels[t]+'</button>';
    }).join('')+
  '</div>';

  if(tab==='users'){
    html += '<div class="table-wrap"><table><thead><tr><th>ইউজারনেম</th><th>নাম</th><th>ইমেইল</th><th>ভূমিকা</th><th>অবস্থা</th><th>যোগদান</th><th>কার্যক্রম</th></tr></thead><tbody>';
    DB.users.forEach(function(u){
      html += '<tr><td class="mono">'+esc(u.username)+'</td><td>'+esc(u.displayName)+'</td><td class="mono">'+esc(u.email)+'</td>'+
        '<td><span class="pill '+(u.role==='admin'?'admin':'user')+'">'+(u.role==='admin'?'প্রশাসক':'ব্যবহারকারী')+'</span></td>'+
        '<td><span class="pill '+(u.banned?'banned':'active')+'">'+(u.banned?'নিষিদ্ধ':'সক্রিয়')+'</span></td>'+
        '<td class="mono" style="font-size:12px">'+fmtDate(u.joined)+'</td>'+
        '<td><div class="action-icons">'+
          '<button class="icon-btn" data-action="admin-ban" data-user="'+esc(u.username)+'" data-val="'+(!u.banned)+'">'+(u.banned?'নিষেধ তুলুন':'নিষিদ্ধ করুন')+'</button>'+
          (u.role==='admin' ? '<button class="icon-btn" data-action="admin-role" data-user="'+esc(u.username)+'" data-val="user">প্রশাসক বাতিল</button>' : '<button class="icon-btn" data-action="admin-role" data-user="'+esc(u.username)+'" data-val="admin">প্রশাসক করুন</button>')+
          '<button class="icon-btn" data-action="admin-delete-user" data-user="'+esc(u.username)+'">মুছুন</button>'+
        '</div></td></tr>';
    });
    html += '</tbody></table></div>';
  } else if(tab==='news'){
    html += '<div class="table-wrap"><table><thead><tr><th>শিরোনাম</th><th>বিভাগ</th><th>লেখক</th><th>তারিখ</th><th>মন্তব্য</th><th>কার্যক্রম</th></tr></thead><tbody>';
    DB.news.forEach(function(a){
      html += '<tr><td><a href="#/article/'+a.id+'">'+esc(a.title.slice(0,40))+(a.title.length>40?'…':'')+'</a></td>'+
        '<td>'+catName(a.category)+'</td><td>'+esc(a.authorDisplay)+'</td>'+
        '<td class="mono" style="font-size:12px">'+fmtDate(a.date)+'</td><td>'+a.comments.length+'</td>'+
        '<td><button class="icon-btn" data-action="delete-article" data-id="'+a.id+'">মুছুন</button></td></tr>';
    });
    html += '</tbody></table></div>';
  } else if(tab==='complaints'){
    if(!complaints.length){
      html += '<div class="empty">এখনো কোনো অভিযোগ জমা পড়েনি।</div>';
    } else {
      html += '<div class="table-wrap"><table><thead><tr><th>প্রেরক</th><th>যোগাযোগ</th><th>বিষয়</th><th>বার্তা</th><th>তারিখ</th><th>অবস্থা</th><th>কার্যক্রম</th></tr></thead><tbody>';
      complaints.forEach(function(c){
        html += '<tr><td>'+esc(c.name)+'</td><td class="mono" style="font-size:12px">'+esc(c.contact)+'</td>'+
          '<td>'+esc(c.subject)+'</td><td class="complaint-msg">'+esc(c.message)+'</td>'+
          '<td class="mono" style="font-size:12px">'+fmtDate(c.date)+'</td>'+
          '<td><span class="pill '+(c.status==='resolved'?'resolved':'pending')+'">'+(c.status==='resolved'?'সমাধান হয়েছে':'অমীমাংসিত')+'</span></td>'+
          '<td><div class="action-icons">'+
            (c.status==='resolved'
              ? '<button class="icon-btn" data-action="complaint-status" data-id="'+c.id+'" data-val="pending">অমীমাংসিত করুন</button>'
              : '<button class="icon-btn" data-action="complaint-status" data-id="'+c.id+'" data-val="resolved">সমাধান হয়েছে চিহ্নিত করুন</button>')+
            '<button class="icon-btn" data-action="complaint-delete" data-id="'+c.id+'">মুছুন</button>'+
          '</div></td></tr>';
      });
      html += '</tbody></table></div>';
    }
  } else if(tab==='notify'){
    html += '<div class="form-shell" style="padding:24px"><h3 style="margin-bottom:14px">সকল ব্যবহারকারীর কাছে নোটিফিকেশন পাঠান</h3>'+
      '<form data-form="broadcast"><div class="field"><textarea name="text" placeholder="আপনার বার্তা লিখুন..." required></textarea></div>'+
      '<button class="btn btn-primary" type="submit">সবাইকে পাঠান</button></form></div>';
  } else if(tab==='message'){
    html += '<div class="form-shell" style="padding:24px"><h3 style="margin-bottom:14px">নির্দিষ্ট ব্যবহারকারীকে ব্যক্তিগত বার্তা পাঠান</h3>'+
      '<form data-form="directmsg">'+
      '<div class="field"><label>ব্যবহারকারী নির্বাচন করুন</label><select name="username" required>'+
        DB.users.filter(function(u){return u.role!=='admin';}).map(function(u){return '<option value="'+esc(u.username)+'">'+esc(u.displayName)+' (@'+esc(u.username)+')</option>';}).join('')+
      '</select></div>'+
      '<div class="field"><textarea name="text" placeholder="আপনার বার্তা লিখুন..." required></textarea></div>'+
      '<button class="btn btn-primary" type="submit">বার্তা পাঠান</button></form></div>';
  }
  return html;
}

/* =========================================================
   EVENTS
   ========================================================= */
function bindEvents(){
  var logoutBtn = app.querySelector('[data-action="logout"]');
  if(logoutBtn) logoutBtn.addEventListener('click', async function(){ await doLogout(); toast('লগআউট সম্পন্ন হয়েছে।'); render(); });

  var searchForm = app.querySelector('[data-form="search"]');
  if(searchForm) searchForm.addEventListener('submit', function(e){
    e.preventDefault();
    var q = new FormData(searchForm).get('q').trim();
    if(q) location.hash = '#/search/'+encodeURIComponent(q); else location.hash='#/';
  });

  var loginForm = app.querySelector('[data-form="login"]');
  if(loginForm) loginForm.addEventListener('submit', async function(e){
    e.preventDefault();
    var fd = new FormData(loginForm);
    try{ await doLogin(fd.get('username'), fd.get('password')); toast('স্বাগতম!'); location.hash='#/'; render(); }
    catch(err){ toast(err.message); }
  });

  var regForm = app.querySelector('[data-form="register"]');
  if(regForm) regForm.addEventListener('submit', async function(e){
    e.preventDefault();
    var fd = new FormData(regForm);
    var data = {displayName:fd.get('displayName').trim(), username:fd.get('username').trim(), email:fd.get('email').trim(), password:fd.get('password')};
    if(fd.get('password')!==fd.get('password2')){ toast('পাসওয়ার্ড দুটি মিলছে না।'); return; }
    try{ await doRegister(data); toast('রেজিস্ট্রেশন সম্পন্ন হয়েছে!'); location.hash='#/'; render(); }
    catch(err){ toast(err.message); }
  });

  var forgotForm = app.querySelector('[data-form="forgot"]');
  if(forgotForm) forgotForm.addEventListener('submit', async function(e){
    e.preventDefault();
    var fd = new FormData(forgotForm);
    try{
      var res = await requestReset(fd.get('identifier').trim());
      app.querySelector('.wrap').insertAdjacentHTML('afterbegin', '<div class="auth-shell"><div class="code-reveal"><div style="font-size:13px;color:var(--forest);margin-bottom:6px">আপনার রিসেট কোড (ডেমো)</div><div class="code">'+res.code+'</div></div><a class="btn btn-primary" style="width:100%;display:block;text-align:center" href="#/reset/'+res.username+'/'+res.code+'">পাসওয়ার্ড রিসেট করতে এগিয়ে যান</a></div>');
    }catch(err){ toast(err.message); }
  });

  var resetForm = app.querySelector('[data-form="reset"]');
  if(resetForm) resetForm.addEventListener('submit', async function(e){
    e.preventDefault();
    var fd = new FormData(resetForm);
    try{ await doReset(fd.get('username').trim(), fd.get('code').trim(), fd.get('password')); toast('পাসওয়ার্ড পরিবর্তন সম্পন্ন হয়েছে। এখন লগইন করুন।'); location.hash='#/login'; render(); }
    catch(err){ toast(err.message); }
  });

  var newPostForm = app.querySelector('[data-form="newpost"]');
  if(newPostForm) newPostForm.addEventListener('submit', async function(e){
    e.preventDefault();
    var fd = new FormData(newPostForm);
    var tags = (fd.get('tags')||'').split(',').map(function(t){return t.trim();}).filter(Boolean);
    var data = {title:fd.get('title').trim(), category:fd.get('category'), tags:tags, imageUrl:fd.get('imageUrl').trim(), excerpt:fd.get('excerpt').trim(), content:fd.get('content').trim()};
    var art = await createArticle(data);
    toast('সংবাদ প্রকাশিত হয়েছে!');
    location.hash = '#/article/'+art.id; render();
  });

  var commentForm = app.querySelector('[data-form="comment"]');
  if(commentForm) commentForm.addEventListener('submit', async function(e){
    e.preventDefault();
    var fd = new FormData(commentForm);
    var text = fd.get('text').trim();
    if(!text) return;
    await addComment(commentForm.getAttribute('data-id'), text);
    toast('মন্তব্য যুক্ত হয়েছে।'); render();
  });

  var complaintForm = app.querySelector('[data-form="complaint"]');
  if(complaintForm) complaintForm.addEventListener('submit', async function(e){
    e.preventDefault();
    var fd = new FormData(complaintForm);
    var data = {name:fd.get('name').trim(), contact:fd.get('contact').trim(), subject:fd.get('subject').trim(), message:fd.get('message').trim()};
    await submitComplaint(data);
    toast('আপনার অভিযোগ সফলভাবে জমা হয়েছে। ধন্যবাদ।');
    location.hash = '#/'; render();
  });

  var broadcastForm = app.querySelector('[data-form="broadcast"]');
  if(broadcastForm) broadcastForm.addEventListener('submit', async function(e){
    e.preventDefault();
    var text = new FormData(broadcastForm).get('text').trim();
    await adminBroadcast(text); toast('সকল ব্যবহারকারীর কাছে নোটিফিকেশন পাঠানো হয়েছে।'); broadcastForm.reset();
  });

  var directForm = app.querySelector('[data-form="directmsg"]');
  if(directForm) directForm.addEventListener('submit', async function(e){
    e.preventDefault();
    var fd = new FormData(directForm);
    await adminMessage(fd.get('username'), fd.get('text').trim());
    toast('বার্তা পাঠানো হয়েছে।'); directForm.reset();
  });

  app.querySelectorAll('[data-action="like"]').forEach(function(btn){
    btn.addEventListener('click', async function(){
      if(!SESSION){ toast('পছন্দ করতে লগইন করুন।'); return; }
      await toggleLike(btn.getAttribute('data-id')); render();
    });
  });
  app.querySelectorAll('[data-action="share-copy"]').forEach(function(btn){
    btn.addEventListener('click', async function(){
      var id = btn.getAttribute('data-id');
      var url = location.origin+location.pathname+'#/article/'+id;
      try{ await navigator.clipboard.writeText(url); }catch(e){}
      await bumpShare(id); toast('লিংক কপি করা হয়েছে।'); render();
    });
  });
  app.querySelectorAll('[data-action="share-fb"]').forEach(function(btn){
    btn.addEventListener('click', async function(){
      var id = btn.getAttribute('data-id');
      var url = location.origin+location.pathname+'#/article/'+id;
      window.open('https://www.facebook.com/sharer/sharer.php?u='+encodeURIComponent(url), '_blank');
      await bumpShare(id); render();
    });
  });
  app.querySelectorAll('[data-action="share-wa"]').forEach(function(btn){
    btn.addEventListener('click', async function(){
      var id = btn.getAttribute('data-id');
      var url = location.origin+location.pathname+'#/article/'+id;
      window.open('https://wa.me/?text='+encodeURIComponent(url), '_blank');
      await bumpShare(id); render();
    });
  });
  app.querySelectorAll('[data-action="delete-article"]').forEach(function(btn){
    btn.addEventListener('click', async function(){
      if(!confirm('আপনি কি নিশ্চিত এই সংবাদটি মুছে ফেলতে চান?')) return;
      await deleteArticle(btn.getAttribute('data-id'));
      toast('সংবাদটি মুছে ফেলা হয়েছে।');
      if(route().indexOf('article/')===0) location.hash='#/';
      render();
    });
  });

  app.querySelectorAll('[data-tab]').forEach(function(btn){
    btn.addEventListener('click', function(){ location.hash = '#/profile/'+btn.getAttribute('data-tab'); });
  });
  app.querySelectorAll('[data-admin-tab]').forEach(function(btn){
    btn.addEventListener('click', function(){ location.hash = '#/admin/'+btn.getAttribute('data-admin-tab'); });
  });
  app.querySelectorAll('[data-action="admin-ban"]').forEach(function(btn){
    btn.addEventListener('click', async function(){
      await adminSetBan(btn.getAttribute('data-user'), btn.getAttribute('data-val')==='true');
      toast('আপডেট সম্পন্ন হয়েছে।'); render();
    });
  });
  app.querySelectorAll('[data-action="admin-role"]').forEach(function(btn){
    btn.addEventListener('click', async function(){
      await adminSetRole(btn.getAttribute('data-user'), btn.getAttribute('data-val'));
      toast('ভূমিকা পরিবর্তন হয়েছে।'); render();
    });
  });
  app.querySelectorAll('[data-action="admin-delete-user"]').forEach(function(btn){
    btn.addEventListener('click', async function(){
      if(!confirm('আপনি কি নিশ্চিত এই ব্যবহারকারীকে মুছে ফেলতে চান? তার সকল সংবাদও মুছে যাবে।')) return;
      await adminDeleteUser(btn.getAttribute('data-user'));
      toast('ব্যবহারকারী মুছে ফেলা হয়েছে।'); render();
    });
  });
  app.querySelectorAll('[data-action="complaint-status"]').forEach(function(btn){
    btn.addEventListener('click', async function(){
      await adminSetComplaintStatus(btn.getAttribute('data-id'), btn.getAttribute('data-val'));
      toast('অভিযোগের অবস্থা হালনাগাদ হয়েছে।'); render();
    });
  });
  app.querySelectorAll('[data-action="complaint-delete"]').forEach(function(btn){
    btn.addEventListener('click', async function(){
      if(!confirm('আপনি কি নিশ্চিত এই অভিযোগটি মুছে ফেলতে চান?')) return;
      await adminDeleteComplaint(btn.getAttribute('data-id'));
      toast('অভিযোগ মুছে ফেলা হয়েছে।'); render();
    });
  });
  var themeBtn = app.querySelector('[data-action="toggle-theme"]');
  if(themeBtn) themeBtn.addEventListener('click', function(){
    SESSION_THEME = SESSION_THEME==='dark' ? 'light' : 'dark';
    document.documentElement.setAttribute('data-theme', SESSION_THEME);
    render();
  });
}

window.addEventListener('hashchange', render);
initData().then(render);
})();
</script>
</body>
</html># fast-news
