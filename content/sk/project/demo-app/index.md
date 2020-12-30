---
title: Nalaď sa lokálne - Demo App
summary: An example of using the in-built project page.
tags:
- recommendations
date: "2020-12-01T00:00:00Z"

# Optional external URL for project (replaces project detail page).
external_link: ""

image:
  caption: 
  focal_point: Smart

links:
- icon: twitter
  icon_pack: fab
  name: Follow
  url: https://twitter.com/dataandlyrics
url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

## Zoznámte sa s aplikáciou `Nalaď sa lokálne`

Naša aplikácia `Nalaď sa lokálne` vyžíva strojové učenie. Systém presne sleduje zadaný cieľ – vyhľadáva hudbu – a pri tom sa neustále učí a zdokonaľuje. Treba sa však opýtať, kto tento cieľ určuje? Webstránka či služba, ktorá sa snaží, aby ste na nej strávili čo najviac času a pozreli si čo najviac reklám? Digitálna streamovacia služba, ktorá chce, aby ste počúvali len hudbu dostupnú na nej? Alebo vy sami?

V našej demo aplikácii si nastavujete cieľ sami. Ako východiskový bod môžete použiť zoznam najhranejších skladieb rádia, playlist rádia, alebo váš vlastný. Cieľ si nastavíte podobne, ako hudobní dramaturgovia nastavujú pomer istej hudby v danom rádiu. Chcete mať v playliste 20 % skladieb v slovenčine? Alebo 15 % skladieb od autorov, ktorí sa za Slovákov považujú? Zaujíma vás hudba z Holandska? Alebo chcete mať v playliste 20 % vydaných Slovákmi na Slovensku?
V našej demo aplikácii sme použili upravený algoritmus zo Spotify. Spotify považujeme za najlepší proprietárny software na svete, ktorý má zároveň dostatočne otvorené rozhranie pre programovanie aplikácií (API). Hoci Spotify svoj algoritmus ani presné nastavenie cieľov neprezradí, poskytuje nám dostatok informácii o hudbe, ktorú by za istých okolností dokázal odporučiť. Jeho systém je zároveň relatívne dobre zdokumentovaný, vďaka čomu máme pomerne dobrú predstavu o dianí za oponou. Pre väčšinu DSP systémov to neplatí. 

Rovnako ako Spotify, aj naša demo aplikácia odporúča skladby alebo nahrávky. Na rozdiel od Spotify vám však aplikácia `Nalaď sa lokálne` umožňuje zvoliť si vlastný cieľ – teda vytvorenie výsledného playlistu na základe vašich preferencií. Okrem toho vám prezradíme všetky kroky. Podobne ako Spotify alebo YouTube, aj `Nalaď sa lokálne` najprv vyberie veľký počet kandidátov – skladieb, ktoré by sa vám mohli páčiť. Následne výber zužuje podľa toho, čo považuje za najbližšie vášmu východiskovému – vzorovému – playlistu.

Naša aplikácia pracuje na princípe užitočnosti – hoci vychádza z pôvodných odporúčaní Spotify, priraďuje väčšiu váhu skladbám, ktoré spĺňajú vami zadané kritériá.

1.	Najväčšia váha je priradená generickým odporúčaniam Spotify, ktoré zároveň spĺňajú vaše kritériá – napr. obsahujú stanovené percento hudby od slovenských umelcov, skladieb vydaných na Slovensku, alebo so slovenskými textami. Veríme, že pri správnom použití je algoritmus, ktorý používa Spotify, skutočne skvelý. 
2.	Druhú najväčšiu váhu dostanú priradenú umelci, ktorých skladby spĺňajú zadané kritériá, a podľa Spotify sú podobní umelcom z vášho vzorového playlistu. Čo považuje algoritmus Spotify za „podobnosť“? Sleduje muzikologické a opisné črty, a tiež interakciu používateľa s touto hudbou. Ak algoritmus považuje umelca za podobného vzorovému playlistu, s veľkou pravdepodobnosťou mu podobný naozaj je.
3.	Tretia najväčšia váha je priradená skladbám, ktoré majú spoločný žáner s niektorými skladbami na vzorovom playliste, a zároveň sú slovenské.

`Nalaď sa lokálne` vyberie veľký počet skladieb a následne ich porovnáva s hudbou na vzorovom playliste. Vďaka využitiu „podobnosti“ nakoniec vznikne playlist, ktorý spĺňa kritériá zadané používateľom.

Väčšina odporúčacích služieb používa tri druhy informácií: informácie o hudbe ako takej, informácie o používateľoch, ktorí ju počúvali alebo hrali, ľubovoľné textové informácie dostupné z údajov poskytnutých umelcom samotným alebo vydavateľstvom, prípadne informácie o kapele z tlače. Snažíme sa poukázať na to, že ak má systém pracovať pre vás, umelcov, musíte mať kontrolu nad vstupnými údajmi. Napríklad, ako by ste opísali vašu hudbu tak, aby jej charakter Spotify, YouTube alebo `Nalaď sa lokálne` správne pochopili? Na ukážku sme použili našu demo verziu slovenskej hudobnej databázy (Demo Slovak Music Database). Databáza je voľne prístupná a využíva princíp opt-in, opt-out. Slovenskí umelci a muzikológovia môžu ovplyvňovať spôsob, akým sa informácie spracúvajú. 

Chceme tiež poukázať na skutočnosť, že na propagáciu hudobných vydavateľstiev, autorských kolektívov alebo hudobnej produkcie danej krajiny je veľmi dôležité nastaviť si ciele šikovne. Z etnomuzikologického hľadiska nestačí povedať, že by sme v playliste chceli mať 20 % slovenskej hudby. V našom projekte sme preto použili stupne „slovenskosti“.

Ak chceme napríklad propagovať „slovenskú hudbu“, „slovenský jazz“, „európsku hudbu“ alebo „novú hudbu“, máme viacero možností, ako nastaviť ciele. Dokážeme algoritmus vytrénovať tak, aby nám prezradil, v ktorom meste alebo krajine sa najviac počúva hudba podobná „slovenskému popu“. Môžeme vytvoriť aplikáciu, ktorá postupne oboznámi žiakov v školách s klasickou či súčasnou slovenskou a európskou hudbou – začne hudbou, ktorú už poznajú a majú radi, a postupne bude odporúčať novú podobnú hudbu, pričom im zároveň umožní vyjadriť svoj názor. Vieme pomôcť hudobným dramaturgom nájsť skladby umelcov z daného mesta, regiónu alebo krajiny, ktorými môžu obohatiť hudobný program rádia.

Používanie algoritmov môže mať isté nežiadúce dôsledky. Stáva sa napríklad, že v menšej krajine odporučí algoritmus používateľom známejšiu hudbu, pretože ju pozná lepšie, a zmenší tak publikum a priestor na trhu pre miestnych umelcov. Sme presvedčení, že podobným situáciám možno predchádzať, ak budú miestni umelci a ich manažéri vedieť, ako algoritmy streamovacích služieb alebo internetových stránok fungujú – ktoré údaje do nich vstupujú, a akú hudbu na ich základe odporučia.

Pracujeme na princípe otvorenej spolupráce – údaje sú používateľom voľne dostupné, algoritmy si možno prečítať, alebo dokonca upraviť. Predchádzame tak nie len negatívnym dôsledkom, ale zároveň pomáhame umelcom, tvorcom alebo ich zástupcom dosahovať želané výsledky. Veríme, že stanovené ciele je možné dosiahnuť len vtedy, ak máte pod kontrolou údaje aj algoritmus. 

