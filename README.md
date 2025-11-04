# Bookmarklets.github.io
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Drag Bookmarklets to Your Bar</title>
<style>
body {
  font-family: system-ui, -apple-system, Segoe UI, Roboto, sans-serif;
  background: #f9fafb;
  color: #111;
  margin: 40px auto;
  padding: 28px;
  max-width: 900px;
  border-radius: 12px;
  box-shadow: 0 6px 20px rgba(16,24,40,.08);
}
h1 { font-size: 1.6rem; }
.card {
  background: white;
  padding: 16px;
  border-radius: 10px;
  border: 1px solid #e6e9ee;
  margin: 12px 0;
  display: flex;
  align-items: center;
  gap: 16px;
}
.link {
  display:inline-block;
  padding:10px 14px;
  border-radius:8px;
  background:#0b5cff;
  color:white;
  text-decoration:none;
  font-weight:600;
  box-shadow:0 6px 18px rgba(11,92,255,.12);
}
.link:hover { background:#0947d1; }
.instructions { font-size:0.95rem; color:#475569; }
</style>
</head>
<body>

<h1>Drag these to your bookmarks bar</h1>
<p>Drag the blue buttons below to your bookmarks bar. Then click them on any page to use them!</p>

<!-- Edit Page Text -->
<div class="card">
  <div style="flex:1">
    <strong>Edit the text of any page</strong>
    <div class="instructions">
      Turns on editable mode. Click anywhere to edit text; reload to reset.
    </div>
  </div>
  <a class="link"
     href="javascript:(function(){var d=document;if(d.designMode==='on'){d.designMode='off';d.body.contentEditable='false';alert('Editing disabled');}else{d.designMode='on';d.body.contentEditable='true';alert('Editing enabled! Click text to edit. Reload to undo.');}})();">
     🔖 Drag: Edit text
  </a>
</div>

<!-- Developer Console -->
<div class="card">
  <div style="flex:1">
    <strong>Developer Console (in-page)</strong>
    <div class="instructions">
      Opens a small console overlay you can use to run JavaScript on the page.
    </div>
  </div>
  <a class="link"
     href="javascript:(function(){try{if(window.__miniConsole&&window.__miniConsole.open){window.__miniConsole.toggle();return;}var c=document.createElement('div');c.id='__miniConsole';c.style='position:fixed;right:18px;bottom:18px;width:420px;max-width:calc(100% - 36px);height:260px;background:rgba(17,24,39,0.98);color:white;border-radius:10px;box-shadow:0 12px 30px rgba(2,6,23,0.6);z-index:999999999;display:flex;flex-direction:column;font-family:ui-monospace,Menlo,monospace;font-size:13px;';var top=document.createElement('div');top.style='padding:8px 10px;display:flex;justify-content:space-between;align-items:center;';var title=document.createElement('div');title.textContent='Mini Console';title.style='font-weight:700;opacity:0.95;';var btns=document.createElement('div');btns.style='display:flex;gap:6px;';var close=document.createElement('button');close.textContent='✕';close.style='cursor:pointer;background:none;border:0;color:white;font-size:14px;';var clear=document.createElement('button');clear.textContent='Clear';clear.style='cursor:pointer;background:none;border:0;color:white;font-size:13px;';btns.append(clear,close);top.append(title,btns);var out=document.createElement('pre');out.style='flex:1;margin:0;padding:10px;overflow:auto;white-space:pre-wrap;line-height:1.4;';out.textContent='Console ready. Type JS below and press Enter.\\n';var input=document.createElement('input');input.type='text';input.placeholder='Type JS and press Enter →';input.style='width:100%;padding:8px;border:1px solid rgba(255,255,255,0.2);border-radius:6px;background:rgba(255,255,255,0.05);color:white;';var inputWrap=document.createElement('div');inputWrap.style='padding:8px;';inputWrap.append(input);c.append(top,out,inputWrap);document.body.append(c);function log(v){out.textContent+=String(v)+'\\n';out.scrollTop=out.scrollHeight;}close.onclick=()=>c.remove();clear.onclick=()=>out.textContent='Console cleared.\\n';input.addEventListener('keydown',e=>{if(e.key==='Enter'){var code=input.value;input.value='';try{var result=eval(code);log('> '+code);log(result);}catch(err){log('Error: '+err);}}});window.__miniConsole={open:true,toggle:()=>{c.style.display=(c.style.display==='none'?'flex':'none');}};}catch(e){alert('Mini console error: '+e);} })();">
     🔖 Drag: Developer console
  </a>
</div>

<p class="instructions">
💡 If your browser won’t let you drag the link, right-click → “Bookmark this link” instead.
</p>

</body>
</html>

