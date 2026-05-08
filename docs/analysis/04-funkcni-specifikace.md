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
- Rozsah povinných údajů má být co nejmenší.
- Systém nebo proces musí umožnit odlišit poslední platnou odpověď od starších nebo chybných odpovědí.
- Veřejná informační stránka nesmí zobrazovat odpovědi jednotlivých jednotek.
- Online řešení musí mít náhradní administrativní postup pro osoby, které neodpoví online.

### Funkce pro vlastníka nebo uživatele bytu

- zobrazit informace k objednávce čipů a telefonů,
- vybrat jednotku nebo vstoupit přes přístupový kód,
- zadat počet čipů,
- vybrat typ telefonu,
- uvést vztah k jednotce, pokud to výbor vyžaduje,
- uvést kontaktní údaj pro potvrzení nebo řešení nejasností, pokud to výbor vyžaduje,
- potvrdit seznámení s doplatkem,
- odeslat odpověď,
- obdržet potvrzení o přijetí odpovědi,
- případně upravit odpověď do termínu uzávěrky podle schváleného pravidla.

### Funkce pro výbor

- zobrazit seznam odpovědí,
- vidět, které jednotky neodpověděly,
- rozlišit platné, nahrazené, neúplné a ručně doplněné odpovědi,
- doplnit odpověď přijatou mimo online formulář,
- opravit zjevnou administrativní chybu se zaznamenáním důvodu,
- exportovat souhrn pro dodavatele,
- exportovat podklady pro doplatky,
- uzavřít sběr odpovědí,
- archivovat finální souhrn použitý pro objednávku.

### Datové položky k potvrzení

Povinné položky pravděpodobného MVP:

- jednotka,
- počet čipů,
- typ telefonu,
- potvrzení seznámení s doplatkem nebo budoucí platební povinností,
- čas odeslání odpovědi.

Volitelné položky podle rozhodnutí výboru:

- jméno odpovídající osoby,
- vztah odpovídající osoby k jednotce,
- e-mail,
- telefon,
- poznámka,
- informace, zda jde o ručně doplněnou odpověď výborem.

### Pravidla validace k potvrzení

- Počet čipů musí být celé číslo v povoleném rozsahu.
- Typ telefonu musí být jedna z výborem schválených variant.
- Jednotka musí být rozpoznatelná proti seznamu jednotek používanému výborem.
- Odpověď bez potvrzení doplatku nebo platební povinnosti nemá být považována za finální.
- Po uzávěrce se nové odpovědi nebo změny zpracují jen podle pravidla stanoveného výborem.

### Náhradní neonline postup

První agenda má počítat s tím, že některé partaje nevyužijí online formulář. Výbor proto potřebuje jednoduchý postup,
jak odpověď získanou e-mailem, telefonicky, papírově nebo osobně převést do stejné evidence a označit ji jako ručně
doplněnou.

## Návrh akceptačních kritérií pro první agendu

- Každá odpověď je přiřazena ke konkrétní jednotce.
- Počet čipů je číselná hodnota v povoleném rozsahu.
- Typ telefonu je vybrán z předem daného seznamu.
- Odpovědi lze exportovat do tabulky.
- Veřejná stránka neobsahuje neveřejná data ani osobní údaje nad nezbytný rozsah.
- Výbor umí zjistit, které jednotky dosud neodpověděly.
- Výbor umí určit finální odpověď za jednotku i v případě opravy nebo ručního doplnění.
- Export pro dodavatele neobsahuje údaje, které dodavatel nepotřebuje.
- Existuje postup pro odpovědi mimo online formulář.