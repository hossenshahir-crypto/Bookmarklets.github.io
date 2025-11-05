# Bookmarklets.github.io
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1"/>
<title>Bookmarklets Hub — Tools & Games</title>
<style>
:root{--bg:#071126;--card:#0b1320;--accent:#1f9fff;--muted:#9fb4d6;--btnText:#012026}
body{font-family:system-ui,-apple-system,Segoe UI,Roboto,Arial;color:#e6eef8;background:linear-gradient(180deg,#051221,#07122b);min-height:100vh;display:flex;align-items:center;justify-content:center;margin:0;padding:28px}
.wrap{max-width:1000px;width:100%}
h1{text-align:center;margin:0 0 14px;font-size:1.6rem}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:14px}
.card{background:var(--card);padding:14px;border-radius:10px;border:1px solid rgba(255,255,255,0.03);display:flex;flex-direction:column;justify-content:space-between;min-height:120px}
.title{font-weight:800;margin-bottom:8px}
.muted{color:var(--muted);font-size:0.95rem;margin-bottom:12px}
a.btn{display:inline-block;padding:10px 14px;border-radius:8px;background:var(--accent);color:var(--btnText);text-decoration:none;font-weight:800;text-align:center;cursor:grab}
a.btn:hover{filter:brightness(1.05)}
footer{color:#8faac6;text-align:center;margin-top:18px;font-size:0.9rem}
</style>
</head>
<body>
<div class="wrap">
<h1>🔖 Drag these to your bookmarks bar — Tools & Games</h1>
<div class="grid" id="cards"></div>
<footer>Only run trusted code in Script Injector.</footer>
</div>

<script>
function makeBookmarklet(name, code, description){
  const esc=encodeURIComponent(code.replace(/\n/g,''));
  const href="javascript:(function(){(new Function(decodeURIComponent('"+esc+"')))();})();";
  const card=document.createElement('div');
  card.className='card';
  const title=document.createElement('div'); title.className='title'; title.textContent=name;
  const muted=document.createElement('div'); muted.className='muted'; muted.textContent=description||'';
  const anchor=document.createElement('a'); anchor.className='btn'; anchor.href=href; anchor.textContent='Drag: '+name;
  card.appendChild(title); card.appendChild(muted); card.appendChild(anchor);
  document.getElementById('cards').appendChild(card);
}

/* 1) Edit Page Text */
const codeEdit="(function(){document.designMode=document.designMode==='on'?'off':'on';document.body.contentEditable=document.designMode==='on';alert('Edit mode: '+document.designMode+'\\nClick any text to edit. Reload to restore.');})();";

/* 2) Developer Console Overlay */
const codeDevConsole="(function(){if(window.__bm_devconsole_open){var e=document.getElementById('__bm_devconsole');if(e)e.style.display=e.style.display==='none'?'flex':'none';return;}window.__bm_devconsole_open=true;var w=document.createElement('div');w.id='__bm_devconsole';w.style='position:fixed;right:18px;bottom:18px;width:480px;height:320px;background:rgba(3,6,12,0.96);color:#e6eef8;border-radius:10px;padding:8px;z-index:2147483646;display:flex;flex-direction:column;font-family:ui-monospace,Menlo,monospace;';var t=document.createElement('div');t.style='display:flex;justify-content:space-between;align-items:center;padding:6px;';var ti=document.createElement('div');ti.textContent='Mini Console';ti.style.fontWeight='700';var btns=document.createElement('div');var c=document.createElement('button');c.textContent='Clear';c.style='margin-right:6px;cursor:pointer;border:0;background:transparent;color:white;';var x=document.createElement('button');x.textContent='✕';x.style='cursor:pointer;border:0;background:transparent;color:white;';btns.appendChild(c);btns.appendChild(x);t.appendChild(ti);t.appendChild(btns);var out=document.createElement('pre');out.style='flex:1;margin:6px 0;padding:8px;overflow:auto;background:rgba(0,0,0,0.4);border-radius:6px;';out.textContent='Console ready.\\n';var inputWrap=document.createElement('div');inputWrap.style='display:flex;gap:8px;';var inp=document.createElement('input');inp.placeholder='Type JS and press Enter →';inp.style='flex:1;padding:8px;border-radius:6px;border:1px solid rgba(255,255,255,0.06);background:transparent;color:white;outline:none;';var r=document.createElement('button');r.textContent='Run';r.style='padding:8px;border-radius:6px;border:0;background:#1f9fff;color:#012;font-weight:700;cursor:pointer;';inputWrap.appendChild(inp);inputWrap.appendChild(r);w.appendChild(t);w.appendChild(out);w.appendChild(inputWrap);document.body.appendChild(w);function log(v){try{out.textContent+=v+'\\n';out.scrollTop=out.scrollHeight;}catch(e){}}r.onclick=function(){try{var res=eval(inp.value);log('> '+inp.value);log(res);}catch(e){log('Error:'+e);}inp.value='';};inp.addEventListener('keydown',function(e){if(e.key==='Enter')r.onclick();});c.onclick=function(){out.textContent='Console cleared.\\n';};x.onclick=function(){w.remove();window.__bm_devconsole_open=false;};})();";

/* 3) Games Hub Overlay */
const codeGamesHub="(function(){if(window.__bm_games_overlay){var ex=document.getElementById('__bm_games_overlay');if(ex)ex.style.display=ex.style.display==='none'?'flex':'none';return;}var o=document.createElement('div');o.id='__bm_games_overlay';o.style='position:fixed;inset:0;display:flex;align-items:center;justify-content:center;background:rgba(2,6,23,0.85);z-index:2147483646;font-family:sans-serif;padding:18px;';var p=document.createElement('div');p.style='width:920px;max-width:96%;height:700px;max-height:96%;background:linear-gradient(180deg,#081124,#071426);border-radius:12px;padding:12px;display:flex;flex-direction:column;box-shadow:0 20px 50px rgba(0,0,0,0.6);color:#e6eef8;';var h=document.createElement('div');h.style='display:flex;justify-content:space-between;align-items:center;gap:12px';var ti=document.createElement('div');ti.innerHTML='<strong style=\"font-size:18px\">🎮 Games Hub</strong><div style=\"font-size:12px;color:#9fb4d6\">Play games — overlay will close on reload</div>';var hb=document.createElement('div');var c=document.createElement('button');c.textContent='Close';c.style='padding:8px 12px;border-radius:8px;border:0;background:#ef4444;color:#fff;cursor:pointer';var rbtn=document.createElement('button');rbtn.textContent='Reset';rbtn.style='margin-right:8px;padding:8px 12px;border-radius:8px;border:0;background:#1f9fff;color:#012;font-weight:700;cursor:pointer';hb.appendChild(rbtn);hb.appendChild(c);h.appendChild(ti);h.appendChild(hb);p.appendChild(h);var ct=document.createElement('div');ct.style='margin-top:10px;display:flex;gap:8px;flex-wrap:wrap';['Snake','TicTacToe','Pong','Breakout','CookieClicker','Flappy','Shooter','2048'].forEach(g=>{var b=document.createElement('button');b.textContent=g;b.style='background:#1572e8;color:#fff;border:0;padding:8px 12px;border-radius:8px;cursor:pointer;font-weight:700';b.onclick=function(){alert('Mini games run here. Implement game logic.');};ct.appendChild(b);});p.appendChild(ct);o.appendChild(p);document.body.appendChild(o);c.onclick=function(){o.remove();window.__bm_games_overlay=false;};rbtn.onclick=function(){alert('Reset canvas');};window.__bm_games_overlay=true;})();";

/* 4) Mini Browser popup */
const codeMiniBrowser="(function(){var w=window.open('','__bm_minibrowser','width=1000,height=700,resizable=yes,scrollbars=yes');if(!w){alert('Popup blocked.');return;}w.document.write('<!doctype html><html><meta charset=\"utf-8\"><title>Mini Browser</title><style>body{margin:0;height:100vh;display:flex;flex-direction:column;font-family:sans-serif}#bar{display:flex;padding:8px;gap:8px;background:#222}input{flex:1;padding:8px;border-radius:6px;border:0}button{padding:8px;border-radius:6px;border:0;background:#0b5cff;color:#fff}iframe{flex:1;border:0}</style><div id=\"bar\"><input id=\"u\" placeholder=\"https://example.com\"><button id=\"g\">Go</button></div><iframe id=\"f\" src=\"about:blank\"></iframe><script>const input=document.getElementById(\"u\"),btn=document.getElementById(\"g\"),frame=document.getElementById(\"f\");function nav(){let v=input.value.trim();if(!/^https?:\\/\\//.test(v))v='https://'+v;frame.src=v;}btn.onclick=nav;input.addEventListener(\"keydown\",e=>{if(e.key==='Enter')nav();});</script></html>');})();";

/* 5) Script Injector */
const codeScriptInjector="(function(){if(window.__bm_injector_overlay){var ex=document.getElementById('__bm_injector_overlay');if(ex)ex.style.display=ex.style.display==='none'?'flex':'none';return;}window.__bm_injector_overlay=true;var o=document.createElement('div');o.id='__bm_injector_overlay';o.style='position:fixed;inset:0;display:flex;align-items:center;justify-content:center;background:rgba(0,0,0,0.7);z-index:2147483646;font-family:monospace;';var b=document.createElement('div');b.style='width:760px;max-width:96%;background:#071026;padding:12px;border-radius:10px;color:#e6eef8';b.innerHTML='<div style=\"display:flex;justify-content:space-between;align-items:center\"><strong>Script Injector</strong><div><button id=\"__inj_close\" style=\"background:#ef4444;border:0;padding:6px 10px;border-radius:8px;color:white;cursor:pointer\">Close</button></div></div><div style=\"margin-top:8px;color:#9fb4d6;font-size:13px\">Paste JavaScript below and press Inject. <strong>Only run trusted code.</strong></div><textarea id=\"__inj_area\" style=\"width:100%;height:300px;margin-top:8px;background:#00101a;color:#e6eef8;border-radius:8px;border:0;padding:8px;font-family:monospace\"></textarea><div style=\"margin-top:8px;display:flex;gap:8px\"><button id=\"__inj_run\" style=\"padding:8px 12px;border-radius:8px;border:0;background:#1f9fff;color:#012;font-weight:800;cursor:pointer\">Inject</button><button id=\"__inj_save\" style=\"padding:8px 12px;border-radius:8px;border:0;background:#1572e8;color:white;cursor:pointer\">Save</button><button id=\"__inj_restore\" style=\"padding:8px 12px;border-radius:8px;border:0;background:#64748b;color:white;cursor:pointer\">Load Saved</button></div>';o.appendChild(b);document.body.appendChild(o);document.getElementById('__inj_close').onclick=function(){o.remove();window.__bm_injector_overlay=false;};var area=document.getElementById('__inj_area');document.getElementById('__inj_run').onclick=function(){try{(new Function(area.value))();alert('Script executed');}catch(e){alert('Error:'+e);}};document.getElementById('__inj_save').onclick=function(){localStorage.setItem('__bm_saved_inject',area.value);alert('Saved');};document.getElementById('__inj_restore').onclick=function(){area.value=localStorage.getItem('__bm_saved_inject')||'';alert('Loaded');};area.value='';})();";

/* 6) Simulate Crash */
const codeSimCrash="(function(){if(window.__bm_sim_crash_active){var ex=document.getElementById('__bm_sim_crash');if(ex)ex.remove();window.__bm_sim_crash_active=false;document.removeEventListener('keydown',window.__bm_sim_esc);return;}window.__bm_sim_crash_active=true;window.__bm_sim_esc=function(e){if(e.key==='Escape'){var el=document.getElementById('__bm_sim_crash');if(el)el.remove();window.__bm_sim_crash_active=false;document.removeEventListener('keydown',window.__bm_sim_esc);}};document.addEventListener('keydown',window.__bm_sim_esc);var o=document.createElement('div');o.id='__bm_sim_crash';o.style='position:fixed;inset:0;z-index:2147483647;display:flex;align-items:center;justify-content:center;background:linear-gradient(180deg,#000,#0b0b0b);color:white;font-family:system-ui;padding:20px';o.innerHTML='<div style=\"max-width:900px;text-align:center;padding:28px;border-radius:12px;backdrop-filter:blur(3px)\"><div style=\"font-size:28px;font-weight:800;margin-bottom:10px\">Aw, snap — the site became unresponsive</div><div style=\"color:#d1d5db;margin-bottom:16px\">The page has encountered an error. Try reloading or click Restore below.</div><div style=\"display:flex;gap:12px;justify-content:center\"><div style=\"width:56px;height:56px;border-radius:50%;border:6px solid rgba(255,255,255,0.06);border-top-color:#1f9fff;animation:__bmspin 1s linear infinite\"></div><button id=\\'__bm_restore\\' style=\\'padding:10px 14px;border-radius:8px;border:0;background:#1f9fff;color:#012;font-weight:700;cursor:pointer\\'>Restore</button></div></div><style>@keyframes __bmspin{0%{transform:rotate(0)}100%{transform:rotate(360deg)}}</style>';document.body.appendChild(o);document.getElementById('__bm_restore').onclick=function(){o.remove();window.__bm_sim_crash_active=false;};})();";

/* Add all bookmarklets */
makeBookmarklet('Edit Page', codeEdit, 'Edit text on any page.');
makeBookmarklet('Dev Console', codeDevConsole, 'Mini console overlay.');
makeBookmarklet('Games Hub', codeGamesHub, 'Play mini games.');
makeBookmarklet('Mini Browser', codeMiniBrowser, 'Popup browser.');
makeBookmarklet('Script Injector', codeScriptInjector, 'Inject JS safely.');
makeBookmarklet('Simulate Crash', codeSimCrash, 'Fake crash overlay.');
</script>
</body>
</html>
