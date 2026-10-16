<html lang="en"><head><meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<style>
:root{--bg:#f6f4ef;--card:#fff;--tx:#1b1b1f;--mu:#6b6b75;--bd:#dcd8cf;--ac:#b8860b;--acbg:#fbf1d6;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#121214;--card:#1c1c20;--tx:#f0eee8;--mu:#9a9aa5;--bd:#33333a;--ac:#e5b94a;--acbg:#3a3015}}
:root[data-theme="dark"]{--bg:#121214;--card:#1c1c20;--tx:#f0eee8;--mu:#9a9aa5;--bd:#33333a;--ac:#e5b94a;--acbg:#3a3015;color-scheme:dark}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--tx);font:16px/1.45 system-ui,-apple-system,"Segoe UI",sans-serif}
header{max-width:900px;margin:0 auto;padding:28px 16px 8px}
h1{margin:0 0 4px;font-size:1.6rem}
.sub{color:var(--mu);margin:0 0 14px;font-size:.92rem}
.bar{position:sticky;top:env(safe-area-inset-top,0px);background:var(--bg);z-index:5;padding:8px 0;display:flex;gap:8px;flex-wrap:wrap;align-items:center}
.prog{flex:1;min-width:140px;font-size:.85rem;color:var(--mu)}
.prog i{display:block;height:6px;border-radius:3px;background:var(--bd);margin-top:4px;overflow:hidden}
.prog b{display:block;height:100%;background:var(--ac);width:0}
button,input{font:inherit;color:var(--tx)}
button{background:var(--card);border:1px solid var(--bd);border-radius:8px;padding:7px 12px;cursor:pointer}
button.p{background:var(--ac);border-color:var(--ac);color:#111}
input{background:var(--card);border:1px solid var(--bd);border-radius:8px;padding:7px 10px;min-width:0}
main{max-width:900px;margin:0 auto;padding:0 16px 40px;display:grid;gap:12px}
details{background:var(--card);border:1px solid var(--bd);border-radius:12px}
summary{cursor:pointer;padding:12px 14px;display:flex;justify-content:space-between;gap:8px;font-weight:600;list-style:none}
summary::-webkit-details-marker{display:none}
.cnt{font-weight:400;font-size:.85rem;color:var(--mu);white-space:nowrap}
.cnt.full{color:var(--ac);font-weight:600}
.chips{display:flex;flex-wrap:wrap;gap:6px;padding:0 14px 14px}
.add{display:flex;gap:6px;margin:0 0 12px}.add input{flex:1}
.chip{border-radius:999px;padding:5px 12px;font-size:.9rem}
.chip[aria-pressed=true]{background:var(--acbg);border-color:var(--ac);font-weight:600}
.chip:disabled{opacity:.4;cursor:not-allowed}
.ac{position:relative;flex:1;min-width:200px}.ac input{width:100%}.ac ul{display:none;position:absolute;left:0;right:0;top:100%;z-index:9;margin:4px 0 0;padding:4px;list-style:none;background:var(--card);border:1px solid var(--bd);border-radius:8px;box-shadow:0 6px 18px #0003;max-height:260px;overflow:auto}.ac li{padding:7px 10px;border-radius:6px;cursor:pointer}.ac li.on,.ac li:hover{background:var(--acbg)}
pre{white-space:pre-wrap;background:var(--card);color:var(--tx);border:1px solid var(--bd);border-radius:10px;padding:12px;font:.85rem/1.5 ui-monospace,monospace;display:none;margin:0}
</style></head><body>
<header>
<h1>🏆 The Game Awards 2026 — Nominee Predictor</h1>
<p class="sub">Type in each category to autocomplete from 2026 releases scoring above 80 on OpenCritic (snapshot Oct 15, 2026; DLC left out). Any other title can be entered as free text. Ceremony: Dec 10, 2026 · nominees expected mid-November. Categories mirror 2025's; the official 2026 list isn't out yet.</p>
<div class="add"><input id="cg" placeholder="Missing a game? Add it here…"><button id="ab">Add game</button></div>
<div class="bar"><div class="prog"><span id="pt"></span><i><b id="pb"></b></i></div>
<button id="ex">Export picks</button><button id="rs">Reset</button></div>
</header>
<main id="m"></main>
<main><pre id="out"></pre></main>
<script>
const GAMES='Mythmatch|Trails in the Sky 2nd Chapter|Dave the Diver: In the Jungle|Mina the Hollower|Forza Horizon 6|Valheim|Schrödinger\'s Call|Lost and Found Co.|Pokémon Pokopia|Fire Emblem: Fortune\'s Weave|Resident Evil Requiem|Big Walk|Elden Ring: Tarnished Edition|Mewgenics|Hermit and Pig|Desktop Explorer|Sovereign Tower|Esoteric Ebb|TetherGeist|Schrödinger\'s Cat Burglar|007 First Light|Ace Combat 8: Wings of Theve|Denshattack!|Devil May Cry 5: Devil Hunter Edition|Star Wars: Galactic Racer|Opus: Prism Peak|Rhell: Warped Worlds & Troubled Times|Dying Light: The Beast Restored Land|Endless Legend 2|Saros|Well Dweller|Super Mario Bros. Wonder – Switch 2 Edition|Onimusha: Way of the Sword|Silver Pines|Cult of the Lamb: Woolhaven|Pragmata|Pieced Together|Servant of the Lake|The Mermaid Mask|Cairn|Demon Tides|Tombwater|Gears of War: E-Day|Super Bomberman Collection|ReStory: Chill Electronics Repairs|Elementallis|Castlevania: Belmont\'s Curse|Nioh 3|Shards of Order|Dragon\'s Dogma 2: Dark Arisen|Marvel Tokon: Fighting Souls|Monster Hunter Stories 3: Twisted Reflection|TerraTech Legion|Wax Heads|Lost Castle 2|Titanium Court|Assassin\'s Creed: Black Flag Resynced|Warhammer 40,000: Boltgun 2|Truxton Extreme|The Blood of Dawnwalker|Vampire Crawlers|PARANORMASIGHT: The Mermaid\'s Curse|The Legend of Heroes: Trails Beyond the Horizon|Rhythm Heaven Groove|MIO: Memories in Orbit|Coffee Talk Tokyo|ShantyTown|Heave Ho 2|Twisted Tower|MONOWAVE|Dressmaker|TOEM 2|Control Resonant|Tormentum II|Order of the Sinking Star|Planet Zoo 2|DragonSword: Awakening|Neva: Prologue|Planet of Lana II: Children of the Leaf|Moomintroll: Winter\'s Warmth|Grime II|Minos|Lovish|FZ: Formation Z|Corsair Cove|Splatoon Raiders|KuloNiku: Bowl Up!|The Perfect Pencil|Raccoin: Coin Pusher Roguelike|Find Your Words|Farlands|Star Fox|Transport Fever 3|TR-49|Birushana: Winds of Fate|Resonance: A Plague Tale Legacy|Lunarium|Halo: Campaign Evolved|Psyvariar 3|Woodo|Temirana: The Lucky Princess and the Tragic Knights|EA Sports UFC 6|Gurei|Marsupilami 2: Salsa Palombia|Nighthawks|Phonopolis|Luna Abyss|Battlestar Galactica: Scattered Hopes|MOUSE: P.I. For Hire|Black Jacket|Vultures - Scavengers of Death|Marathon|HellSlave II: Judgment of the Archon|Graveyard Keeper 2|Silent Hill: Townfall|Ascend to Zero|Aether & Iron'.split('|');
const CATS=[["Game of the Year",6],["Best Game Direction"],["Best Narrative"],["Best Art Direction"],["Best Score & Music"],["Best Audio Design"],["Best Performance"],["Games for Impact"],["Best Ongoing Game"],["Best Community Support"],["Best Independent Game"],["Best Debut Indie Game"],["Best Mobile Game"],["Best VR/AR Game"],["Best Action Game"],["Best Action/Adventure Game"],["Best RPG"],["Best Fighting Game"],["Best Family Game"],["Best Sim/Strategy Game"],["Best Sports/Racing Game"],["Best Multiplayer Game"],["Best Adaptation"],["Most Anticipated Game"],["Best Esports Game"]].map(c=>({n:c[0],max:c[1]||5}));
const K="tga26";let S={picks:{},custom:[]};
try{const r=localStorage.getItem(K);if(r)S=JSON.parse(r)}catch(e){}
const save=()=>{try{localStorage.setItem(K,JSON.stringify(S))}catch(e){}};
const all=()=>[...GAMES,...S.custom];
const m=document.getElementById("m");
const norm=t=>t.normalize("NFD").replace(/[\u0300-\u036f]/g,"").toLowerCase();
function render(){
 const open=[...m.querySelectorAll("details[open]")].map(d=>d.dataset.n);
 m.innerHTML="";let done=0;
 CATS.forEach(c=>{
  const p=S.picks[c.n]||[];if(p.length)done++;
  const d=document.createElement("details");d.dataset.n=c.n;if(open.includes(c.n))d.open=true;
  d.innerHTML=`<summary><span>${c.n}</span><span class="cnt ${p.length==c.max?"full":""}">${p.length}/${c.max}</span></summary>`;
  const w=document.createElement("div");w.className="chips";
  p.forEach(g=>{const b=document.createElement("button");b.className="chip";b.setAttribute("aria-pressed","true");b.textContent=g+" ✕";
   b.onclick=()=>{S.picks[c.n]=p.filter(x=>x!==g);save();render()};w.appendChild(b)});
  if(p.length<c.max){
   const bx=document.createElement("div");bx.className="ac";
   bx.innerHTML='<input placeholder="Type a game…" autocomplete="off"><ul></ul>';
   const inp=bx.firstChild,ul=bx.lastChild;let idx=-1,items=[];
   const add=g=>{g=g.trim();if(!g)return;const a=S.picks[c.n]||[];
    if(a.length<c.max&&!a.some(x=>norm(x)===norm(g))){S.picks[c.n]=[...a,GAMES.concat(S.custom).find(x=>norm(x)===norm(g))||g];
     if(!all().some(x=>norm(x)===norm(g)))S.custom.push(g);save();render();
     const dd=m.querySelector(`details[data-n="${c.n}"] input`);dd&&dd.focus()}};
   const show=()=>{const q=norm(inp.value.trim()),a=S.picks[c.n]||[];
    items=all().filter(g=>!a.includes(g)&&(!q||norm(g).includes(q))).sort((x,y)=>(norm(y).startsWith(q)-norm(x).startsWith(q))).slice(0,8);
    idx=-1;ul.innerHTML="";items.forEach((g,k)=>{const li=document.createElement("li");li.textContent=g;li.onmousedown=e=>{e.preventDefault();add(g)};ul.appendChild(li)});
    ul.style.display=items.length?"block":"none"};
   const hl=()=>[...ul.children].forEach((l,k)=>l.classList.toggle("on",k==idx));
   inp.oninput=show;inp.onfocus=show;inp.onblur=()=>ul.style.display="none";
   inp.onkeydown=e=>{if(e.key==="ArrowDown"){idx=Math.min(idx+1,items.length-1);hl();e.preventDefault()}
    else if(e.key==="ArrowUp"){idx=Math.max(idx-1,0);hl();e.preventDefault()}
    else if(e.key==="Enter"){add(idx>=0?items[idx]:(items[0]&&norm(items[0])===norm(inp.value.trim())?items[0]:inp.value));e.preventDefault()}};
   w.appendChild(bx)}
  d.appendChild(w);m.appendChild(d)});
 document.getElementById("pt").textContent=`${done} of ${CATS.length} categories filled`;
 document.getElementById("pb").style.width=(done/CATS.length*100)+"%";
}
document.getElementById("ab").onclick=()=>{
 const i=document.getElementById("cg"),v=i.value.trim();
 if(v&&!all().some(g=>norm(g)===norm(v))){S.custom.push(v);save();render()}i.value=""};
document.getElementById("cg").onkeydown=e=>{if(e.key==="Enter")document.getElementById("ab").click()};
document.getElementById("rs").onclick=()=>{if(confirm("Clear all picks?")){S={picks:{},custom:S.custom};save();render()}};
document.getElementById("ex").onclick=()=>{
 const t="My TGA 2026 nominee predictions\n\n"+CATS.map(c=>`${c.n}:\n`+((S.picks[c.n]||[]).map(g=>"  • "+g).join("\n")||"  —")).join("\n\n");
 const o=document.getElementById("out");o.style.display="block";o.textContent=t;
 try{navigator.clipboard.writeText(t)}catch(e){}
 o.scrollIntoView({behavior:"smooth"})};
render();
</script></body></html>
