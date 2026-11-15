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

# Foutenjacht: Fouten opsporen en herstellen

In het werkblad *Input, Output en Foutopsporing* heb je zelf fouten gemaakt en opgelost. Dezelfde soorten fouten zie je hier terug, maar in nieuwe programma's. Nu ga je **fouten zoeken in code van anderen**, zoals een echte programmeur. Dat doe je op twee manieren:

1. **Foutenjacht**: je krijgt een programma met een fout. Je leest de foutmelding, wijst de foute regel aan en kiest de juiste reparatie.
2. **Parsons Problems**: je zet de juiste regels in de goede volgorde. Regels met typische fouten staan er ook tussen. Die moet je laten liggen.

```{admonition} Zo lees je een foutmelding
:class: tip
- Kijk eerst naar de **laatste regel**. Daar staat het soort fout en wat er mis is.
- Kijk dan naar het **regelnummer** (`line 8`). Daar zit de fout of vlak erboven.
- **SyntaxError**: de code is verkeerd opgeschreven (aanhalingsteken, haakje of komma vergeten). Er wordt **niets** uitgevoerd.
- **NameError**: Python kent een naam niet (typfout, hoofdletter, nog niet aangemaakt).
- **TypeError**: je gebruikt een waarde van het verkeerde type, bijvoorbeeld tekst plus een getal.
- Geen foutmelding maar toch een verkeerde uitvoer? Dan is het een **logische fout**.
```

*De precieze tekst van een foutmelding kan per Python-versie een beetje anders zijn.*

## Deel 1: Foutenjacht

Elke opdracht heeft drie stappen: de fout herkennen, de foute regel aanwijzen en de reparatie kiezen. Kun je er niet uit? Kijk dan goed naar de foutmelding.

```{raw} html
<style>
.fj-code{list-style:none;margin:.4em 0;padding:0;font-family:var(--pst-font-family-monospace,monospace);font-size:.88em;}
.fj-line{display:flex;gap:10px;width:100%;text-align:left;padding:3px 8px;border:1px solid transparent;border-radius:4px;background:none;color:inherit;font:inherit;cursor:default;}
.fj-line .no{opacity:.5;min-width:1.6em;text-align:right;}
.fj-line.pick{cursor:pointer;border-color:var(--pst-color-border,#999);margin-bottom:2px;}
.fj-line.pick:hover{background:rgba(10,108,255,.12);}
.fj-line.bad{background:rgba(220,50,50,.18);border-color:#d33;}
.fj-line.good{background:rgba(40,160,80,.18);border-color:#2a9d4a;}
.fj-box{padding:6px 4px;border:1px solid var(--pst-color-border,#999);border-radius:8px;background:var(--pst-color-background,#fff);}
.fj-opts{display:flex;flex-direction:column;gap:6px;margin-top:.5em;}
.fj-opt{text-align:left;padding:6px 10px;border:1px solid var(--pst-color-border,#999);border-radius:6px;background:none;color:inherit;cursor:pointer;font:inherit;}
.fj-opt.code{font-family:var(--pst-font-family-monospace,monospace);font-size:.88em;}
.fj-opt:hover{background:rgba(127,127,127,.15);}
.fj-errtxt{color:#ff8b8b;}
.fj-label{font-weight:600;font-size:.85em;margin:.7em 0 .2em;opacity:.8;}
</style>
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
</style><div id="fj-root"></div>
<script>
(function(){
var CASES=[
 {
  "title": "Foutenjacht 1: Bioscoopkaartjes",
  "intro": "Een leerling maakte een programma om bioscoopkaartjes te bestellen. Het aantal kaartjes is een <code>int</code>, zodat er mee gerekend kan worden. Daarna ging het mis. Onderzoek de fout.",
  "typ": "Dune, 3",
  "code": [
   "film = input(\"Film: \")",
   "aantal = int(input(\"Aantal kaartjes: \"))",
   "totaal = aantal * 9",
   "print(\"Film: \" + film)",
   "print(\"Aantal kaartjes: \" + aantal)",
   "print(\"Totaal: \" + str(totaal) + \" euro\")"
  ],
  "bug": 4,
  "outType": "err",
  "out": "Film: Dune\nTraceback (most recent call last):\n  File \"bioscoop.py\", line 5, in <module>\n    print(\"Aantal kaartjes: \" + aantal)\nTypeError: can only concatenate str (not \"int\") to str",
  "q1": {
   "q": "Welke soort fout is dit?",
   "opts": [
    {
     "t": "SyntaxError: de code is verkeerd opgeschreven",
     "fb": "Bij een SyntaxError start het programma helemaal niet. Hier is regel 4 nog wel uitgevoerd: Film: Dune staat op het scherm."
    },
    {
     "t": "TypeError: een waarde heeft het verkeerde type",
     "ok": true,
     "fb": "Dat staat ook in de laatste regel van de foutmelding: je plakt een <code>int</code> aan een <code>str</code>."
    },
    {
     "t": "NameError: een variabele bestaat niet",
     "fb": "Dan zou er staan: name '...' is not defined. Hier bestaat de variabele wel, alleen is het een getal."
    }
   ]
  },
  "hint": "In de foutmelding staat het regelnummer (line 5).",
  "fix": [
   {
    "t": "print(\"Aantal kaartjes: \" + str(aantal))",
    "ok": true,
    "fb": "Met <code>str()</code> zet je het getal om naar tekst. Kijk maar naar regel 6: daar gebeurt hetzelfde met <code>totaal</code>."
   },
   {
    "t": "print(f\"Aantal kaartjes: {aantal}\")",
    "ok": true,
    "fb": "Een f-string zet het getal zelf om naar tekst. Dat werkt ook."
   },
   {
    "t": "print(\"Aantal kaartjes: \" + int(aantal))",
    "fb": "<code>int()</code> maakt van iets een <em>getal</em>. Je hebt juist <em>tekst</em> nodig, dus de TypeError blijft."
   },
   {
    "t": "print(\"Aantal kaartjes: \" + \"aantal\")",
    "fb": "Met aanhalingstekens print Python letterlijk het woord aantal in plaats van het getal 3."
   },
   {
    "t": "print(\"Aantal kaartjes: \" + aantal.str())",
    "fb": "<code>str()</code> is een functie waar je het getal aan meegeeft: <code>str(aantal)</code>. Een getal heeft geen eigen <code>.str()</code>. Dat geeft een AttributeError."
   }
  ],
  "fixedOut": "Film: Dune\nAantal kaartjes: 3\nTotaal: 27 euro",
  "leer": "Een getal (<code>int</code>) kun je niet met <code>+</code> aan tekst plakken. Zet het om met <code>str()</code> of gebruik een f-string."
 },
 {
  "title": "Foutenjacht 2: Welkom bij het dierenasiel",
  "intro": "Dit programma geeft <strong>geen foutmelding</strong>, maar de uitvoer klopt niet. Dat noem je een <em>logische fout</em>. Zoek uit wat er mis is.",
  "typ": "Emma, hond",
  "code": [
   "naam = input(\"Wat is je naam? \")",
   "huisdier = input(\"Welk huisdier heb je? \")",
   "print(\"Hallo naam, wat leuk dat je een huisdier hebt!\")"
  ],
  "bug": 2,
  "outType": "out",
  "out": "Hallo naam, wat leuk dat je een huisdier hebt!",
  "q1": {
   "q": "Wat gaat er mis?",
   "opts": [
    {
     "t": "Python geeft een foutmelding in rood",
     "fb": "Er staat geen rode tekst. Python voert de regel gewoon uit."
    },
    {
     "t": "Er staan de woorden 'naam' en 'huisdier' letterlijk, en niet wat de gebruiker typte",
     "ok": true,
     "fb": "Juist. Wat tussen aanhalingstekens staat, print Python precies zoals het er staat."
    },
    {
     "t": "Het programma stopt direct na de input",
     "fb": "Het programma loopt door: het print wel iets, alleen het verkeerde."
    }
   ]
  },
  "hint": "Zoek de regel met de begroeting.",
  "fix": [
   {
    "t": "print(\"Hallo \" + naam + \", wat leuk dat je een \" + huisdier + \" hebt!\")",
    "ok": true,
    "fb": "Beide variabelen staan nu buiten de aanhalingstekens, dus Python gebruikt hun waarde."
   },
   {
    "t": "print(f\"Hallo {naam}, wat leuk dat je een {huisdier} hebt!\")",
    "ok": true,
    "fb": "Met een f-string zet je de variabelen tussen accolades. Dat werkt ook."
   },
   {
    "t": "print(\"Hallo \" + naam + \", wat leuk dat je een huisdier hebt!\")",
    "fb": "Je hebt maar de helft gerepareerd: het woord <em>huisdier</em> staat nog steeds tussen aanhalingstekens."
   },
   {
    "t": "print(\"Hallo {naam}, wat leuk dat je een {huisdier} hebt!\")",
    "fb": "Zonder de <code>f</code> voor de aanhalingstekens print Python letterlijk {naam} en {huisdier}."
   },
   {
    "t": "print(Hallo + naam + \", wat leuk dat je een \" + huisdier + \" hebt!\")",
    "fb": "Zonder aanhalingstekens denkt Python dat Hallo een variabele is. Dat geeft een NameError."
   }
  ],
  "fixedOut": "Hallo Emma, wat leuk dat je een hond hebt!",
  "leer": "Een variabele zet je <strong>buiten</strong> de aanhalingstekens (of tussen accolades in een f-string). Anders is het gewoon tekst. Controleer dus <em>alle</em> variabelen in een regel."
 },
 {
  "title": "Foutenjacht 3: De Python-quiz",
  "intro": "Een leerling bouwt een quiz. Hij voert het programma uit, maar er gebeurt iets vreemds.",
  "typ": "(er wordt niets gevraagd, want het programma start niet)",
  "code": [
   "print(\"Welkom bij de Python-quiz!\")",
   "antwoord = input(\"Hoe heet de hoofdstad van Frankrijk? \")",
   "print(\"Jouw antwoord is: \" + antwoord)",
   "print(\"Bedankt voor het meespelen!\""
  ],
  "bug": 3,
  "outType": "err",
  "out": "  File \"quiz.py\", line 4\n    print(\"Bedankt voor het meespelen!\"\n         ^\nSyntaxError: '(' was never closed",
  "q1": {
   "q": "Welke regels worden uitgevoerd voordat Python de fout meldt?",
   "opts": [
    {
     "t": "Regel 1 tot en met 3 verschijnen eerst op het scherm",
     "fb": "Dat gebeurt bij een TypeError (zie Foutenjacht 1). Kijk naar de uitvoer hierboven: er staat niets op het scherm."
    },
    {
     "t": "Geen enkele. Een SyntaxError wordt gevonden voordat het programma start",
     "ok": true,
     "fb": "Juist. Python leest eerst het hele programma. Is er een schrijffout, dan wordt er niets uitgevoerd."
    },
    {
     "t": "Alleen regel 1",
     "fb": "Ook regel 1 wordt niet uitgevoerd. Er staat niets op het scherm."
    }
   ]
  },
  "hint": "In de foutmelding staat het regelnummer (line 4).",
  "fix": [
   {
    "t": "print(\"Bedankt voor het meespelen!\")",
    "ok": true,
    "fb": "Elk haakje dat je opent, moet je ook weer sluiten."
   },
   {
    "t": "print(\"Bedankt voor het\" + \" meespelen!\")",
    "ok": true,
    "fb": "Twee stukken tekst met een <code>+</code> aan elkaar geplakt, met een sluitend haakje. Dat werkt ook."
   },
   {
    "t": "print(\"Bedankt voor het meespelen!\"))",
    "fb": "Nu staan er twee sluithaakjes, en dus één te veel. Dat geeft opnieuw een SyntaxError."
   },
   {
    "t": "print(\"Bedankt voor het meespelen!)",
    "fb": "Het haakje staat nu binnen de aanhalingstekens, dus de tekst is niet afgesloten. Dat geeft een SyntaxError."
   },
   {
    "t": "print('Bedankt voor het meespelen!'",
    "fb": "Het sluitende haakje ontbreekt nog steeds. Dat geeft dezelfde SyntaxError."
   }
  ],
  "fixedOut": "Welkom bij de Python-quiz!\nHoe heet de hoofdstad van Frankrijk? Parijs\nJouw antwoord is: Parijs\nBedankt voor het meespelen!",
  "leer": "Een <strong>SyntaxError</strong> betekent dat Python het programma niet eens start: er verschijnt <em>niets</em> op het scherm. Een <strong>TypeError</strong> of <strong>NameError</strong> komt pas tijdens het uitvoeren, nadat een deel al is gelukt."
 },
 {
  "title": "Foutenjacht 4: De cijferkaart",
  "intro": "Dit programma berekent het gemiddelde van twee cijfers. Het stopt vlak voor het einde. Zoek de fout.",
  "typ": "7.5, 8",
  "code": [
   "print(\"Cijferkaart\")",
   "wiskunde = float(input(\"Cijfer wiskunde: \"))",
   "informatica = float(input(\"Cijfer informatica: \"))",
   "gemiddelde = (wiskunde + informatica) / 2",
   "print(\"Wiskunde:\", wiskunde)",
   "print(\"Informatica:\", informatica)",
   "print(\"Gemiddelde:\", gemidelde)"
  ],
  "bug": 6,
  "outType": "err",
  "out": "Cijferkaart\nWiskunde: 7.5\nInformatica: 8.0\nTraceback (most recent call last):\n  File \"cijferkaart.py\", line 7, in <module>\n    print(\"Gemiddelde:\", gemidelde)\nNameError: name 'gemidelde' is not defined. Did you mean: 'gemiddelde'?",
  "q1": {
   "q": "Welke soort fout is dit?",
   "opts": [
    {
     "t": "NameError: Python kent de naam niet",
     "ok": true,
     "fb": "Juist. Python zegt zelfs welke naam het niet kent: gemidelde."
    },
    {
     "t": "TypeError: een waarde heeft het verkeerde type",
     "fb": "Dan zou er staan 'can only concatenate...' of iets over een type. Hier staat: name is not defined."
    },
    {
     "t": "SyntaxError: de code is verkeerd opgeschreven",
     "fb": "Bij een SyntaxError wordt er niets uitgevoerd. Hier zijn al veel regels uitgevoerd."
    }
   ]
  },
  "hint": "In de foutmelding staat het regelnummer (line 7).",
  "fix": [
   {
    "t": "print(\"Gemiddelde:\", gemiddelde)",
    "ok": true,
    "fb": "Bij het aanmaken van de variabele schreef de leerling <code>gemiddelde</code> met twee d's. In de printregel stond één d. Een typfout dus."
   },
   {
    "t": "print(\"Gemiddelde:\", \"gemiddelde\")",
    "fb": "Dan print Python letterlijk het woord gemiddelde in plaats van het getal."
   },
   {
    "t": "print(\"Gemiddelde:\", Gemiddelde)",
    "fb": "Python is hoofdlettergevoelig: <code>Gemiddelde</code> bestaat niet, alleen <code>gemiddelde</code>. Dat geeft opnieuw een NameError."
   },
   {
    "t": "print(\"Gemiddelde:\", gemiddelde())",
    "fb": "Met haakjes behandelt Python <code>gemiddelde</code> als functie. Dat geeft een TypeError."
   }
  ],
  "fixedOut": "Cijferkaart\nWiskunde: 7.5\nInformatica: 8.0\nGemiddelde: 7.75",
  "leer": "Een <strong>typfout</strong> in een variabelenaam geeft een NameError. Python is ook <strong>hoofdlettergevoelig</strong>. Python geeft vaak een tip: Did you mean ...?"
 }
];
function mk(tag,cls,txt){var e=document.createElement(tag);if(cls)e.className=cls;if(txt!==undefined)e.textContent=txt;return e;}
function shuffle(a){a=a.slice();for(var i=a.length-1;i>0;i--){var j=Math.floor(Math.random()*(i+1));var t=a[i];a[i]=a[j];a[j]=t;}return a;}
var root=document.getElementById("fj-root");
CASES.forEach(function(C){
 var step,lines,wrong,msg,q1,fix;
 var wrap=mk("div","pp-wrap");root.appendChild(wrap);
 function reset(){step=1;lines=C.code.slice();wrong=0;msg=null;q1=shuffle(C.q1.opts);fix=shuffle(C.fix);render();}
 function say(cls,html){msg={cls:cls,html:html};render();}
 function render(){
  wrap.innerHTML="";
  wrap.appendChild(mk("h4","",C.title));
  var p=mk("p");p.innerHTML=C.intro;wrap.appendChild(p);
  var t=mk("p");t.appendChild(document.createTextNode("Ingevoerd: "));t.appendChild(mk("code","",C.typ));wrap.appendChild(t);
  wrap.appendChild(mk("div","fj-label","Het programma"));
  var box=mk("div","fj-box"),ol=mk("ol","fj-code");
  lines.forEach(function(l,i){
   var li=mk("li"),b=mk("button","fj-line");b.type="button";
   b.appendChild(mk("span","no",String(i+1)));b.appendChild(mk("code","",l));
   if(step===2)b.classList.add("pick");
   if(step===3&&i===C.bug)b.classList.add("bad");
   if(step===4&&i===C.bug)b.classList.add("good");
   b.onclick=function(){if(step!==2)return;
    if(i===C.bug){step=3;msg=null;render();}
    else{wrong++;say("err","Regel "+(i+1)+" is niet de fout."+(wrong>=2?" <strong>Tip:</strong> "+C.hint:""));}};
   li.appendChild(b);ol.appendChild(li);});
  box.appendChild(ol);wrap.appendChild(box);
  wrap.appendChild(mk("div","fj-label",step===4?"Nu geeft het programma":"Python zegt"));
  var out=mk("div","pp-out");
  if(step===4)out.textContent=C.fixedOut;
  else{var s=mk("span",C.outType==="err"?"fj-errtxt":"",C.out);out.appendChild(s);}
  wrap.appendChild(out);
  var panel=mk("div");
  if(step===1){
   panel.appendChild(mk("div","fj-label","Stap 1. "+C.q1.q));
   var o=mk("div","fj-opts");
   q1.forEach(function(op){var b=mk("button","fj-opt",op.t);b.type="button";
    b.onclick=function(){if(op.ok){step=2;say("ok","<strong>Juist!</strong> "+op.fb);}else say("err",op.fb);};o.appendChild(b);});
   panel.appendChild(o);
  }else if(step===2){
   panel.appendChild(mk("div","fj-label","Stap 2. Klik op de regel die de fout veroorzaakt."));
  }else if(step===3){
   panel.appendChild(mk("div","fj-label","Stap 3. Hoe repareer je regel "+(C.bug+1)+"?"));
   var o2=mk("div","fj-opts");
   fix.forEach(function(op){var b=mk("button","fj-opt code",op.t);b.type="button";
    b.onclick=function(){if(op.ok){lines[C.bug]=op.t;step=4;say("ok","<strong>Goed gedaan!</strong> "+op.fb);}else say("err",op.fb);};o2.appendChild(b);});
   panel.appendChild(o2);
  }
  wrap.appendChild(panel);
  if(msg){var fb=mk("div","pp-fb "+msg.cls);fb.innerHTML=msg.html;wrap.appendChild(fb);}
  if(step===4){var l=mk("div","pp-fb ok");l.innerHTML="💡 <strong>Wat leer je hiervan?</strong> "+C.leer;wrap.appendChild(l);}
  var bar=mk("div","pp-bar"),rb=mk("button","pp-btn sec","Opnieuw");rb.type="button";rb.onclick=reset;bar.appendChild(rb);wrap.appendChild(bar);
 }
 reset();
});
})();
</script>
```

## Deel 2: Parsons Problems

Klik op een regel (of sleep hem) om hem naar jouw programma te verplaatsen. Gebruik ▲ ▼ om de volgorde aan te passen en klik op **Controleer**. Pas op voor de regels met een fout erin!

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
 {
  "title": "Parsons 1: De pizzabestelling",
  "intro": "Zet de regels in de juiste volgorde. Het aantal pizza's is een <code>int</code>, zodat je ermee kunt rekenen. Let op de regels die niet kloppen! Ingevuld wordt: Margherita en 2.",
  "blocks": [
   {
    "id": "a",
    "t": "pizza = input(\"Welke pizza? \")",
    "needs": []
   },
   {
    "id": "b",
    "t": "aantal = int(input(\"Hoeveel? \"))",
    "needs": []
   },
   {
    "id": "c",
    "t": "totaal = aantal * 8",
    "needs": [
     "b"
    ]
   },
   {
    "id": "d",
    "t": "print(\"Je bestelt \" + str(aantal) + \" keer \" + pizza)",
    "needs": [
     "a",
     "b"
    ]
   },
   {
    "id": "e",
    "t": "print(\"Totaal: \" + str(totaal) + \" euro\")",
    "needs": [
     "c"
    ]
   },
   {
    "id": "x1",
    "t": "print(\"Je bestelt \" + aantal + \" keer \" + pizza)",
    "distract": "Je plakt een getal aan tekst zonder str(). Dat geeft een TypeError."
   },
   {
    "id": "x2",
    "t": "aantal = int(input(\"Hoeveel? \")",
    "distract": "Het laatste haakje ontbreekt. Dat geeft een SyntaxError."
   }
  ],
  "out": "Je bestelt 2 keer Margherita\nTotaal: 16 euro"
 },
 {
  "title": "Parsons 2: De uitnodiging",
  "intro": "Maak de uitnodiging af in de juiste volgorde. De naam van de gast is Lisa.",
  "blocks": [
   {
    "id": "a",
    "t": "naam = input(\"Naam van de gast: \")",
    "needs": []
   },
   {
    "id": "b",
    "t": "print(\"Hoi \" + naam + \"!\")",
    "needs": [
     "a"
    ]
   },
   {
    "id": "c",
    "t": "print(\"Je bent uitgenodigd voor mijn feest.\")",
    "needs": [
     "b"
    ]
   },
   {
    "id": "d",
    "t": "print(\"Groetjes, Sam\")",
    "needs": [
     "c"
    ]
   },
   {
    "id": "x1",
    "t": "print(\"Hoi naam!\")",
    "distract": "De variabele staat tussen aanhalingstekens, dus Python print letterlijk het woord naam."
   },
   {
    "id": "x2",
    "t": "print(Groetjes, Sam)",
    "distract": "Zonder aanhalingstekens zoekt Python variabelen met de namen Groetjes en Sam. Die bestaan niet: een NameError."
   }
  ],
  "out": "Hoi Lisa!\nJe bent uitgenodigd voor mijn feest.\nGroetjes, Sam"
 },
 {
  "title": "Parsons 3: De cijferkaart",
  "intro": "Zet het programma in de juiste volgorde. Een variabele moet bestaan voordat je hem print. Ingevuld wordt: Lisa en 7.5.",
  "blocks": [
   {
    "id": "a",
    "t": "print(\"Cijferkaart\")",
    "needs": []
   },
   {
    "id": "b",
    "t": "naam = input(\"Naam: \")",
    "needs": []
   },
   {
    "id": "c",
    "t": "cijfer = float(input(\"Cijfer: \"))",
    "needs": []
   },
   {
    "id": "d",
    "t": "print(\"Naam:\", naam)",
    "needs": [
     "a",
     "b"
    ]
   },
   {
    "id": "e",
    "t": "print(\"Cijfer:\", cijfer)",
    "needs": [
     "c",
     "d"
    ]
   },
   {
    "id": "x1",
    "t": "print(\"Cijfer:\", Cijfer)",
    "distract": "Python is hoofdlettergevoelig. Cijfer bestaat niet, alleen cijfer. Dat geeft een NameError."
   },
   {
    "id": "x2",
    "t": "print(\"Naam:\", \"naam\")",
    "distract": "Met aanhalingstekens print Python letterlijk het woord naam en niet de waarde."
   }
  ],
  "out": "Cijferkaart\nNaam: Lisa\nCijfer: 7.5"
 }
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

Beantwoord in je schrift:

- Welk soort fout zie je het vaakst bij jezelf: SyntaxError, NameError, TypeError of een logische fout?
- Wat is het verschil tussen een SyntaxError en een TypeError? Wat zie je op het scherm als je beide programma's uitvoert?
- Wat doe je de volgende keer als je een foutmelding krijgt? Noem drie stappen.
