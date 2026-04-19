# Rivals123
A slow paced first person shooter pace 
<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
<title>RIVALS</title>
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@700;800;900&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent;user-select:none;}
html,body{width:100%;height:100%;overflow:hidden;background:#060612;touch-action:none;font-family:'Nunito',sans-serif;}
#gc{position:fixed;inset:0;display:block;width:100%!important;height:100%!important;z-index:0;}
.scr{position:fixed;inset:0;display:flex;flex-direction:column;align-items:center;overflow-y:auto;z-index:20;}
.scr.off{display:none!important;}
#menuScr{background:linear-gradient(168deg,#050d1c 0%,#0d0d22 55%,#050d12 100%);justify-content:center;}
.logoT{font-size:clamp(60px,16vw,92px);font-weight:900;color:#fff;letter-spacing:8px;text-shadow:0 0 30px #00c8ff,0 0 60px rgba(0,200,255,.3);}
.logoS{font-size:11px;font-weight:800;color:rgba(0,200,255,.55);letter-spacing:5px;margin-bottom:48px;margin-top:4px;}
.mBtn{background:linear-gradient(135deg,#00c8ff,#0070aa);color:#fff;font-family:'Nunito',sans-serif;font-size:18px;font-weight:900;letter-spacing:3px;border:none;border-radius:12px;padding:16px 54px;cursor:pointer;box-shadow:0 6px 24px rgba(0,200,255,.3);touch-action:manipulation;}
.mBtn:active{transform:scale(.97);}
.ver{margin-top:14px;font-size:11px;color:rgba(255,255,255,.2);text-align:center;padding:0 20px;}
#mapScr,#wepScr{background:#08091a;padding:24px 0 110px;}
.scrT1{font-size:10px;font-weight:800;color:rgba(0,200,255,.6);letter-spacing:4px;margin-bottom:4px;}
.scrT2{font-size:22px;font-weight:900;color:#fff;margin-bottom:20px;}
.mapGrid{display:grid;grid-template-columns:1fr 1fr;gap:10px;padding:0 14px;width:100%;max-width:420px;}
.mapCard{background:rgba(255,255,255,.04);border:2px solid rgba(255,255,255,.07);border-radius:13px;padding:14px 12px;cursor:pointer;touch-action:manipulation;}
.mapCard.sel{border-color:#00c8ff;background:rgba(0,200,255,.09);}
.mapCard:active{transform:scale(.97);}
.mapName{font-size:14px;font-weight:900;color:#fff;margin-bottom:3px;}
.mapSz{font-size:9px;font-weight:800;letter-spacing:1.5px;padding:2px 7px;border-radius:4px;display:inline-block;margin-bottom:5px;}
.sm{background:rgba(0,200,100,.2);color:#44ff99;}.big{background:rgba(255,160,0,.2);color:#ffaa44;}.med{background:rgba(100,100,255,.2);color:#8899ff;}
.mapDesc{font-size:10px;color:rgba(255,255,255,.32);font-weight:700;line-height:1.4;}
.fullW{grid-column:1/-1;}
.wCnt{font-size:11px;font-weight:800;color:rgba(255,255,255,.4);margin:8px 0 4px;letter-spacing:1px;}
.wGrid{display:grid;grid-template-columns:repeat(3,1fr);gap:7px;padding:0 12px;width:100%;max-width:420px;}
.wCard{background:rgba(255,255,255,.04);border:2px solid rgba(255,255,255,.07);border-radius:10px;padding:10px 6px;cursor:pointer;text-align:center;touch-action:manipulation;}
.wCard.sel{border-color:#ffd700;background:rgba(255,215,0,.09);}
.wCard.dis{opacity:.35;pointer-events:none;}
.wCard:active{transform:scale(.96);}
.wIco{font-size:22px;margin-bottom:3px;}
.wNm{font-size:10px;font-weight:800;color:#fff;line-height:1.2;}
.wCat{font-size:8px;font-weight:700;margin-top:3px;padding:1px 5px;border-radius:3px;display:inline-block;}
.cat-gun{background:rgba(100,150,255,.25);color:#99bbff;}
.cat-melee{background:rgba(255,80,80,.25);color:#ffaaaa;}
.cat-flame{background:rgba(255,150,0,.25);color:#ffcc66;}
.cat-throw{background:rgba(255,100,80,.25);color:#ff9988;}
.cat-place{background:rgba(150,50,255,.25);color:#cc88ff;}
.sBar{position:fixed;bottom:0;left:0;right:0;padding:12px 14px 22px;background:linear-gradient(to top,rgba(6,6,22,.98),transparent);display:flex;justify-content:center;gap:10px;z-index:25;}
.sBtn{background:linear-gradient(135deg,#00c8ff,#0070aa);color:#fff;font-family:'Nunito',sans-serif;font-size:15px;font-weight:900;letter-spacing:2px;border:none;border-radius:10px;padding:14px 38px;cursor:pointer;touch-action:manipulation;}
.sBtn:disabled{opacity:.3;pointer-events:none;}
.sBtn.sec{background:rgba(255,255,255,.08);color:rgba(255,255,255,.55);}
#roScr{background:rgba(0,0,0,.93);justify-content:center;}
.roTitle{font-size:clamp(38px,10vw,64px);font-weight:900;letter-spacing:5px;margin-bottom:6px;}
.roTitle.win{color:#00ff88;text-shadow:0 0 28px rgba(0,255,136,.6);}
.roTitle.lose{color:#ff4466;text-shadow:0 0 28px rgba(255,68,102,.6);}
.roScore{font-size:46px;font-weight:900;color:#fff;margin-bottom:16px;}
.roDmg{font-size:13px;font-weight:800;color:rgba(255,215,0,.7);margin-bottom:24px;}
.btnRow{display:flex;gap:12px;}

/* HUD */
#hud{position:fixed;inset:0;pointer-events:none;z-index:10;display:none;}
#scoreBadge{position:absolute;top:14px;left:50%;transform:translateX(-50%);background:rgba(0,0,0,.58);border:1px solid rgba(255,255,255,.1);border-radius:10px;padding:6px 18px;text-align:center;}
#scoreBadge .sc{font-size:24px;font-weight:900;color:#fff;letter-spacing:2px;line-height:1;}
#scoreBadge .slbl{font-size:8px;font-weight:800;color:rgba(255,255,255,.35);letter-spacing:2px;}
#xhair{position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);width:20px;height:20px;pointer-events:none;}
#xhair::before,#xhair::after{content:’’;position:absolute;background:rgba(255,255,255,.88);border-radius:1px;}
#xhair::before{width:2px;height:100%;left:50%;transform:translateX(-50%);}
#xhair::after{height:2px;width:100%;top:50%;transform:translateY(-50%);}
/* bottom-left stack */
#blStack{position:absolute;bottom:calc(26% + 10px);left:14px;display:flex;flex-direction:column;gap:6px;}
#hpWrap .lbl,#slideWrap .lbl,#dmgWrap .lbl{font-size:9px;font-weight:800;color:rgba(255,255,255,.4);letter-spacing:1.5px;}
#hpBg,#slideBg{height:10px;background:rgba(255,255,255,.1);border-radius:5px;overflow:hidden;margin-top:2px;border:1px solid rgba(255,255,255,.08);}
#hpBg{width:110px;}#slideBg{width:110px;}
#hpBar{height:100%;background:linear-gradient(90deg,#ff4466,#ff7090);transition:width .15s;}
#slideFill{height:100%;width:100%;background:linear-gradient(90deg,#00c8ff,#00ffcc);transition:width .1s;}
#dmgWrap .val{font-size:20px;font-weight:900;color:#ffd700;line-height:1.1;}
/* bottom-right */
#wInfo{position:absolute;bottom:calc(26% + 10px);right:14px;text-align:right;}
#wInfo .wn{font-size:13px;font-weight:900;color:#fff;}
#wInfo .wa{font-size:11px;font-weight:800;color:rgba(255,255,255,.5);margin-top:1px;}
#wInfo .rl{font-size:10px;font-weight:800;color:#00c8ff;margin-top:2px;opacity:0;transition:.2s;}
/* weapon slots center-bottom */
#wSlots{position:absolute;bottom:calc(26% + 70px);left:50%;transform:translateX(-50%);display:flex;gap:6px;pointer-events:all;}
.ws{width:46px;height:46px;border-radius:9px;border:2px solid rgba(255,255,255,.15);background:rgba(0,0,0,.5);display:flex;align-items:center;justify-content:center;font-size:20px;touch-action:manipulation;cursor:pointer;}
.ws.cur{border-color:#ffd700;background:rgba(255,215,0,.14);}
.ws.mt{opacity:.3;}
/* special hint */
#specHint{position:absolute;bottom:calc(26% + 54px);left:50%;transform:translateX(-50%);font-size:10px;font-weight:800;color:rgba(255,215,0,.65);letter-spacing:.5px;pointer-events:none;white-space:nowrap;text-align:center;}
/* kill feed */
#kf{position:absolute;top:68px;left:50%;transform:translateX(-50%);display:flex;flex-direction:column;align-items:center;gap:3px;}
.kfe{font-size:10px;font-weight:800;border-radius:5px;padding:3px 10px;animation:kfA 2.5s forwards;white-space:nowrap;}
.kfe.pk{background:rgba(0,255,100,.1);color:#44ff88;}
.kfe.ak{background:rgba(255,50,80,.1);color:#ff6688;}
@keyframes kfA{70%{opacity:1}100%{opacity:0}}
/* floating damage numbers */
.dn{position:fixed;font-family:‘Nunito’,sans-serif;font-weight:900;pointer-events:none;z-index:30;animation:dnA .9s ease-out forwards;}
@keyframes dnA{0%{opacity:1;transform:translateY(0)scale(1)}100%{opacity:0;transform:translateY(-62px)scale(.65)}}
/* overlays */
#dmgV{position:absolute;inset:0;background:radial-gradient(ellipse at center,transparent 38%,rgba(255,0,0,.62) 100%);opacity:0;pointer-events:none;transition:opacity .12s;}
#flashV{position:absolute;inset:0;background:rgba(255,255,255,.96);opacity:0;pointer-events:none;transition:opacity .4s;}
#killV{position:absolute;inset:0;background:rgba(0,255,100,.18);opacity:0;pointer-events:none;transition:opacity .08s;}
#waveMsg{position:absolute;top:36%;left:50%;transform:translateX(-50%);font-size:clamp(22px,7vw,42px);font-weight:900;color:#fff;text-shadow:0 0 26px rgba(255,215,0,.85);opacity:0;transition:.35s;white-space:nowrap;pointer-events:none;}
#slideMsg{position:absolute;top:44%;left:50%;transform:translateX(-50%);font-size:16px;font-weight:900;color:#00ffcc;opacity:0;transition:.2s;letter-spacing:3px;pointer-events:none;}
#spawnV{position:absolute;inset:0;background:rgba(0,0,0,.72);display:none;flex-direction:column;align-items:center;justify-content:center;gap:6px;}
#spawnV .sp1{font-size:15px;font-weight:900;color:rgba(255,255,255,.5);letter-spacing:3px;}
#spawnV .sp2{font-size:72px;font-weight:900;color:#fff;line-height:1;}
#spawnV .sp3{font-size:13px;font-weight:800;color:rgba(255,215,0,.7);letter-spacing:2px;margin-top:6px;}
/* mobile controls */
#ctrlLayer{position:absolute;bottom:0;left:0;right:0;height:26%;pointer-events:none;border-top:1px solid rgba(255,255,255,.05);}
#moveLabel{position:absolute;bottom:7px;left:20px;font-size:8px;font-weight:800;color:rgba(255,255,255,.15);letter-spacing:2px;}
#lookLabel{position:absolute;bottom:7px;right:20px;font-size:8px;font-weight:800;color:rgba(255,255,255,.15);letter-spacing:2px;}
#jBase{position:fixed;width:90px;height:90px;border-radius:50%;border:2px solid rgba(255,255,255,.1);background:rgba(255,255,255,.03);pointer-events:none;display:none;transform:translate(-50%,-50%);z-index:11;}
#jKnob{position:fixed;width:54px;height:54px;border-radius:50%;background:rgba(255,255,255,.22);border:2px solid rgba(255,255,255,.4);pointer-events:none;display:none;transform:translate(-50%,-50%);z-index:12;}
#shootBtn{position:absolute;bottom:18px;right:18px;width:72px;height:72px;border-radius:50%;background:rgba(255,50,80,.5);border:2px solid rgba(255,110,130,.7);display:none;align-items:center;justify-content:center;font-size:28px;pointer-events:all;touch-action:none;box-shadow:0 0 24px rgba(255,50,80,.35);z-index:11;}
#relBtn{position:absolute;bottom:26px;right:104px;width:52px;height:52px;border-radius:50%;background:rgba(0,200,255,.25);border:2px solid rgba(0,200,255,.45);display:none;align-items:center;justify-content:center;font-size:12px;font-weight:900;color:#fff;pointer-events:all;touch-action:none;z-index:11;}
</style>

</head>
<body>
<canvas id="gc"></canvas>

<!-- HUD -->

<div id="hud">
  <div id="scoreBadge"><div class="slbl">SCORE</div><div class="sc"><span id="pS">0</span> : <span id="aS">0</span></div></div>
  <div id="xhair"></div>
  <div id="dmgV"></div><div id="flashV"></div><div id="killV"></div>
  <div id="waveMsg"></div><div id="slideMsg">SLIDING</div>
  <div id="kf"></div>
  <div id="blStack">
    <div id="hpWrap"><div class="lbl">HP</div><div id="hpBg"><div id="hpBar" style="width:100%"></div></div></div>
    <div id="slideWrap"><div class="lbl">SLIDE CD</div><div id="slideBg"><div id="slideFill"></div></div></div>
    <div id="dmgWrap"><div class="lbl">DAMAGE DEALT</div><div class="val" id="dmgVal">0</div></div>
  </div>
  <div id="wInfo"><div class="wn" id="wNm">—</div><div class="wa" id="wAm"></div><div class="rl" id="rLbl">RELOADING…</div></div>
  <div id="wSlots"></div>
  <div id="specHint"></div>
  <div id="ctrlLayer">
    <div id="moveLabel">◀ MOVE</div>
    <div id="lookLabel">LOOK ▶</div>
  </div>
  <div id="jBase"></div><div id="jKnob"></div>
  <div id="shootBtn">🔫</div>
  <div id="relBtn">R</div>
  <div id="spawnV"><div class="sp1" id="spTitle">ROUND RESET</div><div class="sp2" id="spCnt">5</div><div class="sp3" id="spSub"></div></div>
</div>

<!-- Menu -->

<div class="scr" id="menuScr">
  <div class="logoT">RIVALS</div>
  <div class="logoS">FIRST PERSON · 1v1</div>
  <button class="mBtn" id="menuBtn">▶ PLAY</button>
  <div class="ver">First to 5 kills wins · Shift/double-tap left = Slide · E/double-tap right = Special</div>
</div>

<!-- Map Select -->

<div class="scr off" id="mapScr">
  <div style="padding:26px 0 0;text-align:center;"><div class="scrT1">STEP 1 / 2</div><div class="scrT2">Choose Map</div></div>
  <div class="mapGrid" id="mapGrid"></div>
  <div class="sBar"><button class="sBtn" id="mapNext" disabled>Next →</button></div>
</div>

<!-- Weapon Select -->

<div class="scr off" id="wepScr">
  <div style="padding:26px 0 0;text-align:center;"><div class="scrT1">STEP 2 / 2</div><div class="scrT2">Your Loadout</div></div>
  <div class="wCnt" id="wCnt">Pick up to 4 weapons (0 / 4)</div>
  <div class="wGrid" id="wGrid"></div>
  <div class="sBar">
    <button class="sBtn sec" id="wBack">← Back</button>
    <button class="sBtn" id="wReady" disabled>Fight! 🔫</button>
  </div>
</div>

<!-- Round Over -->

<div class="scr off" id="roScr">
  <div class="roTitle" id="roT">YOU WIN!</div>
  <div class="roScore" id="roS">5 – 2</div>
  <div class="roDmg" id="roDmg">Total damage dealt: 0</div>
  <div class="btnRow">
    <button class="mBtn" id="roMenu" style="font-size:15px;padding:14px 32px;">Menu</button>
    <button class="mBtn" id="roAgain" style="font-size:15px;padding:14px 32px;">▶ Again</button>
  </div>
</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>

<script>
'use strict';
const IS_MOB='ontouchstart' in window;
const TILE=2.4,EYE_H=1.62,P_RAD=0.36,WIN_K=5;

// ══════════════════════════════════════════
// WEAPONS
// ══════════════════════════════════════════
const WD={
  pistol:    {n:'Pistol',          i:'[gun]',cat:'gun',  c:0xaaaaaa,am:12,rate:.22,rel:1.4,dmg:15,spd:22,spr:.03, auto:0,p:1, special:'burst',    sDesc:'[E] Burst Fire (×3 rapid)'},
  revolver:  {n:'Revolver',        i:'[gun]',cat:'gun',  c:0x996633,am:6, rate:.65,rel:2.4,dmg:38,spd:28,spr:.012,auto:0,p:1, special:'fan',      sDesc:'[E] Fan the Hammer'},
  ar:        {n:'AR',              i:'[gun]',cat:'gun',  c:0x335533,am:30,rate:.10,rel:1.9,dmg:12,spd:24,spr:.045,auto:1,p:1, special:'ugnade',   sDesc:'[E] Underbarrel Grenade'},
  shotgun:   {n:'Shotgun',         i:'[gun]',cat:'gun',  c:0x994422,am:8, rate:.75,rel:2.0,dmg:18,spd:17,spr:.14, auto:0,p:6, special:'blast',    sDesc:'[E] Point-Blank Blast (×2)'},
  sniper:    {n:'Sniper',          i:'[scope]',cat:'gun',  c:0x334455,am:5, rate:1.5,rel:2.2,dmg:88,spd:70,spr:.004,auto:0,p:1, special:'mark',     sDesc:'[E] Mark Target (+50% dmg)'},
  flameth:   {n:'Flamethrower',    i:'[flame]',cat:'flame',c:0xff5500,am:80,rate:.06,rel:2.0,dmg:7, rng:7,  auto:1,          special:'spin',     sDesc:'[E] Fire Spin 360deg'},
  energygun: {n:'Energy Gun',      i:'[zap]',cat:'gun',  c:0x0088ff,am:999,rate:.12,rel:0, dmg:14,spd:35,spr:.025,auto:1,p:1,heat:1, special:'beam',sDesc:'[E] Overcharge Beam'},
  flaregun:  {n:'Flare Gun',       i:'[flare]',cat:'gun',  c:0xff6600,am:4, rate:1.3,rel:2.0,dmg:42,spd:11,spr:.025,auto:0,p:1,burn:1, special:'signal',sDesc:'[E] Signal Flare (area)'},
  flashbang: {n:'Flashbang',       i:'[flash]',cat:'throw',c:0xffffaa,am:2, rate:.5, rel:0,  dmg:0,  flash:1,                 special:'lthrow',   sDesc:'[E] Long Throw'},
  grenade:   {n:'Grenade',         i:'[bomb]',cat:'throw',c:0x44aa44,am:3, rate:.5, rel:0,  dmg:75, rad:5.5,                 special:'cook',     sDesc:'[E] Cook Grenade (short fuse)'},
  stickybomb:{n:'Sticky Bomb',     i:'[sticky]',cat:'throw',c:0xff8800,am:3, rate:.8, rel:0,  dmg:88, rad:4.5,sticky:1,        special:'remote',   sDesc:'[E] Remote Detonate'},
  tripmine:  {n:'Subspace Tripmine',i:'[mine]',cat:'place',c:0x9900ff,am:2,rate:.5, rel:0,  dmg:95, rad:3.5,                 special:'multi',    sDesc:'[E] Deploy 3 Mines'},
  knife:     {n:'Knife',           i:'[knife]',cat:'melee',c:0xcccccc,am:999,rate:.32,rel:0, dmg:45, rng:2.4,                 special:'backstab', sDesc:'[E] Backstab (160 dmg from behind!)'},
};
const WK=Object.keys(WD);

// ══════════════════════════════════════════
// MAPS
// ══════════════════════════════════════════
const MAPS=[
  // ── 1. ARENA ─────────────────────────────────────
  // Gladiator pit: sandy floor, stone columns, symmetrical open pit
  {name:'Arena',sz:'sm',desc:'Gladiator pit — symmetric stone columns, nowhere to run.',
   fC:0xD4AA55,wC:0x9B7340,bg:0x7EC8E3,
   rows:[
    '################',
    '#..............#',
    '#.##........##.#',
    '#..............#',
    '#....######....#',
    '#....#....#....#',
    '#....######....#',
    '#..............#',
    '#.##........##.#',
    '#..............#',
    '################',
   ],pS:{r:1,c:8},aS:{r:9,c:7}},

  // ── 2. CROSSROADS ────────────────────────────────
  // Real city intersection: 4 corner buildings, 2 wide crossing roads
  {name:'Crossroads',sz:'big',desc:'Four-way street crossing — control the center intersection.',
   fC:0x4A4A4A,wC:0x2A2A2A,bg:0xB8C8D0,
   rows:[
    '####################',
    '########....########',
    '########....########',
    '########....########',
    '########....########',
    '########....########',
    '.....................',
    '.....................',
    '.....................',
    '.....................',
    '########....########',
    '########....########',
    '########....########',
    '########....########',
    '########....########',
    '####################',
   ],pS:{r:7,c:2},aS:{r:7,c:17}},

  // ── 3. CONSTRUCTION ──────────────────────────────
  // Half-built structure: scaffold walls, exposed rooms, material piles
  {name:'Construction',sz:'sm',desc:'Half-built site — exposed rooms, scaffolding, tight corners.',
   fC:0x7A6550,wC:0x6A8040,bg:0x99AACC,
   rows:[
    '##################',
    '#................#',
    '#.####..##.......#',
    '#....#..##.......#',
    '#.####..##...###.#',
    '#.......##.......#',
    '#.......##...###.#',
    '#.######.........#',
    '#................#',
    '#..###...........#',
    '#..#.............#',
    '#..###...###.....#',
    '#................#',
    '#..####..####....#',
    '#................#',
    '##################',
   ],pS:{r:1,c:9},aS:{r:14,c:9}},

  // ── 4. TOWN ──────────────────────────────────────
  // City district: proper grid streets, building blocks between them
  {name:'Town',sz:'big',desc:'City grid — horizontal and vertical streets between buildings.',
   fC:0xAA9977,wC:0xAA4433,bg:0xFFCC88,
   rows:[
    '######################',
    '#....................#',
    '#....................#',
    '#..####..####..####..#',
    '#..####..####..####..#',
    '#..####..####..####..#',
    '#....................#',
    '#....................#',
    '#..####..####..####..#',
    '#..####..####..####..#',
    '#..####..####..####..#',
    '#....................#',
    '#....................#',
    '#..####..####..####..#',
    '#..####..####..####..#',
    '#..####..####..####..#',
    '#....................#',
    '#....................#',
    '#....................#',
    '######################',
   ],pS:{r:2,c:11},aS:{r:17,c:11}},

  // ── 5. FACTORY ───────────────────────────────────
  // Industrial plant: offset rows of machines, maintenance corridors
  {name:'Factory',sz:'med',desc:'Industrial plant — rows of machinery with tight maintenance corridors.',
   fC:0x555555,wC:0x885533,bg:0xBBAA88,
   rows:[
    '####################',
    '#..................#',
    '#.###.###.###.###..#',
    '#.###.###.###.###..#',
    '#..................#',
    '#..###.###.###.###.#',
    '#..###.###.###.###.#',
    '#..................#',
    '#.###.###.###.###..#',
    '#.###.###.###.###..#',
    '#..................#',
    '#..###.###.###.###.#',
    '#..###.###.###.###.#',
    '#..................#',
    '#.##.##...##.##....#',
    '#..................#',
    '####################',
   ],pS:{r:1,c:10},aS:{r:15,c:9}},

  // ── 6. ROOFTOP ───────────────────────────────────
  // Night rooftop: AC housing units for cover, open edges
  {name:'Rooftop',sz:'sm',desc:'Nighttime rooftop — AC units for cover, exposed edges.',
   fC:0x444455,wC:0x334466,bg:0x080818,
   rows:[
    '##############',
    '#............#',
    '#.##......##.#',
    '#............#',
    '#....####....#',
    '#....#..#....#',
    '#....####....#',
    '#............#',
    '#....####....#',
    '#....#..#....#',
    '#....####....#',
    '#............#',
    '#.##......##.#',
    '##############',
   ],pS:{r:1,c:7},aS:{r:12,c:6}},

  // ── 7. WAREHOUSE ─────────────────────────────────
  // Storage facility: shelf rows with wide aisles between them
  {name:'Warehouse',sz:'big',desc:'Storage facility — long shelf aisles, lots of cover.',
   fC:0x7A5530,wC:0x556677,bg:0x221810,
   rows:[
    '####################',
    '#..................#',
    '#.##.##.##.##.##...#',
    '#.##.##.##.##.##...#',
    '#..................#',
    '#.##.##.##.##.##...#',
    '#.##.##.##.##.##...#',
    '#..................#',
    '#.##.##.##.##.##...#',
    '#.##.##.##.##.##...#',
    '#..................#',
    '#.##.##.##.##.##...#',
    '#.##.##.##.##.##...#',
    '#..................#',
    '#.##.##.##.##.##...#',
    '#.##.##.##.##.##...#',
    '#..................#',
    '####################',
   ],pS:{r:1,c:10},aS:{r:16,c:10}},

  // ── 8. SHIPYARD ──────────────────────────────────
  // Port: stacked shipping containers in offset rows, corridors between
  {name:'Shipyard',sz:'big',desc:'Container port — offset container stacks, sunset silhouettes.',
   fC:0x556677,wC:0x334455,bg:0xFF7744,
   rows:[
    '######################',
    '#....................#',
    '#.###.###.###.###....#',
    '#.###.###.###.###....#',
    '#.###.###.###.###....#',
    '#....................#',
    '#....###.###.###.###.#',
    '#....###.###.###.###.#',
    '#....###.###.###.###.#',
    '#....................#',
    '#.##...........##....#',
    '#....................#',
    '#.###.###.###.###....#',
    '#.###.###.###.###....#',
    '#.###.###.###.###....#',
    '#....................#',
    '#....###.###.###.###.#',
    '######################',
   ],pS:{r:1,c:11},aS:{r:16,c:10}},

  // ── 9. DESERT FORT ───────────────────────────────
  // Ancient ruins: crumbling fort walls, sandy courtyard, broken battlements
  {name:'Desert Fort',sz:'sm',desc:'Ancient fort ruins — crumbling walls, sandy courtyard.',
   fC:0xE8C870,wC:0xCC9944,bg:0xFF9933,
   rows:[
    '################',
    '#..............#',
    '#.##.......##..#',
    '#..............#',
    '#....######....#',
    '#....#....#....#',
    '#..#.#....#.#..#',
    '#....######....#',
    '#..............#',
    '##..........####',
    '#..............#',
    '#.####......####',
    '#..............#',
    '################',
   ],pS:{r:1,c:8},aS:{r:12,c:8}},
];

// ══════════════════════════════════════════
// THREE.JS SETUP
// ══════════════════════════════════════════
const cv=document.getElementById('gc');
const renderer=new THREE.WebGLRenderer({canvas:cv,antialias:!IS_MOB});
renderer.setPixelRatio(IS_MOB?Math.min(window.devicePixelRatio,1.5):Math.min(window.devicePixelRatio,2));
renderer.shadowMap.enabled=!IS_MOB;renderer.shadowMap.type=THREE.PCFSoftShadowMap;
const scene=new THREE.Scene();
const camera=new THREE.PerspectiveCamera(80,1,.08,120);camera.rotation.order='YXZ';
function resz(){const W=window.innerWidth,H=window.innerHeight;renderer.setSize(W,H);camera.aspect=W/H;camera.updateProjectionMatrix();}
window.addEventListener('resize',resz);resz();
scene.add(new THREE.AmbientLight(0xffffff,.65));
const sun=new THREE.DirectionalLight(0xfffbee,1.0);sun.position.set(18,32,14);
sun.castShadow=!IS_MOB;if(sun.shadow){sun.shadow.mapSize.set(512,512);Object.assign(sun.shadow.camera,{left:-40,right:40,top:40,bottom:-40,near:1,far:120});}
scene.add(sun);

// ══════════════════════════════════════════
// CHARACTER  (sphere head, blocky body, face details, no ears)
// ══════════════════════════════════════════
function mkChar(bC,hC){
  const G=new THREE.Group();
  const M=c=>new THREE.MeshLambertMaterial({color:c});
  const mk=(geo,mat,x,y,z,rx,ry,rz)=>{
    const ms=new THREE.Mesh(geo,mat);
    ms.position.set(x,y,z);
    if(rx)ms.rotation.x=rx; if(ry)ms.rotation.y=ry; if(rz)ms.rotation.z=rz;
    ms.castShadow=true; G.add(ms); return ms;
  };

  const MB=M(bC);
  const MH=M(hC);
  const MF=M(0xF5C18A);
  const ME=M(0x111122);
  const MP=M(new THREE.Color(bC).multiplyScalar(.52));
  const MS=M(0x222222);
  const MN=M(0x888899);
  const MW2=M(0xffffff);
  const MLip=M(0xcc7766);
  const MBr=M(new THREE.Color(hC).multiplyScalar(0.65));
  const MNs=M(0xE0A07A);
  const MBlush=M(0xffaaaa); MBlush.transparent=true; MBlush.opacity=.28;

  // ── SHOES (blocky) ──
  mk(new THREE.BoxGeometry(.28,.13,.36),MS,-.19,.065, .03);
  mk(new THREE.BoxGeometry(.28,.13,.36),MS, .19,.065, .03);

  // ── LEGS (blocky) ──
  G._ll=mk(new THREE.BoxGeometry(.26,.72,.26),MP,-.19,.52,0);
  G._rl=mk(new THREE.BoxGeometry(.26,.72,.26),MP, .19,.52,0);

  // ── TORSO (blocky) ──
  mk(new THREE.BoxGeometry(.72,.88,.44),MB,0,1.3,0);

  // Belt strip
  mk(new THREE.BoxGeometry(.74,.07,.46),MS,0,.88,0);

  // Neck (small block)
  mk(new THREE.BoxGeometry(.3,.2,.28),MF,0,1.82,0);

  // ── ARMS (blocky) ──
  G._la=mk(new THREE.BoxGeometry(.24,.78,.24),MB,-.5,1.28,0);
  G._ra=mk(new THREE.BoxGeometry(.24,.78,.24),MB, .5,1.28,0);

  // ── HANDS (small blocks) ──
  mk(new THREE.BoxGeometry(.22,.2,.22),MF,-.5,.8,0);
  mk(new THREE.BoxGeometry(.22,.2,.22),MF, .5,.8,0);

  // ── HEAD  (smooth sphere) ──
  const headG=new THREE.SphereGeometry(.3,16,12);
  mk(headG,MF,0,2.15,0);

  // ── FACE — on the sphere ──

  // Eye whites
  mk(new THREE.SphereGeometry(.075,8,8),MW2,-.112,2.21,.268);
  mk(new THREE.SphereGeometry(.075,8,8),MW2, .112,2.21,.268);

  // Pupils
  mk(new THREE.SphereGeometry(.046,8,8),ME,-.112,2.21,.286);
  mk(new THREE.SphereGeometry(.046,8,8),ME, .112,2.21,.286);

  // Eye shine
  mk(new THREE.SphereGeometry(.016,6,6),MW2,-.096,2.234,.297);
  mk(new THREE.SphereGeometry(.016,6,6),MW2, .128,2.234,.297);

  // Eyebrows (flat boxes angled slightly)
  mk(new THREE.BoxGeometry(.108,.026,.038),MBr,-.112,2.3,.264,-.1,0,-.07);
  mk(new THREE.BoxGeometry(.108,.026,.038),MBr, .112,2.3,.264,-.1,0, .07);

  // Nose bump
  mk(new THREE.SphereGeometry(.036,6,6),MNs,0,2.13,.287);

  // Mouth line
  mk(new THREE.BoxGeometry(.092,.013,.018),ME,  0,2.062,.281);
  // Upper lip
  mk(new THREE.BoxGeometry(.078,.02,.025),MLip, 0,2.077,.278);
  // Lower lip
  mk(new THREE.BoxGeometry(.068,.018,.022),MLip,0,2.047,.276);

  // Cheek blush
  mk(new THREE.SphereGeometry(.052,6,6),MBlush,-.218,2.1,.224);
  mk(new THREE.SphereGeometry(.052,6,6),MBlush, .218,2.1,.224);

  // ── HAIR (blocky pieces on sphere head) ──
  // Top cap (half-sphere for smoothness at top, then boxes)
  mk(new THREE.SphereGeometry(.315,12,8,0,Math.PI*2,0,Math.PI*.48),MH,0,2.19,0);
  // Front bangs block
  mk(new THREE.BoxGeometry(.52,.1,.16),MH,0,2.46, .18,-.2,0,0);
  // Left side
  mk(new THREE.BoxGeometry(.1,.36,.28),MH,-.295,2.1,.02);
  // Right side
  mk(new THREE.BoxGeometry(.1,.36,.28),MH, .295,2.1,.02);
  // Back
  mk(new THREE.BoxGeometry(.5,.28,.1),MH,0,2.1,-.266,.08,0,0);

  // ── GUN (blocky, right hand) ──
  mk(new THREE.BoxGeometry(.09,.22,.1),MN, .5,.8,.06);
  mk(new THREE.BoxGeometry(.07,.07,.3),MN, .5,.88,.2);

  return G;
}

// ══════════════════════════════════════════
// MAP BUILD
// ══════════════════════════════════════════
const mapGrp=new THREE.Group();scene.add(mapGrp);
let walls=[];
function buildMap(md){
  while(mapGrp.children.length)mapGrp.remove(mapGrp.children[0]);
  walls=[];
  scene.background=new THREE.Color(md.bg);scene.fog=new THREE.FogExp2(md.bg,.042);
  const rows=md.rows,R=rows.length;
  const fG=new THREE.PlaneGeometry(TILE,TILE);
  const fA=new THREE.MeshLambertMaterial({color:md.fC});
  const fB=new THREE.MeshLambertMaterial({color:new THREE.Color(md.fC).multiplyScalar(.86)});
  const wG=new THREE.BoxGeometry(TILE,3,TILE);
  const wM=new THREE.MeshLambertMaterial({color:md.wC});
  const cM=new THREE.MeshLambertMaterial({color:new THREE.Color(md.wC).multiplyScalar(1.22)});
  const cG=new THREE.BoxGeometry(TILE-.06,.18,TILE-.06);
  for(let r=0;r<R;r++)for(let c=0;c<(rows[r]||'').length;c++){
    const ch=rows[r][c],wx=c*TILE+TILE/2,wz=r*TILE+TILE/2;
    if(ch==='#'){
      const wm=new THREE.Mesh(wG,wM);wm.position.set(wx,1.5,wz);wm.castShadow=wm.receiveShadow=true;mapGrp.add(wm);
      const cm=new THREE.Mesh(cG,cM);cm.position.set(wx,3.09,wz);mapGrp.add(cm);
      walls.push({x:wx-TILE/2,z:wz-TILE/2,w:TILE,d:TILE});
    }else{
      const fm=new THREE.Mesh(fG,(r+c)%2?fA:fB);fm.rotation.x=-Math.PI/2;fm.position.set(wx,0,wz);fm.receiveShadow=true;mapGrp.add(fm);
    }
  }
}
function wallHit(x,z,r){for(const w of walls){const nx=Math.max(w.x,Math.min(x,w.x+w.w)),nz=Math.max(w.z,Math.min(z,w.z+w.d));if(Math.hypot(x-nx,z-nz)<r)return true;}return false;}
function mv(x,z,dx,dz,r){let nx=x+dx;if(!wallHit(nx,z,r))x=nx;let nz=z+dz;if(!wallHit(x,nz,r))z=nz;return{x,z};}
function hasLOS(x1,z1,x2,z2){const dx=x2-x1,dz=z2-z1,d=Math.hypot(dx,dz);if(d<.1)return true;const s=Math.ceil(d/.4)+1;for(let i=1;i<s;i++){if(wallHit(x1+dx*i/s,z1+dz*i/s,.18))return false;}return true;}
function spawnPos(sp,rows){for(let dr=-2;dr<=2;dr++)for(let dc=-2;dc<=2;dc++){const rr=sp.r+dr,cc=sp.c+dc;if(rr>=0&&cc>=0&&rr<rows.length&&cc<(rows[rr]||'').length&&rows[rr][cc]==='.')return{x:(cc+.5)*TILE,z:(rr+.5)*TILE};}return{x:(sp.c+.5)*TILE,z:(sp.r+.5)*TILE};}

// ══════════════════════════════════════════
// GAME STATE
// ══════════════════════════════════════════
let gst='menu';
let selMap2=0,pWeps2=[],aiWepKeys=[];
let pScore=0,aScore=0,totalDmg=0;
let P=null,AI=null;
let projs=[],throwns=[],mines=[],flamePs=[],burns=[];
let lastT=0,mouseHeld=false;
let aiMarked=false,aiMarkT=0;

// ── Camera animation state ──
const CAM={
  bobT:0,           // walk bob timer
  kickY:0,          // vertical recoil (pitch kick)
  kickDecay:0,      // how much kick remains
  tiltZ:0,          // slide camera roll
  shakeX:0,shakeY:0,// damage shake
  shakeT:0,
  killFlash:0,      // green kill flash
};

function mkWS(k){const d=WD[k];return{key:k,d,am:d.am,shootT:0,rel:false,relT:0,heat:0,ov:false,specCd:0};}

// ══════════════════════════════════════════
// DAMAGE NUMBERS
// ══════════════════════════════════════════
function showDN(dmg,crit,special){
  const el=document.createElement('div');
  el.className='dn';
  const W=window.innerWidth,H=window.innerHeight;
  el.style.left=(W*.5+(Math.random()-.5)*70)+'px';
  el.style.top=(H*.5-40+(Math.random()-.5)*30)+'px';
  el.style.fontSize=(crit||special)?'28px':'17px';
  el.style.color=special?'#00ffff':crit?'#ff4466':'#ffd700';
  el.style.textShadow=`0 2px 8px ${special?'#00ffff88':crit?'#ff446688':'#ffaa0088'}`;
  el.textContent=(special?'* ':crit?'!! ':'')+Math.round(dmg);
  document.body.appendChild(el);
  setTimeout(()=>el.remove(),950);
  totalDmg+=Math.round(dmg);
  document.getElementById('dmgVal').textContent=totalDmg;
}

// ══════════════════════════════════════════
// INIT
// ══════════════════════════════════════════
function initP(wkeys){
  if(P?.mesh)scene.remove(P.mesh);
  const sp=spawnPos(MAPS[selMap2].pS,MAPS[selMap2].rows);
  P={x:sp.x,z:sp.z,yaw:0,pitch:0,hp:100,maxHp:100,radius:P_RAD,
     weps:wkeys.map(mkWS),wi:0,alive:true,inv:true,invT:3,walkT:0,
     sliding:false,slideT:0,slideDx:0,slideDz:0,slideCd:0,mesh:null};
  refreshWHUD();refreshHP();
}
function initAI(wkeys){
  if(AI?.mesh)scene.remove(AI.mesh);
  const sp=spawnPos(MAPS[selMap2].aS,MAPS[selMap2].rows);
  const mesh=mkChar(0xff4466,0xcc2244);mesh.position.set(sp.x,0,sp.z);scene.add(mesh);
  AI={x:sp.x,z:sp.z,yaw:0,hp:100,maxHp:100,radius:P_RAD,
      weps:wkeys.map(mkWS),wi:0,alive:true,inv:true,invT:3,walkT:0,
      mesh,state:'chase',flashT:0,shootT:0};
}

// ══════════════════════════════════════════
// VISUAL HELPERS
// ══════════════════════════════════════════
const bGeo=new THREE.SphereGeometry(.09,5,4);
const mats={};
function bmat(c){if(!mats[c])mats[c]=new THREE.MeshBasicMaterial({color:c});return mats[c];}
const ptGeo=new THREE.BoxGeometry(.1,.1,.1);
function spawnFx(x,y,z,c,n=8){
  for(let i=0;i<n;i++){
    const m=new THREE.Mesh(ptGeo,new THREE.MeshBasicMaterial({color:c}));
    m.position.set(x,y,z);scene.add(m);
    const a=Math.random()*Math.PI*2,s=2+Math.random()*4;
    flamePs.push({x,y,z,vx:Math.cos(a)*s,vy:1+Math.random()*4,vz:Math.sin(a)*s,dmg:0,isP:true,rng:0,life:.45,mesh:m,vfx:true});
  }
}

// ══════════════════════════════════════════
// FIRE
// ══════════════════════════════════════════
function fireW(actor,isP){
  const w=actor.weps[actor.wi];
  if(!w||w.shootT>0||w.rel||w.ov)return;
  const d=w.d;
  if(d.cat==='melee'){doMelee(actor,isP,w,false);return;}
  if(d.cat==='flame'){doFlame(actor,isP,w);return;}
  if(d.cat==='throw'){doThrow(actor,isP,w,false);return;}
  if(d.cat==='place'){doPlace(actor,isP,w,1);return;}
  if(w.am<=0){tryRel(actor,isP);return;}
  const yaw=isP?P.yaw:AI.yaw,pitch=isP?P.pitch:0;
  // Player camera faces (-sin(yaw), -cos(yaw)); AI yaw points toward player (+sin/+cos)
  const dir=isP?-1:1;
  for(let i=0;i<(d.p||1);i++){
    const sy=yaw+(Math.random()-.5)*d.spr*2.2,sp2=pitch+(Math.random()-.5)*(d.spr||.03);
    const vx=dir*Math.sin(sy)*Math.cos(sp2)*d.spd,vy=Math.sin(sp2)*d.spd,vz=dir*Math.cos(sy)*Math.cos(sp2)*d.spd;
    const m=new THREE.Mesh(bGeo,bmat(d.c));m.position.set(actor.x+vx*.1,EYE_H,actor.z+vz*.1);scene.add(m);
    projs.push({x:actor.x,y:EYE_H,z:actor.z,vx,vy,vz,dmg:d.dmg*(isP&&aiMarked?1.5:1),isP,life:2.8,mesh:m,burn:!!d.burn});
  }
  if(d.heat)w.heat=Math.min(100,w.heat+3.5);
  w.am--;w.shootT=d.rate;
  if(w.am<=0&&d.rel>0)beginRel(w,isP);
  if(isP){
    refreshWHUD();
    // Recoil kick animation
    CAM.kickY=Math.min(.08+Math.random()*.04, (d.dmg>50?.1:d.p>1?.07:.05));
    CAM.kickDecay=CAM.kickY;
  }
  spawnFx(actor.x-Math.sin(yaw)*.5*dir,EYE_H,actor.z-Math.cos(yaw)*.5*dir,d.c,3);
}

function doMelee(actor,isP,w,isBackstab){
  const tgt=isP?AI:P;
  if(!tgt?.alive)return;
  const dist=Math.hypot(actor.x-tgt.x,actor.z-tgt.z);
  if(dist>w.d.rng){if(isP)msgAnn('Too far!',1);return;}
  let dmg=isBackstab?160:w.d.dmg;
  if(isP){
    if(!AI.inv){AI.hp-=dmg;showDN(dmg,isBackstab,false);spawnFx(AI.x,1.4,AI.z,0xff4466,isBackstab?20:7);if(AI.hp<=0)onAIDead();}
  }else{
    if(!P.inv){P.hp-=dmg;flashDmg();refreshHP();spawnFx(P.x,EYE_H,P.z,0xff4466,7);if(P.hp<=0)onPDead();}
  }
  w.shootT=w.d.rate;if(isP)refreshWHUD();
}

function doFlame(actor,isP,w){
  if(w.am<=0){beginRel(w,isP);return;}
  const yaw=isP?P.yaw:AI.yaw,pitch=isP?P.pitch:0;
  const dir=isP?-1:1;
  for(let i=0;i<3;i++){
    const sy=yaw+(Math.random()-.5)*.28,sp2=pitch+(Math.random()-.5)*.15,s=7+Math.random()*3;
    const m=new THREE.Mesh(bGeo,bmat(Math.random()<.5?0xff5500:0xff9900));
    m.position.set(actor.x+dir*Math.sin(yaw)*.4,EYE_H,actor.z+dir*Math.cos(yaw)*.4);scene.add(m);
    flamePs.push({x:m.position.x,y:EYE_H,z:m.position.z,vx:dir*Math.sin(sy)*s,vy:Math.sin(sp2)*s+.5,vz:dir*Math.cos(sy)*s,dmg:w.d.dmg,isP,rng:w.d.rng||7,life:.55,mesh:m,vfx:false});
  }
  w.am--;w.shootT=w.d.rate;if(w.am<=0)beginRel(w,isP);if(isP)refreshWHUD();
}

function doThrow(actor,isP,w,longThrow){
  if(w.am<=0)return;
  const yaw=isP?P.yaw:AI.yaw,pitch=isP?(P.pitch+.4):.38,s=longThrow?18:11;
  const dir=isP?-1:1;
  const vx=dir*Math.sin(yaw)*Math.cos(pitch)*s,vy=Math.sin(pitch)*s+2,vz=dir*Math.cos(yaw)*Math.cos(pitch)*s;
  const m=new THREE.Mesh(new THREE.BoxGeometry(.22,.22,.22),bmat(w.d.c));
  m.position.set(actor.x+dir*Math.sin(yaw)*.5,EYE_H,actor.z+dir*Math.cos(yaw)*.5);scene.add(m);
  throwns.push({x:m.position.x,y:EYE_H,z:m.position.z,vx,vy,vz,isP,d:w.d,mesh:m,stuck:false,fuse:w.d.sticky?2.5:1.6,bnc:0});
  w.am--;w.shootT=w.d.rate;if(isP)refreshWHUD();
}

function doPlace(actor,isP,w,count){
  for(let i=0;i<count;i++){
    if(w.am<=0)break;
    const ox=i===0?0:(Math.random()-.5)*2.5,oz=i===0?0:(Math.random()-.5)*2.5;
    const m=new THREE.Mesh(new THREE.BoxGeometry(.3,.08,.3),bmat(w.d.c));
    m.position.set(actor.x+ox,.04,actor.z+oz);scene.add(m);
    mines.push({x:actor.x+ox,z:actor.z+oz,isP,d:w.d,mesh:m,armed:false,armT:1.2});
    w.am--;
  }
  w.shootT=w.d.rate;if(isP)refreshWHUD();
}

function beginRel(w,isP){w.rel=true;w.relT=w.d.rel;if(isP)document.getElementById('rLbl').style.opacity='1';}
function tryRel(actor,isP){const w=actor.weps[actor.wi];if(w&&!w.rel&&w.am<w.d.am&&w.d.rel>0)beginRel(w,isP);}

// ══════════════════════════════════════════
// SPECIAL ABILITIES
// ══════════════════════════════════════════
function doSpecial(){
  if(!P?.alive||gst!=='playing')return;
  const w=P.weps[P.wi];
  if(!w||w.specCd>0)return;
  const sp=w.d.special,yaw=P.yaw;
  if(!sp)return;

  if(sp==='backstab'){
    if(!AI?.alive){msgAnn('No target!',1);return;}
    const dist=Math.hypot(P.x-AI.x,P.z-AI.z);
    if(dist>3.8){msgAnn('Get closer for backstab!',1.3);return;}
    const angleToP=Math.atan2(P.x-AI.x,P.z-AI.z);
    const diff=Math.abs(((AI.yaw-angleToP)+Math.PI*3)%(Math.PI*2)-Math.PI);
    const behind=diff<Math.PI*.44;
    if(behind){doMelee(P,true,w,true);msgAnn('BACKSTAB! 💀',1.8);}
    else{doMelee(P,true,w,false);msgAnn('Front stab (turn their back first)',1.4);}
    w.specCd=4;
  }
  else if(sp==='burst'){
    for(let i=0;i<3;i++)setTimeout(()=>{if(P?.alive&&P.weps[P.wi].am>0)fireW(P,true);},i*85);
    w.specCd=3;
  }
  else if(sp==='fan'){
    const left=w.am;for(let i=0;i<left;i++)setTimeout(()=>{if(P?.alive&&P.weps[P.wi].am>0)fireW(P,true);},i*55);
    w.specCd=4;
  }
  else if(sp==='ugnade'){
    const m=new THREE.Mesh(new THREE.BoxGeometry(.22,.22,.22),bmat(0x44aa44));
    m.position.set(P.x-Math.sin(yaw)*.5,EYE_H,P.z-Math.cos(yaw)*.5);scene.add(m);
    const pitch=P.pitch+.5,s=14;
    throwns.push({x:m.position.x,y:EYE_H,z:m.position.z,vx:-Math.sin(yaw)*Math.cos(pitch)*s,vy:Math.sin(pitch)*s+2,vz:-Math.cos(yaw)*Math.cos(pitch)*s,isP:true,d:{dmg:75,rad:5.5},mesh:m,stuck:false,fuse:1.3,bnc:0});
    w.specCd=5;
  }
  else if(sp==='blast'){
    if(w.am<=0)return;
    for(let i=0;i<8;i++){const sy=yaw+(Math.random()-.5)*.95;const m2=new THREE.Mesh(bGeo,bmat(0xffaa44));m2.position.set(P.x,EYE_H,P.z);scene.add(m2);projs.push({x:P.x,y:EYE_H,z:P.z,vx:-Math.sin(sy)*14,vy:0,vz:-Math.cos(sy)*14,dmg:w.d.dmg*2,isP:true,life:.5,mesh:m2,burn:false});}
    w.am--;if(w.am<=0)beginRel(w,true);w.specCd=5;refreshWHUD();
  }
  else if(sp==='mark'){aiMarked=true;aiMarkT=6;msgAnn('TARGET MARKED — +50% DMG for 6s ',1.8);w.specCd=8;}
  else if(sp==='spin'){
    for(let i=0;i<16;i++){const a=(i/16)*Math.PI*2,m2=new THREE.Mesh(bGeo,bmat(0xff5500));m2.position.set(P.x,EYE_H,P.z);scene.add(m2);flamePs.push({x:P.x,y:EYE_H,z:P.z,vx:Math.sin(a)*9,vy:.2,vz:Math.cos(a)*9,dmg:w.d.dmg,isP:true,rng:7,life:.6,mesh:m2,vfx:false});}
    w.am=Math.max(0,w.am-12);w.specCd=5;refreshWHUD();
  }
  else if(sp==='beam'){
    if(AI?.alive&&!AI.inv){const bd=Math.hypot(P.x-AI.x,P.z-AI.z);if(bd<32&&hasLOS(P.x,P.z,AI.x,AI.z)){AI.hp-=55;showDN(55,false,true);spawnFx(AI.x,1.5,AI.z,0x0088ff,14);if(AI.hp<=0)onAIDead();}}
    w.heat=Math.min(100,w.heat+28);w.specCd=4;
  }
  else if(sp==='signal'){
    const m=new THREE.Mesh(new THREE.BoxGeometry(.22,.22,.22),bmat(0xff6600));
    const tx=P.x-Math.sin(yaw)*5,tz=P.z-Math.cos(yaw)*5;
    m.position.set(tx,EYE_H,tz);scene.add(m);
    throwns.push({x:tx,y:EYE_H,z:tz,vx:0,vy:0,vz:0,isP:true,d:{dmg:30,rad:4},mesh:m,stuck:true,fuse:.1,bnc:99});
    burns.push({t:'zone',x:tx,z:tz,rad:4,ti:4.5,dmg:12});
    w.specCd=5;
  }
  else if(sp==='lthrow'){doThrow(P,true,w,true);w.specCd=4;}
  else if(sp==='cook'){
    // Place a grenade with short fuse
    if(w.am<=0)return;
    const m=new THREE.Mesh(new THREE.BoxGeometry(.22,.22,.22),bmat(0x44aa44));
    m.position.set(P.x-Math.sin(yaw)*.5,EYE_H,P.z-Math.cos(yaw)*.5);scene.add(m);
    throwns.push({x:m.position.x,y:EYE_H,z:m.position.z,vx:-Math.sin(yaw)*9,vy:2.5,vz:-Math.cos(yaw)*9,isP:true,d:{dmg:w.d.dmg,rad:w.d.rad},mesh:m,stuck:false,fuse:.35,bnc:0});
    w.am--;refreshWHUD();w.specCd=4;
  }
  else if(sp==='remote'){throwns.filter(t=>t.isP).forEach(t=>t.fuse=0);w.specCd=3;}
  else if(sp==='multi'){doPlace(P,true,w,3);w.specCd=5;}

  refreshWHUD();
}

// ══════════════════════════════════════════
// AI
// ══════════════════════════════════════════
function updateAI(dt){
  if(!AI?.alive||!P?.alive)return;
  if(AI.inv){AI.invT-=dt;if(AI.invT<=0)AI.inv=false;}
  if(AI.flashT>0){AI.flashT-=dt;return;}
  for(const w of AI.weps){
    if(w.shootT>0)w.shootT-=dt;
    if(w.rel){w.relT-=dt;if(w.relT<=0){w.rel=false;w.am=w.d.am===999?999:w.d.am;}}
  }
  const dx=P.x-AI.x,dz=P.z-AI.z,dist=Math.hypot(dx,dz);
  let bi=AI.wi,bs=-99;
  for(let i=0;i<AI.weps.length;i++){
    const w=AI.weps[i];if((w.am===0&&w.d.rel===0)||w.ov)continue;
    const d=w.d;let sc=0;
    if(d.cat==='melee')sc=dist<d.rng?16:dist<4?8:0;
    else if(d.cat==='gun'||d.cat==='flame'){const opt=d.cat==='flame'?4:d.spd>40?18:d.spd>20?12:7;sc=12-Math.abs(dist-opt);}
    else if(d.cat==='throw'&&dist<12&&dist>3)sc=9;
    else if(d.cat==='place'&&dist<5)sc=7;
    if(sc>bs){bs=sc;bi=i;}
  }
  AI.wi=bi;
  if(AI.hp<22)AI.state='flee';
  else{const los=dist<40&&hasLOS(AI.x,AI.z,P.x,P.z);AI.state=(los&&dist<(AI.weps[AI.wi]?.d.rng||15))?'attack':'chase';}
  const spd=(AI.state==='attack'?1.1:3.4)*dt;
  const ang=Math.atan2(dx,dz)+(AI.state==='flee'?Math.PI:0);
  if(dist>1.3||AI.state==='flee'){const r=mv(AI.x,AI.z,Math.sin(ang)*spd,Math.cos(ang)*spd,AI.radius);AI.x=r.x;AI.z=r.z;}
  AI.yaw=Math.atan2(P.x-AI.x,P.z-AI.z);AI.mesh.rotation.y=AI.yaw;AI.mesh.position.set(AI.x,0,AI.z);
  AI.walkT+=dt*7;
  const ew=Math.sin(AI.walkT)*.32;
  if(AI.mesh._ll)AI.mesh._ll.rotation.x=ew;
  if(AI.mesh._rl)AI.mesh._rl.rotation.x=-ew;
  if(AI.mesh._la)AI.mesh._la.rotation.x=-ew*.6;
  if(AI.mesh._ra)AI.mesh._ra.rotation.x=ew*.6;
  if(AI.state==='attack'&&hasLOS(AI.x,AI.z,P.x,P.z)&&dist<32)fireW(AI,false);
}

// ══════════════════════════════════════════
// KEYBOARD
// ══════════════════════════════════════════
const keys={};
let pLocked=false;
document.addEventListener('keydown',e=>{
  const k=e.key.toLowerCase();keys[k]=true;
  if(gst!=='playing')return;
  if(k==='r')tryRel(P,true);
  if(k>='1'&&k<='4'){const i=parseInt(k)-1;if(i<P.weps.length){P.wi=i;refreshWHUD();}}
  if(k===' '){e.preventDefault();if(P?.alive)fireW(P,true);}
  if(k==='e'){e.preventDefault();doSpecial();}
  if(k==='shift'&&P?.alive&&!P.sliding&&P.slideCd<=0)doSlide();
});
document.addEventListener('keyup',e=>{keys[e.key.toLowerCase()]=false;});
cv.addEventListener('click',()=>{if(gst==='playing'&&!IS_MOB)cv.requestPointerLock();});
document.addEventListener('pointerlockchange',()=>{pLocked=document.pointerLockElement===cv;});
document.addEventListener('mousemove',e=>{if(!pLocked||gst!=='playing'||!P?.alive)return;P.yaw-=e.movementX*.0025;P.pitch=Math.max(-1.05,Math.min(.85,P.pitch-e.movementY*.0025));});
document.addEventListener('mousedown',e=>{if(e.button===0){mouseHeld=true;if(gst==='playing'&&P?.alive)fireW(P,true);}});
document.addEventListener('mouseup',e=>{if(e.button===0)mouseHeld=false;});
cv.addEventListener('dblclick',()=>{if(gst==='playing')doSpecial();});

// ══════════════════════════════════════════
// SLIDE
// ══════════════════════════════════════════
function doSlide(){
  if(!P||P.sliding||P.slideCd>0)return;
  P.sliding=true;P.slideT=.58;P.slideCd=2.4;
  P.slideDx=-Math.sin(P.yaw)*9;P.slideDz=-Math.cos(P.yaw)*9;
  const sm=document.getElementById('slideMsg');sm.style.opacity='1';setTimeout(()=>sm.style.opacity='0',500);
}

// ══════════════════════════════════════════
// MOBILE CONTROLS
// Left half  = MOVE joystick  (double-tap = slide)
// Right half = LOOK swipe     (double-tap = special)
// ══════════════════════════════════════════
let jT={id:-1,sx:0,sy:0,cx:0,cy:0};
let lT={id:-1,lx:0,ly:0};
let shootHeld=false;
let lastLTap=0,lastRTap=0;

// Joystick clear helper
function clearJoy(){
  jT.id=-1; jT.cx=jT.sx; jT.cy=jT.sy;
  document.getElementById('jBase').style.display='none';
  document.getElementById('jKnob').style.display='none';
}

if(IS_MOB){
  document.getElementById('shootBtn').style.display='flex';
  document.getElementById('relBtn').style.display='flex';
  document.getElementById('xhair').style.display='none';

  document.addEventListener('touchstart',e=>{
    if(gst==='playing')e.preventDefault();
    for(const t of e.changedTouches){
      if(gst!=='playing')continue;
      // Shoot btn
      const sb=document.getElementById('shootBtn').getBoundingClientRect();
      if(t.clientX>=sb.left&&t.clientX<=sb.right&&t.clientY>=sb.top&&t.clientY<=sb.bottom){shootHeld=true;if(P?.alive)fireW(P,true);continue;}
      // Reload btn
      const rb=document.getElementById('relBtn').getBoundingClientRect();
      if(t.clientX>=rb.left&&t.clientX<=rb.right&&t.clientY>=rb.top&&t.clientY<=rb.bottom){tryRel(P,true);continue;}
      // Weapon slots
      let hs=false;
      document.querySelectorAll('.ws').forEach((ws,i)=>{const r=ws.getBoundingClientRect();if(t.clientX>=r.left&&t.clientX<=r.right&&t.clientY>=r.top&&t.clientY<=r.bottom){P.wi=i;refreshWHUD();hs=true;}});
      if(hs)continue;

      const W=window.innerWidth;
      const isLeft=t.clientX<W*.5;
      if(isLeft){
        // Move joystick — use sentinel -1 (NOT null/0 which are falsy/equal)
        if(jT.id===-1){
          jT={id:t.identifier,sx:t.clientX,sy:t.clientY,cx:t.clientX,cy:t.clientY};
          const jb=document.getElementById('jBase'),jk=document.getElementById('jKnob');
          jb.style.left=t.clientX+'px';jb.style.top=t.clientY+'px';jb.style.display='block';
          jk.style.left=t.clientX+'px';jk.style.top=t.clientY+'px';jk.style.display='block';
        }
        // Double-tap left = SLIDE
        const now=Date.now();
        if(now-lastLTap<280&&P?.alive&&!P.sliding&&P.slideCd<=0)doSlide();
        lastLTap=now;
      }else{
        // Look swipe — use sentinel -1
        if(lT.id===-1)lT={id:t.identifier,lx:t.clientX,ly:t.clientY};
        // Double-tap right = SPECIAL
        const now=Date.now();
        if(now-lastRTap<270)doSpecial();
        lastRTap=now;
      }
    }
  },{passive:false});

  document.addEventListener('touchmove',e=>{
    if(gst!=='playing'||!P?.alive)return;
    e.preventDefault();
    for(const t of e.changedTouches){
      if(t.identifier===jT.id){
        jT.cx=t.clientX;jT.cy=t.clientY;
        const dx=t.clientX-jT.sx,dy=t.clientY-jT.sy,d=Math.min(Math.hypot(dx,dy),44),a=Math.atan2(dy,dx);
        document.getElementById('jKnob').style.left=(jT.sx+Math.cos(a)*d)+'px';
        document.getElementById('jKnob').style.top=(jT.sy+Math.sin(a)*d)+'px';
      }
      if(t.identifier===lT.id&&P){
        P.yaw-=(t.clientX-lT.lx)*.0065;
        P.pitch=Math.max(-1.05,Math.min(.85,P.pitch-(t.clientY-lT.ly)*.0055));
        lT.lx=t.clientX;lT.ly=t.clientY;
      }
    }
  },{passive:false});

  const onTouchEnd=e=>{
    for(const t of e.changedTouches){
      if(t.identifier===jT.id) clearJoy();
      if(t.identifier===lT.id) lT.id=-1;
      const sb=document.getElementById('shootBtn').getBoundingClientRect();
      if(t.clientX>=sb.left&&t.clientX<=sb.right&&t.clientY>=sb.top&&t.clientY<=sb.bottom)shootHeld=false;
    }
  };
  document.addEventListener('touchend',onTouchEnd);
  // Also clear on cancel (system gesture, incoming call, etc.)
  document.addEventListener('touchcancel',()=>{clearJoy();lT.id=-1;shootHeld=false;});
} // end if(IS_MOB)

// ══════════════════════════════════════════
// HUD
// ══════════════════════════════════════════
function refreshWHUD(){
  if(!P)return;
  const w=P.weps[P.wi];
  document.getElementById('wNm').textContent=w?w.d.n:'—';
  if(w){
    const a=w.d.am;
    document.getElementById('wAm').textContent=
      w.d.heat?`Heat: ${Math.round(w.heat)}%`:
      w.d.cat==='melee'?'Unlimited':
      (w.d.cat==='throw'||w.d.cat==='place')?`×${w.am}`:
      `${w.am} / ${a===999?'∞':a}`;
    document.getElementById('rLbl').style.opacity=w.rel?'1':'0';
    const sh=document.getElementById('specHint');
    if(w.d.sDesc){
      const onCd=w.specCd>0;
      sh.textContent=(onCd?`~ ${w.d.sDesc.replace('[E]','').trim()} (${Math.ceil(w.specCd)}s)`:w.d.sDesc);
      sh.style.color=onCd?'rgba(255,160,0,.55)':'rgba(255,215,0,.65)';
    }else sh.textContent='';
  }
  const sc=document.getElementById('wSlots');sc.innerHTML='';
  P.weps.forEach((ww,i)=>{
    const el=document.createElement('div');
    el.className='ws'+(i===P.wi?' cur':'')+(ww.am===0&&ww.d.am!==999?' mt':'');
    el.textContent=ww.d.i;
    el.addEventListener(IS_MOB?'touchstart':'click',ev=>{ev.preventDefault();P.wi=i;refreshWHUD();},{passive:false});
    sc.appendChild(el);
  });
}
function refreshHP(){
  if(!P)return;
  const pct=Math.max(0,P.hp/P.maxHp*100),f=document.getElementById('hpBar');
  f.style.width=pct+'%';
  f.style.background=pct>60?'linear-gradient(90deg,#ff4466,#ff7090)':pct>30?'linear-gradient(90deg,#ff8800,#ffaa44)':'linear-gradient(90deg,#ff2200,#ff4422)';
}
function setScore(){document.getElementById('pS').textContent=pScore;document.getElementById('aS').textContent=aScore;}
function msgAnn(t,d=2.5){const e=document.getElementById('waveMsg');e.textContent=t;e.style.opacity='1';setTimeout(()=>e.style.opacity='0',(d-.35)*1000);}
function kfAdd(txt,isP){const kf=document.getElementById('kf'),el=document.createElement('div');el.className='kfe '+(isP?'pk':'ak');el.textContent=txt;kf.appendChild(el);setTimeout(()=>el.remove(),2600);}
function flashDmg(){
  const v=document.getElementById('dmgV');v.style.opacity='1';setTimeout(()=>v.style.opacity='0',200);
  // Camera shake
  CAM.shakeT=.22; CAM.shakeX=(Math.random()-.5)*.025; CAM.shakeY=(Math.random()-.5)*.018;
}
function flashKill(){
  const v=document.getElementById('killV');v.style.opacity='1';setTimeout(()=>v.style.opacity='0',180);
}
function doFlashBang(){const f=document.getElementById('flashV');f.style.opacity='1';setTimeout(()=>f.style.opacity='0',2700);}

// ══════════════════════════════════════════
// DEATH / ROUND RESET
// ══════════════════════════════════════════
function onPDead(){
  if(!P.alive)return;
  P.alive=false;aScore++;setScore();
  kfAdd('Rival eliminated you!',false);
  if(aScore>=WIN_K){endRound(false);return;}
  doRoundReset('Rival got a kill!');
}
function onAIDead(){
  if(!AI?.alive)return;
  AI.alive=false;scene.remove(AI.mesh);
  spawnFx(AI.x,1.5,AI.z,0xff4466,22);
  pScore++;setScore();
  kfAdd('You eliminated the rival! ',true);
  flashKill();
  if(pScore>=WIN_K){endRound(true);return;}
  doRoundReset('You got a kill!');
}

function doRoundReset(msg){
  // Freeze game
  gst='countdown';
  Object.assign(CAM,{bobT:0,kickY:0,kickDecay:0,tiltZ:0,shakeX:0,shakeY:0,shakeT:0,killFlash:0});
  // Clear all projectiles/throwables/mines to reset arena
  [projs,throwns,mines,flamePs].forEach(arr=>arr.forEach(o=>{if(o?.mesh)scene.remove(o.mesh);}));
  projs=[];throwns=[];mines=[];burns=[];flamePs=[];
  // Move player back to spawn
  const psp=spawnPos(MAPS[selMap2].pS,MAPS[selMap2].rows);
  Object.assign(P,{x:psp.x,z:psp.z,hp:100,alive:true,inv:true,invT:4,pitch:0,sliding:false,slideT:0,slideCd:0});
  P.weps.forEach(w=>{w.am=w.d.am;w.rel=false;w.heat=0;w.ov=false;w.shootT=0;});
  // Respawn AI back to spawn
  if(AI?.mesh)scene.remove(AI.mesh);
  const asp=spawnPos(MAPS[selMap2].aS,MAPS[selMap2].rows);
  const mesh=mkChar(0xff4466,0xcc2244);mesh.position.set(asp.x,0,asp.z);scene.add(mesh);
  AI={x:asp.x,z:asp.z,yaw:0,hp:100,maxHp:100,radius:P_RAD,
      weps:aiWepKeys.map(mkWS),wi:0,alive:true,inv:true,invT:4,walkT:0,
      mesh,state:'chase',flashT:0,shootT:0};
  refreshHP();refreshWHUD();
  // Show countdown overlay
  const ss=document.getElementById('spawnV');
  document.getElementById('spTitle').textContent='ROUND RESET';
  document.getElementById('spSub').textContent=msg;
  ss.style.display='flex';
  let c=5;
  document.getElementById('spCnt').textContent=c;
  const iv=setInterval(()=>{
    c--;
    document.getElementById('spCnt').textContent=c;
    if(c<=0){
      clearInterval(iv);
      ss.style.display='none';
      gst='playing';
      msgAnn('FIGHT!');
    }
  },1000);
}
function endRound(win){
  gst='roundOver';
  document.getElementById('hud').style.display='none';
  if(pLocked)document.exitPointerLock();
  document.getElementById('roT').textContent=win?'YOU WIN!':'YOU LOST';
  document.getElementById('roT').className='roTitle '+(win?'win':'lose');
  document.getElementById('roS').textContent=pScore+' - '+aScore;
  document.getElementById('roDmg').textContent='Total damage dealt: '+totalDmg;
  showScr('roScr');
}

// ══════════════════════════════════════════
// MAIN UPDATE
// ══════════════════════════════════════════
function update(dt){
  if(gst==='countdown'){
    // Still update camera position so view doesn't freeze
    if(P) camera.position.set(P.x,EYE_H,P.z);
    return;
  }
  if(gst!=='playing')return;
  if(aiMarked){aiMarkT-=dt;if(aiMarkT<=0){aiMarked=false;aiMarkT=0;}}

  // Weapon ticks
  if(P?.alive){
    for(const w of P.weps){
      if(w.shootT>0)w.shootT-=dt;
      if(w.specCd>0){w.specCd-=dt;if(w.specCd<=0){w.specCd=0;refreshWHUD();}}
      if(w.rel){w.relT-=dt;if(w.relT<=0){w.rel=false;w.am=w.d.am===999?999:w.d.am;document.getElementById('rLbl').style.opacity='0';refreshWHUD();}}
      if(w.d.heat){if(w.ov){w.heat-=22*dt;if(w.heat<=0){w.heat=0;w.ov=false;refreshWHUD();}}else{w.heat=Math.max(0,w.heat-10*dt);if(w.heat>=100)w.ov=true;}}
    }
    const cw=P.weps[P.wi];
    if(cw?.d.auto&&!cw.rel&&!cw.ov){if(IS_MOB?shootHeld:(mouseHeld||keys[' ']))fireW(P,true);}
    if(P.inv){P.invT-=dt;if(P.invT<=0)P.inv=false;}
  }

  // Slide
  if(P?.alive){
    if(P.slideCd>0)P.slideCd-=dt;
    if(P.sliding){
      P.slideT-=dt;
      const frac=Math.max(0,P.slideT/.58);
      const r=mv(P.x,P.z,P.slideDx*frac*dt,P.slideDz*frac*dt,P.radius);P.x=r.x;P.z=r.z;
      if(P.slideT<=0)P.sliding=false;
    }
    const fillPct=P.slideCd>0?Math.max(0,1-P.slideCd/2.4):1;
    document.getElementById('slideFill').style.width=(fillPct*100)+'%';
  }

  // Player move
  if(P?.alive&&!P.sliding){
    let mdx=0,mdz=0;
    if(IS_MOB&&jT.id!==-1){
      const jdx=(jT.cx-jT.sx)/44,jdy=(jT.cy-jT.sy)/44;
      // jdy is negative when pushing UP — use directly (no negation) so up = forward
      if(Math.hypot(jdx,jdy)>.08){mdx=Math.sin(P.yaw)*jdy+Math.cos(P.yaw)*jdx;mdz=Math.cos(P.yaw)*jdy-Math.sin(P.yaw)*jdx;}
    }else{
      if(keys['w']||keys['arrowup'])   {mdx-=Math.sin(P.yaw);mdz-=Math.cos(P.yaw);}
      if(keys['s']||keys['arrowdown']) {mdx+=Math.sin(P.yaw);mdz+=Math.cos(P.yaw);}
      if(keys['a']||keys['arrowleft']) {mdx-=Math.cos(P.yaw);mdz+=Math.sin(P.yaw);}
      if(keys['d']||keys['arrowright']){mdx+=Math.cos(P.yaw);mdz-=Math.sin(P.yaw);}
    }
    const ml=Math.hypot(mdx,mdz);
    if(ml>.001){const r=mv(P.x,P.z,mdx/ml*5.2*dt,mdz/ml*5.2*dt,P_RAD);P.x=r.x;P.z=r.z;}
  }

  // ── Camera animations ──
  const isMoving = IS_MOB ? jT.id!==-1 : (keys['w']||keys['s']||keys['a']||keys['d']||keys['arrowup']||keys['arrowdown']||keys['arrowleft']||keys['arrowright']);
  if(isMoving&&!P.sliding) CAM.bobT+=dt*9;

  // Head bob
  const bob = isMoving&&!P.sliding ? Math.sin(CAM.bobT)*.028 : 0;
  const bobX = isMoving&&!P.sliding ? Math.sin(CAM.bobT*.5)*.012 : 0;

  // Recoil decay
  if(CAM.kickDecay>0){ CAM.kickDecay=Math.max(0,CAM.kickDecay-dt*4.5); CAM.kickY=CAM.kickDecay; }

  // Damage shake decay
  if(CAM.shakeT>0){ CAM.shakeT-=dt; if(CAM.shakeT<=0){CAM.shakeX=0;CAM.shakeY=0;} }

  // Slide tilt
  const targetTilt = P.sliding ? -0.14 : 0;
  CAM.tiltZ += (targetTilt - CAM.tiltZ) * Math.min(1, dt*10);

  const eo = P.sliding ? .55 : 0;
  camera.position.set(P.x + CAM.shakeX, EYE_H - eo + bob, P.z + CAM.shakeY);
  camera.rotation.y = P.yaw + bobX;
  camera.rotation.x = (P.sliding ? Math.min(0,P.pitch)*.5 : P.pitch) - CAM.kickY;
  camera.rotation.z = CAM.tiltZ;

  updateAI(dt);

  // Projectiles
  for(let i=projs.length-1;i>=0;i--){
    const p=projs[i];p.x+=p.vx*dt;p.y+=p.vy*dt;p.z+=p.vz*dt;p.life-=dt;
    p.mesh.position.set(p.x,p.y,p.z);
    if(wallHit(p.x,p.z,.12)||p.life<=0){spawnFx(p.x,p.y,p.z,p.mesh.material.color.getHex(),4);scene.remove(p.mesh);projs.splice(i,1);continue;}
    if(p.isP&&AI?.alive&&!AI.inv&&Math.hypot(p.x-AI.x,p.z-AI.z)<.68&&Math.abs(p.y-1.3)<1.5){
      AI.hp-=p.dmg;showDN(p.dmg,p.dmg>70,false);spawnFx(p.x,p.y,p.z,0xff4466,6);scene.remove(p.mesh);projs.splice(i,1);
      if(p.burn)burns.push({t:'ai',ti:4,dmg:4.5});if(AI.hp<=0)onAIDead();continue;
    }
    if(!p.isP&&P?.alive&&!P.inv&&Math.hypot(p.x-P.x,p.z-P.z)<.65&&Math.abs(p.y-EYE_H)<1.1){
      P.hp-=p.dmg;flashDmg();refreshHP();scene.remove(p.mesh);projs.splice(i,1);
      if(p.burn)burns.push({t:'p',ti:4,dmg:4.5});if(P.hp<=0)onPDead();continue;
    }
  }

  // Flames / particles
  for(let i=flamePs.length-1;i>=0;i--){
    const f=flamePs[i];f.x+=f.vx*dt;f.y+=f.vy*dt;f.z+=f.vz*dt;f.vy-=(f.vfx?9:4)*dt;f.life-=dt;
    f.mesh.position.set(f.x,f.y,f.z);f.mesh.scale.setScalar(Math.max(0,f.life*2.5));
    if(wallHit(f.x,f.z,.12)||f.life<=0){scene.remove(f.mesh);flamePs.splice(i,1);continue;}
    if(!f.vfx&&f.rng>0){
      if(f.isP&&AI?.alive&&!AI.inv&&Math.hypot(f.x-AI.x,f.z-AI.z)<f.rng&&Math.abs(f.y-1.3)<2){AI.hp-=f.dmg*dt*18;if(AI.hp<=0)onAIDead();}
      if(!f.isP&&P?.alive&&!P.inv&&Math.hypot(f.x-P.x,f.z-P.z)<f.rng&&Math.abs(f.y-EYE_H)<1.6){P.hp-=f.dmg*dt*18;flashDmg();refreshHP();if(P.hp<=0)onPDead();}
    }
  }

  // Thrown
  for(let i=throwns.length-1;i>=0;i--){
    const t=throwns[i];
    if(!t.stuck){
      t.x+=t.vx*dt;t.y+=t.vy*dt;t.z+=t.vz*dt;t.vy-=14*dt;
      t.mesh.rotation.x+=4*dt;t.mesh.rotation.z+=3*dt;
      if(t.y<=.12||wallHit(t.x,t.z,.15)){t.y=Math.max(.12,t.y);t.vy*=-.28;t.vx*=.5;t.vz*=.5;t.bnc++;if(t.d.sticky&&t.bnc>=1)t.stuck=true;}
      t.mesh.position.set(t.x,t.y,t.z);
    }
    t.fuse-=dt;if(t.fuse<=0)exThrow(t,i);
  }

  // Mines
  for(let i=mines.length-1;i>=0;i--){
    const m=mines[i];if(!m.armed){m.armT-=dt;if(m.armT<=0)m.armed=true;continue;}
    const tx=m.isP?AI?.x:P?.x,tz=m.isP?AI?.z:P?.z;
    if(tx!==undefined&&Math.hypot(tx-m.x,tz-m.z)<m.d.rad*.75)exMine(m,i);
  }

  // Burns
  for(let i=burns.length-1;i>=0;i--){
    const b=burns[i];b.ti-=dt;
    if(b.t==='p'&&P?.alive&&!P.inv){P.hp-=b.dmg*dt;flashDmg();refreshHP();if(P.hp<=0){onPDead();burns.splice(i,1);continue;}}
    if(b.t==='ai'&&AI?.alive&&!AI.inv){AI.hp-=b.dmg*dt;if(AI.hp<=0){onAIDead();burns.splice(i,1);continue;}}
    if(b.t==='zone'){
      if(P?.alive&&!P.inv&&Math.hypot(P.x-b.x,P.z-b.z)<b.rad){P.hp-=b.dmg*dt;flashDmg();refreshHP();if(P.hp<=0)onPDead();}
      if(AI?.alive&&!AI.inv&&Math.hypot(AI.x-b.x,AI.z-b.z)<b.rad){AI.hp-=b.dmg*dt;if(AI.hp<=0)onAIDead();}
    }
    if(b.ti<=0)burns.splice(i,1);
  }
}

function exThrow(t,idx){
  scene.remove(t.mesh);throwns.splice(idx,1);
  if(t.d.flash){
    if(Math.hypot(t.x-P.x,t.z-P.z)<10)doFlashBang();
    if(AI&&Math.hypot(t.x-AI.x,t.z-AI.z)<10)AI.flashT=2.8;
    spawnFx(t.x,t.y,t.z,0xffffff,14);return;
  }
  spawnFx(t.x,t.y+.5,t.z,0xff8800,16);
  const pd=Math.hypot(t.x-P.x,t.z-P.z),ad=AI?Math.hypot(t.x-AI.x,t.z-AI.z):999;
  if(!t.isP&&P?.alive&&!P.inv&&pd<t.d.rad){const d=t.d.dmg*(1-pd/t.d.rad);P.hp-=d;flashDmg();refreshHP();if(P.hp<=0)onPDead();}
  if(t.isP&&AI?.alive&&!AI.inv&&ad<t.d.rad){const d=t.d.dmg*(1-ad/t.d.rad);AI.hp-=d;showDN(d,d>60,false);if(AI.hp<=0)onAIDead();}
}
function exMine(m,idx){
  scene.remove(m.mesh);mines.splice(idx,1);spawnFx(m.x,.5,m.z,0x9900ff,18);
  const pd=Math.hypot(m.x-P.x,m.z-P.z),ad=AI?Math.hypot(m.x-AI.x,m.z-AI.z):999;
  if(!m.isP&&P?.alive&&!P.inv&&pd<m.d.rad){const d=m.d.dmg*(1-pd/m.d.rad);P.hp-=d;flashDmg();refreshHP();if(P.hp<=0)onPDead();}
  if(m.isP&&AI?.alive&&!AI.inv&&ad<m.d.rad){const d=m.d.dmg*(1-ad/m.d.rad);AI.hp-=d;showDN(d,d>60,false);if(AI.hp<=0)onAIDead();}
}

// ══════════════════════════════════════════
// SCREENS
// ══════════════════════════════════════════
const SCRIDS=['menuScr','mapScr','wepScr','roScr'];
function showScr(id){SCRIDS.forEach(s=>{const e=document.getElementById(s);const show=s===id;e.classList.toggle('off',!show);e.style.display=show?'flex':'none';});}

let selWeps=new Set();
function buildMapGrid(){
  const g=document.getElementById('mapGrid');g.innerHTML='';
  MAPS.forEach((m,i)=>{
    const el=document.createElement('div');
    const sz=m.sz==='big'?'big':m.sz==='med'?'med':'sm';
    el.className='mapCard'+(m.sz==='big'?' fullW':'')+(selMap2===i?' sel':'');
    el.innerHTML=`<div class="mapName">${m.name}</div><div class="mapSz ${sz}">${{sm:'Small',big:'Big',med:'Medium'}[m.sz]}</div><div class="mapDesc">${m.desc}</div>`;
    el.onclick=()=>{selMap2=i;document.querySelectorAll('.mapCard').forEach(c=>c.classList.remove('sel'));el.classList.add('sel');document.getElementById('mapNext').disabled=false;};
    g.appendChild(el);
  });
  document.getElementById('mapNext').disabled=false;
}
function buildWepGrid(){
  const g=document.getElementById('wGrid');g.innerHTML='';selWeps.clear();
  WK.forEach(k=>{
    const d=WD[k],el=document.createElement('div');el.className='wCard';el.dataset.key=k;
    el.innerHTML=`<div class="wIco">${d.i}</div><div class="wNm">${d.n}</div><div class="wCat cat-${d.cat}">${d.cat}</div>`;
    el.onclick=()=>{
      if(selWeps.has(k)){selWeps.delete(k);el.classList.remove('sel');}
      else if(selWeps.size<4){selWeps.add(k);el.classList.add('sel');}
      document.getElementById('wCnt').textContent=`Pick up to 4 weapons (${selWeps.size} / 4)`;
      document.getElementById('wReady').disabled=selWeps.size===0;
      document.querySelectorAll('.wCard').forEach(c=>{c.classList.toggle('dis',selWeps.size>=4&&!selWeps.has(c.dataset.key));});
    };
    g.appendChild(el);
  });
  document.getElementById('wCnt').textContent='Pick up to 4 weapons (0 / 4)';
  document.getElementById('wReady').disabled=true;
}
function startGame(){
  if(AI?.mesh)scene.remove(AI.mesh);
  [projs,throwns,mines,flamePs,burns].forEach(arr=>arr.forEach(o=>{if(o?.mesh)scene.remove(o.mesh);}));
  projs=[];throwns=[];mines=[];flamePs=[];burns=[];
  pScore=0;aScore=0;totalDmg=0;aiMarked=false;
  document.getElementById('dmgVal').textContent='0';setScore();
  buildMap(MAPS[selMap2]);
  pWeps2=selWeps.size>0?Array.from(selWeps):['pistol'];
  const pool=[...WK];aiWepKeys=[];
  while(aiWepKeys.length<4&&pool.length)aiWepKeys.push(pool.splice(Math.floor(Math.random()*pool.length),1)[0]);
  initP(pWeps2);initAI(aiWepKeys);
  showScr(null);
  document.getElementById('hud').style.display='block';
  document.getElementById('spawnV').style.display='none';
  gst='playing';msgAnn('FIGHT!');
}

document.getElementById('menuBtn').onclick=()=>{buildMapGrid();showScr('mapScr');};
document.getElementById('mapNext').onclick=()=>{buildWepGrid();showScr('wepScr');};
document.getElementById('wBack').onclick=()=>{buildMapGrid();showScr('mapScr');};
document.getElementById('wReady').onclick=startGame;
document.getElementById('roMenu').onclick=()=>{gst='menu';document.getElementById('hud').style.display='none';showScr('menuScr');};
document.getElementById('roAgain').onclick=startGame;

// ══════════════════════════════════════════
// LOOP
// ══════════════════════════════════════════
buildMap(MAPS[0]);
camera.position.set(MAPS[0].pS.c*TILE+TILE/2+2,10,MAPS[0].pS.r*TILE+TILE/2+14);
camera.lookAt(MAPS[0].pS.c*TILE+TILE/2,0,MAPS[0].pS.r*TILE+TILE/2);
function loop(t){
  requestAnimationFrame(loop);
  const dt=Math.min((t-lastT)/1000,.05);lastT=t;
  update(dt);
  if(gst==='menu'||gst==='mapSel'||gst==='wepSel')
    camera.position.x=MAPS[0].pS.c*TILE+TILE/2+Math.sin(t*.0003)*8;
  renderer.render(scene,camera);
}
showScr('menuScr');
requestAnimationFrame(loop);
</script>

</body>
</html>
