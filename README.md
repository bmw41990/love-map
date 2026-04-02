# love-map
Love Map Trivia app
[index.html](https://github.com/user-attachments/files/26447927/index.html)
<!DOCTYPE html>
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
      --rose: #C4747A;
      --rose-light: #F9EEEE;
      --rose-mid: #E8C4C4;
      --rose-dark: #8B4A50;
      --ink: #231E1C;
      --ink-soft: #6B5B58;
      --ink-faint: #A89490;
      --cream: #FAF8F5;
      --cream-2: #F2EDE8;
      --cream-3: #E8E0D8;
      --white: #FFFFFF;
      --green: #3A7D5C;
      --green-light: #EBF4EE;
      --serif: 'Cormorant Garamond', Georgia, serif;
      --sans: 'DM Sans', system-ui, sans-serif;
      --r: 18px;
      --rsm: 12px;
      --shadow: 0 2px 16px rgba(35,30,28,0.08);
    }

    html { height: 100%; }
    body {
      font-family: var(--sans);
      background: var(--cream);
      color: var(--ink);
      min-height: 100%;
      font-size: 15px;
      line-height: 1.6;
      -webkit-font-smoothing: antialiased;
    }

    #app { min-height: 100vh; }

    /* ── Shell ── */
    .shell {
      display: flex;
      flex-direction: column;
      align-items: center;
      min-height: 100vh;
      padding: 0 16px calc(72px + env(safe-area-inset-bottom));
    }

    .topbar {
      width: 100%;
      max-width: 500px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 22px 0 18px;
    }

    .wordmark {
      font-family: var(--serif);
      font-size: 24px;
      font-weight: 400;
      letter-spacing: 0.01em;
      color: var(--ink);
      user-select: none;
    }
    .wordmark em { color: var(--rose); font-style: italic; }

    .page { width: 100%; max-width: 500px; }

    /* ── Cards ── */
    .card {
      background: var(--white);
      border: 1px solid var(--cream-3);
      border-radius: var(--r);
      padding: 24px 22px;
      margin-bottom: 14px;
      box-shadow: var(--shadow);
    }

    /* ── Typography ── */
    .serif-lg { font-family: var(--serif); font-size: 26px; font-weight: 300; line-height: 1.3; }
    .serif-md { font-family: var(--serif); font-size: 20px; font-weight: 300; line-height: 1.3; }
    .serif-sm { font-family: var(--serif); font-size: 17px; font-weight: 300; }
    .label { font-size: 11px; font-weight: 500; text-transform: uppercase; letter-spacing: 0.09em; color: var(--ink-faint); }
    .muted { font-size: 13px; color: var(--ink-soft); line-height: 1.5; }

    /* ── Inputs ── */
    .field { margin-bottom: 14px; }
    .field label { display: block; margin-bottom: 5px; }

    input[type="text"], input[type="email"], input[type="password"], textarea {
      width: 100%;
      padding: 12px 14px;
      font-family: var(--sans);
      font-size: 15px;
      color: var(--ink);
      background: var(--cream);
      border: 1.5px solid var(--cream-3);
      border-radius: var(--rsm);
      outline: none;
      transition: border-color 0.15s, background 0.15s;
      -webkit-appearance: none;
    }
    input:focus, textarea:focus { border-color: var(--rose); background: var(--white); }
    textarea { resize: vertical; min-height: 90px; line-height: 1.6; }

    /* ── Buttons ── */
    .btn {
      display: inline-flex; align-items: center; justify-content: center; gap: 7px;
      padding: 13px 20px; border-radius: var(--rsm);
      font-family: var(--sans); font-size: 14px; font-weight: 500;
      cursor: pointer; border: none; transition: all 0.15s;
      width: 100%; letter-spacing: 0.01em;
    }
    .btn-primary { background: var(--rose); color: white; }
    .btn-primary:hover:not(:disabled) { background: var(--rose-dark); }
    .btn-primary:disabled { opacity: 0.45; cursor: not-allowed; }
    .btn-ghost { background: transparent; color: var(--ink-soft); border: 1.5px solid var(--cream-3); }
    .btn-ghost:hover:not(:disabled) { background: var(--cream-2); border-color: var(--cream-3); }
    .btn-danger { background: transparent; color: #A03030; border: 1.5px solid rgba(160,48,48,0.2); }
    .btn-danger:hover { background: #FEF0F0; }
    .mt-3 { margin-top: 12px; }
    .mt-4 { margin-top: 16px; }

    /* ── Auth ── */
    .auth-hero {
      text-align: center;
      padding: 50px 0 32px;
    }
    .heart-mark {
      font-size: 52px;
      line-height: 1;
      margin-bottom: 18px;
      display: block;
      color: var(--rose);
    }
    .auth-hero h1 {
      font-family: var(--serif);
      font-size: 42px;
      font-weight: 300;
      line-height: 1.15;
      margin-bottom: 12px;
    }
    .auth-hero h1 em { font-style: italic; color: var(--rose); }

    .tabs {
      display: flex; gap: 5px;
      background: var(--cream-2); padding: 4px; border-radius: var(--rsm);
      margin-bottom: 22px;
    }
    .tab {
      flex: 1; padding: 9px; border-radius: 9px;
      font-family: var(--sans); font-size: 14px; font-weight: 500;
      cursor: pointer; border: none; background: transparent;
      color: var(--ink-soft); transition: all 0.15s;
    }
    .tab.active { background: white; color: var(--ink); box-shadow: 0 1px 4px rgba(0,0,0,0.08); }

    /* ── Category pill ── */
    .pill {
      display: inline-block; padding: 4px 13px;
      background: var(--rose-light); color: var(--rose-dark);
      border-radius: 100px; font-size: 12px; font-weight: 500;
      margin-bottom: 14px;
    }

    /* ── Date badge ── */
    .date-badge { font-size: 12px; font-weight: 500; text-transform: uppercase; letter-spacing: 0.09em; color: var(--rose); margin-bottom: 8px; }

    /* ── Banners ── */
    .banner-green {
      display: flex; align-items: center; gap: 9px;
      padding: 11px 14px; background: var(--green-light);
      border-radius: var(--rsm); font-size: 13px; color: var(--green);
      margin-bottom: 16px; border: 1px solid rgba(58,125,92,0.15);
    }
    .banner-rose {
      display: flex; align-items: center; gap: 9px;
      padding: 11px 14px; background: var(--rose-light);
      border-radius: var(--rsm); font-size: 13px; color: var(--rose-dark);
      margin-top: 12px; border: 1px solid var(--rose-mid);
    }

    /* ── Answer grid ── */
    .ans-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 11px; margin-top: 16px; }
    .ans-card { background: var(--cream); border: 1px solid var(--cream-3); border-radius: var(--rsm); padding: 13px; }
    .ans-who { font-size: 11px; font-weight: 500; text-transform: uppercase; letter-spacing: 0.08em; color: var(--ink-faint); margin-bottom: 5px; }
    .ans-text { font-size: 14px; color: var(--ink); line-height: 1.55; }
    .ans-pending { font-size: 14px; color: var(--ink-faint); font-style: italic; }

    /* ── Pulse dots ── */
    .dots { display: flex; gap: 4px; align-items: center; }
    .dots span { width: 5px; height: 5px; border-radius: 50%; background: var(--rose); animation: pulse 1.4s ease-in-out infinite; }
    .dots span:nth-child(2) { animation-delay: .2s; }
    .dots span:nth-child(3) { animation-delay: .4s; }
    @keyframes pulse { 0%,80%,100%{opacity:.3;transform:scale(.8)} 40%{opacity:1;transform:scale(1)} }

    /* ── Bottom nav ── */
    .nav {
      position: fixed; bottom: 0; left: 0; right: 0;
      background: rgba(255,255,255,0.96);
      backdrop-filter: blur(12px);
      -webkit-backdrop-filter: blur(12px);
      border-top: 1px solid var(--cream-3);
      display: flex; justify-content: space-around;
      padding: 8px 0;
      padding-bottom: max(8px, env(safe-area-inset-bottom));
      z-index: 100;
    }
    .nav-item {
      display: flex; flex-direction: column; align-items: center; gap: 3px;
      padding: 5px 22px; cursor: pointer; border: none; background: transparent;
      color: var(--ink-faint); font-family: var(--sans); font-size: 10px; font-weight: 500;
      transition: color 0.15s; letter-spacing: 0.04em; text-transform: uppercase;
    }
    .nav-item.active { color: var(--rose); }
    .nav-icon { font-size: 20px; line-height: 1; margin-bottom: 1px; }

    /* ── Avatar ── */
    .avatar {
      border-radius: 50%;
      background: var(--rose-light); color: var(--rose-dark);
      display: flex; align-items: center; justify-content: center;
      font-family: var(--serif); font-weight: 400; flex-shrink: 0;
    }
    .avatar-sm { width: 38px; height: 38px; font-size: 18px; }
    .avatar-lg { width: 72px; height: 72px; font-size: 30px; margin: 0 auto 12px; }
    .avatar-blue { background: #EAF0FD; color: #2B5098; }

    /* ── History items ── */
    .hist-item {
      background: white; border: 1px solid var(--cream-3); border-radius: var(--rsm);
      padding: 16px 18px; margin-bottom: 10px; cursor: pointer;
      transition: border-color 0.15s, box-shadow 0.15s; box-shadow: var(--shadow);
    }
    .hist-item:hover { border-color: var(--rose-mid); box-shadow: 0 4px 20px rgba(196,116,122,0.12); }

    /* ── Invite code ── */
    .invite-code {
      font-family: 'Courier New', monospace;
      font-size: 30px; letter-spacing: 0.2em; font-weight: 600;
      text-align: center; padding: 16px; background: var(--cream);
      border-radius: var(--rsm); border: 1.5px dashed var(--rose-mid);
      color: var(--ink); margin: 14px 0; user-select: all;
    }

    /* ── Stats ── */
    .stat-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
    .stat-card { background: var(--cream); border-radius: var(--rsm); padding: 14px; text-align: center; }
    .stat-num { font-family: var(--serif); font-size: 30px; font-weight: 300; color: var(--rose); line-height: 1; margin-bottom: 4px; }

    /* ── Misc ── */
    .divider { height: 1px; background: var(--cream-2); margin: 18px 0; }
    .err { font-size: 13px; color: #A03030; margin-top: 7px; padding: 9px 13px; background: #FEF0F0; border-radius: 9px; }
    .success { font-size: 13px; color: var(--green); padding: 9px 13px; background: var(--green-light); border-radius: 9px; margin-top: 7px; }
    .text-center { text-align: center; }
    .streak { display: flex; align-items: center; gap: 8px; font-size: 13px; color: var(--ink-soft); margin-bottom: 14px; }
    .streak-n { font-family: var(--serif); font-size: 24px; color: var(--rose); line-height: 1; }

    /* ── Loading ── */
    .loading {
      display: flex; flex-direction: column; align-items: center;
      justify-content: center; min-height: 100vh; gap: 16px; color: var(--ink-soft);
    }
    .spinner {
      width: 30px; height: 30px;
      border: 2.5px solid var(--rose-light); border-top-color: var(--rose);
      border-radius: 50%; animation: spin 0.8s linear infinite;
    }
    @keyframes spin { to { transform: rotate(360deg); } }

    /* ── Fade in ── */
    .fade-in { animation: fadeIn 0.3s ease; }
    @keyframes fadeIn { from { opacity: 0; transform: translateY(6px); } to { opacity: 1; transform: translateY(0); } }

    /* ── No pair center ── */
    .center-icon { font-size: 52px; text-align: center; margin-bottom: 16px; }
  </style>
</head>
<body>
<div id="app">
  <div class="loading"><div class="spinner"></div><span>Loading…</span></div>
</div>

<!-- Firebase -->
<script type="module">
import { initializeApp } from 'https://www.gstatic.com/firebasejs/10.12.0/firebase-app.js';
import { getAuth, createUserWithEmailAndPassword, signInWithEmailAndPassword, signOut, onAuthStateChanged, updateProfile } from 'https://www.gstatic.com/firebasejs/10.12.0/firebase-auth.js';
import { getFirestore, doc, setDoc, getDoc, updateDoc, onSnapshot, collection, query, orderBy } from 'https://www.gstatic.com/firebasejs/10.12.0/firebase-firestore.js';

// ── Firebase init ──────────────────────────────────────────────────────────
const firebaseConfig = {
  apiKey: "AIzaSyCZD44GtU9xyqdFp_X37TZ9SuLCQKjTHZ8",
  authDomain: "love-map-trivia.firebaseapp.com",
  projectId: "love-map-trivia",
  storageBucket: "love-map-trivia.firebasestorage.app",
  messagingSenderId: "50697985872",
  appId: "1:50697985872:web:e2721b7dae4274f31f1655"
};

const app = initializeApp(firebaseConfig);
const auth = getAuth(app);
const db = getFirestore(app);

// ── Questions ──────────────────────────────────────────────────────────────
const QUESTIONS = [
  { id:1, text:"What's one small thing I do that makes your day a little better?", cat:"Daily Love" },
  { id:2, text:"What's a childhood memory that still makes you smile?", cat:"Origins" },
  { id:3, text:"If we could live anywhere in the world for a year, where would you choose?", cat:"Dreams" },
  { id:4, text:"What's something you've always wanted to learn but haven't yet?", cat:"Growth" },
  { id:5, text:"Describe our perfect lazy Sunday in detail.", cat:"Daily Love" },
  { id:6, text:"What's a fear you've never fully told me about?", cat:"Depth" },
  { id:7, text:"What does home mean to you?", cat:"Values" },
  { id:8, text:"What's one thing you wish you could go back and tell your teenage self?", cat:"Origins" },
  { id:9, text:"What's something you're most proud of that you rarely talk about?", cat:"Depth" },
  { id:10, text:"If you could have dinner with any three people, living or dead, who would you pick?", cat:"Dreams" },
  { id:11, text:"What's a tradition from your family you'd love to carry forward?", cat:"Values" },
  { id:12, text:"What's the bravest thing you've ever done?", cat:"Depth" },
  { id:13, text:"What song instantly transports you back to a specific moment in your life?", cat:"Origins" },
  { id:14, text:"What's something I do that surprises you, even after all this time?", cat:"Us" },
  { id:15, text:"What does a truly fulfilling career look like to you?", cat:"Growth" },
  { id:16, text:"What's a place you've visited that left a mark on you?", cat:"Dreams" },
  { id:17, text:"How do you most like to be comforted when you're having a hard day?", cat:"Daily Love" },
  { id:18, text:"What's something on your bucket list that feels almost impossible?", cat:"Dreams" },
  { id:19, text:"What quality in yourself are you still working on?", cat:"Growth" },
  { id:20, text:"When did you first realize you were in love with me?", cat:"Us" },
  { id:21, text:"What's a book, film, or song that changed how you see the world?", cat:"Origins" },
  { id:22, text:"What's something you need more of in your life right now?", cat:"Growth" },
  { id:23, text:"What does a perfect morning look like for you?", cat:"Daily Love" },
  { id:24, text:"What's the kindest thing a stranger has ever done for you?", cat:"Values" },
  { id:25, text:"What's something you secretly find hilarious about me?", cat:"Us" },
  { id:26, text:"If money were no object, how would you spend your time?", cat:"Dreams" },
  { id:27, text:"What does friendship mean to you?", cat:"Values" },
  { id:28, text:"What's a lesson failure taught you that you're grateful for?", cat:"Growth" },
  { id:29, text:"What's one ritual or habit of ours you never want to give up?", cat:"Us" },
  { id:30, text:"What's something you're looking forward to in the next year?", cat:"Dreams" },
  { id:31, text:"What's your favorite thing about the season we're in right now?", cat:"Daily Love" },
  { id:32, text:"What's a hobby you dropped that you secretly miss?", cat:"Growth" },
  { id:33, text:"Describe a moment when you felt completely at peace.", cat:"Depth" },
  { id:34, text:"What's something small you do every day that brings you joy?", cat:"Daily Love" },
  { id:35, text:"What's your earliest memory of us?", cat:"Us" },
];

// ── Helpers ────────────────────────────────────────────────────────────────
function todayStr() {
  const d = new Date();
  return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`;
}
function formatDate(str) {
  const [y,m,d] = str.split('-').map(Number);
  return new Date(y,m-1,d).toLocaleDateString('en-US',{weekday:'long',month:'long',day:'numeric'});
}
function getDayQuestion(dateStr, seed) {
  const s = dateStr.replace(/-/g,'') + String(seed||0);
  let h = 0;
  for (let i=0; i<s.length; i++) { h = ((h<<5)-h) + s.charCodeAt(i); h|=0; }
  return QUESTIONS[Math.abs(h) % QUESTIONS.length];
}
function genCode() {
  const c = 'ABCDEFGHJKLMNPQRSTUVWXYZ23456789';
  return Array.from({length:6}, ()=>c[Math.floor(Math.random()*c.length)]).join('');
}
function el(tag, props={}, ...children) {
  const e = document.createElement(tag);
  for (const [k,v] of Object.entries(props)) {
    if (k === 'class') e.className = v;
    else if (k === 'style') Object.assign(e.style, v);
    else if (k.startsWith('on')) e.addEventListener(k.slice(2).toLowerCase(), v);
    else e.setAttribute(k, v);
  }
  for (const c of children.flat()) {
    if (c == null) continue;
    e.append(typeof c === 'string' ? document.createTextNode(c) : c);
  }
  return e;
}
function div(cls, ...children) { return el('div', {class:cls}, ...children); }
function h(tag, cls, text) { const e = document.createElement(tag); e.className=cls; e.textContent=text; return e; }

// ── State ──────────────────────────────────────────────────────────────────
let currentUser = null;
let currentTab = 'today';
let unsubPair = null;

// ── Render ─────────────────────────────────────────────────────────────────
function render(content, noNav=false) {
  const root = document.getElementById('app');
  root.innerHTML = '';
  root.appendChild(content);
}

function renderLoading() {
  render(div('loading', div('spinner'), el('span',{},'Loading…')));
}

// ── Auth Screen ────────────────────────────────────────────────────────────
function renderAuth(mode='login') {
  const wrap = div('shell');
  wrap.style.paddingBottom = '40px';
  const topbar = div('topbar', el('span',{class:'wordmark'},'love ', el('em',{},'map')));
  wrap.appendChild(topbar);

  const page = div('page fade-in');

  const hero = div('auth-hero');
  hero.innerHTML = `<span class="heart-mark">♡</span>
    <h1>Know each<br/><em>other deeper.</em></h1>`;
  const sub = document.createElement('p');
  sub.className = 'muted'; sub.style.maxWidth='280px'; sub.style.margin='0 auto';
  sub.textContent = 'A daily ritual of questions for you and your person.';
  hero.appendChild(sub);
  page.appendChild(hero);

  const card = div('card');

  // Tabs
  const tabs = div('tabs');
  const t1 = el('button',{class:`tab ${mode==='login'?'active':''}`},'Sign in');
  const t2 = el('button',{class:`tab ${mode==='register'?'active':''}`},'Create account');
  t1.onclick = () => renderAuth('login');
  t2.onclick = () => renderAuth('register');
  tabs.append(t1,t2);
  card.appendChild(tabs);

  const errEl = div('err'); errEl.style.display='none';
  const form = {};

  function field(labelText, type, placeholder, key, extra={}) {
    const f = div('field');
    const lbl = el('label',{class:'label'},labelText);
    const inp = el('input',{type, placeholder, ...extra});
    f.append(lbl,inp); card.appendChild(f);
    form[key] = inp;
  }

  if (mode==='register') field('Your name','text','First name','name');
  field('Email','email','you@example.com','email');
  field('Password','password', mode==='register'?'At least 6 characters':'Your password','password');
  if (mode==='register') {
    const f = div('field');
    const lbl = el('label',{class:'label'},'Partner invite code ');
    const note = el('span',{style:{fontWeight:'300',textTransform:'none',letterSpacing:'0'}},'(optional — add later)');
    lbl.appendChild(note);
    const inp = el('input',{type:'text',placeholder:'e.g. XK9RMJ',maxlength:'6',style:{letterSpacing:'0.12em',textTransform:'uppercase'}});
    inp.oninput = ()=>{ inp.value=inp.value.toUpperCase(); };
    f.append(lbl,inp); card.appendChild(f);
    form.invite = inp;
  }

  card.appendChild(errEl);

  const btn = el('button',{class:'btn btn-primary', style:{marginTop:'14px'}}, mode==='login'?'Sign in':'Create account');

  async function doLogin() {
    errEl.style.display='none';
    btn.disabled=true; btn.textContent='Please wait…';
    try {
      await signInWithEmailAndPassword(auth, form.email.value.trim(), form.password.value);
    } catch(e) {
      let msg = 'Something went wrong. Try again.';
      if (e.code==='auth/user-not-found'||e.code==='auth/invalid-credential') msg='No account found, or wrong password.';
      else if (e.code==='auth/wrong-password') msg='Incorrect password.';
      else if (e.code==='auth/invalid-email') msg='Please enter a valid email.';
      errEl.textContent=msg; errEl.style.display='block';
      btn.disabled=false; btn.textContent='Sign in';
    }
  }

  async function doRegister() {
    errEl.style.display='none';
    const email=form.email.value.trim(), pass=form.password.value, name=form.name.value.trim();
    const invite=(form.invite?.value||'').trim().toUpperCase();
    if (!name) { errEl.textContent='Please enter your name.'; errEl.style.display='block'; return; }
    if (pass.length<6) { errEl.textContent='Password must be at least 6 characters.'; errEl.style.display='block'; return; }
    btn.disabled=true; btn.textContent='Please wait…';

    try {
      // Check invite code first
      let pairData = null;
      if (invite) {
        const pairSnap = await getDoc(doc(db,'pairs',invite));
        if (!pairSnap.exists()) { errEl.textContent='Invite code not found. Check and try again.'; errEl.style.display='block'; btn.disabled=false; btn.textContent='Create account'; return; }
        pairData = pairSnap.data();
        if (pairData.user2Id) { errEl.textContent='This invite code has already been used.'; errEl.style.display='block'; btn.disabled=false; btn.textContent='Create account'; return; }
      }

      const cred = await createUserWithEmailAndPassword(auth, email, pass);
      await updateProfile(cred.user, {displayName: name});

      // Save user doc
      await setDoc(doc(db,'users',cred.user.uid), { name, email, pairCode: invite||null, uid: cred.user.uid });

      // Join pair if invite provided
      if (invite && pairData) {
        await updateDoc(doc(db,'pairs',invite), { user2Id: cred.user.uid, user2Name: name, user2Email: email });
      }
    } catch(e) {
      let msg = 'Something went wrong. Try again.';
      if (e.code==='auth/email-already-in-use') msg='An account with this email already exists.';
      else if (e.code==='auth/invalid-email') msg='Please enter a valid email.';
      errEl.textContent=msg; errEl.style.display='block';
      btn.disabled=false; btn.textContent='Create account';
    }
  }

  btn.onclick = mode==='login' ? doLogin : doRegister;
  form.password && (form.password.onkeydown = e => { if(e.key==='Enter') btn.click(); });
  card.appendChild(btn);
  page.appendChild(card);
  wrap.appendChild(page);
  render(wrap, true);
}

// ── Main Shell ─────────────────────────────────────────────────────────────
function renderShell(user, userData) {
  const wrap = div('shell');

  const topbar = div('topbar');
  topbar.appendChild(el('span',{class:'wordmark'},'love ',el('em',{},'map')));
  const av = div(`avatar avatar-sm`); av.textContent=(userData?.name||user.displayName||'?')[0].toUpperCase();
  topbar.appendChild(av);
  wrap.appendChild(topbar);

  const page = div('page');
  wrap.appendChild(page);

  const nav = div('nav');
  const navItems = [
    {id:'today', icon:'♡', label:'Today'},
    {id:'history', icon:'◷', label:'History'},
    {id:'profile', icon:'◎', label:'Profile'},
  ];
  navItems.forEach(n => {
    const btn = el('button',{class:`nav-item ${currentTab===n.id?'active':''}`});
    btn.innerHTML=`<span class="nav-icon">${n.icon}</span>${n.label}`;
    btn.onclick = () => { currentTab=n.id; renderShell(user,userData); };
    nav.appendChild(btn);
  });

  document.getElementById('app').innerHTML='';
  document.getElementById('app').append(wrap, nav);

  if (currentTab==='today') renderToday(page, user, userData);
  if (currentTab==='history') renderHistory(page, user, userData);
  if (currentTab==='profile') renderProfile(page, user, userData);
}

// ── Today Tab ──────────────────────────────────────────────────────────────
async function renderToday(page, user, userData) {
  page.innerHTML='';
  page.appendChild(div('loading', div('spinner')));

  if (!userData?.pairCode) {
    page.innerHTML='';
    renderNoPair(page, user, userData);
    return;
  }

  const pairSnap = await getDoc(doc(db,'pairs',userData.pairCode));
  if (!pairSnap.exists()) {
    page.innerHTML='';
    renderNoPair(page, user, userData);
    return;
  }

  const pairData = pairSnap.data();
  const isUser1 = pairData.user1Id === user.uid;
  const partnerName = isUser1 ? pairData.user2Name : pairData.user1Name;
  const partnerId = isUser1 ? pairData.user2Id : pairData.user1Id;

  const today = todayStr();
  const q = getDayQuestion(today, pairData.seed);

  // Live listener on today's entry
  if (unsubPair) unsubPair();
  const entryRef = doc(db,'pairs',userData.pairCode,'history',today);

  unsubPair = onSnapshot(entryRef, snap => {
    const entry = snap.exists() ? snap.data() : null;
    const myAnswer = entry?.answers?.[user.uid];
    const partnerAnswer = partnerId ? entry?.answers?.[partnerId] : null;
    const bothAnswered = !!(myAnswer && partnerAnswer);

    page.innerHTML='';
    const card = div('card fade-in');

    // Streak
    // (just show today's status — full streak would need extra reads)

    // Connected banner
    if (partnerName) {
      const banner = div('banner-green');
      banner.innerHTML=`<span>♡</span><span>Connected with <strong>${partnerName}</strong></span>`;
      card.appendChild(banner);
    }

    // Date + question
    const db2 = h('div','date-badge', formatDate(today));
    const pill = el('span',{class:'pill'}, q.cat);
    const qEl = h('div','serif-lg', q.text);
    qEl.style.marginBottom='18px';
    card.append(db2, pill, qEl);

    if (!myAnswer) {
      // Answer input
      const lbl = h('label','label','Your answer');
      const ta = el('textarea',{placeholder:'Write your honest answer…', rows:'3'});
      const hint = el('p',{class:'muted',style:{fontSize:'12px',textAlign:'center',marginTop:'8px'}},
        "Your partner won't see this until they answer too.");
      const submitBtn = el('button',{class:'btn btn-primary',style:{marginTop:'12px'}},'Submit answer');
      submitBtn.disabled = true;
      ta.oninput = () => { submitBtn.disabled = !ta.value.trim(); };
      submitBtn.onclick = async () => {
        if (!ta.value.trim()) return;
        submitBtn.disabled=true; submitBtn.textContent='Saving…';
        const freshSnap = await getDoc(entryRef);
        const freshData = freshSnap.exists() ? freshSnap.data() : { qId: q.id, answers: {} };
        freshData.answers = freshData.answers||{};
        freshData.answers[user.uid] = ta.value.trim();
        await setDoc(entryRef, freshData);
      };
      card.append(lbl, ta, submitBtn, hint);
    } else if (!bothAnswered) {
      // Waiting
      const waiting = div('banner-rose');
      const dots = div('dots', el('span'),el('span'),el('span'));
      const txt = el('span',{},'Waiting for ', el('strong',{},partnerName||'your partner'), ' to answer…');
      waiting.append(dots, txt);
      const grid = div('ans-grid');
      const myCard = div('ans-card', h('div','ans-who','You'), el('div',{class:'ans-text'},myAnswer));
      const pCard = div('ans-card', h('div','ans-who', partnerName||'Partner'), h('div','ans-pending','Not yet answered'));
      grid.append(myCard, pCard);
      card.append(waiting, grid);
    } else {
      // Both revealed
      const revealed = div('banner-green');
      revealed.innerHTML='<span>✦</span><span><strong>Both answers revealed!</strong></span>';
      const grid = div('ans-grid');
      const myCard = div('ans-card', h('div','ans-who','You'), el('div',{class:'ans-text'},myAnswer));
      const pCard = div('ans-card', h('div','ans-who',partnerName||'Partner'), el('div',{class:'ans-text'},partnerAnswer));
      grid.append(myCard, pCard);
      card.append(revealed, grid);
    }

    page.appendChild(card);
  });
}

// ── No Pair ────────────────────────────────────────────────────────────────
function renderNoPair(page, user, userData) {
  page.innerHTML='';

  function showMain() {
    page.innerHTML='';
    const card = div('card fade-in text-center');
    card.style.paddingTop='32px'; card.style.paddingBottom='32px';
    const icon = div('center-icon'); icon.textContent='♡';
    const title = h('div','serif-md','Connect with your partner');
    title.style.marginBottom='8px';
    const sub = h('p','muted','Link accounts to start answering daily questions together.');
    sub.style.marginBottom='22px';
    const btn1 = el('button',{class:'btn btn-primary'},'Create a pair & invite partner');
    const sep = el('p',{class:'muted',style:{margin:'10px 0'}},'or');
    const btn2 = el('button',{class:'btn btn-ghost'},'Enter partner\'s invite code');
    btn1.onclick = () => showCreate();
    btn2.onclick = () => showJoin();
    card.append(icon,title,sub,btn1,sep,btn2);
    page.appendChild(card);
  }

  async function showCreate() {
    page.innerHTML='';
    const card = div('card fade-in');
    const title = h('div','serif-md','Create a pair');
    const sub = h('p','muted','You\'ll get a 6-character code to share with your partner.');
    sub.style.marginBottom='16px';
    const btn = el('button',{class:'btn btn-primary'},'Generate invite code');
    const back = el('button',{class:'btn btn-ghost mt-3'},'Back');
    back.onclick = showMain;
    card.append(title, sub, btn, back);
    page.appendChild(card);

    btn.onclick = async () => {
      btn.disabled=true; btn.textContent='Creating…';
      const code = genCode();
      const seed = Math.floor(Math.random()*9999);
      await setDoc(doc(db,'pairs',code), {
        code, seed,
        user1Id: user.uid, user1Name: userData.name, user1Email: userData.email,
        user2Id: null, user2Name: null, user2Email: null,
        createdAt: Date.now()
      });
      await updateDoc(doc(db,'users',user.uid), { pairCode: code });
      userData.pairCode = code;
      showInvite(code);
    };
  }

  function showInvite(code) {
    page.innerHTML='';
    const card = div('card fade-in');
    const title = h('div','serif-md','Invite your partner ♡');
    const sub = h('p','muted','Share this code with your partner. They enter it when creating their account — works on any device, anywhere.');
    sub.style.marginBottom='4px';
    const codeEl = div('invite-code'); codeEl.textContent=code;
    const copyBtn = el('button',{class:'btn btn-ghost'},'Copy code');
    copyBtn.onclick = () => {
      navigator.clipboard.writeText(code).then(()=>{ copyBtn.textContent='✓ Copied!'; setTimeout(()=>copyBtn.textContent='Copy code',2000); });
    };
    const note = h('p','muted','Once your partner joins, refresh the Today tab to start answering together.');
    note.style.marginTop='12px'; note.style.textAlign='center'; note.style.fontSize='12px';
    card.append(title, sub, codeEl, copyBtn, note);
    page.appendChild(card);
  }

  async function showJoin() {
    page.innerHTML='';
    const card = div('card fade-in');
    const title = h('div','serif-md','Join with a code');
    const sub = h('p','muted','Enter the 6-character code your partner created.');
    sub.style.marginBottom='16px';
    const lbl = h('label','label','Invite code');
    const inp = el('input',{type:'text',placeholder:'XXXXXX',maxlength:'6',style:{letterSpacing:'0.15em',textTransform:'uppercase',fontSize:'20px',textAlign:'center'}});
    inp.oninput = ()=>{ inp.value=inp.value.toUpperCase(); joinBtn.disabled=inp.value.length<6; };
    const errEl = div('err'); errEl.style.display='none';
    const joinBtn = el('button',{class:'btn btn-primary',style:{marginTop:'4px'}},'Join pair');
    joinBtn.disabled=true;
    const back = el('button',{class:'btn btn-ghost mt-3'},'Back');
    back.onclick = showMain;
    card.append(title,sub,lbl,inp,errEl,joinBtn,back);
    page.appendChild(card);

    joinBtn.onclick = async () => {
      errEl.style.display='none';
      const code = inp.value.trim().toUpperCase();
      joinBtn.disabled=true; joinBtn.textContent='Joining…';
      const pairSnap = await getDoc(doc(db,'pairs',code));
      if (!pairSnap.exists()) { errEl.textContent='Code not found. Check and try again.'; errEl.style.display='block'; joinBtn.disabled=false; joinBtn.textContent='Join pair'; return; }
      const pd = pairSnap.data();
      if (pd.user2Id) { errEl.textContent='This code has already been used.'; errEl.style.display='block'; joinBtn.disabled=false; joinBtn.textContent='Join pair'; return; }
      if (pd.user1Id===user.uid) { errEl.textContent="That's your own code!"; errEl.style.display='block'; joinBtn.disabled=false; joinBtn.textContent='Join pair'; return; }
      await updateDoc(doc(db,'pairs',code), { user2Id:user.uid, user2Name:userData.name, user2Email:userData.email });
      await updateDoc(doc(db,'users',user.uid), { pairCode:code });
      userData.pairCode=code;
      // Re-render today
      currentTab='today';
      renderShell(user,userData);
    };
  }

  showMain();
}

// ── History Tab ────────────────────────────────────────────────────────────
async function renderHistory(page, user, userData) {
  page.innerHTML='';
  page.appendChild(div('loading', div('spinner')));

  if (!userData?.pairCode) {
    page.innerHTML='';
    page.appendChild(Object.assign(div('card text-center'), {innerHTML:'<p class="muted">Connect with a partner to see your history.</p>'}));
    return;
  }

  const pairSnap = await getDoc(doc(db,'pairs',userData.pairCode));
  if (!pairSnap.exists()) { page.innerHTML='No pair data.'; return; }
  const pairData = pairSnap.data();
  const isUser1 = pairData.user1Id===user.uid;
  const partnerName = isUser1 ? pairData.user2Name : pairData.user1Name;
  const partnerId = isUser1 ? pairData.user2Id : pairData.user1Id;

  // Fetch history subcollection
  const histSnap = await getDocs_compat(db, userData.pairCode);
  page.innerHTML='';

  if (!histSnap.length) {
    page.appendChild(Object.assign(div('card text-center'), {innerHTML:'<p class="muted">No history yet — answer today\'s question to get started!</p>'}));
    return;
  }

  const dates = histSnap.sort((a,b)=>b.id.localeCompare(a.id));
  const badge = h('div','date-badge',`${dates.length} ${dates.length===1?'day':'days'} together`);
  badge.style.marginBottom='14px';
  page.appendChild(badge);

  dates.forEach(snap => {
    const entry = snap.data();
    const q = QUESTIONS.find(x=>x.id===entry.qId) || getDayQuestion(snap.id, pairData.seed);
    const both = entry.answers?.[user.uid] && partnerId && entry.answers?.[partnerId];

    const item = div('hist-item');
    item.innerHTML=`
      <div style="font-size:11px;text-transform:uppercase;letter-spacing:.07em;color:var(--ink-faint);margin-bottom:3px">${formatDate(snap.id)}</div>
      <div class="serif-sm" style="margin-bottom:6px">${q.text}</div>
      <div class="muted" style="font-size:12px">${both?`✦ Both answered · ${q.cat}`:`Incomplete · ${q.cat}`}</div>
    `;
    item.onclick = () => renderHistDetail(page, snap.id, entry, q, user, partnerId, partnerName, pairData.seed, userData, pairSnap);
    page.appendChild(item);
  });
}

async function getDocs_compat(db, pairCode) {
  const { getDocs, collection } = await import('https://www.gstatic.com/firebasejs/10.12.0/firebase-firestore.js');
  const snap = await getDocs(collection(db,'pairs',pairCode,'history'));
  return snap.docs;
}

function renderHistDetail(page, dateStr, entry, q, user, partnerId, partnerName, seed, userData, pairSnap) {
  page.innerHTML='';
  const backBtn = el('button',{class:'btn btn-ghost',style:{width:'auto',marginBottom:'14px'}},'← Back');
  backBtn.onclick = () => renderHistory(page, user, userData);
  page.appendChild(backBtn);

  const card = div('card fade-in');
  const myA = entry.answers?.[user.uid];
  const pA = partnerId ? entry.answers?.[partnerId] : null;
  card.innerHTML=`
    <div class="date-badge">${formatDate(dateStr)}</div>
    <span class="pill">${q.cat}</span>
    <div class="serif-lg" style="margin-bottom:18px">${q.text}</div>
    <div class="divider"></div>
  `;
  if (myA && pA) {
    const grid = div('ans-grid');
    grid.append(
      Object.assign(div('ans-card'), {innerHTML:`<div class="ans-who">You</div><div class="ans-text">${myA}</div>`}),
      Object.assign(div('ans-card'), {innerHTML:`<div class="ans-who">${partnerName||'Partner'}</div><div class="ans-text">${pA}</div>`})
    );
    card.appendChild(grid);
  } else {
    card.appendChild(Object.assign(el('p',{class:'muted'}), {textContent:"Both answers weren't submitted this day."}));
  }
  page.appendChild(card);
}

// ── Profile Tab ────────────────────────────────────────────────────────────
async function renderProfile(page, user, userData) {
  page.innerHTML='';
  page.appendChild(div('loading', div('spinner')));

  let pairData = null, totalDays=0, bothDays=0;
  let partnerName=null, partnerEmail=null, partnerId=null;

  if (userData?.pairCode) {
    const pSnap = await getDoc(doc(db,'pairs',userData.pairCode));
    if (pSnap.exists()) {
      pairData = pSnap.data();
      const isUser1 = pairData.user1Id===user.uid;
      partnerName = isUser1 ? pairData.user2Name : pairData.user1Name;
      partnerEmail = isUser1 ? pairData.user2Email : pairData.user1Email;
      partnerId = isUser1 ? pairData.user2Id : pairData.user1Id;

      const histDocs = await getDocs_compat(db, userData.pairCode);
      totalDays = histDocs.length;
      bothDays = histDocs.filter(s=>{
        const e=s.data(); return e.answers?.[user.uid] && partnerId && e.answers?.[partnerId];
      }).length;
    }
  }

  page.innerHTML='';

  // User card
  const userCard = div('card fade-in text-center');
  userCard.style.paddingTop='28px';
  const av = div('avatar avatar-lg'); av.textContent=(userData?.name||'?')[0].toUpperCase();
  const name = h('div','serif-lg', userData?.name||'');
  name.style.marginBottom='4px';
  const emailEl = h('p','muted', userData?.email||'');
  userCard.append(av,name,emailEl);
  page.appendChild(userCard);

  // Partner card
  if (pairData && partnerName) {
    const pCard = div('card');
    const ptitle = h('div','serif-sm','Your partner'); ptitle.style.marginBottom='14px';
    const prow = div('', div('avatar avatar-sm avatar-blue'));
    prow.style.cssText='display:flex;align-items:center;gap:12px;margin-bottom:16px';
    prow.children[0].textContent=partnerName[0].toUpperCase();
    const pinfo = div('');
    pinfo.innerHTML=`<div style="font-weight:500">${partnerName}</div><div class="muted">${partnerEmail||''}</div>`;
    prow.appendChild(pinfo);
    const stats = div('stat-grid');
    [{n:totalDays,l:'days active'},{n:bothDays,l:'both answered'}].forEach(({n,l})=>{
      const s=div('stat-card'); s.innerHTML=`<div class="stat-num">${n}</div><div class="label" style="font-size:11px">${l}</div>`;
      stats.appendChild(s);
    });
    pCard.append(ptitle,prow,stats);
    page.appendChild(pCard);
  }

  // Invite card (if partner not yet joined)
  if (pairData && !partnerName && userData.pairCode) {
    const iCard = div('card');
    iCard.innerHTML=`<div class="serif-sm" style="margin-bottom:6px">Invite your partner</div>
      <p class="muted" style="margin-bottom:4px">Share this code — works on any device.</p>`;
    const codeEl = div('invite-code'); codeEl.textContent=userData.pairCode;
    const copyBtn = el('button',{class:'btn btn-ghost'},'Copy code');
    let copied=false;
    copyBtn.onclick=()=>{
      navigator.clipboard.writeText(userData.pairCode).then(()=>{
        copyBtn.textContent='✓ Copied!'; setTimeout(()=>copyBtn.textContent='Copy code',2000);
      });
    };
    iCard.append(codeEl,copyBtn);
    page.appendChild(iCard);
  }

  // Sign out
  const soCard = div('card');
  const soBtn = el('button',{class:'btn btn-danger'},'Sign out');
  soBtn.onclick = async () => {
    if (unsubPair) { unsubPair(); unsubPair=null; }
    await signOut(auth);
  };
  soCard.appendChild(soBtn);
  page.appendChild(soCard);
}

// ── Auth state listener ────────────────────────────────────────────────────
onAuthStateChanged(auth, async (user) => {
  if (unsubPair) { unsubPair(); unsubPair=null; }
  if (!user) {
    renderAuth('login');
    return;
  }
  renderLoading();
  const snap = await getDoc(doc(db,'users',user.uid));
  const userData = snap.exists() ? snap.data() : { name: user.displayName||'', email: user.email, pairCode: null };
  currentTab = 'today';
  renderShell(user, userData);
});

</script>
</body>
</html>
