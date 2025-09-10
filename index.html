<!doctype html>
<html lang="ja">
<head>
<meta charset="utf-8"/>
<title>ブラウザTCG - 完全サンプル</title>
<meta name="viewport" content="width=device-width,initial-scale=1"/>
<style>
  body{font-family:system-ui,Arial;background:#f6f7fb;margin:12px;color:#111}
  h1{margin:0 0 12px}
  .row{display:flex;gap:12px;align-items:flex-start}
  .panel{background:#fff;border:1px solid #e0e0e0;border-radius:8px;padding:10px;box-shadow:0 1px 3px rgba(0,0,0,0.04)}
  .panel.small{width:260px}
  .card{display:inline-block;background:#fff;border:1px solid #bbb;border-radius:6px;padding:6px;margin:6px;width:120px;text-align:center;font-size:13px;cursor:pointer}
  .card.small{width:90px;padding:4px;font-size:12px}
  .btn{display:inline-block;padding:6px 10px;border-radius:6px;background:#fff;border:1px solid #333;cursor:pointer;margin:4px}
  .btn.primary{background:#111;color:#fff;border-color:#111}
  .muted{color:#666;font-size:13px}
  .fieldCardBox{background:#fff8dc;padding:8px;border-radius:6px;border:1px solid #d7c59a}
  .hand{min-height:80px}
  .zone{min-height:80px;padding:8px;border:1px dashed #ddd;border-radius:6px}
  input[type=text]{padding:6px;border-radius:6px;border:1px solid #ccc;width:220px}
  .deckRow{display:flex;gap:8px;align-items:center;margin:6px 0}
  #modal{position:fixed;inset:0;display:none;align-items:center;justify-content:center;background:rgba(0,0,0,0.5)}
  #modal .box{background:#fff;padding:18px;border-radius:8px;min-width:300px;text-align:center}
  .new{color:#c00;font-weight:700}
  .statusSmall{font-size:13px;color:#444}
</style>
</head>
<body>

<h1>ブラウザTCG - 完全サンプル</h1>

<div id="menu" class="row" style="margin-bottom:12px">
  <div class="panel small">
    <div><strong>所持パック:</strong> <span id="packCount">0</span></div>
    <div><strong>欠片:</strong> <span id="shardCount">0</span></div>
    <div style="margin-top:8px">
      <button class="btn" onclick="openDeckBuilder()">デッキ構築</button>
      <button class="btn" onclick="openPackOpener()">パック開封</button>
      <button class="btn" onclick="openCollection()">所持カード</button>
    </div>
  </div>

  <div class="panel" style="flex:1">
    <div class="muted">ローカル保存（localStorage）でコレクション・デッキを管理します。</div>
    <div style="margin-top:8px">
      <button class="btn primary" onclick="startQuickMatch()">クイック対戦（自動デッキ）</button>
      <button class="btn" onclick="startMatchWithSavedDeck()">対戦開始（保存デッキから）</button>
      <button class="btn" onclick="resetAll()">セーブ初期化</button>
    </div>
  </div>
</div>

<!-- デッキ構築 -->
<div id="deckBuilder" class="panel" style="display:none;margin-bottom:12px">
  <h2>デッキ構築</h2>
  <div class="muted">デッキは30枚、同一カードは最大4枚まで。不要なカードはデッキ上でクリックして所持に戻せます。</div>

  <div style="margin-top:8px">
    <strong>保存デッキ</strong>
    <div id="savedDecks" style="margin-top:8px"></div>
  </div>

  <hr>

  <div style="margin-top:8px">
    <strong>所持コレクション</strong>
    <div id="collectionArea" style="margin-top:8px"></div>
  </div>

  <div style="margin-top:8px">
    <strong>現在のデッキ（<span id="deckCount">0</span>/30）</strong>
    <div id="deckArea" style="margin-top:8px"></div>
    <div style="margin-top:8px">
      <input id="deckName" type="text" placeholder="デッキ名を入力（例: 初心者デッキ）"/>
      <button class="btn" onclick="saveCurrentDeck()">デッキ名を付けて保存</button>
      <button class="btn primary" onclick="saveDeckAndStart()">デッキ保存して開始</button>
      <button class="btn" onclick="closeDeckBuilder()">閉じる</button>
    </div>
  </div>
</div>

<!-- 所持カード -->
<div id="collectionPanel" class="panel" style="display:none;margin-bottom:12px">
  <h2>所持カード</h2>
  <div id="collectionList"></div>
  <div style="margin-top:8px"><button class="btn" onclick="clearNewFlags()">NEWをクリア</button> <button class="btn" onclick="closeCollection()">閉じる</button></div>
</div>

<!-- パック開封 -->
<div id="packOpener" class="panel" style="display:none;margin-bottom:12px">
  <h2>パック開封</h2>
  <div>
    <button class="btn" onclick="openPackManual()">1パック開封</button>
    <button class="btn" id="exchangeBtn" onclick="exchangeShards()">欠片6個で1パック交換</button>
  </div>
  <div id="packResult" style="margin-top:12px"></div>
  <div style="margin-top:8px">
    <button class="btn" onclick="closePackOpener()">閉じる</button>
  </div>
</div>

<!-- 対戦画面 -->
<div id="battleArea" class="panel" style="display:none">
  <div style="display:flex;justify-content:space-between;align-items:center">
    <div>
      <strong>あなた</strong> ライフ: <span id="playerLife">20</span> ｜ マナ: <span id="playerMana">0</span>/<span id="playerMaxMana">0</span>
    </div>
    <div>
      <button class="btn" onclick="surrender()">降参</button>
      <button class="btn" onclick="giveDebugPack()">（デバッグ）1パック獲得</button>
    </div>
    <div>
      <strong>CPU</strong> ライフ: <span id="cpuLife">20</span> ｜ マナ: <span id="cpuMana">0</span>/<span id="cpuMaxMana">0</span>
    </div>
  </div>

  <div style="margin-top:8px" id="fieldCardArea">
    <div class="fieldCardBox" id="fieldCardBox">フィールド: なし</div>
  </div>

  <div style="margin-top:10px">
    <div><strong>CPU フィールド</strong></div>
    <div id="cpuField" class="zone cpu"></div>
  </div>

  <div style="margin-top:10px">
    <div><strong>あなたのフィールド</strong></div>
    <div id="playerField" class="zone player"></div>
  </div>

  <div style="margin-top:10px">
    <div><strong>あなたの手札</strong></div>
    <div id="playerHand" class="hand"></div>
  </div>

  <div style="margin-top:10px">
    <button class="btn" onclick="endTurn()">ターン終了</button>
    <button class="btn primary" onclick="attackModeToggle()">攻撃モード</button>
    <span class="muted" id="modeHint"></span>
  </div>
</div>

<!-- モーダル -->
<div id="modal">
  <div class="box" id="modalBox"></div>
</div>

<script>
/* -------------------------
   カード定義（日本語）
--------------------------*/
const ALL_CARDS = [
  {id:"slime", name:"スライム", type:"monster", cost:1, atk:1, desc:"召喚時: デッキにスライムがあれば1枚手札に加える"},
  {id:"kijin", name:"鬼人", type:"monster", cost:5, atk:4, desc:"エンド時: 相手モンスターをランダムで1体破壊"},
  {id:"necromancer", name:"ネクロマンサー", type:"monster", cost:4, atk:2, desc:"エンド時: 自分墓地からランダムでモンスターを召喚"},
  {id:"jyujutsushi", name:"呪術師", type:"monster", cost:4, atk:2, desc:"場にいる間: 相手モンスターの効果無効化"},
  {id:"happy", name:"ハッピーマウンテン", type:"field", cost:2, desc:"エンド時: 両者1ドロー"},
  {id:"forest", name:"亡者の森", type:"field", cost:3, desc:"エンド時: ランダムな墓地のカード1枚を持ち主の手札へ"},
  {id:"heal", name:"ヒーリングライト", type:"spell", cost:2, desc:"自分のライフを3回復"},
  {id:"sacrifice", name:"ダークサクリファイス", type:"spell", cost:3, desc:"自分モンスター1体破壊→その攻撃力分相手にダメージ"},
  {id:"thunder", name:"雷撃", type:"spell", cost:4, desc:"相手に2ダメージ"},
  {id:"relic", name:"亡者の遺品", type:"spell", cost:2, desc:"自分の墓地のカード1枚を手札に戻す"}
];

/* -------------------------
   localStorageキー
--------------------------*/
const KEY_COLLECTION = "tcg_collection_v3";
const KEY_PACKS = "tcg_packs_v3";
const KEY_SHARDS = "tcg_shards_v3";
const KEY_DECKS = "tcg_decks_v3";
const KEY_NEW = "tcg_new_v3";

/* -------------------------
   状態
--------------------------*/
let collection = {};           // {id:count}
let packCount = 0;
let shardCount = 0;
let savedDecks = {};           // {name: [id,...]}
let currentDeck = [];          // building deck
let newCards = {};             // {id:true} for NEW badge

let player = null, cpu = null;
let globalField = null;
let playerTurn = true;
let attackMode = false;
let selectedAttacker = null;
let gameActive = false;

/* -------------------------
   ユーティリティ
--------------------------*/
function cardById(id){ return ALL_CARDS.find(c=>c.id===id) || null; }
function saveAll(){
  localStorage.setItem(KEY_COLLECTION, JSON.stringify(collection));
  localStorage.setItem(KEY_PACKS, String(packCount));
  localStorage.setItem(KEY_SHARDS, String(shardCount));
  localStorage.setItem(KEY_DECKS, JSON.stringify(savedDecks));
  localStorage.setItem(KEY_NEW, JSON.stringify(newCards));
}
function loadAll(){
  collection = JSON.parse(localStorage.getItem(KEY_COLLECTION) || "{}");
  packCount = parseInt(localStorage.getItem(KEY_PACKS) || "0");
  shardCount = parseInt(localStorage.getItem(KEY_SHARDS) || "0");
  savedDecks = JSON.parse(localStorage.getItem(KEY_DECKS) || "{}");
  newCards = JSON.parse(localStorage.getItem(KEY_NEW) || "{}");
}

/* -------------------------
   初期10パック配布（自動開封・NEW登録）
--------------------------*/
function ensureInitialPacks(){
  loadAll();
  if(Object.keys(collection).length===0 && packCount===0 && shardCount===0){
    for(let i=0;i<10;i++){ openPackInternal(true); } // silently add to collection but mark NEW
    packCount = 0; // initial packs consumed into collection
    saveAll();
    alert("初期10パックを配布しました（コレクションに追加されました）");
  }
  updateTopCounts();
}

/* -------------------------
   コレクション管理（欠片ルール）
   - 所持4枚上限、5枚目以降は欠片化
   - NEWフラグを付ける
--------------------------*/
function addCardToCollection(id){
  const owned = collection[id] || 0;
  if(owned < 4){
    collection[id] = owned + 1;
    newCards[id] = true;
    saveAll();
    return {isNew: owned===0, shardGained:false};
  } else {
    shardCount++;
    saveAll();
    updateTopCounts();
    return {isNew:false, shardGained:true};
  }
}

/* -------------------------
   パック（1パック=5枚）
--------------------------*/
function openPackInternal(silent=false){
  const results = [];
  for(let i=0;i<5;i++){
    const c = ALL_CARDS[Math.floor(Math.random()*ALL_CARDS.length)];
    const res = addCardToCollection(c.id);
    results.push({card:c, isNew:res.isNew, shardGained:res.shardGained});
  }
  if(!silent) showPackResultOnPage(results);
  updateTopCounts();
  saveAll();
  return results;
}
function openPackManual(){
  if(packCount<=0){ alert("パックがありません"); return; }
  packCount--; saveAll(); updateTopCounts();
  const res = openPackInternal(false);
  showPackResultOnPage(res);
}
function exchangeShards(){
  if(shardCount < 6){ alert("欠片が6個必要です"); return; }
  shardCount -= 6; packCount++; saveAll(); updateTopCounts();
  alert("欠片6個で1パックを獲得しました");
}
function showPackResultOnPage(results){
  const area = document.getElementById("packResult");
  area.innerHTML = "<h3>開封結果</h3>";
  results.forEach(r=>{
    const div = document.createElement("div"); div.className="card small";
    div.innerHTML = `${r.card.name} ${r.isNew?'<span class="new">NEW!</span>':''} ${r.shardGained?'（欠片+1）':''}`;
    area.appendChild(div);
  });
}

/* -------------------------
   UI top counts
--------------------------*/
function updateTopCounts(){
  document.getElementById("packCount").textContent = packCount;
  document.getElementById("shardCount").textContent = shardCount;
  document.getElementById("exchangeBtn").disabled = (shardCount < 6);
}

/* -------------------------
   デッキ構築 UI
   - 所持一覧を表示、クリックでデッキへ
   - デッキ上のカードをクリックで「戻す（所持へ）」
--------------------------*/
function openDeckBuilder(){
  loadAll();
  document.getElementById("menu").style.display = "none";
  document.getElementById("packOpener").style.display = "none";
  document.getElementById("collectionPanel").style.display = "none";
  document.getElementById("deckBuilder").style.display = "block";
  renderSavedDecks();
  renderCollectionArea();
  renderDeckArea();
  updateTopCounts();
}
function closeDeckBuilder(){
  document.getElementById("deckBuilder").style.display = "none";
  document.getElementById("menu").style.display = "flex";
}
function renderSavedDecks(){
  const area = document.getElementById("savedDecks"); area.innerHTML="";
  for(const name in savedDecks){
    const row = document.createElement("div"); row.className="deckRow";
    const span = document.createElement("div"); span.style.flex="1"; span.textContent = `${name} (${savedDecks[name].length}枚)`;
    const loadBtn = document.createElement("button"); loadBtn.className="btn"; loadBtn.textContent="読み込み";
    loadBtn.onclick = ()=>{ currentDeck = savedDecks[name].slice(); renderCollectionArea(); renderDeckArea(); };
    const delBtn = document.createElement("button"); delBtn.className="btn"; delBtn.textContent="削除";
    delBtn.onclick = ()=>{ if(confirm(`${name} を削除しますか？`)){ delete savedDecks[name]; saveAll(); renderSavedDecks(); } };
    row.appendChild(span); row.appendChild(loadBtn); row.appendChild(delBtn);
    area.appendChild(row);
  }
}
function renderCollectionArea(){
  const area = document.getElementById("collectionArea"); area.innerHTML = "";
  ALL_CARDS.forEach(c=>{
    const owned = collection[c.id] || 0;
    const inDeck = currentDeck.filter(x=>x===c.id).length;
    const d = document.createElement("div"); d.className="card";
    d.innerHTML = `<strong>${c.name}</strong><div class="muted">${c.type} / cost:${c.cost||"-"}</div><div>所持:${owned} / デッキ:${inDeck}</div>${newCards[c.id] ? ' <div class="new">NEW</div>' : ''}`;
    d.onclick = ()=>{
      if(currentDeck.length >= 30){ alert("デッキは30枚までです"); return; }
      if(inDeck >= 4){ alert("同じカードは4枚までです"); return; }
      if(inDeck >= owned){ alert("所持枚数を超えています"); return; }
      currentDeck.push(c.id); renderCollectionArea(); renderDeckArea();
    };
    area.appendChild(d);
  });
}
function renderDeckArea(){
  const area = document.getElementById("deckArea"); area.innerHTML = "";
  currentDeck.forEach((id, idx)=>{
    const c = cardById(id);
    const d = document.createElement("div"); d.className="card";
    d.innerHTML = `${c.name}<div class="muted">クリックでデッキから戻す</div>`;
    d.onclick = ()=>{ // 戻す機能：デッキ->所持に1枚戻す
      const owned = collection[id] || 0;
      if(owned >= 4){
        // If collection already has 4, converting to shard makes sense; but for deck-building '戻す' we should allow incrementing collection beyond 4?
        // We'll allow returning to collection but still cap display at 4 (excess becomes shards)
        shardCount++;
        alert('所持が4枚以上のため、戻したカードは欠片に変換されました（欠片+1）');
      } else {
        collection[id] = owned + 1;
      }
      currentDeck.splice(idx,1);
      saveAll();
      renderCollectionArea(); renderDeckArea(); updateTopCounts();
    };
    area.appendChild(d);
  });
  document.getElementById("deckCount").textContent = currentDeck.length;
}
function saveCurrentDeck(){
  const name = document.getElementById("deckName").value.trim();
  if(!name){ alert("デッキ名を入力してください"); return; }
  if(currentDeck.length !== 30){ alert("デッキはちょうど30枚必要です"); return; }
  savedDecks[name] = currentDeck.slice();
  saveAll();
  renderSavedDecks();
  alert("デッキを保存しました: " + name);
}
function saveDeckAndStart(){
  if(currentDeck.length !== 30){ alert("デッキはちょうど30枚必要です"); return; }
  saveAll();
  startMatchWithDeck(currentDeck);
}

/* -------------------------
   所持カード表示
--------------------------*/
function openCollection(){
  loadAll();
  document.getElementById("menu").style.display = "none";
  document.getElementById("collectionPanel").style.display = "block";
  renderCollectionList();
}
function closeCollection(){ document.getElementById("collectionPanel").style.display="none"; document.getElementById("menu").style.display="flex"; }
function renderCollectionList(){
  const area = document.getElementById("collectionList"); area.innerHTML="";
  ALL_CARDS.forEach(c=>{
    const owned = collection[c.id] || 0;
    const wrap = document.createElement("div"); wrap.style.display="inline-block";
    const d = document.createElement("div"); d.className="card small";
    d.innerHTML = `<strong>${c.name}</strong><div class="muted">${c.type} / cost:${c.cost||"-"}</div><div>所持:${owned}${newCards[c.id] ? ' <span class="new">NEW</span>' : ''}</div>`;
    wrap.appendChild(d);
    area.appendChild(wrap);
  });
}
function clearNewFlags(){ newCards = {}; saveAll(); renderCollectionList(); alert('NEWフラグをクリアしました'); }

/* -------------------------
   対戦開始
--------------------------*/
function startMatchWithDeck(deckList){
  player = { life:20, deck:deckList.map(id=>({id, uid:Math.random()})), hand:[], field:[], grave:[], maxMana:0, currMana:0 };
  cpu    = { life:20, deck:deckList.map(id=>({id, uid:Math.random()})), hand:[], field:[], grave:[], maxMana:0, currMana:0 };
  shuffle(player.deck); shuffle(cpu.deck);
  player.hand=[]; cpu.hand=[];
  for(let i=0;i<5;i++){ draw(player); draw(cpu); }
  globalField = null;
  playerTurn = true; attackMode = false; selectedAttacker = null; gameActive = true;
  document.getElementById("menu").style.display="none";
  document.getElementById("deckBuilder").style.display="none";
  document.getElementById("packOpener").style.display="none";
  document.getElementById("collectionPanel").style.display="none";
  document.getElementById("battleArea").style.display="block";
  startTurn(player); renderBattle();
}
function startMatchWithSavedDeck(){
  const names = Object.keys(savedDecks);
  if(names.length === 0){ alert("保存デッキがありません。デッキ構築でデッキを作成してください。"); return; }
  startMatchWithDeck(savedDecks[names[0]]);
}

/* -------------------------
   draw / shuffle
--------------------------*/
function draw(side){
  if(side.deck.length === 0) return;
  const card = side.deck.pop();
  const data = cardById(card.id);
  side.hand.push({ uid:card.uid, id:data.id, name:data.name, type:data.type, cost:data.cost||0, atk:data.atk||0, desc:data.desc||"" });
}
function shuffle(a){ for(let i=a.length-1;i>0;i--){ const j=Math.floor(Math.random()*(i+1)); [a[i],a[j]]=[a[j],a[i]]; } }

/* -------------------------
   マナロジック
   - startTurn(side) で maxMana++ (上限10) -> currMana=maxMana
--------------------------*/
function startTurn(side){
  side.maxMana = Math.min((side.maxMana||0) + 1, 10);
  side.currMana = side.maxMana;
}

/* -------------------------
   レンダリング（戦闘画面）
--------------------------*/
function renderBattle(){
  document.getElementById("playerLife").textContent = player.life;
  document.getElementById("cpuLife").textContent = cpu.life;
  document.getElementById("playerMana").textContent = player.currMana;
  document.getElementById("playerMaxMana").textContent = player.maxMana;
  document.getElementById("cpuMana").textContent = cpu.currMana;
  document.getElementById("cpuMaxMana").textContent = cpu.maxMana;

  // field card
  const fbox = document.getElementById("fieldCardBox");
  fbox.innerHTML = globalField ? `<strong>フィールド:</strong> ${globalField.name}<div class="muted">${globalField.desc}</div>` : "フィールド: なし";

  // CPU field
  const cpuF = document.getElementById("cpuField"); cpuF.innerHTML="";
  cpu.field.forEach((c, idx)=>{
    const d = document.createElement("div"); d.className = "card small";
    d.innerHTML = `${c.name}<br>ATK:${c.atk}`;
    if(attackMode && selectedAttacker && playerTurn){
      d.style.border = "2px solid #c33"; d.style.cursor = "pointer";
      d.onclick = ()=>{ playerAttackTarget(selectedAttacker, { owner: cpu, index: idx }); };
    }
    cpuF.appendChild(d);
  });

  // player field
  const plF = document.getElementById("playerField"); plF.innerHTML="";
  player.field.forEach((c, idx)=>{
    const d = document.createElement("div"); d.className="card";
    d.innerHTML = `${c.name}<br>ATK:${c.atk}`;
    if(c.canAttack && !c.hasAttacked && playerTurn){
      const btn = document.createElement("button"); btn.className="btn"; btn.textContent="攻撃";
      btn.onclick = ()=>{ // 攻撃ボタンは相手場の有無で動作を変える
        if(cpu.field.length === 0){
          // 直接攻撃
          playerAttackDirect(c);
        } else {
          enterAttackMode(c);
        }
      };
      d.appendChild(btn);
    } else {
      if(!c.canAttack){ const s=document.createElement("div"); s.className="muted"; s.textContent="(召喚酔い)"; d.appendChild(s); }
      if(c.hasAttacked){ const s=document.createElement("div"); s.className="muted"; s.textContent="(攻撃済)"; d.appendChild(s); }
    }
    plF.appendChild(d);
  });

  // player hand
  const ph = document.getElementById("playerHand"); ph.innerHTML="";
  player.hand.forEach((c, idx)=>{
    const d = document.createElement("div"); d.className="card";
    d.innerHTML = `<strong>${c.name}</strong><div class="muted">${c.type} / cost:${c.cost}</div><div style="font-size:12px">${c.desc||""}</div><div class="statusSmall">現在マナ: ${player.currMana}</div>`;
    d.onclick = ()=>{ playCardFromHand(idx); };
    ph.appendChild(d);
  });

  document.getElementById("modeHint").textContent = attackMode ? "攻撃モード: 相手モンスターをクリック" : "";
  checkWinSilent();
}

/* -------------------------
   手札からカードプレイ（マナ消費チェック）
--------------------------*/
function playCardFromHand(idx){
  if(!playerTurn){ alert("自分のターンではありません"); return; }
  const card = player.hand[idx];
  if(player.currMana < card.cost){ alert("マナが足りません"); return; }

  player.currMana -= card.cost;

  if(card.type === "monster"){
    player.field.push({ uid:card.uid, id:card.id, name:card.name, atk:card.atk, canAttack:false, hasAttacked:false });
    // スライムの召喚効果：デッキにスライムがいれば1枚手札へ（デッキから引く）
    if(card.id === "slime"){
      const sIdx = player.deck.findIndex(x=>x.id==="slime");
      if(sIdx >= 0){
        const cc = player.deck.splice(sIdx,1)[0];
        const data = cardById(cc.id);
        player.hand.push({ uid:cc.uid, id:data.id, name:data.name, type:data.type, cost:data.cost||0, atk:data.atk||0, desc:data.desc||"" });
      }
    }
  } else if(card.type === "spell"){
    resolveSpell(card, true);
    player.grave.push({id:card.id, name:card.name});
  } else if(card.type === "field"){
    if(globalField) player.grave.push({id:globalField.id, name:globalField.name});
    globalField = {id:card.id, name:card.name, desc:card.desc};
  }
  player.hand.splice(idx,1);
  renderBattle();
}

/* -------------------------
   spell 解決
--------------------------*/
function resolveSpell(card, isPlayer){
  const me = isPlayer ? player : cpu;
  const opp = isPlayer ? cpu : player;
  if(card.id === "heal"){ me.life += 3; }
  if(card.id === "sacrifice"){
    if(me.field.length > 0){
      const m = me.field.pop();
      me.grave.push({id:m.id, name:m.name});
      opp.life -= m.atk;
    }
  }
  if(card.id === "thunder"){ opp.life -= 2; }
  if(card.id === "relic"){
    if(me.grave.length > 0){
      const idx = Math.floor(Math.random()*me.grave.length);
      const g = me.grave.splice(idx,1)[0];
      const data = cardById(g.id);
      me.hand.push({ uid:Math.random(), id:data.id, name:data.name, type:data.type, cost:data.cost||0, atk:data.atk||0, desc:data.desc||"" });
    }
  }
  renderBattle();
}

/* -------------------------
   攻撃モード / 攻撃処理（モンスター攻撃 / 直接攻撃）
--------------------------*/
function attackModeToggle(){ attackMode = !attackMode; selectedAttacker = null; renderBattle(); }
function enterAttackMode(attacker){
  if(!playerTurn){ alert("自分のターンではありません"); return; }
  if(!attacker.canAttack || attacker.hasAttacked){ alert("このモンスターは攻撃できません"); return; }
  attackMode = true; selectedAttacker = attacker;
  renderBattle();
}
function playerAttackTarget(attacker, targetRef){
  const attackerIndex = player.field.indexOf(attacker);
  if(attackerIndex < 0){ attackMode=false; selectedAttacker=null; renderBattle(); return; }
  const defender = cpu.field[targetRef.index];
  // 呪術師チェック（相手の呪術師がいる場合、相手モンスター効果は無効 -> ここではエンド効果や召喚効果に影響）
  const opponentHasJyujutsu = cpu.field.some(x=>x.id==="jyujutsushi");
  // resolve battle (単純なATK比較：勝ち→破壊、引き分け→両方破壊)
  if(attacker.atk > defender.atk){
    cpu.grave.push({id:defender.id, name:defender.name});
    cpu.field.splice(targetRef.index,1);
  } else if(attacker.atk < defender.atk){
    player.grave.push({id:attacker.id, name:attacker.name});
    player.field.splice(attackerIndex,1);
  } else {
    cpu.grave.push({id:defender.id, name:defender.name});
    player.grave.push({id:attacker.id, name:attacker.name});
    cpu.field.splice(targetRef.index,1);
    const idx = player.field.indexOf(attacker); if(idx>=0) player.field.splice(idx,1);
  }
  attacker.hasAttacked = true;
  attackMode=false; selectedAttacker=null;
  checkWin();
  renderBattle();
}
// 直接攻撃（相手場が空のときのみ）
function playerAttackDirect(attacker){
  if(!playerTurn) return;
  if(cpu.field.length > 0) { alert("相手にモンスターがいるため直接攻撃はできません"); return; }
  cpu.life -= attacker.atk;
  attacker.hasAttacked = true;
  attackMode = false; selectedAttacker = null;
  checkWin();
  renderBattle();
}

/* -------------------------
   ターン処理（endTurn -> CPU処理 -> 戻る）
--------------------------*/
function endTurn(){
  if(!gameActive) return;
  // player end-phase effects
  triggerEndPhaseEffects(true);
  // mark: player's monsters that attacked keep hasAttacked until next player start
  playerTurn = false;
  attackMode = false; selectedAttacker = null;
  renderBattle();
  setTimeout(()=>{ cpuTurn(); }, 400);
}

function cpuTurn(){
  if(!gameActive) return;
  // CPU start-turn: mana inc & draw
  startTurn(cpu); draw(cpu);
  // CPU play: try to play best available (monster > field > spell) once
  for(let i=0;i<cpu.hand.length;i++){
    const c = cpu.hand[i];
    if(c.cost <= cpu.currMana){
      if(c.type === "monster"){
        cpu.currMana -= c.cost;
        cpu.field.push({ uid:c.uid, id:c.id, name:c.name, atk:c.atk, canAttack:false, hasAttacked:false });
        cpu.hand.splice(i,1);
        if(c.id === "slime"){
          const si = cpu.deck.findIndex(x=>x.id==="slime");
          if(si>=0){
            const cc = cpu.deck.splice(si,1)[0];
            const data = cardById(cc.id);
            cpu.hand.push({ uid:cc.uid, id:data.id, name:data.name, type:data.type, cost:data.cost||0, atk:data.atk||0, desc:data.desc||"" });
          }
        }
        break;
      } else if(c.type === "field"){
        cpu.currMana -= c.cost;
        if(globalField) cpu.grave.push({id:globalField.id,name:globalField.name});
        globalField = { id:c.id, name:c.name, desc:c.desc };
        cpu.hand.splice(i,1);
        break;
      } else if(c.type === "spell"){
        if(c.id === "thunder" || c.id === "relic"){
          cpu.currMana -= c.cost;
          resolveSpell(c, false);
          cpu.grave.push({id:c.id, name:c.name});
          cpu.hand.splice(i,1);
          break;
        }
      }
    }
  }

  // CPU attacks
  cpu.field.forEach(m=>{ m.canAttack = true; m.hasAttacked = false; });
  for(let i=0;i<cpu.field.length;i++){
    const attacker = cpu.field[i];
    if(!attacker.canAttack || attacker.hasAttacked) continue;
    if(player.field.length > 0){
      const idx = Math.floor(Math.random()*player.field.length);
      const defender = player.field[idx];
      if(attacker.atk > defender.atk){
        player.grave.push({id:defender.id, name:defender.name});
        player.field.splice(idx,1);
      } else if(attacker.atk < defender.atk){
        cpu.grave.push({id:attacker.id, name:attacker.name});
        cpu.field.splice(i,1);
      } else {
        player.grave.push({id:defender.id, name:defender.name});
        cpu.grave.push({id:attacker.id, name:attacker.name});
        player.field.splice(idx,1);
        cpu.field.splice(i,1);
      }
    } else {
      player.life -= attacker.atk;
    }
    attacker.hasAttacked = true;
    if(checkWin()) return;
  }

  // CPU end-phase
  triggerEndPhaseEffects(false);

  // prepare player next turn
  startTurn(player); draw(player);
  player.field.forEach(m=>{ m.canAttack = true; m.hasAttacked = false; });
  cpu.field.forEach(m=>{ m.canAttack = true; m.hasAttacked = false; });

  playerTurn = true;
  renderBattle();
}

/* -------------------------
   エンドフェイズ効果（モンスター・フィールド）
--------------------------*/
function triggerEndPhaseEffects(isPlayer){
  const me = isPlayer ? player : cpu;
  const opp = isPlayer ? cpu : player;
  const oppHasJyujutsu = opp.field.some(x=>x.id==="jyujutsushi");

  const copies = me.field.slice();
  copies.forEach(m=>{
    if(m.id === "kijin" && !oppHasJyujutsu){
      if(opp.field.length > 0){
        const idx = Math.floor(Math.random()*opp.field.length);
        const removed = opp.field.splice(idx,1)[0];
        opp.grave.push({id:removed.id, name:removed.name});
      }
    }
    if(m.id === "necromancer" && !oppHasJyujutsu){
      const monsIdx = me.grave.findIndex(g=>{
        const cd = cardById(g.id);
        return cd && cd.type === "monster";
      });
      if(monsIdx >= 0 && me.field.length < 5){
        const g = me.grave.splice(monsIdx,1)[0];
        const data = cardById(g.id);
        me.field.push({ uid:Math.random(), id:data.id, name:data.name, atk:data.atk, canAttack:false, hasAttacked:false });
      }
    }
  });

  if(globalField){
    if(globalField.id === "happy"){
      draw(player); draw(cpu);
    }
    if(globalField.id === "forest"){
      const candidates = [];
      if(player.grave.length>0) candidates.push(player);
      if(cpu.grave.length>0) candidates.push(cpu);
      if(candidates.length>0){
        const pick = candidates[Math.floor(Math.random()*candidates.length)];
        const idx = Math.floor(Math.random()*pick.grave.length);
        const g = pick.grave.splice(idx,1)[0];
        const data = cardById(g.id);
        pick.hand.push({ uid:Math.random(), id:data.id, name:data.name, type:data.type, cost:data.cost||0, atk:data.atk||0, desc:data.desc||"" });
      }
    }
  }
  renderBattle();
}

/* -------------------------
   勝敗判定 / モーダル
--------------------------*/
function checkWinSilent(){
  if(player.life <= 0 || cpu.life <= 0){ showEndModal(); return true; } return false;
}
function checkWin(){
  if(player.life <= 0){ showEndModal(false); return true; }
  if(cpu.life <= 0){
    packCount++; saveAll(); updateTopCounts();
    showEndModal(true); return true;
  }
  return false;
}
function showEndModal(playerWon){
  gameActive = false;
  const modal = document.getElementById("modal"); const box = document.getElementById("modalBox");
  modal.style.display = "flex";
  if(playerWon === undefined){
    box.innerHTML = `<h3>ゲーム終了</h3><div class="muted">どちらかのライフが0になりました。</div><div style="margin-top:12px"><button class="btn primary" onclick="closeModalAndReturn()">タイトルへ戻る</button></div>`;
  } else if(playerWon){
    box.innerHTML = `<h3>あなたの勝利！</h3><div class="muted">勝利報酬: パックを1つ獲得しました。</div>
      <div style="margin-top:12px"><button class="btn" onclick="rematch()">再戦</button><button class="btn" onclick="closeModalAndReturn()">タイトルへ戻る</button></div>`;
  } else {
    box.innerHTML = `<h3>あなたの敗北...</h3><div style="margin-top:12px"><button class="btn" onclick="rematch()">再戦</button><button class="btn" onclick="closeModalAndReturn()">タイトルへ戻る</button></div>`;
  }
}
function rematch(){
  closeModal();
  if(Object.keys(savedDecks).length>0){ const n=Object.keys(savedDecks)[0]; startMatchWithDeck(savedDecks[n]); }
  else startQuickMatch();
}
function closeModalAndReturn(){
  closeModal();
  document.getElementById("battleArea").style.display = "none";
  document.getElementById("menu").style.display = "flex";
  gameActive = false;
}
function closeModal(){ document.getElementById("modal").style.display = "none"; }

/* -------------------------
   降参 / デバッグ
--------------------------*/
function surrender(){
  if(!confirm("本当に降参しますか？")) return;
  saveAll(); updateTopCounts();
  showEndModal(false);
}
function giveDebugPack(){ packCount++; saveAll(); updateTopCounts(); alert("パックを1つ獲得しました"); }

/* -------------------------
   quick match & reset
--------------------------*/
function startQuickMatch(){
  if(Object.keys(collection).length===0) ensureInitialPacks();
  const deck = [];
  for(const c of ALL_CARDS){
    const own = collection[c.id]||0;
    const add = Math.min(4, own);
    for(let i=0;i<add && deck.length<30;i++) deck.push(c.id);
  }
  while(deck.length<30) deck.push("slime");
  currentDeck = deck.slice();
  startMatchWithDeck(currentDeck);
}
function resetAll(){
  if(!confirm("セーブを初期化しますか？")) return;
  localStorage.removeItem(KEY_COLLECTION); localStorage.removeItem(KEY_PACKS);
  localStorage.removeItem(KEY_SHARDS); localStorage.removeItem(KEY_DECKS); localStorage.removeItem(KEY_NEW);
  collection={}; packCount=0; shardCount=0; savedDecks={}; currentDeck=[]; newCards={};
  ensureInitialPacks();
  alert("初期化しました。ページを再読み込みしてください。");
}

/* -------------------------
   pack helper wrappers
--------------------------*/
function openPackManualUI(){ if(packCount<=0){ alert("パックがありません"); return; } packCount--; saveAll(); updateTopCounts(); const res=openPackInternal(false); showPackResultOnPage(res); }
function openPackOpener(){ document.getElementById("menu").style.display="none"; document.getElementById("packOpener").style.display="block"; document.getElementById("packResult").innerHTML=""; }
function closePackOpener(){ document.getElementById("packOpener").style.display="none"; document.getElementById("menu").style.display="flex"; }

/* -------------------------
   misc helpers
--------------------------*/
function cardById(id){ return ALL_CARDS.find(x=>x.id===id) || null; }
function draw(side){ if(side.deck.length===0) return; const card = side.deck.pop(); const data = cardById(card.id); side.hand.push({ uid:card.uid, id:data.id, name:data.name, type:data.type, cost:data.cost||0, atk:data.atk||0, desc:data.desc||"" }); }
function shuffle(a){ for(let i=a.length-1;i>0;i--){ const j=Math.floor(Math.random()*(i+1)); [a[i],a[j]]=[a[j],a[i]]; } }

/* -------------------------
   起動時バインド
--------------------------*/
document.addEventListener("DOMContentLoaded",()=>{
  loadAll();
  ensureInitialPacks();
  updateTopCounts();
  // exports for UI
  window.openDeckBuilder = openDeckBuilder;
  window.closeDeckBuilder = closeDeckBuilder;
  window.openPackOpener = openPackOpener;
  window.closePackOpener = closePackOpener;
  window.openPackManual = openPackManualUI;
  window.exchangeShards = exchangeShards;
  window.openCollection = openCollection;
  window.closeCollection = closeCollection;
  window.startQuickMatch = startQuickMatch;
  window.startMatchWithDeck = startMatchWithDeck;
  window.saveDeckAndStart = saveDeckAndStart;
  window.openPackManual = openPackManualUI;
});
</script>

</body>
</html>
