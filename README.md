# Bookmarklets.github.io
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Bookmarklets — Tools & Games</title>
<style>
  body{font-family:system-ui,-apple-system,Segoe UI,Roboto,Arial;background:#0b1220;color:#e6eef8;margin:0;min-height:100vh;display:flex;align-items:center;justify-content:center;padding:28px}
  .wrap{max-width:980px;width:100%}
  h1{text-align:center;margin:0 0 14px}
  .grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:14px}
  .card{background:#071026;padding:16px;border-radius:10px;border:1px solid rgba(255,255,255,0.04);display:flex;flex-direction:column;justify-content:space-between;min-height:120px}
  .title{font-weight:700;margin-bottom:8px}
  .muted{color:#9fb4d6;font-size:0.95rem;margin-bottom:12px}
  a.btn{display:inline-block;padding:10px 14px;border-radius:8px;background:#1f9fff;color:#012026;text-decoration:none;font-weight:700;text-align:center;cursor:grab}
  a.btn:hover{filter:brightness(1.05)}
  footer{color:#8faac6;text-align:center;margin-top:18px;font-size:0.9rem}
  code{background:rgba(255,255,255,0.03);padding:3px 6px;border-radius:6px}
</style>
</head>
<body>
  <div class="wrap">
    <h1>🔖 Drag these to your bookmarks bar — Tools & Games Hub</h1>

    <div class="grid">

      <!-- Edit -->
      <div class="card">
        <div>
          <div class="title">Edit Page Text</div>
          <div class="muted">Toggle editable mode—click text to edit. Reload to restore.</div>
        </div>
        <!-- URL-encoded javascript -->
        <a class="btn"
           href="javascript:(function(){document.designMode=(document.designMode==='on'?'off':'on');document.body.contentEditable=(document.designMode==='on');alert('Edit mode: '+document.designMode);})();">
           Drag: Edit text
        </a>
      </div>

      <!-- Dev Console -->
      <div class="card">
        <div>
          <div class="title">Developer Console (mini)</div>
          <div class="muted">Opens a small popup console for running JS.</div>
        </div>
        <a class="btn"
           href="javascript:(function(){var w=window.open('','miniConsole','width=640,height=420');if(!w){alert('Popup blocked — allow popups for this site.');return;}w.document.write('<!doctype html><html><meta charset=\"utf-8\"><title>Mini Console</title><style>body{background:#111;color:#eee;font-family:monospace;margin:0;display:flex;flex-direction:column;height:100vh}#out{flex:1;overflow:auto;padding:10px;background:#000}#in{display:flex;padding:8px;gap:6px}input{flex:1;padding:8px;border-radius:6px;border:0;background:#222;color:#fff}button{padding:8px;border-radius:6px;border:0;background:#0b5cff;color:#fff}</style><div id=\"out\">Console ready.\n</div><div id=\"in\"><input id=\"cmd\" placeholder=\"Type JS and press Enter\"><button id=\"run\">Run</button></div><script>const out=document.getElementById(\"out\"),cmd=document.getElementById(\"cmd\");function log(v){out.textContent+=String(v)+'\\n';out.scrollTop=out.scrollHeight;}document.getElementById('run').onclick=()=>{try{var r=eval(cmd.value);log('> '+cmd.value);log(r);}catch(e){log('Error: '+e);}cmd.value='';};cmd.addEventListener('keydown',e=>{if(e.key==='Enter'){document.getElementById('run').click();}});<\/script></html>');})();">
           Drag: Developer console
        </a>
      </div>

      <!-- Games Hub (popup) -->
      <div class="card">
        <div>
          <div class="title">Games Hub (many games)</div>
          <div class="muted">Opens a popup with multiple built-in mini-games (Snake, Pong, TTT, Breakout, Flappy, Shooter, 2048, Cookie).</div>
        </div>
        <a class="btn"
           href="javascript:(function(){try{var w=window.open('','GamesHub','width=860,height=700');if(!w){alert('Popup blocked — allow popups.');return;}w.document.write('<!doctype html><html><head><meta charset=\"utf-8\"><title>Games Hub</title><style>body{background:#050714;color:#e6eef8;font-family:sans-serif;margin:0;padding:12px}#bar{display:flex;flex-wrap:wrap;gap:8px}button{background:#1572e8;color:#fff;border:0;padding:8px 12px;border-radius:8px;cursor:pointer;font-weight:700}canvas{display:block;margin-top:12px;border-radius:8px;background:#000;}</style></head><body><h1>🎮 Games Hub</h1><div id=\"bar\"></div><canvas id=\"cv\" width=\"600\" height=\"420\"></canvas><div style=\"margin-top:10px\"><button id=\"close\">Close</button></div><script>const games=[\"Snake\",\"TicTacToe\",\"Pong\",\"Breakout\",\"CookieClicker\",\"Flappy\",\"Shooter\",\"2048\"];const bar=document.getElementById('bar'),cv=document.getElementById('cv'),ctx=cv.getContext('2d');games.forEach(g=>{let b=document.createElement('button');b.textContent=g;b.onclick=()=>startGame(g);bar.appendChild(b);});document.getElementById('close').onclick=()=>window.close();/* games code (compact) */function snakeGame(){let S=20,cols=30,rows=21;cv.width=cols*S;cv.height=rows*S;let px=5,py=5,dx=1,dy=0,trail=[],tail=5,food={x:10,y:10};document.onkeydown=e=>{if(e.key.includes('Arrow')){dx=(e.key=='ArrowLeft'?-1:e.key=='ArrowRight'?1:0);dy=(e.key=='ArrowUp'?-1:e.key=='ArrowDown'?1:0);}};let id=setInterval(()=>{px+=dx;py+=dy; if(px<0)px=cols-1;if(px>=cols)px=0;if(py<0)py=rows-1;if(py>=rows)py=0; ctx.fillStyle='#001';ctx.fillRect(0,0,cv.width,cv.height); ctx.fillStyle='lime'; trail.forEach(s=>ctx.fillRect(s.x*S,s.y*S,S-2,S-2)); trail.push({x:px,y:py}); while(trail.length>tail)trail.shift(); if(food.x==px&&food.y==py){tail++; food={x:Math.floor(Math.random()*cols),y:Math.floor(Math.random()*rows)} } ctx.fillStyle='red'; ctx.fillRect(food.x*S,food.y*S,S-2,S-2); if(trail.slice(0,-1).some(s=>s.x==px&&s.y==py)){clearInterval(id);alert('Game Over (Snake)');}},90);}function ttt(){cv.width=600;cv.height=600;let b=Array(9).fill('');let turn='X';draw();cv.onclick=e=>{let x=Math.floor(e.offsetX/200),y=Math.floor(e.offsetY/200),i=y*3+x;if(!b[i]){b[i]=turn;turn=(turn=='X'?'O':'X');draw();}};function draw(){ctx.fillStyle='#001';ctx.fillRect(0,0,cv.width,cv.height);ctx.strokeStyle='#fff';for(let i=1;i<3;i++){ctx.beginPath();ctx.moveTo(i*200,0);ctx.lineTo(i*200,600);ctx.moveTo(0,i*200);ctx.lineTo(600,i*200);ctx.stroke();}ctx.fillStyle='#fff';ctx.font='120px sans-serif';ctx.textAlign='center';ctx.textBaseline='middle';for(let i=0;i<9;i++){if(b[i])ctx.fillText(b[i],(i%3)*200+100,Math.floor(i/3)*200+100);} }}function pong(){cv.width=600;cv.height=420;let ball={x:300,y:210,dx:4,dy:3},paddleY=160;document.onmousemove=e=>paddleY=e.clientY-cv.getBoundingClientRect().top-50; let id=setInterval(()=>{ball.x+=ball.dx;ball.y+=ball.dy;if(ball.y<0||ball.y>420)ball.dy*=-1;if(ball.x<0||ball.x>600)ball.dx*=-1; ctx.fillStyle='#001';ctx.fillRect(0,0,cv.width,cv.height); ctx.fillStyle='#fff'; ctx.fillRect(580,paddleY,12,100); ctx.beginPath(); ctx.arc(ball.x,ball.y,8,0,6.28); ctx.fill(); if(ball.x>572&&ball.y>paddleY&&ball.y<paddleY+100){ball.dx*=-1;} if(ball.x>600){clearInterval(id);alert('Game Over (Pong)');}},16);}function breakout(){cv.width=600;cv.height=420;let bricks=[];for(let r=0;r<4;r++)for(let c=0;c<8;c++)bricks.push({x:70*c+10,y:30*r+10,w:64,h:18,hit:false});let paddle={x:260,y:380,w:80,h:12},ball={x:300,y:200,dx:3,dy:3};document.onmousemove=e=>paddle.x = e.clientX - cv.getBoundingClientRect().left - paddle.w/2; let id=setInterval(()=>{ball.x+=ball.dx;ball.y+=ball.dy; if(ball.x<0||ball.x>cv.width)ball.dx*=-1;if(ball.y<0)ball.dy*=-1; if(ball.y>paddle.y&&ball.x>paddle.x&&ball.x<paddle.x+paddle.w){ball.dy*=-1;} ctx.fillStyle='#001';ctx.fillRect(0,0,cv.width,cv.height); ctx.fillStyle='#fff';ctx.fillRect(paddle.x,paddle.y,paddle.w,paddle.h); ctx.beginPath();ctx.arc(ball.x,ball.y,8,0,6.28);ctx.fill(); for(let b of bricks){if(!b.hit)ctx.fillStyle='#b33',ctx.fillRect(b.x,b.y,b.w,b.h); if(!b.hit && ball.x>b.x && ball.x<b.x+b.w && ball.y>b.y && ball.y<b.y+b.h){b.hit=true;ball.dy*=-1;} } if(ball.y>cv.height){clearInterval(id);alert('Game Over (Breakout)');}},16);}function cookie(){cv.width=600;cv.height=420;let cookies=0;draw();cv.onclick=e=>{let dx=e.offsetX-300,dy=e.offsetY-210;if(dx*dx+dy*dy<80*80){cookies++;draw();}};function draw(){ctx.fillStyle='#001';ctx.fillRect(0,0,cv.width,cv.height);ctx.fillStyle='#c47';ctx.beginPath();ctx.arc(300,210,80,0,6.28);ctx.fill();ctx.fillStyle='#fff';ctx.font='22px sans-serif';ctx.fillText('Cookies: '+cookies,20,30);} }function flappy(){cv.width=600;cv.height=420;let bird={x:100,y:200,vy:0},pipes=[],tick=0;document.onkeydown=e=>{if(e.key===' '||e.key==='Spacebar'){bird.vy=-6}};let id=setInterval(()=>{tick++;bird.vy+=0.35;bird.y+=bird.vy; if(tick%90===0){pipes.push({x:600,y:Math.random()*220+60});} ctx.fillStyle='#001';ctx.fillRect(0,0,cv.width,cv.height); ctx.fillStyle='yellow';ctx.beginPath();ctx.arc(bird.x,bird.y,12,0,6.28);ctx.fill(); for(let p of pipes){p.x-=2; ctx.fillStyle='#0b3'; ctx.fillRect(p.x,0,50,p.y-80); ctx.fillRect(p.x,p.y+80,50,cv.height); if(bird.x>p.x && bird.x<p.x+50 && (bird.y<p.y-80 || bird.y>p.y+80)){clearInterval(id);alert('Game Over (Flappy)');} } if(bird.y>cv.height||bird.y<0){clearInterval(id);alert('Game Over (Flappy)');}},20);}function shooter(){cv.width=600;cv.height=420;let ship={x:300,y:380,w:30,h:12},bullets=[],enemies=[],spawn=0;document.onmousemove=e=>{ship.x=e.clientX-cv.getBoundingClientRect().left;}document.onclick=()=>{bullets.push({x:ship.x+15,y:ship.y-6});};let id=setInterval(()=>{spawn++; if(spawn%40==0)enemies.push({x:Math.random()*560,y:-20}); bullets.forEach(b=>b.y-=8); enemies.forEach(en=>en.y+=2); ctx.fillStyle='#001';ctx.fillRect(0,0,cv.width,cv.height); ctx.fillStyle='white';ctx.fillRect(ship.x,ship.y,ship.w,ship.h); bullets.forEach(b=>ctx.fillRect(b.x,b.y,4,8)); enemies.forEach(en=>ctx.fillRect(en.x,en.y,32,16)); bullets.forEach((b,i)=>{enemies.forEach((en,j)=>{if(b.x>en.x&&b.x<en.x+32&&b.y>en.y&&b.y<en.y+16){enemies.splice(j,1);bullets.splice(i,1);}})}); if(enemies.some(en=>en.y>cv.height)) {clearInterval(id);alert('Game Over (Shooter)');}},30);}function g2048(){cv.width=600;cv.height=420;let grid=[[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0]];function addRand(){let empt=[];for(let r=0;r<4;r++)for(let c=0;c<4;c++)if(grid[r][c]===0)empt.push([r,c]); if(!empt.length)return;let [r,c]=empt[Math.floor(Math.random()*empt.length)];grid[r][c]=Math.random()<0.9?2:4;}function draw(){ctx.fillStyle='#001';ctx.fillRect(0,0,cv.width,cv.height);ctx.font='36px sans-serif';ctx.fillStyle='#fff';for(let r=0;r<4;r++)for(let c=0;c<4;c++){ctx.fillStyle=grid[r][c]?'#efefef':'#444';ctx.fillRect(c*140+20,r*100+20,120,80); ctx.fillStyle=grid[r][c]?'#000':'#fff';if(grid[r][c])ctx.fillText(grid[r][c],c*140+80,r*100+70);} } function slide(row){let arr=row.filter(v=>v),res=[];for(let v of arr){if(res.length&&res[res.length-1]===v){res[res.length-1]*=2;res.push(0);}else res.push(v);}res=res.filter(v=>v);while(res.length<4)res.push(0);return res;}function move(dir){let moved=false; if(dir==='left'){for(let r=0;r<4;r++){let old=grid[r].slice();grid[r]=slide(grid[r]);if(JSON.stringify(old)!==JSON.stringify(grid[r]))moved=true}} if(dir==='right'){for(let r=0;r<4;r++){let old=grid[r].slice();grid[r]=slide(grid[r].slice().reverse()).reverse();if(JSON.stringify(old)!==JSON.stringify(grid[r]))moved=true}} if(dir==='up'){for(let c=0;c<4;c++){let col=[];for(let r=0;r<4;r++)col.push(grid[r][c]);let old=col.slice();col=slide(col);for(let r=0;r<4;r++)grid[r][c]=col[r];if(JSON.stringify(old)!==JSON.stringify(col))moved=true}} if(dir==='down'){for(let c=0;c<4;c++){let col=[];for(let r=0;r<4;r++)col.push(grid[r][c]);let old=col.slice();col=slide(col.reverse()).reverse();for(let r=0;r<4;r++)grid[r][c]=col[r];if(JSON.stringify(old)!==JSON.stringify(col))moved=true}} if(moved)addRand();draw();}addRand();addRand();draw();window.onkeydown=e=>{if(e.key==='ArrowLeft')move('left');if(e.key==='ArrowRight')move('right');if(e.key==='ArrowUp')move('up');if(e.key==='ArrowDown')move('down');};}function startGame(name){window.onkeydown=null;document.onkeydown=null;if(name=='Snake')snakeGame();else if(name=='TicTacToe')ttt();else if(name=='Pong')pong();else if(name=='Breakout')breakout();else if(name=='CookieClicker')cookie();else if(name=='Flappy')flappy();else if(name=='Shooter')shooter();else if(name=='2048')g2048();}<\/script>');}catch(e){alert('Error: '+e);} })();">
           Drag: Games Hub
        </a>
      </div>

      <!-- Improved Mini Browser -->
      <div class="card">
        <div>
          <div class="title">Mini Browser (popup)</div>
          <div class="muted">Popup window where you can visit any URL.</div>
        </div>
        <a class="btn"
           href="javascript:(function(){try{var w=window.open('','miniBrowser','width=1000,height=700');if(!w){alert('Popup blocked — allow popups.');return;}w.document.write('<!doctype html><html><meta charset=\"utf-8\"><title>Mini Browser</title><style>body{margin:0;height:100vh;display:flex;flex-direction:column;font-family:sans-serif}#bar{display:flex;padding:8px;gap:8px;background:#222}input{flex:1;padding:8px;border-radius:6px;border:0}button{padding:8px;border-radius:6px;border:0;background:#0b5cff;color:#fff}iframe{flex:1;border:0}</style><div id=\"bar\"><input id=\"u\" placeholder=\"https://example.com\"><button id=\"g\">Go</button></div><iframe id=\"f\" src=\"about:blank\"></iframe><script>const input=document.getElementById(\"u\"),btn=document.getElementById(\"g\"),frame=document.getElementById(\"f\");function nav(){let v=input.value.trim(); if(!/^https?:\\/\\//.test(v))v='https://'+v; frame.src=v;} btn.onclick=nav; input.addEventListener('keydown',e=>{if(e.key==='Enter')nav();});</script></html>');}catch(e){alert(e);} })();">
           Drag: Mini Browser
        </a>
      </div>

      <!-- Script Injector -->
      <div class="card">
        <div>
          <div class="title">Script Injector (tamper-style)</div>
          <div class="muted">Popup where you paste JS and send to the opener to run. Only run trusted code.</div>
        </div>
        <a class="btn"
           href="javascript:(function(){try{var w=window.open('','ScriptInjector','width=700,height=520');if(!w){alert('Popup blocked — allow popups.');return;}w.document.write('<!doctype html><html><meta charset=\"utf-8\"><title>Script Injector</title><style>body{background:#0b1220;color:#e6eef8;font-family:monospace;padding:12px}textarea{width:100%;height:360px;background:#071026;color:#e6eef8;border-radius:8px;border:0;padding:8px;font-family:monospace}button{padding:8px 12px;border-radius:6px;border:0;background:#1f9fff;color:#03263b;font-weight:700;cursor:pointer;margin-right:8px}</style><div><h2>Script Injector</h2><div style=\"margin-bottom:8px;color:#9fb4d6\">Paste JavaScript below, click Inject to run it on the page that opened this bookmark. Do not run untrusted code.</div><textarea id=\"t\"></textarea><div style=\"margin-top:8px\"><button id=\"inj\">Inject</button><button id=\"save\">Save</button><button id=\"close\">Close</button></div><script>const ta=document.getElementById('t');document.getElementById('inj').onclick=()=>{try{opener.postMessage({__inject:ta.value},'*');alert('Sent script to parent');}catch(e){alert('Error: '+e)}};document.getElementById('save').onclick=()=>{localStorage.setItem('saved_inject',ta.value);alert('Saved');};document.getElementById('close').onclick=()=>window.close();ta.value=localStorage.getItem('saved_inject')||'';<\/script></div></html>'); if(!window.__scriptInjectorListener){window.__scriptInjectorListener=function(ev){try{if(ev.data&&ev.data.__inject){eval(ev.data.__inject);alert('Injected script executed');}}catch(e){alert('Injection error: '+e);}};window.addEventListener('message',window.__scriptInjectorListener);} }catch(e){alert('Error: '+e);} })();">
           Drag: Script Injector
        </a>
      </div>

      <!-- Simulate Crash (improved) -->
      <div class="card">
        <div>
          <div class="title">Simulate Crash (visual)</div>
          <div class="muted">Shows a full-screen overlay that looks like a crash. Press Esc or click Restore to remove. Reload restores page.</div>
        </div>
        <a class="btn"
           href="javascript:(function(){try{if(window.__simCrashActive){var o=document.getElementById('__simoverlay2'); if(o)o.remove(); window.__simCrashActive=false; document.removeEventListener('keydown',window.__simCrashEsc); return;} window.__simCrashActive=true; var restore=function(){var el=document.getElementById('__simoverlay2'); if(el)el.remove(); window.__simCrashActive=false; document.removeEventListener('keydown',window.__simCrashEsc);}; window.__simCrashEsc=function(e){if(e.key==='Escape')restore();}; document.addEventListener('keydown',window.__simCrashEsc); var overlay=document.createElement('div'); overlay.id='__simoverlay2'; overlay.style='position:fixed;inset:0;z-index:2147483647;display:flex;align-items:center;justify-content:center;background:linear-gradient(180deg,#000 0%,#0b0b0b 100%);color:#fff;font-family:system-ui,Segoe UI,Roboto,Arial,sans-serif;'; overlay.innerHTML = \"<div style='max-width:820px;margin:24px;text-align:center;padding:28px;border-radius:12px;backdrop-filter:blur(3px);'><div style='font-size:28px;font-weight:800;margin-bottom:10px;'>Aw, snap — the site became unresponsive</div><div style='margin-bottom:18px;color:#d1d5db;'>The page has encountered an error. Try reloading the page or restore below.</div><div style='margin:16px auto;display:flex;gap:12px;justify-content:center;align-items:center;'><div style=\"width:56px;height:56px;border-radius:50%;border:6px solid rgba(255,255,255,0.08);border-top-color:#1f9fff;animation:__spin 1s linear infinite;\"></div><button id='__simRestoreBtn' style='padding:10px 14px;border-radius:8px;border:0;background:#1f9fff;color:#012;font-weight:700;cursor:pointer;'>Restore Page</button><button id='__simReloadBtn' style='padding:10px 14px;border-radius:8px;border:0;background:#ef4444;color:#fff;font-weight:700;cursor:pointer;'>Reload</button></div><div style='margin-top:14px;color:#94a3b8;font-size:13px;'>Press <kbd style='background:#0b1220;padding:4px 6px;border-radius:4px;border:1px solid rgba(255,255,255,0.04)'>Esc</kbd> to restore, or click Restore.</div></div><style>@keyframes __spin{to{transform:rotate(360deg)}} button:active{transform:scale(.98)}</style>\"; document.body.appendChild(overlay); document.getElementById('__simRestoreBtn').onclick=restore; document.getElementById('__simReloadBtn').onclick=function(){location.reload()}; }catch(e){alert('Simulate Crash error: '+e);} })();">
           Drag: Simulate Crash
        </a>
      </div>

    </div>

    <footer>
      <div>Note: If you see code instead of the page, you are probably viewing the <code>raw</code> file. Open the GitHub Pages URL instead (Settings → Pages shows it).</div>
      <div style="margin-top:6px">Security: <strong>Do not</strong> run scripts you don't trust. The Script Injector will execute any code you paste.</div>
    </footer>
  </div>
</body>
</html>



