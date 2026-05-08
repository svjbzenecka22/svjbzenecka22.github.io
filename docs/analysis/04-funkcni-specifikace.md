# Funkční specifikace

## Stav dokumentu

Pracovní kostra. Bude doplněna po dokončení byznys analýzy.

## Veřejný web

### Očekávané funkce

- zobrazit hlavní stránku SVJ,
- zobrazit tematické sekce,
- publikovat veřejné dokumenty,
- zobrazit kontakty,
- odkázat na neveřejné nebo formulářové agendy,
- být použitelný na mobilu i počítači.

## Soukromá část

### Očekávané funkce do budoucna

- ověřit oprávnění uživatele,
- zobrazit obsah podle role nebo jednotky,
- ukládat odpovědi a souhlasy,
- umožnit výboru export dat,
- omezit přístup k neveřejným dokumentům,
- rozlišit veřejné dokumenty, dokumenty pro přihlášené vlastníky a uživatele bytů a případně dokumenty vázané ke konkrétní jednotce,
- elektronické hlasování řešit až po změně stanov a samostatném právním a procesním ověření,
- u budoucích elektronických souhlasů nebo hlasování počítat s auditní stopou a pravidly uchování.

Poznámka: dokumenty a hlasování nejsou požadavkem první agendy přístupového systému. Tato oblast má zůstat zatím
rámcově evidovaná pro budoucí rozvoj portálu.

## První agenda: přístupový systém

### Stav specifikace

Tato část je pracovní návrh funkčních požadavků. Nejde zatím o výběr technologie ani o finální návrh obrazovek.
Požadavky je nutné potvrdit po zodpovězení prioritních otázek v byznys analýze.

### Role v první agendě

- Odpovídající osoba: vyplňuje požadavek za jednotku.
- Domácnost nebo jednotkový přístup: pracovní model, kdy přístup prakticky reprezentuje domácnost nebo bytovou jednotku, ne ověřenou identitu každé osoby.
- Výbor: připravuje zadání, sleduje stav odpovědí, řeší výjimky a exportuje data.
- Dodavatel: dostává pouze finální souhrn od výboru, nikoliv přímý přístup do interní evidence.

### Základní pravidla MVP

- Každá jednotka má mít nejvýše jednu finální odpověď použitou pro objednávku.
- Odpověď musí být přiřazena ke konkrétní jednotce.
- Odpověď se v první fázi chápe jako odpověď jednotky, nikoliv jako ověřený osobní úkon konkrétní osoby.
- Rozsah povinných údajů má být co nejmenší.
- Systém nebo proces musí umožnit odlišit poslední platnou odpověď od starších nebo chybných odpovědí.
- Do uzávěrky má být možné odpověď za jednotku změnit; jako finální má být použita poslední odpověď před uzávěrkou.
- Změna odpovědi do uzávěrky má být samoobslužná.
- Po uzávěrce nemá být změna dostupná v běžné uživatelské části systému; výjimky řeší výbor individuálně.
- U spoluvlastnictví stačí jedna odpověď za jednotku.
- Platební komunikace se má u bytů vlastněných fyzickou osobou vést na kontakt evidovaný u jednotky, typicky na vlastníka, ne automaticky na osobu, která odpověď zadala.
- U nájemních bytů ve vlastnictví Stavebního bytového družstva Mír má platební komunikace směřovat na nájemníky.
- Běžný přístup do portálu mají mít vlastníci i nájemníci nebo uživatelé bytů; SBD Mír jako formální vlastník družstevních bytů nemá mít běžný přístup do agend jednotlivých domácností.
- U jednotky nebo domácnosti má být evidován primární kontaktní e-mail a hlavní kontaktní telefon.
- Stabilním identifikátorem má být jednotka, nikoliv samotný e-mail nebo telefon.
- Administrátorský přístup mají mít všichni tři členové výboru.
- Veřejná informační stránka nesmí zobrazovat odpovědi jednotlivých jednotek.
- Standardní způsob podání odpovědi je online formulář; náhradní neonline postup není požadavkem první agendy.

### Funkce pro vlastníka nebo uživatele bytu

- zobrazit informace k objednávce čipů a telefonů,
- vybrat jednotku nebo vstoupit přes přístupový kód,
- zadat počet čipů,
- vybrat typ telefonu,
- uvést vztah k jednotce, pokud to výbor vyžaduje,
- uvést kontaktní údaj pro potvrzení nebo řešení nejasností, pokud to výbor vyžaduje,
- zobrazit finální výši doplatku podle počtu čipů a zvoleného typu telefonu,
- zobrazit platební pokyny včetně částky a variabilního symbolu,
- potvrdit seznámení s finálním doplatkem a platebními pokyny,
- odeslat odpověď,
- obdržet potvrzení o přijetí odpovědi,
- případně upravit odpověď do termínu uzávěrky podle schváleného pravidla.

Poznámka k oprávnění: v první fázi se nepředpokládá spolehlivé ověření osoby proti registru vlastníků nebo nájemníků.
Přístup má proto prakticky reprezentovat jednotku. Do budoucna je vhodné počítat s jednotkovým účtem nebo jiným
stabilním přístupem za jednotku.

### Funkce pro výbor

- zobrazit seznam odpovědí,
- vidět, které jednotky neodpověděly,
- rozlišit platné, nahrazené a neúplné odpovědi,
- opravit zjevnou administrativní chybu se zaznamenáním důvodu,
- administrativně upravit evidovanou odpověď po uzávěrce, pokud výbor schválí výjimku,
- vyfiltrovat jednotky bez odpovědi pro e-mailové připomenutí,
- pokud to zvolená technologie rozumně umožní, vygenerovat e-mail nebo seznam kontaktů pro jednotky bez odpovědi,
- pokud to zvolená technologie rozumně umožní, připravit avízo před uzávěrkou pro jednotky bez odpovědi,
- evidovat finální výši doplatku za jednotku,
- evidovat nebo vygenerovat unikátní variabilní symbol pro platbu,
- porovnat údaje z výpisu z účtu s evidencí podle variabilního symbolu a částky,
- vygenerovat sestavu jednotek, které v daném termínu nezaplatily,
- exportovat souhrn pro dodavatele,
- exportovat pro dodavatele tabulku s poslední platnou odpovědí za jednotku,
- exportovat podklady pro doplatky,
- filtrovat jednotky bez odpovědi pro následné kontaktování,
- uzavřít sběr odpovědí,
- archivovat finální souhrn použitý pro objednávku.

### Datové položky k potvrzení

Povinné položky pravděpodobného MVP:

- jednotka,
- počet čipů,
- typ telefonu,
- potvrzení seznámení s finálním doplatkem a platebními pokyny,
- vypočtená finální výše doplatku,
- variabilní symbol platby,
- čas odeslání odpovědi.

Pokud MVP nebude mít obecnou portálovou identitu s rolemi a přístupy, mají být povinné nebo důrazně doporučené také
údaje o tom, kdo odpověď za jednotku vyplnil:

- jméno odpovídající osoby,
- kontaktní údaj pro řešení nejasností,
- vztah odpovídající osoby k jednotce.

Pro pracovní model domácnosti nebo jednotky mají být evidovány také hlavní kontakty pro komunikaci výboru:

- primární kontaktní e-mail domácnosti nebo jednotky,
- hlavní kontaktní telefon domácnosti nebo jednotky.

Volitelné položky podle rozhodnutí výboru:

- druhý kontaktní údaj, například telefon vedle e-mailu,
- poznámka s dotazem nebo připomínkou k agendě.

Pokud bude existovat obecná portálová identita s rolemi a přístupy, má systém identifikaci odpovídající osoby a její
vztah k jednotce přednostně odvozovat z přihlášení nebo profilu, nikoliv vyžadovat ruční opakované zadání.

### Pravidla pro čipy a telefony

- Počet čipů nemá stanovený horní obchodní limit.
- Počet čipů musí být kladné celé číslo.
- Hodnota 0 čipů je chyba, protože by znamenala nefunkční přístup uživatele jednotky do domu nebo společných částí.
- Každý objednaný čip se platí; není základní počet čipů zahrnutý v ceně.
- Cena jednoho čipu je 44 Kč.
- Podklad k čipu je veden v dokumentu `13-cipy.md` a v datovém souboru `data/cipy.csv`.
- Všechny typy bytového telefonu jsou dostupné pro všechny jednotky.
- Základní varianta telefonu bez doplatku má mít doplatek 0 Kč.
- Systém nemá předvybírat doporučenou variantu telefonu podle doporučení výboru nebo dodavatele.
- Názvy a ceny variant telefonů mají odpovídat aktuální nabídce nebo ceníku dodavatele.
- Podklady k telefonům jsou vedeny v dokumentu `12-telefonni-varianty.md` a v datovém souboru `data/telefonni-varianty.csv`.

### Pravidla pro doplatky a platby

- Ceny čipů a telefonů jsou finální a mají být doplněny do systému nebo podkladů.
- Doplatek má být vypočten z počtu čipů a zvolené varianty telefonu.
- Formulář má zobrazit finální výši doplatku před odesláním odpovědi.
- Čipy i telefon se hradí jednou společnou platbou.
- Každá objednávka nebo odpověď za jednotku má mít unikátní variabilní symbol.
- Kontrola plateb má být možná porovnáním výpisu z účtu s evidencí podle variabilního symbolu a částky.
- Systém má ideálně umožnit evidovat stav platby a vygenerovat sestavu nezaplacených jednotek.
- Automatické napojení na banku není požadavkem první fáze.

### Pravidla pro exporty

- Export pro dodavatele má být tabulka.
- Export pro dodavatele má obsahovat vždy jen poslední platnou odpověď za jednotku.
- Pracovní rozsah exportu pro dodavatele: jméno, příjmení, kontakt, číslo bytu, podlaží, počet čipů a typ telefonu.
- Finální rozsah osobních a kontaktních údajů v exportu je potřeba potvrdit podle skutečných potřeb dodavatele.
- Přehled pro dodavatele a hlavní export pro výbor se mají generovat až po uzavření sběru objednávek.
- Výbor musí umět filtrovat jednotky bez odpovědi.
- Standardní sběr probíhá online formulářem; evidence odpovědí mimo online formulář není požadavkem první agendy.
- Uchování historie změn a starších odpovědí je otevřený bod závislý na zvoleném systému a pravidlech uchování dat.
- Finální souhrn pro dodavatele má být připraven k předání do 2026-05-24.
- Dne 2026-05-19 má výbor zkontrolovat neodpovězené jednotky a poslat e-mailovou urgenci.
- Dne 2026-05-24 má proběhnout finální kontrola úplnosti a zjevných nesrovnalostí, například neplatné hodnoty počtu čipů nebo neobvykle vysokého počtu čipů.
- Po předání finálního souhrnu dodavateli už se běžně nemá měnit počet čipů ani typ telefonu v rámci objednávky.

### Provozní pravidla pro náhradní čipy

- Ztracený nebo poškozený čip má být vyřazen z evidence nebo deaktivován.
- Náhradní čip si vlastník nebo uživatel objedná u výboru.
- Výbor má zvážit objednání rezervních čipů do zásoby pro řešení ztrát a poškození.
- Pracovní úvaha pro zásobu je přibližně 60 čipů; finální množství zůstává k rozhodnutí.

### Pravidla validace k potvrzení

- Počet čipů musí být kladné celé číslo.
- Typ telefonu musí být jedna z výborem schválených variant.
- Jednotka musí být rozpoznatelná proti seznamu jednotek používanému výborem.
- Variabilní symbol musí být v rámci agendy unikátní.
- Vypočtená částka doplatku musí odpovídat počtu čipů a zvolené variantě telefonu podle finálního ceníku.
- Odpověď bez potvrzení finálního doplatku a platebních pokynů nemá být považována za finální.
- Po uzávěrce se nové odpovědi nebo změny zpracují jen individuálně přes výbor a případně administrativním zásahem výboru.
- Volná poznámka má být určena pouze pro dotazy a připomínky k agendě; uživatel má být stručně upozorněn, aby neuváděl zbytečné osobní nebo citlivé údaje.

### Režim online formuláře

První agenda počítá s online formulářem jako jedinou standardní cestou pro odeslání odpovědi. Systém proto nemá v MVP
vyžadovat samostatnou evidenci odpovědí přijatých e-mailem, telefonicky, papírově nebo osobně. Případné výjimečné
opravy po kontaktování partaje řeší výbor individuálně, zejména pokud finální kontrola odhalí chybějící odpověď nebo
zjevnou nesrovnalost.

## Návrh akceptačních kritérií pro první agendu

- Každá odpověď je přiřazena ke konkrétní jednotce.
- Počet čipů je kladné celé číslo.
- Typ telefonu je vybrán z předem daného seznamu.
- Odpovědi lze exportovat do tabulky.
- Každá finální odpověď má vypočtenou finální výši doplatku a variabilní symbol.
- Výbor umí připravit podklad pro kontrolu plateb podle variabilního symbolu a částky.
- Výbor umí získat sestavu jednotek, které v daném termínu nezaplatily.
- Veřejná stránka neobsahuje neveřejná data ani osobní údaje nad nezbytný rozsah.
- Výbor umí zjistit, které jednotky dosud neodpověděly.
- Výbor umí určit finální odpověď za jednotku i v případě opravy nebo opakovaného odeslání formuláře.
- Pokud přijde více odpovědí za stejnou jednotku před uzávěrkou, systém nebo proces umí určit poslední platnou odpověď.
- Export pro dodavatele obsahuje poslední platnou odpověď za jednotku a finální rozsah údajů potvrzený s dodavatelem.
- Standardní odpověď se podává online formulářem; odpovědi mimo online formulář nejsou běžnou součástí MVP.
