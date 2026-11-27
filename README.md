
<html lang="id">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no, viewport-fit=cover">
<title>Smash Court: Game Badminton</title>
<meta name="description" content="Main badminton melawan CPU langsung di browser. Servis, lob, drop shot, dan smash. Gratis, tanpa unduhan.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Chakra+Petch:wght@500;700&display=swap" rel="stylesheet">
<style>
:root{--bg:#eef1fb;--surface:#ffffff;--ink:#101735;--muted:#56608a;--line:#cdd4ee;--accent:#e8483b;--accent2:#1fa8bd;--gold:#ffd23f;
  box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#090e20;--surface:#141b38;--ink:#eef1ff;--muted:#9aa5d4;--line:#27315c;--accent:#ff6a5c;--accent2:#3cc9de;color-scheme:dark}}
:root[data-theme="dark"]{--bg:#090e20;--surface:#141b38;--ink:#eef1ff;--muted:#9aa5d4;--line:#27315c;--accent:#ff6a5c;--accent2:#3cc9de;color-scheme:dark}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font:500 16px/1.5 "Chakra Petch",system-ui,sans-serif;-webkit-tap-highlight-color:transparent}
.wrap{max-width:900px;margin:0 auto;padding:18px 14px 28px}
h1{margin:0;font-size:clamp(1.6rem,5vw,2.4rem);font-weight:700;letter-spacing:.02em}
h1 span{color:var(--accent)}
.sub{margin:2px 0 14px;color:var(--muted)}
.stage{position:relative;border-radius:16px;overflow:hidden;border:2px solid var(--line);background:#0b1330}
canvas{display:block;width:100%;height:auto;touch-action:none}
.ov{position:absolute;inset:0;display:grid;place-items:center;background:rgba(6,10,28,.82);color:#fff;text-align:center;padding:14px}
.ov.hide{display:none}
.card{max-width:420px}
.card h2{margin:0 0 6px;font-size:clamp(1.4rem,4.5vw,2rem)}
.card p{margin:6px 0;color:#c9d1f5;font-size:15px}
.chips{display:flex;gap:8px;justify-content:center;margin:14px 0}
.chip{font:700 15px "Chakra Petch",sans-serif;padding:8px 18px;border-radius:999px;border:2px solid #4a5690;background:transparent;color:#fff;cursor:pointer}
.chip[aria-pressed="true"]{background:var(--gold);color:#2a1c00;border-color:var(--gold)}
.go{font:700 18px "Chakra Petch",sans-serif;background:var(--accent);color:#fff;border:0;border-radius:999px;padding:13px 34px;cursor:pointer;box-shadow:0 4px 0 rgba(0,0,0,.35)}
.go:active{transform:translateY(3px);box-shadow:0 1px 0 rgba(0,0,0,.35)}
button:focus-visible{outline:3px solid var(--gold);outline-offset:2px}
#pad{display:none;justify-content:space-between;gap:10px;margin-top:12px;user-select:none;-webkit-user-select:none}
#pad div{display:flex;gap:10px}
#pad button{font:700 15px "Chakra Petch",sans-serif;min-width:62px;height:62px;border-radius:16px;border:2px solid var(--line);background:var(--surface);color:var(--ink);touch-action:none}
#pad button.on{background:var(--accent2);color:#04222a}
#pad .big{min-width:92px;background:var(--accent);color:#fff;border-color:var(--accent)}
@media (pointer:coarse){#pad{display:flex}.kb{display:none}}
.kb,.note{margin:12px 0 0;color:var(--muted);font-size:14px}
kbd{background:var(--surface);border:1px solid var(--line);border-bottom-width:2px;border-radius:6px;padding:1px 7px;font:700 13px "Chakra Petch",sans-serif;color:var(--ink)}
.tools{display:flex;justify-content:space-between;align-items:center;margin-top:10px;color:var(--muted);font-size:14px}
.link{background:none;border:0;color:var(--accent2);font:700 14px "Chakra Petch",sans-serif;cursor:pointer;text-decoration:underline}
.stage{box-shadow:0 20px 60px rgba(5,10,40,.35)}
.ov{background:radial-gradient(circle at 50% 30%,rgba(40,70,160,.55),rgba(5,8,25,.93) 70%)}
.eyebrow{font-size:12px;letter-spacing:.28em;color:var(--gold);margin-bottom:4px}
.logo{font-size:clamp(2rem,8vw,3.2rem)!important;font-weight:700;letter-spacing:.03em;line-height:1}
.logo span{color:var(--accent)}
.lvl{margin-top:14px;font-size:12px;letter-spacing:.2em;text-transform:uppercase;color:#9fb0ea}
.keys{display:flex;flex-wrap:wrap;gap:6px 16px;justify-content:center;margin-top:16px;font-size:13px;color:#b9c4f2}
.ov kbd{background:#1c2658;border-color:#3a4686;color:#fff}
.chips{margin:8px 0 16px}
html{touch-action:manipulation}body{overscroll-behavior:none;-webkit-touch-callout:none}
.rot{display:none;margin:0 0 10px;padding:8px 12px;border-radius:10px;background:var(--surface);border:1px solid var(--line);color:var(--muted);font-size:14px}
@media (pointer:coarse){#pad{display:flex;gap:6px;margin:0;padding:10px 8px;background:#060a1c}#pad div{display:flex;gap:6px;flex:1;min-width:0}#pad button{flex:1;min-width:0;height:54px;padding:0;font-size:14px;-webkit-user-select:none;user-select:none}#pad .big{flex:1.5;min-width:0}.rot{display:block}}
@media (pointer:coarse) and (orientation:landscape){
 html,body{height:100%;overflow:hidden}
 .wrap{padding:0;max-width:none}
 h1,.sub,.kb,.tools,.note,.rot{display:none}
 .stage{position:fixed;inset:0;border:0;border-radius:0;box-shadow:none;background:#04060f;display:grid;place-items:center}
 canvas{width:min(100%,calc((100vh - env(safe-area-inset-top,0px) - env(safe-area-inset-bottom,0px))*1.7778));height:auto}
 #pad{position:absolute;left:0;right:0;bottom:0;margin:0;padding:0 max(14px,env(safe-area-inset-right,0px)) max(12px,env(safe-area-inset-bottom,0px)) max(14px,env(safe-area-inset-left,0px));background:none;pointer-events:none;z-index:5}
 #pad div{flex:none;gap:10px}
 #pad button{flex:none;pointer-events:auto;min-width:64px;height:64px;border-radius:50%;background:rgba(10,16,48,.55);border-color:rgba(255,255,255,.35);color:#fff;font-size:18px}
 #pad .big{flex:none;min-width:86px;height:86px;background:rgba(232,72,59,.72);font-size:16px}
 #pad button.on{background:rgba(255,210,63,.88);color:#2a1c00}
 .ov .card{transform:scale(.88)}
 .ov .keys{display:none}
}
</style>
</head>
<body>
<main class="wrap">
  <h1>Smash <span>Court</span></h1>
  <p class="sub">Badminton satu lawan satu. Skor pertama yang mencapai 11 menang.</p>
  <p class="rot">Untuk layar yang lebih luas, putar HP ke mode lanskap.</p>
  <div class="stage">
    <canvas id="c" width="800" height="450" aria-label="Arena badminton"></canvas>
    <div class="ov" id="menu"><div class="card">
      <div class="eyebrow">BADMINTON · 1 VS CPU</div>
      <h2 class="logo">SMASH <span>COURT</span></h2>
      <p>Servis, lob, drop shot, dan smash. Rebut 11 poin lebih dulu dari lawanmu.</p>
      <div class="lvl">Tingkat kesulitan</div>
      <div class="chips" id="diffs" role="group" aria-label="Tingkat kesulitan"></div>
      <button class="go" id="start" type="button">Mulai pertandingan</button>
      <div class="keys"><span><kbd>←</kbd><kbd>→</kbd> Gerak</span><span><kbd>↑</kbd> Lompat</span><span><kbd>Spasi</kbd> Pukul</span><span><kbd>K</kbd> Smash</span></div>
      <p id="winsTxt"></p>
    </div></div>
    <div class="ov hide" id="over"><div class="card">
      <h2 id="ovT"></h2><p id="ovS"></p>
      <button class="go" id="again" type="button">Main lagi</button>
    </div></div>
    <div id="pad" aria-label="Kontrol sentuh">
    <div><button data-k="l" type="button">◀</button><button data-k="r" type="button">▶</button><button data-k="u" type="button">▲</button></div>
    <div><button data-k="smash" type="button">Smash</button><button data-k="hit" type="button" class="big">Pukul</button></div>
  </div>
  </div>
  <p class="kb"><kbd>←</kbd> <kbd>→</kbd> atau <kbd>A</kbd> <kbd>D</kbd> bergerak · <kbd>↑</kbd>/<kbd>W</kbd> lompat · <kbd>Spasi</kbd> pukul · <kbd>K</kbd> smash. Tahan kiri saat memukul untuk drop shot pendek, tahan kanan untuk pukulan jauh.</p>
  <div class="tools"><span id="rl">Reli: 0</span><button class="link" id="fs" type="button">Layar penuh</button><button class="link" id="snd" type="button">Suara: nyala</button></div>
  <p class="note">Smash paling efektif saat kok berada tinggi, jadi lompatlah. Servis: tekan Pukul saat giliranmu. Di HP, pakai tombol di layar: ◀ ▶ untuk gerak, ▲ untuk lompat.</p>
</main>

<script>
var cv=document.getElementById("c"),ctx=cv.getContext("2d");
var W=800,H=450,G=380,NX=400,NT=282,GA=620,DR=0.0035;
var DIFF=[{n:"Mudah",sp:170,miss:.3,smash:.15,err:50},{n:"Sedang",sp:230,miss:.15,smash:.35,err:30},{n:"Sulit",sp:300,miss:.06,smash:.55,err:14}];
var ANG={lob:-0.8,drop:-1.0,smash:0.32};
var diff=1,phase="menu",score={p:0,c:0},server="p",msg="",pointT=0,srvT=0,shotId=0,rally=0,sound=true,wins=0,lastTs=0;
try{wins=+localStorage.getItem("sc-wins")||0}catch(e){}
var P={x:200,jy:0,jv:0,sw:0,swK:"lob",cd:0,face:1,mv:0};
var Cp={x:600,jy:0,jv:0,sw:0,swK:"lob",cd:0,face:-1,mv:0,tx:600,miss:false,react:0,shot:-1,d:200,wj:false};
var S={x:0,y:0,vx:0,vy:0,last:"p",tr:[]};
var keys={l:0,r:0,u:0},fx=[],pop=[];
function clamp(v,a,b){return Math.max(a,Math.min(b,v))}
var AC=null;
function beep(f){if(!sound)return;try{AC=AC||new(window.AudioContext||window.webkitAudioContext)();var o=AC.createOscillator(),g=AC.createGain();o.type="triangle";o.frequency.value=f;g.gain.value=.06;o.connect(g);g.connect(AC.destination);o.start();g.gain.exponentialRampToValueAtTime(.001,AC.currentTime+.12);o.stop(AC.currentTime+.13)}catch(e){}}

/* fisika kok */
function stepO(o,dt){var sp=Math.hypot(o.vx,o.vy);o.vx-=DR*sp*o.vx*dt;o.vy+=(GA-DR*sp*o.vy)*dt;o.x+=o.vx*dt;o.y+=o.vy*dt}
function sim(x,y,vx,vy,wy){
  var o={x:x,y:y,vx:vx,vy:vy},px;
  for(var i=0;i<900;i++){px=o.x;stepO(o,1/120);
    if((px-NX)*(o.x-NX)<0&&o.y>NT)return{net:true,x:o.x};
    if(wy!==undefined&&o.vy>0&&o.y>=wy)return{net:false,x:o.x};
    if(o.y>=G)return{net:false,x:o.x}}
  return{net:false,x:o.x}
}
function aim(x,y,dir,d,kind){
  var a=ANG[kind],tx=NX+dir*d,best=null,bd=1e9;
  for(var s=260;s<=1400;s+=20){
    var vx=dir*s*Math.cos(a),vy=s*Math.sin(a),r=sim(x,y,vx,vy);
    if(r.net||dir*(r.x-NX)<0)continue;
    var e=Math.abs(r.x-tx);if(e<bd){bd=e;best={vx:vx,vy:vy}}
  }
  if(best)return best;
  if(kind!=="lob")return aim(x,y,dir,d,"lob");
  return{vx:dir*900*Math.cos(a),vy:900*Math.sin(a)}
}
function reach(p){return{x:p.x+p.face*30,y:G-110-p.jy}}
function hit(who,kind,d){
  var dir=who==="p"?1:-1,r=aim(S.x,S.y,dir,d,kind);
  S.vx=r.vx;S.vy=r.vy;S.last=who;shotId++;rally++;
  fx.push({x:S.x,y:S.y,t:0});beep(kind==="smash"?260:520);
  if(kind==="smash")pop.push({x:S.x,y:S.y-24,t:0});
  document.getElementById("rl").textContent="Reli: "+rally;
}
function startSwing(p,k){if(p.cd>0)return false;p.sw=.28;p.swK=k;p.cd=.45;return true}

/* alur permainan */
function resetRally(){
  P.x=200;Cp.x=600;P.jy=P.jv=Cp.jy=Cp.jv=0;P.sw=Cp.sw=0;
  phase="serve";S.last=server;srvT=1;msg="";rally=0;S.tr=[];shotId++;
  document.getElementById("rl").textContent="Reli: 0";
}
function startGame(){score={p:0,c:0};server="p";document.getElementById("menu").classList.add("hide");document.getElementById("over").classList.add("hide");resetRally();beep(440)}
function endPoint(w,text){
  score[w]++;server=w;phase="point";pointT=1.5;
  msg=(w==="p"?"Poin untukmu! ":"Poin untuk CPU. ")+text;
}
function isOver(){var a=score.p,b=score.c;return ((a>=11||b>=11)&&Math.abs(a-b)>=2)||a>=15||b>=15}
function land(){
  var x=S.x,l=S.last,ok;
  S.y=G;
  if(l==="p"){ok=x>NX&&x<=770}else{ok=x<NX&&x>=30}
  var w=ok?l:(l==="p"?"c":"p"),t=ok?"Kok jatuh di area lawan.":(x<30||x>770?"Kok keluar garis.":"Kok jatuh di area sendiri.");
  endPoint(w,t);
}
function tryHit(who){
  var pl=who==="p"?P:Cp;if(pl.sw<=0||S.last===who)return;
  var r=reach(pl);if(Math.hypot(S.x-r.x,S.y-r.y)>74)return;
  var k=pl.swK,d;
  if(who==="p"){d=keys.l?100:keys.r?330:210;if(k==="lob"&&keys.l){k="drop";d=95}if(k==="smash")d=keys.l?150:keys.r?300:220}
  else d=pl.d;
  hit(who,k,d);pl.sw=.12;
}
function serveHit(who){
  var pl=who==="p"?P:Cp,r=reach(pl);S.x=r.x;S.y=r.y;
  var d=who==="p"?(keys.l?120:keys.r?300:220):180+Math.random()*120;
  pl.sw=.28;pl.cd=.45;hit(who,"lob",d);phase="rally";rally=1;
  document.getElementById("rl").textContent="Reli: 1";
}
function playerSwing(k){
  if(phase==="serve"&&server==="p"&&srvT<=0.2){serveHit("p");return}
  if(phase==="rally")startSwing(P,k);
}
function jump(p,dt,want){
  if(want&&p.jy===0&&p.jv===0)p.jv=640;
  if(p.jv!==0||p.jy>0){p.jy+=p.jv*dt;p.jv-=1900*dt;if(p.jy<=0&&p.jv<=0){p.jy=0;p.jv=0}}
}
function ai(dt){
  var d=DIFF[diff];Cp.wj=false;
  var inc=phase==="rally"&&S.last==="p"&&S.x>NX-40;
  if(inc){
    if(Cp.shot!==shotId){Cp.shot=shotId;var r0=sim(S.x,S.y,S.vx,S.vy,G-105);Cp.tx=r0.x+30+(Math.random()*2-1)*d.err;Cp.miss=Math.random()<d.miss;Cp.react=.1+Math.random()*.15}
    Cp.react-=dt;
    if(Cp.react<=0){var dx=Cp.tx-Cp.x;Cp.x+=clamp(dx,-d.sp*dt,d.sp*dt)}
    Cp.x=clamp(Cp.x,430,775);
    var r=reach(Cp),dist=Math.hypot(S.x-r.x,S.y-r.y);
    if(diff>0&&S.y<G-150&&S.vy>0&&Math.abs(S.x-r.x)<80)Cp.wj=true;
    if(!Cp.miss&&Cp.cd<=0&&dist<80){
      var hi=S.y<G-130,k=hi&&Math.random()<d.smash?"smash":(Math.random()<.25?"drop":"lob");
      Cp.d=k==="smash"?120+Math.random()*200:k==="drop"?70+Math.random()*50:160+Math.random()*180;
      startSwing(Cp,k);
    }
  }else if(phase==="rally"||phase==="serve"){Cp.x+=clamp(600-Cp.x,-120*dt,120*dt)}
}
function update(dt){
  if(phase==="menu"||phase==="over")return;
  P.mv=keys.r-keys.l;P.x=clamp(P.x+P.mv*300*dt,30,370);
  jump(P,dt,keys.u);
  P.sw=Math.max(0,P.sw-dt);P.cd=Math.max(0,P.cd-dt);Cp.sw=Math.max(0,Cp.sw-dt);Cp.cd=Math.max(0,Cp.cd-dt);
  var cpx=Cp.x;ai(dt);Cp.mv=Math.abs(Cp.x-cpx)>.05?Math.sign(Cp.x-cpx):0;jump(Cp,dt,Cp.wj);
  if(phase==="serve"){
    var pl=server==="p"?P:Cp,r=reach(pl);S.x=r.x+(server==="p"?4:-4);S.y=r.y+20;S.vx=S.vy=0;S.tr=[];
    srvT-=dt;if(server==="c"&&srvT<=-.4)serveHit("c");
  }else{
    var px=S.x;stepO(S,dt);S.tr.push({x:S.x,y:S.y});if(S.tr.length>12)S.tr.shift();
    if(phase==="rally"){
      tryHit("p");tryHit("c");
      if((px-NX)*(S.x-NX)<0&&S.y>NT){S.vx=0;endPoint(S.last==="p"?"c":"p","Kok mengenai net.")}
      else if(S.y>=G)land();
    }else if(S.y>=G){S.y=G;S.vx=S.vy=0}
    if(phase==="point"){
      pointT-=dt;
      if(pointT<=0){if(isOver())finish();else resetRally()}
    }
  }
  fx.forEach(function(f){f.t+=dt});fx=fx.filter(function(f){return f.t<.35});
  pop.forEach(function(f){f.t+=dt});pop=pop.filter(function(f){return f.t<.8});
}
function finish(){
  phase="over";var won=score.p>score.c;
  if(won){wins++;try{localStorage.setItem("sc-wins",String(wins))}catch(e){}}
  document.getElementById("ovT").textContent=won?"Kamu menang!":"CPU menang";
  document.getElementById("ovS").textContent="Skor akhir "+score.p+" : "+score.c+(won?". Pertahankan performamu." :". Coba lagi, kamu pasti bisa.");
  document.getElementById("over").classList.remove("hide");
  document.getElementById("winsTxt").textContent="Total kemenanganmu: "+wins;
}

/* gambar */
var bgc=document.createElement("canvas");bgc.width=W;bgc.height=H;var vg=null;
function rr(x,y,w,h,r){ctx.beginPath();if(ctx.roundRect)ctx.roundRect(x,y,w,h,r);else ctx.rect(x,y,w,h)}
function ell(x,y,rx,ry,rot){ctx.beginPath();ctx.ellipse(x,y,rx,ry,rot,0,Math.PI*2)}
function lab(s,x,y,size,col,al){ctx.font="700 "+size+"px 'Chakra Petch',sans-serif";ctx.textAlign=al||"center";ctx.fillStyle=col;ctx.fillText(s,x,y)}
function text(s,x,y,size,col,al){ctx.lineJoin="round";ctx.font="700 "+size+"px 'Chakra Petch',sans-serif";ctx.textAlign=al||"center";ctx.lineWidth=6;ctx.strokeStyle="rgba(5,8,25,.8)";ctx.strokeText(s,x,y);ctx.fillStyle=col;ctx.fillText(s,x,y)}
function PT(x,t){var s=.84+.16*t;return[400+(x-400)*s,350+100*t]}
function buildBG(){
  var main=ctx;ctx=bgc.getContext("2d");
  var g=ctx.createLinearGradient(0,0,0,350);g.addColorStop(0,"#060a1f");g.addColorStop(1,"#1b2e6e");ctx.fillStyle=g;ctx.fillRect(0,0,W,350);
  ctx.fillStyle="#0a1131";ctx.fillRect(0,96,W,200);
  var seed=7;function rnd(){seed=(seed*16807)%2147483647;return seed/2147483647}
  var cc=["#e8483b","#1fa8bd","#ffd23f","#e9edff","#7c5cff","#ff8a3c"];
  for(var r=0;r<7;r++)for(var i=0;i<60;i++){var x=i*14+(r%2)*7+rnd()*4,y=110+r*24+rnd()*3;
    ctx.fillStyle="rgba(8,12,40,.9)";ctx.beginPath();ctx.arc(x,y+9,8,0,7);ctx.fill();
    ctx.fillStyle=cc[Math.floor(rnd()*6)];ctx.globalAlpha=.45+r*.06;ctx.beginPath();ctx.arc(x,y-2,5,0,7);ctx.fill();ctx.globalAlpha=1}
  ctx.fillStyle="#0b1647";ctx.fillRect(0,296,W,52);
  for(var j=0;j<5;j++){ctx.fillStyle=j%2?"#c8362b":"#15808f";ctx.fillRect(j*160+6,302,148,40);lab("SMASH COURT",j*160+80,328,16,"#fff")}
  ctx.fillStyle="#050816";ctx.fillRect(0,296,W,4);
  ctx.fillStyle="#0b3556";ctx.fillRect(0,348,W,102);
  var a=PT(30,.04),b=PT(770,.04),c=PT(770,.96),d=PT(30,.96);
  var fg=ctx.createLinearGradient(0,350,0,450);fg.addColorStop(0,"#2380bd");fg.addColorStop(1,"#1a6aa0");ctx.fillStyle=fg;
  ctx.beginPath();ctx.moveTo(a[0],a[1]);ctx.lineTo(b[0],b[1]);ctx.lineTo(c[0],c[1]);ctx.lineTo(d[0],d[1]);ctx.closePath();ctx.fill();
  function ln(x1,t1,x2,t2){var p=PT(x1,t1),q=PT(x2,t2);ctx.moveTo(p[0],p[1]);ctx.lineTo(q[0],q[1])}
  ctx.strokeStyle="rgba(255,255,255,.92)";ctx.lineWidth=3;ctx.beginPath();
  ln(30,.04,770,.04);ln(30,.96,770,.96);ln(30,.04,30,.96);ln(770,.04,770,.96);ln(400,.04,400,.96);ln(275,.04,275,.96);ln(525,.04,525,.96);ln(30,.5,275,.5);ln(525,.5,770,.5);ctx.stroke();
  ctx.lineWidth=2;ctx.beginPath();ln(30,.14,770,.14);ln(30,.86,770,.86);ctx.stroke();
  [120,400,680].forEach(function(lx){var rg=ctx.createRadialGradient(lx,0,0,lx,0,200);rg.addColorStop(0,"rgba(255,244,210,.5)");rg.addColorStop(1,"rgba(255,244,210,0)");ctx.fillStyle=rg;ctx.fillRect(lx-200,0,400,230)});
  ctx=main;
}
function person(p,shirt,shorts,skin,hair,num){
  var f=p.face,gy=G-p.jy,x=p.x,run=(p.mv&&p.jy===0)?Math.sin(performance.now()/95):0;
  ctx.fillStyle="rgba(0,0,0,"+(.34-Math.min(.22,p.jy/500))+")";ell(x,G+4,25-p.jy/14,6,0);ctx.fill();
  ctx.save();ctx.translate(x,gy);ctx.rotate(p.mv*.06);ctx.lineCap="round";ctx.lineJoin="round";
  for(var k=0;k<2;k++){var hx=k?7:-7,dx=(k?-run:run)*9,air=p.jy>0?(k?4:-4):0;
    ctx.strokeStyle=skin;ctx.lineWidth=7;ctx.beginPath();ctx.moveTo(hx,-34);ctx.lineTo(hx+dx*.5,-17+air*.3);ctx.lineTo(hx+dx,-5+air);ctx.stroke();
    ctx.fillStyle="#f4f6ff";ell(hx+dx+f*3,-3+air,9,4.5,0);ctx.fill()}
  ctx.fillStyle=shorts;rr(-13,-50,26,22,6);ctx.fill();
  ctx.strokeStyle=skin;ctx.lineWidth=6;ctx.beginPath();ctx.moveTo(-f*7,-84);ctx.lineTo(-f*13,-64);ctx.stroke();
  ctx.fillStyle=shirt;rr(-13,-92,26,46,9);ctx.fill();
  ctx.fillStyle="rgba(255,255,255,.25)";ctx.fillRect(-13,-56,26,3);
  lab(num,0,-66,13,"#fff");
  ctx.fillStyle=skin;ctx.beginPath();ctx.arc(0,-106,11,0,7);ctx.fill();
  ctx.fillStyle=hair;ctx.beginPath();ctx.arc(0,-108,11.5,Math.PI,0);ctx.fill();
  ctx.fillStyle="#fff";ctx.fillRect(-11.5,-111,23,4);
  var sx=f*6,sy=-84,hx2=f*17,hy=-74,phi=f*.55;
  if(p.sw>0)phi=f*(-1.3+3*(1-p.sw/.28));
  var s=Math.sin(phi),c=Math.cos(phi),tx=hx2+s*40,ty=hy-c*40,cx=tx+s*17,cy=ty-c*17;
  ctx.strokeStyle=skin;ctx.lineWidth=6;ctx.beginPath();ctx.moveTo(sx,sy);ctx.lineTo(hx2,hy);ctx.stroke();
  ctx.strokeStyle="#c9d1ea";ctx.lineWidth=3;ctx.beginPath();ctx.moveTo(hx2,hy);ctx.lineTo(tx,ty);ctx.stroke();
  ctx.strokeStyle="#fff";ctx.lineWidth=3;ell(cx,cy,11,17,phi);ctx.stroke();
  ctx.strokeStyle="rgba(255,255,255,.4)";ctx.lineWidth=1;ctx.beginPath();
  [-5,0,5].forEach(function(o){var ax=cx+Math.cos(phi)*o,ay=cy+Math.sin(phi)*o;ctx.moveTo(ax-s*13,ay+c*13);ctx.lineTo(ax+s*13,ay-c*13)});ctx.stroke();
  ctx.restore();
}
function draw(){
  ctx.drawImage(bgc,0,0);
  // net
  ctx.fillStyle="rgba(255,255,255,.14)";ctx.fillRect(NX-14,NT,28,G-NT+4);
  ctx.strokeStyle="rgba(255,255,255,.3)";ctx.lineWidth=1;ctx.beginPath();
  for(var yy=NT+6;yy<G+4;yy+=9){ctx.moveTo(NX-14,yy);ctx.lineTo(NX+14,yy)}for(var xx=NX-14;xx<=NX+14;xx+=7){ctx.moveTo(xx,NT);ctx.lineTo(xx,G+4)}ctx.stroke();
  ctx.fillStyle="#cfd6ee";ctx.fillRect(NX-2,NT-10,4,G-NT+14);
  ctx.fillStyle="#fff";ctx.fillRect(NX-14,NT-3,28,5);
  person(Cp,"#1fa8bd","#10224a","#e7b48a","#3d2a1a","7");
  person(P,"#e8483b","#1b2447","#d9a074","#2a1a12","1");
  if(phase!=="menu"){
    var hh=G-S.y,sa=clamp(.38-hh/900,.08,.38),sr=Math.max(4,11-hh/70);
    ctx.fillStyle="rgba(0,0,0,"+sa+")";ell(S.x,G+8,sr,sr*.35,0);ctx.fill();
    S.tr.forEach(function(q,i){ctx.fillStyle="rgba(255,255,255,"+(i/S.tr.length*.3)+")";ctx.beginPath();ctx.arc(q.x,q.y,2.5,0,7);ctx.fill()});
    ctx.save();ctx.translate(S.x,S.y);ctx.rotate(Math.atan2(S.vy,S.vx));
    ctx.fillStyle="#f4f6ff";ctx.beginPath();ctx.moveTo(-3,-4);ctx.lineTo(-19,-10);ctx.lineTo(-19,10);ctx.lineTo(-3,4);ctx.closePath();ctx.fill();
    ctx.strokeStyle="rgba(120,130,170,.6)";ctx.lineWidth=1;ctx.beginPath();[-6,-2,2,6].forEach(function(o){ctx.moveTo(-4,o*.5);ctx.lineTo(-19,o*1.6)});ctx.stroke();
    ctx.fillStyle="#ffd23f";ctx.beginPath();ctx.arc(0,0,4.5,0,7);ctx.fill();ctx.restore();
  }
  fx.forEach(function(f){var a=1-f.t/.35;ctx.strokeStyle="rgba(255,210,63,"+a+")";ctx.lineWidth=3;ctx.beginPath();ctx.arc(f.x,f.y,8+f.t*100,0,7);ctx.stroke();
    ctx.lineWidth=2;ctx.beginPath();for(var q=0;q<8;q++){var an=q*Math.PI/4,r1=12+f.t*90,r2=r1+10;ctx.moveTo(f.x+Math.cos(an)*r1,f.y+Math.sin(an)*r1);ctx.lineTo(f.x+Math.cos(an)*r2,f.y+Math.sin(an)*r2)}ctx.stroke()});
  pop.forEach(function(f){text("SMASH!",f.x,f.y-f.t*40,28,"#ffd23f")});
  if(!vg){vg=ctx.createRadialGradient(400,225,200,400,225,520);vg.addColorStop(0,"rgba(0,0,0,0)");vg.addColorStop(1,"rgba(0,0,0,.42)")}
  ctx.fillStyle=vg;ctx.fillRect(0,0,W,H);
  // papan skor
  rr(14,12,214,70,12);ctx.fillStyle="rgba(5,9,30,.86)";ctx.fill();
  [["KAMU",score.p,"#ff6a5c","p"],["CPU",score.c,"#3cc9de","c"]].forEach(function(r,i){
    var y=16+i*33;rr(22,y+3,5,24,2);ctx.fillStyle=r[2];ctx.fill();
    lab(r[0],38,y+23,16,"#fff","left");lab(String(r[1]),190,y+25,24,"#fff","right");
    if(server===r[3]){ctx.fillStyle="#ffd23f";ctx.beginPath();ctx.arc(208,y+16,4.5,0,7);ctx.fill()}});
  ctx.fillStyle="rgba(255,255,255,.12)";ctx.fillRect(22,48,192,1);
  rr(640,14,146,26,13);ctx.fillStyle="rgba(5,9,30,.7)";ctx.fill();lab("Level: "+DIFF[diff].n,713,32,14,"#dfe5ff");
  if(phase==="serve"){rr(250,402,300,34,17);ctx.fillStyle="rgba(5,9,30,.78)";ctx.fill();lab(server==="p"?"Servis: tekan Pukul":"CPU bersiap servis…",400,425,16,"#fff")}
  if(phase==="point"){rr(190,118,420,58,14);var bg2=ctx.createLinearGradient(190,0,610,0);bg2.addColorStop(0,"#b8221a");bg2.addColorStop(1,"#c9852a");ctx.fillStyle=bg2;ctx.fill();lab(msg,400,155,20,"#fff")}
}
function loop(ts){var v=(phase==="menu"||phase==="over")?"hidden":"visible";if(padEl.style.visibility!==v)padEl.style.visibility=v;var dt=Math.min(.033,(ts-lastTs)/1000||0);lastTs=ts;update(dt);draw();requestAnimationFrame(loop)}

/* kontrol */
var KM={ArrowLeft:"l",KeyA:"l",ArrowRight:"r",KeyD:"r",ArrowUp:"u",KeyW:"u"};
addEventListener("keydown",function(e){
  var k=KM[e.code];
  if(k){keys[k]=1;e.preventDefault()}
  if(e.repeat)return;
  if(e.code==="Space"||e.code==="KeyJ"){e.preventDefault();playerSwing("lob")}
  if(e.code==="KeyK"){e.preventDefault();playerSwing("smash")}
});
addEventListener("keyup",function(e){var k=KM[e.code];if(k)keys[k]=0});
addEventListener("blur",function(){keys.l=keys.r=keys.u=0});
function padRel(b,k){b.classList.remove("on");if(k!=="hit"&&k!=="smash")keys[k]=0}
document.querySelectorAll("#pad button").forEach(function(b){
  var k=b.getAttribute("data-k");
  b.addEventListener("pointerdown",function(e){e.preventDefault();try{b.setPointerCapture(e.pointerId)}catch(x){}b.classList.add("on");
    if(k==="hit")playerSwing("lob");else if(k==="smash")playerSwing("smash");else keys[k]=1});
  ["pointerup","pointercancel","lostpointercapture"].forEach(function(ev){b.addEventListener(ev,function(){padRel(b,k)})});
  b.addEventListener("contextmenu",function(e){e.preventDefault()});
});
var fsb=document.getElementById("fs"),stg=document.querySelector(".stage"),padEl=document.getElementById("pad");
if(!(document.fullscreenEnabled||document.webkitFullscreenEnabled))fsb.style.display="none";
fsb.addEventListener("click",function(){
  var el=document.fullscreenElement||document.webkitFullscreenElement;
  if(el){(document.exitFullscreen||document.webkitExitFullscreen).call(document);return}
  var rq=stg.requestFullscreen||stg.webkitRequestFullscreen;
  if(rq){var pr=rq.call(stg);if(screen.orientation&&screen.orientation.lock)Promise.resolve(pr).then(function(){return screen.orientation.lock("landscape")}).catch(function(){})}
});
var dbox=document.getElementById("diffs");
DIFF.forEach(function(d,i){
  var b=document.createElement("button");b.type="button";b.className="chip";b.textContent=d.n;b.setAttribute("aria-pressed",i===diff?"true":"false");
  b.addEventListener("click",function(){diff=i;dbox.querySelectorAll(".chip").forEach(function(c,j){c.setAttribute("aria-pressed",j===i?"true":"false")})});
  dbox.appendChild(b);
});
document.getElementById("start").addEventListener("click",startGame);
document.getElementById("again").addEventListener("click",startGame);
document.getElementById("snd").addEventListener("click",function(){sound=!sound;this.textContent="Suara: "+(sound?"nyala":"mati")});
document.getElementById("winsTxt").textContent=wins?"Total kemenanganmu: "+wins:"";
resetRally();phase="menu";buildBG();if(document.fonts&&document.fonts.ready)document.fonts.ready.then(buildBG);
requestAnimationFrame(loop);
</script>
</body>
</html>
