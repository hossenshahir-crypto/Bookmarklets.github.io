# Bookmarklets.github.io
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1"/>
<title>Bookmarklets — Games + Tools</title>
<style>
  body{font-family:system-ui,-apple-system,Segoe UI,Roboto,Arial;background:#0b1220;color:#e6eef8;margin:0;min-height:100vh;display:flex;align-items:center;justify-content:center;padding:28px}
  .wrap{max-width:980px;width:100%}
  h1{margin:0 0 12px;font-size:1.6rem;text-align:center}
  .grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));gap:14px;margin-top:14px}
  .card{background:#071026;padding:16px;border-radius:10px;border:1px solid rgba(255,255,255,0.04);display:flex;flex-direction:column;justify-content:space-between;min-height:120px}
  .title{font-weight:700;margin-bottom:8px}
  .muted{color:#9fb4d6;font-size:0.95rem;margin-bottom:12px}
  a.btn{display:inline-block;padding:10px 14px;border-radius:8px;background:#1f9fff;color:#03263b;text-decoration:none;font-weight:700;text-align:center;cursor:grab}
  a.btn:hover{filter:brightness(1.05)}
  footer{color:#8faac6;text-align:center;margin-top:18px;font-size:0.9rem}
  code{background:rgba(255,255,255,0.03);padding:3px 6px;border-radius:6px}
</style>
</head>
<body>
  <div class="wrap">
    <h1>🔖 Drag these to your bookmarks bar — Tools + Games Hub</h1>
    <div class="grid">

      <!-- Edit Page -->
      <div class="card">
        <div>
          <div class="title">Edit Page Text</div>
          <div class="muted">Toggle contentEditable so you can change visible text (reload to restore).</div>
        </div>
        <a class="btn" href="javascript:(function(){document.designMode=(document.designMode==='on'?'off':'on');document.body.contentEditable=(document.designMode==='on');alert('Edit mode: '+document.designMode);} )();">Drag: Edit text</a>
      </div>

      <!-- Dev Console -->
      <div class="card">
        <div>
          <div class="title">Developer Console (mini)</div>
          <div class="muted">Small in-page console for quick evals (safer than using browser devtools for bookmarklets).</div>
        </div>
        <a class="btn" href="javascript:(function(){try{if(window.__miniConsole&&window.__miniConsole.open){window.__miniConsole.toggle();return;}var c=window.open('','_blank','width=600,height=420,resizable=yes,scrollbars=yes');if(!c){alert('Popup blocked — allow popups.');return;}c.document.write('<!doctype html><html><meta charset=\"utf-8\"><title>Mini Console</title><style>body{background:#111;color:#eee;font-family:monospace;margin:0;display:flex;flex-direction:column;height:100vh}#out{flex:1;overflow:auto;padding:10px;background:#000}#in{display:flex;padding:8px;gap:6px}input{flex:1;padding:8px;border-radius:6px;border:0;background:#222;color:#fff}button{padding:8px;border-radius:6px;border:0;background:#0b5cff;color:#fff}</style><div id=\"out\">Console ready.\n</div><div id=\"in\"><input id=\"cmd\" placeholder=\"Type JS and press Enter\"><button id=\"run\">Run</button></div><script>const out=document.getElementById(\"out\"),cmd=document.getElementById(\"cmd\");function log(v){out.textContent+=String(v)+'\\n';out.scrollTop=out.scrollHeight;}document.getElementById('run').onclick=()=>{try{var r=eval(cmd.value);log('> '+cmd.value);log(r);}catch(e){log('Error: '+e);}cmd.value='';};cmd.addEventListener('keydown',e=>{if(e.key==='Enter'){document.getElementById('run').click();}});<\/script></html>');}catch(e){alert('Error: '+e);} })();">Drag: Dev Console</a>
      </div>

      <!-- Games Hub -->
      <div class="card">
        <div>
          <div class="title">Games Hub (many mini-games)</div>
          <div class="muted">Popup hosting Snake, Tic-Tac-Toe, Pong, Breakout, Cookie Clicker, Flappy Bird, Space Shooter, 2048.</div>
        </div>
        <a class="btn" href="javascript:(function(){
  try{
    var w=window.open('','GamesHub','width=860,height=700,resizable=yes,scrollbars=yes');
    if(!w){alert('Popup blocked — allow popups.');return;}
    w.document.write('<!doctype html><html><head><meta charset=\"utf-8\"><title>Games Hub</title><style>body{background:#050714;color:#e6eef8;font-family:sans-serif;margin:0;padding:14px}header{display:flex;align-items:center;gap:12px}h1{margin:0;font-size:20px}#bar{margin-top:10px;display:flex;gap:8px;flex-wrap:wrap}button{background:#1572e8;color:#fff;border:0;padding:8px 12px;border-radius:8px;cursor:pointer;font-weight:700}canvas{display:block;margin-top:12px;border-radius:8px;background:#000;}</style></head><body><header><h1>🎮 Games Hub</h1></header><div id=\"bar\"></div><canvas id=\"cv\" width=\"600\" height=\"420\"></canvas><div style=\"margin-top:10px\"><button id=\"close\">Close</button></div><script>'
+
/* helper: UI buttons */
'const games=[\"Snake\",\"TicTacToe\",\"Pong\",\"Breakout\",\"CookieClicker\",\"Flappy\",\"Space\",\"2048\"];const bar=document.getElementById(\"bar\"),cv=document.getElementById(\"cv\"),ctx=cv.getContext(\"2d\");games.forEach(g=>{let b=document.createElement(\"button\");b.textContent=g;b.onclick=()=>startGame(g);bar.appendChild(b);});document.getElementById(\"close\").onclick=()=>window.close();'
+
/* Snake */
+'function snakeGame(){let S=20,cols=30,rows=21;cv.width=cols*S;cv.height=rows*S;let px=5,py=5,dx=1,dy=0,trail=[],tail=5,food={x:10,y:10};document.onkeydown=e=>{if(e.key.includes(\"Arrow\")){dx=(e.key==\"ArrowLeft\"?-1:e.key==\"ArrowRight\"?1:0);dy=(e.key==\"ArrowUp\"?-1:e.key==\"ArrowDown\"?1:0);}};let id=setInterval(()=>{px+=dx;py+=dy; if(px<0)px=cols-1;if(px>=cols)px=0;if(py<0)py=rows-1;if(py>=rows)py=0; ctx.fillStyle='#001';ctx.fillRect(0,0,cv.width,cv.height); ctx.fillStyle='lime'; trail.forEach(s=>ctx.fillRect(s.x*S,s.y*S,S-2,S-2)); trail.push({x:px,y:py}); while(trail.length>tail)trail.shift(); if(food.x==px&&food.y==py){tail++; food={x:Math.floor(Math.random()*cols),y:Math.floor(Math.random()*rows)} } ctx.fillStyle='red'; ctx.fillRect(food.x*S,food.y*S,S-2,S-2); if(trail.slice(0,-1).some(s=>s.x==px&&s.y==py)){clearInterval(id);alert('Game Over (Snake)');}},90); }'
/* TicTacToe */
+'function ttt(){cv.width=600;cv.height=600;let b=Array(9).fill(\"\");let turn=\"X\";draw();cv.onclick=e=>{let x=Math.floor(e.offsetX/200),y=Math.floor(e.offsetY/200),i=y*3+x;if(!b[i]){b[i]=turn;turn=(turn==\"X\"?\"O\":\"X\");draw();}};function draw(){ctx.fillStyle=\"#001\";ctx.fillRect(0,0,cv.width,cv.height);ctx.strokeStyle=\"#fff\";for(let i=1;i<3;i++){ctx.beginPath();ctx.moveTo(i*200,0);ctx.lineTo(i*200,600);ctx.moveTo(0,i*200);ctx.lineTo(600,i*200);ctx.stroke();}ctx.fillStyle=\"#fff\";ctx.font='120px sans-serif';ctx.textAlign='center';ctx.textBaseline='middle';for(let i=0;i<9;i++){if(b[i])ctx.fillText(b[i],(i%3)*200+100,Math.floor(i/3)*200+100);} }}'
/* Pong */
+'function pong(){cv.width=600;cv.height=420;let ball={x:300,y:210,dx:4,dy:3},paddleY=160;document.onmousemove=e=>{paddleY=e.clientY - cv.getBoundingClientRect().top - 50}; let id=setInterval(()=>{ball.x+=ball.dx;ball.y+=ball.dy;if(ball.y<0||ball.y>420)ball.dy*=-1;if(ball.x<0||ball.x>600)ball.dx*=-1; ctx.fillStyle=\"#001\";ctx.fillRect(0,0,cv.width,cv.height); ctx.fillStyle='#fff'; ctx.fillRect(580,paddleY,12,100); ctx.beginPath(); ctx.arc(ball.x,ball.y,8,0,6.28); ctx.fill(); if(ball.x>572 && ball.y>paddleY && ball.y<paddleY+100){ball.dx*=-1;} if(ball.x>600){clearInterval(id);alert('Game Over (Pong)');}},16);}'
/* Breakout */
+'function breakout(){cv.width=600;cv.height=420;let bricks=[];for(let r=0;r<4;r++)for(let c=0;c<8;c++)bricks.push({x:70*c+10,y:30*r+10,w:64,h:18,hit:false});let paddle={x:260,y:380,w:80,h:12},ball={x:300,y:200,dx:3,dy:3};document.onmousemove=e=>{paddle.x = e.clientX - cv.getBoundingClientRect().left - paddle.w/2;} let id=setInterval(()=>{ball.x+=ball.dx;ball.y+=ball.dy; if(ball.x<0||ball.x>cv.width)ball.dx*=-1;if(ball.y<0)ball.dy*=-1; if(ball.y>paddle.y && ball.x>paddle.x && ball.x<paddle.x+paddle.w){ball.dy*=-1;} ctx.fillStyle='#001';ctx.fillRect(0,0,cv.width,cv.height); ctx.fillStyle='#fff';ctx.fillRect(paddle.x,paddle.y,paddle.w,paddle.h); ctx.beginPath();ctx.arc(ball.x,ball.y,8,0,6.28);ctx.fill(); for(let b of bricks){if(!b.hit){ctx.fillStyle='#b33';ctx.fillRect(b.x,b.y,b.w,b.h);} if(!b.hit && ball.x>b.x && ball.x<b.x+b.w && ball.y>b.y && ball.y<b.y+b.h){b.hit=true;ball.dy*=-1;} } if(ball.y>cv.height){clearInterval(id);alert('Game Over (Breakout)');}},16);}'
/* Cookie Clicker */
+'function cookie(){cv.width=600;cv.height=420;let cookies=0;draw();cv.onclick=e=>{let dx=e.offsetX-300,dy=e.offsetY-210;if(dx*dx+dy*dy<80*80){cookies++;draw();}};function draw(){ctx.fillStyle=\"#001\";ctx.fillRect(0,0,cv.width,cv.height);ctx.fillStyle=\"#c47\";ctx.beginPath();ctx.arc(300,210,80,0,6.28);ctx.fill();ctx.fillStyle=\"#fff\";ctx.font=\"22px sans-serif\";ctx.fillText('Cookies: '+cookies,20,30);} }'
/* Flappy */
+'function flappy(){cv.width=600;cv.height=420;let bird={x:100,y:200,vy:0},pipes=[],tick=0;document.onkeydown=e=>{if(e.key===' '||e.key==='Spacebar'){bird.vy=-6}};let id=setInterval(()=>{tick++;bird.vy+=0.35;bird.y+=bird.vy; if(tick%90===0){pipes.push({x:600,y:Math.random()*220+60});} ctx.fillStyle=\"#001\";ctx.fillRect(0,0,cv.width,cv.height); ctx.fillStyle='yellow';ctx.beginPath();ctx.arc(bird.x,bird.y,12,0,6.28);ctx.fill(); for(let p of pipes){p.x-=2; ctx.fillStyle='#0b3'; ctx.fillRect(p.x,0,50,p.y-80); ctx.fillRect(p.x,p.y+80,50,cv.height); if(bird.x>p.x && bird.x<p.x+50 && (bird.y<p.y-80 || bird.y>p.y+80)){clearInterval(id);alert('Game Over (Flappy)');} } if(bird.y>cv.height||bird.y<0){clearInterval(id);alert('Game Over (Flappy)');}},20);}'
/* Space Shooter */
+'function shooter(){cv.width=600;cv.height=420;let ship={x:300,y:380,w:30,h:12},bullets=[],enemies=[],spawn=0;document.onmousemove=e=>{ship.x=e.clientX-cv.getBoundingClientRect().left;}document.onclick=()=>{bullets.push({x:ship.x+15,y:ship.y-6});};let id=setInterval(()=>{spawn++; if(spawn%40==0)enemies.push({x:Math.random()*560,y:-20}); bullets.forEach(b=>b.y-=8); enemies.forEach(en=>en.y+=2); ctx.fillStyle='#001';ctx.fillRect(0,0,cv.width,cv.height); ctx.fillStyle='white';ctx.fillRect(ship.x,ship.y,ship.w,ship.h); bullets.forEach(b=>ctx.fillRect(b.x,b.y,4,8)); enemies.forEach(en=>ctx.fillRect(en.x,en.y,32,16)); bullets.forEach((b,i)=>{enemies.forEach((en,j)=>{if(b.x>en.x&&b.x<en.x+32&&b.y>en.y&&b.y<en.y+16){enemies.splice(j,1);bullets.splice(i,1);}})}); if(enemies.some(en=>en.y>cv.height)) {clearInterval(id);alert('Game Over (Shooter)');}},30);}'
/* 2048 - minimal */
+'function g2048(){cv.width=600;cv.height=420;let grid=[[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0]];function addRand(){let empt=[];for(let r=0;r<4;r++)for(let c=0;c<4;c++)if(grid[r][c]===0)empt.push([r,c]); if(!empt.length)return;let [r,c]=empt[Math.floor(Math.random()*empt.length)];grid[r][c]=Math.random()<0.9?2:4;}function draw(){ctx.fillStyle='#001';ctx.fillRect(0,0,cv.width,cv.height);ctx.font='36px sans-serif';ctx.fillStyle='#fff';for(let r=0;r<4;r++)for(let c=0;c<4;c++){ctx.fillStyle=grid[r][c]?'#efefef':'#444';ctx.fillRect(c*140+20,r*100+20,120,80); ctx.fillStyle=grid[r][c]?'#000':'#fff';if(grid[r][c])ctx.fillText(grid[r][c],c*140+80,r*100+70);} } function move(dir){let moved=false; function slide(row){let arr=row.filter(v=>v),res=[]; for(let v of arr){ if(res.length&&res[res.length-1]===v){res[res.length-1]*=2;res.push(0);}else res.push(v);} res=res.filter(v=>v); while(res.length<4)res.push(0); return res;} if(dir==='left'){for(let r=0;r<4;r++){let old=grid[r].slice(); grid[r]=slide(grid[r]); if(JSON.stringify(old)!==JSON.stringify(grid[r]))moved=true}} if(dir==='right'){for(let r=0;r<4;r++){let old=grid[r].slice(); grid[r]=slide(grid[r].slice().reverse()).reverse(); if(JSON.stringify(old)!==JSON.stringify(grid[r]))moved=true}} if(dir==='up'){for(let c=0;c<4;c++){let col=[];for(let r=0;r<4;r++)col.push(grid[r][c]); let old=col.slice(); col=slide(col); for(let r=0;r<4;r++)grid[r][c]=col[r]; if(JSON.stringify(old)!==JSON.stringify(col))moved=true}} if(dir==='down'){for(let c=0;c<4;c++){let col=[];for(let r=0;r<4;r++)col.push(grid[r][c]); let old=col.slice(); col=slide(col.reverse()).reverse(); for(let r=0;r<4;r++)grid[r][c]=col[r]; if(JSON.stringify(old)!==JSON.stringify(col))moved=true}} if(moved)addRand(); draw();} addRand();addRand();draw(); window.onkeydown=e=>{if(e.key==='ArrowLeft')move('left'); if(e.key==='ArrowRight')move('right'); if(e.key==='ArrowUp')move('up'); if(e.key==='ArrowDown')move('down');}; }'
/* Start switcher */
+'function startGame(name){window.onkeydown=null;document.onkeydown=null; if(name==\"Snake\")snakeGame(); else if(name==\"TicTacToe\")ttt(); else if(name==\"Pong\")pong(); else if(name==\"Breakout\")breakout(); else if(name==\"CookieClicker\")cookie(); else if(name==\"Flappy\")flappy(); else if(name==\"Space\")shooter(); else if(name==\"2048\")g2048(); }'
+
'</script></body></html>');
  }catch(e){alert('Error launching Games Hub: '+e);}
})();">Drag: Games Hub</a>
      </div>

      <!-- Mini Browser (improved popup) -->
      <div class="card">
        <div>
          <div class="title">Mini Browser (popup)</div>
          <div class="muted">Popup window where you can navigate to any URL.</div>
        </div>
        <a class="btn" href="javascript:(function(){try{var w=window.open('','miniBrowser','width=1000,height=700,resizable=yes,scrollbars=yes');if(!w){alert('Popup blocked — allow popups.');return;}w.document.write('<!doctype html><html><meta charset=\"utf-8\"><title>Mini Browser</title><style>body{margin:0;height:100vh;display:flex;flex-direction:column;font-family:sans-serif}#bar{display:flex;padding:8px;gap:8px;background:#222}input{flex:1;padding:8px;border-radius:6px;border:0}button{padding:8px;border-radius:6px;border:0;background:#0b5cff;color:#fff}iframe{flex:1;border:0}</style><div id=\"bar\"><input id=\"u\" placeholder=\"https://example.com\"><button id=\"g\">Go</button></div><iframe id=\"f\" src=\"about:blank\"></iframe><script>const input=document.getElementById(\"u\"),btn=document.getElementById(\"g\"),frame=document.getElementById(\"f\");function nav(){let v=input.value.trim(); if(!/^https?:\\/\\//.test(v))v='https://'+v; frame.src=v;} btn.onclick=nav; input.addEventListener('keydown',e=>{if(e.key==='Enter')nav();});</script></html>');}catch(e){alert(e);} })();">Drag: Mini Browser</a>
      </div>

      <!-- Script Injector (Tampermonkey-like) -->
      <div class="card">
        <div>
          <div class="title">Script Injector (paste & inject)</div>
          <div class="muted">Opens a popup where you can paste JS to run on the current page. <strong>Only run scripts you trust.</strong></div>
        </div>
        <a class="btn" href="javascript:(function(){try{var w=window.open('','ScriptInjector','width=700,height=520,resizable=yes,scrollbars=yes');if(!w){alert('Popup blocked — allow popups.');return;}w.document.write('<!doctype html><html><meta charset=\"utf-8\"><title>Script Injector</title><style>body{background:#0b1220;color:#e6eef8;font-family:monospace;padding:12px}textarea{width:100%;height:360px;background:#071026;color:#e6eef8;border-radius:8px;border:0;padding:8px;font-family:monospace}button{padding:8px 12px;border-radius:6px;border:0;background:#1f9fff;color:#03263b;font-weight:700;cursor:pointer;margin-right:8px}</style><div><h2>Script Injector</h2><div style=\"margin-bottom:8px;color:#9fb4d6\">Paste JavaScript below, click Inject to run it on the page that opened this bookmark. Do not run untrusted code.</div><textarea id=\"t\"></textarea><div style=\"margin-top:8px\"><button id=\"inj\">Inject</button><button id=\"save\">Save</button><button id=\"close\">Close</button></div><script>const ta=document.getElementById('t');document.getElementById('inj').onclick=()=>{try{opener.postMessage({__inject:ta.value},'*');alert('Sent script to parent');}catch(e){alert('Error: '+e)}};document.getElementById('save').onclick=()=>{localStorage.setItem('saved_inject',ta.value);alert('Saved');};document.getElementById('close').onclick=()=>window.close();ta.value=localStorage.getItem('saved_inject')||'';</script></div></html>'); // set listener in parent to receive and run
          // parent listener:
          if(!window.__scriptInjectorListener){window.__scriptInjectorListener=function(ev){try{if(ev.data&&ev.data.__inject){eval(ev.data.__inject);alert('Injected script executed');}}catch(e){alert('Injection error: '+e);}};window.addEventListener('message',window.__scriptInjectorListener);}" }catch(e){alert('Error: '+e);} })();">Drag: Script Injector</a>
      </div>

      <!-- Simulate Crash (safe) -->
      <div class="card">
        <div>
          <div class="title">Simulate Crash (safe)</div>
          <div class="muted">Temporarily hides the page content to simulate a crash. Reload to restore. (Non-destructive.)</div>
        </div>
        <a class="btn" href="javascript:(function(){if(document.__simHide){document.body.style.filter='';document.__simHide=false;alert('Restored page (reload to fully reset).');return;}var overlay=document.createElement('div');overlay.id='__simoverlay';overlay.style.position='fixed';overlay.style.inset='0';overlay.style.background='#000';overlay.style.color='#fff';overlay.style.display='flex';overlay.style.alignItems='center';overlay.style.justifyContent='center';overlay.style.zIndex=2147483647;overlay.innerHTML='<div style=\"text-align:center;font-family:system-ui;padding:20px\"><h1>Site is unresponsive</h1><p style=\"opacity:0.85\">Reload the page to restore.</p></div>';document.body.appendChild(overlay);document.__simHide=true;alert('Page visually hidden — reload the page to fully restore.');})();">Drag: Simulate Crash</a>
      </div>

    </div>

    <footer>
      <div>Refused to build destructive "crash" bookmarklet. The <em>Simulate Crash</em> bookmarklet above is a harmless, reversible visual-only alternative.</div>
      <div style="margin-top:6px">Security: <strong>Do not</strong> use the Script Injector with code from untrusted sources. Bookmarklets run code in the context of the page — they can access and send data from that page.</div>
    </footer>
  </div>
</body>
</html>


