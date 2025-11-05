# Bookmarklets.github.io
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8"/>
<title>Bookmarklets Hub</title>
<style>
body{font-family:sans-serif;background:#071126;color:#fff;padding:20px}
h1{text-align:center}
button{display:block;margin:10px auto;padding:10px 14px;background:#1f9fff;color:#012;border:none;border-radius:6px;cursor:grab;min-width:200px;font-weight:700}
</style>
</head>
<body>
<h1>Drag these to your bookmarks bar</h1>

<button id="edit">Edit Page</button>
<button id="console">Dev Console</button>
<button id="games">Games Hub</button>
<button id="mini">Mini Browser</button>
<button id="injector">Script Injector</button>
<button id="crash">Simulate Crash</button>

<script>
// 1) Edit Page
document.getElementById('edit').href="javascript:(function(){document.designMode=document.designMode==='on'?'off':'on';document.body.contentEditable=document.designMode==='on';alert('Edit mode: '+document.designMode);})();";

// 2) Dev Console Overlay
document.getElementById('console').href="javascript:(function(){if(window.__bm_console_open){var e=document.getElementById('__bm_console');if(e)e.style.display=e.style.display==='none'?'flex':'none';return;}window.__bm_console_open=true;var w=document.createElement('div');w.id='__bm_console';w.style='position:fixed;right:20px;bottom:20px;width:400px;height:250px;background:#0b1320;color:#fff;border-radius:10px;padding:8px;display:flex;flex-direction:column;z-index:2147483647;font-family:monospace';var t=document.createElement('div');t.style='display:flex;justify-content:space-between';t.innerHTML='<strong>Mini Console</strong><button id=closec style=\"cursor:pointer\">✕</button>';w.appendChild(t);var out=document.createElement('pre');out.style='flex:1;overflow:auto;background:#001026;border-radius:6px;padding:6px;margin-top:4px';out.textContent='Console ready\\n';w.appendChild(out);var inp=document.createElement('input');inp.placeholder='Type JS and press Enter';inp.style='width:100%;padding:6px;margin-top:4px;border-radius:6px;border:none;background:#001026;color:#fff';w.appendChild(inp);document.body.appendChild(w);inp.addEventListener('keydown',function(e){if(e.key==='Enter'){try{var r=eval(inp.value);out.textContent+='> '+inp.value+'\\n'+r+'\\n';}catch(er){out.textContent+='Error:'+er+'\\n';}inp.value='';}});document.getElementById('closec').onclick=function(){w.remove();window.__bm_console_open=false;};})()";

// 3) Games Hub
document.getElementById('games').href="javascript:(function(){if(window.__bm_games_open){var e=document.getElementById('__bm_games');if(e)e.style.display=e.style.display==='none'?'flex':'none';return;}window.__bm_games_open=true;var o=document.createElement('div');o.id='__bm_games';o.style='position:fixed;inset:0;background:rgba(2,6,23,0.85);display:flex;align-items:center;justify-content:center;z-index:2147483647;font-family:sans-serif';var p=document.createElement('div');p.style='background:#081124;padding:12px;border-radius:12px;width:800px;height:600px;display:flex;flex-direction:column;color:#fff';var h=document.createElement('div');h.style='display:flex;justify-content:space-between;align-items:center';h.innerHTML='<strong style=\"font-size:18px\">Games Hub</strong>';var c=document.createElement('button');c.textContent='Close';c.style='cursor:pointer';c.onclick=function(){o.remove();window.__bm_games_open=false;};h.appendChild(c);p.appendChild(h);var bwrap=document.createElement('div');bwrap.style='display:flex;flex-wrap:wrap;gap:8px;margin-top:10px';['Snake','TicTacToe','Pong','Breakout','2048','Flappy','Shooter','CookieClicker'].forEach(function(g){var b=document.createElement('button');b.textContent=g;b.style='padding:8px;background:#1f9fff;color:#012;border:none;border-radius:6px;cursor:pointer;font-weight:700';b.onclick=function(){alert('Launch '+g+' game');};bwrap.appendChild(b);});p.appendChild(bwrap);o.appendChild(p);document.body.appendChild(o);})()";

// 4) Mini Browser
document.getElementById('mini').href="javascript:(function(){var w=window.open('','MiniBrowser','width=1000,height=700,resizable=yes,scrollbars=yes');if(!w){alert('Popup blocked');return;}w.document.write('<!doctype html><html><head><meta charset=\"utf-8\"><title>Mini Browser</title><style>body{margin:0;height:100vh;display:flex;flex-direction:column;font-family:sans-serif}#bar{display:flex;padding:8px;gap:8px}input{flex:1;padding:6px;border-radius:6px;border:1px solid #ccc}button{padding:6px;border-radius:6px;border:0;background:#1f9fff;color:#012;cursor:pointer}iframe{flex:1;border:0}</style></head><body><div id=\"bar\"><input id=\"u\" placeholder=\"https://example.com\"><button id=\"g\">Go</button></div><iframe id=\"f\" src=\"about:blank\"></iframe><script>const i=document.getElementById(\"u\"),b=document.getElementById(\"g\"),fr=document.getElementById(\"f\");b.onclick=function(){var v=i.value.trim();if(!/^https?:\\/\\//.test(v))v='https://'+v;fr.src=v;};i.addEventListener('keydown',e=>{if(e.key==='Enter')b.onclick();});</script></body></html>');})()";

// 5) Script Injector
document.getElementById('injector').href="javascript:(function(){var s=prompt('Paste JS to run:');if(s)eval(s);})();";

// 6) Simulate Crash
document.getElementById('crash').href="javascript:(function(){if(window.__bm_crash_active){var e=document.getElementById('__bm_crash');if(e)e.remove();window.__bm_crash_active=false;return;}window.__bm_crash_active=true;var o=document.createElement('div');o.id='__bm_crash';o.style='position:fixed;inset:0;background:black;color:white;display:flex;align-items:center;justify-content:center;flex-direction:column;z-index:2147483647';o.innerHTML='<h1>Aw, snap — the page became unresponsive</h1><p>Press Escape to close</p>';document.body.appendChild(o);document.addEventListener('keydown',function f(e){if(e.key==='Escape'){o.remove();window.__bm_crash_active=false;document.removeEventListener('keydown',f);}});})();";
</script>
</body>
</html>
