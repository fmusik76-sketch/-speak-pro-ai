<!DOCTYPE html>
<html lang="uz">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover">
<meta name="theme-color" content="#1d3044">
<title>Speak Pro AI</title>

<style>
*{
  box-sizing:border-box;
  margin:0;
  padding:0;
  -webkit-tap-highlight-color:transparent;
}

:root{
  --accent:#ff3e38;
  --accentSoft:#fff0ef;
  --ink:#10192e;
  --muted:#6f7b92;
  --paper:#fff;
  --page:#f7f5ef;
}

body{
  font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Arial,sans-serif;
  background:#000;
  color:var(--ink);
}

button{
  font:inherit;
  cursor:pointer;
}

.app{
  width:100%;
  max-width:760px;
  min-height:100vh;
  margin:auto;
  background:var(--page);
  overflow:hidden;
}

/* TOP */

.top{
  position:sticky;
  top:0;
  z-index:100;
  height:112px;
  background:#203449;
  color:white;
  display:flex;
  align-items:center;
  justify-content:center;
  text-align:center;
  box-shadow:0 4px 15px rgba(0,0,0,.12);
}

.top h1{
  font-size:25px;
  font-weight:850;
}

.top p{
  color:#aab4c2;
  font-size:13px;
  margin-top:3px;
}

.top-left,
.top-right{
  position:absolute;
  top:50%;
  transform:translateY(-50%);
}

.top-left{
  left:22px;
  color:#34a8ff;
  font-size:18px;
}

.top-right{
  right:22px;
  color:#34a8ff;
  font-size:29px;
}

/* PERSONA PAGE */

.home{
  padding-bottom:35px;
}

.home-title{
  padding:26px 24px 14px;
}

.home-title h2{
  font-size:30px;
  margin-bottom:8px;
}

.home-title p{
  color:var(--muted);
  line-height:1.5;
}

.personas{
  padding:8px 16px 30px;
}

.card{
  --c:#2d68ee;
  --soft:#eef4ff;

  background:#fff;
  border:2px solid color-mix(in srgb,var(--c) 28%, white);
  border-radius:32px;
  padding:23px;
  margin-bottom:22px;
  box-shadow:0 12px 35px rgba(30,38,60,.06);
}

.card-top{
  display:flex;
  gap:18px;
  align-items:center;
}

.bot-mini{
  width:112px;
  min-width:112px;
  height:112px;
  border-radius:27px;
  border:5px solid var(--c);
  background:#faf8f0;
  display:flex;
  align-items:center;
  justify-content:center;
  font-size:47px;
  position:relative;
  overflow:hidden;
}

.bot-mini::after{
  content:"SPEAK PRO";
  position:absolute;
  left:0;
  right:0;
  bottom:0;
  padding:6px 2px;
  color:#fff;
  background:var(--c);
  font-size:10px;
  font-weight:900;
  text-align:center;
  letter-spacing:.4px;
}

.card-tag{
  color:var(--c);
  font-size:13px;
  font-weight:900;
  letter-spacing:2px;
}

.card-name{
  font-size:31px;
  line-height:1.06;
  font-weight:900;
  margin-top:7px;
}

.card-badge{
  display:inline-block;
  background:var(--soft);
  color:var(--c);
  border:1px solid color-mix(in srgb,var(--c) 35%,white);
  padding:7px 11px;
  border-radius:999px;
  font-size:12px;
  font-weight:900;
  margin-top:10px;
}

.line{
  height:1px;
  background:#edf0f5;
  margin:22px 0;
}

.desc{
  color:#56637a;
  font-size:17px;
  line-height:1.55;
}

.voice-title{
  color:#a2aec0;
  font-size:13px;
  font-weight:900;
  letter-spacing:1.5px;
  margin-top:22px;
}

.voice-grid{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:12px;
  margin-top:10px;
}

.voice{
  padding:14px;
  border:2px solid #e1e6ee;
  border-radius:19px;
  background:#f8f9fb;
  display:flex;
  align-items:center;
  gap:10px;
  color:#344158;
  text-align:left;
}

.voice.active{
  background:#0d1730;
  color:white;
  border-color:#0d1730;
}

.voice .e{
  font-size:29px;
}

.voice b{
  display:block;
}

.voice small{
  display:block;
  opacity:.7;
  margin-top:2px;
}

.start{
  width:100%;
  margin-top:18px;
  border:none;
  border-radius:22px;
  padding:18px;
  color:#fff;
  background:var(--c);
  font-weight:900;
  font-size:18px;
  box-shadow:0 10px 22px color-mix(in srgb,var(--c) 25%,transparent);
}

/* SPEAKING */

.speaking{
  display:none;
  background:var(--page);
  min-height:100vh;
}

.speaking.show{
  display:block;
}

.speaking-content{
  padding:28px 16px 38px;
}

.back-pill{
  display:inline-flex;
  align-items:center;
  gap:9px;
  border:1px solid #e4e7ec;
  background:#fff;
  color:#4b566c;
  border-radius:18px;
  padding:11px 16px;
  font-weight:850;
  box-shadow:0 5px 15px rgba(20,30,50,.07);
}

.meta{
  margin-top:20px;
  padding:13px 16px;
  background:#fff;
  border:1px solid #e7e9ef;
  border-radius:20px;
  display:flex;
  gap:8px;
  align-items:center;
  justify-content:center;
  flex-wrap:wrap;
  box-shadow:0 6px 18px rgba(20,30,50,.05);
}

.chip{
  padding:7px 11px;
  border-radius:12px;
  background:#f1f2ff;
  color:#5140bf;
  font-weight:850;
  font-size:12px;
}

.chip.person{
  background:var(--accentSoft);
  color:var(--accent);
}

.stage{
  margin-top:22px;
  background:#fff;
  border-radius:30px;
  padding:30px 24px 26px;
  box-shadow:0 12px 40px rgba(30,35,55,.06);
}

.bot-face{
  width:100%;
  max-width:490px;
  height:230px;
  margin:auto;
  border-radius:95px;
  border:10px solid var(--accent);
  background:#faf8f0;
  position:relative;
  box-shadow:
    0 0 26px color-mix(in srgb,var(--accent) 30%,transparent),
    inset 0 0 0 3px rgba(255,255,255,.8);
  display:flex;
  align-items:center;
  justify-content:center;
  transition:.25s;
}

.bot-face.speaking{
  transform:scale(1.015);
  box-shadow:
    0 0 38px color-mix(in srgb,var(--accent) 55%,transparent),
    inset 0 0 0 3px rgba(255,255,255,.8);
}

.eyes{
  display:flex;
  gap:65px;
  align-items:center;
}

.eye{
  width:47px;
  height:60px;
  border-radius:50%;
  background:#202b40;
  position:relative;
}

.eye::after{
  content:"";
  width:12px;
  height:12px;
  background:#fff;
  border-radius:50%;
  position:absolute;
  right:8px;
  top:9px;
}

.brow{
  position:absolute;
  width:62px;
  height:10px;
  background:#202b40;
  border-radius:99px;
  top:54px;
}

.brow.left{
  left:28%;
  transform:rotate(15deg);
}

.brow.right{
  right:28%;
  transform:rotate(-15deg);
}

.mouth{
  position:absolute;
  width:72px;
  height:12px;
  border-radius:99px;
  background:#202b40;
  bottom:58px;
}

.dots{
  position:absolute;
  bottom:20px;
  display:flex;
  gap:9px;
}

.dot{
  width:10px;
  height:10px;
  border-radius:50%;
  background:color-mix(in srgb,var(--accent) 38%,white);
}

.name-area{
  text-align:center;
  margin-top:26px;
}

.name-area h2{
  font-size:31px;
  line-height:1.1;
}

.name-area h2 span{
  color:var(--accent);
}

.voice-label{
  font-size:15px;
  color:#8a96a9;
  margin-top:9px;
  font-weight:850;
  letter-spacing:1px;
}

.ai-state{
  margin-top:7px;
  font-size:16px;
  color:#4b76e8;
  font-weight:800;
  min-height:24px;
}

.timer{
  margin:16px auto 0;
  width:max-content;
  max-width:100%;
  border:1.5px solid #bdc8ff;
  background:#f3f5ff;
  color:#4d41bc;
  padding:9px 18px;
  border-radius:999px;
  font-family:monospace;
  font-weight:850;
  font-size:15px;
}

.topic-box{
  margin-top:27px;
  padding:18px;
  border-radius:23px;
  background:#f6f3ff;
  border:1.5px solid #d8cbff;
}

.topic-top{
  display:flex;
  align-items:center;
  justify-content:space-between;
  gap:12px;
}

.topic-badge{
  display:inline-block;
  background:#f4dcff;
  color:#7d28a8;
  font-size:12px;
  font-weight:900;
  padding:8px 11px;
  border-radius:15px;
}

.level{
  color:#4c55c2;
  background:#eef1ff;
  border:1px solid #bdc8ff;
  border-radius:18px;
  padding:8px 13px;
  font-size:13px;
  font-weight:900;
}

.topic-box h3{
  font-size:21px;
  margin-top:15px;
}

.topic-box p{
  color:#58667c;
  line-height:1.5;
  margin-top:8px;
}

.word-box{
  margin-top:18px;
  padding:18px;
  border-radius:23px;
  background:#fffcec;
  border:1.5px solid #f0d465;
}

.word-title{
  font-size:13px;
  font-weight:900;
  color:#9a5a0a;
  line-height:1.4;
}

.words{
  display:flex;
  flex-wrap:wrap;
  gap:9px;
  margin-top:14px;
}

.word{
  border:1.5px solid #eba91f;
  background:#fff;
  color:#a25705;
  border-radius:999px;
  padding:8px 12px;
  font-size:13px;
  font-weight:800;
}

.helper-box{
  margin-top:18px;
  padding:18px;
  border-radius:23px;
  background:#f7f8fb;
  border:1.5px solid #dde1ea;
}

.helper-title{
  font-size:13px;
  font-weight:900;
  color:#4b3bc4;
}

.helpers{
  display:flex;
  flex-wrap:wrap;
  gap:10px;
  margin-top:13px;
}

.helper{
  padding:8px 12px;
  border:1.5px solid #bdc8ff;
  background:#fff;
  border-radius:999px;
  color:#3f438a;
  font-size:13px;
  font-weight:800;
}

.mic-wrap{
  text-align:center;
  margin-top:28px;
}

.mic{
  width:108px;
  height:108px;
  border-radius:50%;
  border:8px solid #cbc7ff;
  background:#5144ed;
  color:#fff;
  font-size:48px;
  box-shadow:0 13px 30px rgba(80,67,237,.28);
}

.mic.listening{
  background:#ed1d4b;
  border-color:#ffc0cf;
  animation:pulse 1s infinite;
}

.mic-text{
  color:#78849a;
  margin-top:9px;
  font-size:14px;
  font-weight:750;
}

.finish{
  width:108px;
  height:108px;
  border-radius:50%;
  border:8px solid #ffc5d1;
  background:#ed1d4b;
  color:#fff;
  margin-top:29px;
  font-size:35px;
  box-shadow:0 13px 30px rgba(237,29,75,.22);
}

.finish-text{
  color:#78849a;
  margin-top:9px;
  font-size:14px;
  font-weight:750;
}

.last-answer{
  margin-top:16px;
  color:#6f7a90;
  font-size:12px;
  text-align:center;
  min-height:18px;
}

@keyframes pulse{
  50%{transform:scale(.95)}
}

@media(max-width:520px){
  .top{
    height:104px;
  }

  .card{
    padding:20px;
    border-radius:27px;
  }

  .bot-mini{
    width:90px;
    min-width:90px;
    height:100px;
    font-size:38px;
  }

  .card-name{
    font-size:26px;
  }

  .bot-face{
    height:210px;
    border-width:8px;
  }

  .eyes{
    gap:58px;
  }

  .brow.left{left:24%}
  .brow.right{right:24%}

  .stage{
    padding:24px 16px;
  }
}
</style>
</head>

<body>

<div class="app">

  <header class="top">
    <div class="top-left">Закрыть</div>

    <div>
      <h1>Speak Pro</h1>
      <p>мини-приложение</p>
    </div>

    <div class="top-right">•••</div>
  </header>


  <!-- PERSONA PAGE -->

  <section class="home" id="home">

    <div class="home-title">
      <h2>Speaking Personalar 🎭</h2>
      <p>
        Personani va ovozni tanlang.
        Keyin AI bilan speaking mashqini boshlang.
      </p>
    </div>

    <main class="personas" id="personaList"></main>

  </section>


  <!-- SPEAKING PAGE -->

  <section class="speaking" id="speaking">

    <div class="speaking-content">

      <button class="back-pill" id="backBtn">
        ← Personalar
      </button>


      <div class="meta">

        <div class="chip">
          🇬🇧 English
        </div>

        <div class="chip">
          🎓 Mavzu Suhbat
        </div>

        <div class="chip person" id="metaPersona">
          😤 QATTIQQO‘L
        </div>

      </div>


      <div class="stage">

        <div class="bot-face" id="botFace">

          <div class="brow left"></div>
          <div class="brow right"></div>

          <div class="eyes">

            <div class="eye"></div>
            <div class="eye"></div>

          </div>

          <div class="mouth"></div>

          <div class="dots">
            <div class="dot"></div>
            <div class="dot"></div>
            <div class="dot"></div>
            <div class="dot"></div>
          </div>

        </div>


        <div class="name-area">

          <h2>
            <span id="displayPersona">
              Qattiqqo‘l
            </span>
            Speak Pro
          </h2>

          <div class="voice-label"
               id="displayVoice">
            👨 ERKAK OVOZ
          </div>

          <div class="ai-state"
               id="aiState">
            Boshlash uchun mikrofonni bosing
          </div>

          <div class="timer"
               id="timer">
            ● Suhbat vaqti: 00:00
          </div>

        </div>


        <div class="topic-box">

          <div class="topic-top">

            <div class="topic-badge">
              🎓 MAVZU TUSHUNTIRISH & SUHBAT
            </div>

            <div class="level">
              B1/B2
            </div>

          </div>

          <h3 id="topicTitle">
            🎙️ Free Time
          </h3>

          <p id="topicText">
            Tell me what you usually do in your free time,
            why you enjoy it and how often you do it.
          </p>

        </div>


        <div class="word-box">

          <div class="word-title">
            💎 TAVSIYA ETILADIGAN B2/C1 SO‘ZLAR
          </div>

          <div class="words"
               id="wordList">

            <span class="word">enjoyable</span>
            <span class="word">beneficial</span>
            <span class="word">fascinating</span>
            <span class="word">essential</span>

          </div>

        </div>


        <div class="helper-box">

          <div class="helper-title">
            ⚡ PAUZALAR UCHUN ULOVCHI IBORALAR
          </div>

          <div class="helpers">

            <span class="helper">
              To be honest...
            </span>

            <span class="helper">
              In my opinion...
            </span>

            <span class="helper">
              From my point of view...
            </span>

            <span class="helper">
              That's an interesting question...
            </span>

          </div>

        </div>


        <div class="mic-wrap">

          <button class="mic"
                  id="micBtn">
            🎙
          </button>

          <div class="mic-text"
               id="micText">
            Boshlash uchun bosing
          </div>

        </div>


        <div class="last-answer"
             id="lastAnswer"></div>


        <div class="mic-wrap">

          <button class="finish"
                  id="finishBtn">
            ☎
          </button>

          <div class="finish-text">
            Tugatish uchun bosing
          </div>

        </div>

      </div>

    </div>

  </section>

</div>


<script>

/* ==========================
   PERSONAS
========================== */

const personas = [

{
 id:"strict",
 name:"Qattiqqo‘l",
 label:"QATTIQQO‘L",
 emoji:"😤",
 tag:"KESKIN TANBEH",
 badge:"🔥 QATTIQ",
 color:"#ff3e38",
 soft:"#fff0ef",

 desc:
 "Xatolaringizni ayab o‘tirmaydi. Qattiq gapiradi va aniqroq javob berishingizni talab qiladi.",

 replies:[
  "That answer was too short. Explain your reason clearly.",
  "You can do better. Give me one example.",
  "Stop using very simple words. Try a stronger expression."
 ]
},

{
 id:"demanding",
 name:"Talabchan",
 label:"TALABCHAN",
 emoji:"⭐",
 tag:"PROFESSIONAL",
 badge:"⭐ OMMABOP",
 color:"#2d68ee",
 soft:"#edf4ff",

 desc:
 "Professional murabbiy. Xatolaringizni to‘g‘rilashga va javobni kengaytirishga majbur qiladi.",

 replies:[
  "Good start. Develop your answer with more detail.",
  "Explain why you think so.",
  "Now use a more advanced word in your answer."
 ]
},

{
 id:"funny",
 name:"Hazilkash",
 label:"HAZILKASH",
 emoji:"😂",
 tag:"KULGULI & BEG‘UBOR",
 badge:"😂 YANGI",
 color:"#efa737",
 soft:"#fff7e8",

 desc:
 "Suhbat davomida hazillashadi va stressni kamaytiradi.",

 replies:[
  "Okay 😂 your English survived that sentence. Tell me more!",
  "Not bad 😂 but grammar is asking for help.",
  "Come on, give me a more interesting answer!"
 ]
},

{
 id:"fast",
 name:"Tezkor",
 label:"TEZKOR",
 emoji:"🚀",
 tag:"CHAKKASH & SHIDDATLI",
 badge:"🚀 TEZKOR",
 color:"#4db6d3",
 soft:"#ebfbff",

 desc:
 "Savollarni tez beradi. Tez fikrlash va tez javob qaytarishni mashq qiladi.",

 replies:[
  "Quick! Why?",
  "What happened next?",
  "Give me another example. Fast!"
 ]
},

{
 id:"detective",
 name:"Detektiv",
 label:"DETEKTIV",
 emoji:"🕵️",
 tag:"SIRLI TERGOVCHI",
 badge:"🕵️ TERGOV",
 color:"#8858f5",
 soft:"#f4efff",

 desc:
 "Javobingizdagi detallarni kovlaydi va savollarni chuqurlashtiradi.",

 replies:[
  "Interesting. When exactly did that happen?",
  "Why do you think that?",
  "I need more evidence. Give me a specific example."
 ]
},

{
 id:"motivator",
 name:"Motivator",
 label:"MOTIVATOR",
 emoji:"🏆",
 tag:"CHEMPION TRENER",
 badge:"🏆 CHEMPION",
 color:"#ff7816",
 soft:"#fff1e7",

 desc:
 "Doim qo‘llab-quvvatlaydi va ko‘proq gapirishga motivatsiya beradi.",

 replies:[
  "Great job! Keep going!",
  "Nice answer. You can make it even stronger.",
  "Excellent! Add one more detail."
 ]
},

{
 id:"lazy",
 name:"Erinchoq",
 label:"ERINCHOQ",
 emoji:"🥱",
 tag:"DANGASA IMTIHONCHI",
 badge:"🥱 DANGASA",
 color:"#708099",
 soft:"#f1f4f8",

 desc:
 "Uzun javoblardan zerikadi. Qisqa va mazmunli gapirishni mashq qildiradi.",

 replies:[
  "Hmm... keep it shorter 😴.",
  "Tell me only the important part.",
  "Okay... and your main point is?"
 ]
},

{
 id:"carefree",
 name:"Beparvo",
 label:"BEPARVO",
 emoji:"😎",
 tag:"ERKIN SUHBAT",
 badge:"😎 CHILL",
 color:"#69c80a",
 soft:"#f3ffe8",

 desc:
 "Erkin va norasmiy suhbat qiladi. Kundalik speaking uchun mos.",

 replies:[
  "Cool 😎 tell me more.",
  "Sounds good. What do you enjoy most about it?",
  "Nice. What would you do next?"
 ]
},

{
 id:"calm",
 name:"Sokin",
 label:"SOKIN",
 emoji:"😌",
 tag:"XOTIRJAM",
 badge:"😌 SOKIN",
 color:"#20b99f",
 soft:"#eafffa",

 desc:
 "Shoshirmaydi. Sekin va stresssiz suhbat qilishga yordam beradi.",

 replies:[
  "Good. Take your time.",
  "Can you explain that with one more detail?",
  "Nice. Now say the same idea in another way."
 ]
},

{
 id:"kind",
 name:"Mehribon",
 label:"MEHRIBON",
 emoji:"😊",
 tag:"DO‘STONA",
 badge:"💛 MEHR",
 color:"#e84a9c",
 soft:"#fff0f7",

 desc:
 "Yumshoq va do‘stona suhbat qiladi. Xatolarni qo‘pol tanqid qilmaydi.",

 replies:[
  "Nice answer 😊. Let's make it even better.",
  "Good job. Can you add one more sentence?",
  "You're doing well. Tell me a little more."
 ]
}

];


const topics = [

{
 title:"🎙️ Free Time",
 text:
 "Tell me what you usually do in your free time, why you enjoy it and how often you do it.",

 words:[
  "enjoyable",
  "beneficial",
  "fascinating",
  "essential"
 ]
},

{
 title:"🎙️ Your Hometown",
 text:
 "Describe your hometown. Talk about the people, interesting places and what you like about it.",

 words:[
  "peaceful",
  "crowded",
  "convenient",
  "attractive"
 ]
},

{
 title:"🎙️ Technology",
 text:
 "Explain how technology affects your daily life and whether it makes life easier or more difficult.",

 words:[
  "efficient",
  "innovative",
  "essential",
  "time-consuming"
 ]
}

];


/* ==========================
   CREATE PERSONA CARDS
========================== */

const personaList =
document.getElementById("personaList");

let selectedVoice = {};

personas.forEach(p=>{

 selectedVoice[p.id]="male";

 const card =
 document.createElement("section");

 card.className="card";

 card.style.setProperty("--c",p.color);
 card.style.setProperty("--soft",p.soft);

 card.innerHTML=`

 <div class="card-top">

   <div class="bot-mini">
     ${p.emoji}
   </div>

   <div>

     <div class="card-tag">
       ${p.tag}
     </div>

     <div class="card-name">
       ${p.name}<br>Speak Pro
     </div>

     <div class="card-badge">
       ${p.badge}
     </div>

   </div>

 </div>


 <div class="line"></div>


 <div class="desc">
   ${p.desc}
 </div>


 <div class="voice-title">
   OVOZ TANLANG
 </div>


 <div class="voice-grid">

   <button
   class="voice active"
   data-person="${p.id}"
   data-voice="male">

     <span class="e">
       👨
     </span>

     <span>
       <b>Erkak ovoz</b>
       <small>Male voice</small>
     </span>

   </button>


   <button
   class="voice"
   data-person="${p.id}"
   data-voice="female">

     <span class="e">
       👩
     </span>

     <span>
       <b>Ayol ovoz</b>
       <small>Female voice</small>
     </span>

   </button>

 </div>


 <button
 class="start"
 data-start="${p.id}">

   ${p.emoji}
   ${p.name} bilan Boshlash
   →

 </button>
 `;

 personaList.appendChild(card);

});


document
.querySelectorAll(".voice")
.forEach(btn=>{

 btn.onclick=()=>{

  const id=
  btn.dataset.person;

  document
  .querySelectorAll(
   `.voice[data-person="${id}"]`
  )
  .forEach(x=>
   x.classList.remove("active")
  );

  btn.classList.add("active");

  selectedVoice[id]=
  btn.dataset.voice;

 };

});


/* ==========================
   SPEAKING
========================== */

let activePersona=null;
let activeVoice="male";
let currentTopic=null;

let seconds=0;
let timerInterval=null;
let started=false;

const home=
document.getElementById("home");

const speaking=
document.getElementById("speaking");

const botFace=
document.getElementById("botFace");

const aiState=
document.getElementById("aiState");

const micBtn=
document.getElementById("micBtn");

const micText=
document.getElementById("micText");

const lastAnswer=
document.getElementById("lastAnswer");


document
.querySelectorAll("[data-start]")
.forEach(btn=>{

 btn.onclick=()=>{

  const id=
  btn.dataset.start;

  activePersona=
  personas.find(
   p=>p.id===id
  );

  activeVoice=
  selectedVoice[id];

  openSpeaking();

 };

});


function openSpeaking(){

 document.documentElement.style
 .setProperty(
  "--accent",
  activePersona.color
 );

 document.documentElement.style
 .setProperty(
  "--accentSoft",
  activePersona.soft
 );

 currentTopic=
 topics[
  Math.floor(
   Math.random()*topics.length
  )
 ];

 document
 .getElementById(
  "metaPersona"
 )
 .textContent=
 activePersona.emoji+
 " "+
 activePersona.label;


 document
 .getElementById(
  "displayPersona"
 )
 .textContent=
 activePersona.name;


 document
 .getElementById(
  "displayVoice"
 )
 .textContent=
 activeVoice==="male"
 ? "👨 ERKAK OVOZ"
 : "👩 AYOL OVOZ";


 document
 .getElementById(
  "topicTitle"
 )
 .textContent=
 currentTopic.title;


 document
 .getElementById(
  "topicText"
 )
 .textContent=
 currentTopic.text;


 document
 .getElementById(
  "wordList"
 )
 .innerHTML=
 currentTopic.words
 .map(w=>
  `<span class="word">${w}</span>`
 )
 .join("");


 home.style.display="none";

 speaking.classList.add("show");

 seconds=0;
 started=false;

 updateTimer();

 aiState.textContent=
 "Boshlash uchun mikrofonni bosing";

 lastAnswer.textContent="";

 window.scrollTo(0,0);

}


/* ==========================
   TIMER
========================== */

function startTimer(){

 if(started)return;

 started=true;

 timerInterval=
 setInterval(()=>{

  seconds++;

  updateTimer();

 },1000);

}


function updateTimer(){

 const m=
 String(
  Math.floor(seconds/60)
 )
 .padStart(2,"0");

 const s=
 String(
  seconds%60
 )
 .padStart(2,"0");

 document
 .getElementById(
  "timer"
 )
 .textContent=
 `● Suhbat vaqti: ${m}:${s}`;

}


/* ==========================
   AI DEMO REPLY
========================== */

function getReply(){

 const arr=
 activePersona.replies;

 return arr[
  Math.floor(
   Math.random()*arr.length
  )
 ];

}


/* ==========================
   VOICE
========================== */

function selectVoice(){

 const all=
 speechSynthesis.getVoices();

 const en=
 all.filter(
  v=>
  v.lang &&
  v.lang.toLowerCase()
  .startsWith("en")
 );

 if(!en.length)
 return all[0];


 if(activeVoice==="female"){

  return en.find(v=>
   /samantha|karen|victoria|moira|ava/i
   .test(v.name)
  ) || en[0];

 }

 return en.find(v=>
  /daniel|alex|fred|aaron|male/i
  .test(v.name)
 ) || en[0];

}


function speak(text){

 if(
  !("speechSynthesis" in window)
 )return;


 speechSynthesis.cancel();


 const u=
 new SpeechSynthesisUtterance(text);


 u.lang="en-US";


 const v=
 selectVoice();


 if(v)
 u.voice=v;


 if(
  activePersona.id==="fast"
 )
 u.rate=1.18;

 else if(
  activePersona.id==="calm"
 )
 u.rate=.87;

 else
 u.rate=1;


 u.onstart=()=>{

  botFace
  .classList
  .add("speaking");

  aiState.textContent=
  "AI gapiryapti...";

 };


 u.onend=()=>{

  botFace
  .classList
  .remove("speaking");

  aiState.textContent=
  "Javobingizni kutyapman...";

 };


 speechSynthesis.speak(u);

}


/* ==========================
   MICROPHONE
========================== */

const SpeechRecognition=
window.SpeechRecognition ||
window.webkitSpeechRecognition;


if(SpeechRecognition){

 const recognition=
 new SpeechRecognition();


 recognition.lang="en-US";

 recognition.interimResults=false;

 recognition.continuous=false;


 micBtn.onclick=()=>{

  startTimer();

  recognition.start();

  micBtn
  .classList
  .add("listening");

  micText.textContent=
  "Tinglayapman...";

  aiState.textContent=
  "Gapiring...";

 };


 recognition.onresult=e=>{

  const text=
  e.results[0][0]
  .transcript;


  lastAnswer.textContent=
  "Siz: "+text;


  aiState.textContent=
  "Iltimos, kuting...";


  setTimeout(()=>{

   const reply=
   getReply();

   speak(reply);

  },700);

 };


 recognition.onend=()=>{

  micBtn
  .classList
  .remove("listening");

  micText.textContent=
  "Yana gapirish uchun bosing";

 };


 recognition.onerror=()=>{

  micBtn
  .classList
  .remove("listening");

  micText.textContent=
  "Mikrofonni qayta bosing";

  aiState.textContent=
  "Mikrofonga ruxsatni tekshiring";

 };

}

else{

 micBtn.onclick=()=>{

  alert(
   "Bu brauzer speech recognition funksiyasini qo‘llamayapti. Real AI voice ulaganda bu qismni alohida qilamiz."
  );

 };

}


/* ==========================
   BACK + FINISH
========================== */

function closeSpeaking(){

 clearInterval(
  timerInterval
 );

 speechSynthesis.cancel();

 speaking
 .classList
 .remove("show");

 home.style.display="block";

 window.scrollTo(0,0);

}


document
.getElementById(
 "backBtn"
)
.onclick=
closeSpeaking;


document
.getElementById(
 "finishBtn"
)
.onclick=()=>{

 aiState.textContent=
 "Suhbat tugadi ✅";

 setTimeout(
  closeSpeaking,
  700
 );

};

</script>

</body>
</html>