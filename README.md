 <!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<meta name="theme-color" content="#ffffff">
<title>Ultra Goal | UG Chat</title>

<style>
:root {
  --bg: #fff;
  --side: #f5f6f8;
  --text: #202124;
  --muted: #70757d;
  --line: #e5e7eb;
  --accent: #3568e8;
  --bubble: #f1f3f5;
  --card: #fff;
}

* { box-sizing: border-box; }

body {
  margin: 0;
  background: var(--bg);
  color: var(--text);
  font-family: Inter, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  height: 100dvh;
  overflow: hidden;
}

button, textarea { font: inherit; }
button { cursor: pointer; }

.app {
  display: flex;
  height: 100dvh;
  width: 100%;
}

.sidebar {
  width: 265px;
  background: var(--side);
  padding: 17px 13px;
  display: flex;
  flex-direction: column;
  gap: 18px;
  flex-shrink: 0;
  transition: transform .2s;
}

.brandrow {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 2px 7px 9px;
}

.logo {
  height: 34px;
  width: 34px;
  border-radius: 12px;
  display: grid;
  place-items: center;
  color: white;
  font-weight: 900;
  font-size: 12px;
  letter-spacing: -.5px;
  background: linear-gradient(135deg,#3278ee,#8c5ce9);
}

.brandname {
  font-weight: 800;
  letter-spacing: .2px;
  font-size: 15px;
}

.brandname span { color: #5e68d8; }

.newchat {
  display: flex;
  align-items: center;
  gap: 10px;
  border: 0;
  border-radius: 25px;
  padding: 12px 15px;
  background: #e8ebf1;
  color: #34383f;
  font-size: 13px;
  font-weight: 650;
  text-align: left;
}

.newchat:hover { background: #dde2eb; }

.history-label {
  font-size: 11px;
  color: #858b95;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: .8px;
  padding: 0 9px;
}

.history {
  display: flex;
  flex-direction: column;
  gap: 4px;
  overflow: auto;
}

.history-item {
  border: 0;
  background: transparent;
  text-align: left;
  border-radius: 10px;
  padding: 10px 11px;
  font-size: 13px;
  color: #434750;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.history-item:hover,
.history-item.active { background: #e9ecf2; }

.sidebottom {
  margin-top: auto;
  display: grid;
  gap: 5px;
}

.sidefoot {
  font-size: 11px;
  color: #8a9099;
  padding: 8px 9px;
  line-height: 1.5;
}

.main {
  flex: 1;
  min-width: 0;
  display: flex;
  flex-direction: column;
  position: relative;
}

.topbar {
  height: 62px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 22px;
  border-bottom: 1px solid #f0f1f3;
  flex-shrink: 0;
}

.top-left {
  display: flex;
  align-items: center;
  gap: 12px;
}

.menu {
  display: none;
  border: 0;
  background: transparent;
  font-size: 22px;
  color: #525761;
  padding: 5px;
}

.modelname {
  font-weight: 700;
  font-size: 15px;
}

.modeltag {
  font-size: 11px;
  color: #6b7280;
  background: #f3f4f6;
  padding: 5px 8px;
  border-radius: 7px;
  margin-left: 7px;
}

.top-actions {
  display: flex;
  align-items: center;
  gap: 9px;
}

.avatar {
  height: 30px;
  width: 30px;
  border-radius: 50%;
  display: grid;
  place-items: center;
  background: #e8eaff;
  color: #5452a2;
  font-weight: 800;
  font-size: 12px;
}

.chatarea {
  flex: 1;
  overflow-y: auto;
  padding: 24px 20px 18px;
  scroll-behavior: smooth;
}

.welcome {
  max-width: 760px;
  margin: 11vh auto 0;
  text-align: center;
}

.welcome-logo {
  height: 58px;
  width: 58px;
  border-radius: 20px;
  margin: 0 auto 20px;
  display: grid;
  place-items: center;
  background: linear-gradient(135deg,#367df1,#a16be8);
  color: white;
  font-weight: 900;
  font-size: 20px;
  box-shadow: 0 10px 28px #5e78dc25;
}

.welcome h1 {
  font-size: clamp(28px,4vw,39px);
  letter-spacing: -1.2px;
  margin: 0 0 12px;
  font-weight: 650;
}

.welcome h1 span {
  background: linear-gradient(100deg,#3278ef,#9b66dc);
  background-clip: text;
  -webkit-background-clip: text;
  color: transparent;
}

.welcome p {
  margin: 0 auto;
  color: var(--muted);
  font-size: 14px;
  line-height: 1.7;
  max-width: 500px;
}

.suggestions {
  display: grid;
  grid-template-columns: repeat(2,minmax(0,1fr));
  gap: 11px;
  margin: 32px auto 0;
  max-width: 650px;
  text-align: left;
}

.suggestion {
  border: 1px solid #e7e9ed;
  background: #fff;
  border-radius: 16px;
  padding: 15px 16px;
  min-height: 85px;
  text-align: left;
  color: #343941;
  transition: border-color .15s,background .15s;
}

.suggestion:hover {
  border-color: #bdc9f3;
  background: #fbfcff;
}

.suggestion b {
  display: block;
  font-size: 13px;
  margin-bottom: 6px;
}

.suggestion span {
  font-size: 12px;
  color: #737983;
  line-height: 1.45;
}

.messages {
  max-width: 790px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 24px;
  padding-bottom: 15px;
}

.msg {
  display: flex;
  gap: 12px;
  align-items: flex-start;
}

.msg.user { justify-content: flex-end; }

.msg .mini-logo {
  width: 29px;
  height: 29px;
  flex-shrink: 0;
  border-radius: 10px;
  display: grid;
  place-items: center;
  background: linear-gradient(135deg,#367df1,#a16be8);
  color: #fff;
  font-weight: 900;
  font-size: 10px;
}

.msgbody {
  max-width: min(680px,90%);
  font-size: 14px;
  line-height: 1.75;
  white-space: pre-wrap;
  overflow-wrap: anywhere;
}

.userbubble {
  background: #f1f3f5;
  border-radius: 20px;
  padding: 11px 16px;
  max-width: min(610px,85%);
  font-size: 14px;
  line-height: 1.65;
  white-space: pre-wrap;
  overflow-wrap: anywhere;
}

.response-actions {
  display: flex;
  gap: 7px;
  margin-top: 10px;
}

.response-actions button {
  border: 0;
  background: transparent;
  color: #858b95;
  padding: 5px 7px;
  border-radius: 7px;
  font-size: 12px;
}

.response-actions button:hover {
  background: #f1f3f5;
  color: #343941;
}

.typing {
  color: #7a818b;
  font-size: 13px;
  padding: 6px 0;
}

.composer-wrap {
  padding: 10px 20px 17px;
  background: linear-gradient(to top,#fff 80%,#ffffffd9);
}

.composer {
  max-width: 790px;
  margin: auto;
  border: 1px solid #dfe2e7;
  border-radius: 25px;
  padding: 12px 13px 9px 18px;
  box-shadow: 0 5px 20px #17223a0a;
  background: #fff;
}

.composer:focus-within {
  border-color: #c3cce0;
  box-shadow: 0 5px 24px #17223a0d;
}

.composer textarea {
  display: block;
  width: 100%;
  resize: none;
  border: 0;
  outline: 0;
  background: transparent;
  color: #202124;
  font-size: 14px;
  line-height: 1.55;
  min-height: 29px;
  max-height: 150px;
}

.composer textarea::placeholder { color: #858b95; }

.composer-bottom {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 10px;
  margin-top: 8px;
}

.toolrow {
  display: flex;
  align-items: center;
  gap: 7px;
}

.toolbtn {
  border: 0;
  background: transparent;
  color: #6f7680;
  border-radius: 9px;
  padding: 7px 9px;
  font-size: 12px;
}

.toolbtn:hover { background: #f3f4f6; }

.send {
  height: 34px;
  width: 36px;
  border: 0;
  border-radius: 50%;
  background: #252a31;
  color: white;
  font-size: 18px;
  display: grid;
  place-items: center;
}

.send:disabled {
  background: #c8cbd0;
  cursor: not-allowed;
}

.disclaimer {
  text-align: center;
  font-size: 10.5px;
  color: #969ba3;
  margin: 9px auto 0;
  max-width: 790px;
  line-height: 1.5;
}

.mobile-overlay { display: none; }
.hidden { display: none !important; }

@media(max-width:760px) {
  .sidebar {
    position: fixed;
    z-index: 20;
    inset: 0 auto 0 0;
    width: 275px;
    transform: translateX(-105%);
    box-shadow: 10px 0 40px #0001;
  }

  .sidebar.open { transform: translateX(0); }

  .mobile-overlay.show {
    display: block;
    position: fixed;
    z-index: 19;
    inset: 0;
    background: #11182755;
  }

  .menu { display: block; }

  .topbar {
    height: 57px;
    padding: 0 13px;
  }

  .chatarea { padding: 18px 14px; }
  .welcome { margin: 8vh auto 0; }
  .welcome-logo { width: 51px; height: 51px; }

  .suggestions {
    grid-template-columns: 1fr;
    gap: 8px;
    margin-top: 25px;
  }

  .suggestion {
    min-height: 68px;
    padding: 12px 14px;
  }

  .composer-wrap { padding: 8px 11px 12px; }

  .composer {
    border-radius: 22px;
    padding: 11px 11px 8px 14px;
  }

  .toolbtn { padding: 7px 5px; }
  .disclaimer { font-size: 10px; }
  .modeltag { display: none; }
  .messages { gap: 20px; }
  .msgbody { font-size: 14px; }
  .userbubble { max-width: 88%; }
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

    <button class="newchat" id="newChat" type="button">
      <span style="font-size:18px">＋</span> New chat
    </button>

    <div class="history-label">Recent chats</div>
    <div class="history" id="history"></div>

    <div class="sidebottom">
      <button class="history-item" id="aboutBtn" type="button">
        ✦ About Ultra Goal
      </button>
      <div class="sidefoot">
        UG AI Chat · Demo interface<br>
        Dream big. Build smart.
      </div>
    </div>
  </aside>

  <div class="mobile-overlay" id="overlay"></div>

  <main class="main">
    <header class="topbar">
      <div class="top-left">
        <button class="menu" id="menuBtn" aria-label="Open menu" type="button">☰</button>
        <div>
          <span class="modelname">UG Chat</span>
          <span class="modeltag">Preview</span>
        </div>
      </div>

      <div class="top-actions">
        <div class="avatar" aria-label="Ultra Goal">UG</div>
      </div>
    </header>

    <section class="chatarea" id="chatarea">
      <div class="welcome" id="welcome">
        <div class="welcome-logo">UG</div>

        <h1>What can I help you <span>build?</span></h1>

        <p>
          Your space to explore AI, learn Python, and discover robotics.
          Ask a question or choose a starter prompt below.
        </p>

        <div class="suggestions">
          <button class="suggestion" data-prompt="Teach me Python basics with a simple example." type="button">
            <b>💻 Learn Python</b>
            <span>Understand a coding concept step by step</span>
          </button>

          <button class="suggestion" data-prompt="Explain artificial intelligence in simple Kannada and English." type="button">
            <b>🧠 Explore AI</b>
            <span>Learn how AI works in simple language</span>
          </button>

          <button class="suggestion" data-prompt="Give me a beginner robotics project I can simulate for free." type="button">
            <b>🤖 Start robotics</b>
            <span>Try a beginner-friendly virtual robot project</span>
          </button>

          <button class="suggestion" data-prompt="Help me plan a useful AI startup with a zero budget." type="button">
            <b>🚀 Build a startup</b>
            <span>Turn an idea into a practical first project</span>
          </button>
        </div>
      </div>

      <div class="messages hidden" id="messages" aria-live="polite"></div>
    </section>

    <div class="composer-wrap">
      <form class="composer" id="chatForm">
        <textarea
          id="prompt"
          rows="1"
          maxlength="8000"
          placeholder="Message Ultra Goal..."
          aria-label="Message Ultra Goal"
        ></textarea>

        <div class="composer-bottom">
          <div class="toolrow">
            <button type="button" class="toolbtn" id="topicBtn">✧ Learning mode</button>
            <button type="button" class="toolbtn" id="clearInput">Clear</button>
          </div>

          <button
            class="send"
            id="sendBtn"
            type="submit"
            aria-label="Send message"
            title="Send message"
            disabled
          >↑</button>
        </div>
      </form>

      <div class="disclaimer">
        UG Chat is a front-end demo and does not connect to a live AI model yet.
        Responses are sample guidance, not generated by an online AI service.
      </div>
    </div>
  </main>
</div>

<script>
const $ = id => document.getElementById(id);

const textarea = $('prompt');
const sendBtn = $('sendBtn');
const STORAGE_KEY = 'ultraGoalChatsV2';

let chats = [];
let activeChatId = null;
let learningMode = true;

function activeChat() {
  return chats.find(chat => chat.id === activeChatId) || null;
}

function saveChats() {
  try {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(chats.slice(0, 30)));
  } catch (error) {
    console.warn('Could not save chat history:', error);
  }
}

function renderHistory() {
  const history = $('history');
  history.replaceChildren();

  if (!chats.length) {
    const empty = document.createElement('div');
    empty.className = 'sidefoot';
    empty.textContent = 'Your conversations will appear here.';
    history.appendChild(empty);
    return;
  }

  chats.slice(0, 30).forEach(chat => {
    const button = document.createElement('button');

    button.className =
      'history-item' + (chat.id === activeChatId ? ' active' : '');

    button.type = 'button';
    button.textContent = chat.title || 'New chat';
    button.title = button.textContent;

    button.onclick = () => showChat(chat.id);

    history.appendChild(button);
  });
}

function showWelcome() {
  $('welcome').classList.remove('hidden');
  $('messages').classList.add('hidden');
  $('messages').replaceChildren();
  $('chatarea').scrollTop = 0;
}

function newChat() {
  const chat = {
    id: String(Date.now()) + Math.random().toString(16).slice(2),
    title: 'New chat',
    messages: []
  };

  chats.unshift(chat);
  activeChatId = chat.id;

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

  $('welcome').classList.add('hidden');
  $('messages').classList.remove('hidden');
  $('messages').replaceChildren();

  chat.messages.forEach(message => {
    appendMessage(
      message.role,
      message.text,
      message.role === 'assistant'
    );
  });

  renderHistory();
  scrollBottom();
  closeSidebar();
}

function appendMessage(role, text, addActions = true) {
  const row = document.createElement('div');
  row.className = 'msg ' + (role === 'user' ? 'user' : 'assistant');

  if (role === 'user') {
    const bubble = document.createElement('div');
    bubble.className = 'userbubble';
    bubble.textContent = text;
    row.appendChild(bubble);
  } else {
    const logo = document.createElement('div');
    logo.className = 'mini-logo';
    logo.textContent = 'UG';

    const content = document.createElement('div');
    content.className = 'msgbody';

    const answer = document.createElement('div');
    answer.textContent = text;
    content.appendChild(answer);

    row.append(logo, content);

    if (addActions) {
      const actions = document.createElement('div');
      actions.className = 'response-actions';

      const copy = document.createElement('button');
      copy.type = 'button';
      copy.textContent = 'Copy';

      copy.onclick = async () => {
        try {
          if (navigator.clipboard && window.isSecureContext) {
            await navigator.clipboard.writeText(text);
          } else {
            const temp = document.createElement('textarea');
            temp.value = text;
            temp.style.position = 'fixed';
            temp.style.opacity = '0';

            document.body.appendChild(temp);
            temp.select();
            document.execCommand('copy');
            temp.remove();
          }

          copy.textContent = 'Copied';
        } catch (error) {
          copy.textContent = 'Copy failed';
        }
      };

      actions.appendChild(copy);
      content.appendChild(actions);
    }
  }

  $('messages').appendChild(row);
}

function send(text) {
  const value = (text ?? textarea.value).trim();

  if (!value) {
    textarea.focus();
    return;
  }

  let chat = activeChat();

  if (!chat) {
    chat = {
      id: String(Date.now()) + Math.random().toString(16).slice(2),
      title: value.slice(0, 34),
      messages: []
    };

    chats.unshift(chat);
    activeChatId = chat.id;
  }

  if (!chat.messages.length || chat.title === 'New chat') {
    chat.title = value.slice(0, 34);
  }

  chat.messages.push({ role: 'user', text: value });

  saveChats();
  renderHistory();

  $('welcome').classList.add('hidden');
  $('messages').classList.remove('hidden');
  $('messages').replaceChildren();

  chat.messages.forEach(message => {
    appendMessage(
      message.role,
      message.text,
      message.role === 'assistant'
    );
  });

  textarea.value = '';
  resizeInput();

  const chatId = chat.id;

  const typing = document.createElement('div');
  typing.className = 'msg assistant';
  typing.dataset.typingFor = chatId;

  const logo = document.createElement('div');
  logo.className = 'mini-logo';
  logo.textContent = 'UG';

  const label = document.createElement('div');
  label.className = 'typing';
  label.textContent = 'UG is preparing a demo response…';

  typing.append(logo, label);
  $('messages').appendChild(typing);

  scrollBottom();

  setTimeout(() => {
    const current = chats.find(item => item.id === chatId);
    if (!current) return;

    const answer = sampleAnswer(value);

    current.messages.push({
      role: 'assistant',
      text: answer
    });

    saveChats();

    if (activeChatId === chatId) {
      const indicator = $('messages').querySelector(
        '[data-typing-for="' + chatId + '"]'
      );

      if (indicator) indicator.remove();

      appendMessage('assistant', answer, true);
      scrollBottom();
    }
  }, 450);
}

function scrollBottom() {
  $('chatarea').scrollTop = $('chatarea').scrollHeight;
}

function resizeInput() {
  textarea.style.height = 'auto';
  textarea.style.height = Math.min(textarea.scrollHeight, 150) + 'px';
  sendBtn.disabled = !textarea.value.trim();
}

function closeSidebar() {
  $('sidebar').classList.remove('open');
  $('overlay').classList.remove('show');
}

function sampleAnswer(prompt) {
  const p = prompt.toLowerCase();

  if (/python|code|program|coding/.test(p)) {
    return `Let’s build this step by step.

Try this beginner Python example:

name = input("What is your name? ")
print("Welcome to Ultra Goal,", name)

What it teaches:
• input() collects text from the user.
• A variable stores that text.
• print() displays a message.

Mini-challenge: change the program so it also asks which topic you want to learn.

Note: UG Chat is currently a demo and does not execute code or connect to a live AI model.`;
  }

  if (/robot|sensor|motor|simulation/.test(p)) {
    return `A good first robotics project is a virtual obstacle-avoiding robot.

Beginner plan:
1. Represent the robot with a simple shape on a screen.
2. Give it forward, left, right and stop actions.
3. Add a simulated obstacle.
4. If the path is blocked, turn; otherwise move forward.
5. Test different obstacle positions.

You can prototype the movement logic in Python first, then explore a free simulator such as Webots. You do not need to buy a physical robot for the first version.`;
  }

  if (/startup|business|company|zero budget|₹0|budget/.test(p)) {
    return `For a ₹0 AI startup, start with a small problem rather than expensive hardware.

A practical first idea: Ultra Goal Learning Assistant — a beginner tool that helps students learn Python and basic robotics in simple language.

First steps:
1. Talk to 5 students and ask what coding topic confuses them.
2. Build a small Python prototype for one topic.
3. Let them try it and ask what was useful or confusing.
4. Improve the prototype before adding AI or hardware.

Free prototypes are possible, but live AI APIs and public hosting may have limits or costs later.`;
  }

  if (/kannada|ಕನ್ನಡ|english/.test(p)) {
    return `Artificial Intelligence (AI) ಅಂದರೆ computers ಬಳಸಿ learning, pattern recognition, language understanding ಮತ್ತು decision-support ಹೀಗೆ tasks ಮಾಡಿಸುವ technology.

Example: A program can learn from examples to classify pictures. Machine Learning is one area of AI. Robotics combines software with sensors and physical or simulated machines.

ನಿನಗೆ ಬೇಕಾದ topic ಹೇಳು — ನಾವು simple Kannada + Englishನಲ್ಲಿ step by step ಕಲಿಯೋಣ.`;
  }

  if (/hello|hi|hey|namaste/.test(p)) {
    return `Hello! Welcome to Ultra Goal (UG) 👋

I can help you practise Python, explore AI concepts, plan beginner robotics simulations, and shape your startup ideas.

What would you like to learn first?`;
  }

  return `Thanks for your question! I’m the Ultra Goal (UG) chat prototype.

I can currently show sample guidance about:
• Python basics and small coding projects
• AI and machine learning fundamentals
• Beginner robotics and virtual simulations
• Planning a low-budget technology startup

This demo does not connect to a live AI model, so I can’t generate a true AI answer to every question yet. A later version can connect to an AI service.`;
}

$('chatForm').addEventListener('submit', event => {
  event.preventDefault();
  send();
});

textarea.addEventListener('input', resizeInput);

textarea.addEventListener('keydown', event => {
  if (
    event.key === 'Enter' &&
    !event.shiftKey &&
    !event.isComposing
  ) {
    event.preventDefault();
    send();
  }
});

$('newChat').addEventListener('click', newChat);

$('clearInput').addEventListener('click', () => {
  textarea.value = '';
  resizeInput();
  textarea.focus();
});

document.querySelectorAll('[data-prompt]').forEach(button => {
  button.addEventListener('click', () => {
    textarea.value = button.dataset.prompt;
    resizeInput();
    send();
  });
});

$('menuBtn').addEventListener('click', () => {
  $('sidebar').classList.add('open');
  $('overlay').classList.add('show');
});

$('overlay').addEventListener('click', closeSidebar);

$('aboutBtn').addEventListener('click', () => {
  alert(
    'Ultra Goal (UG) is a learning project for AI, Python and robotics. This page is a demo UI, not a live AI service.'
  );
});

$('topicBtn').addEventListener('click', () => {
  learningMode = !learningMode;

  $('topicBtn').textContent = learningMode
    ? '✧ Learning mode'
    : '✧ General mode';

  textarea.placeholder = learningMode
    ? 'Ask about AI, Python or robotics...'
    : 'Message Ultra Goal...';
});

function loadChats() {
  try {
    const saved = JSON.parse(
      localStorage.getItem(STORAGE_KEY) || '[]'
    );

    chats = Array.isArray(saved) ? saved : [];
  } catch (error) {
    chats = [];
  }

  if (chats.length) {
    showChat(chats[0].id);
  } else {
    showWelcome();
    renderHistory();
  }
}

loadChats();
resizeInput();
</script>
</body>
</html>
