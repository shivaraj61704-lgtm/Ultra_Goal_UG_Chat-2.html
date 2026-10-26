 <!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#ffffff">
<title>Ultra Goal | UG Chat</title>

<style>
:root {
  --bg: #ffffff;
  --sidebar: #f6f7f9;
  --text: #202124;
  --muted: #777e89;
  --border: #e5e7eb;
  --accent: #5368e8;
  --bubble: #f0f2f5;
}

* {
  box-sizing: border-box;
}

html, body {
  width: 100%;
  height: 100%;
  margin: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  background: var(--bg);
  color: var(--text);
  overflow: hidden;
}

button, textarea {
  font: inherit;
}

button {
  cursor: pointer;
}

.app {
  height: 100dvh;
  display: flex;
  overflow: hidden;
}

/* SIDEBAR */

.sidebar {
  width: 260px;
  flex-shrink: 0;
  display: flex;
  flex-direction: column;
  gap: 17px;
  padding: 18px 13px;
  background: var(--sidebar);
  border-right: 1px solid var(--border);
}

.brand {
  display: flex;
  align-items: center;
  gap: 11px;
  padding: 3px 6px 12px;
  font-size: 17px;
  font-weight: 800;
}

.logo {
  width: 37px;
  height: 37px;
  border-radius: 12px;
  display: grid;
  place-items: center;
  color: white;
  font-size: 13px;
  font-weight: 900;
  background: linear-gradient(135deg, #347cf3, #9662e8);
}

.brand span {
  color: var(--accent);
}

.new-chat {
  width: 100%;
  min-height: 45px;
  padding: 10px 13px;
  display: flex;
  align-items: center;
  gap: 10px;
  border: 1px solid var(--border);
  border-radius: 13px;
  background: white;
  color: var(--text);
  font-size: 14px;
  font-weight: 600;
  text-align: left;
}

.new-chat:hover {
  background: #eef1ff;
  border-color: #d3d9ff;
}

.plus {
  display: grid;
  place-items: center;
  width: 25px;
  height: 25px;
  border-radius: 8px;
  background: #edf0ff;
  color: var(--accent);
  font-size: 21px;
}

.section-title {
  padding: 0 8px;
  color: var(--muted);
  font-size: 11px;
  font-weight: bold;
  letter-spacing: 1px;
  text-transform: uppercase;
}

.history {
  display: flex;
  flex-direction: column;
  gap: 5px;
  overflow-y: auto;
}

.history-item {
  width: 100%;
  padding: 11px;
  border: 0;
  border-radius: 10px;
  background: transparent;
  color: #414650;
  font-size: 13px;
  text-align: left;
  text-overflow: ellipsis;
  overflow: hidden;
  white-space: nowrap;
}

.history-item:hover,
.history-item.active {
  background: #e8ebf1;
}

.sidebar-bottom {
  margin-top: auto;
  color: #8a9099;
  font-size: 11px;
  line-height: 1.6;
  padding: 8px;
}

/* MAIN AREA */

.main {
  min-width: 0;
  height: 100dvh;
  flex: 1;
  display: flex;
  flex-direction: column;
  overflow: hidden;
  position: relative;
}

/* Small, clean header */

.header {
  height: 44px;
  min-height: 44px;
  display: flex;
  align-items: center;
  padding: 0 18px;
  border-bottom: 1px solid #f0f1f3;
  background: white;
}

.menu-button {
  display: none;
  border: 0;
  background: transparent;
  font-size: 22px;
  padding: 4px 8px 4px 0;
}

/* ONLY THE CHAT CONTENT SCROLLS */

.chat-area {
  flex: 1 1 auto;
  min-height: 0;
  overflow-y: auto;
  overscroll-behavior: contain;
  padding: 25px 18px;
  scroll-behavior: smooth;
}

/* WELCOME SCREEN */

.welcome {
  max-width: 720px;
  margin: 9vh auto 0;
  text-align: center;
}

.welcome-logo {
  width: 59px;
  height: 59px;
  margin: 0 auto 21px;
  border-radius: 20px;
  display: grid;
  place-items: center;
  background: linear-gradient(135deg, #347cf3, #9662e8);
  color: white;
  font-weight: 900;
  font-size: 21px;
}

.welcome h1 {
  margin: 0 0 12px;
  font-size: clamp(28px, 4vw, 39px);
  letter-spacing: -1px;
}

.gradient-text {
  background: linear-gradient(100deg, #347cf3, #9662e8);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}

.welcome p {
  max-width: 480px;
  margin: auto;
  color: var(--muted);
  font-size: 14px;
  line-height: 1.7;
}

.suggestions {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 12px;
  margin: 30px auto 0;
  text-align: left;
}

.suggestion {
  min-height: 84px;
  padding: 15px;
  border: 1px solid var(--border);
  border-radius: 15px;
  background: white;
  text-align: left;
}

.suggestion:hover {
  border-color: #bfcaf8;
  background: #fbfcff;
}

.suggestion strong {
  display: block;
  font-size: 13px;
  margin-bottom: 7px;
}

.suggestion small {
  color: var(--muted);
  font-size: 12px;
  line-height: 1.5;
}

/* MESSAGES */

.messages {
  max-width: 790px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 24px;
  padding-bottom: 15px;
}

.message {
  display: flex;
  gap: 12px;
  align-items: flex-start;
}

.message.user {
  justify-content: flex-end;
}

.message-logo {
  flex-shrink: 0;
  width: 30px;
  height: 30px;
  border-radius: 10px;
  display: grid;
  place-items: center;
  background: linear-gradient(135deg, #347cf3, #9662e8);
  color: white;
  font-size: 10px;
  font-weight: 900;
}

.message-body {
  max-width: min(680px, 90%);
  font-size: 14px;
  line-height: 1.75;
  white-space: pre-wrap;
  overflow-wrap: anywhere;
}

.user-bubble {
  max-width: min(610px, 85%);
  padding: 12px 16px;
  border-radius: 19px;
  background: var(--bubble);
  font-size: 14px;
  line-height: 1.65;
  white-space: pre-wrap;
  overflow-wrap: anywhere;
}

.message-actions {
  margin-top: 9px;
}

.copy-button {
  padding: 5px 8px;
  border: 0;
  border-radius: 7px;
  background: transparent;
  color: var(--muted);
  font-size: 12px;
}

.copy-button:hover {
  background: #f0f2f5;
}

.typing {
  padding: 5px 0;
  color: var(--muted);
  font-size: 13px;
}

/* FIXED CHAT INPUT */

.composer-area {
  flex: 0 0 auto;
  position: relative;
  z-index: 2;
  padding: 11px 18px 13px;
  background: white;
  border-top: 1px solid #f0f1f3;
}

.composer {
  max-width: 790px;
  margin: 0 auto;
  padding: 12px 13px 9px 17px;
  border: 1px solid #dfe2e7;
  border-radius: 24px;
  background: white;
  box-shadow: 0 4px 18px #00000008;
}

.composer:focus-within {
  border-color: #c2cbed;
}

.composer textarea {
  display: block;
  width: 100%;
  min-height: 29px;
  max-height: 140px;
  resize: none;
  overflow-y: auto;
  border: 0;
  outline: 0;
  background: transparent;
  color: var(--text);
  font-size: 14px;
  line-height: 1.55;
}

.composer textarea::placeholder {
  color: #858b95;
}

.composer-bottom {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 8px;
  margin-top: 8px;
}

.tools {
  display: flex;
  gap: 6px;
  align-items: center;
}

.tool-button {
  padding: 7px 8px;
  border: 0;
  border-radius: 8px;
  background: transparent;
  color: #6f7680;
  font-size: 12px;
}

.tool-button:hover {
  background: #f2f4f7;
}

.send-button {
  width: 36px;
  height: 36px;
  flex-shrink: 0;
  display: grid;
  place-items: center;
  border: 0;
  border-radius: 50%;
  background: #242832;
  color: white;
  font-size: 21px;
}

.send-button:disabled {
  background: #c8cbd0;
  cursor: not-allowed;
}

.disclaimer {
  max-width: 790px;
  margin: 8px auto 0;
  color: #969ba3;
  text-align: center;
  font-size: 10px;
  line-height: 1.5;
}

.hidden {
  display: none !important;
}

.overlay {
  display: none;
}

@media (max-width: 760px) {
  .sidebar {
    position: fixed;
    z-index: 30;
    inset: 0 auto 0 0;
    width: 275px;
    transform: translateX(-105%);
    transition: transform .2s;
    box-shadow: 8px 0 30px #00000012;
  }

  .sidebar.open {
    transform: translateX(0);
  }

  .overlay.show {
    display: block;
    position: fixed;
    z-index: 29;
    inset: 0;
    background: #00000055;
  }

  .menu-button {
    display: block;
  }

  .header {
    height: 42px;
    min-height: 42px;
    padding: 0 12px;
  }

  .chat-area {
    padding: 18px 13px;
  }

  .welcome {
    margin-top: 7vh;
  }

  .suggestions {
    grid-template-columns: 1fr;
    gap: 8px;
    margin-top: 24px;
  }

  .suggestion {
    min-height: 68px;
    padding: 12px 14px;
  }

  .composer-area {
    padding: 8px 10px 10px;
  }

  .composer {
    padding: 10px 10px 8px 13px;
  }

  .messages {
    gap: 20px;
  }
}
</style>
</head>

<body>
<div class="app">

  <aside class="sidebar" id="sidebar">

    <div class="brand">
      <div class="logo">UG</div>
      <div>Ultra <span>Goal</span></div>
    </div>

    <!-- The first New Chat button is always visible here -->
    <button class="new-chat" id="newChat" type="button">
      <span class="plus">＋</span>
      <span>New Chat</span>
    </button>

    <div class="section-title">Recent chats</div>

    <div class="history" id="history"></div>

    <div class="sidebar-bottom">
      Ultra Goal · Learning Demo<br>
      Dream big. Build smart.
    </div>

  </aside>

  <div class="overlay" id="overlay"></div>

  <main class="main">

    <!-- Clean header, no duplicate New Chat button -->
    <header class="header">
      <button
        class="menu-button"
        id="menuButton"
        type="button"
        aria-label="Open menu"
      >☰</button>
    </header>

    <!-- Only this area scrolls -->
    <section class="chat-area" id="chatArea">

      <div class="welcome" id="welcome">

        <div class="welcome-logo">UG</div>

        <h1>
          What can I help you
          <span class="gradient-text">build?</span>
        </h1>

        <p>
          Explore AI, learn Python, and discover robotics.
          Ask a question or choose a starter prompt below.
        </p>

        <div class="suggestions">

          <button
            class="suggestion"
            data-prompt="Teach me Python basics with a simple example."
            type="button"
          >
            <strong>💻 Learn Python</strong>
            <small>Understand coding step by step</small>
          </button>

          <button
            class="suggestion"
            data-prompt="Explain artificial intelligence in simple Kannada and English."
            type="button"
          >
            <strong>🧠 Explore AI</strong>
            <small>Learn how artificial intelligence works</small>
          </button>

          <button
            class="suggestion"
            data-prompt="Give me a beginner robotics project I can simulate for free."
            type="button"
          >
            <strong>🤖 Start Robotics</strong>
            <small>Explore a beginner-friendly project</small>
          </button>

          <button
            class="suggestion"
            data-prompt="Help me plan a useful AI startup with a zero budget."
            type="button"
          >
            <strong>🚀 Build a Startup</strong>
            <small>Turn an idea into a practical project</small>
          </button>

        </div>
      </div>

      <div class="messages hidden" id="messages" aria-live="polite"></div>

    </section>

    <!-- Composer stays in the same place while messages scroll -->
    <footer class="composer-area">

      <form class="composer" id="chatForm">

        <textarea
          id="prompt"
          rows="1"
          maxlength="8000"
          placeholder="Message Ultra Goal..."
          aria-label="Message Ultra Goal"
        ></textarea>

        <div class="composer-bottom">

          <div class="tools">
            <button
              class="tool-button"
              id="modeButton"
              type="button"
            >✧ Learning mode</button>

            <button
              class="tool-button"
              id="clearButton"
              type="button"
            >Clear</button>
          </div>

          <button
            class="send-button"
            id="sendButton"
            type="submit"
            aria-label="Send message"
            title="Send message"
            disabled
          >↑</button>

        </div>
      </form>

      <div class="disclaimer">
        Ultra Goal is currently a demo interface with sample responses.
      </div>

    </footer>

  </main>
</div>

<script>
const $ = id => document.getElementById(id);

const STORAGE_KEY = "ultraGoalChatsV3";

let chats = [];
let activeChatId = null;
let learningMode = true;

const textarea = $("prompt");
const sendButton = $("sendButton");

function createId() {
  return Date.now().toString(36) +
    Math.random().toString(36).slice(2);
}

function getActiveChat() {
  return chats.find(chat => chat.id === activeChatId) || null;
}

function saveChats() {
  try {
    localStorage.setItem(
      STORAGE_KEY,
      JSON.stringify(chats.slice(0, 40))
    );
  } catch (error) {
    console.warn("Unable to save chat history.", error);
  }
}

function renderHistory() {
  const history = $("history");
  history.replaceChildren();

  if (chats.length === 0) {
    const empty = document.createElement("div");
    empty.className = "sidebar-bottom";
    empty.textContent = "Your chats will appear here.";
    history.appendChild(empty);
    return;
  }

  chats.forEach(chat => {
    const button = document.createElement("button");

    button.type = "button";
    button.className =
      "history-item" +
      (chat.id === activeChatId ? " active" : "");

    button.textContent = chat.title || "New Chat";
    button.title = button.textContent;

    button.addEventListener("click", () => {
      showChat(chat.id);
    });

    history.appendChild(button);
  });
}

function showWelcome() {
  $("welcome").classList.remove("hidden");
  $("messages").classList.add("hidden");
  $("messages").replaceChildren();
  $("chatArea").scrollTop = 0;
}

function newChat() {
  const chat = {
    id: createId(),
    title: "New Chat",
    messages: []
  };

  chats.unshift(chat);
  activeChatId = chat.id;

  saveChats();
  renderHistory();
  showWelcome();

  textarea.value = "";
  resizeTextarea();
  closeSidebar();
  textarea.focus();
}

function showChat(id) {
  const chat = chats.find(item => item.id === id);
  if (!chat) return;

  activeChatId = id;

  $("welcome").classList.add("hidden");
  $("messages").classList.remove("hidden");
  $("messages").replaceChildren();

  chat.messages.forEach(message => {
    appendMessage(
      message.role,
      message.text,
      message.role === "assistant"
    );
  });

  renderHistory();
  scrollToBottom();
  closeSidebar();
}

function appendMessage(role, text, showCopy = false) {
  const row = document.createElement("div");
  row.className = "message " + role;

  if (role === "user") {
    const bubble = document.createElement("div");
    bubble.className = "user-bubble";
    bubble.textContent = text;
    row.appendChild(bubble);
  } else {
    const logo = document.createElement("div");
    logo.className = "message-logo";
    logo.textContent = "UG";

    const body = document.createElement("div");
    body.className = "message-body";

    const answer = document.createElement("div");
    answer.textContent = text;
    body.appendChild(answer);

    if (showCopy) {
      const actions = document.createElement("div");
      actions.className = "message-actions";

      const copy = document.createElement("button");
      copy.className = "copy-button";
      copy.type = "button";
      copy.textContent = "Copy";

      copy.addEventListener("click", async () => {
        try {
          if (navigator.clipboard && window.isSecureContext) {
            await navigator.clipboard.writeText(text);
          } else {
            const temp = document.createElement("textarea");
            temp.value = text;
            temp.style.position = "fixed";
            temp.style.opacity = "0";
            document.body.appendChild(temp);
            temp.select();
            document.execCommand("copy");
            temp.remove();
          }

          copy.textContent = "Copied";
        } catch (error) {
          copy.textContent = "Copy failed";
        }
      });

      actions.appendChild(copy);
      body.appendChild(actions);
    }

    row.append(logo, body);
  }

  $("messages").appendChild(row);
}

function sendMessage(messageText) {
  const text = (messageText ?? textarea.value).trim();

  if (!text) {
    textarea.focus();
    return;
  }

  let chat = getActiveChat();

  if (!chat) {
    chat = {
      id: createId(),
      title: text.slice(0, 36),
      messages: []
    };

    chats.unshift(chat);
    activeChatId = chat.id;
  }

  if (
    chat.messages.length === 0 ||
    chat.title === "New Chat"
  ) {
    chat.title = text.slice(0, 36);
  }

  chat.messages.push({
    role: "user",
    text
  });

  saveChats();
  renderHistory();

  $("welcome").classList.add("hidden");
  $("messages").classList.remove("hidden");
  $("messages").replaceChildren();

  chat.messages.forEach(message => {
    appendMessage(
      message.role,
      message.text,
      message.role === "assistant"
    );
  });

  textarea.value = "";
  resizeTextarea();

  const chatId = chat.id;

  const typingRow = document.createElement("div");
  typingRow.className = "message assistant";
  typingRow.dataset.typingFor = chatId;

  const logo = document.createElement("div");
  logo.className = "message-logo";
  logo.textContent = "UG";

  const typingText = document.createElement("div");
  typingText.className = "typing";
  typingText.textContent = "UG is preparing a demo response...";

  typingRow.append(logo, typingText);
  $("messages").appendChild(typingRow);

  scrollToBottom();

  setTimeout(() => {
    const targetChat = chats.find(item => item.id === chatId);
    if (!targetChat) return;

    const answer = getSampleAnswer(text);

    targetChat.messages.push({
      role: "assistant",
      text: answer
    });

    saveChats();

    if (activeChatId === chatId) {
      const indicator = $("messages").querySelector(
        '[data-typing-for="' + chatId + '"]'
      );

      if (indicator) indicator.remove();

      appendMessage("assistant", answer, true);
      scrollToBottom();
    }
  }, 450);
}

function getSampleAnswer(text) {
  const query = text.toLowerCase();

  if (/python|coding|program|code/.test(query)) {
    return `Let's learn Python step by step.

Example:

name = input("Enter your name: ")
print("Welcome to Ultra Goal,", name)

Explanation:
1. input() asks the user to enter information.
2. name stores the entered text.
3. print() displays the welcome message.

Try changing the message and running the code in a Python editor.

This is a demo response, not a live AI-generated answer.`;
  }

  if (/robot|sensor|motor|simulation/.test(query)) {
    return `Beginner robotics project: Virtual obstacle-avoiding robot.

Steps:
1. Create a simple robot in a simulator.
2. Give it forward, left, right and stop actions.
3. Add a simulated obstacle.
4. Make the robot turn when its path is blocked.
5. Test it with obstacles in different positions.

You can begin by simulating the logic before buying any hardware.`;
  }

  if (/startup|business|company|budget|₹0/.test(query)) {
    return `A practical first startup project is a beginner learning assistant.

Problem:
Students often struggle to understand programming concepts.

Possible first version:
1. Choose one Python topic.
2. Explain it in simple language.
3. Show a short example.
4. Give the learner a small practice task.
5. Ask a few students to test it and share feedback.

Start small and use free tools. Check the terms and limits of any services you use.

This demo is not connected to a live AI service.`;
  }

  if (/kannada|ಕನ್ನಡ/.test(query)) {
    return `Artificial Intelligence (AI) ಅಂದರೆ computers ಮೂಲಕ learning, patterns ಗುರುತಿಸುವುದು ಮತ್ತು language ಅರ್ಥಮಾಡಿಕೊಳ್ಳುವಂತಹ ಕೆಲಸಗಳನ್ನು ಮಾಡಲು ಬಳಸುವ technology.

ಉದಾಹರಣೆ:
Machine Learning ನಲ್ಲಿ computer examples ಮೂಲಕ patterns ಕಲಿಯಬಹುದು.

Robotics ಎಂದರೆ software, sensors ಮತ್ತು machines ಅನ್ನು ಸೇರಿಸಿ ಕೆಲಸ ಮಾಡಿಸುವ ಕ್ಷೇತ್ರ.

ನೀವು ಯಾವ topic ಕಲಿಯಲು ಬಯಸುತ್ತೀರಿ ಎಂದು ಹೇಳಿ. ಈ website ಈಗ demo mode‌ನಲ್ಲಿದೆ.`;
  }

  if (/hello|hi|hey|namaste/.test(query)) {
    return `Hello! Welcome to Ultra Goal (UG).

You can explore:
• Python programming
• Artificial Intelligence
• Machine Learning
• Beginner robotics
• Technology startup ideas

What would you like to learn today?`;
  }

  return `Thanks for your question!

Ultra Goal is currently a front-end chat demo. It can show sample guidance about Python, AI, robotics and startup planning, but it is not connected to a live AI model yet.

To generate real AI responses, this project needs an AI service and a secure backend.`;
}

function resizeTextarea() {
  textarea.style.height = "auto";
  textarea.style.height =
    Math.min(textarea.scrollHeight, 140) + "px";

  sendButton.disabled = !textarea.value.trim();
}

function scrollToBottom() {
  $("chatArea").scrollTop = $("chatArea").scrollHeight;
}

function closeSidebar() {
  $("sidebar").classList.remove("open");
  $("overlay").classList.remove("show");
}

function loadChats() {
  try {
    const stored = JSON.parse(
      localStorage.getItem(STORAGE_KEY) || "[]"
    );

    chats = Array.isArray(stored) ? stored : [];
  } catch (error) {
    chats = [];
  }

  if (chats.length > 0) {
    showChat(chats[0].id);
  } else {
    activeChatId = null;
    showWelcome();
    renderHistory();
  }
}

/* EVENTS */

$("chatForm").addEventListener("submit", event => {
  event.preventDefault();
  sendMessage();
});

textarea.addEventListener("input", resizeTextarea);

textarea.addEventListener("keydown", event => {
  if (
    event.key === "Enter" &&
    !event.shiftKey &&
    !event.isComposing
  ) {
    event.preventDefault();
    sendMessage();
  }
});

$("newChat").addEventListener("click", newChat);

$("clearButton").addEventListener("click", () => {
  textarea.value = "";
  resizeTextarea();
  textarea.focus();
});

document.querySelectorAll("[data-prompt]").forEach(button => {
  button.addEventListener("click", () => {
    sendMessage(button.dataset.prompt);
  });
});

$("menuButton").addEventListener("click", () => {
  $("sidebar").classList.add("open");
  $("overlay").classList.add("show");
});

$("overlay").addEventListener("click", closeSidebar);

$("modeButton").addEventListener("click", () => {
  learningMode = !learningMode;

  $("modeButton").textContent = learningMode
    ? "✧ Learning mode"
    : "✧ General mode";

  textarea.placeholder = learningMode
    ? "Ask about AI, Python or robotics..."
    : "Message Ultra Goal...";
});

loadChats();
resizeTextarea();
</script>

</body>
</html>
