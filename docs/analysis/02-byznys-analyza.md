# Byznys analýza

## Cíl dokumentu

Popsat uživatele, procesy, potřeby a pravidla dříve, než bude vybrána technologie.

## Typy uživatelů

### Veřejný návštěvník

Může jít o vlastníka, nájemníka, dodavatele nebo jinou osobu. Vidí pouze veřejné informace.

### Vlastník jednotky

Potřebuje přístup k informacím, dokumentům, výzvám, formulářům a případně k neveřejným agendám své jednotky.

### Nájemník nebo uživatel bytu

Může potřebovat praktické informace, objednávku čipů, volbu telefonu nebo oznámení provozních problémů.
Je nutné rozhodnout, ve kterých agendách smí jednat samostatně a kde je vyžadováno potvrzení vlastníka.

### Výbor SVJ

Potřebuje publikovat informace, sbírat odpovědi, kontrolovat stav agend, exportovat data a mít přehled o rizicích.

### Dodavatel

Dodavatel typicky nemá mít přístup do systému. Výbor mu předává pouze schválený export nebo souhrn objednávky.

## Veřejná část webu

Možné oblasti:

- základní informace o SVJ,
- kontakty,
- aktuální oznámení,
- veřejné dokumenty,
- informace ke shromáždění,
- informace k projektům domu,
- rozcestník na formuláře a neveřejné agendy.

## Soukromá část webu

Možné oblasti:

- dokumenty určené pouze vlastníkům,
- sběr požadavků a souhlasů,
- správa objednávek za jednotky,
- přehled platebních pokynů,
- hlasování nebo ankety,
- evidence odpovědí a exporty pro výbor.

## První proces: přístupový systém

### Cíl první agendy

Cílem první agendy není zatím vybudovat plnohodnotný portál SVJ, ale bezpečně a srozumitelně získat od každé
partaje jednu použitelnou odpověď pro přípravu objednávky přístupového systému.

Výsledek sběru má výboru umožnit:

- zjistit požadovaný počet čipů za jednotku,
- zjistit zvolený typ bytového telefonu za jednotku,
- rozlišit jednotky, které odpověděly a které neodpověděly,
- připravit objednávkový souhrn pro dodavatele,
- připravit podklady pro doplatky jednotlivých partají,
- doložit, z čeho výbor při objednávce vycházel.

Technologické řešení má být vybráno až po vyjasnění procesních pravidel, citlivosti dat, způsobu ověření osoby
a požadované kvality exportů.

### Pojmy pro první agendu

- Jednotka: byt nebo jiný prostor, ke kterému se objednávka vztahuje.
- Partaj: praktické označení domácnosti nebo skupiny osob užívajících jednotku; v analýze může zahrnovat vlastníka,
  spoluvlastníky, nájemníka nebo jiného uživatele bytu.
- Oprávněná osoba: osoba, které SVJ dovolí vyplnit finální odpověď za jednotku.
- Finální odpověď: poslední platná odpověď za jednotku použitá pro objednávku a doplatek.
- Uzávěrka: datum a čas, po kterém už výbor odpovědi běžně nemění bez individuální domluvy.

### Rozsah sbíraných údajů

Minimální rozsah údajů pro první agendu:

- identifikace jednotky,
- počet požadovaných čipů,
- zvolený typ bytového telefonu,
- potvrzení seznámení s doplatkem nebo budoucí platební povinností,
- datum a čas odeslání odpovědi.

Údaje, které mohou být potřebné, ale mají být sbírány jen při jasném důvodu:

- jméno osoby, která odpověď vyplnila,
- kontaktní e-mail nebo telefon pro řešení nejasností,
- poznámka k nestandardní situaci,
- potvrzení vztahu k jednotce, například vlastník, spoluvlastník, nájemník nebo pověřená osoba.

Údaje, které nejsou pro první agendu zřejmou nutností:

- rodná čísla,
- čísla dokladů,
- kompletní seznam členů domácnosti,
- dlouhodobé uživatelské účty pro všechny vlastníky.

### Pracovní předpoklad k odpovědi za jednotku

Pro další analýzu je vhodné pracovat s variantou jedna finální odpověď za jednotku. Tento předpoklad je potřeba
potvrdit výborem, protože přímo ovlivňuje pravidla pro spoluvlastníky, nájemníky, změny odpovědí a odpovědnost
za doplatek.

Pokud bude povoleno více odpovědí za jednotku, musí být předem určeno, která odpověď je závazná a kdo řeší rozpory.

Pracovní závěr z 2026-05-08: první agenda má být vedena po jednotkách. Odpověď se nemá evidovat jako samostatný
projev konkrétní osoby, ale jako aktuální požadavek dané jednotky. Osoba, která má přístup k odpovědi za jednotku,
může prakticky zadat nebo změnit počet čipů a typ telefonu, protože v první fázi neexistuje samostatný systém,
který by spolehlivě ověřil její totožnost a vztah k jednotce.

Pro byty vlastněné fyzickou osobou zůstává odpovědnost vůči SVJ na vlastníkovi. U bytů ve vlastnictví Stavebního
bytového družstva Mír se předpokládá zvláštní praktický režim: rozhodovat o počtu čipů a typu telefonu má spíše
uživatel bytu, protože je faktickým uživatelem zařízení.

Platební komunikace a výzva k doplatku mají směřovat na kontakt evidovaný u jednotky, typicky na vlastníka bytu.
Nemají se automaticky posílat na nájemníka nebo jinou osobu jen proto, že odpověď vyplnila.

Do uzávěrky se má odpověď za jednotku dát změnit. Pro další práci se předpokládá pravidlo, že platí poslední odpověď
za jednotku před uzávěrkou. Tím se snižuje riziko duplicitních odpovědí za stejnou jednotku.

Do budoucna je vhodným směrem stabilní přístup nebo účet za každou jednotku, který by bylo možné použít i pro další
agendy, například dotazníky, hlasování nebo vkládání zpráv.

### Návrh průběhu

1. Výbor zveřejní informační stránku k přístupovému systému.
2. Výbor předem určí, kdo smí odpověď za jednotku vyplnit a jak se bude řešit spor.
3. Každá jednotka obdrží způsob přístupu k formuláři nebo instrukce k vyplnění.
4. Oprávněná osoba vyplní počet čipů a typ telefonu.
5. Oprávněná osoba potvrdí seznámení s doplatkem nebo s tím, že doplatek bude stanoven podle výsledné objednávky.
6. Systém nebo výbor potvrdí přijetí odpovědi.
7. Do uzávěrky je podle předem daného pravidla možné odpověď opravit nebo nahradit novou odpovědí.
8. Výbor po termínu uzávěrky exportuje souhrn.
9. Výbor zkontroluje jednotky bez odpovědi a rozporné nebo neúplné odpovědi.
10. Výbor připraví objednávku pro dodavatele.
11. Výbor stanoví doplatky a platební instrukce pro jednotlivé partaje.

### Varianty oprávnění k vyplnění

#### Varianta 1: odpovídá pouze vlastník

Výhoda: jasnější odpovědnost za jednotku a doplatek.

Nevýhoda: horší dosažitelnost u pronajímaných bytů, kde praktické potřeby zná nájemník.

#### Varianta 2: odpovídá vlastník nebo nájemník

Výhoda: rychlejší získání praktických údajů od skutečných uživatelů bytu.

Nevýhoda: nutnost pravidla, zda nájemník může zavázat vlastníka k doplatku nebo zda jde jen o technický požadavek.

#### Varianta 3: odpovídá kdokoliv s přístupovým údajem jednotky

Výhoda: jednoduché použití a nízká administrativní zátěž.

Nevýhoda: slabší kontrola identity a vyšší význam správné distribuce přístupových údajů.

Pracovní preference pro první agendu: varianta 3, tedy odpověď za jednotku přes přístup určený pro jednotku. Nejde
o potvrzení identity konkrétní osoby, ale o praktickou evidenci aktuální odpovědi dané jednotky.

### Varianty změny odpovědi

#### Varianta 1: odpověď po odeslání nelze měnit

Jednoduché na řízení, ale zvyšuje počet individuálních oprav přes výbor.

#### Varianta 2: do uzávěrky platí poslední odpověď za jednotku

Praktické pro vlastníky, ale vyžaduje jasnou evidenci času odpovědi a pravidlo pro nahrazení starší odpovědi.

Pracovní preference pro první agendu: tato varianta. Případné opakované vyplnění za stejnou jednotku se má chápat
jako změna odpovědi jednotky, nikoliv jako paralelní odpověď jiné osoby.

#### Varianta 3: změnu potvrzuje výbor

Vhodné u vyšší citlivosti nebo vyšších doplatků, ale zatěžuje administraci.

### Exporty a navazující práce výboru

Export pro dodavatele má pravděpodobně obsahovat jen údaje nutné k objednávce: jednotku, počet čipů a typ telefonu.

Export pro výbor může obsahovat širší údaje: stav odpovědi, čas odeslání, kontaktní údaj pro řešení nejasností,
poznámku, potvrzení doplatku a případně výši doplatku, pokud bude v době exportu známá.

Před návrhem řešení je potřeba odlišit, zda má systém doplatky pouze evidovat jako podklad, nebo je má také počítat.
Automatické párování plateb je mimo rozsah první fáze.

### Otevřená procesní rozhodnutí

- Potvrdit finální formulaci pravidla, že odpověď patří jednotce, ne osobě.
- Potvrdit zvláštní režim pro byty ve vlastnictví Stavebního bytového družstva Mír.
- Potvrdit, zda u spoluvlastnictví stačí jedna osoba jednající za jednotku.
- Potvrdit, že do uzávěrky automaticky platí poslední odpověď za jednotku.
- Jak se řeší jednotka ve spoluvlastnictví?
- Jak se řeší rozpor mezi vlastníkem a nájemníkem?
- Kdo potvrdí finální objednávku a kdo nese odpovědnost za doplatek?
- Jak výbor osloví jednotky, které neodpoví do uzávěrky?
- Má systém počítat doplatek, nebo pouze sbírat podklady?
- Jak dlouho se budou odpovědi uchovávat po dokončení objednávky?

## Prioritizace funkcí

### Nutné pro první agendu

- srozumitelná informační stránka,
- formulář pro odpověď za jednotku,
- evidence odpovědí,
- export pro výbor,
- ochrana proti náhodnému vyplnění cizí jednotky,
- jasný text o doplatku a platební povinnosti,
- pravidlo pro jednu platnou odpověď za jednotku,
- seznam jednotek, proti kterému lze kontrolovat úplnost odpovědí,
- postup pro opravy a pozdní odpovědi.

### Vhodné zlepšení

- možnost úpravy odpovědi do uzávěrky,
- automatické potvrzení e-mailem,
- přehled stavu pro výbor,
- jednoduché připomenutí nevyplněným jednotkám.

### Budoucí možnosti

- uživatelské účty,
- neveřejná dokumentová sekce,
- ankety a hlasování,
- elektronické souhlasy,
- historie požadavků za jednotku.