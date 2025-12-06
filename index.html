<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>No More Scrolling — App Timer</title>
  <style>
    :root{--bg:#0f1724;--card:#0b1220;--accent:#7c3aed;--muted:#94a3b8;--success:#10b981}
    *{box-sizing:border-box;font-family:Inter,ui-sans-serif,system-ui,Segoe UI,Roboto,"Helvetica Neue",Arial}
    body{margin:0;background:linear-gradient(180deg,#071024 0%, #07172a 100%);color:#e6eef8;min-height:100vh;padding:28px}
    .wrap{max-width:980px;margin:0 auto}
    header{display:flex;align-items:center;gap:16px;margin-bottom:18px}
    header h1{font-size:20px;margin:0}
    .card{background:rgba(255,255,255,0.03);border:1px solid rgba(255,255,255,0.03);padding:16px;border-radius:12px;margin-bottom:14px}
    .grid{display:grid;grid-template-columns:1fr 360px;gap:16px}
    label{display:block;margin-bottom:6px;color:var(--muted);font-size:13px}
    .apps-list{display:flex;flex-direction:column;gap:8px}
    .app-row{display:flex;align-items:center;gap:8px;background:rgba(255,255,255,0.02);padding:8px;border-radius:8px}
    .app-row input[type="checkbox"]{transform:scale(1.1)}
    .app-name{flex:1}
    .controls{display:flex;gap:8px;align-items:center}
    input[type="number"],input[type="text"],select{background:transparent;border:1px solid rgba(255,255,255,0.06);padding:8px;border-radius:8px;color:inherit}
    button{background:var(--accent);border:none;color:white;padding:8px 12px;border-radius:10px;cursor:pointer}
    button.ghost{background:transparent;border:1px solid rgba(255,255,255,0.06)}
    .timers{display:flex;flex-direction:column;gap:10px}
    .timer-card{background:linear-gradient(90deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));padding:12px;border-radius:10px;border:1px solid rgba(255,255,255,0.02)}
    .progress{height:8px;background:rgba(255,255,255,0.03);border-radius:999px;overflow:hidden;margin-top:8px}
    .bar{height:100%;background:var(--success);width:0%;transition:width 0.2s}
    .muted{color:var(--muted);font-size:13px}
    footer{margin-top:18px;color:var(--muted);font-size:13px}
    .row{display:flex;gap:8px;align-items:center}
    .small{font-size:13px;padding:6px 8px}
    .blocked{background:#2b1010;color:#ffdede;border:1px solid rgba(255,0,0,0.1)}
    @media (max-width:880px){.grid{grid-template-columns:1fr}}
  </style>
</head>
<body>
  <div class="wrap">
    <header>
      <h1>No More Scrolling — App Timer</h1>
      <div class="muted">Select apps, set timers and curb mindless scrolling (browser simulation).</div>
    </header>

    <div class="grid">
      <section class="card">
        <label>Available apps</label>
        <div class="apps-list" id="appsList"></div>

        <div style="margin-top:12px;display:flex;gap:8px;align-items:center">
          <input id="newAppName" type="text" placeholder="Add a custom app (e.g. Instagram)" style="flex:1" />
          <button id="addAppBtn" class="small">Add</button>
        </div>

        <hr style="margin:12px 0;border:0;border-top:1px solid rgba(255,255,255,0.03)" />

        <label>Selected apps — set timer per app (minutes)</label>
        <div id="selectedApps"></div>

        <div style="display:flex;gap:8px;margin-top:10px">
          <button id="startBtn">Start Timers</button>
          <button id="pauseBtn" class="ghost">Pause</button>
          <button id="resetBtn" class="ghost">Reset</button>
        </div>

        <p class="muted" style="margin-top:8px">Note: This page simulates timers and helps you plan/track usage. It cannot literally block other native apps — for that you need OS-level controls (Screen Time, Digital Wellbeing) or an app with native permissions.</p>
      </section>

      <aside class="card">
        <label>Active timers</label>
        <div class="timers" id="timersContainer">
          <div class="muted">No timers running yet.</div>
        </div>

        <hr style="margin:12px 0;border:0;border-top:1px solid rgba(255,255,255,0.03)" />

        <label>Quick settings</label>
        <div style="display:flex;flex-direction:column;gap:8px">
          <div class="row"><label style="min-width:110px">Notify on finish</label><input id="notifyToggle" type="checkbox" checked /></div>
          <div class="row"><label style="min-width:110px">Persist across reload</label><input id="persistToggle" type="checkbox" checked /></div>
          <div class="row"><label style="min-width:110px">Auto-add unselected apps when timer set</label><input id="autoAddToggle" type="checkbox" /></div>
        </div>

        <hr style="margin:12px 0;border:0;border-top:1px solid rgba(255,255,255,0.03)" />

        <label>How to use</label>
        <ol class="muted" style="padding-left:18px;margin:6px 0">
          <li>Select apps and set minutes for each.</li>
          <li>Click Start Timers — countdowns will appear in "Active timers".</li>
          <li>When a timer finishes the app will be marked blocked here and (optionally) a notification appears.</li>
        </ol>
      </aside>
    </div>

    <footer>Designed to help you reduce scrolling. Save this file as <code>no-more-scrolling.html</code> and open in your browser.</footer>
  </div>

  <script>
    // Simple single-file app timer simulation. Uses localStorage if persistence enabled.
    const defaultApps = [
      'Instagram','Facebook','YouTube','Twitter / X','TikTok','Reddit','WhatsApp','Snapchat','Telegram','LinkedIn'
    ];

    let apps = [];
    let timers = {}; // id -> {name, remainingMs, totalMs, running, intervalId, blocked}
    const appsListEl = document.getElementById('appsList');
    const selectedAppsEl = document.getElementById('selectedApps');
    const timersContainer = document.getElementById('timersContainer');
    const newAppName = document.getElementById('newAppName');
    const addAppBtn = document.getElementById('addAppBtn');
    const startBtn = document.getElementById('startBtn');
    const pauseBtn = document.getElementById('pauseBtn');
    const resetBtn = document.getElementById('resetBtn');
    const notifyToggle = document.getElementById('notifyToggle');
    const persistToggle = document.getElementById('persistToggle');
    const autoAddToggle = document.getElementById('autoAddToggle');

    function idFromName(name){return name.replace(/[^a-z0-9]/gi,'_').toLowerCase()}

    function load(){
      const saved = localStorage.getItem('nms_state');
      if(saved){
        try{const obj=JSON.parse(saved);apps=obj.apps||defaultApps;timers=obj.timers||{};}
        catch(e){apps=defaultApps;}
      } else apps=defaultApps;
      renderApps();renderSelected();renderTimers();
    }

    function save(){
      if(!persistToggle.checked) return;
      const snapshot = {apps, timers: serializeTimers()};
      localStorage.setItem('nms_state', JSON.stringify(snapshot));
    }

    function serializeTimers(){
      const out = {};
      Object.keys(timers).forEach(k=>{
        const t = timers[k];
        out[k]={name:t.name,remainingMs:t.remainingMs,totalMs:t.totalMs,blocked:!!t.blocked,running:!!t.running};
      });
      return out;
    }

    function renderApps(){
      appsListEl.innerHTML='';
      apps.forEach(name=>{
        const id = 'chk_'+idFromName(name);
        const row = document.createElement('div');row.className='app-row';
        const cb = document.createElement('input');cb.type='checkbox';cb.id=id;cb.dataset.app=name;
        cb.addEventListener('change',renderSelected);
        row.appendChild(cb);
        const span = document.createElement('div');span.className='app-name';span.textContent=name;row.appendChild(span);
        const hint = document.createElement('div');hint.className='muted';hint.style.fontSize='12px';hint.style.marginLeft='8px';hint.textContent='set minutes →';
        row.appendChild(hint);
        appsListEl.appendChild(row);
      })
    }

    function renderSelected(){
      selectedAppsEl.innerHTML='';
      const checkboxes = appsListEl.querySelectorAll('input[type=checkbox]');
      let any=false;
      checkboxes.forEach(cb=>{
        if(cb.checked){any=true; const name=cb.dataset.app; const id=idFromName(name);
          const row = document.createElement('div');row.className='row';row.style.marginTop='8px';
          const label = document.createElement('div');label.textContent=name;label.style.flex='1';
          const num = document.createElement('input');num.type='number';num.min='0';num.value = Math.max(1, Math.round(((timers[id] && timers[id].totalMs)/60000) || 10)); num.style.width='90px';
          const setBtn = document.createElement('button');setBtn.className='small ghost';setBtn.textContent='Set';
          setBtn.addEventListener('click',()=>{
            const minutes = parseInt(num.value,10)||0; setTimerForApp(name, minutes);
            if(autoAddToggle.checked) save(); renderTimers();
          });
          row.appendChild(label);row.appendChild(num);row.appendChild(setBtn);
          selectedAppsEl.appendChild(row);
        }
      });
      if(!any) selectedAppsEl.innerHTML='<div class="muted">No app selected (check an app from the left)</div>';
    }

    addAppBtn.addEventListener('click',()=>{
      const v = newAppName.value.trim(); if(!v) return; apps.unshift(v); newAppName.value=''; renderApps(); save();
    });

    function setTimerForApp(name, minutes){
      const id = idFromName(name);
      const ms = Math.max(0, Math.round(minutes))*60000;
      timers[id] = timers[id] || {name,remainingMs:ms,totalMs:ms,running:false,blocked:false};
      timers[id].remainingMs = ms; timers[id].totalMs = ms; timers[id].blocked=false;
      renderTimers(); save();
    }

    function msToText(ms){
      if(ms<=0) return '0:00';
      const s = Math.floor(ms/1000); const m = Math.floor(s/60); const sec = s%60; return m+':'+String(sec).padStart(2,'0');
    }

    function renderTimers(){
      timersContainer.innerHTML='';
      const keys = Object.keys(timers);
      if(!keys.length){timersContainer.innerHTML='<div class="muted">No timers set yet.</div>';return}
      keys.forEach(id=>{
        const t = timers[id];
        const card = document.createElement('div');card.className='timer-card'; if(t.blocked) card.classList.add('blocked');
        const top = document.createElement('div');top.style.display='flex';top.style.justifyContent='space-between';top.style.alignItems='center';
        const left = document.createElement('div');
        left.innerHTML = '<strong>'+t.name+'</strong><div class="muted">'+(t.blocked? 'Blocked' : (t.running? 'Running' : 'Paused'))+'</div>';
        const right = document.createElement('div');
        right.innerHTML = '<div style="text-align:right"><div style="font-weight:600">'+msToText(t.remainingMs)+'</div><div class="muted">'+msToText(t.totalMs)+'</div></div>';
        top.appendChild(left);top.appendChild(right);
        card.appendChild(top);
        const progressWrap = document.createElement('div');progressWrap.className='progress';
        const bar = document.createElement('div');bar.className='bar';
        const pct = t.totalMs? Math.max(0, Math.min(100, (1 - t.remainingMs / t.totalMs) * 100)) : 0; bar.style.width = pct+'%';
        progressWrap.appendChild(bar); card.appendChild(progressWrap);

        const actions = document.createElement('div');actions.style.display='flex';actions.style.gap='8px';actions.style.marginTop='8px';
        const start = document.createElement('button');start.className='small'; start.textContent = t.running? 'Running' : 'Start'; start.disabled = t.running || t.blocked;
        start.addEventListener('click',()=>{startTimer(id)});
        const pause = document.createElement('button');pause.className='small ghost'; pause.textContent='Pause'; pause.disabled = !t.running || t.blocked; pause.addEventListener('click',()=>{pauseTimer(id)});
        const reset = document.createElement('button');reset.className='small ghost'; reset.textContent='Reset'; reset.addEventListener('click',()=>{resetTimer(id)});
        const remove = document.createElement('button');remove.className='small ghost'; remove.textContent='Remove'; remove.addEventListener('click',()=>{delete timers[id]; renderTimers(); save();});
        actions.appendChild(start);actions.appendChild(pause);actions.appendChild(reset);actions.appendChild(remove);
        card.appendChild(actions);
        timersContainer.appendChild(card);
      })
    }

    function startTimer(id){
      const t = timers[id]; if(!t || t.blocked) return; t.running=true; t.lastTick = Date.now();
      if(t.intervalId) clearInterval(t.intervalId);
      t.intervalId = setInterval(()=>{
        const now = Date.now(); const dt = now - t.lastTick; t.lastTick = now; t.remainingMs -= dt; if(t.remainingMs<=0){
          t.remainingMs=0; t.running=false; t.blocked=true; clearInterval(t.intervalId); t.intervalId=null; onTimerFinished(t);
        }
        renderTimers();
      },250);
      renderTimers(); save();
    }

    function pauseTimer(id){
      const t = timers[id]; if(!t) return; t.running=false; if(t.intervalId) clearInterval(t.intervalId); t.intervalId=null; renderTimers(); save();
    }

    function resetTimer(id){
      const t = timers[id]; if(!t) return; t.remainingMs = t.totalMs; t.running=false; t.blocked=false; if(t.intervalId) clearInterval(t.intervalId); t.intervalId=null; renderTimers(); save();
    }

    function onTimerFinished(t){
      renderTimers();
      if(notifyToggle.checked && 'Notification' in window){
        if(Notification.permission==='granted'){
          new Notification('Time up — '+t.name,{body:'Timer finished for '+t.name});
        } else if(Notification.permission!=='denied'){
          Notification.requestPermission().then(p=>{ if(p==='granted') new Notification('Time up — '+t.name,{body:'Timer finished for '+t.name});});
        }
      }
    }

    startBtn.addEventListener('click',()=>{
      // Start all non-blocked timers that have >0 remaining
      Object.keys(timers).forEach(k=>{if(!timers[k].blocked && timers[k].remainingMs>0) startTimer(k)});
    });
    pauseBtn.addEventListener('click',()=>{
      Object.keys(timers).forEach(k=>{pauseTimer(k)});
    });
    resetBtn.addEventListener('click',()=>{
      Object.keys(timers).forEach(k=>{resetTimer(k)});
    });

    function restoreFromSerialized(s){
      Object.keys(s).forEach(k=>{const item = s[k]; timers[k]={name:item.name,remainingMs:item.remainingMs,totalMs:item.totalMs,running:false,blocked:!!item.blocked,intervalId:null}})
    }

    // if persisted state exists but timers object contains serialized shapes
    function normalizeTimers(){
      // If timers entries exist from localStorage load, restore properly
      Object.keys(timers).forEach(k=>{
        const t = timers[k]; if(t && !('remainingMs' in t) && typeof t==='object'){
          // outdated format — ignore
          delete timers[k];
        }
      })
    }

    // When page unload, stop intervals and optionally persist remaining states
    window.addEventListener('beforeunload',()=>{
      Object.keys(timers).forEach(k=>{if(timers[k].intervalId) clearInterval(timers[k].intervalId); delete timers[k].intervalId});
      save();
    });

    // helper: if data loaded has timers shaped with fields inside
    function boot(){
      // If localStorage present and persist enabled, use it — already loaded in load()
      // If there is a serialized timers object (from previous sessions), convert
      Object.keys(timers).forEach(k=>{
        const t = timers[k]; if(t && typeof t==='object' && 'remainingMs' in t) t.running=false;
      });
      normalizeTimers(); renderApps(); renderSelected(); renderTimers();
    }

    // Initialize
    load(); boot();
  </script>
</body>
</html>
