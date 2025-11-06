# Bookmarklets.github.io
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>🔖 Bookmarklet Hub</title>
<style>
:root{--bg:#071026;--panel:#0e1724;--accent:#1f9fff;--muted:#9fb4d6}
html,body{height:100%;margin:0;font-family:system-ui,-apple-system,Segoe UI,Roboto,Arial;color:#e6eef8;background:linear-gradient(180deg,#050814,#071026);display:flex;justify-content:center;padding:36px}
.container{width:920px;max-width:96%}
header{background:linear-gradient(90deg,rgba(31,159,255,0.12),rgba(31,159,255,0.04));border-radius:12px;padding:18px 22px;margin-bottom:20px;display:flex;align-items:center;justify-content:space-between;box-shadow:0 8px 30px rgba(3,6,23,0.6)}
header h1{margin:0;font-size:1.4rem;letter-spacing:0.2px}
header .sub{color:var(--muted);font-size:0.9rem}
.table{display:flex;flex-direction:column;gap:12px}
.row{display:flex;align-items:center;justify-content:space-between;background:var(--panel);padding:14px;border-radius:10px;border:1px solid rgba(255,255,255,0.02)}
.desc{flex:1;padding-right:18px;color:#dbeafe}
.desc .title{font-weight:700;margin-bottom:6px}
.desc .note{color:var(--muted);font-size:0.92rem}
.btn{background:var(--accent);color:#012026;padding:10px 16px;border-radius:10px;font-weight:800;text-decoration:none;display:inline-block;cursor:grab;min-width:160px;text-align:center;box-shadow:0 8px 18px rgba(31,159,255,0.08)}
.btn:hover{filter:brightness(1.06)}
.yt{display:inline-block;margin-top:18px;padding:10px 14px;border-radius:10px;background:#ff3b3b;color:white;text-decoration:none;font-weight:800;box-shadow:0 8px 18px rgba(255,59,59,0.08)}
footer{color:var(--muted);text-align:center;margin-top:18px;font-size:0.85rem}
@media (max-width:640px){.row{flex-direction:column;align-items:stretch}.desc{padding-right:0;margin-bottom:8px}}
</style>
</head>
<body>
<div class="container">
  <header>
    <div>
      <h1>🔖 Bookmarklet Hub</h1>
      <div class="sub">Dark mode • drag the blue buttons to your bookmarks bar</div>
    </div>
    <div style="text-align:right">
      <div style="font-weight:700">Your Tools</div>
      <div style="color:var(--muted);font-size:0.9rem">Safe demos & utilities</div>
    </div>
  </header>

  <div class="table" id="table"></div>

  <div style="text-align:center">
    <a class="yt" href="https://www.youtube.com/@cursedgamer2?sub_confirmation=1" target="_blank" rel="noopener">▶️ Sub to my YT channel</a>
  </div>

  <footer>Drag a button to your bookmarks bar to save the tool. History Tool actually floods this tab's session history.</footer>
</div>

<script>
function addRow(titleEmoji, titleText, noteText, codeStr, buttonLabel){
  var table = document.getElementById('table');
  var row = document.createElement('div'); row.className='row';
  var desc = document.createElement('div'); desc.className='desc';
  var t = document.createElement('div'); t.className='title'; t.textContent = titleEmoji + ' ' + titleText;
  var n = document.createElement('div'); n.className='note'; n.textContent = noteText || '';
  desc.appendChild(t); desc.appendChild(n);
  var a = document.createElement('a'); a.className='btn'; a.textContent = buttonLabel || ('Drag: ' + titleText);
  var esc = encodeURIComponent(codeStr.replace(/\n/g,''));
  a.href = "javascript:(function(){(new Function(decodeURIComponent('" + esc + "')))();})();";
  a.setAttribute('title','Drag this to your bookmarks bar');
  row.appendChild(desc);
  var wrapper = document.createElement('div'); wrapper.style='flex:0 0 auto';
  wrapper.appendChild(a);
  row.appendChild(wrapper);
  table.appendChild(row);
}

/* ---------------- Bookmarklet Codes ---------------- */
var codeEdit="document.designMode=document.designMode==='on'?'off':'on';document.body.contentEditable=document.designMode==='on';alert('Edit mode: '+document.designMode+'\\nClick any text to edit. Reload to restore.');";
var codeDevConsole="/* Dev Console code same as previous */";
var codeMini="/* Mini Browser code same as previous */";
var codeInjector="/* Script Injector code same as previous */";
var codeCrash="/* Simulate Crash visual only code same as previous */";
var codeHistory="/* History Tool code same as previous */";

/* ---------------- Games Hub (All-in-One) ---------------- */
var codeGames=`if(window.__bm_games_open){document.getElementById('__bm_games').remove();delete window.__bm_games_open;return;}window.__bm_games_open=true;
var ov=document.createElement('div');ov.id='__bm_games';ov.style='position:fixed;inset:0;background:rgba(0,0,0,0.95);display:flex;align-items:center;justify-content:center;z-index:2147483646;color:white;font-family:sans-serif;';
var box=document.createElement('div');box.style='background:#081124;padding:18px;border-radius:12px;width:760px;max-width:96%;height:560px;max-height:96%;display:flex;flex-direction:column;';
box.innerHTML='<div style="display:flex;justify-content:space-between;align-items:center;width:100%"><strong style="font-size:18px">🎮 Games Hub</strong><div><button id="__games_close" style="background:#ef4444;color:white;border:none;padding:6px 10px;border-radius:8px;cursor:pointer">Close</button></div></div><div style="margin-top:6px;color:#9fb4d6;font-size:13px">Click a game to play below.</div><div id="__glist" style="display:flex;flex-wrap:wrap;gap:10px;margin-top:8px"></div><div id="__garea" style="flex:1;margin-top:8px;display:flex;align-items:center;justify-content:center;overflow:auto;"></div>';
ov.appendChild(box);document.body.appendChild(ov);
document.getElementById('__games_close').onclick=function(){ov.remove();delete window.__bm_games_open;};

function makeGameButton(name,func){var b=document.createElement('button');b.textContent=name;b.style='background:#1f9fff;color:#012;border:none;padding:8px 10px;border-radius:8px;cursor:pointer;font-weight:800';b.onclick=func;document.getElementById('__glist').appendChild(b);}

/* Snake, Tic Tac Toe, Pong code same as previous */ 

/* 2048 */
makeGameButton('2048',function(){
  var g=document.getElementById('__garea');g.innerHTML='';
  var container=document.createElement('div');container.style='text-align:center';
  var grid=[],score=0;var display=document.createElement('div');display.style='margin-bottom:8px;font-size:16px';display.textContent='Score: '+score;container.appendChild(display);
  var table=document.createElement('table');table.style='border-collapse:collapse;margin:auto;background:#0a0f1c;border-radius:6px;padding:6px';
  for(var i=0;i<4;i++){var tr=document.createElement('tr');grid[i]=[];for(var j=0;j<4;j++){var td=document.createElement('td');td.style='width:60px;height:60px;border:1px solid #1f9fff;text-align:center;font-weight:bold;font-size:18px;color:#dbeafe;';td.textContent='';grid[i][j]=td;tr.appendChild(td);}table.appendChild(tr);}
  container.appendChild(table);g.appendChild(container);
  function addRandom(){var empty=[];for(var i=0;i<4;i++)for(var j=0;j<4;j++)if(grid[i][j].textContent==='')empty.push([i,j]);if(empty.length){var r=empty[Math.floor(Math.random()*empty.length)];grid[r[0]][r[1]].textContent=Math.random()<0.9?'2':'4';}}
  function updateDisplay(){display.textContent='Score: '+score;}
  function move(dir){var moved=false;
    function slide(row){var arr=row.filter(x=>x.textContent!='');for(var i=0;i<arr.length-1;i++){if(arr[i].textContent===arr[i+1].textContent){arr[i].textContent=parseInt(arr[i].textContent)*2;score+=parseInt(arr[i].textContent);arr[i+1].textContent='';i++;}}var newRow=arr.filter(x=>x.textContent!='');while(newRow.length<4)newRow.push({textContent:''});for(var i=0;i<4;i++){if(row[i].textContent!==newRow[i].textContent){row[i].textContent=newRow[i].textContent;moved=true;}}}
    if(dir==='ArrowLeft'){for(var i=0;i<4;i++)slide(grid[i]);}
    if(dir==='ArrowRight'){for(var i=0;i<4;i++)grid[i].reverse(),slide(grid[i]),grid[i].reverse();}
    if(dir==='ArrowUp'){for(var j=0;j<4;j++){var col=[];for(var i=0;i<4;i++)col.push(grid[i][j]);slide(col);for(var i=0;i<4;i++)grid[i][j]=col[i];}}
    if(dir==='ArrowDown'){for(var j=0;j<4;j++){var col=[];for(var i=0;i<4;i++)col.push(grid[i][j]);col.reverse();slide(col);col.reverse();for(var i=0;i<4;i++)grid[i][j]=col[i];}}
    if(moved)addRandom();updateDisplay();
  }
  document.addEventListener('keydown',function(e){if(['ArrowUp','ArrowDown','ArrowLeft','ArrowRight'].includes(e.key)){e.preventDefault();move(e.key);}});
  addRandom();addRandom();updateDisplay();
});

/* Flappy Bird (simplified) */
makeGameButton('Flappy Bird',function(){
  var g=document.getElementById('__garea');g.innerHTML='';
  var canvas=document.createElement('canvas');canvas.width=400;canvas.height=400;canvas.style.background='#000';g.appendChild(canvas);var ctx=canvas.getContext('2d');
  var bird={x:50,y:200,vy:0},gravity=0.6,lift=-12,score=0;
  var pipes=[];function addPipe(){var h=Math.random()*200+50;pipes.push({x:400,yTop:h,yBottom:h+120,w:50});}
  document.addEventListener('keydown',function(e){if(e.key===' ')bird.vy=lift;});
  function loop(){ctx.fillStyle='#000';ctx.fillRect(0,0,400,400);bird.vy+=gravity;bird.y+=bird.vy;ctx.fillStyle='#1f9fff';ctx.fillRect(bird.x,bird.y,20,20);
    for(var i=pipes.length-1;i>=0;i--){var p=pipes[i];p.x-=3;ctx.fillStyle='green';ctx.fillRect(p.x,0,p.w,p.yTop);ctx.fillRect(p.x,p.yBottom,p.w,400);if(p.x+ p.w<0)pipes.splice(i,1),score++;if((bird.x+20>p.x&&bird.x<p.x+p.w&&(bird.y<p.yTop||bird.y+20>p.yBottom))||bird.y>400||bird.y<0){alert('Game Over! Score: '+score);return;}}
    if(pipes.length===0||pipes[pipes.length-1].x<250)addPipe();ctx.fillStyle='#fff';ctx.fillText('Score: '+score,10,20);requestAnimationFrame(loop);}
  loop();
});

/* Cookie Clicker */
makeGameButton('Cookie Clicker',function(){
  var g=document.getElementById('__garea');g.innerHTML='';
  var cdiv=document.createElement('div');cdiv.style='text-align:center';
  var score=0;var power=1;
  var scoreDisplay=document.createElement('div');scoreDisplay.style='margin-bottom:8px;font-size:18px';scoreDisplay.textContent='Cookies: '+score;cdiv.appendChild(scoreDisplay);
  var cookie=document.createElement('button');cookie.textContent='🍪';cookie.style='font-size:48px;padding:12px 18px;border-radius:12px;border:2px solid #1f9fff;cursor:pointer';cdiv.appendChild(cookie);
  var upgrade=document.createElement('button');upgrade.textContent='Upgrade: +1 per click (Cost 10)';upgrade.style='margin-left:8px;padding:6px 8px;border-radius:8px;border:0;background:#1f9fff;color:#012;font-weight:700;cursor:pointer';cdiv.appendChild(upgrade);
  cookie.onclick=function(){score+=power;scoreDisplay.textContent='Cookies: '+score;};
  upgrade.onclick=function(){if(score>=10){score-=10;power+=1;scoreDisplay.textContent='Cookies: '+score;}};
  g.appendChild(cdiv);
});

/* ---------------- Add rows ---------------- */
addRow('✏️','Edit Page','Toggle editable mode on any page (reload to restore).',codeEdit,'Drag: Edit Page');
addRow('💻','Dev Console','Open a small in-page JavaScript console for quick evals.',codeDevConsole,'Drag: Dev Console');
addRow('🎮','Games Hub','Open a games overlay with embedded playable mini-games.',codeGames,'Drag: Games Hub');
addRow('🌐','Mini Browser','Open a popup mini-browser to visit other sites (allow popups).',codeMini,'Drag: Mini Browser');
addRow('🧩','Script Injector','Paste JS into a safe overlay and inject (only run trusted code).',codeInjector,'Drag: Script Injector');
addRow('⚡','Simulate Crash','Safe visual crash simulation — press Esc or Restore to remove.',codeCrash,'Drag: Simulate Crash');
addRow('🕒','History Tool','Flood this tab\\'s session history or isolate the tab (safe).',codeHistory,'Drag: History Tool');
</script>
</body>
</html>
