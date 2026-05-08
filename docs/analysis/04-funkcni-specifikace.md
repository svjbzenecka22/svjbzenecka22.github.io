# Funkční specifikace

## Stav dokumentu

Pracovní návrh MVP první agendy k 2026-05-09. Dokument shrnuje, co má systém umět z pohledu vlastníků, uživatelů bytů
a výboru SVJ. Nejde ještě o technickou specifikaci ani o definitivní výběr technologie.

Podkladem jsou zodpovězené otázky v byznys analýze a v dokumentu otevřených otázek. V této fázi už nejsou evidovány
blokující otevřené otázky pro samotný sběr počtu čipů a volby typu bytového telefonu.

## Rámec webu a portálu

### Veřejný web

Veřejný web má dál sloužit jako hlavní informační rozcestník SVJ. Má umět:

- zobrazit hlavní stránku SVJ,
- zobrazit tematické sekce,
- publikovat veřejné dokumenty,
- zobrazit kontakty,
- odkázat na formulářové nebo neveřejné agendy,
- být použitelný na mobilu i počítači.

Veřejný web nesmí zobrazovat odpovědi jednotlivých jednotek, neveřejné dokumenty ani osobní údaje nad nezbytný rozsah.

### Budoucí soukromá část

Soukromá část webu nebo portálu je dlouhodobý směr, ne nutná podmínka pro MVP první agendy. Do budoucna má být možné:

- ověřit oprávnění uživatele,
- zobrazit obsah podle role nebo jednotky,
- ukládat odpovědi a souhlasy,
- umožnit výboru export dat,
- omezit přístup k neveřejným dokumentům,
- rozlišit veřejné dokumenty, dokumenty pro přihlášené vlastníky a uživatele bytů a případně dokumenty vázané ke konkrétní jednotce,
- elektronické hlasování řešit až po změně stanov a samostatném právním a procesním ověření,
- u budoucích elektronických souhlasů nebo hlasování počítat s auditní stopou a pravidly uchování.

Dokumenty a hlasování nejsou požadavkem první agendy přístupového systému. Tato oblast zůstává rámcově evidovaná pro
budoucí rozvoj portálu.

## MVP první agendy: přístupový systém

### Cíl MVP

Cílem MVP je získat od každé bytové jednotky jednu použitelnou finální odpověď pro přípravu objednávky přístupového
systému. Výbor má po uzavření sběru umět připravit podklady pro dodavatele a pro kontrolu doplatků.

MVP má výboru umožnit zejména:

- zjistit požadovaný počet čipů za jednotku,
- zjistit zvolený typ bytového telefonu za jednotku,
- rozlišit jednotky, které odpověděly a neodpověděly,
- určit poslední platnou odpověď za jednotku,
- vypočítat doplatek za jednotku,
- přiřadit odpovědi variabilní symbol pro platbu,
- připravit objednávkový souhrn pro dodavatele,
- připravit podklady pro kontrolu plateb,
- archivovat finální souhrn použitý pro objednávku.

### Hranice MVP

Součástí MVP má být:

- online sběr odpovědí,
- evidence odpovědí po jednotkách,
- samoobslužná změna odpovědi do uzávěrky,
- výpočet doplatku podle počtu čipů a zvoleného telefonu,
- potvrzení seznámení s doplatkem a platebními pokyny,
- přehled odpovědí pro výbor,
- filtrace jednotek bez odpovědi,
- export finálních odpovědí pro dodavatele,
- podklad pro kontrolu plateb podle variabilního symbolu a částky.

Součástí MVP nemá být:

- plnohodnotný portál pro všechny agendy SVJ,
- ověřování totožnosti každé osoby proti samostatnému registru vlastníků a nájemníků,
- samostatný účet pro každého spoluvlastníka nebo člena domácnosti,
- elektronické hlasování,
- automatické napojení na banku,
- automatické párování plateb,
- běžná evidence odpovědí mimo online formulář,
- přímý přístup dodavatele do interní evidence výboru,
- kompletní dlouhodobá evidence všech provozních událostí čipů.

## Role a oprávnění

### Odpovídající osoba

Odpovídající osoba vyplňuje nebo mění odpověď za jednotku. Může jít o vlastníka, spoluvlastníka, nájemníka, uživatele
bytu nebo pověřenou osobu podle praktického režimu dané jednotky.

V první fázi se odpověď chápe jako odpověď jednotky, nikoliv jako právně ověřený osobní úkon konkrétní osoby.

### Domácnost nebo jednotkový přístup

Pracovní model přístupu je domácnost nebo jednotka. Přístup prakticky reprezentuje bytovou jednotku a skupinu osob,
která ji užívá, ne samostatně ověřenou identitu každé osoby.

Každá jednotka nebo domácnost má mít evidovaný primární kontaktní e-mail a hlavní kontaktní telefon pro komunikaci
výboru. Tyto údaje mohou pomoci s přístupem a komunikací, ale stabilním datovým klíčem musí zůstat bytová jednotka.

### Vlastník a uživatel bytu

Běžný přístup do portálu mají mít vlastníci i nájemníci nebo uživatelé bytů. U bytů ve vlastnictví fyzické osoby je pro
komunikaci vůči SVJ určující vlastník, zejména pokud by vznikl rozpor mezi vlastníkem a uživatelem bytu.

U bytů ve vlastnictví Stavebního bytového družstva Mír má být praktickým uživatelem agendy nájemník nebo uživatel
bytu. SBD Mír jako formální vlastník družstevních bytů nemá mít běžný přístup do agend jednotlivých domácností;
případný budoucí přístup SBD Mír má být omezený a navázaný na konkrétní potřebu.

### Výbor

Výbor připravuje zadání, sleduje stav odpovědí, řeší výjimky, kontroluje úplnost, připravuje exporty a provádí
kontrolu plateb. Administrátorský přístup mají mít všichni tři členové výboru.

### Dodavatel

Dodavatel nemá mít přímý přístup do systému. Výbor mu předává pouze schválený finální souhrn nebo export.

## Uživatelský průběh

### Zobrazení zadání

Uživatel má před vyplněním vidět srozumitelné informace k agendě:

- že se sbírá počet čipů a volba typu bytového telefonu,
- že odpověď se vztahuje k bytové jednotce,
- že standardní cesta odpovědi je online formulář,
- že uzávěrka sběru je 2026-05-24,
- že ceny čipů a telefonů jsou finální,
- že výsledný doplatek bude vypočten před odesláním odpovědi,
- že po uzávěrce se změny řeší jen individuálně přes výbor.

Není potřeba samostatné rozsáhlé komunikační kolo před spuštěním sběru, protože vlastníci a uživatelé bytů byli s
problematikou seznámeni na shromáždění dne 2026-04-27.

### Vyplnění odpovědi

Uživatel má v online formuláři provést tyto kroky:

1. Identifikovat jednotku nebo vstoupit přes přístup určený pro jednotku.
2. Uvést počet požadovaných čipů.
3. Vybrat typ bytového telefonu.
4. Uvést údaje o odpovídající osobě, pokud nejsou spolehlivě známé z přihlášení nebo profilu.
5. Uvést kontaktní údaj pro řešení nejasností, pokud není spolehlivě známý z profilu jednotky.
6. Volitelně uvést poznámku s dotazem nebo připomínkou k agendě.
7. Zkontrolovat vypočtený doplatek a platební pokyny.
8. Potvrdit seznámení s finálním doplatkem a platebními pokyny.
9. Odeslat odpověď.

Po odeslání má uživatel obdržet potvrzení o přijetí odpovědi nebo alespoň jasné potvrzení na obrazovce.

### Změna odpovědi

Do uzávěrky má být změna odpovědi samoobslužná. Pokud přijde více odpovědí za stejnou jednotku před uzávěrkou, jako
finální se použije poslední platná odpověď za jednotku.

Po uzávěrce nemá být změna dostupná v běžné uživatelské části systému. Osoba, která potřebuje změnu po uzávěrce,
musí kontaktovat výbor individuálně, například e-mailem, telefonicky nebo přes WhatsApp. Výbor případnou výjimku
posoudí a pokud ji přijme, upraví odpověď administrativně.

## Administrace výboru

Výbor má v MVP potřebovat především pracovní přehled a exporty, ne složitou administraci portálu. Systém má výboru
umožnit:

- zobrazit seznam odpovědí,
- zobrazit stav odpovědí podle jednotek,
- filtrovat jednotky bez odpovědi,
- rozlišit platné, nahrazené a neúplné odpovědi,
- určit poslední platnou odpověď za jednotku,
- zkontrolovat zjevné nesrovnalosti,
- administrativně upravit odpověď po uzávěrce, pokud výbor schválí výjimku,
- evidovat nebo vygenerovat variabilní symbol,
- zobrazit vypočtený doplatek za jednotku,
- připravit podklad pro e-mailovou urgenci neodpovězeným jednotkám,
- uzavřít sběr odpovědí,
- exportovat finální souhrn pro dodavatele,
- exportovat podklad pro kontrolu plateb,
- archivovat finální souhrn použitý pro objednávku.

Pokud to zvolená technologie rozumně umožní, má systém pomoci výboru i s vygenerováním e-mailu nebo seznamu kontaktů
pro jednotky bez odpovědi. Ruční odeslání e-mailů výborem je pro MVP přijatelné.

## Datové položky

### Povinné údaje odpovědi

Každá finální odpověď má obsahovat:

- jednotku,
- počet čipů,
- typ telefonu,
- vypočtenou finální výši doplatku,
- variabilní symbol platby,
- potvrzení seznámení s finálním doplatkem a platebními pokyny,
- datum a čas odeslání odpovědi,
- stav odpovědi, například platná, nahrazená, neúplná nebo administrativně upravená.

### Údaje o odpovídající osobě

Pokud MVP nebude mít obecnou portálovou identitu s rolemi a přístupy, mají být povinné nebo důrazně doporučené také:

- jméno odpovídající osoby,
- kontaktní údaj pro řešení nejasností,
- vztah odpovídající osoby k jednotce.

Pokud bude existovat obecná portálová identita, má systém tyto údaje přednostně odvozovat z přihlášení nebo profilu,
nikoliv vyžadovat ruční opakované zadání.

### Údaje o jednotce nebo domácnosti

Pro pracovní model jednotky nebo domácnosti mají být evidovány:

- identifikace jednotky,
- primární kontaktní e-mail domácnosti nebo jednotky,
- hlavní kontaktní telefon domácnosti nebo jednotky,
- případně informace, zda jde o byt vlastněný fyzickou osobou nebo byt ve vlastnictví SBD Mír.

Primární e-mail a telefon jsou kontaktní a případně přístupové údaje. Nesmí být jediným stabilním identifikátorem,
protože se mohou změnit nebo být sdílené více osobami.

### Volitelné údaje

Volitelné položky:

- druhý kontaktní údaj, například telefon vedle e-mailu,
- poznámka s dotazem nebo připomínkou k agendě.

Volná poznámka má být určena pouze pro dotazy a připomínky k této agendě. Uživatel má být stručně upozorněn, aby do
poznámky neuváděl zbytečné osobní nebo citlivé údaje.

## Čipy a telefony

### Čipy

- Počet čipů nemá stanovený horní obchodní limit.
- Počet čipů musí být kladné celé číslo.
- Hodnota 0 čipů je chyba, protože by znamenala nefunkční přístup uživatele jednotky do domu nebo společných částí.
- Každý objednaný čip se platí; není základní počet čipů zahrnutý v ceně.
- Cena jednoho čipu je 44 Kč.
- Podklad k čipu je veden v dokumentu `13-cipy.md` a v datovém souboru `data/cipy.csv`.

### Bytové telefony

- Všechny typy bytového telefonu jsou dostupné pro všechny jednotky.
- Základní varianta telefonu bez doplatku má doplatek 0 Kč.
- Systém nemá předvybírat doporučenou variantu telefonu podle doporučení výboru nebo dodavatele.
- Výbor ani dodavatel nemají doporučenou výchozí variantu pro nerozhodnuté partaje.
- Názvy a ceny variant telefonů mají odpovídat aktuální nabídce nebo ceníku dodavatele.
- Podklady k telefonům jsou vedeny v dokumentu `12-telefonni-varianty.md` a v datovém souboru `data/telefonni-varianty.csv`.

## Doplatky a platby

- Ceny čipů a telefonů jsou pro sběr finální.
- Doplatek se počítá z počtu čipů a zvolené varianty telefonu.
- Formulář má zobrazit finální výši doplatku před odesláním odpovědi.
- Čipy i telefon se hradí jednou společnou platbou.
- Každá objednávka nebo odpověď za jednotku má mít unikátní variabilní symbol.
- Odpověď bez potvrzení finálního doplatku a platebních pokynů nemá být považována za finální.
- Kontrola plateb má být možná porovnáním výpisu z účtu s evidencí podle variabilního symbolu a částky.
- Systém má ideálně umožnit evidovat stav platby a vygenerovat sestavu nezaplacených jednotek.
- Automatické napojení na banku ani automatické párování plateb není požadavkem MVP.

Platební komunikace se má u bytů vlastněných fyzickou osobou vést na kontakt evidovaný u jednotky, typicky na
vlastníka. U nájemních bytů ve vlastnictví SBD Mír má platební komunikace směřovat na nájemníky; SBD Mír nemá
vystupovat jako zprostředkovatel této platby.

## Exporty a výstupy

### Export pro dodavatele

Export pro dodavatele má být tabulka obsahující poslední platnou odpověď za každou jednotku. Pracovní rozsah exportu:

- jméno a příjmení,
- kontakt,
- číslo bytu,
- podlaží,
- počet čipů,
- zvolený typ telefonu.

Finální rozsah osobních a kontaktních údajů je potřeba potvrdit podle skutečných potřeb dodavatele. Dodavatel nemá
dostávat více osobních údajů, než je nezbytné pro objednávku a montáž.

### Výstupy pro výbor

Výbor má mít k dispozici:

- přehled všech jednotek a jejich stavu odpovědi,
- seznam jednotek bez odpovědi,
- seznam zjevných nesrovnalostí k ručnímu ověření,
- finální souhrn objednávky,
- podklad pro kontrolu plateb podle variabilního symbolu a částky,
- sestavu jednotek, které v daném termínu nezaplatily,
- archivní finální souhrn použitý pro objednávku.

Exporty pro dodavatele a hlavní exporty pro výbor se mají generovat až po uzavření sběru objednávek.

## Termíny a provozní pravidla

- Sběr má být spuštěn po publikování verze webu nebo portálu, která umožní evidenci odpovědí.
- Uzávěrka sběru je 2026-05-24.
- Dne 2026-05-19 má výbor zkontrolovat neodpovězené jednotky a poslat e-mailovou urgenci.
- Dne 2026-05-24 má proběhnout finální kontrola úplnosti a zjevných nesrovnalostí.
- Finální souhrn pro dodavatele má být připraven k předání do 2026-05-24.
- Po předání finálního souhrnu dodavateli už se běžně nemá měnit počet čipů ani typ telefonu v rámci objednávky.
- Standardní odpověď se podává online formulářem; odpovědi mimo online formulář nejsou běžnou součástí MVP.

Při finální kontrole má výbor řešit hlavně chybějící odpovědi a zjevné nesrovnalosti, například neplatnou hodnotu
počtu čipů, neobvykle vysoký počet čipů nebo jinou podezřelou hodnotu. Dotčené partaje bude výbor individuálně
kontaktovat.

## Validace a pravidla kvality dat

- Jednotka musí být rozpoznatelná proti seznamu jednotek používanému výborem.
- Počet čipů musí být kladné celé číslo.
- Typ telefonu musí být jedna z výborem schválených variant.
- Variabilní symbol musí být v rámci agendy unikátní.
- Vypočtená částka doplatku musí odpovídat počtu čipů a zvolené variantě telefonu podle finálního ceníku.
- Odpověď bez potvrzení doplatku a platebních pokynů není finální.
- Poslední platná odpověď za jednotku před uzávěrkou je rozhodná pro objednávku.
- Starší odpovědi za stejnou jednotku nemají být použity pro objednávku, ale podle možností systému mají zůstat dohledatelné pro kontrolu.
- Po uzávěrce se nové odpovědi nebo změny zpracují jen individuálně přes výbor.

## Uchování dat a auditní stopa

MVP má umět doložit, z jakých odpovědí výbor při objednávce vycházel. Minimálně má být archivován finální souhrn
použitý pro objednávku a podklady pro kontrolu doplatků.

Uchování historie změn a starších odpovědí závisí na zvoleném systému a pravidlech uchování dat. Pro první agendu je
vhodné uchovat alespoň informaci o tom, která odpověď je finální a kdy byla odeslána. Přesná doba uchování má být
stanovena později podle právního a provozního posouzení.

Sdílený přístup za domácnost nebo jednotku je pro první fázi přijatelný, ale omezuje přesnost auditní stopy konkrétní
osoby. Pro budoucí citlivější agendy, souhlasy, dokumenty nebo hlasování bude potřeba posoudit osobní identitu a
samostatné účty přísněji.

## Provozní pravidla pro náhradní čipy

Evidence ztracených, poškozených a náhradních čipů není hlavní součástí MVP sběru objednávek, ale systémový návrh s ní
má do budoucna počítat.

Procesní pravidla:

- ztracený nebo poškozený čip má být vyřazen z evidence nebo deaktivován,
- náhradní čip si vlastník nebo uživatel objedná u výboru,
- výbor má zvážit objednání rezervních čipů do zásoby pro řešení ztrát a poškození,
- pracovní úvaha pro zásobu je přibližně 60 čipů; finální množství zůstává k rozhodnutí.

## Akceptační kritéria MVP

MVP lze považovat za funkčně splněné, pokud platí:

- každá odpověď je přiřazena ke konkrétní jednotce,
- za každou jednotku lze určit jednu finální odpověď,
- pokud přijde více odpovědí za stejnou jednotku před uzávěrkou, rozhodná je poslední platná odpověď,
- počet čipů je validován jako kladné celé číslo,
- typ telefonu je vybrán z předem daného seznamu,
- formulář zobrazí finální doplatek před odesláním,
- finální odpověď obsahuje potvrzení seznámení s doplatkem a platebními pokyny,
- každá finální odpověď má vypočtenou částku a variabilní symbol,
- výbor umí zjistit, které jednotky dosud neodpověděly,
- výbor umí připravit podklad pro urgenci neodpovězených jednotek,
- výbor umí exportovat finální souhrn pro dodavatele,
- výbor umí připravit podklad pro kontrolu plateb podle variabilního symbolu a částky,
- výbor umí získat sestavu jednotek, které v daném termínu nezaplatily,
- veřejná stránka neobsahuje neveřejná data ani odpovědi jednotlivých jednotek,
- dodavatel nedostává přímý přístup do interní evidence,
- standardní odpověď se podává online formulářem,
- po uzávěrce lze změny řešit pouze individuálně přes výbor,
- finální souhrn použitý pro objednávku lze archivovat.

## Návaznost na technickou specifikaci

Technická specifikace má po výběru technologie doplnit zejména:

- konkrétní způsob přístupu za jednotku,
- datový model,
- návrh formuláře a administrativního přehledu,
- způsob výpočtu variabilního symbolu,
- formát exportů,
- pravidla zabezpečení a správy administrátorů,
- způsob zálohování a archivace,
- postup nasazení a provozu.
