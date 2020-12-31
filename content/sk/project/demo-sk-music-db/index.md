---
title: Hudobná databáza Demo Slovak Music Database
summary: Ukážka databázy, ktorá pomáha sledovať dodržiavanie vysielacích kvót a propagovať hudbu prostredníctvom digitálnych streamovacích služieb.
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

## Hudobná databáza Demo Slovak Music Database

Moderné streamovacie služby, podobne ako dodržiavanie miestnych smerníc (napr. vysielacích kvót), vyžadujú dostupnosť údajov o hranej a odporúčanej hudbe, a tiež metadata – údaje o údajoch. Na Slovensku v súčasnosti neexistuje databáza, ktorá by uľahčila dodržiavanie vysielacích kvót, alebo pomáhala napr. organizácii LaLa – Slovak music export či slovenským hudobným vydavateľstvám predstaviť hudbu novým fanúšikom.

Pripravili sme preto demo verziu slovenskej hudobnej databázy – Demo Slovak Music Database, ktorá tieto problémy dokáže vyriešiť. Zároveň sme vytvorili demo verziu aplikácie Listen Slovak, ktorá túto databázu využíva. V štúdii realizovateľnosti, ktorú sme v rámci projektu pripravili, vysvetľujeme postupy a predstavujeme údaje potrebné na vytvorenie a aktualizáciu kompletnej databázy v reálnom čase.
Demo verzia databázy obsahuje informácie o slovenských umelcoch a nahrávkach, ktoré vydali na Slovensku aj v zahraničí. Môže pomôcť jednoduchšie dodržiavať vysielacie kvóty, poslúžiť na vzdelávacie účely, či jednoducho zvýšiť pravdepodobnosť, že Spotify alebo YouTube odporučia poslucháčovi konkrétnu slovenskú nahrávku alebo video.

Celá databáza je prístupná cez SQLite (`db`) alebo vo formátoch `.csv`, `.xlsx` či `.rds`. Ak by ste ju chceli vyskúšať alebo rovno použiť, pokojne sa na nás obráťte. Naša databáza je otvorená, zadarmo, a záujemcom radi pomôžeme a poradíme. V úvode tejto stránky sme umiestnili zoznam umelcov, ktorí sa v databáze momentálne nachádzajú.

## Umelci

### Zaradenie do databázy {#opt-in}
Umelci a hudobné vydavateľstvá boli do databázy zaradené na základe dobrovoľného dotazníku od SOZA a Reprex BV. Účastníkov sme sa pýtali na vek, charakter vystúpení, jazyk a lokalitu. Možnosť zaradenia do databázy stále existuje – s radosťou do našej demo databázy a demo aplikácie pridáme ďalších umelcov. Dúfame, že naša spolupráca na projekte so SOZA a ďalšími partnermi bude pokračovať, a jej výsledkom bude naozaj rozsiahla databáza, ktorá bude obsahovať všetku slovenskú hudbu. 

### Vyradenie z databázy
Vyradenie z databázy je v tejto fáze veľmi jednoduché – stačí, ak nám dáte vedieť, že v nej naďalej nechcete byť zaradení.

### Údaje v databáze
Vhodný typ údajov do databázy sme zvolili pomerne subjektívne. Nemohli – a ani nechceli – sme totiž nakladať s osobnými údajmi, ktoré spadajú pod smernicu GDPR. Podľa v súčasnosti platnej vysielacej kvóty sú za slovenských umelcov považovaní tí, ktorí majú na území SR trvalý pobyt. Toto kritérium nebolo pre nás celkom vhodné, keďže trvalý pobyt patrí medzi osobné údaje a zosnulí umelci ho, prirodzene, nemajú.

Zvolili sme alternatívne riešenie a pripravili dlhý zoznam kandidátov na základe preferencií slovenských poslucháčov. Na začiatku sme vybrali umelcov, ktorí sa objavili v rebríčkoch rádií, na konkrétnych slovenských playlistoch v Spotify, alebo sami seba opisujú slovíčkom „slovenský, slovenská“, napr. `Slovak rock` alebo `Slovak hip-hop`. Na Wikipédii sme si prečítali ich anglické biografie rozdelené na ženskú a mužskú kategóriu.

Muzikologička Dominika Semaňáková, pôvodom zo Slovenska, nám pomohla určiť, ktorých umelcov by sme naozaj mali považovať za slovenských. Kritériá boli nasledovné – známe miesto pôsobenia (teda kde umelec alebo skupina väčšinou pôsobí), miesto narodenia, miesto úmrtia, jazyk textov, jazyk názvu skladby a ďalšie verejne dostupné informácie o umelcovi.

V demo verzii sme sa snažili obmedziť množstvo zadaných údajov a zamerali sme sa len na Spotify (dôvody si môžete prečítať tu ). Ku každému Spotify ID sú priradené nasledujúce údaje:

* `popularity`: hodnota od 0 do 100, ktoré na základe počtu prehraní na Spotify opisuje obľúbenosť umelca.
* `followers`: celkový počet používateľov, ktorí na Spotify umelca sledujú.
* `genre`: až tri žánre na umelca.
* `total_recommendations`: počet odporúčaní súvisiacich s daným umelcom po troch iteráciách algoritmu. Umelci s nulovou hodnotou odporúčaní sú pre Spotify prakticky neviditeľní a pravdepodobne nebudú odporúčaní nikdy. Jedným z našich hlavných cieľov je vyhnúť sa tzv. `cold start`-u, ktorý v roku 2020 postihol približne 15 % slovenských umelcov.
* `genres``: až tri žánre na umelca.
* `any_slovak_release`: ak umelec vydal nahrávky na Slovensku, priradí sa hodnota 1, inak sa priradí 0.
* `slovak_release_pct`: % nahrávok umelca vydaných na Slovensku.
* `any_slovak_title`: ak majú niektoré nahrávky daného umelca slovenský názov, priradí sa hodnota 1, inak sa priradí 0.
* `all_slovak_title`: ak majú všetky nahrávky daného umelca slovenský text, priradí sa hodnota 1, inak sa priradí 0.
* `all_english_title`: ak majú všetky nahrávky daného umelca slovenský text, priradí sa hodnota 1, inak sa priradí 0.
* `known_slovak_city`: slovenské mestá spojené s daným umelcom.
* `considered_czech`: ak je umelec zároveň považovaný za českého, priradí sa hodnota 1, inak sa priradí 0. Najväčšou výzvou bolo pre nás stanoviť hranicu medzi slovenským a českým.
* `popular_song_titles`: krátky výber najpopulárnejších skladieb umelca.
* `latest_popular_releases`: dátum vydania poslednej populárnej nahrávky umelca.
* `spotify_url`: odkaz na oficiálny profil na Spotify. 
* `Official_website_url`: odkaz na oficiálnu internetovú stránku umelca alebo skupiny.

### Zvukové nahrávky

Z celkového počtu 3 937 nahrávok obsahuje databáza Demo Slovak Music Database najviac 10 nahrávok, ktoré nie sú priradené k žiadnemu slovenskému umelcovi. Ak požiadame Spotify, aby nám odporučilo najvhodnejšie nahrávky, 19 umelcov sa vo výsledkoch vôbec nezobrazí. V prípade nájdených umelcov boli obsiahnuté tieto údaje: 
Ku každej skladbe sú priradené tieto údaje: ^[Kompletný zoznam údajov, ktoré Spotify jednotlivým nahrávkam priraďuje, nájdete na: [https://developer.spotify.com/documentation/web-api/reference/tracks/get-audio-features/](https://developer.spotify.com/documentation/web-api/reference/tracks/get-audio-features/)]

## Žánre

Všetci vieme, že pri vyhľadávaní a výbere nových hudobných diel je žáner veľmi dôležitý. V bežnej reči však niekedy býva problém hudbu dobre opísať. Žánrové názvoslovie môže byť zavádzajúce – napr. slovenskí hudobní fanúšikovia môžu chápať `jazz` trochu inak ako poslucháči v Japonsku alebo v Spojených štátoch. 
Digitálne streamovacie služby a internetové stránky zvyčajne využívajú umelú inteligenciu, ktorá vychádza z anglických pomenovaní žánrov. Preto je nesmierne dôležité správne pochopiť a používať slovenské a anglické definície jednotlivých žánrov. Popová skladba, ktorá je mylne označená ako `rock` sa môže stať neviditeľnou, pretože nevyhovuje vkusu fanúšikov „rocku“. Používatelia služby ju preskočia a umelá inteligencia sa naučí, že táto skladba je „neobľúbená“. Ak by sme ju však ponúkli fanúšikom `pop`u, mohla by sa ujať.

Tabuľka žánrov v našej databáze mapuje hypotetické rozdiely medzi „slovenskými“ žánrami, napr. `Slovak indie` či `Slovak jazz` a žánrami iných krajín, napr. `Belgian indie` alebo `Japanese jazz`. Tieto rozdiely sú dôležitou súčasťou našej databázy a ich správne rozlíšenie vyžaduje širší konsenzus hudobných dramaturgov, promotérov hudby v zahraničí, hudobných vydavateľstiev, umelcami a odborníkov v oblasti počítačovej muzikológie. Zaraďovanie skladieb do našej databázy ukazuje, že nedostatočné povedomie o žánrovom názvosloví globálnych streamovacích služieb je jedným z hlavných dôvodov nízkej viditeľnosti slovenskej hudby na týchto platformách. 
