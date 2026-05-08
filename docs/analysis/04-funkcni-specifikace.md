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
- omezit přístup k neveřejným dokumentům.

## První agenda: přístupový systém

### Stav specifikace

Tato část je pracovní návrh funkčních požadavků. Nejde zatím o výběr technologie ani o finální návrh obrazovek.
Požadavky je nutné potvrdit po zodpovězení prioritních otázek v byznys analýze.

### Role v první agendě

- Odpovídající osoba: vyplňuje požadavek za jednotku.
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
- Veřejná informační stránka nesmí zobrazovat odpovědi jednotlivých jednotek.
- Online řešení musí mít náhradní administrativní postup pro osoby, které neodpoví online.

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
- rozlišit platné, nahrazené, neúplné a ručně doplněné odpovědi,
- doplnit odpověď přijatou mimo online formulář,
- opravit zjevnou administrativní chybu se zaznamenáním důvodu,
- administrativně zapsat nebo upravit odpověď po uzávěrce, pokud výbor schválí výjimku,
- vyfiltrovat jednotky bez odpovědi pro e-mailové připomenutí,
- pokud to zvolená technologie rozumně umožní, vygenerovat e-mail nebo seznam kontaktů pro jednotky bez odpovědi,
- pokud to zvolená technologie rozumně umožní, připravit avízo před uzávěrkou pro jednotky bez odpovědi,
- evidovat finální výši doplatku za jednotku,
- evidovat nebo vygenerovat unikátní variabilní symbol pro platbu,
- porovnat údaje z výpisu z účtu s evidencí podle variabilního symbolu a částky,
- vygenerovat sestavu jednotek, které v daném termínu nezaplatily,
- exportovat souhrn pro dodavatele,
- exportovat podklady pro doplatky,
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

Volitelné položky podle rozhodnutí výboru:

- druhý kontaktní údaj, například telefon vedle e-mailu,
- poznámka s dotazem nebo připomínkou k agendě,
- informace, zda jde o ručně doplněnou odpověď výborem.

Pokud bude existovat obecná portálová identita s rolemi a přístupy, má systém identifikaci odpovídající osoby a její
vztah k jednotce přednostně odvozovat z přihlášení nebo profilu, nikoliv vyžadovat ruční opakované zadání.

### Pravidla pro čipy a telefony

- Počet čipů nemá stanovený minimální ani maximální obchodní limit.
- Počet čipů musí být celé nezáporné číslo.
- Každý objednaný čip se platí; není základní počet čipů zahrnutý v ceně.
- Všechny typy bytového telefonu jsou dostupné pro všechny jednotky.
- Základní varianta telefonu bez doplatku má mít doplatek 0 Kč.
- Systém nemá předvybírat doporučenou variantu telefonu podle doporučení výboru nebo dodavatele.
- Názvy a ceny variant telefonů mají odpovídat aktuální nabídce nebo ceníku dodavatele.

### Pravidla pro doplatky a platby

- Ceny čipů a telefonů jsou finální a mají být doplněny do systému nebo podkladů.
- Doplatek má být vypočten z počtu čipů a zvolené varianty telefonu.
- Formulář má zobrazit finální výši doplatku před odesláním odpovědi.
- Čipy i telefon se hradí jednou společnou platbou.
- Každá objednávka nebo odpověď za jednotku má mít unikátní variabilní symbol.
- Kontrola plateb má být možná porovnáním výpisu z účtu s evidencí podle variabilního symbolu a částky.
- Systém má ideálně umožnit evidovat stav platby a vygenerovat sestavu nezaplacených jednotek.
- Automatické napojení na banku není požadavkem první fáze.

### Pravidla validace k potvrzení

- Počet čipů musí být celé nezáporné číslo.
- Typ telefonu musí být jedna z výborem schválených variant.
- Jednotka musí být rozpoznatelná proti seznamu jednotek používanému výborem.
- Variabilní symbol musí být v rámci agendy unikátní.
- Vypočtená částka doplatku musí odpovídat počtu čipů a zvolené variantě telefonu podle finálního ceníku.
- Odpověď bez potvrzení finálního doplatku a platebních pokynů nemá být považována za finální.
- Po uzávěrce se nové odpovědi nebo změny zpracují jen individuálně přes výbor a případně administrativním zásahem výboru.
- Volná poznámka má být určena pouze pro dotazy a připomínky k agendě; uživatel má být stručně upozorněn, aby neuváděl zbytečné osobní nebo citlivé údaje.

### Náhradní neonline postup

První agenda má počítat s tím, že některé partaje nevyužijí online formulář. Výbor proto potřebuje jednoduchý postup,
jak odpověď získanou e-mailem, telefonicky, papírově nebo osobně převést do stejné evidence a označit ji jako ručně
doplněnou.

## Návrh akceptačních kritérií pro první agendu

- Každá odpověď je přiřazena ke konkrétní jednotce.
- Počet čipů je celé nezáporné číslo.
- Typ telefonu je vybrán z předem daného seznamu.
- Odpovědi lze exportovat do tabulky.
- Každá finální odpověď má vypočtenou finální výši doplatku a variabilní symbol.
- Výbor umí připravit podklad pro kontrolu plateb podle variabilního symbolu a částky.
- Výbor umí získat sestavu jednotek, které v daném termínu nezaplatily.
- Veřejná stránka neobsahuje neveřejná data ani osobní údaje nad nezbytný rozsah.
- Výbor umí zjistit, které jednotky dosud neodpověděly.
- Výbor umí určit finální odpověď za jednotku i v případě opravy nebo ručního doplnění.
- Pokud přijde více odpovědí za stejnou jednotku před uzávěrkou, systém nebo proces umí určit poslední platnou odpověď.
- Export pro dodavatele neobsahuje údaje, které dodavatel nepotřebuje.
- Existuje postup pro odpovědi mimo online formulář.
