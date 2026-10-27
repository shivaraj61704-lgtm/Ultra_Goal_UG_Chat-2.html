 [Ultra_Goal_UG_Chat_Enhanced_Updated.html](https://github.com/user-attachments/files/34035449/Ultra_Goal_UG_Chat_Enhanced_Updated.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<meta name="theme-color" content="#ffffff">
<title>Ultra Goal | UG Chat</title>

<!-- Markdown, sanitization and math rendering -->
<script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/dompurify/dist/purify.min.js"></script>
<script>
window.MathJax = {
  tex: {
    inlineMath: [['\\(', '\\)'], ['$', '$']],
    displayMath: [['\\[', '\\]'], ['$$', '$$']]
  },
  options: { skipHtmlTags: ['script','noscript','style','textarea','pre','code'] },
  startup: { typeset: false }
};
</script>
<script defer src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>

<style>
:root {
  color-scheme: light;
  --bg:#fff; --panel:#f7f8fb; --panel2:#edf0f6; --text:#202431;
  --muted:#707887; --line:#e4e7ee; --accent:#4169e1; --user:#edf1f8;
  --shadow:0 10px 35px #18223a0c; --danger:#d93025;
}
:root[data-theme="dark"] {
  color-scheme:dark; --bg:#111318; --panel:#191c23; --panel2:#252a35;
  --text:#edf0f6; --muted:#a0a7b5; --line:#303541; --accent:#91a9ff;
  --user:#272d3a; --shadow:0 10px 35px #0004; --danger:#ff7168;
}
* { box-sizing:border-box }
html,body { height:100%; margin:0 }
body { background:var(--bg); color:var(--text); font-family:Inter,system-ui,-apple-system,"Segoe UI",sans-serif; overflow:hidden }
button,input,textarea { font:inherit }
button { cursor:pointer }
button:focus-visible,input:focus-visible,textarea:focus-visible { outline:2px solid var(--accent); outline-offset:2px }
button:disabled { opacity:.45; cursor:not-allowed }
.hidden { display:none!important }

.app { height:100dvh; display:flex }
.sidebar {
  width:270px; flex-shrink:0; display:flex; flex-direction:column; gap:15px;
  padding:17px 13px; background:var(--panel); border-right:1px solid var(--line);
  z-index:30; transition:transform .2s;
}
.brandrow { display:flex; align-items:center; gap:10px; padding:3px 7px 8px }
.logo,.welcome-logo,.mini-logo {
  display:grid; place-items:center; color:white; font-weight:900;
  background:linear-gradient(135deg,#3278ee,#9560e9);
}
.logo { width:36px; height:36px; border-radius:13px }
.brandname { font-weight:800; font-size:15px }
.brandname span { color:var(--accent) }
.newchat,.sidebutton {
  display:flex; align-items:center; gap:9px; width:100%; border:1px solid var(--line);
  border-radius:12px; padding:11px 13px; background:var(--bg); color:var(--text);
  font-size:13px; text-align:left;
}
.newchat { background:var(--panel2); font-weight:700 }
.history-label { font-size:10px; color:var(--muted); font-weight:800; text-transform:uppercase; letter-spacing:1px; padding:2px 9px }
.history { display:flex; flex-direction:column; gap:4px; overflow:auto; min-height:0 }
.history-item {
  width:100%; border:0; background:transparent; text-align:left; border-radius:10px;
  padding:10px 11px; font-size:13px; color:var(--text); overflow:hidden;
  text-overflow:ellipsis; white-space:nowrap;
}
.history-item.active,.history-item:hover { background:var(--panel2) }
.history-empty,.sidefoot { font-size:11px; color:var(--muted); padding:8px 9px; line-height:1.6 }
.sidebottom { margin-top:auto; display:grid; gap:6px }

.main { flex:1; min-width:0; display:flex; flex-direction:column; position:relative }
.topbar {
  min-height:60px; display:flex; align-items:center; justify-content:space-between;
  padding:0 22px; border-bottom:1px solid var(--line); flex-shrink:0; gap:12px;
}
.top-left,.top-actions { display:flex; align-items:center; gap:10px; min-width:0 }
.menu { display:none; border:0; background:transparent; color:var(--text); font-size:22px }
.modelname { font-size:15px; font-weight:750 }
.modeltag { font-size:10px; color:var(--muted); background:var(--panel); padding:4px 7px; border-radius:7px; margin-left:7px }
.iconbtn {
  display:grid; place-items:center; height:38px; min-width:38px; padding:0 8px;
  border:1px solid var(--line); border-radius:11px; background:var(--bg); color:var(--text);
}
.top-actions { gap:8px; flex-shrink:0 }
.profilebtn {
  display:grid; place-items:center; height:38px; width:38px; flex-shrink:0;
  border:2px solid var(--line); border-radius:50%;
  background:linear-gradient(135deg,#3278ee,#9560e9); color:#fff; font-weight:800;
  overflow:hidden; text-overflow:clip; white-space:nowrap;
}
#micBtn.listening { background:var(--danger); color:white; border-color:var(--danger) }

.chatarea { flex:1; overflow-y:auto; padding:22px 20px 18px; scroll-behavior:smooth }
.welcome {
  min-height:100%; max-width:850px; margin:auto; display:flex; flex-direction:column;
  align-items:center; justify-content:center; text-align:center; padding:18px 0 32px;
}
.welcome-logo { height:64px; width:64px; border-radius:22px; margin:0 auto 22px; font-size:21px }
.welcome h1 { font-size:clamp(29px,4vw,44px); line-height:1.15; letter-spacing:-1px; margin:0 0 13px }
.welcome h1 span { background:linear-gradient(100deg,#3278ef,#a064df); background-clip:text; -webkit-background-clip:text; color:transparent }
.welcome p { color:var(--muted); font-size:14px; line-height:1.75; max-width:540px; margin:0 auto }
.suggestions { display:grid; grid-template-columns:repeat(2,minmax(0,1fr)); gap:11px; margin:30px auto 0; max-width:680px; width:100%; text-align:left }
.suggestion { border:1px solid var(--line); background:var(--bg); border-radius:16px; padding:15px; min-height:88px; text-align:left; color:var(--text) }
.suggestion:hover { border-color:var(--accent) }
.suggestion b { display:block; font-size:13px; margin-bottom:7px }
.suggestion span { font-size:12px; color:var(--muted); line-height:1.5 }

.messages { max-width:820px; width:100%; margin:0 auto; display:flex; flex-direction:column; gap:24px; padding-bottom:20px }
.msg { display:flex; gap:12px; align-items:flex-start; min-width:0 }
.msg.user { justify-content:flex-end }
.mini-logo { width:30px; height:30px; flex-shrink:0; border-radius:10px; font-size:10px; margin-top:2px }
.msgbody { min-width:0; max-width:min(720px,92%); font-size:15px; line-height:1.8; overflow-wrap:anywhere }
.userwrap { max-width:100% }
.userbubble { background:var(--user); border:1px solid var(--line); border-radius:19px; padding:12px 15px; max-width:min(650px,86%); font-size:14px; line-height:1.75; white-space:pre-wrap; overflow-wrap:anywhere }
.message-content p { margin:0 0 14px }
.message-content p:last-child { margin-bottom:0 }
.message-content h1,.message-content h2,.message-content h3 { line-height:1.35; margin:22px 0 10px }
.message-content h1 { font-size:1.45em }.message-content h2 { font-size:1.3em }.message-content h3 { font-size:1.12em }
.message-content ul,.message-content ol { padding-left:25px; margin:9px 0 16px }
.message-content li { margin:5px 0 }
.message-content blockquote { border-left:3px solid var(--accent); margin:14px 0; padding:5px 14px; color:var(--muted) }
.message-content table { border-collapse:collapse; display:block; overflow-x:auto; margin:14px 0; max-width:100% }
.message-content th,.message-content td { border:1px solid var(--line); padding:8px 11px; text-align:left }
.message-content th { background:var(--panel) }
.message-content pre { background:var(--panel); border:1px solid var(--line); border-radius:12px; padding:14px; overflow:auto; max-width:100%; line-height:1.6 }
.message-content pre code { white-space:pre }
.message-content :not(pre)>code { background:var(--panel2); border-radius:5px; padding:1px 5px; font-size:.9em }
.message-content a { color:var(--accent) }
.message-content mjx-container { max-width:100%; overflow-x:auto; overflow-y:hidden }
.response-actions,.user-tools { display:flex; gap:5px; margin-top:8px; flex-wrap:wrap }
.user-tools { justify-content:flex-end }
.response-actions button,.user-tools button { border:0; background:transparent; color:var(--muted); padding:5px 7px; border-radius:7px; font-size:11px }
.response-actions button:hover,.user-tools button:hover { background:var(--panel2); color:var(--text) }
.typing { color:var(--muted); font-size:13px; padding:6px 0 }
.typing-dots::after { content:""; animation:dots 1.2s steps(4,end) infinite }
@keyframes dots { 0%{content:""} 25%{content:"."} 50%{content:".."} 75%,100%{content:"..."} }

.composer-wrap { padding:10px 20px 15px; background:linear-gradient(to top,var(--bg) 82%,transparent) }
.composer { max-width:820px; margin:auto; border:1px solid var(--line); border-radius:24px; padding:12px 13px 9px 18px; box-shadow:var(--shadow); background:var(--bg) }
.composer textarea { display:block; width:100%; resize:none; border:0; outline:0; background:transparent; color:var(--text); font-size:14px; line-height:1.6; min-height:29px; max-height:170px }
.composer-bottom { display:flex; align-items:center; justify-content:space-between; gap:10px; margin-top:8px }
.toolrow { display:flex; align-items:center; gap:5px; flex-wrap:wrap }
.toolbtn { border:0; background:transparent; color:var(--muted); border-radius:9px; padding:7px 9px; font-size:12px }
.toolbtn:hover { background:var(--panel) }
.send { height:38px; width:40px; flex-shrink:0; border:0; border-radius:50%; background:var(--text); color:var(--bg); font-size:19px }
.disclaimer { text-align:center; font-size:10.5px; color:var(--muted); margin:9px auto 0; max-width:820px; line-height:1.5 }

.mobile-overlay { display:none }
.modal-backdrop { position:fixed; inset:0; z-index:100; background:#0b1020a6; display:grid; place-items:center; padding:18px }
.modal { width:min(460px,100%); background:var(--bg); color:var(--text); border:1px solid var(--line); border-radius:22px; padding:24px; box-shadow:var(--shadow) }
.modal h2 { margin:0 0 8px; font-size:22px }
.modal p { color:var(--muted); font-size:13px; line-height:1.6 }
.modal label { display:block; font-size:12px; font-weight:700; margin:14px 0 6px }
.modal input { width:100%; border:1px solid var(--line); border-radius:11px; padding:11px 12px; background:var(--bg); color:var(--text) }
.modal-actions { display:flex; justify-content:flex-end; gap:8px; margin-top:18px }
.primary,.secondary { border-radius:11px; padding:10px 15px; font-weight:700 }
.primary { background:var(--accent); color:white; border:0 }
.secondary { background:var(--panel); color:var(--text); border:1px solid var(--line) }
.toast { position:fixed; z-index:120; bottom:22px; left:50%; transform:translateX(-50%); background:var(--text); color:var(--bg); padding:10px 14px; border-radius:12px; font-size:12px; max-width:calc(100% - 30px); text-align:center }

@media(max-width:760px) {
  .sidebar { position:fixed; inset:0 auto 0 0; width:280px; transform:translateX(-105%); box-shadow:10px 0 40px #0002 }
  .sidebar.open { transform:translateX(0) }
  .mobile-overlay.show { display:block; position:fixed; z-index:29; inset:0; background:#11182766 }
  .menu { display:block }
  .topbar { min-height:57px; padding:0 13px }
  .chatarea { padding:15px 13px }
  .welcome { padding-top:8px }
  .welcome-logo { width:54px; height:54px }
  .suggestions { grid-template-columns:1fr; gap:8px; margin-top:23px }
  .suggestion { min-height:68px; padding:12px 14px }
  .composer-wrap { padding:8px 10px 12px }
  .composer { border-radius:22px; padding:11px 11px 8px 14px }
  .toolbtn { padding:7px 5px }
  .disclaimer { font-size:10px }
  .messages { gap:20px }
  .msgbody { font-size:14px }
  .userbubble { max-width:90% }
  .top-actions { gap:5px }
}
@media(max-width:400px) {
  .topbar { padding:0 8px; gap:5px }
  .top-left { gap:5px }
  .modeltag { display:none }
  .top-actions { gap:4px }
  .iconbtn { height:34px; min-width:34px; padding:0 5px }
  .profilebtn { height:34px; width:34px }
  .composer-bottom { align-items:flex-end }
  .toolbtn { font-size:11px }
}
@media(prefers-reduced-motion:reduce) {
  *,*::before,*::after { scroll-behavior:auto!important; animation:none!important; transition:none!important }
}
</style>
</head>

<body>
<div class="app">
  <aside class="sidebar" id="sidebar">
    <div class="brandrow">
      <div class="logo">UG</div>
      <div class="brandname">Ultra <span>Goal</span></div>
    </div>
    <button class="newchat" id="newChat" type="button">＋ New chat <span style="margin-left:auto;color:var(--muted)">Ctrl K</span></button>
    <button class="sidebutton" id="loginSide" type="button">👤 <span id="profileLabel">Sign in / profile</span></button>
    <div class="history-label">Recent chats</div>
    <div class="history" id="history"></div>
    <div class="sidebottom">
      <button class="sidebutton" id="exportBtn" type="button">⇩ Export conversations</button>
      <button class="sidebutton" id="clearHistoryBtn" type="button">⌫ Clear chat history</button>
      <button class="sidebutton" id="aboutBtn" type="button">✦ About Ultra Goal</button>
      <button class="sidebutton" id="themeSide" type="button">🌙 Dark mode</button>
      <div class="sidefoot">UG AI Chat<br>Dream big. Build smart.</div>
    </div>
  </aside>

  <div class="mobile-overlay" id="overlay"></div>

  <main class="main">
    <header class="topbar">
      <div class="top-left">
        <button class="menu" id="menuBtn" type="button" aria-label="Open menu">☰</button>
        <div>
          <span class="modelname">UG Chat</span>
          <span class="modeltag">AI · Smart mode</span>
        </div>
      </div>
      <div class="top-actions">
        <button class="iconbtn" id="themeTop" type="button" title="Toggle light/dark theme" aria-label="Toggle theme">☾</button>
        <button class="iconbtn" id="micBtn" type="button" title="Voice input" aria-label="Start voice input">🎙️</button>
        <button class="profilebtn" id="profileBtn" type="button" aria-label="Open profile">UG</button>
      </div>
    </header>

    <section class="chatarea" id="chatarea">
      <div class="welcome" id="welcome">
        <div class="welcome-logo">UG</div>
        <h1>What can I help you <span>build?</span></h1>
        <p>Your space to learn, create, and explore. Ask in easy Kannada + English, build with Python, or discover AI and robotics. 😊</p>
        <div class="suggestions">
          <button class="suggestion" data-prompt="Teach me Python basics with a simple example in easy Kannada and English." type="button"><b>💻 Learn Python</b><span>Learn coding step by step</span></button>
          <button class="suggestion" data-prompt="Explain artificial intelligence in easy Kannada and English." type="button"><b>🧠 Explore AI</b><span>Understand AI simply</span></button>
          <button class="suggestion" data-prompt="Give me a beginner robotics project I can simulate for free." type="button"><b>🤖 Start robotics</b><span>Explore a virtual robot</span></button>
          <button class="suggestion" data-prompt="Help me plan a useful AI startup with a zero budget." type="button"><b>🚀 Build a startup</b><span>Plan your first project</span></button>
        </div>
      </div>
      <div class="messages hidden" id="messages" aria-live="polite"></div>
    </section>

    <div class="composer-wrap">
      <form class="composer" id="chatForm">
        <textarea id="prompt" rows="1" maxlength="8000" placeholder="Message Ultra Goal..." aria-label="Message Ultra Goal"></textarea>
        <div class="composer-bottom">
          <div class="toolrow">
            <button type="button" class="toolbtn" id="topicBtn">✧ Learning mode</button>
            <button type="button" class="toolbtn" id="clearInput">Clear</button>
            <button type="button" class="toolbtn" id="stopBtn" disabled>■ Stop</button>
          </div>
          <button class="send" id="sendBtn" type="submit" aria-label="Send message" disabled>↑</button>
        </div>
      </form>
      <div class="disclaimer">AI can make mistakes. Avoid entering passwords, private information, or sensitive data.</div>
    </div>
  </main>
</div>

<div class="modal-backdrop hidden" id="modalBackdrop" role="dialog" aria-modal="true" aria-labelledby="modalTitle">
  <div class="modal">
    <h2 id="modalTitle">Welcome to Ultra Goal 👋</h2>
    <p id="modalDescription">Set a local profile to personalize this browser. This demo does not create a secure account or authenticate your identity.</p>
    <form id="profileForm">
      <label for="profileName">Display name</label>
      <input id="profileName" maxlength="60" autocomplete="nickname" placeholder="What should we call you?">
      <label for="profileEmail">Email (optional, saved only on this device)</label>
      <input id="profileEmail" maxlength="120" type="email" autocomplete="email" placeholder="you@example.com">
      <div class="modal-actions">
        <button class="secondary" type="button" id="modalCancel">Cancel</button>
        <button class="primary" type="submit" id="modalSubmit">Save profile</button>
      </div>
    </form>
  </div>
</div>
<div class="toast hidden" id="toast" role="status"></div>

<script>
'use strict';

const $ = id => document.getElementById(id);
const textarea = $('prompt');
const sendBtn = $('sendBtn');
const STORAGE_KEY = 'ultraGoalChatsV3';
const THEME_KEY = 'ultraGoalTheme';
const PROFILE_KEY = 'ultraGoalProfile';

/* Change this URL only if your deployed Worker URL is different. */
const WORKER_URL = 'https://ultra-goal-ai.shivaraj61704.workers.dev/';

let chats = [];
let activeChatId = null;
let learningMode = true;
let editingMessageIndex = null;
let activeController = null;
let toastTimer = null;
let recognition = null;
let listening = false;

function activeChat() {
  return chats.find(c => c.id === activeChatId) || null;
}

function saveChats() {
  try {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(chats.slice(0, 50)));
  } catch (error) {
    showToast('Could not save history in this browser.');
  }
}

function showToast(message) {
  const toast = $('toast');
  toast.textContent = message;
  toast.classList.remove('hidden');
  clearTimeout(toastTimer);
  toastTimer = setTimeout(() => toast.classList.add('hidden'), 2800);
}

function applyTheme(theme) {
  const value = theme === 'dark' ? 'dark' : 'light';
  document.documentElement.dataset.theme = value;
  $('themeTop').textContent = value === 'dark' ? '☀' : '☾';
  $('themeTop').title = value === 'dark' ? 'Switch to light mode' : 'Switch to dark mode';
  $('themeSide').textContent = value === 'dark' ? '☀ Light mode' : '🌙 Dark mode';
  const meta = document.querySelector('meta[name="theme-color"]');
  if (meta) meta.content = value === 'dark' ? '#111318' : '#ffffff';
  try { localStorage.setItem(THEME_KEY, value); } catch (_) {}
}

function toggleTheme() {
  applyTheme(document.documentElement.dataset.theme === 'dark' ? 'light' : 'dark');
}

function getProfile() {
  try { return JSON.parse(localStorage.getItem(PROFILE_KEY) || 'null'); }
  catch (_) { return null; }
}

function updateProfileUI() {
  const profile = getProfile();
  $('profileLabel').textContent = profile?.name || 'Sign in / profile';
  $('profileBtn').textContent = profile?.name ? profile.name.trim().slice(0, 2).toUpperCase() : 'UG';
  $('profileBtn').title = profile?.name || 'Open profile';
}

function openProfile() {
  const profile = getProfile();
  $('profileName').value = profile?.name || '';
  $('profileEmail').value = profile?.email || '';
  $('modalTitle').textContent = profile ? 'Your profile 👤' : 'Welcome to Ultra Goal 👋';
  $('modalSubmit').textContent = profile ? 'Save changes' : 'Save profile';
  $('modalBackdrop').classList.remove('hidden');
  $('profileName').focus();
}

function closeProfile() {
  $('modalBackdrop').classList.add('hidden');
}

$('profileForm').addEventListener('submit', event => {
  event.preventDefault();
  const name = $('profileName').value.trim();
  const email = $('profileEmail').value.trim();
  if (email && !/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email)) {
    showToast('Enter a valid email or leave it blank.');
    return;
  }
  try {
    localStorage.setItem(PROFILE_KEY, JSON.stringify({ name: name || 'UG User', email }));
    updateProfileUI();
    closeProfile();
    showToast('Profile saved on this device.');
  } catch (_) {
    showToast('Could not save profile.');
  }
});

$('modalCancel').addEventListener('click', closeProfile);
$('modalBackdrop').addEventListener('click', event => {
  if (event.target === $('modalBackdrop')) closeProfile();
});
$('loginSide').addEventListener('click', () => { openProfile(); closeSidebar(); });
$('profileBtn').addEventListener('click', openProfile);

function renderHistory() {
  const history = $('history');
  history.replaceChildren();

  if (!chats.length) {
    const empty = document.createElement('div');
    empty.className = 'history-empty';
    empty.textContent = 'Your conversations will appear here.';
    history.appendChild(empty);
    return;
  }

  chats.slice(0, 50).forEach(chat => {
    const button = document.createElement('button');
    button.className = 'history-item' + (chat.id === activeChatId ? ' active' : '');
    button.type = 'button';
    button.textContent = chat.title || 'New chat';
    button.title = chat.title || 'New chat';
    button.addEventListener('click', () => showChat(chat.id));
    history.appendChild(button);
  });
}

function showWelcome() {
  $('welcome').classList.remove('hidden');
  $('messages').classList.add('hidden');
  $('messages').replaceChildren();
}

function newChat() {
  const chat = {
    id: String(Date.now()) + Math.random().toString(16).slice(2),
    title: 'New chat',
    messages: []
  };
  chats.unshift(chat);
  activeChatId = chat.id;
  editingMessageIndex = null;
  saveChats();
  renderHistory();
  showWelcome();
  textarea.value = '';
  resizeInput();
  closeSidebar();
  textarea.focus();
}

function showChat(id) {
  const chat = chats.find(item => item.id === id);
  if (!chat) return;

  activeChatId = id;
  editingMessageIndex = null;
  $('welcome').classList.add('hidden');
  $('messages').classList.remove('hidden');
  $('messages').replaceChildren();

  chat.messages.forEach((message, index) => {
    appendMessage(message.role, message.text, message.role === 'assistant', index);
  });

  renderHistory();
  scrollBottom();
  closeSidebar();
}

function formatMarkdown(text) {
  if (typeof marked === 'undefined' || typeof DOMPurify === 'undefined') return null;
  marked.setOptions({ gfm: true, breaks: true });
  return DOMPurify.sanitize(marked.parse(String(text ?? '')));
}

async function renderMath(element) {
  if (window.MathJax?.typesetPromise) {
    try {
      if (window.MathJax.typesetClear) window.MathJax.typesetClear([element]);
      await window.MathJax.typesetPromise([element]);
    } catch (error) {
      console.warn('MathJax render failed', error);
    }
  }
}

async function copyText(text, button) {
  try {
    await navigator.clipboard.writeText(String(text ?? ''));
    const old = button.textContent;
    button.textContent = 'Copied ✓';
    setTimeout(() => { button.textContent = old; }, 1300);
  } catch (_) {
    showToast('Copy blocked by browser. Try HTTPS or copy manually.');
  }
}

function addUserTools(wrap, text, index) {
  const tools = document.createElement('div');
  tools.className = 'user-tools';

  const copy = document.createElement('button');
  copy.type = 'button';
  copy.textContent = 'Copy';
  copy.addEventListener('click', () => copyText(text, copy));

  const edit = document.createElement('button');
  edit.type = 'button';
  edit.textContent = '✎ Edit';
  edit.addEventListener('click', () => {
    const chat = activeChat();
    if (!chat || chat.messages[index]?.role !== 'user') return;
    editingMessageIndex = index;
    textarea.value = text;
    resizeInput();
    textarea.focus();
    textarea.setSelectionRange(textarea.value.length, textarea.value.length);
    showToast('Edit the message and press Send. Later messages will be removed.');
  });

  tools.append(copy, edit);
  wrap.appendChild(tools);
}

function appendMessage(role, text, actions = true, index = -1) {
  const row = document.createElement('div');
  row.className = 'msg ' + (role === 'user' ? 'user' : 'assistant');

  if (role === 'user') {
    const wrap = document.createElement('div');
    wrap.className = 'userwrap';

    const bubble = document.createElement('div');
    bubble.className = 'userbubble';
    bubble.textContent = text;
    wrap.appendChild(bubble);
    addUserTools(wrap, text, index);
    row.appendChild(wrap);
  } else {
    const logo = document.createElement('div');
    logo.className = 'mini-logo';
    logo.textContent = 'UG';

    const content = document.createElement('div');
    content.className = 'msgbody';

    const answer = document.createElement('div');
    answer.className = 'message-content';
    const html = formatMarkdown(text);
    if (html === null) answer.textContent = text;
    else answer.innerHTML = html;

    content.appendChild(answer);
    row.append(logo, content);
    renderMath(answer);

    if (actions) {
      const bar = document.createElement('div');
      bar.className = 'response-actions';

      const copy = document.createElement('button');
      copy.type = 'button';
      copy.textContent = 'Copy';
      copy.addEventListener('click', () => copyText(text, copy));

      const regenerate = document.createElement('button');
      regenerate.type = 'button';
      regenerate.textContent = '↻ Regenerate';
      regenerate.addEventListener('click', () => {
        const chat = activeChat();
        if (!chat || activeController) return;
        const lastUser = chat.messages.map(m => m.role).lastIndexOf('user');
        if (lastUser < 0) return;
        chat.messages = chat.messages.slice(0, lastUser + 1);
        saveChats();
        showChat(chat.id);
        send(null, { regenerate: true });
      });

      bar.append(copy, regenerate);
      content.appendChild(bar);
    }
  }

  $('messages').appendChild(row);
}

function scrollBottom() {
  const area = $('chatarea');
  area.scrollTop = area.scrollHeight;
}

function resizeInput() {
  textarea.style.height = 'auto';
  textarea.style.height = Math.min(textarea.scrollHeight, 170) + 'px';
  sendBtn.disabled = !textarea.value.trim() || !!activeController;
}

function closeSidebar() {
  $('sidebar').classList.remove('open');
  $('overlay').classList.remove('show');
}

function makeTyping(id) {
  const row = document.createElement('div');
  row.className = 'msg assistant';
  row.dataset.typingFor = id;

  const logo = document.createElement('div');
  logo.className = 'mini-logo';
  logo.textContent = 'UG';

  const label = document.createElement('div');
  label.className = 'typing typing-dots';
  label.textContent = 'Ultra Goal is thinking';

  row.append(logo, label);
  $('messages').appendChild(row);
}

/* Accept common response formats returned by different Worker implementations. */
function extractAnswer(data) {
  if (typeof data === 'string') return data;
  const candidates = [
    data?.response,
    data?.reply,
    data?.text,
    data?.answer,
    data?.result?.response,
    data?.result?.text,
    data?.output_text,
    data?.output?.[0]?.content?.[0]?.text,
    data?.result?.output?.[0]?.content?.[0]?.text,
    data?.choices?.[0]?.message?.content
  ];
  return candidates.find(value => typeof value === 'string' && value.trim()) || '';
}

async function send(textOverride, options = {}) {
  if (activeController) return;

  const value = (textOverride ?? textarea.value).trim();
  if (!value && !options.regenerate) return;

  let chat = activeChat();
  if (!chat) {
    chat = {
      id: String(Date.now()) + Math.random().toString(16).slice(2),
      title: value.slice(0, 34) || 'New chat',
      messages: []
    };
    chats.unshift(chat);
    activeChatId = chat.id;
  }

  if (options.regenerate) {
    const lastUser = chat.messages.map(m => m.role).lastIndexOf('user');
    if (lastUser < 0) return;
    chat.messages = chat.messages.slice(0, lastUser + 1);
  } else if (editingMessageIndex !== null) {
    const index = editingMessageIndex;
    chat.messages = chat.messages.slice(0, index);
    chat.messages.push({ role: 'user', text: value });
    editingMessageIndex = null;
  } else {
    chat.messages.push({ role: 'user', text: value });
  }

  if (chat.title === 'New chat') chat.title = value.slice(0, 34) || 'New chat';
  saveChats();
  renderHistory();
  $('welcome').classList.add('hidden');
  $('messages').classList.remove('hidden');
  $('messages').replaceChildren();

  chat.messages.forEach((message, index) => {
    appendMessage(message.role, message.text, message.role === 'assistant', index);
  });

  textarea.value = '';
  resizeInput();

  const chatId = chat.id;
  makeTyping(chatId);
  activeController = new AbortController();
  sendBtn.disabled = true;
  $('stopBtn').disabled = false;
  scrollBottom();

  try {
    const current = chats.find(item => item.id === chatId);
    const messages = (current?.messages || [])
      .filter(message => message.role === 'user' || message.role === 'assistant')
      .slice(-30)
      .map(message => ({ role: message.role, content: message.text }));

    const latestUser = [...messages].reverse().find(message => message.role === 'user');
    const response = await fetch(WORKER_URL, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        message: latestUser?.content || value,
        messages,
        learningMode
      }),
      signal: activeController.signal
    });

    const raw = await response.text();
    let data;
    try { data = raw ? JSON.parse(raw) : {}; }
    catch (_) { data = { error: raw || 'Server returned an unreadable response.' }; }

    if (!response.ok) {
      const detail = [data.error, data.details, data.message, 'HTTP ' + response.status]
        .filter(Boolean).join(' — ');
      throw new Error(detail || 'Worker request failed.');
    }

    const answer = extractAnswer(data);
    if (!answer.trim()) {
      throw new Error(data.error || 'The Worker returned no answer text. Check its API response format.');
    }

    const latestChat = chats.find(item => item.id === chatId);
    if (latestChat) {
      latestChat.messages.push({ role: 'assistant', text: answer.trim() });
      saveChats();
    }

    if (activeChatId === chatId) {
      $('messages').querySelector('[data-typing-for="' + chatId + '"]')?.remove();
      appendMessage('assistant', answer.trim(), true, (activeChat()?.messages.length || 1) - 1);
      scrollBottom();
    }
  } catch (error) {
    if (error.name === 'AbortError') {
      showToast('Generation stopped.');
    } else if (activeChatId === chatId) {
      $('messages').querySelector('[data-typing-for="' + chatId + '"]')?.remove();
      const message = error?.message || 'Please try again.';
      appendMessage(
        'assistant',
        'Could not get an AI response: ' + message +
        '\n\nCheck that your Cloudflare Worker is deployed, accepts POST requests, and returns JSON containing a response, reply, text, or answer field.',
        false
      );
      scrollBottom();
    }
  } finally {
    activeController = null;
    $('stopBtn').disabled = true;
    resizeInput();
  }
}

$('chatForm').addEventListener('submit', event => {
  event.preventDefault();
  send();
});

textarea.addEventListener('input', resizeInput);
textarea.addEventListener('keydown', event => {
  if (event.key === 'Enter' && !event.shiftKey && !event.isComposing) {
    event.preventDefault();
    send();
  }
});

$('newChat').addEventListener('click', newChat);
$('clearInput').addEventListener('click', () => {
  textarea.value = '';
  editingMessageIndex = null;
  resizeInput();
  textarea.focus();
});
$('stopBtn').addEventListener('click', () => {
  if (activeController) activeController.abort();
});

document.querySelectorAll('[data-prompt]').forEach(button => {
  button.addEventListener('click', () => {
    textarea.value = button.dataset.prompt || '';
    resizeInput();
    send();
  });
});

$('menuBtn').addEventListener('click', () => {
  $('sidebar').classList.add('open');
  $('overlay').classList.add('show');
});
$('overlay').addEventListener('click', closeSidebar);
$('themeTop').addEventListener('click', toggleTheme);
$('themeSide').addEventListener('click', toggleTheme);

$('topicBtn').addEventListener('click', () => {
  learningMode = !learningMode;
  $('topicBtn').textContent = learningMode ? '✧ Learning mode' : '✧ General mode';
  textarea.placeholder = learningMode ? 'Ask about AI, Python or robotics...' : 'Message Ultra Goal...';
  showToast(learningMode ? 'Learning mode enabled.' : 'General mode enabled.');
});

$('aboutBtn').addEventListener('click', () => {
  closeSidebar();
  alert(
    'Ultra Goal AI Chat\n\n' +
    'A learning-focused interface for maths, Python, AI, robotics, and startup ideas.\n\n' +
    'Features: Markdown, maths rendering, local chat history, edit, copy, regenerate, themes, voice input, export, and local profile settings.\n\n' +
    'The profile is stored only in this browser; it is not secure account authentication. Conversations are sent to the configured Cloudflare Worker.'
  );
});

$('clearHistoryBtn').addEventListener('click', () => {
  if (!confirm('Clear all saved conversations from this browser? This cannot be undone.')) return;
  if (activeController) activeController.abort();
  chats = [];
  activeChatId = null;
  editingMessageIndex = null;
  saveChats();
  renderHistory();
  showWelcome();
  closeSidebar();
  showToast('Chat history cleared.');
});

$('exportBtn').addEventListener('click', () => {
  const blob = new Blob([JSON.stringify(chats, null, 2)], { type: 'application/json' });
  const url = URL.createObjectURL(blob);
  const anchor = document.createElement('a');
  anchor.href = url;
  anchor.download = 'ultra-goal-chat-history.json';
  document.body.appendChild(anchor);
  anchor.click();
  anchor.remove();
  setTimeout(() => URL.revokeObjectURL(url), 1000);
  showToast('Chat history export started.');
});

document.addEventListener('keydown', event => {
  if ((event.ctrlKey || event.metaKey) && event.key.toLowerCase() === 'k') {
    event.preventDefault();
    newChat();
  }
  if (event.key === 'Escape') {
    closeProfile();
    closeSidebar();
    if (listening && recognition) recognition.stop();
  }
});

/* Browser speech recognition: voice-to-text only. HTTPS/localhost and permission may be required. */
function setupMicrophone() {
  const micButton = $('micBtn');
  const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;

  if (!SpeechRecognition) {
    micButton.addEventListener('click', () => {
      showToast('Voice input is not supported in this browser. Try a recent Chrome browser.');
    });
    return;
  }

  recognition = new SpeechRecognition();
  recognition.lang = 'en-IN';
  recognition.continuous = false;
  recognition.interimResults = true;

  recognition.onstart = () => {
    listening = true;
    micButton.classList.add('listening');
    micButton.textContent = '⏹';
    micButton.title = 'Stop voice input';
    micButton.setAttribute('aria-label', 'Stop voice input');
    showToast('Listening… speak now.');
  };

  recognition.onresult = event => {
    let transcript = '';
    for (let index = 0; index < event.results.length; index++) {
      transcript += event.results[index][0].transcript;
    }
    textarea.value = transcript;
    resizeInput();
  };

  recognition.onerror = event => {
    const messages = {
      'not-allowed': 'Allow microphone permission in your browser settings.',
      'no-speech': 'No speech detected. Tap the microphone and try again.',
      'audio-capture': 'No microphone was detected.'
    };
    showToast(messages[event.error] || ('Voice input error: ' + event.error));
  };

  recognition.onend = () => {
    listening = false;
    micButton.classList.remove('listening');
    micButton.textContent = '🎙️';
    micButton.title = 'Voice input';
    micButton.setAttribute('aria-label', 'Start voice input');
  };

  micButton.addEventListener('click', () => {
    if (listening) {
      recognition.stop();
      return;
    }
    try { recognition.start(); }
    catch (_) { showToast('Please wait a moment and try the microphone again.'); }
  });
}

function loadChats() {
  try {
    const saved = JSON.parse(localStorage.getItem(STORAGE_KEY) || '[]');
    chats = Array.isArray(saved) ? saved.filter(chat =>
      chat && typeof chat.id === 'string' && Array.isArray(chat.messages)
    ) : [];
  } catch (_) {
    chats = [];
  }

  if (chats.length) showChat(chats[0].id);
  else {
    showWelcome();
    renderHistory();
  }
}

try { applyTheme(localStorage.getItem(THEME_KEY) || 'light'); }
catch (_) { applyTheme('light'); }

updateProfileUI();
loadChats();
resizeInput();
setupMicrophone();
</script>
</body>
</html>
