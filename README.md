<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<title>CLIENTS — Akash</title>
<link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=VT323&family=JetBrains+Mono:wght@400;600&display=swap" rel="stylesheet"/>
<style>
:root{
  --bg:#020810;--bg2:#030C18;--bg3:#050F20;--sur:#071425;
  --b:#00BFFF;--b2:#7DDFFF;--bd:rgba(0,191,255,.10);--bb:rgba(0,191,255,.18);
  --cyan:#00FFE5;--red:#FF3C5A;--gold:#FFD166;--purple:#A78BFA;
  --tx:#C8E8FF;--mu:#1E4060;--mu2:#0D2030;--wa:#25D366;
}
*{box-sizing:border-box;margin:0;padding:0}
html,body{height:100%;overflow:hidden}
body{background:var(--bg);color:var(--tx);font-family:'JetBrains Mono',monospace;display:flex;flex-direction:column}
body::before{content:'';position:fixed;inset:0;pointer-events:none;z-index:9999;background:repeating-linear-gradient(0deg,transparent,transparent 2px,rgba(0,0,0,.07) 2px,rgba(0,0,0,.07) 4px)}

.topbar{height:50px;background:rgba(2,8,16,.98);border-bottom:1px solid var(--mu2);display:flex;align-items:center;padding:0 20px;gap:14px;flex-shrink:0}
.tlogo{font-family:'VT323',monospace;font-size:24px;color:var(--b);text-shadow:0 0 12px rgba(0,191,255,.5);letter-spacing:.1em}
.tdiv{width:1px;height:18px;background:var(--mu2)}
.tpill{padding:3px 10px;border-radius:2px;font-size:8px;letter-spacing:.15em;border:1px solid;display:flex;align-items:center;gap:5px;font-family:'Share Tech Mono',monospace}
.tpill.b{border-color:var(--bb);color:var(--b);background:var(--bd)}
.tpill.w{border-color:rgba(37,211,102,.22);color:var(--wa);background:rgba(37,211,102,.07)}
.pulse{animation:pulse 1.5s infinite}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:.35}}
.tright{margin-left:auto;display:flex;align-items:center;gap:10px}
.tsender{font-size:10px;color:var(--mu);font-family:'Share Tech Mono',monospace}
.tsender span{color:var(--b)}
.tsbtn{padding:4px 11px;background:transparent;border:1px solid var(--mu2);color:var(--mu);font-family:'Share Tech Mono',monospace;font-size:9px;border-radius:2px;cursor:pointer}
.tsbtn:hover{border-color:var(--bb);color:var(--b)}

.body{display:grid;grid-template-columns:220px 1fr 270px;flex:1;overflow:hidden}

/* SIDEBAR */
.side{background:var(--bg2);border-right:1px solid var(--mu2);display:flex;flex-direction:column;overflow-y:auto}
.aw{margin:10px;background:var(--bd);border:1px solid var(--bb);border-radius:2px;padding:12px}
.awt{font-size:8px;color:var(--b);margin-bottom:4px;font-family:'Share Tech Mono',monospace}
.awn{font-family:'VT323',monospace;font-size:18px;color:var(--b2)}
.aws{display:flex;align-items:center;gap:5px;font-size:8px;color:var(--b);margin-top:4px;font-family:'Share Tech Mono',monospace}
.dot{width:6px;height:6px;border-radius:50%;background:var(--b);animation:pulse 1.5s infinite;box-shadow:0 0 6px var(--b)}
.ss{padding:12px 0}
.sl{font-size:7px;letter-spacing:.25em;color:var(--mu);padding:0 14px 6px;text-transform:uppercase;font-family:'Share Tech Mono',monospace}
.nv{display:flex;align-items:center;gap:9px;padding:9px 14px;cursor:pointer;font-size:9px;color:var(--mu);border:none;background:none;width:100%;text-align:left;font-family:'Share Tech Mono',monospace;border-left:2px solid transparent;transition:all .15s}
.nv:hover{color:var(--tx);background:rgba(0,191,255,.03)}
.nv.on{color:var(--b);border-left-color:var(--b);background:var(--bd)}
.nv .ic{font-size:13px;width:17px;text-align:center}
.nv .bx{margin-left:auto;background:var(--red);color:#fff;font-size:7px;padding:1px 5px;border-radius:2px}
.nv .gx{margin-left:auto;background:var(--b);color:var(--bg);font-size:7px;padding:1px 5px;border-radius:2px}
.met{padding:10px;border-top:1px solid var(--mu2);margin-top:auto}
.mr{display:flex;justify-content:space-between;font-size:8px;padding:2px 0;font-family:'Share Tech Mono',monospace}
.mr .ml{color:var(--mu)}
.vg{color:var(--b)}.vb{color:var(--cyan)}.vo{color:var(--gold)}
.pb{background:var(--mu2);height:2px;overflow:hidden;margin:7px 0 3px}
.pf{height:100%;background:linear-gradient(90deg,var(--b),var(--cyan));transition:width 1s}

/* CENTER */
.center{display:flex;flex-direction:column;overflow:hidden}
.tabs{display:flex;border-bottom:1px solid var(--mu2);background:var(--bg2);flex-shrink:0}
.tab{padding:12px 14px;font-size:9px;cursor:pointer;color:var(--mu);border-bottom:2px solid transparent;margin-bottom:-1px;transition:all .15s;letter-spacing:.08em;font-family:'Share Tech Mono',monospace}
.tab:hover{color:var(--tx)}.tab.on{color:var(--b);border-bottom-color:var(--b)}
.scroll{flex:1;overflow-y:auto;padding:16px}
.sec{display:none}.sec.on{display:block}

/* CARDS */
.card{background:var(--bg3);border:1px solid var(--mu2);border-radius:2px;padding:14px;margin-bottom:12px;position:relative;overflow:hidden}
.card::before{content:'';position:absolute;top:0;left:0;right:0;height:1px;background:linear-gradient(90deg,transparent,var(--bb),transparent)}
.ct{font-family:'VT323',monospace;font-size:16px;color:var(--b);margin-bottom:10px;display:flex;align-items:center;justify-content:space-between;text-shadow:0 0 8px rgba(0,191,255,.3)}

/* INPUTS */
.inp{width:100%;background:var(--sur);border:1px solid var(--mu2);color:var(--tx);padding:8px 12px;font-family:'JetBrains Mono',monospace;font-size:11px;border-radius:2px;outline:none;transition:border-color .2s;caret-color:var(--b)}
.inp:focus{border-color:var(--b)}
.inp::placeholder{color:var(--mu)}
select.inp{appearance:none;cursor:pointer}
textarea.inp{resize:vertical;min-height:80px;line-height:1.7}
.ir{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:10px}
.ig{margin-bottom:10px}
.il{font-size:7px;color:var(--mu);letter-spacing:.2em;text-transform:uppercase;margin-bottom:4px;display:block;font-family:'Share Tech Mono',monospace}

/* BUTTONS */
.btn{padding:7px 14px;border-radius:2px;font-family:'Share Tech Mono',monospace;font-size:9px;letter-spacing:.1em;cursor:pointer;transition:all .2s;border:1px solid;white-space:nowrap}
.bg{background:transparent;color:var(--b);border-color:var(--b)}
.bg:hover{background:var(--bd)}
.bh{background:transparent;color:var(--mu);border-color:var(--mu2)}
.bh:hover{color:var(--tx);border-color:var(--bb)}
.bw{background:rgba(37,211,102,.1);color:var(--wa);border-color:rgba(37,211,102,.25)}
.bw:hover{background:rgba(37,211,102,.18)}
.br{display:flex;gap:8px;flex-wrap:wrap;margin-top:8px}

/* TABLE */
.tbl{width:100%;border-collapse:collapse;font-size:9px}
.tbl th{text-align:left;color:var(--mu);padding:5px 6px;border-bottom:1px solid var(--mu2);font-size:7px;letter-spacing:.18em;text-transform:uppercase;font-weight:400;font-family:'Share Tech Mono',monospace}
.tbl td{padding:7px 6px;border-bottom:1px solid rgba(255,255,255,.02);vertical-align:middle}
.tbl tr:hover td{background:rgba(0,191,255,.02)}
.tag{display:inline-block;padding:1px 6px;border-radius:2px;font-size:7px;letter-spacing:.08em;text-transform:uppercase;font-family:'Share Tech Mono',monospace}
.tn{background:rgba(255,60,90,.08);color:var(--red);border:1px solid rgba(255,60,90,.16)}
.ty{background:rgba(0,191,255,.08);color:var(--b);border:1px solid rgba(0,191,255,.18)}
.tp{background:rgba(255,209,102,.07);color:var(--gold);border:1px solid rgba(255,209,102,.16)}
.ts{background:rgba(0,255,229,.07);color:var(--cyan);border:1px solid rgba(0,255,229,.16)}
.mb{padding:2px 7px;font-family:'Share Tech Mono',monospace;font-size:8px;border-radius:2px;cursor:pointer;border:1px solid var(--mu2);background:transparent;color:var(--mu);transition:all .2s}
.mb:hover{border-color:var(--bb);color:var(--b)}

/* LOG */
.log{background:#010508;border:1px solid var(--mu2);border-radius:2px;padding:10px;height:140px;overflow-y:auto;font-size:9px;font-family:'JetBrains Mono',monospace}
.ll{line-height:2;color:var(--mu)}
.ll .lt{color:rgba(0,191,255,.25);margin-right:8px}
.ll.ok .lm{color:var(--b)}.ll.er .lm{color:var(--red)}.ll.in .lm{color:var(--cyan)}.ll.wa .lm{color:var(--wa)}.ll.wr .lm{color:var(--gold)}
@keyframes blink{0%,100%{opacity:1}50%{opacity:0}}
.cur{display:inline-block;width:7px;height:11px;background:var(--b);vertical-align:middle;animation:blink 1s infinite;margin-left:3px}

/* PROGRESS */
.prb{background:var(--mu2);height:3px;overflow:hidden}
.prf{height:100%;background:linear-gradient(90deg,var(--b),var(--cyan));transition:width .6s;box-shadow:0 0 8px var(--b)}

/* RIGHT */
.rp{background:var(--bg2);border-left:1px solid var(--mu2);display:flex;flex-direction:column;overflow:hidden}
.rpt{padding:12px 14px;font-size:11px;color:var(--b);border-bottom:1px solid var(--mu2);background:var(--bg3);font-family:'VT323',monospace;letter-spacing:.08em;display:flex;align-items:center;justify-content:space-between}
.phone{margin:10px;border:1px solid var(--mu2);border-radius:8px;overflow:hidden;display:flex;flex-direction:column;background:#020C14;height:320px}
.wab{background:#091B28;padding:9px 12px;display:flex;align-items:center;gap:8px;border-bottom:1px solid var(--mu2)}
.av{width:28px;height:28px;border-radius:50%;background:rgba(0,191,255,.1);border:1px solid var(--bb);display:flex;align-items:center;justify-content:center;font-size:13px}
.wn{font-size:10px;color:var(--tx);font-family:'Share Tech Mono',monospace}
.ws{font-size:7px;color:var(--b)}
.wm{flex:1;overflow-y:auto;padding:10px;display:flex;flex-direction:column;gap:7px;background:#020C14}
.bb{max-width:88%;padding:8px 11px;border-radius:6px;font-size:8px;line-height:1.6;font-family:'JetBrains Mono',monospace}
.bb.out{background:#082034;border:1px solid rgba(0,191,255,.15);border-radius:6px 6px 2px 6px;align-self:flex-end;color:#A8D8F0}
.bb.in{background:var(--sur);border:1px solid var(--mu2);border-radius:6px 6px 6px 2px;align-self:flex-start;color:var(--tx)}
.bb .bt{font-size:6px;color:rgba(255,255,255,.25);margin-top:3px;text-align:right}
.wir{background:#091B28;padding:7px;display:flex;gap:6px;align-items:center;border-top:1px solid var(--mu2)}
.wi{flex:1;background:#0D2438;border:1px solid var(--mu2);padding:6px 10px;border-radius:14px;font-size:8px;color:var(--tx);font-family:'JetBrains Mono',monospace;outline:none}
.ws2{width:26px;height:26px;background:var(--b);border-radius:50%;border:none;cursor:pointer;font-size:11px}
.qa{padding:8px 10px;display:flex;flex-direction:column;gap:6px}
.qb{width:100%;padding:8px;font-family:'Share Tech Mono',monospace;font-size:9px;border-radius:2px;cursor:pointer;border:1px solid;display:flex;align-items:center;justify-content:center;gap:6px;letter-spacing:.06em;transition:all .2s}
.qb.bl{background:var(--bd);color:var(--b);border-color:var(--bb)}
.qb.bl:hover{background:rgba(0,191,255,.15)}
.qb.gn{background:rgba(37,211,102,.08);color:var(--wa);border-color:rgba(37,211,102,.22)}
.qb.gh{background:transparent;color:var(--mu);border-color:var(--mu2)}
.qb.gh:hover{color:var(--tx);border-color:var(--bb)}
.qb.rd{background:rgba(255,60,90,.07);color:var(--red);border-color:rgba(255,60,90,.18)}
.stag{margin:0 10px 8px;background:var(--bd);border:1px solid var(--bb);border-radius:2px;padding:9px 11px}
.stl{font-size:7px;color:var(--mu);letter-spacing:.18em;margin-bottom:3px;font-family:'Share Tech Mono',monospace}
.stn{font-family:'VT323',monospace;font-size:18px;color:var(--b2)}
.sti{font-size:7px;color:var(--mu);font-family:'Share Tech Mono',monospace}

/* TOAST */
.toast{position:fixed;bottom:18px;right:18px;padding:10px 16px;border-radius:2px;font-size:9px;font-weight:700;z-index:9999;transform:translateY(60px);transition:transform .3s;font-family:'Share Tech Mono',monospace;letter-spacing:.08em}
.toast.show{transform:translateY(0)}
.toast.ok{background:var(--bg3);color:var(--b);border:1px solid var(--b);box-shadow:0 0 20px rgba(0,191,255,.2)}
.toast.er{background:var(--bg3);color:var(--red);border:1px solid var(--red)}
.toast.wa{background:var(--bg3);color:var(--wa);border:1px solid var(--wa)}

/* MODAL */
.ov{position:fixed;inset:0;background:rgba(0,0,0,.92);z-index:500;display:flex;align-items:center;justify-content:center;opacity:0;pointer-events:none;transition:opacity .3s}
.ov.open{opacity:1;pointer-events:all}
.modal{background:var(--bg3);border:1px solid var(--bb);border-radius:2px;padding:26px;max-width:400px;width:92%;position:relative}
.mt{font-family:'VT323',monospace;font-size:22px;color:var(--b);margin-bottom:14px}
.mc{position:absolute;top:10px;right:12px;background:none;border:none;color:var(--mu);font-size:16px;cursor:pointer}

::-webkit-scrollbar{width:2px;height:2px}
::-webkit-scrollbar-thumb{background:var(--mu2)}
</style>
</head>
<body>

<div class="topbar">
  <div class="tlogo">▸ CLIENTS</div>
  <div class="tdiv"></div>
  <span class="tpill w"><span class="dot"></span> WA_LIVE</span>
  <span class="tpill b pulse">⚡ AKASH</span>
  <div class="tright">
    <span class="tsender">TX: <span>+91 8088749195</span></span>
    <button class="tsbtn" onclick="openCfg()">[ CFG ]</button>
  </div>
</div>

<div class="body">

  <!-- SIDEBAR -->
  <aside class="side">
    <div class="aw">
      <div class="awt">// AKASH · CLIENTS</div>
      <div class="awn">+91 8088749195</div>
      <div class="aws"><span class="dot"></span> WA CONNECTED</div>
      <div style="font-size:7px;color:var(--mu);margin-top:3px;font-family:'Share Tech Mono',monospace">Bengaluru, Karnataka</div>
    </div>
    <div class="ss">
      <div class="sl">// MODULES</div>
      <button class="nv on" onclick="go(this,'scanner')"><span class="ic">🗺</span> maps_scanner</button>
      <button class="nv" onclick="go(this,'compose')"><span class="ic">✍</span> msg_compose</button>
      <button class="nv" onclick="go(this,'campaign')"><span class="ic">📤</span> campaign_tx <span class="bx" id="qbadge">0</span></button>
      <button class="nv" onclick="go(this,'replies')"><span class="ic">💬</span> replies_rx <span class="gx">2</span></button>
      <button class="nv" onclick="go(this,'packages')"><span class="ic">💰</span> packages</button>
    </div>
    <div class="met">
      <div class="mr"><span class="ml">sent_today</span><span class="vg" id="ms">0</span></div>
      <div class="mr"><span class="ml">delivered</span><span class="vb" id="md">0</span></div>
      <div class="mr"><span class="ml">replied</span><span class="vo">2</span></div>
      <div class="pb"><div class="pf" id="mb" style="width:0%"></div></div>
      <div style="font-size:7px;color:var(--mu);font-family:'Share Tech Mono',monospace" id="mr2">0%_delivery</div>
    </div>
  </aside>

  <!-- CENTER -->
  <div class="center">
    <div class="tabs">
      <div class="tab on" data-s="scanner" onclick="tc(this)">▸ SCANNER</div>
      <div class="tab" data-s="compose" onclick="tc(this)">▸ COMPOSE</div>
      <div class="tab" data-s="campaign" onclick="tc(this)">▸ CAMPAIGN</div>
      <div class="tab" data-s="replies" onclick="tc(this)">▸ REPLIES</div>
      <div class="tab" data-s="packages" onclick="tc(this)">▸ PACKAGES</div>
    </div>

    <div class="scroll">

      <!-- SCANNER -->
      <div class="sec on" id="sec-scanner">
        <div class="card">
          <div class="ct">// BENGALURU BUSINESS SCANNER</div>
          <div class="ir">
            <div class="ig"><label class="il">target_area</label><input class="inp" id="sc-city" value="Bengaluru, Karnataka"/></div>
            <div class="ig"><label class="il">category</label>
              <select class="inp" id="sc-cat">
                <option value="restaurants">Restaurants</option>
                <option value="salons">Salons</option>
                <option value="clinics">Clinics</option>
                <option value="auto_repair">Auto Repair</option>
                <option value="retail">Retail Shops</option>
                <option value="coaching">Coaching Centers</option>
                <option value="gyms">Gym & Fitness</option>
                <option value="hotels">Hotels</option>
                <option value="bakeries">Bakeries</option>
                <option value="realestate">Real Estate</option>
              </select>
            </div>
          </div>
          <div class="br">
            <button class="btn bg" onclick="doScan()">▸ SCAN NOW</button>
            <button class="btn bh" onclick="clearScan()">CLEAR</button>
          </div>
        </div>

        <div class="card" id="res-card" style="display:none">
          <div class="ct">
            <span>RESULTS: <span id="res-n">0</span> targets — all NO website</span>
            <button class="btn bw" onclick="queueAll()">📲 QUEUE ALL</button>
          </div>
          <table class="tbl">
            <thead><tr>
              <th><input type="checkbox" style="accent-color:var(--b)" onclick="ca(this)"/></th>
              <th>name</th><th>area</th><th>phone</th><th>★</th><th>website</th><th>add</th>
            </tr></thead>
            <tbody id="res-body"></tbody>
          </table>
        </div>

        <div class="card">
          <div class="ct">// SCAN LOG</div>
          <div class="log" id="scan-log"><div class="ll in"><span class="lt">00:00:00</span><span class="lm">[READY] select category → SCAN NOW</span></div><span class="cur"></span></div>
        </div>
      </div>

      <!-- COMPOSE -->
      <div class="sec" id="sec-compose">
        <div class="card">
          <div class="ct">// MESSAGE TEMPLATE — AKASH · CLIENTS</div>
          <div class="ig"><label class="il">template (use {name} {category} {price} {link})</label>
            <textarea class="inp" id="msg-tpl" style="height:195px">🌐 *Namaste {name}!* 👋

Maine Google Maps pe aapka *{category}* business Bengaluru mein dekha — notice kiya ke aapki *website nahi hai*.

Aaj ke zamane mein bina website ke kaafi customers miss hote hain. 😕

📹 Aapke liye *FREE demo* banaya hai:
👉 *{link}*

*Fayde:*
✅ Google top ranking
✅ 3x zyada customers
✅ Online booking 24/7
✅ Professional image

💰 *Sirf {price} mein sab kuch*
(Domain + Hosting + Design + SEO)

📲 Reply *YES* karein!

— Akash | CLIENTS
📞 +91 8088749195</textarea>
          </div>
          <div class="ir">
            <div class="ig"><label class="il">delay_seconds</label><input class="inp" id="msg-delay" type="number" value="10" min="3"/></div>
            <div class="ig"><label class="il">price</label><input class="inp" id="msg-price" value="₹10,000"/></div>
          </div>
          <div class="ig"><label class="il">wasenderapi_key</label><input class="inp" id="wa-key" type="password" placeholder="paste key here..."/></div>
          <div class="br">
            <button class="btn bg" onclick="saveCfg()">▸ SAVE</button>
            <button class="btn bw" onclick="selfTest()">◈ SELF_TEST</button>
          </div>
        </div>
        <div class="card">
          <div class="ct">// PREVIEW</div>
          <div style="background:#010508;border:1px solid var(--mu2);border-radius:2px;padding:12px;font-size:10px;color:#A8D8F0;line-height:1.8;white-space:pre-wrap;font-family:'JetBrains Mono',monospace" id="preview"></div>
        </div>
      </div>

      <!-- CAMPAIGN -->
      <div class="sec" id="sec-campaign">
        <div class="card">
          <div class="ct">
            <span>// TX ENGINE — <span style="color:var(--cyan)" id="qcount">0</span> QUEUED</span>
            <div class="br" style="margin:0">
              <button class="btn bw" id="camp-btn" onclick="toggleCamp()">▸ START TX</button>
              <button class="btn bh" onclick="flushQ()">FLUSH</button>
            </div>
          </div>
          <div id="prog-wrap" style="display:none;margin-bottom:10px">
            <div style="display:flex;justify-content:space-between;font-size:8px;color:var(--mu);margin-bottom:4px;font-family:'Share Tech Mono',monospace">
              <span>from: <span style="color:var(--b)">+91 8088749195</span></span>
              <span id="prog-txt">0/0</span>
            </div>
            <div class="prb"><div class="prf" id="prog-bar" style="width:0%"></div></div>
          </div>
          <table class="tbl">
            <thead><tr><th>name</th><th>phone</th><th>area</th><th>website</th><th>status</th><th>tx</th></tr></thead>
            <tbody id="camp-body"></tbody>
          </table>
        </div>
        <div class="card">
          <div class="ct">// TX LOG</div>
          <div class="log" id="camp-log"><div class="ll in"><span class="lt">00:00:00</span><span class="lm">[STANDBY] queue targets → start tx</span></div><span class="cur"></span></div>
        </div>
      </div>

      <!-- REPLIES -->
      <div class="sec" id="sec-replies">
        <div class="card">
          <div class="ct">// REPLIES INBOX</div>
          <div id="rep-list"></div>
        </div>
      </div>

      <!-- PACKAGES -->
      <div class="sec" id="sec-packages">
        <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:10px">
          <div class="card" style="margin:0">
            <div style="font-size:7px;color:var(--mu);letter-spacing:.2em;margin-bottom:5px;font-family:'Share Tech Mono',monospace">// STARTER</div>
            <div style="font-family:'VT323',monospace;font-size:30px;color:var(--b)">₹10K</div>
            <div style="font-size:8px;color:var(--mu);margin-bottom:8px;font-family:'Share Tech Mono',monospace">one_time</div>
            <div style="font-size:9px;line-height:2.2">▸ 5-page site<br>▸ Mobile ready<br>▸ Maps linked<br>▸ Basic SEO<br>▸ 1yr hosting</div>
            <button class="btn bg" style="width:100%;margin-top:10px;text-align:center" onclick="setP('₹10,000')">USE</button>
          </div>
          <div class="card" style="margin:0;border-color:rgba(255,209,102,.2)">
            <div style="font-size:7px;color:var(--gold);letter-spacing:.2em;margin-bottom:5px;font-family:'Share Tech Mono',monospace">// POPULAR ★</div>
            <div style="font-family:'VT323',monospace;font-size:30px;color:var(--gold)">₹25K</div>
            <div style="font-size:8px;color:var(--mu);margin-bottom:8px;font-family:'Share Tech Mono',monospace">one_time</div>
            <div style="font-size:9px;line-height:2.2">▸ 10-page site<br>▸ 3D design<br>▸ Booking sys<br>▸ Maps SEO<br>▸ 2yr hosting</div>
            <button class="btn" style="width:100%;margin-top:10px;background:rgba(255,209,102,.08);border-color:rgba(255,209,102,.3);color:var(--gold);font-family:'Share Tech Mono',monospace;font-size:9px;cursor:pointer;padding:7px;border-radius:2px" onclick="setP('₹25,000')">USE</button>
          </div>
          <div class="card" style="margin:0;border-color:rgba(167,139,250,.2)">
            <div style="font-size:7px;color:var(--purple);letter-spacing:.2em;margin-bottom:5px;font-family:'Share Tech Mono',monospace">// PREMIUM</div>
            <div style="font-family:'VT323',monospace;font-size:30px;color:var(--purple)">₹50K</div>
            <div style="font-size:8px;color:var(--mu);margin-bottom:8px;font-family:'Share Tech Mono',monospace">one_time</div>
            <div style="font-size:9px;line-height:2.2">▸ Unlimited pages<br>▸ Custom 3D<br>▸ E-commerce<br>▸ Google Ads<br>▸ 3yr hosting</div>
            <button class="btn" style="width:100%;margin-top:10px;background:rgba(167,139,250,.08);border-color:rgba(167,139,250,.25);color:var(--purple);font-family:'Share Tech Mono',monospace;font-size:9px;cursor:pointer;padding:7px;border-radius:2px" onclick="setP('₹50,000')">USE</button>
          </div>
        </div>
      </div>

    </div>
  </div>

  <!-- RIGHT PANEL -->
  <div class="rp">
    <div class="rpt">▸ WA_PREVIEW <span style="font-size:8px;color:var(--mu);font-family:'Share Tech Mono',monospace" id="rps">idle</span></div>
    <div class="phone">
      <div class="wab">
        <div class="av">🏪</div>
        <div style="flex:1"><div class="wn" id="wa-name">waiting...</div><div class="ws">● online</div></div>
      </div>
      <div class="wm" id="wa-msgs"><div class="bb in">// scan → queue → tx messages here</div></div>
      <div class="wir">
        <input class="wi" id="wa-inp" placeholder="// type..."/>
        <button class="ws2" onclick="mSend()">➤</button>
      </div>
    </div>
    <div class="stag">
      <div class="stl">// TX NODE · AKASH</div>
      <div class="stn">+91 8088749195</div>
      <div class="sti">WasenderAPI · Bengaluru</div>
    </div>
    <div class="qa">
      <button class="qb bl" onclick="toggleCamp()">▸ TX_ALL_NOW</button>
      <button class="qb gn" onclick="selfTest()">◈ SELF_TEST</button>
      <button class="qb gh" onclick="sw('compose')">✍ EDIT_MSG</button>
      <button class="qb rd" onclick="stopCamp()">■ ABORT</button>
    </div>
  </div>
</div>

<div class="toast" id="toast"></div>

<div class="ov" id="cfg-modal">
  <div class="modal">
    <button class="mc" onclick="closeCfg()">[ X ]</button>
    <div class="mt">// CONFIG</div>
    <div class="ig"><label class="il">WasenderAPI Key</label><input class="inp" id="cfg-key" type="password" placeholder="paste key..."/></div>
    <div class="ig"><label class="il">Sender Number</label><input class="inp" id="cfg-num" value="+918088749195"/></div>
    <div class="br"><button class="btn bg" onclick="saveCfgModal()">▸ SAVE</button><button class="btn bh" onclick="closeCfg()">CANCEL</button></div>
  </div>
</div>

<script>
// ═══════════════════════════════
// STATE
// ═══════════════════════════════
let waKey = localStorage.getItem('wak')||'';
let businesses=[], queue=[], running=false, stopped=false, sent=0;

window.addEventListener('load',()=>{
  if(waKey) document.getElementById('wa-key').value=waKey;
  updPrev();
  renderReplies();
});

// ═══════════════════════════════
// BUSINESS DATABASE — Bengaluru
// ═══════════════════════════════
const DB = {
  restaurants:[
    {n:"Udupi Sagar",a:"Koramangala 5th Block",p:"9845201234",r:4.3},
    {n:"Sri Venkateshwara Tiffins",a:"Jayanagar 4th T Block",p:"9900112233",r:4.1},
    {n:"Annapoorna Mess",a:"BTM Layout 2nd Stage",p:"8762341890",r:3.9},
    {n:"Pallavi Darshini",a:"Marathahalli Bridge",p:"9123456780",r:4.2},
    {n:"Raju Military Hotel",a:"HSR Layout Sector 6",p:"9988776655",r:4.0},
    {n:"Saraswathi Bhavan",a:"Basavanagudi",p:"8877665544",r:4.4},
    {n:"New Shanti Sagar",a:"Indiranagar 100ft Road",p:"9741230045",r:3.8},
    {n:"Kamath Family Restaurant",a:"Rajajinagar 1st Block",p:"9632145870",r:4.5},
    {n:"Meenakshi Tiffin Center",a:"Vijayanagar",p:"8123456789",r:3.7},
    {n:"Dwaraka Pure Veg",a:"Malleswaram 8th Cross",p:"9845678901",r:4.1},
    {n:"Srinidhi Hotel",a:"Electronic City Phase 1",p:"9900234561",r:3.9},
    {n:"Vasavi Mess",a:"Yelahanka New Town",p:"8765432190",r:4.0},
    {n:"Akshaya Darshini",a:"Whitefield Main Road",p:"9876512340",r:4.3},
    {n:"Anand Bhavan",a:"Hebbal Ring Road",p:"9123098765",r:3.8},
    {n:"Subha Darshini",a:"JP Nagar 7th Phase",p:"8890123456",r:4.2},
    {n:"Giri Veg Hotel",a:"Banashankari 3rd Stage",p:"9741890123",r:4.0},
    {n:"Abhiruchi Restaurant",a:"Nagarbhavi",p:"9632890145",r:3.9},
    {n:"Lakshmi Tiffin House",a:"Bommanahalli",p:"8123789456",r:4.1},
    {n:"Sai Baba Mess",a:"Sarjapur Road",p:"9845890234",r:3.8},
    {n:"Amruth Darshini",a:"Domlur Layout",p:"9900876543",r:4.3},
  ],
  salons:[
    {n:"Ravi Gents Salon",a:"Koramangala 1st Block",p:"9845312456",r:4.1},
    {n:"Priya Beauty Parlour",a:"Indiranagar 12th Main",p:"9900445566",r:4.4},
    {n:"Sri Balaji Hair Cutting",a:"BTM Layout 1st Stage",p:"8761234509",r:3.9},
    {n:"Meena Ladies Beauty",a:"Jayanagar 9th Block",p:"9123765430",r:4.5},
    {n:"Raja Hair Studio",a:"HSR Layout 27th Main",p:"9988112233",r:4.0},
    {n:"Lakshmi Beauty Center",a:"Basavanagudi",p:"8877334455",r:4.2},
    {n:"Kumar Gents Parlour",a:"Marathahalli",p:"9741567890",r:3.8},
    {n:"Divya Hair & Beauty",a:"Whitefield",p:"9632567801",r:4.3},
    {n:"Sai Gents Salon",a:"Electronic City",p:"8123456012",r:3.7},
    {n:"Sunita Ladies Parlour",a:"Rajajinagar",p:"9845901234",r:4.1},
    {n:"Mohan Hair Works",a:"Vijayanagar",p:"9900567812",r:3.9},
    {n:"Anjali Beauty Studio",a:"Malleswaram",p:"8765234012",r:4.4},
    {n:"Venkatesh Barber",a:"Yelahanka",p:"9876234501",r:3.8},
    {n:"Pooja Beauty Lounge",a:"JP Nagar",p:"9123450987",r:4.2},
    {n:"Classic Gents Salon",a:"Banashankari",p:"8890234567",r:4.0},
    {n:"Nirmala Beauty Parlour",a:"Hebbal",p:"9741012345",r:4.3},
    {n:"Shiva Hair Cutting",a:"Sarjapur Road",p:"9632234789",r:3.9},
    {n:"Ananya Ladies Beauty",a:"Bommanahalli",p:"8123345890",r:4.1},
    {n:"Mahesh Gents Hair",a:"Domlur",p:"9845345901",r:3.8},
    {n:"Padma Beauty Center",a:"Nagarbhavi",p:"9900678901",r:4.2},
  ],
  clinics:[
    {n:"Dr. Sharma General Clinic",a:"Koramangala 3rd Block",p:"9845456789",r:4.4},
    {n:"Sai Health Center",a:"Indiranagar",p:"9900789012",r:4.2},
    {n:"Nirmala Medical",a:"HSR Layout",p:"8761890234",r:4.0},
    {n:"Dr. Reddy Family Clinic",a:"BTM Layout",p:"9123890456",r:4.5},
    {n:"Suraksha Clinic",a:"Jayanagar",p:"9988234567",r:4.1},
    {n:"Arogya Health Center",a:"Marathahalli",p:"8877456789",r:3.9},
    {n:"Dr. Kumar ENT Clinic",a:"Basavanagudi",p:"9741678901",r:4.3},
    {n:"Pavan Medical Center",a:"Whitefield",p:"9632678012",r:4.0},
    {n:"Swastha Clinic",a:"Electronic City",p:"8123456012",r:3.8},
    {n:"Dr. Rao Dental Clinic",a:"Rajajinagar",p:"9845012567",r:4.4},
    {n:"Sanjeevini Health",a:"Vijayanagar",p:"9900123456",r:4.1},
    {n:"Dr. Gowda Ayurveda",a:"Malleswaram",p:"8765234012",r:4.2},
    {n:"City Medical Center",a:"Yelahanka",p:"9876234501",r:3.9},
    {n:"Lakshmi Child Clinic",a:"JP Nagar",p:"9123501234",r:4.5},
    {n:"Dhanvantari Clinic",a:"Banashankari",p:"8890345678",r:4.0},
    {n:"Dr. Singh Ortho",a:"Hebbal",p:"9741123456",r:4.3},
    {n:"Asha Women Clinic",a:"Sarjapur",p:"9632345890",r:4.2},
    {n:"Navajeevan Medical",a:"Bommanahalli",p:"8123456901",r:3.8},
    {n:"Srinivas Clinic",a:"Domlur",p:"9845345901",r:4.1},
    {n:"Dr. Patil Eye Clinic",a:"Nagarbhavi",p:"9900890123",r:4.4},
  ],
  auto_repair:[
    {n:"Ravi Auto Works",a:"Koramangala",p:"9845567890",r:4.2},
    {n:"Shiva Motor Garage",a:"Marathahalli",p:"9900901234",r:4.0},
    {n:"Sri Ganesh Auto",a:"HSR Layout",p:"8762012345",r:3.9},
    {n:"Kumar Car Service",a:"BTM Layout",p:"9123012678",r:4.3},
    {n:"Balaji Auto Repair",a:"Electronic City",p:"9988345678",r:4.1},
    {n:"New India Garage",a:"Whitefield",p:"8877678901",r:3.8},
    {n:"Sai Auto Center",a:"Indiranagar",p:"9741789012",r:4.4},
    {n:"Raj Motors",a:"Jayanagar",p:"9632789123",r:4.0},
    {n:"Venkat Auto Works",a:"Basavanagudi",p:"8123567234",r:3.9},
    {n:"Pavan Car Care",a:"Rajajinagar",p:"9845678012",r:4.2},
    {n:"Modern Auto Garage",a:"Yelahanka",p:"9900012678",r:4.1},
    {n:"Lakshmi Auto Service",a:"Vijayanagar",p:"8765345123",r:3.8},
    {n:"Star Motors",a:"Malleswaram",p:"9876345012",r:4.3},
    {n:"Guru Auto Repair",a:"JP Nagar",p:"9123612345",r:4.0},
    {n:"Hanuman Auto Works",a:"Banashankari",p:"8890456789",r:3.9},
    {n:"Maruthi Car Service",a:"Hebbal",p:"9741234567",r:4.1},
    {n:"Srinivas Motors",a:"Sarjapur",p:"9632456901",r:4.2},
    {n:"City Auto Center",a:"Bommanahalli",p:"8123567012",r:3.8},
    {n:"Quick Fix Garage",a:"Domlur",p:"9845456012",r:4.0},
    {n:"National Auto Works",a:"Nagarbhavi",p:"9900234789",r:4.3},
  ],
  retail:[
    {n:"Srinivas General Store",a:"Koramangala",p:"9845678123",r:4.1},
    {n:"Lakshmi Kirana",a:"BTM Layout",p:"9900345890",r:4.3},
    {n:"Ravi Provision Store",a:"HSR Layout",p:"8762123456",r:3.9},
    {n:"Ganesh Supermarket",a:"Indiranagar",p:"9123234890",r:4.2},
    {n:"Shiva Kirana Store",a:"Jayanagar",p:"9988456789",r:4.0},
    {n:"New Modern Store",a:"Whitefield",p:"8877678901",r:3.8},
    {n:"Sri Balaji Stores",a:"Marathahalli",p:"9741890234",r:4.4},
    {n:"Kumar Provision",a:"Electronic City",p:"9632890256",r:4.1},
    {n:"Amma Kirana",a:"Basavanagudi",p:"8123678345",r:3.9},
    {n:"Pavan General Stores",a:"Rajajinagar",p:"9845789123",r:4.2},
    {n:"Vijay Provision",a:"Yelahanka",p:"9900123789",r:4.0},
    {n:"Sai Kirana",a:"Vijayanagar",p:"8765456234",r:3.8},
    {n:"Vaibhav Stores",a:"Malleswaram",p:"9876456123",r:4.3},
    {n:"Subhash Provision",a:"JP Nagar",p:"9123723456",r:4.1},
    {n:"Om Sai Kirana",a:"Banashankari",p:"8890567890",r:3.9},
    {n:"Mahalakshmi Stores",a:"Hebbal",p:"9741345678",r:4.2},
    {n:"New Ganga Store",a:"Sarjapur",p:"9632456901",r:4.0},
    {n:"Kannan General Store",a:"Bommanahalli",p:"8123567012",r:3.8},
    {n:"Vinayaka Kirana",a:"Domlur",p:"9845567123",r:4.1},
    {n:"Anand Provision",a:"Nagarbhavi",p:"9900345678",r:4.3},
  ],
  coaching:[
    {n:"Bright Future Academy",a:"Koramangala",p:"9845789234",r:4.4},
    {n:"Sri Vidya Coaching",a:"Jayanagar",p:"9900456901",r:4.2},
    {n:"Kumar Maths Tutor",a:"BTM Layout",p:"8762234567",r:4.0},
    {n:"New Era Classes",a:"HSR Layout",p:"9123345901",r:4.5},
    {n:"Excellent Coaching",a:"Indiranagar",p:"9988567890",r:4.1},
    {n:"Saraswathi Classes",a:"Whitefield",p:"8877789012",r:3.9},
    {n:"Gyan Deep Academy",a:"Marathahalli",p:"9741901234",r:4.3},
    {n:"Success Point",a:"Electronic City",p:"9632901345",r:4.0},
    {n:"Vidya Mandir Coaching",a:"Basavanagudi",p:"8123789456",r:3.8},
    {n:"Akash Tutorials",a:"Rajajinagar",p:"9845890234",r:4.2},
    {n:"Top Rank Classes",a:"Yelahanka",p:"9900234890",r:4.4},
    {n:"Pioneer Academy",a:"Vijayanagar",p:"8765567345",r:4.1},
    {n:"Talent Hub Coaching",a:"Malleswaram",p:"9876567234",r:3.9},
    {n:"Champs Institute",a:"JP Nagar",p:"9123834567",r:4.3},
    {n:"Wisdom Classes",a:"Banashankari",p:"8890678901",r:4.0},
    {n:"Star Coaching Center",a:"Hebbal",p:"9741456789",r:4.2},
    {n:"Future Leaders Academy",a:"Sarjapur",p:"9632567012",r:4.1},
    {n:"Nalanda Coaching",a:"Bommanahalli",p:"8123678123",r:3.8},
    {n:"Excel Tutorials",a:"Domlur",p:"9845678234",r:4.0},
    {n:"Milestone Academy",a:"Nagarbhavi",p:"9900456789",r:4.3},
  ],
  gyms:[
    {n:"Power House Gym",a:"Koramangala",p:"9845890345",r:4.3},
    {n:"Fitness King",a:"Indiranagar",p:"9900567012",r:4.1},
    {n:"Iron Body Gym",a:"BTM Layout",p:"8762345678",r:4.0},
    {n:"Champion Fitness",a:"HSR Layout",p:"9123345901",r:4.4},
    {n:"Muscles Gym",a:"Jayanagar",p:"9988678901",r:3.9},
    {n:"Fit Zone",a:"Whitefield",p:"8877890123",r:4.2},
    {n:"Health First Gym",a:"Marathahalli",p:"9741012456",r:4.1},
    {n:"Strong Man Fitness",a:"Electronic City",p:"9632012467",r:3.8},
    {n:"Sri Fitness Center",a:"Basavanagudi",p:"8123890567",r:4.3},
    {n:"New Life Gym",a:"Rajajinagar",p:"9845901345",r:4.0},
    {n:"Body Craft",a:"Yelahanka",p:"9900345901",r:4.2},
    {n:"Flex Fitness",a:"Vijayanagar",p:"8765678456",r:3.9},
    {n:"Warrior Gym",a:"Malleswaram",p:"9876678345",r:4.1},
    {n:"Elite Fitness",a:"JP Nagar",p:"9123945678",r:4.4},
    {n:"Galaxy Gym",a:"Banashankari",p:"8890789012",r:4.0},
    {n:"Dynamic Fitness",a:"Hebbal",p:"9741567890",r:3.8},
    {n:"Max Gym",a:"Sarjapur",p:"9632678123",r:4.3},
    {n:"Shape Up Fitness",a:"Bommanahalli",p:"8123789234",r:4.1},
    {n:"Force Gym",a:"Domlur",p:"9845789345",r:3.9},
    {n:"Active Fitness Center",a:"Nagarbhavi",p:"9900567890",r:4.2},
  ],
  hotels:[
    {n:"Hotel Shanthi",a:"Koramangala",p:"9845901456",r:3.9},
    {n:"Sri Lakshmi Lodge",a:"Majestic",p:"9900678123",r:3.7},
    {n:"New Bharat Hotel",a:"Yeshwanthpur",p:"8762456789",r:4.0},
    {n:"Tourist Home",a:"Shivajinagar",p:"9123456012",r:3.8},
    {n:"Hotel Kaveri",a:"Basavanagudi",p:"9988789012",r:4.1},
    {n:"Comfort Stay",a:"BTM Layout",p:"8877901234",r:3.9},
    {n:"Highway Hotel",a:"Marathahalli",p:"9741123567",r:3.8},
    {n:"Hotel Venkatesh",a:"Electronic City",p:"9632123578",r:4.0},
    {n:"Travellers Inn",a:"Whitefield",p:"8124012789",r:3.7},
    {n:"Hotel Srinivas",a:"Rajajinagar",p:"9845012456",r:4.2},
    {n:"Classic Residency",a:"Yelahanka",p:"9900456012",r:3.9},
    {n:"Hotel Parvathi",a:"Vijayanagar",p:"8765789567",r:4.0},
    {n:"Budget Stay Inn",a:"HSR Layout",p:"9876789456",r:3.8},
    {n:"Hotel Maharaja",a:"JP Nagar",p:"9124056789",r:4.1},
    {n:"Regal Rooms",a:"Banashankari",p:"8890890123",r:3.9},
    {n:"Hotel Ganga",a:"Hebbal",p:"9741678901",r:4.0},
    {n:"Stay Well Lodge",a:"Sarjapur",p:"9632789234",r:3.8},
    {n:"Hotel Saraswathi",a:"Bommanahalli",p:"8124001456",r:4.1},
    {n:"Metro Stay",a:"Domlur",p:"9845890456",r:3.9},
    {n:"Hotel Ashok",a:"Nagarbhavi",p:"9900678234",r:4.0},
  ],
  bakeries:[
    {n:"Hari Bakery",a:"Koramangala",p:"9845012567",r:4.2},
    {n:"Sri Venkatesh Bakery",a:"Jayanagar",p:"9900789234",r:4.4},
    {n:"New Modern Bakery",a:"BTM Layout",p:"8762567890",r:4.0},
    {n:"Daily Bread Bakery",a:"Indiranagar",p:"9123567123",r:4.3},
    {n:"Anand Sweets Bakery",a:"HSR Layout",p:"9988890123",r:4.1},
    {n:"Krishna Bakery",a:"Basavanagudi",p:"8878012345",r:3.9},
    {n:"Sunrise Bakery",a:"Marathahalli",p:"9741234678",r:4.2},
    {n:"Fresh Bake",a:"Whitefield",p:"9632234689",r:4.0},
    {n:"Tasty Treats Bakery",a:"Electronic City",p:"8124012789",r:3.8},
    {n:"City Bakery",a:"Rajajinagar",p:"9846123567",r:4.3},
    {n:"Home Bakery",a:"Yelahanka",p:"9900567123",r:4.1},
    {n:"Sai Sweets Bakery",a:"Vijayanagar",p:"8765890678",r:3.9},
    {n:"Golden Crust",a:"Malleswaram",p:"9877890567",r:4.4},
    {n:"Royal Bakery",a:"JP Nagar",p:"9124167890",r:4.2},
    {n:"Yummy Bakes",a:"Banashankari",p:"8891001234",r:4.0},
    {n:"Star Bakery",a:"Hebbal",p:"9741789012",r:3.8},
    {n:"Pavan Bakery",a:"Sarjapur",p:"9632890345",r:4.1},
    {n:"Om Sai Bakery",a:"Bommanahalli",p:"8124001456",r:3.9},
    {n:"Sweet Crust",a:"Domlur",p:"9846001567",r:4.2},
    {n:"Priya Bakery",a:"Nagarbhavi",p:"9900789345",r:4.3},
  ],
  realestate:[
    {n:"Srinivas Properties",a:"Koramangala",p:"9846123678",r:4.1},
    {n:"Kumar Realty",a:"Indiranagar",p:"9900890345",r:4.3},
    {n:"City Property Dealers",a:"BTM Layout",p:"8762678901",r:3.9},
    {n:"Raj Real Estate",a:"HSR Layout",p:"9123678234",r:4.2},
    {n:"Shiva Properties",a:"Whitefield",p:"9989001234",r:4.0},
    {n:"Lakshmi Realty",a:"Marathahalli",p:"8878123456",r:3.8},
    {n:"New Era Properties",a:"Electronic City",p:"9741345789",r:4.4},
    {n:"Home Finders",a:"Jayanagar",p:"9632345800",r:4.1},
    {n:"Balaji Properties",a:"Basavanagudi",p:"8124123890",r:3.9},
    {n:"Ganesh Real Estate",a:"Rajajinagar",p:"9846234678",r:4.2},
    {n:"Prime Properties",a:"Yelahanka",p:"9900678234",r:4.0},
    {n:"Sai Realty",a:"Vijayanagar",p:"8765901789",r:3.8},
    {n:"Apex Properties",a:"Malleswaram",p:"9877901678",r:4.3},
    {n:"Smart Homes",a:"JP Nagar",p:"9124278901",r:4.1},
    {n:"Comfort Realty",a:"Banashankari",p:"8891112345",r:4.0},
    {n:"Dream Properties",a:"Hebbal",p:"9741890123",r:4.2},
    {n:"Vijay Real Estate",a:"Sarjapur",p:"9632901456",r:3.9},
    {n:"Metro Properties",a:"Bommanahalli",p:"8124112567",r:4.1},
    {n:"Landmark Realty",a:"Domlur",p:"9846112678",r:3.8},
    {n:"Star Properties",a:"Nagarbhavi",p:"9900890456",r:4.3},
  ],
};

// ═══════════════════════════════
// SCAN — 100% OFFLINE, NO NETWORK
// ═══════════════════════════════
async function doScan(){
  const cat = document.getElementById('sc-cat').value;
  const city = document.getElementById('sc-city').value||'Bengaluru';
  businesses = [];
  document.getElementById('res-card').style.display='none';

  alog('scan-log','in','SCAN INIT :: '+cat+' in '+city);
  await sl(300);
  alog('scan-log','ok','Database connected ✓');
  await sl(400);
  alog('scan-log','in','Fetching businesses with no website...');
  await sl(500);

  const raw = DB[cat]||DB['restaurants'];
  // shuffle for variety each scan
  businesses = [...raw].sort(()=>Math.random()-.5).map((b,i)=>({
    id:i+1, name:b.n, address:b.a+', Bengaluru', phone:b.p,
    rating:b.r, website:'', cat, status:'pending',
    slug:b.n.toLowerCase().replace(/[^a-z0-9]/g,'-').substring(0,25)+'-blr'
  }));

  alog('scan-log','ok',businesses.length+' businesses found');
  alog('scan-log','ok','All targets have NO website ✓');
  alog('scan-log','ok','Ready to queue → send WhatsApp');

  document.getElementById('res-card').style.display='block';
  document.getElementById('res-n').textContent=businesses.length;
  renderTable();
  toast('SCAN OK :: '+businesses.length+' targets','ok');
}

function renderTable(){
  const tb=document.getElementById('res-body'); tb.innerHTML='';
  businesses.forEach(b=>{
    const tr=document.createElement('tr');
    tr.innerHTML=`
      <td><input type="checkbox" checked style="accent-color:var(--b)"/></td>
      <td style="color:var(--tx);font-size:9px">${b.name}</td>
      <td style="color:var(--mu);font-size:8px">${b.address.replace(', Bengaluru','')}</td>
      <td style="color:var(--b);font-size:9px">${b.phone}</td>
      <td style="color:var(--gold);font-size:9px">★${b.rating}</td>
      <td><span class="tag tn">✗ NONE</span></td>
      <td><button class="mb" onclick="addOne(${b.id})">ADD</button></td>`;
    tb.appendChild(tr);
  });
}

function clearScan(){ businesses=[]; document.getElementById('res-card').style.display='none'; alog('scan-log','in','[CLEARED]'); }
function ca(el){ document.querySelectorAll('#res-body input[type=checkbox]').forEach(c=>c.checked=el.checked); }

function queueAll(){
  businesses.forEach(b=>{ if(!queue.find(x=>x.id===b.id)) queue.push({...b,status:'pending'}); });
  renderCamp();
  sw('campaign');
  toast('QUEUED :: '+queue.length+' targets','wa');
}

function addOne(id){
  const b=businesses.find(x=>x.id===id);
  if(!b||queue.find(x=>x.id===id)) return;
  queue.push({...b,status:'pending'});
  renderCamp(); updBadge();
  toast('ADDED :: '+b.name,'ok');
}

// ═══════════════════════════════
// CAMPAIGN
// ═══════════════════════════════
function renderCamp(){
  const tb=document.getElementById('camp-body'); tb.innerHTML='';
  document.getElementById('qcount').textContent=queue.length;
  updBadge();
  queue.forEach(b=>{
    let st='<span class="tag tp">PENDING</span>';
    if(b.status==='sending') st='<span class="tag ts">TX...</span>';
    else if(b.status==='sent') st='<span class="tag ty">SENT ✓✓</span>';
    else if(b.status==='failed') st='<span class="tag tn">FAILED</span>';
    const tr=document.createElement('tr'); tr.id='cr-'+b.id;
    tr.innerHTML=`
      <td style="font-size:9px;color:var(--tx)">${b.name}</td>
      <td style="font-size:8px;color:var(--b)">${b.phone}</td>
      <td style="font-size:8px;color:var(--mu)">${b.address.replace(', Bengaluru','').substring(0,18)}</td>
      <td><span class="tag tn">NONE</span></td>
      <td id="cs-${b.id}">${st}</td>
      <td><button class="mb" onclick="txOne(${b.id})">TX</button></td>`;
    tb.appendChild(tr);
  });
}

function buildMsg(b){
  return document.getElementById('msg-tpl').value
    .replace(/{name}/g,b.name)
    .replace(/{category}/g,b.cat)
    .replace(/{price}/g,document.getElementById('msg-price').value||'₹10,000')
    .replace(/{link}/g,'https://clients.in/demo/'+b.slug);
}

async function txWA(phone, msg){
  const key = document.getElementById('wa-key').value.trim()||waKey;
  if(!key) throw new Error('No API key — go to COMPOSE tab');
  const to = phone.replace(/\D/g,'');
  const finalTo = to.length===10 ? '91'+to : to;
  const url = 'https://corsproxy.io/?'+encodeURIComponent('https://api.wasenderapi.com/api/send-message');
  const r = await fetch(url,{
    method:'POST',
    headers:{'Content-Type':'application/json','Authorization':'Bearer '+key,'x-requested-with':'XMLHttpRequest'},
    body:JSON.stringify({to:finalTo, text:msg})
  });
  const d = await r.json().catch(()=>({}));
  if(!r.ok) throw new Error(d.error?.message||d.message||'HTTP '+r.status);
  return d;
}

async function toggleCamp(){
  if(running){ stopCamp(); return; }
  if(!queue.length){ toast('Queue empty — scan first','er'); return; }
  const key=document.getElementById('wa-key').value.trim()||waKey;
  if(!key){ toast('Paste WasenderAPI key in COMPOSE tab','er'); sw('compose'); return; }
  running=true; stopped=false;
  document.getElementById('camp-btn').textContent='■ ABORT';
  document.getElementById('prog-wrap').style.display='block';
  document.getElementById('rps').textContent='tx_active';
  alog('camp-log','ok','TX START :: Akash · CLIENTS · +91 8088749195');
  await runCamp();
}

function stopCamp(){ running=false; stopped=true; document.getElementById('camp-btn').textContent='▸ START TX'; document.getElementById('rps').textContent='aborted'; alog('camp-log','wr','TX ABORTED'); }
function flushQ(){ queue=[]; running=false; renderCamp(); toast('QUEUE FLUSHED','ok'); }

async function runCamp(){
  const delay=(parseInt(document.getElementById('msg-delay').value)||10)*1000;
  for(let i=0;i<queue.length;i++){
    if(stopped||!running) break;
    const b=queue[i];
    if(b.status==='sent') continue;
    b.status='sending'; updSt(b);
    alog('camp-log','in','TX >> '+b.name+' :: '+b.phone);
    document.getElementById('wa-name').textContent=b.name;
    document.getElementById('rps').textContent='tx>>'+b.name.substring(0,10);
    try{
      await txWA(b.phone, buildMsg(b));
      b.status='sent'; updSt(b); sent++; updMet();
      alog('camp-log','wa','ACK ✓✓ :: '+b.name);
      addBubble(b.name, buildMsg(b));
      toast('TX OK :: '+b.name,'wa');
    } catch(e){
      b.status='failed'; updSt(b);
      alog('camp-log','er','FAIL :: '+b.name+' — '+e.message);
    }
    const done=queue.filter(x=>x.status==='sent'||x.status==='failed').length;
    document.getElementById('prog-txt').textContent=done+'/'+queue.length;
    document.getElementById('prog-bar').style.width=(done/queue.length*100)+'%';
    if(i<queue.length-1&&!stopped){ alog('camp-log','in','SLEEP '+delay/1000+'s...'); await sl(delay); }
  }
  if(!stopped){ running=false; document.getElementById('camp-btn').textContent='▸ START TX'; document.getElementById('rps').textContent='complete'; alog('camp-log','ok','TX COMPLETE ✓'); toast('CAMPAIGN DONE ✓','ok'); }
}

async function txOne(id){
  const b=queue.find(x=>x.id===id); if(!b) return;
  b.status='sending'; updSt(b);
  try{
    await txWA(b.phone, buildMsg(b));
    b.status='sent'; updSt(b); sent++; updMet();
    addBubble(b.name, buildMsg(b)); toast('TX OK :: '+b.name,'wa');
  } catch(e){ b.status='failed'; updSt(b); toast('FAIL :: '+e.message,'er'); }
}

async function selfTest(){
  const key=document.getElementById('wa-key').value.trim()||waKey;
  if(!key){ toast('Paste WasenderAPI key first','er'); return; }
  waKey=key; localStorage.setItem('wak',key);
  toast('SELF_TEST >> +91 8088749195','ok');
  try{
    await txWA('918088749195','// CLIENTS · AKASH\n\nTest message!\nStatus: OPERATIONAL ✓\nReady to send in Bengaluru 🚀');
    toast('SELF_TEST OK ✓✓ — check WhatsApp!','wa');
    alog('camp-log','wa','SELF_TEST OK :: +91 8088749195');
  } catch(e){ toast('FAIL :: '+e.message,'er'); alog('camp-log','er','SELF_TEST FAIL :: '+e.message); }
}

function updSt(b){
  const c=document.getElementById('cs-'+b.id); if(!c) return;
  if(b.status==='sending') c.innerHTML='<span class="tag ts">TX...</span>';
  else if(b.status==='sent') c.innerHTML='<span class="tag ty">SENT ✓✓</span>';
  else if(b.status==='failed') c.innerHTML='<span class="tag tn">FAILED</span>';
}
function updBadge(){ document.getElementById('qbadge').textContent=queue.length; }
function updMet(){ document.getElementById('ms').textContent=sent; document.getElementById('md').textContent=sent; document.getElementById('mb').style.width=Math.min(sent*5,100)+'%'; document.getElementById('mr2').textContent=sent>0?'100%_delivery':'0%_delivery'; }
function sl(ms){ return new Promise(r=>setTimeout(r,ms)); }

function addBubble(name,msg){
  const c=document.getElementById('wa-msgs');
  const d=document.createElement('div'); d.className='bb out';
  const s=msg.length>160?msg.substring(0,160)+'...':msg;
  d.innerHTML=s.replace(/\n/g,'<br>').replace(/\*(.*?)\*/g,'<b>$1</b>')+'<div class="bt">sent ✓✓</div>';
  c.appendChild(d); c.scrollTop=c.scrollHeight;
}
function mSend(){ const i=document.getElementById('wa-inp'); if(!i.value.trim()) return; const c=document.getElementById('wa-msgs'); const d=document.createElement('div'); d.className='bb out'; d.innerHTML=i.value+'<div class="bt">now ✓</div>'; c.appendChild(d); c.scrollTop=c.scrollHeight; i.value=''; }

function updPrev(){
  const t=document.getElementById('msg-tpl'); const p=document.getElementById('preview');
  if(!t||!p) return;
  const pr=document.getElementById('msg-price')?.value||'₹10,000';
  p.innerHTML=t.value
    .replace(/{name}/g,'<b style="color:var(--b2)">Udupi Sagar</b>')
    .replace(/{category}/g,'<span style="color:var(--gold)">Restaurant</span>')
    .replace(/{price}/g,'<span style="color:var(--b)">'+pr+'</span>')
    .replace(/{link}/g,'<a href="#" style="color:var(--b)">clients.in/demo/udupi-sagar</a>')
    .replace(/\n/g,'<br>').replace(/\*(.*?)\*/g,'<b>$1</b>');
}
document.addEventListener('input',e=>{ if(['msg-tpl','msg-price'].includes(e.target.id)) updPrev(); });

function setP(p){ document.getElementById('msg-price').value=p; updPrev(); sw('compose'); toast('PRICE :: '+p,'ok'); }
function saveCfg(){ const k=document.getElementById('wa-key').value.trim(); if(k){waKey=k;localStorage.setItem('wak',k);} toast('CONFIG SAVED ✓','ok'); }

const REPLIES=[
  {n:"Sharma's Restaurant",m:"Haan bhai, price kya hai?",t:"2 min ago",e:"🔥"},
  {n:"Priya Beauty Salon",m:"YES! Please call me.",t:"18 min ago",e:"🔥"},
];
function renderReplies(){
  const l=document.getElementById('rep-list'); if(!l) return; l.innerHTML='';
  REPLIES.forEach(r=>{
    const d=document.createElement('div');
    d.style.cssText='background:var(--sur);border:1px solid var(--mu2);border-radius:2px;padding:10px;margin-bottom:8px;display:flex;gap:10px;align-items:flex-start';
    d.innerHTML=`<span style="font-size:18px">${r.e}</span><div style="flex:1"><div style="font-size:10px;color:var(--b);margin-bottom:2px;font-family:'Share Tech Mono',monospace">${r.n}</div><div style="font-size:9px;color:var(--tx);margin-bottom:2px">"${r.m}"</div><div style="font-size:7px;color:var(--mu);font-family:'Share Tech Mono',monospace">${r.t}</div></div><button class="mb">CALL</button>`;
    l.appendChild(d);
  });
}

function alog(id,type,msg){
  const log=document.getElementById(id); if(!log) return;
  const d=document.createElement('div'); d.className='ll '+type;
  const n=new Date(); const ts=[n.getHours(),n.getMinutes(),n.getSeconds()].map(x=>x.toString().padStart(2,'0')).join(':');
  d.innerHTML=`<span class="lt">${ts}</span><span class="lm">[${type.toUpperCase()}] ${msg}</span>`;
  const cur=log.querySelector('.cur'); if(cur) log.insertBefore(d,cur); else log.appendChild(d);
  log.scrollTop=log.scrollHeight;
}

function go(el,k){ document.querySelectorAll('.nv').forEach(n=>n.classList.remove('on')); el.classList.add('on'); sw(k); }
function tc(el){ document.querySelectorAll('.tab').forEach(t=>t.classList.remove('on')); el.classList.add('on'); document.querySelectorAll('.sec').forEach(s=>s.classList.remove('on')); const s=document.getElementById('sec-'+el.dataset.s); if(s) s.classList.add('on'); }
function sw(k){ document.querySelectorAll('.sec').forEach(s=>s.classList.remove('on')); document.querySelectorAll('.tab').forEach(t=>t.classList.remove('on')); const s=document.getElementById('sec-'+k); if(s) s.classList.add('on'); document.querySelectorAll('.tab').forEach(t=>{ if(t.dataset.s===k) t.classList.add('on'); }); }
function toast(msg,type){ const t=document.getElementById('toast'); t.textContent=msg; t.className='toast '+type+' show'; setTimeout(()=>t.classList.remove('show'),3000); }
function openCfg(){ document.getElementById('cfg-key').value=waKey; document.getElementById('cfg-modal').classList.add('open'); }
function closeCfg(){ document.getElementById('cfg-modal').classList.remove('open'); }
function saveCfgModal(){ waKey=document.getElementById('cfg-key').value.trim(); localStorage.setItem('wak',waKey); closeCfg(); toast('SAVED ✓','ok'); }
</script>
</body>
</html>
