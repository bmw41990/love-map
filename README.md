# love-map
Love Map Trivia app

[index.html](https://github.com/user-attachments/files/26448510/index.html)
[index.html](https://github.com/user-attachments/files/26448510/index.html)
[Uploading<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover" />
  <title>Love Map</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;1,300;1,400&family=DM+Sans:opsz,wght@9..40,300;9..40,400;9..40,500&display=swap" rel="stylesheet">
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    :root {
      --rose: #C4747A; --rose-light: #F9EEEE; --rose-mid: #E8C4C4; --rose-dark: #8B4A50;
      --ink: #231E1C; --ink-soft: #6B5B58; --ink-faint: #A89490;
      --cream: #FAF8F5; --cream-2: #F2EDE8; --cream-3: #E8E0D8; --white: #FFFFFF;
      --green: #3A7D5C; --green-light: #EBF4EE;
      --gold: #A07840; --gold-light: #FBF4E8;
      --serif: 'Cormorant Garamond', Georgia, serif;
      --sans: 'DM Sans', system-ui, sans-serif;
      --r: 18px; --rsm: 12px;
      --shadow: 0 2px 16px rgba(35,30,28,0.08);
    }
    html { height: 100%; }
    body { font-family: var(--sans); background: var(--cream); color: var(--ink); min-height: 100%; font-size: 15px; line-height: 1.6; -webkit-font-smoothing: antialiased; }
    #app { min-height: 100vh; }
    .shell { display:flex; flex-direction:column; align-items:center; min-height:100vh; padding:0 16px calc(72px + env(safe-area-inset-bottom)); }
    .topbar { width:100%; max-width:500px; display:flex; justify-content:space-between; align-items:center; padding:22px 0 18px; }
    .wordmark { font-family:var(--serif); font-size:24px; font-weight:400; letter-spacing:0.01em; color:var(--ink); user-select:none; }
    .wordmark em { color:var(--rose); font-style:italic; }
    .page { width:100%; max-width:500px; }
    .card { background:var(--white); border:1px solid var(--cream-3); border-radius:var(--r); padding:24px 22px; margin-bottom:14px; box-shadow:var(--shadow); }
    .serif-lg { font-family:var(--serif); font-size:26px; font-weight:300; line-height:1.3; }
    .serif-md { font-family:var(--serif); font-size:20px; font-weight:300; line-height:1.3; }
    .serif-sm { font-family:var(--serif); font-size:17px; font-weight:300; }
    .label { font-size:11px; font-weight:500; text-transform:uppercase; letter-spacing:0.09em; color:var(--ink-faint); }
    .muted { font-size:13px; color:var(--ink-soft); line-height:1.5; }
    .field { margin-bottom:14px; }
    .field label { display:block; margin-bottom:5px; }
    input[type="text"], input[type="email"], input[type="password"], textarea {
      width:100%; padding:12px 14px; font-family:var(--sans); font-size:15px; color:var(--ink);
      background:var(--cream); border:1.5px solid var(--cream-3); border-radius:var(--rsm);
      outline:none; transition:border-color .15s,background .15s; -webkit-appearance:none;
    }
    input:focus, textarea:focus { border-color:var(--rose); background:var(--white); }
    textarea { resize:vertical; min-height:90px; line-height:1.6; }
    .btn { display:inline-flex; align-items:center; justify-content:center; gap:7px; padding:13px 20px; border-radius:var(--rsm); font-family:var(--sans); font-size:14px; font-weight:500; cursor:pointer; border:none; transition:all .15s; width:100%; letter-spacing:0.01em; }
    .btn-primary { background:var(--rose); color:white; }
    .btn-primary:hover:not(:disabled) { background:var(--rose-dark); }
    .btn-primary:disabled { opacity:.45; cursor:not-allowed; }
    .btn-ghost { background:transparent; color:var(--ink-soft); border:1.5px solid var(--cream-3); }
    .btn-ghost:hover:not(:disabled) { background:var(--cream-2); }
    .btn-danger { background:transparent; color:#A03030; border:1.5px solid rgba(160,48,48,.2); }
    .btn-danger:hover { background:#FEF0F0; }
    .btn-gold { background:var(--gold-light); color:var(--gold); border:1.5px solid rgba(160,120,64,.2); }
    .btn-gold:hover { background:#F5EAD4; }
    .mt-3 { margin-top:12px; } .mt-4 { margin-top:16px; }
    .auth-hero { text-align:center; padding:50px 0 32px; }
    .heart-mark { font-size:52px; line-height:1; margin-bottom:18px; display:block; color:var(--rose); }
    .auth-hero h1 { font-family:var(--serif); font-size:42px; font-weight:300; line-height:1.15; margin-bottom:12px; }
    .auth-hero h1 em { font-style:italic; color:var(--rose); }
    .tabs { display:flex; gap:5px; background:var(--cream-2); padding:4px; border-radius:var(--rsm); margin-bottom:22px; }
    .tab { flex:1; padding:9px; border-radius:9px; font-family:var(--sans); font-size:14px; font-weight:500; cursor:pointer; border:none; background:transparent; color:var(--ink-soft); transition:all .15s; }
    .tab.active { background:white; color:var(--ink); box-shadow:0 1px 4px rgba(0,0,0,.08); }
    .pill { display:inline-block; padding:4px 13px; background:var(--rose-light); color:var(--rose-dark); border-radius:100px; font-size:12px; font-weight:500; margin-bottom:14px; }
    .pill-gold { background:var(--gold-light); color:var(--gold); }
    .date-badge { font-size:12px; font-weight:500; text-transform:uppercase; letter-spacing:0.09em; color:var(--rose); margin-bottom:14px; }
    .q-num { font-size:11px; font-weight:500; text-transform:uppercase; letter-spacing:0.09em; color:var(--ink-faint); margin-bottom:6px; }
    .banner-green { display:flex; align-items:center; gap:9px; padding:11px 14px; background:var(--green-light); border-radius:var(--rsm); font-size:13px; color:var(--green); margin-bottom:16px; border:1px solid rgba(58,125,92,.15); }
    .banner-rose { display:flex; align-items:center; gap:9px; padding:11px 14px; background:var(--rose-light); border-radius:var(--rsm); font-size:13px; color:var(--rose-dark); margin-top:12px; border:1px solid var(--rose-mid); }
    .ans-grid { display:grid; grid-template-columns:1fr 1fr; gap:11px; margin-top:16px; }
    .ans-card { background:var(--cream); border:1px solid var(--cream-3); border-radius:var(--rsm); padding:13px; }
    .ans-who { font-size:11px; font-weight:500; text-transform:uppercase; letter-spacing:.08em; color:var(--ink-faint); margin-bottom:5px; }
    .ans-text { font-size:14px; color:var(--ink); line-height:1.55; }
    .ans-pending { font-size:14px; color:var(--ink-faint); font-style:italic; }
    .dots { display:flex; gap:4px; align-items:center; }
    .dots span { width:5px; height:5px; border-radius:50%; background:var(--rose); animation:pulse 1.4s ease-in-out infinite; }
    .dots span:nth-child(2){animation-delay:.2s} .dots span:nth-child(3){animation-delay:.4s}
    @keyframes pulse{0%,80%,100%{opacity:.3;transform:scale(.8)}40%{opacity:1;transform:scale(1)}}
    .nav { position:fixed; bottom:0; left:0; right:0; background:rgba(255,255,255,.96); backdrop-filter:blur(12px); -webkit-backdrop-filter:blur(12px); border-top:1px solid var(--cream-3); display:flex; justify-content:space-around; padding:8px 0; padding-bottom:max(8px,env(safe-area-inset-bottom)); z-index:100; }
    .nav-item { display:flex; flex-direction:column; align-items:center; gap:3px; padding:5px 16px; cursor:pointer; border:none; background:transparent; color:var(--ink-faint); font-family:var(--sans); font-size:10px; font-weight:500; transition:color .15s; letter-spacing:.04em; text-transform:uppercase; }
    .nav-item.active { color:var(--rose); }
    .nav-icon { font-size:20px; line-height:1; margin-bottom:1px; }
    .avatar { border-radius:50%; background:var(--rose-light); color:var(--rose-dark); display:flex; align-items:center; justify-content:center; font-family:var(--serif); font-weight:400; flex-shrink:0; }
    .avatar-sm { width:38px; height:38px; font-size:18px; }
    .avatar-lg { width:72px; height:72px; font-size:30px; margin:0 auto 12px; }
    .avatar-blue { background:#EAF0FD; color:#2B5098; }
    .hist-item { background:white; border:1px solid var(--cream-3); border-radius:var(--rsm); padding:16px 18px; margin-bottom:10px; cursor:pointer; transition:border-color .15s,box-shadow .15s; box-shadow:var(--shadow); }
    .hist-item:hover { border-color:var(--rose-mid); box-shadow:0 4px 20px rgba(196,116,122,.12); }
    .invite-code { font-family:'Courier New',monospace; font-size:30px; letter-spacing:0.2em; font-weight:600; text-align:center; padding:16px; background:var(--cream); border-radius:var(--rsm); border:1.5px dashed var(--rose-mid); color:var(--ink); margin:14px 0; user-select:all; }
    .stat-grid { display:grid; grid-template-columns:1fr 1fr; gap:10px; }
    .stat-card { background:var(--cream); border-radius:var(--rsm); padding:14px; text-align:center; }
    .stat-num { font-family:var(--serif); font-size:30px; font-weight:300; color:var(--rose); line-height:1; margin-bottom:4px; }
    .divider { height:1px; background:var(--cream-2); margin:18px 0; }
    .err { font-size:13px; color:#A03030; margin-top:7px; padding:9px 13px; background:#FEF0F0; border-radius:9px; }
    .text-center { text-align:center; }
    .loading { display:flex; flex-direction:column; align-items:center; justify-content:center; min-height:100vh; gap:16px; color:var(--ink-soft); }
    .spinner { width:30px; height:30px; border:2.5px solid var(--rose-light); border-top-color:var(--rose); border-radius:50%; animation:spin .8s linear infinite; }
    @keyframes spin{to{transform:rotate(360deg)}}
    .fade-in { animation:fadeIn .3s ease; }
    @keyframes fadeIn{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:translateY(0)}}
    .center-icon { font-size:52px; text-align:center; margin-bottom:16px; }
    .q-divider { display:flex; align-items:center; gap:10px; margin:22px 0 18px; }
    .q-divider::before, .q-divider::after { content:''; flex:1; height:1px; background:var(--cream-3); }
    .q-divider span { font-size:11px; font-weight:500; text-transform:uppercase; letter-spacing:.09em; color:var(--ink-faint); white-space:nowrap; }
    .quote-card { border:1px solid var(--rose-mid); border-radius:var(--r); padding:22px 24px 20px; margin-bottom:14px; text-align:center; position:relative; overflow:hidden; background:#FEFAF8; }
    .quote-bg { font-family:var(--serif); font-size:120px; line-height:.6; color:var(--rose-mid); position:absolute; top:10px; left:12px; user-select:none; pointer-events:none; opacity:.5; }
    .quote-text { font-family:var(--serif); font-size:18px; font-weight:300; font-style:italic; color:var(--ink); line-height:1.55; margin-bottom:12px; position:relative; z-index:1; padding:0 4px; }
    .quote-author { font-size:11px; font-weight:500; text-transform:uppercase; letter-spacing:.09em; color:var(--rose-dark); }
    .admin-badge { display:inline-block; padding:3px 10px; background:var(--gold-light); color:var(--gold); border-radius:100px; font-size:11px; font-weight:500; letter-spacing:.06em; text-transform:uppercase; margin-bottom:14px; border:1px solid rgba(160,120,64,.2); }
    .user-row { display:flex; align-items:center; justify-content:space-between; padding:13px 0; border-bottom:1px solid var(--cream-2); }
    .user-row:last-child { border-bottom:none; }
    .user-name { font-weight:500; font-size:14px; }
    .user-email { font-size:12px; color:var(--ink-soft); margin-top:1px; }
    .btn-sm { padding:7px 13px; font-size:12px; width:auto; }
    .modal-bg { position:fixed; inset:0; background:rgba(35,30,28,.5); display:flex; align-items:flex-end; justify-content:center; z-index:200; }
    .modal-sheet { background:white; border-radius:20px 20px 0 0; padding:28px 24px; padding-bottom:max(28px,env(safe-area-inset-bottom)); width:100%; max-width:500px; animation:slideUp .25s ease; }
    @keyframes slideUp{from{transform:translateY(100%)}to{transform:translateY(0)}}
    .modal-handle { width:36px; height:4px; border-radius:2px; background:var(--cream-3); margin:0 auto 20px; }
  </style>
</head>
<body>
<div id="app"><div class="loading"><div class="spinner"></div><span>Loading…</span></div></div>

<script type="module">
import { initializeApp } from 'https://www.gstatic.com/firebasejs/10.12.0/firebase-app.js';
import { getAuth, createUserWithEmailAndPassword, signInWithEmailAndPassword, signOut, onAuthStateChanged, updateProfile } from 'https://www.gstatic.com/firebasejs/10.12.0/firebase-auth.js';
import { getFirestore, doc, setDoc, getDoc, getDocs, updateDoc, onSnapshot, collection, deleteDoc } from 'https://www.gstatic.com/firebasejs/10.12.0/firebase-firestore.js';

const firebaseConfig = {
  apiKey: "AIzaSyCZD44GtU9xyqdFp_X37TZ9SuLCQKjTHZ8",
  authDomain: "love-map-trivia.firebaseapp.com",
  projectId: "love-map-trivia",
  storageBucket: "love-map-trivia.firebasestorage.app",
  messagingSenderId: "50697985872",
  appId: "1:50697985872:web:e2721b7dae4274f31f1655"
};

const fireApp = initializeApp(firebaseConfig);
const auth = getAuth(fireApp);
const db = getFirestore(fireApp);

// ── Set your admin UID here after first login (see Profile tab for your UID) ─
const ADMIN_UID = 'REPLACE_WITH_YOUR_UID';

// ── Questions ─────────────────────────────────────────────────────────────
const QUESTIONS = [
  {id:1,text:"What's one small thing I do that makes your day a little better?",cat:"Daily Love"},
  {id:2,text:"What's a childhood memory that still makes you smile?",cat:"Origins"},
  {id:3,text:"If we could live anywhere in the world for a year, where would you choose?",cat:"Dreams"},
  {id:4,text:"What's something you've always wanted to learn but haven't yet?",cat:"Growth"},
  {id:5,text:"Describe our perfect lazy Sunday in detail.",cat:"Daily Love"},
  {id:6,text:"What's a fear you've never fully told me about?",cat:"Depth"},
  {id:7,text:"What does home mean to you?",cat:"Values"},
  {id:8,text:"What's one thing you wish you could go back and tell your teenage self?",cat:"Origins"},
  {id:9,text:"What's something you're most proud of that you rarely talk about?",cat:"Depth"},
  {id:10,text:"If you could have dinner with any three people, living or dead, who would you pick?",cat:"Dreams"},
  {id:11,text:"What's a tradition from your family you'd love to carry forward?",cat:"Values"},
  {id:12,text:"What's the bravest thing you've ever done?",cat:"Depth"},
  {id:13,text:"What song instantly transports you back to a specific moment in your life?",cat:"Origins"},
  {id:14,text:"What's something I do that surprises you, even after all this time?",cat:"Us"},
  {id:15,text:"What does a truly fulfilling career look like to you?",cat:"Growth"},
  {id:16,text:"What's a place you've visited that left a mark on you?",cat:"Dreams"},
  {id:17,text:"How do you most like to be comforted when you're having a hard day?",cat:"Daily Love"},
  {id:18,text:"What's something on your bucket list that feels almost impossible?",cat:"Dreams"},
  {id:19,text:"What quality in yourself are you still working on?",cat:"Growth"},
  {id:20,text:"When did you first realize you were in love with me?",cat:"Us"},
  {id:21,text:"What's a book, film, or song that changed how you see the world?",cat:"Origins"},
  {id:22,text:"What's something you need more of in your life right now?",cat:"Growth"},
  {id:23,text:"What does a perfect morning look like for you?",cat:"Daily Love"},
  {id:24,text:"What's the kindest thing a stranger has ever done for you?",cat:"Values"},
  {id:25,text:"What's something you secretly find hilarious about me?",cat:"Us"},
  {id:26,text:"If money were no object, how would you spend your time?",cat:"Dreams"},
  {id:27,text:"What does friendship mean to you?",cat:"Values"},
  {id:28,text:"What's a lesson failure taught you that you're grateful for?",cat:"Growth"},
  {id:29,text:"What's one ritual or habit of ours you never want to give up?",cat:"Us"},
  {id:30,text:"What's something you're looking forward to in the next year?",cat:"Dreams"},
  {id:31,text:"What's your favorite thing about the season we're in right now?",cat:"Daily Love"},
  {id:32,text:"What's a hobby you dropped that you secretly miss?",cat:"Growth"},
  {id:33,text:"Describe a moment when you felt completely at peace.",cat:"Depth"},
  {id:34,text:"What's something small you do every day that brings you joy?",cat:"Daily Love"},
  {id:35,text:"What's your earliest memory of us?",cat:"Us"},
  {id:36,text:"What's a quality you admire in me that you wish you had more of yourself?",cat:"Us"},
  {id:37,text:"If you could relive one day of your life, which would you choose?",cat:"Origins"},
  {id:38,text:"What does love look like in action to you?",cat:"Values"},
  {id:39,text:"What's something you've changed your mind about in the last few years?",cat:"Growth"},
  {id:40,text:"What's the most meaningful gift you've ever received?",cat:"Depth"},
  {id:41,text:"What's something you find beautiful that most people overlook?",cat:"Depth"},
  {id:42,text:"How do you want to be remembered?",cat:"Values"},
  {id:43,text:"What's a dream you've let go of that you still think about?",cat:"Dreams"},
  {id:44,text:"What's one thing you'd tell our future selves?",cat:"Us"},
  {id:45,text:"What's something about yourself that took you a long time to accept?",cat:"Growth"},
];

const QUOTES = [
  {text:"The best thing to hold onto in life is each other.",author:"Audrey Hepburn"},
  {text:"A great relationship is about two things: appreciating the similarities, and respecting the differences.",author:"Unknown"},
  {text:"Being deeply loved by someone gives you strength, while loving someone deeply gives you courage.",author:"Lao Tzu"},
  {text:"A happy marriage is a long conversation which always seems too short.",author:"André Maurois"},
  {text:"The real act of marriage takes place in the heart, not in the ballroom or church.",author:"Barbara De Angelis"},
  {text:"In all the world, there is no heart for me like yours.",author:"Maya Angelou"},
  {text:"Love is an act of endless forgiveness, a tender look which becomes a habit.",author:"Peter Ustinov"},
  {text:"A successful marriage requires falling in love many times, always with the same person.",author:"Mignon McLaughlin"},
  {text:"To be fully seen by somebody, and be loved anyhow — this is a human offering that can border on miraculous.",author:"Elizabeth Gilbert"},
  {text:"Love doesn't make the world go 'round. Love is what makes the ride worthwhile.",author:"Franklin P. Jones"},
  {text:"Whatever our souls are made of, his and mine are the same.",author:"Emily Brontë"},
  {text:"The most important thing in the world is family and love.",author:"John Wooden"},
  {text:"We loved with a love that was more than love.",author:"Edgar Allan Poe"},
  {text:"You don't love someone for their looks or their clothes or their car. You love them because they sing a song only you can hear.",author:"Oscar Wilde"},
  {text:"Love is not about how many days, months, or years you have been together. It's how much you love each other every single day.",author:"Unknown"},
];

// ── Helpers ───────────────────────────────────────────────────────────────
function todayStr() {
  const d=new Date();
  return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`;
}
function formatDate(str) {
  const [y,m,d]=str.split('-').map(Number);
  return new Date(y,m-1,d).toLocaleDateString('en-US',{weekday:'long',month:'long',day:'numeric'});
}
function getDayQuestions(dateStr, seed) {
  const base = dateStr.replace(/-/g,'') + String(seed||0);
  function hash(extra) {
    const s=base+extra; let h=0;
    for(let i=0;i<s.length;i++){h=((h<<5)-h)+s.charCodeAt(i);h|=0;}
    return Math.abs(h);
  }
  const i1=hash('q1')%QUESTIONS.length;
  let i2=hash('q2')%QUESTIONS.length; if(i2===i1) i2=(i2+1)%QUESTIONS.length;
  let i3=hash('q3')%QUESTIONS.length; if(i3===i1||i3===i2) i3=(i3+2)%QUESTIONS.length;
  return [QUESTIONS[i1],QUESTIONS[i2],QUESTIONS[i3]];
}
function getDailyQuote(dateStr) {
  let h=0; for(let i=0;i<dateStr.length;i++){h=((h<<5)-h)+dateStr.charCodeAt(i);h|=0;}
  return QUOTES[Math.abs(h)%QUOTES.length];
}
function genCode() {
  const c='ABCDEFGHJKLMNPQRSTUVWXYZ23456789';
  return Array.from({length:6},()=>c[Math.floor(Math.random()*c.length)]).join('');
}
function el(tag,props={},...children) {
  const e=document.createElement(tag);
  for(const [k,v] of Object.entries(props)){
    if(k==='class')e.className=v;
    else if(k==='style')Object.assign(e.style,v);
    else if(k.startsWith('on'))e.addEventListener(k.slice(2).toLowerCase(),v);
    else e.setAttribute(k,v);
  }
  for(const c of children.flat()){if(c==null)continue;e.append(typeof c==='string'?document.createTextNode(c):c);}
  return e;
}
function div(cls,...children){return el('div',{class:cls},...children);}
function h(tag,cls,text){const e=document.createElement(tag);e.className=cls;e.textContent=text;return e;}

// ── State ─────────────────────────────────────────────────────────────────
let currentUser=null, currentTab='today', unsubPair=null;

function render(content){const root=document.getElementById('app');root.innerHTML='';root.appendChild(content);}
function renderLoading(){render(div('loading',div('spinner'),el('span',{},'Loading…')));}

// ── Auth ──────────────────────────────────────────────────────────────────
function renderAuth(mode='login'){
  const wrap=div('shell'); wrap.style.paddingBottom='40px';
  wrap.appendChild(div('topbar',el('span',{class:'wordmark'},'love ',el('em',{},'map'))));
  const page=div('page fade-in');
  const hero=div('auth-hero');
  hero.innerHTML=`<span class="heart-mark">♡</span><h1>Know each<br/><em>other deeper.</em></h1>`;
  const sub=document.createElement('p'); sub.className='muted'; sub.style.cssText='max-width:280px;margin:0 auto';
  sub.textContent='A daily ritual of questions for you and your person.';
  hero.appendChild(sub); page.appendChild(hero);
  const card=div('card');
  const tabs=div('tabs');
  const t1=el('button',{class:`tab ${mode==='login'?'active':''}`},'Sign in');
  const t2=el('button',{class:`tab ${mode==='register'?'active':''}`},'Create account');
  t1.onclick=()=>renderAuth('login'); t2.onclick=()=>renderAuth('register');
  tabs.append(t1,t2); card.appendChild(tabs);
  const errEl=div('err'); errEl.style.display='none';
  const form={};
  function field(lText,type,ph,key){
    const f=div('field'),lbl=el('label',{class:'label'},lText),inp=el('input',{type,placeholder:ph});
    f.append(lbl,inp); card.appendChild(f); form[key]=inp;
  }
  if(mode==='register') field('Your name','text','First name','name');
  field('Email','email','you@example.com','email');
  field('Password','password',mode==='register'?'At least 6 characters':'Your password','password');
  if(mode==='register'){
    const f=div('field'); const lbl=el('label',{class:'label'},'Partner invite code ');
    lbl.appendChild(el('span',{style:{fontWeight:'300',textTransform:'none',letterSpacing:'0'}},'(optional)'));
    const inp=el('input',{type:'text',placeholder:'e.g. XK9RMJ',maxlength:'6',style:{letterSpacing:'0.12em',textTransform:'uppercase'}});
    inp.oninput=()=>{inp.value=inp.value.toUpperCase();}; f.append(lbl,inp); card.appendChild(f); form.invite=inp;
  }
  card.appendChild(errEl);
  const btn=el('button',{class:'btn btn-primary',style:{marginTop:'14px'}},mode==='login'?'Sign in':'Create account');

  async function doLogin(){
    errEl.style.display='none'; btn.disabled=true; btn.textContent='Please wait…';
    try{ await signInWithEmailAndPassword(auth,form.email.value.trim(),form.password.value); }
    catch(e){
      let msg='Something went wrong. Try again.';
      if(e.code==='auth/user-not-found'||e.code==='auth/invalid-credential') msg='No account found, or wrong password.';
      else if(e.code==='auth/wrong-password') msg='Incorrect password.';
      else if(e.code==='auth/invalid-email') msg='Please enter a valid email.';
      errEl.textContent=msg; errEl.style.display='block'; btn.disabled=false; btn.textContent='Sign in';
    }
  }
  async function doRegister(){
    errEl.style.display='none';
    const email=form.email.value.trim(),pass=form.password.value,name=form.name.value.trim();
    const invite=(form.invite?.value||'').trim().toUpperCase();
    if(!name){errEl.textContent='Please enter your name.';errEl.style.display='block';return;}
    if(pass.length<6){errEl.textContent='Password must be at least 6 characters.';errEl.style.display='block';return;}
    btn.disabled=true; btn.textContent='Please wait…';
    try{
      let pairData=null;
      if(invite){
        const ps=await getDoc(doc(db,'pairs',invite));
        if(!ps.exists()){errEl.textContent='Invite code not found.';errEl.style.display='block';btn.disabled=false;btn.textContent='Create account';return;}
        pairData=ps.data();
        if(pairData.user2Id){errEl.textContent='This invite code has already been used.';errEl.style.display='block';btn.disabled=false;btn.textContent='Create account';return;}
      }
      const cred=await createUserWithEmailAndPassword(auth,email,pass);
      await updateProfile(cred.user,{displayName:name});
      await setDoc(doc(db,'users',cred.user.uid),{name,email,pairCode:invite||null,uid:cred.user.uid});
      if(invite&&pairData) await updateDoc(doc(db,'pairs',invite),{user2Id:cred.user.uid,user2Name:name,user2Email:email});
    }catch(e){
      let msg='Something went wrong. Try again.';
      if(e.code==='auth/email-already-in-use') msg='An account with this email already exists.';
      else if(e.code==='auth/invalid-email') msg='Please enter a valid email.';
      errEl.textContent=msg; errEl.style.display='block'; btn.disabled=false; btn.textContent='Create account';
    }
  }
  btn.onclick=mode==='login'?doLogin:doRegister;
  form.password&&(form.password.onkeydown=e=>{if(e.key==='Enter')btn.click();});
  card.appendChild(btn); page.appendChild(card); wrap.appendChild(page); render(wrap);
}

// ── Shell ─────────────────────────────────────────────────────────────────
function renderShell(user,userData){
  const wrap=div('shell');
  const topbar=div('topbar');
  topbar.appendChild(el('span',{class:'wordmark'},'love ',el('em',{},'map')));
  const av=div('avatar avatar-sm'); av.textContent=(userData?.name||user.displayName||'?')[0].toUpperCase();
  topbar.appendChild(av); wrap.appendChild(topbar);
  const page=div('page'); wrap.appendChild(page);
  const nav=div('nav');
  const isAdmin=user.uid===ADMIN_UID;
  const navItems=[
    {id:'today',icon:'♡',label:'Today'},
    {id:'history',icon:'◷',label:'History'},
    {id:'profile',icon:'◎',label:'Profile'},
    ...(isAdmin?[{id:'admin',icon:'⚙',label:'Admin'}]:[]),
  ];
  navItems.forEach(n=>{
    const btn=el('button',{class:`nav-item ${currentTab===n.id?'active':''}`});
    btn.innerHTML=`<span class="nav-icon">${n.icon}</span>${n.label}`;
    btn.onclick=()=>{currentTab=n.id;renderShell(user,userData);};
    nav.appendChild(btn);
  });
  document.getElementById('app').innerHTML='';
  document.getElementById('app').append(wrap,nav);
  if(currentTab==='today') renderToday(page,user,userData);
  if(currentTab==='history') renderHistory(page,user,userData);
  if(currentTab==='profile') renderProfile(page,user,userData);
  if(currentTab==='admin'&&isAdmin) renderAdmin(page,user,userData);
}

// ── Quote card ────────────────────────────────────────────────────────────
function makeQuoteCard(){
  const q=getDailyQuote(todayStr());
  const card=div('quote-card');
  card.innerHTML=`<div class="quote-bg">"</div>
    <div class="quote-text">${q.text}</div>
    <div class="quote-author">— ${q.author}</div>`;
  return card;
}

// ── Question block ────────────────────────────────────────────────────────
function buildQuestionBlock(container, {qNum,q,myAnswer,partnerAnswer,partnerName,entryRef,user,isBonus}){
  const numEl=h('div','q-num',isBonus?'✦ Bonus question':`Question ${qNum} of 2`);
  const pill=el('span',{class:`pill${isBonus?' pill-gold':''}`},q.cat);
  const qEl=h('div','serif-lg',q.text); qEl.style.marginBottom='18px';
  container.append(numEl,pill,qEl);

  if(!myAnswer){
    const lbl=h('label','label','Your answer');
    const ta=el('textarea',{placeholder:'Write your honest answer…',rows:'3'});
    const hint=el('p',{class:'muted',style:{fontSize:'12px',textAlign:'center',marginTop:'8px'}},"Your partner won't see this until they answer too.");
    const submitBtn=el('button',{class:`btn ${isBonus?'btn-gold':'btn-primary'}`,style:{marginTop:'12px'}},'Submit answer');
    submitBtn.disabled=true;
    ta.oninput=()=>{submitBtn.disabled=!ta.value.trim();};
    submitBtn.onclick=async()=>{
      if(!ta.value.trim()) return;
      submitBtn.disabled=true; submitBtn.textContent='Saving…';
      const freshSnap=await getDoc(entryRef);
      const freshData=freshSnap.exists()?freshSnap.data():{};
      if(isBonus){
        if(!freshData.bonusAnswers) freshData.bonusAnswers={};
        freshData.bonusAnswers[user.uid]=ta.value.trim();
      } else {
        if(!freshData[`answers${qNum}`]) freshData[`answers${qNum}`]={};
        freshData[`answers${qNum}`][user.uid]=ta.value.trim();
        freshData[`qId${qNum}`]=q.id;
      }
      await setDoc(entryRef,freshData,{merge:true});
    };
    container.append(lbl,ta,submitBtn,hint);
  } else if(!partnerAnswer){
    const waiting=div('banner-rose');
    waiting.append(div('dots',el('span'),el('span'),el('span')),el('span',{},'Waiting for ',el('strong',{},partnerName||'your partner'),' to answer…'));
    const grid=div('ans-grid');
    grid.append(
      Object.assign(div('ans-card'),{innerHTML:`<div class="ans-who">You</div><div class="ans-text">${myAnswer}</div>`}),
      Object.assign(div('ans-card'),{innerHTML:`<div class="ans-who">${partnerName||'Partner'}</div><div class="ans-pending">Not yet answered</div>`})
    );
    container.append(waiting,grid);
  } else {
    const revealed=div('banner-green');
    revealed.innerHTML='<span>✦</span><span><strong>Both answers revealed!</strong></span>';
    const grid=div('ans-grid');
    grid.append(
      Object.assign(div('ans-card'),{innerHTML:`<div class="ans-who">You</div><div class="ans-text">${myAnswer}</div>`}),
      Object.assign(div('ans-card'),{innerHTML:`<div class="ans-who">${partnerName||'Partner'}</div><div class="ans-text">${partnerAnswer}</div>`})
    );
    container.append(revealed,grid);
  }
}

// ── Today Tab ─────────────────────────────────────────────────────────────
async function renderToday(page,user,userData){
  page.innerHTML=''; page.appendChild(div('loading',div('spinner')));
  if(!userData?.pairCode){page.innerHTML='';renderNoPair(page,user,userData);return;}
  const pairSnap=await getDoc(doc(db,'pairs',userData.pairCode));
  if(!pairSnap.exists()){page.innerHTML='';renderNoPair(page,user,userData);return;}
  const pairData=pairSnap.data();
  const isUser1=pairData.user1Id===user.uid;
  const partnerName=isUser1?pairData.user2Name:pairData.user1Name;
  const partnerId=isUser1?pairData.user2Id:pairData.user1Id;
  const today=todayStr();
  const [q1,q2,q3]=getDayQuestions(today,pairData.seed);
  if(unsubPair) unsubPair();
  const entryRef=doc(db,'pairs',userData.pairCode,'history',today);

  unsubPair=onSnapshot(entryRef,snap=>{
    const entry=snap.exists()?snap.data():null;
    const myA1=entry?.answers1?.[user.uid], pA1=partnerId?entry?.answers1?.[partnerId]:null;
    const myA2=entry?.answers2?.[user.uid], pA2=partnerId?entry?.answers2?.[partnerId]:null;
    const myAB=entry?.bonusAnswers?.[user.uid], pAB=partnerId?entry?.bonusAnswers?.[partnerId]:null;
    const both1=!!(myA1&&pA1), both2=!!(myA2&&pA2), bothMain=both1&&both2;
    const bonusUnlocked=!!(entry?.bonusQId||entry?.bonusAnswers);

    page.innerHTML='';

    if(partnerName){
      const banner=div('banner-green');
      banner.innerHTML=`<span>♡</span><span>Connected with <strong>${partnerName}</strong></span>`;
      page.appendChild(banner);
    }

    const card=div('card fade-in');
    card.appendChild(h('div','date-badge',formatDate(today)));

    // Q1
    buildQuestionBlock(card,{qNum:1,q:q1,myAnswer:myA1,partnerAnswer:pA1,partnerName,entryRef,user,isBonus:false});

    // Q2 separator + block
    const sep2=div('q-divider'); sep2.appendChild(el('span',{},'Question 2')); card.appendChild(sep2);
    buildQuestionBlock(card,{qNum:2,q:q2,myAnswer:myA2,partnerAnswer:pA2,partnerName,entryRef,user,isBonus:false});

    // Bonus — only after both main questions fully revealed
    if(bothMain){
      const sepB=div('q-divider'); sepB.appendChild(el('span',{},'Bonus')); card.appendChild(sepB);
      if(!bonusUnlocked){
        const hint=h('p','muted',"You've both finished today's questions. Want to go deeper?");
        hint.style.cssText='text-align:center;font-size:13px;margin-bottom:12px';
        const bonusBtn=el('button',{class:'btn btn-gold'},'✦ Unlock a bonus question');
        bonusBtn.onclick=async()=>{ await setDoc(entryRef,{bonusQId:q3.id},{merge:true}); };
        card.append(hint,bonusBtn);
      } else {
        buildQuestionBlock(card,{qNum:null,q:q3,myAnswer:myAB,partnerAnswer:pAB,partnerName,entryRef,user,isBonus:true});
      }
    }

    page.appendChild(card);
    // Daily quote below the question card
    page.appendChild(makeQuoteCard());
  });
}

// ── No Pair ───────────────────────────────────────────────────────────────
function renderNoPair(page,user,userData){
  function showMain(){
    page.innerHTML='';
    const card=div('card fade-in text-center'); card.style.cssText='padding-top:32px;padding-bottom:32px';
    const icon=div('center-icon'); icon.textContent='♡';
    const title=h('div','serif-md','Connect with your partner'); title.style.marginBottom='8px';
    const sub=h('p','muted','Link accounts to start answering daily questions together.'); sub.style.marginBottom='22px';
    const btn1=el('button',{class:'btn btn-primary'},'Create a pair & invite partner');
    const sep=el('p',{class:'muted',style:{margin:'10px 0'}},'or');
    const btn2=el('button',{class:'btn btn-ghost'},"Enter partner's invite code");
    btn1.onclick=showCreate; btn2.onclick=showJoin;
    card.append(icon,title,sub,btn1,sep,btn2); page.appendChild(card);
  }
  async function showCreate(){
    page.innerHTML='';
    const card=div('card fade-in');
    const title=h('div','serif-md','Create a pair');
    const sub=h('p','muted',"You'll get a 6-character code to share with your partner."); sub.style.marginBottom='16px';
    const btn=el('button',{class:'btn btn-primary'},'Generate invite code');
    const back=el('button',{class:'btn btn-ghost mt-3'},'Back'); back.onclick=showMain;
    card.append(title,sub,btn,back); page.appendChild(card);
    btn.onclick=async()=>{
      btn.disabled=true; btn.textContent='Creating…';
      const code=genCode(),seed=Math.floor(Math.random()*9999);
      await setDoc(doc(db,'pairs',code),{code,seed,user1Id:user.uid,user1Name:userData.name,user1Email:userData.email,user2Id:null,user2Name:null,user2Email:null,createdAt:Date.now()});
      await updateDoc(doc(db,'users',user.uid),{pairCode:code});
      userData.pairCode=code; showInvite(code);
    };
  }
  function showInvite(code){
    page.innerHTML='';
    const card=div('card fade-in');
    const title=h('div','serif-md','Invite your partner ♡');
    const sub=h('p','muted','Share this code. Works on any device, anywhere.'); sub.style.marginBottom='4px';
    const codeEl=div('invite-code'); codeEl.textContent=code;
    const copyBtn=el('button',{class:'btn btn-ghost'},'Copy code');
    copyBtn.onclick=()=>{navigator.clipboard.writeText(code).then(()=>{copyBtn.textContent='✓ Copied!';setTimeout(()=>copyBtn.textContent='Copy code',2000);});};
    const note=h('p','muted','Once your partner joins, the Today tab updates automatically.');
    note.style.cssText='margin-top:12px;text-align:center;font-size:12px';
    card.append(title,sub,codeEl,copyBtn,note); page.appendChild(card);
  }
  async function showJoin(){
    page.innerHTML='';
    const card=div('card fade-in');
    const title=h('div','serif-md','Join with a code');
    const sub=h('p','muted','Enter the 6-character code your partner created.'); sub.style.marginBottom='16px';
    const lbl=h('label','label','Invite code');
    const inp=el('input',{type:'text',placeholder:'XXXXXX',maxlength:'6',style:{letterSpacing:'0.15em',textTransform:'uppercase',fontSize:'20px',textAlign:'center'}});
    inp.oninput=()=>{inp.value=inp.value.toUpperCase();joinBtn.disabled=inp.value.length<6;};
    const errEl=div('err'); errEl.style.display='none';
    const joinBtn=el('button',{class:'btn btn-primary',style:{marginTop:'4px'}},'Join pair'); joinBtn.disabled=true;
    const back=el('button',{class:'btn btn-ghost mt-3'},'Back'); back.onclick=showMain;
    card.append(title,sub,lbl,inp,errEl,joinBtn,back); page.appendChild(card);
    joinBtn.onclick=async()=>{
      errEl.style.display='none';
      const code=inp.value.trim().toUpperCase(); joinBtn.disabled=true; joinBtn.textContent='Joining…';
      const ps=await getDoc(doc(db,'pairs',code));
      if(!ps.exists()){errEl.textContent='Code not found. Check and try again.';errEl.style.display='block';joinBtn.disabled=false;joinBtn.textContent='Join pair';return;}
      const pd=ps.data();
      if(pd.user2Id){errEl.textContent='This code has already been used.';errEl.style.display='block';joinBtn.disabled=false;joinBtn.textContent='Join pair';return;}
      if(pd.user1Id===user.uid){errEl.textContent="That's your own code!";errEl.style.display='block';joinBtn.disabled=false;joinBtn.textContent='Join pair';return;}
      await updateDoc(doc(db,'pairs',code),{user2Id:user.uid,user2Name:userData.name,user2Email:userData.email});
      await updateDoc(doc(db,'users',user.uid),{pairCode:code});
      userData.pairCode=code; currentTab='today'; renderShell(user,userData);
    };
  }
  showMain();
}

// ── History Tab ───────────────────────────────────────────────────────────
async function renderHistory(page,user,userData){
  page.innerHTML=''; page.appendChild(div('loading',div('spinner')));
  if(!userData?.pairCode){
    page.innerHTML='';
    page.appendChild(Object.assign(div('card text-center'),{innerHTML:'<p class="muted">Connect with a partner to see your history.</p>'}));
    return;
  }
  const pairSnap=await getDoc(doc(db,'pairs',userData.pairCode));
  if(!pairSnap.exists()){page.innerHTML='No pair data.';return;}
  const pd=pairSnap.data();
  const isUser1=pd.user1Id===user.uid;
  const partnerName=isUser1?pd.user2Name:pd.user1Name;
  const partnerId=isUser1?pd.user2Id:pd.user1Id;
  const histSnap=await getDocs(collection(db,'pairs',userData.pairCode,'history'));
  page.innerHTML='';
  if(histSnap.empty){
    page.appendChild(Object.assign(div('card text-center'),{innerHTML:"<p class='muted'>No history yet — answer today's questions to get started!</p>"}));
    return;
  }
  const dates=histSnap.docs.sort((a,b)=>b.id.localeCompare(a.id));
  const badge=h('div','date-badge',`${dates.length} ${dates.length===1?'day':'days'} together`);
  badge.style.marginBottom='14px'; page.appendChild(badge);
  dates.forEach(snap=>{
    const entry=snap.data();
    const [q1,q2,q3]=getDayQuestions(snap.id,pd.seed);
    const both1=entry.answers1?.[user.uid]&&partnerId&&entry.answers1?.[partnerId];
    const both2=entry.answers2?.[user.uid]&&partnerId&&entry.answers2?.[partnerId];
    const hasBonus=!!(entry.bonusAnswers?.[user.uid]&&partnerId&&entry.bonusAnswers?.[partnerId]);
    const item=div('hist-item');
    item.innerHTML=`
      <div style="font-size:11px;text-transform:uppercase;letter-spacing:.07em;color:var(--ink-faint);margin-bottom:3px">${formatDate(snap.id)}</div>
      <div class="serif-sm" style="margin-bottom:4px">${q1.text}</div>
      <div class="muted" style="font-size:12px">${(both1&&both2)?'✦ Both answered':'Incomplete'}${hasBonus?' · +bonus':''}</div>
    `;
    item.onclick=()=>renderHistDetail(page,snap.id,entry,q1,q2,q3,user,partnerId,partnerName,userData);
    page.appendChild(item);
  });
}

function renderHistDetail(page,dateStr,entry,q1,q2,q3,user,partnerId,partnerName,userData){
  page.innerHTML='';
  const back=el('button',{class:'btn btn-ghost',style:{width:'auto',marginBottom:'14px'}},'← Back');
  back.onclick=()=>renderHistory(page,user,userData); page.appendChild(back);
  const card=div('card fade-in');
  card.innerHTML=`<div class="date-badge">${formatDate(dateStr)}</div>`;
  function showQ(num,q,isBonus){
    const aKey=isBonus?'bonusAnswers':`answers${num}`;
    const myA=entry[aKey]?.[user.uid], pA=partnerId?entry[aKey]?.[partnerId]:null;
    const numEl=h('div','q-num',isBonus?'✦ Bonus question':`Question ${num} of 2`);
    const pill=el('span',{class:`pill${isBonus?' pill-gold':''}`},q.cat);
    const qEl=h('div','serif-lg',q.text); qEl.style.marginBottom='14px';
    card.append(numEl,pill,qEl);
    if(myA&&pA){
      const grid=div('ans-grid');
      grid.append(
        Object.assign(div('ans-card'),{innerHTML:`<div class="ans-who">You</div><div class="ans-text">${myA}</div>`}),
        Object.assign(div('ans-card'),{innerHTML:`<div class="ans-who">${partnerName||'Partner'}</div><div class="ans-text">${pA}</div>`})
      );
      card.appendChild(grid);
    } else {
      card.appendChild(Object.assign(el('p',{class:'muted'}),{textContent:"Both answers weren't submitted for this question."}));
    }
  }
  showQ(1,q1,false);
  const sep=div('q-divider'); sep.appendChild(el('span',{},'Question 2')); card.appendChild(sep);
  showQ(2,q2,false);
  if(entry.bonusAnswers||entry.bonusQId){
    const sepB=div('q-divider'); sepB.appendChild(el('span',{},'Bonus')); card.appendChild(sepB);
    showQ(null,q3,true);
  }
  page.appendChild(card);
}

// ── Profile Tab ───────────────────────────────────────────────────────────
async function renderProfile(page,user,userData){
  page.innerHTML=''; page.appendChild(div('loading',div('spinner')));
  let pairData=null,totalDays=0,bothDays=0,partnerName=null,partnerEmail=null,partnerId=null;
  if(userData?.pairCode){
    const pSnap=await getDoc(doc(db,'pairs',userData.pairCode));
    if(pSnap.exists()){
      pairData=pSnap.data();
      const isUser1=pairData.user1Id===user.uid;
      partnerName=isUser1?pairData.user2Name:pairData.user1Name;
      partnerEmail=isUser1?pairData.user2Email:pairData.user1Email;
      partnerId=isUser1?pairData.user2Id:pairData.user1Id;
      const histDocs=await getDocs(collection(db,'pairs',userData.pairCode,'history'));
      totalDays=histDocs.size;
      bothDays=histDocs.docs.filter(s=>{
        const e=s.data();
        return e.answers1?.[user.uid]&&partnerId&&e.answers1?.[partnerId]&&e.answers2?.[user.uid]&&e.answers2?.[partnerId];
      }).length;
    }
  }
  page.innerHTML='';
  const userCard=div('card fade-in text-center'); userCard.style.paddingTop='28px';
  const av=div('avatar avatar-lg'); av.textContent=(userData?.name||'?')[0].toUpperCase();
  const nm=h('div','serif-lg',userData?.name||''); nm.style.marginBottom='4px';
  const emailEl=h('p','muted',userData?.email||'');

  // Show UID hint for admin setup
  const uidEl=h('p','muted',`UID: ${user.uid}`);
  uidEl.style.cssText='font-size:10px;font-family:monospace;margin-top:6px;color:var(--ink-faint);word-break:break-all';
  userCard.append(av,nm,emailEl,uidEl); page.appendChild(userCard);

  if(pairData&&partnerName){
    const pCard=div('card');
    const pt=h('div','serif-sm','Your partner'); pt.style.marginBottom='14px';
    const prow=div(''); prow.style.cssText='display:flex;align-items:center;gap:12px;margin-bottom:16px';
    const pav=div('avatar avatar-sm avatar-blue'); pav.textContent=partnerName[0].toUpperCase();
    const pinfo=div(''); pinfo.innerHTML=`<div style="font-weight:500">${partnerName}</div><div class="muted">${partnerEmail||''}</div>`;
    prow.append(pav,pinfo);
    const stats=div('stat-grid');
    [{n:totalDays,l:'days active'},{n:bothDays,l:'both answered'}].forEach(({n,l})=>{
      const s=div('stat-card'); s.innerHTML=`<div class="stat-num">${n}</div><div class="label" style="font-size:11px">${l}</div>`;
      stats.appendChild(s);
    });
    pCard.append(pt,prow,stats); page.appendChild(pCard);
  }
  if(pairData&&!partnerName&&userData.pairCode){
    const iCard=div('card');
    iCard.innerHTML=`<div class="serif-sm" style="margin-bottom:6px">Invite your partner</div><p class="muted" style="margin-bottom:4px">Share this code — works on any device.</p>`;
    const codeEl=div('invite-code'); codeEl.textContent=userData.pairCode;
    const copyBtn=el('button',{class:'btn btn-ghost'},'Copy code');
    copyBtn.onclick=()=>{navigator.clipboard.writeText(userData.pairCode).then(()=>{copyBtn.textContent='✓ Copied!';setTimeout(()=>copyBtn.textContent='Copy code',2000);});};
    iCard.append(codeEl,copyBtn); page.appendChild(iCard);
  }
  const soCard=div('card');
  const soBtn=el('button',{class:'btn btn-danger'},'Sign out');
  soBtn.onclick=async()=>{if(unsubPair){unsubPair();unsubPair=null;}await signOut(auth);};
  soCard.appendChild(soBtn); page.appendChild(soCard);
}

// ── Admin Panel ───────────────────────────────────────────────────────────
async function renderAdmin(page,user,userData){
  page.innerHTML=''; page.appendChild(div('loading',div('spinner')));
  const usersSnap=await getDocs(collection(db,'users'));
  page.innerHTML='';
  const card=div('card fade-in');
  const badge=div('admin-badge'); badge.textContent='⚙ Admin';
  const title=h('div','serif-md','User management'); title.style.marginBottom='4px';
  const count=h('p','muted',`${usersSnap.size} account${usersSnap.size===1?'':'s'} registered`); count.style.marginBottom='18px';
  card.append(badge,title,count);
  const list=div('');
  let hasOthers=false;
  usersSnap.forEach(snap=>{
    const u=snap.data();
    if(u.uid===user.uid) return;
    hasOthers=true;
    const row=div('user-row');
    const info=div('');
    info.innerHTML=`<div class="user-name">${u.name||'Unknown'}</div><div class="user-email">${u.email||''}</div>`;
    const delBtn=el('button',{class:'btn btn-danger btn-sm'},'Delete');
    delBtn.onclick=()=>confirmDelete(u,()=>renderAdmin(page,user,userData));
    row.append(info,delBtn); list.appendChild(row);
  });
  if(!hasOthers){
    const empty=h('p','muted','No other accounts yet.'); empty.style.textAlign='center';
    list.appendChild(empty);
  }
  card.appendChild(list); page.appendChild(card);
}

function confirmDelete(targetUser,onDone){
  const overlay=div('modal-bg');
  const sheet=div('modal-sheet');
  sheet.innerHTML=`<div class="modal-handle"></div>
    <div class="serif-md" style="margin-bottom:8px">Delete account?</div>
    <p class="muted" style="margin-bottom:20px">This will permanently remove <strong>${targetUser.name}</strong>'s account data from Firestore. This cannot be undone.</p>`;
  const confirmBtn=el('button',{class:'btn btn-danger'},'Yes, delete account');
  const cancelBtn=el('button',{class:'btn btn-ghost mt-3'},'Cancel');
  cancelBtn.onclick=()=>overlay.remove();
  confirmBtn.onclick=async()=>{
    confirmBtn.disabled=true; confirmBtn.textContent='Deleting…';
    try{
      await deleteDoc(doc(db,'users',targetUser.uid));
      if(targetUser.pairCode){
        const pSnap=await getDoc(doc(db,'pairs',targetUser.pairCode));
        if(pSnap.exists()){
          const pd=pSnap.data();
          const updates={};
          if(pd.user1Id===targetUser.uid){updates.user1Id=null;updates.user1Name=null;updates.user1Email=null;}
          if(pd.user2Id===targetUser.uid){updates.user2Id=null;updates.user2Name=null;updates.user2Email=null;}
          if(Object.keys(updates).length) await updateDoc(doc(db,'pairs',targetUser.pairCode),updates);
        }
      }
      overlay.remove(); onDone();
    }catch(e){
      confirmBtn.disabled=false; confirmBtn.textContent='Yes, delete account';
      alert('Error: '+e.message);
    }
  };
  sheet.append(confirmBtn,cancelBtn); overlay.appendChild(sheet);
  overlay.onclick=e=>{if(e.target===overlay)overlay.remove();};
  document.body.appendChild(overlay);
}

// ── Auth listener ──────────────────────────────────────────────────────────
onAuthStateChanged(auth,async(user)=>{
  if(unsubPair){unsubPair();unsubPair=null;}
  if(!user){renderAuth('login');return;}
  renderLoading();
  const snap=await getDoc(doc(db,'users',user.uid));
  const userData=snap.exists()?snap.data():{name:user.displayName||'',email:user.email,pairCode:null};
  currentTab='today';
  renderShell(user,userData);
});
</script>
</body>
</html>
 index.html…]()
