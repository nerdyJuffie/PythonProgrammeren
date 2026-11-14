---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# Parsons Problems: /, // en %

In de vorige les heb je geleerd hoe je kunt delen met `/`, `//` en `%`. Nu ga je oefenen met **Parsons Problems**: je krijgt de juiste regels code, maar die staan door elkaar. Sommige regels horen er zelfs helemaal niet bij!

## Zo werkt het

1. **Klik op een regel** (of sleep hem) om hem naar jouw programma te verplaatsen. Klik nogmaals om hem terug te zetten.
2. Gebruik de pijltjes ▲ ▼ om de volgorde aan te passen.
3. Klik op **Controleer**. Je krijgt een hint als er iets niet klopt.
4. Gebruik **Opnieuw** om een nieuwe, door elkaar gehusselde reeks te krijgen.

```{admonition} Denk eraan
:class: tip
- `/` geeft een getal **met decimalen** (`7 / 2 = 3.5`)
- `//` geeft **hoe vaak het past** (`7 // 2 = 3`)
- `%` geeft **wat er overblijft** (`7 % 2 = 1`)
- Python voert regels uit **van boven naar beneden**: een variabele moet eerst bestaan voordat je hem gebruikt.
```

## Opdrachten

```{raw} html
<style>
.pp-wrap{margin:1.5em 0;padding:1em 1.2em;border:1px solid var(--pst-color-border,#bbb);border-radius:10px;background:var(--pst-color-surface,rgba(127,127,127,.06));}
.pp-wrap h4{margin:.1em 0 .4em;}
.pp-cols{display:grid;grid-template-columns:1fr 1fr;gap:1em;}
@media (max-width:700px){.pp-cols{grid-template-columns:1fr;}}
.pp-col-title{font-weight:600;font-size:.85em;margin-bottom:.4em;opacity:.8;}
.pp-list{min-height:70px;padding:.5em;border:2px dashed var(--pst-color-border,#aaa);border-radius:8px;display:flex;flex-direction:column;gap:6px;}
.pp-list.over{border-color:var(--pst-color-primary,#0a6cff);background:rgba(10,108,255,.07);}
.pp-block{display:flex;align-items:center;gap:6px;padding:6px 8px;border:1px solid var(--pst-color-border,#999);border-radius:6px;background:var(--pst-color-background,#fff);color:var(--pst-color-text-base,inherit);font-family:var(--pst-font-family-monospace,monospace);font-size:.88em;cursor:grab;text-align:left;}
.pp-block .txt{flex:1;white-space:pre-wrap;word-break:break-word;background:none;border:0;padding:0;font:inherit;color:inherit;text-align:left;cursor:pointer;}
.pp-block.dragging{opacity:.4;}
.pp-block.bad{border-color:#d33;background:rgba(220,50,50,.15);}
.pp-block.good{border-color:#2a9d4a;background:rgba(40,160,80,.15);}
.pp-mv{border:1px solid var(--pst-color-border,#999);background:none;color:inherit;border-radius:4px;cursor:pointer;padding:0 6px;line-height:1.5;}
.pp-mv:hover{background:rgba(127,127,127,.2);}
.pp-bar{margin-top:.8em;display:flex;gap:8px;flex-wrap:wrap;align-items:center;}
.pp-btn{padding:6px 14px;border-radius:6px;border:1px solid var(--pst-color-primary,#0a6cff);background:var(--pst-color-primary,#0a6cff);color:#fff;cursor:pointer;font-size:.9em;}
.pp-btn.sec{background:none;color:var(--pst-color-primary,#0a6cff);}
.pp-fb{margin-top:.7em;padding:.6em .8em;border-radius:6px;display:none;}
.pp-fb.ok{display:block;background:rgba(40,160,80,.15);border-left:4px solid #2a9d4a;}
.pp-fb.err{display:block;background:rgba(220,50,50,.12);border-left:4px solid #d33;}
.pp-out{margin-top:.5em;padding:.5em .8em;border-radius:6px;background:#1e1e1e;color:#e6e6e6;font-family:var(--pst-font-family-monospace,monospace);font-size:.85em;white-space:pre-wrap;}
.pp-empty{opacity:.55;font-size:.85em;font-style:italic;}
</style>
<div id="pp-root"></div>
<script>
(function(){
var PROBLEMS=[
{title:"Parsons 1: Eitjes",intro:"Je hebt 34 eieren en in een doosje passen 6 eieren. Zet de regels in de juiste volgorde, zodat het programma de volle doosjes en de overgebleven eieren print. <strong>Let op:</strong> er staan regels tussen die niet kloppen!",
 blocks:[
 {id:"a",t:'eieren = 34',needs:[]},
 {id:"b",t:'doosjes = eieren // 6',needs:["a"]},
 {id:"c",t:'over = eieren % 6',needs:["a"]},
 {id:"d",t:'print("Aantal volle doosjes:", doosjes)',needs:["b"]},
 {id:"e",t:'print("Eieren over:", over)',needs:["c"]},
 {id:"x1",t:'doosjes = eieren / 6',distract:"/ geeft een kommagetal (5.666...), geen aantal volle doosjes."},
 {id:"x2",t:'over = eieren // 6',distract:"// geeft het aantal volle doosjes, niet wat er overblijft."}],
 out:"Aantal volle doosjes: 5\nEieren over: 4"},
{title:"Parsons 2: Tijd",intro:"Een evenement duurt 130 minuten. Maak het programma dat uren en resterende minuten print.",
 blocks:[
 {id:"a",t:'totaal_minuten = 130',needs:[]},
 {id:"b",t:'uren = totaal_minuten // 60',needs:["a"]},
 {id:"c",t:'minuten_over = totaal_minuten % 60',needs:["a"]},
 {id:"d",t:'print("Het duurt", uren, "uur en", minuten_over, "minuten.")',needs:["b","c"]},
 {id:"x1",t:'uren = totaal_minuten / 60',distract:"/ geeft 2.1666... uur, geen hele uren."},
 {id:"x2",t:'minuten_over = totaal_minuten // 60',distract:"// berekent de hele uren, niet de resterende minuten."}],
 out:"Het duurt 2 uur en 10 minuten."},
{title:"Parsons 3: Snoepjes verdelen",intro:"Je verdeelt 47 snoepjes eerlijk over 5 kinderen. Hoeveel krijgt ieder kind en hoeveel blijven er over?",
 blocks:[
 {id:"a",t:'snoepjes = 47',needs:[]},
 {id:"b",t:'kinderen = 5',needs:[]},
 {id:"c",t:'per_kind = snoepjes // kinderen',needs:["a","b"]},
 {id:"d",t:'rest = snoepjes % kinderen',needs:["a","b"]},
 {id:"e",t:'print("Elk kind krijgt", per_kind, "snoepjes.")',needs:["c"]},
 {id:"f",t:'print("Er blijven", rest, "snoepjes over.")',needs:["d"]},
 {id:"x1",t:'per_kind = snoepjes / kinderen',distract:"/ geeft 9.4, maar je kunt geen stukje snoep uitdelen."},
 {id:"x2",t:'rest = snoepjes // kinderen',distract:"// geeft het aantal per kind, niet de rest."}],
 out:"Elk kind krijgt 9 snoepjes.\nEr blijven 2 snoepjes over."},
{title:"Parsons 4 (uitdaging): Cijfers van een getal",intro:"Splits het getal 73 in tientallen en eenheden en tel ze op. Hint: delen door 10 en de rest bij delen door 10.",
 blocks:[
 {id:"a",t:'getal = 73',needs:[]},
 {id:"b",t:'tientallen = getal // 10',needs:["a"]},
 {id:"c",t:'eenheden = getal % 10',needs:["a"]},
 {id:"d",t:'som = tientallen + eenheden',needs:["b","c"]},
 {id:"e",t:'print("Tientallen:", tientallen)',needs:["b"]},
 {id:"f",t:'print("Eenheden:", eenheden)',needs:["c"]},
 {id:"g",t:'print("Som van de cijfers:", som)',needs:["d"]},
 {id:"x1",t:'tientallen = getal / 10',distract:"/ geeft 7.3, niet alleen het aantal tientallen."},
 {id:"x2",t:'eenheden = getal // 10',distract:"// geeft de tientallen, niet de eenheden."},
 {id:"x3",t:'som = tientallen * eenheden',distract:"Je moet de cijfers optellen (+), niet vermenigvuldigen (*)."}],
 out:"Tientallen: 7\nEenheden: 3\nSom van de cijfers: 10"}
];
function shuffle(a){a=a.slice();for(var i=a.length-1;i>0;i--){var j=Math.floor(Math.random()*(i+1));var t=a[i];a[i]=a[j];a[j]=t;}return a;}
function mk(tag,cls,txt){var e=document.createElement(tag);if(cls)e.className=cls;if(txt!==undefined)e.textContent=txt;return e;}
var root=document.getElementById("pp-root");
PROBLEMS.forEach(function(P){
 var byId={};P.blocks.forEach(function(b){byId[b.id]=b;});
 var pool=shuffle(P.blocks.map(function(b){return b.id;})),sol=[],drag=null;
 var wrap=mk("div","pp-wrap");
 wrap.appendChild(mk("h4","",P.title));
 var p=mk("p");p.innerHTML=P.intro;wrap.appendChild(p);
 var cols=mk("div","pp-cols"),cA=mk("div"),cB=mk("div");
 cA.appendChild(mk("div","pp-col-title","Beschikbare regels (klik of sleep)"));
 cB.appendChild(mk("div","pp-col-title","Jouw programma (van boven naar beneden)"));
 var lA=mk("div","pp-list"),lB=mk("div","pp-list");
 cA.appendChild(lA);cB.appendChild(lB);cols.appendChild(cA);cols.appendChild(cB);wrap.appendChild(cols);
 var bar=mk("div","pp-bar"),bC=mk("button","pp-btn","Controleer"),bR=mk("button","pp-btn sec","Opnieuw");
 bC.type=bR.type="button";bar.appendChild(bC);bar.appendChild(bR);wrap.appendChild(bar);
 var fb=mk("div","pp-fb");wrap.appendChild(fb);
 var marks={};
 function move(id,to,idx){
  pool=pool.filter(function(x){return x!==id;});sol=sol.filter(function(x){return x!==id;});
  if(to==="sol"){if(idx===undefined||idx>sol.length)idx=sol.length;sol.splice(idx,0,id);}else pool.push(id);
  marks={};fb.className="pp-fb";fb.innerHTML="";render();
 }
 function block(id,inSol){
  var b=mk("div","pp-block"+(marks[id]?" "+marks[id]:""));b.draggable=true;b.dataset.id=id;
  var t=mk("button","txt",byId[id].t);t.type="button";
  t.title=inSol?"Klik om terug te zetten":"Klik om toe te voegen";
  t.onclick=function(){move(id,inSol?"pool":"sol");};
  b.appendChild(t);
  if(inSol){
   var i=sol.indexOf(id);
   [["▲",-1,"Omhoog"],["▼",1,"Omlaag"]].forEach(function(m){
    var bt=mk("button","pp-mv",m[0]);bt.type="button";bt.setAttribute("aria-label",m[2]);
    bt.onclick=function(){var j=i+m[1];if(j<0||j>=sol.length)return;sol.splice(i,1);sol.splice(j,0,id);marks={};fb.className="pp-fb";render();};
    b.appendChild(bt);});
  }
  b.addEventListener("dragstart",function(e){drag=id;b.classList.add("dragging");try{e.dataTransfer.setData("text/plain",id);}catch(x){}});
  b.addEventListener("dragend",function(){drag=null;b.classList.remove("dragging");});
  return b;
 }
 function render(){
  lA.innerHTML="";lB.innerHTML="";
  pool.forEach(function(id){lA.appendChild(block(id,false));});
  if(!pool.length)lA.appendChild(mk("div","pp-empty","Alle regels zijn gebruikt."));
  sol.forEach(function(id){lB.appendChild(block(id,true));});
  if(!sol.length)lB.appendChild(mk("div","pp-empty","Sleep hier regels naartoe."));
 }
 function wire(list,to){
  list.addEventListener("dragover",function(e){e.preventDefault();list.classList.add("over");});
  list.addEventListener("dragleave",function(){list.classList.remove("over");});
  list.addEventListener("drop",function(e){
   e.preventDefault();list.classList.remove("over");if(!drag)return;
   var idx;
   if(to==="sol"){
    var kids=Array.prototype.slice.call(list.querySelectorAll(".pp-block")),
        y=e.clientY;idx=kids.length;
    for(var k=0;k<kids.length;k++){var r=kids[k].getBoundingClientRect();if(y<r.top+r.height/2){idx=k;break;}}
    var cur=sol.indexOf(drag);if(cur>-1&&cur<idx)idx--;
   }
   move(drag,to,idx);
  });
 }
 wire(lA,"pool");wire(lB,"sol");
 bR.onclick=function(){pool=shuffle(P.blocks.map(function(b){return b.id;}));sol=[];marks={};fb.className="pp-fb";fb.innerHTML="";render();};
 bC.onclick=function(){
  marks={};
  function say(cls,html){fb.className="pp-fb "+cls;fb.innerHTML=html;render();}
  if(!sol.length){say("err","Sleep eerst regels naar je programma.");return;}
  var bad=sol.filter(function(id){return byId[id].distract;});
  if(bad.length){bad.forEach(function(id){marks[id]="bad";});
   say("err","<strong>Niet helemaal.</strong> Een regel in je programma klopt niet: <em>"+byId[bad[0]].distract+"</em>");return;}
  for(var i=0;i<sol.length;i++){var b=byId[sol[i]];
   for(var n=0;n<b.needs.length;n++){if(sol.indexOf(b.needs[n])<0||sol.indexOf(b.needs[n])>i){
     marks[sol[i]]="bad";
     say("err","<strong>Let op de volgorde.</strong> Python leest van boven naar beneden. De regel <code>"+b.t+"</code> gebruikt iets wat op dat moment nog niet bestaat.");return;}}}
  var need=P.blocks.filter(function(b){return !b.distract;}).length;
  if(sol.length<need){say("err","<strong>Goed bezig,</strong> maar er ontbreken nog "+(need-sol.length)+" regel(s).");return;}
  sol.forEach(function(id){marks[id]="good";});
  say("ok","<strong>Goed gedaan!</strong> Jouw programma geeft:<div class=\"pp-out\"></div>");
  fb.querySelector(".pp-out").textContent=P.out;
 };
 render();root.appendChild(wrap);
});
})();
</script>
```

## 💡 Reflectie

Beantwoord voor jezelf:

- Welke regels herkende je meteen als "fout"? Waaraan zag je dat?
- Wanneer gebruik je `//` en wanneer `%`? Bedenk een eigen situatie waarin je ze allebei nodig hebt.
