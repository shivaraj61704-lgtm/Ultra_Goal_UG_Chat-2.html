# Ultra_Goal_UG_Chat-2.html

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ultra Goal | UG AI</title>
<style>
*{box-sizing:border-box}
:root{--bg:#fff;--sidebar:#f4f5f7;--text:#202123;
--muted:#707784;--border:#e3e5e8;--accent:#6758e8}
body.dark{--bg:#17191f;--sidebar:#20232b;--text:#f2f3f7;
--muted:#a5adbb;--border:#353945}
body{margin:0;background:var(--bg);color:var(--text);
font-family:Arial,sans-serif;height:100dvh;overflow:hidden}
.app{display:flex;height:100dvh}
.sidebar{width:260px;background:var(--sidebar);
padding:16px;display:flex;flex-direction:column;
border-right:1px solid var(--border);flex-shrink:0}
.brand{font-size:23px;font-weight:800;padding:12px 5px 22px}
.brand span{color:var(--accent)}
.btn{border:1px solid var(--border);border-radius:12px;
padding:12px;background:var(--bg);color:var(--text);
cursor:pointer;font-size:14px}
.btn:hover,.suggestion:hover{background:var(--sidebar)}
.newchat{text-align:left}
.section{font-size:12px;color:var(--muted);
margin:25px 5px 10px}
.history{overflow:auto;flex:1}
.history button{display:block;width:100%;border:0;
background:transparent;color:var(--text);text-align:left;
padding:11px 8px;border-radius:8px;cursor:pointer;
white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.history button:hover{background:var(--border)}
.profile{border-top:1px solid var(--border);padding-top:14px;
display:flex;align-items:center;gap:10px;font-size:13px}
.avatar{width:35px;height:35px;border-radius:50%;
background:var(--accent);color:white;display:grid;
place-items:center;font-weight:bold}
.main{flex:1;min-width:0;display:flex;flex-direction:column}
.topbar{height:62px;display:flex;align-items:center;
justify-content:space-between;padding:0 20px;
border-bottom:1px solid var(--border)}
.topbar strong{font-size:16px}
.actions{display:flex;gap:8px}
.iconbtn{border:1px solid var(--border);background:var(--bg);
color:var(--text);border-radius:10px;padding:9px 11px;cursor:pointer}
.content{flex:1;overflow:auto;display:flex;flex-direction:column;
align-items:center;padding:35px 20px 20px}
.welcome{width:100%;max-width:760px;margin:auto 0}
.welcome h1{font-size:clamp(28px,5vw,43px);
letter-spacing:-1.4px;margin:0 0 10px}
.gradient{background:linear-gradient(90deg,#6d5ce8,#2999d6);
color:transparent;background-clip:text}
.welcome p{color:var(--muted);margin-bottom:30px}
.suggestions{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));
gap:12px;margin-bottom:20px}
.suggestion{background:var(--bg);border:1px solid var(--border);
color:var(--text);padding:17px;border-radius:15px;
text-align:left;cursor:pointer;line-height:1.5}
.suggestion b{display:block;margin-bottom:5px}
.chat{width:100%;max-width:760px;margin:auto 0}
.message{display:flex;gap:12px;margin:22px 0;line-height:1.65;
white-space:pre-wrap;overflow-wrap:anywhere}
.message .avatar{flex-shrink:0}
.bubble{padding:5px 0;min-width:0}
.user .bubble{background:var(--sidebar);padding:12px 16px;
border-radius:18px;max-width:85%}
.user{justify-content:flex-end}
.user .avatar{display:none}
.composer-wrap{width:100%;padding:12px 20px 8px;
display:flex;flex-direction:column;align-items:center}
.composer{width:100%;max-width:760px;border:1px solid var(--border);
border-radius:24px;padding:10px 12px;display:flex;
gap:10px;align-items:flex-end;box-shadow:0 3px 18px #00000008}
textarea{flex:1;resize:none;max-height:150px;border:0;outline:0;
background:transparent;color:var(--text);font:15px Arial;
padding:10px;min-width:0}
.send{background:var(--accent);color:white;border:0;
border-radius:14px;width:40px;height:40px;cursor:pointer;font-size:19px}
.send:disabled{opacity:.4;cursor:default}
.disclaimer{font-size:11px;color:var(--muted);
text-align:center;padding:8px 12px 12px}
@media(max-width:650px){
 .sidebar{display:none}
 .topbar{height:56px;padding:0 12px}
 .content{padding:24px 16px}
 .composer-wrap{padding:10px 12px 4px}
 .suggestions{grid-template-columns:1fr}
 .suggestion{padding:13px}
 .welcome h1{font-size:31px}
}
</style>
</head>
<body>
<div class="app">
<aside class="sidebar">
  <div class="brand">ULTRA <span>GOAL</span></div>
  <button class="btn newchat" id="newChat">＋ New chat</button>
  <div class="section">RECENT CHATS</div>
  <div class="history" id="history"></div>
  <div class="profile">
    <div class="avatar">UG</div>
    <div><b>Ultra Goal</b><br><span style="color:var(--muted)">AI Workspace Demo</span></div>
  </div>
</aside>

<main class="main">
  <header class="topbar">
    <strong>UG <span style="color:var(--accent)">AI</span></strong>
    <div class="actions">
      <button class="iconbtn" id="theme" title="Toggle theme">◐</button>
      <button class="iconbtn" id="mobileNew">＋ New</button>
    </div>
  </header>

  <section class="content" id="content">
    <div class="welcome" id="welcome">
      <h1><span class="gradient">Hello, Goal Achiever.</span><br>What shall we explore?</h1>
      <p>Ask, learn, create and build your next big idea.</p>
      <div class="suggestions">
        <button class="suggestion" data-prompt="Teach me Python basics with examples.">
          <b>⌨ Learn Python</b>Start coding step by step
        </button>
        <button class="suggestion" data-prompt="Explain artificial intelligence in simple English and Kannada.">
          <b>✦ Explore AI</b>Understand intelligent technology
        </button>
        <button class="suggestion" data-prompt="Help me build a beginner robotics simulation in Python.">
          <b>🤖 Build a robot</b>Explore robotics concepts
        </button>
        <button class="suggestion" data-prompt="Help me plan a startup with zero budget.">
          <b>🚀 Startup ideas</b>Turn a problem into a project
        </button>
      </div>
    </div>
    <div class="chat" id="chat" hidden></div>
  </section>

  <div class="composer-wrap">
    <form class="composer" id="form">
      <textarea id="input" rows="1" placeholder="Message Ultra Goal..." aria-label="Message Ultra Goal"></textarea>
      <button class="send" id="send" type="submit" aria-label="Send message">↑</button>
    </form>
    <div class="disclaimer">UG AI Demo can make mistakes. Verify important information.</div>
  </div>
</main>
</div>

<script>
const $ = id => document.getElementById(id);
let conversations = [];
let current = [];
let chatCount = 0;

function escapeHTML(text){
  return text.replace(/[&<>"']/g, c => ({
    '&':'&amp;','<':'&lt;','>':'&gt;',
    '"':'&quot;',"'":'&#39;'
  })[c]);
}

function newChat(){
  current = [];
  $('chat').innerHTML = '';
  $('chat').hidden = true;
  $('welcome').hidden = false;
  $('input').value = '';
  $('input').focus();
}

function addMessage(role,text){
  $('welcome').hidden = true;
  $('chat').hidden = false;
  const row = document.createElement('div');
  row.className = 'message ' + role;
  const avatar = role === 'assistant'
    ? '<div class="avatar">UG</div>' : '<div class="avatar"></div>';
  row.innerHTML = avatar +
    '<div class="bubble">' + escapeHTML(text) + '</div>';
  $('chat').appendChild(row);
  $('content').scrollTop = $('content').scrollHeight;
}

function demoReply(text){
  const q = text.toLowerCase();
  if(q.includes('python') || q.includes('code')){
    return 'Let’s learn Python step by step!\\n\\nExample:\\nname = input("Your name: ")\\nprint("Hello", name)\\n\\ninput() receives text from the user, and print() displays a message. Try changing the code and running it in Python.\\n\\nNote: UG is currently a demo, so I generate sample responses rather than using a live AI model.';
  }
  if(q.includes('robot')){
    return 'Robotics combines programming, sensors, control systems and mechanical design.\\n\\nBeginner project: simulate a robot that moves forward and turns when it detects an obstacle. You can start with Python logic before buying any hardware.\\n\\nThis is a sample UG response, not a live AI answer.';
  }
  if(q.includes('startup') || q.includes('business')){
    return 'A good startup begins by solving a real problem.\\n\\n1. Identify one group of people and a problem they face.\\n2. Interview a few potential users.\\n3. Build the smallest useful prototype.\\n4. Test it and improve it from feedback.\\n\\nWith ₹0, start with free tools and software prototypes. This is a sample response from UG Demo.';
  }
  if(q.includes('ai') || q.includes('artificial intelligence')){
    return 'Artificial Intelligence (AI) is a field of computing that builds systems able to perform tasks such as recognising patterns, understanding language and making predictions.\\n\\nMachine learning is one approach to AI: a model learns patterns from data.\\n\\nThis UG version uses sample responses. Connect a real AI service to get open-ended answers.';
  }
  return 'Thanks for trying Ultra Goal! 🚀\\n\\nI’m currently running in Demo Mode, so I can respond to a few topics with sample answers. I’m not connected to ChatGPT, Gemini, or another live AI model yet.\\n\\nNext step: connect a real AI model through a secure backend.';
}

function sendMessage(text){
  text = text.trim();
  if(!text) return;
  if(current.length===0) chatCount++;
  current.push({role:'user',text});
  addMessage('user',text);
  $('input').value='';
  $('input').style.height='auto';
  $('send').disabled=true;
  const reply = demoReply(text);
  setTimeout(()=>{
    current.push({role:'assistant',text:reply});
    addMessage('assistant',reply);
    $('send').disabled=false;
    updateHistory(text);
  },350);
}

function updateHistory(title){
  const item = document.createElement('button');
  item.textContent = title;
  item.title = title;
  item.addEventListener('click',()=>{
    $('chat').innerHTML='';
    $('welcome').hidden=true;
    $('chat').hidden=false;
    current.forEach(m=>addMessage(m.role,m.text));
  });
  $('history').prepend(item);
}

$('form').addEventListener('submit',e=>{
  e.preventDefault();
  sendMessage($('input').value);
});
$('input').addEventListener('keydown',e=>{
  if(e.key==='Enter'&&!e.shiftKey){
    e.preventDefault();
    $('form').requestSubmit();
  }
});
$('input').addEventListener('input',()=>{
  $('input').style.height='auto';
  $('input').style.height=Math.min($('input').scrollHeight,150)+'px';
});
$('newChat').addEventListener('click',newChat);
$('mobileNew').addEventListener('click',newChat);
$('theme').addEventListener('click',()=>document.body.classList.toggle('dark'));
document.querySelectorAll('[data-prompt]').forEach(btn=>{
  btn.addEventListener('click',()=>sendMessage(btn.dataset.prompt));
});
</script>
</body>
</html>
