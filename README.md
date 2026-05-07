
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Happy Birthday Maria 🎂</title>
<link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Nunito:wght@400;700;900&display=swap" rel="stylesheet"/>
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html,body{width:100%;height:100%;overflow:hidden;font-family:'Nunito',sans-serif}

.page{position:fixed;inset:0;display:none;align-items:center;justify-content:center;}
.page.active{display:flex}

/* PAGE 1 */
#page1{
  background:url('https://i.imgur.com/W3tBmxd.jpg') center top / cover no-repeat;
  flex-direction:column;text-align:center;
}
#page1::after{
  content:'';position:absolute;inset:0;
  background:linear-gradient(to bottom,rgba(10,4,30,0.35) 0%,rgba(10,4,30,0.72) 100%);
}
.p1-content{position:relative;z-index:2;display:flex;flex-direction:column;align-items:center;padding:2rem;}
.gift-icon{font-size:clamp(5rem,18vw,9rem);animation:float 3s ease-in-out infinite;cursor:pointer;filter:drop-shadow(0 0 30px rgba(255,200,80,0.9));transition:transform 0.15s;user-select:none;}
.gift-icon:hover{transform:scale(1.1) rotate(-4deg);}
.gift-icon:active{transform:scale(0.9);}
@keyframes float{0%,100%{transform:translateY(0)}50%{transform:translateY(-18px)}}
.tease{color:#fff;font-size:clamp(1rem,3vw,1.4rem);font-weight:700;margin-top:1.2rem;text-shadow:0 2px 12px rgba(0,0,0,0.7);}
.hint{color:rgba(255,255,255,0.6);font-size:0.9rem;margin-top:0.5rem;}

.photo-strip{position:absolute;bottom:1.5rem;left:50%;transform:translateX(-50%);display:flex;gap:1rem;z-index:2;}
.photo-frame{width:68px;height:68px;border-radius:50%;border:3px solid rgba(255,224,75,0.9);overflow:hidden;box-shadow:0 0 20px rgba(255,110,180,0.6);}
.photo-frame img{width:100%;height:100%;object-fit:cover;object-position:top;}

/* OVERLAY */
#overlay{position:fixed;inset:0;background:rgba(8,3,25,0.88);backdrop-filter:blur(6px);z-index:20;display:none;opacity:0;transition:opacity 0.4s;align-items:center;justify-content:center;}
#overlay.show{display:flex}
#overlay.visible{opacity:1}

/* POPUP */
.popup{
  position:relative;
  background:linear-gradient(145deg,#1e0a3c,#2d0f5a 50%,#1a0a3c);
  border:3px solid rgba(255,255,255,0.15);
  border-radius:28px;padding:2.2rem 2rem 2rem;
  max-width:520px;width:90%;text-align:center;
  box-shadow:0 0 80px rgba(201,184,255,0.3),0 30px 80px rgba(0,0,0,0.5);
  transform:scale(0.5) translateY(80px);
  transition:transform 0.55s cubic-bezier(0.175,0.885,0.32,1.275);
  overflow:hidden;
}
.popup.popped{transform:scale(1) translateY(0)}
.popup-glow{position:absolute;inset:-40px;background:radial-gradient(circle at 50%,rgba(255,110,180,0.15),transparent 70%);pointer-events:none;animation:glowP 3s ease-in-out infinite;}
@keyframes glowP{0%,100%{opacity:0.6}50%{opacity:1}}

.popup-photos{display:flex;gap:0.8rem;justify-content:center;margin-bottom:1rem;}
.pp{width:90px;height:90px;border-radius:16px;overflow:hidden;border:3px solid rgba(255,224,75,0.8);box-shadow:0 4px 20px rgba(255,110,180,0.4);}
.pp:nth-child(1){transform:rotate(-4deg);}
.pp:nth-child(2){transform:rotate(3deg);margin-top:-8px;}
.pp img{width:100%;height:100%;object-fit:cover;object-position:top;}

.cake{font-size:3.5rem;display:block;animation:cakeB 1s 0.6s cubic-bezier(0.36,0.07,0.19,0.97) both;filter:drop-shadow(0 0 16px rgba(255,224,75,0.8));}
@keyframes cakeB{0%{transform:scale(0) rotate(-15deg)}60%{transform:scale(1.3) rotate(8deg)}80%{transform:scale(0.9)}100%{transform:scale(1)}}
.hbd{font-family:'Pacifico',cursive;font-size:clamp(1.6rem,6vw,2.6rem);background:linear-gradient(135deg,#FFE04B,#FF6EB4,#C9B8FF,#3DFFC0);background-size:300%;-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;animation:titleS 0.7s 0.9s ease both,shimmer 4s 1.5s linear infinite;margin:0.3rem 0;}
@keyframes titleS{from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:translateY(0)}}
@keyframes shimmer{0%{background-position:0%}100%{background-position:300%}}
.fname{font-family:'Pacifico',cursive;font-size:clamp(2.5rem,9vw,3.8rem);color:#FFE04B;text-shadow:0 0 30px rgba(255,224,75,0.7),0 0 60px rgba(255,110,180,0.4);animation:nameR 0.8s 1.1s ease both;display:block;}
@keyframes nameR{from{opacity:0;letter-spacing:10px}to{opacity:1;letter-spacing:normal}}
.pmsg{color:rgba(255,255,255,0.82);font-size:0.95rem;line-height:1.7;margin:1rem 0 1.5rem;animation:fadeU 0.6s 1.6s ease both;}
@keyframes fadeU{from{opacity:0;transform:translateY(15px)}to{opacity:1;transform:translateY(0)}}
.close-btn{background:linear-gradient(135deg,#FF6EB4,#FF5F5F);color:#fff;border:none;padding:0.7rem 2rem;border-radius:100px;font-family:'Nunito',sans-serif;font-size:1rem;font-weight:900;cursor:pointer;box-shadow:0 6px 20px rgba(255,110,180,0.4);transition:transform 0.2s,box-shadow 0.2s;animation:fadeU 0.6s 1.9s ease both;}
.close-btn:hover{transform:scale(1.06) translateY(-2px);box-shadow:0 10px 28px rgba(255,110,180,0.6)}

/* PAGE 3: QUIZ */
#page3{flex-direction:column;background:linear-gradient(135deg,#1a0a2e,#2d0f5a,#1a0a2e);overflow-y:auto;padding:2rem 1rem;}
.quiz-wrap{max-width:520px;width:100%;text-align:center;}
.quiz-title{font-family:'Pacifico',cursive;font-size:clamp(1.6rem,6vw,2.2rem);color:#FFE04B;text-shadow:0 0 20px rgba(255,224,75,0.5);margin-bottom:0.4rem;}
.quiz-sub{color:rgba(255,255,255,0.55);font-size:0.9rem;margin-bottom:2rem;}
.q-card{background:rgba(255,255,255,0.06);border:1px solid rgba(255,255,255,0.12);border-radius:20px;padding:1.5rem;margin-bottom:1.2rem;text-align:left;}
.q-label{color:rgba(255,255,255,0.45);font-size:0.75rem;font-weight:700;text-transform:uppercase;letter-spacing:1px;margin-bottom:0.4rem;}
.q-text{color:white;font-size:1rem;font-weight:700;margin-bottom:1rem;}
.q-options{display:grid;grid-template-columns:1fr 1fr;gap:0.5rem;}
.q-opt{background:rgba(255,255,255,0.08);border:1px solid rgba(255,255,255,0.15);border-radius:12px;padding:0.6rem 0.8rem;color:rgba(255,255,255,0.75);font-size:0.85rem;font-weight:700;cursor:pointer;transition:all 0.2s;text-align:center;}
.q-opt:hover{background:rgba(255,110,180,0.2);border-color:rgba(255,110,180,0.5);color:white;}
.q-opt.selected{background:linear-gradient(135deg,rgba(255,110,180,0.4),rgba(201,184,255,0.3));border-color:#FF6EB4;color:white;}
.q-input{width:100%;background:rgba(255,255,255,0.08);border:1px solid rgba(255,255,255,0.2);border-radius:12px;padding:0.7rem 1rem;color:white;font-family:'Nunito',sans-serif;font-size:0.9rem;outline:none;resize:none;}
.q-input:focus{border-color:#FF6EB4;background:rgba(255,110,180,0.1);}
.submit-btn{margin-top:2rem;background:linear-gradient(135deg,#FF6EB4,#C9B8FF);color:#1a0a2e;border:none;padding:0.9rem 2.5rem;border-radius:100px;font-family:'Nunito',sans-serif;font-size:1.1rem;font-weight:900;cursor:pointer;box-shadow:0 8px 24px rgba(255,110,180,0.4);transition:transform 0.2s;width:100%;}
.submit-btn:hover{transform:scale(1.03) translateY(-2px);}

/* PAGE 4: RESULT */
#page4{flex-direction:column;background:linear-gradient(135deg,#1a0a2e,#2d0f5a);text-align:center;padding:2rem;}
.result-emoji{font-size:5rem;animation:float 3s ease-in-out infinite;margin-bottom:1rem;}
.result-title{font-family:'Pacifico',cursive;font-size:clamp(2rem,7vw,3rem);color:#FFE04B;text-shadow:0 0 30px rgba(255,224,75,0.6);margin-bottom:0.8rem;}
.result-msg{color:rgba(255,255,255,0.75);font-size:1rem;line-height:1.8;max-width:420px;}
.score-badge{display:inline-block;margin:1.5rem 0;background:linear-gradient(135deg,#FF6EB4,#C9B8FF);color:#1a0a2e;font-family:'Pacifico',cursive;font-size:1.4rem;padding:0.6rem 2rem;border-radius:100px;}
.replay-btn{margin-top:1.5rem;background:transparent;border:2px solid rgba(255,255,255,0.3);color:white;padding:0.6rem 1.8rem;border-radius:100px;font-family:'Nunito',sans-serif;font-weight:700;cursor:pointer;transition:background 0.2s,transform 0.2s;}
.replay-btn:hover{background:rgba(255,255,255,0.1);transform:scale(1.05)}

/* Stars */
.stars{position:fixed;inset:0;pointer-events:none;z-index:1;}
.star{position:absolute;border-radius:50%;background:white;opacity:0;animation:twinkle var(--d,3s) var(--dl,0s) ease-in-out infinite alternate;}
@keyframes twinkle{0%{opacity:0.1}100%{opacity:0.9}}

/* Balloons & Confetti */
#balloons{position:fixed;inset:0;pointer-events:none;z-index:40;overflow:hidden;}
.balloon{position:absolute;bottom:-150px;font-size:var(--s,3rem);animation:rise var(--d,7s) var(--del,0s) ease-in forwards;}
@keyframes rise{0%{bottom:-150px;opacity:1;transform:translateX(0) rotate(var(--t1,0deg))}80%{opacity:1}100%{bottom:110%;opacity:0;transform:translateX(var(--dr,30px)) rotate(var(--t2,5deg))}}
#confetti-canvas{position:fixed;inset:0;pointer-events:none;z-index:50;}
</style>
</head>
<body>

<div class="stars" id="stars"></div>
<div id="balloons"></div>
<canvas id="confetti-canvas"></canvas>

<!-- PAGE 1 -->
<div class="page active" id="page1">
  <div class="p1-content">
    <div class="gift-icon" id="giftBox" onclick="openCard()">🎁</div>
    <p class="tease">Maria has a surprise waiting... 🎀</p>
    <p class="hint">tap the gift to open it ✨</p>
  </div>
  <div class="photo-strip">
    <div class="photo-frame"><img src="https://i.imgur.com/SDBE8Jz.jpg" alt=""/></div>
    <div class="photo-frame"><img src="https://i.imgur.com/W3tBmxd.jpg" alt=""/></div>
  </div>
</div>

<!-- OVERLAY -->
<div id="overlay">
  <div class="popup" id="popup">
    <div class="popup-glow"></div>
    <div class="popup-photos">
      <div class="pp"><img src="https://i.imgur.com/SDBE8Jz.jpg" alt=""/></div>
      <div class="pp"><img src="https://i.imgur.com/W3tBmxd.jpg" alt=""/></div>
    </div>
    <span class="cake">🎂</span>
    <h1 class="hbd">Happy Birthday</h1>
    <span class="fname">Maria! 🎉</span>
    <p class="pmsg">You are absolutely amazing and your smile lights up every room 🌟<br>Wishing you the most beautiful year yet, filled with joy, love, and all your dreams coming true! 💖</p>
    <button class="close-btn" onclick="goToQuiz()">Answer some fun questions! 🎊</button>
  </div>
</div>

<!-- PAGE 3: QUIZ -->
<div class="page" id="page3">
  <div class="quiz-wrap" id="quizWrap"></div>
</div>

<!-- PAGE 4: RESULT -->
<div class="page" id="page4">
  <div class="result-emoji">🎉</div>
  <h2 class="result-title">Happy Birthday, Maria! 🎂</h2>
  <div class="score-badge" id="scoreBadge"></div>
  <p class="result-msg" id="resultMsg"></p>
  <button class="replay-btn" onclick="location.reload()">🔄 Start Over</button>
</div>

<script>
// Stars
const starsEl=document.getElementById('stars');
for(let i=0;i<100;i++){
  const s=document.createElement('div');s.className='star';
  const sz=Math.random()*2.5+1;
  s.style.cssText=`width:${sz}px;height:${sz}px;top:${Math.random()*100}%;left:${Math.random()*100}%;--d:${2+Math.random()*4}s;--dl:${Math.random()*5}s`;
  starsEl.appendChild(s);
}

// Confetti
const canvas=document.getElementById('confetti-canvas');
const ctx=canvas.getContext('2d');
let pieces=[],animId=null;
const colors=['#FF6EB4','#FFE04B','#3DFFC0','#FF5F5F','#C9B8FF','#7DD9FF','#FF9F43','#fff'];
function resizeC(){canvas.width=innerWidth;canvas.height=innerHeight}
resizeC();window.addEventListener('resize',resizeC);
function launchConfetti(burst){
  const n=burst?200:70;
  for(let i=0;i<n;i++) pieces.push({x:Math.random()*canvas.width,y:burst?Math.random()*canvas.height*0.4:-10,w:Math.random()*10+4,h:Math.random()*5+3,color:colors[Math.floor(Math.random()*colors.length)],vx:(Math.random()-0.5)*6,vy:Math.random()*4+2,rot:Math.random()*360,rotV:(Math.random()-0.5)*8,life:1,shape:Math.random()>0.5?'rect':'circle'});
  if(!animId) drawC();
}
function drawC(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  pieces.forEach(p=>{ctx.save();ctx.globalAlpha=p.life;ctx.fillStyle=p.color;ctx.translate(p.x,p.y);ctx.rotate(p.rot*Math.PI/180);p.shape==='circle'?(ctx.beginPath(),ctx.arc(0,0,p.w/2,0,Math.PI*2),ctx.fill()):ctx.fillRect(-p.w/2,-p.h/2,p.w,p.h);ctx.restore();p.x+=p.vx;p.y+=p.vy;p.rot+=p.rotV;p.vy+=0.08;p.vx*=0.99;if(p.y>canvas.height+20)p.life=0;});
  pieces=pieces.filter(p=>p.life>0);
  pieces.length?animId=requestAnimationFrame(drawC):animId=null;
}

// Balloons
const ballEmojis=['🎈','🎈','🎉','🎊','✨','🌟','💖','🥳','🎀'];
function launchBalloons(){
  const c=document.getElementById('balloons');c.innerHTML='';
  for(let i=0;i<25;i++){
    const b=document.createElement('div');b.className='balloon';
    b.textContent=ballEmojis[Math.floor(Math.random()*ballEmojis.length)];
    const s=2.5+Math.random()*2.5,l=Math.random()*100,d=5+Math.random()*6,del=Math.random()*4,dr=(Math.random()-0.5)*120,t1=(Math.random()-0.5)*20,t2=(Math.random()-0.5)*20;
    b.style.cssText=`left:${l}%;--s:${s}rem;--d:${d}s;--del:${del}s;--dr:${dr}px;--t1:${t1}deg;--t2:${t2}deg`;
    c.appendChild(b);
  }
}

// Open card
function openCard(){
  const box=document.getElementById('giftBox');
  box.style.animation='none';box.textContent='💥';
  setTimeout(()=>box.textContent='🎉',200);
  launchBalloons();
  setTimeout(()=>launchConfetti(true),300);
  setTimeout(()=>launchConfetti(),1500);
  const ov=document.getElementById('overlay');
  ov.classList.add('show');
  requestAnimationFrame(()=>{
    ov.classList.add('visible');
    setTimeout(()=>document.getElementById('popup').classList.add('popped'),50);
  });
}

// Quiz
const questions=[
  {type:'mc',q:"How would you describe your perfect birthday celebration?",opts:["🏖️ Beach vibes","🎤 Karaoke night","🍕 Chill with besties","🌍 Travel somewhere new"]},
  {type:'mc',q:"Pick your birthday cake flavour! 🎂",opts:["🍫 Chocolate lava","🍓 Strawberry cream","🍋 Lemon zest","🥭 Mango tropical"]},
  {type:'mc',q:"What's your birthday mood right now? 🥳",opts:["💃 Ready to dance","😊 Grateful & happy","🤩 Feeling like royalty","🥰 Loved & blessed"]},
  {type:'open',q:"What's the #1 thing you wish for this new year of your life? 🌟",placeholder:"Write your wish here..."},
  {type:'mc',q:"Which word best describes YOU? ✨",opts:["🔥 Unstoppable","💡 Creative","❤️ Loving","⚡ Adventurous"]},
  {type:'open',q:"Write a one-sentence message to your future self on your next birthday 🎀",placeholder:"Dear future Maria..."}
];
let answers={};

function buildQuiz(){
  const wrap=document.getElementById('quizWrap');
  let html=`<h2 class="quiz-title">🎂 Maria's Birthday Quiz!</h2><p class="quiz-sub">A little fun just for you 🌟</p>`;
  questions.forEach((q,i)=>{
    html+=`<div class="q-card" id="qcard${i}"><div class="q-label">Question ${i+1}</div><div class="q-text">${q.q}</div>`;
    if(q.type==='mc'){
      html+=`<div class="q-options">`;
      q.opts.forEach((o,j)=>{html+=`<div class="q-opt" onclick="selectOpt(${i},${j},this)">${o}</div>`;});
      html+=`</div>`;
    } else {
      html+=`<textarea class="q-input" rows="3" placeholder="${q.placeholder}" oninput="answers[${i}]=this.value"></textarea>`;
    }
    html+=`</div>`;
  });
  html+=`<button class="submit-btn" onclick="submitQuiz()">See My Results 🎊</button>`;
  wrap.innerHTML=html;
}

function selectOpt(qi,oi,el){
  document.getElementById(`qcard${qi}`).querySelectorAll('.q-opt').forEach(o=>o.classList.remove('selected'));
  el.classList.add('selected');
  answers[qi]=questions[qi].opts[oi];
}

function submitQuiz(){
  if(Object.keys(answers).length<questions.length){alert('Please answer all questions first! 🎀');return;}
  document.getElementById('page3').classList.remove('active');
  document.getElementById('page4').classList.add('active');
  launchBalloons();launchConfetti(true);
  setTimeout(()=>launchConfetti(),1500);
  const wish=answers[3]||'all your dreams';
  const word=answers[4]||'amazing';
  const msg=answers[5]||'Keep shining!';
  document.getElementById('scoreBadge').textContent=`${word} 💖`;
  document.getElementById('resultMsg').innerHTML=`Your wish: <em>"${wish}"</em> 🌟<br><br>To future Maria: <em>"${msg}"</em> 💌<br><br>May every single day this year be as radiant as your smile! ✨`;
}

function goToQuiz(){
  const ov=document.getElementById('overlay');
  ov.classList.remove('visible');
  setTimeout(()=>{
    ov.classList.remove('show');
    document.getElementById('page1').classList.remove('active');
    document.getElementById('page3').classList.add('active');
    buildQuiz();launchConfetti();
  },400);
}
</script>
</body>
</html>
