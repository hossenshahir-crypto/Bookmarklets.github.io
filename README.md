# Bookmarklets.github.io
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Drag these bookmarklets</title>
<style>
  :root{font-family:system-ui,-apple-system,Segoe UI,Roboto,"Helvetica Neue",Arial; color:#111}
  body{max-width:900px;margin:40px auto;padding:28px;background:#f9fafb;border-radius:12px;box-shadow:0 6px 20px rgba(16,24,40,.08)}
  h1{margin:0 0 12px;font-size:1.6rem}
  p.lead{margin:0 0 18px;color:#334155}
  .card{background:white;padding:16px;border-radius:10px;border:1px solid #e6e9ee;margin:12px 0;display:flex;align-items:center;gap:16px}
  .link{display:inline-block;padding:10px 14px;border-radius:8px;background:#0b5cff;color:white;text-decoration:none;font-weight:600;box-shadow:0 6px 18px rgba(11,92,255,.12)}
  .instructions{font-size:0.95rem;color:#475569}
  .code{font-family:ui-monospace,SFMono-Regular,Menlo,Monaco,Consolas,"Liberation Mono","Courier New",monospace;background:#f1f5f9;padding:10px;border-radius:8px;overflow:auto}
  footer{margin-top:20px;color:#64748b;font-size:0.9rem}
  .hint{font-size:0.95rem;color:#0b5cff}
  @media (max-width:520px){body{margin:18px;padding:18px}}
</style>
</head>
<body>
  <h1>Drag these to your bookmarks bar</h1>
  <p class="lead">Drag either of the blue items below to your browser's bookmarks bar (or right click → bookmark this link). Then click the saved bookmarklet on any page to use it.</p>

  <div class="card">
    <div style="flex:1">
      <div style="margin-bottom:8px"><strong>Edit the text of any page</strong></div>
      <div class="instructions">Toggle an editable mode on the page. Makes the visible text editable (non-persistent; reload to restore original).</div>
    </div>
    <!-- Bookmarklet 1 -->
    <a class="link"
       href="javascript:(function(){var d=document;try{if(d.__bookmark_edit_mode&&d.__bookmark_edit_mode.on){d.designMode='off';d.body.contentEditable='false';d.__bookmark_edit_mode.on=false;alert('Page editing disabled');}else{d.designMode='on';d.body.contentEditable='true';d.__bookmark_edit_mode={on:true};alert('Page editing enabled — click anywhere to edit text. Reload page to restore.');}}catch(e){alert('Error: '+e);}})();"
       title="Drag to your bookmarks bar — toggles edit mode">
      🔖 Drag: Edit page text
    </a>
  </div>

  <div class="card">
    <div style="flex:1">
      <div style="margin-bottom:8px"><strong>Developer console (in-page)</strong></div>
      <div class="instructions">Opens a small overlay console you can use to run JavaScript on the page. Use the input, press Enter to run. The overlay persists on that page until you close it.</div>
    </div>
    <!-- Bookmarklet 2 -->
    <a class="link"
       href="javascript:(function(){try{if(window.__miniConsole&&window.__miniConsole.open){window.__miniConsole.toggle();return;} var c=document.createElement('div'); c.id='__miniConsole'; c.style.position='fixed'; c.style.right='18px'; c.style.bottom='18px'; c.style.width='420px'; c.style.maxWidth='calc(100% - 36px)'; c.style.height='260px'; c.style.background='rgba(17,24,39,0.98)'; c.style.color='white'; c.style.borderRadius='10px'; c.style.boxShadow='0 12px 30px rgba(2,6,23,0.6)'; c.style.zIndex='2147483646'; c.style.display='flex'; c.style.flexDirection='column'; c.style.fontFamily='ui-monospace,Menlo,monospace'; c.style.fontSize='13px'; var topBar=document.createElement('div'); topBar.style.padding='8px 10px'; topBar.style.display='flex'; topBar.style.justifyContent='space-between'; topBar.style.alignItems='center'; topBar.style.gap='8px'; var title=document.createElement('div'); title.textContent='Mini Console'; title.style.fontWeight='700'; title.style.opacity='0.95'; var btns=document.createElement('div'); btns.style.display='flex'; btns.style.gap='6px'; var closeBtn=document.createElement('button'); closeBtn.textContent='✕'; closeBtn.title='Close console'; closeBtn.style.cursor='pointer'; closeBtn.style.border='0'; closeBtn.style.background='transparent'; closeBtn.style.color='white'; closeBtn.style.fontSize='14px'; var clearBtn=document.createElement('button'); clearBtn.textContent='Clear'; clearBtn.title='Clear output'; clearBtn.style.cursor='pointer'; clearBtn.style.border='0'; clearBtn.style.background='transparent'; clearBtn.style.color='white'; clearBtn.style.fontSize='13px'; btns.appendChild(clearBtn); btns.appendChild(closeBtn); topBar.appendChild(title); topBar.appendChild(btns); var out=document.createElement('pre'); out.style.flex='1'; out.style.margin='0'; out.style.padding='10px'; out.style.overflow='auto'; out.style.background='transparent'; out.style.color='white'; out.style.whiteSpace='pre-wrap'; out.style.lineHe


