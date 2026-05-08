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
- potvrzení seznámení s finálním doplatkem a platebními pokyny,
- datum a čas odeslání odpovědi.

Pro samotnou objednávku dodavateli jsou klíčové zejména jednotka, počet čipů a typ telefonu. Ostatní údaje slouží
hlavně výboru pro dohledání odpovědi, řešení nejasností a komunikaci s partají.

Údaje, které mohou být potřebné, ale mají být sbírány jen při jasném důvodu:

- jméno osoby, která odpověď vyplnila,
- kontaktní e-mail nebo telefon pro řešení nejasností,
- poznámka k nestandardní situaci,
- potvrzení vztahu k jednotce, například vlastník, spoluvlastník, nájemník nebo pověřená osoba.

Pravidlo pro identifikaci odpovídající osoby závisí na zvolené technologické a provozní variantě. Pokud bude už při
spuštění agendy existovat obecná portálová identita s rolemi a přístupy, nemá být nutné znovu ručně sbírat údaje,
které systém spolehlivě zná. Pokud půjde o MVP bez nadefinovaných rolí a přístupů, je vhodné u odpovědi sbírat
alespoň jméno osoby, kontaktní údaj pro řešení nejasností a vztah k jednotce, aby výbor věděl, kdo odpověď za jednotku
vyplnil.

Volná poznámka má být povolena pro dotazy a připomínky k agendě přístupového systému. Formulář má uživatele stručně
navést, aby do poznámky neuváděl zbytečné osobní nebo citlivé údaje.

### Čipy a typy telefonů

Počet čipů na jednotku nemá stanovený minimální ani maximální obchodní limit. Z praktického hlediska má formulář
stále pracovat s celým nezáporným číslem. Každý objednaný čip se platí; není určen základní počet čipů zahrnutý
v ceně.

Všechny typy bytového telefonu mají být dostupné pro všechny jednotky. Varianta bez doplatku se má řešit jako
základní verze telefonu s doplatkem 0 Kč, nikoliv jako doporučená volba výboru. Výbor ani dodavatel nemají pro
nerozhodnuté partaje doporučenou výchozí variantu telefonu. Konkrétní názvy a ceny variant je potřeba držet podle
aktuální nabídky nebo ceníku dodavatele.

### Doplatky a kontrola plateb

Ceny čipů i jednotlivých variant bytových telefonů jsou známé a mají být doplněny do podkladů. Pro první agendu se
pracuje s finálními cenami, nikoliv s orientační cenou nebo pozdějším zpřesněním. Formulář má proto zobrazovat
finální výši doplatku podle počtu čipů a zvoleného typu telefonu.

Doplatek za čipy a telefon má být hrazen jednou společnou platbou. Každá objednávka nebo odpověď za jednotku má mít
unikátní variabilní symbol, aby výbor mohl následně zkontrolovat platby proti výpisu z účtu. Kontrola má porovnávat
alespoň variabilní symbol a zaplacenou částku s údaji evidovanými v systému.

Systém má ideálně umožnit evidovat stav platby a vygenerovat sestavu jednotek, které v daném termínu nezaplatily.
Automatické napojení na banku nebo automatické párování plateb není požadavkem první fáze; postačí podklady pro
kontrolu na základě výpisu z účtu.

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

U spoluvlastnictví stačí odpověď jedné osoby jednající za jednotku, protože systém v první fázi nebude ověřovat,
která konkrétní osoba se za jednotku přihlásila.

Platební komunikace a výzva k doplatku mají u bytů vlastněných fyzickou osobou směřovat na kontakt evidovaný
u jednotky, typicky na vlastníka bytu. Oslovováni mají být vlastníci, nikoliv nájemníci. U nájemních bytů ve
vlastnictví Stavebního bytového družstva Mír má platba směřovat na nájemníky a SBD Mír nemá vystupovat jako
zprostředkovatel této platby.

Pokud by se u bytu vlastněného fyzickou osobou ozval vlastník i uživatel bytu s rozdílným požadavkem, je pro
komunikaci vůči SVJ určující vlastník, protože právě vlastník je oficiálně oslovenou osobou.

Do uzávěrky se má odpověď za jednotku dát změnit. Pro další práci se předpokládá pravidlo, že platí poslední odpověď
za jednotku před uzávěrkou. Tím se snižuje riziko duplicitních odpovědí za stejnou jednotku.

Změna odpovědi do uzávěrky má být samoobslužná. Po uzávěrce už nemá být změna dostupná v běžné uživatelské části
systému. Osoba, která potřebuje změnu po uzávěrce, musí kontaktovat výbor individuálně, například e-mailem,
telefonicky nebo přes WhatsApp. Výbor případnou výjimku posoudí a pokud ji přijme, zapíše nebo upraví odpověď
administrativně ze své strany. Jednotky bez odpovědi budou po uzávěrce kontaktovány e-mailem.

Pokud to nebude technicky příliš náročné, je vhodné, aby systém uměl výboru připravit seznam neodpovězených jednotek
včetně evidovaných kontaktů nebo přímo vygenerovat e-mail pro připomenutí. Praktickým zlepšením by bylo také avízo
před uzávěrkou, aby jednotky, které na agendu zapomněly, měly ještě čas odpověď promyslet a odeslat.

Do budoucna je vhodným směrem stabilní přístup nebo účet za každou jednotku, který by bylo možné použít i pro další
agendy, například dotazníky, hlasování nebo vkládání zpráv.

### Návrh průběhu

1. Výbor zveřejní informační stránku k přístupovému systému.
2. Výbor předem určí, kdo smí odpověď za jednotku vyplnit a jak se bude řešit spor.
3. Každá jednotka obdrží způsob přístupu k formuláři nebo instrukce k vyplnění.
4. Oprávněná osoba vyplní počet čipů a typ telefonu.
5. Oprávněná osoba potvrdí seznámení s finálním doplatkem a platebními pokyny.
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
poznámku, potvrzení finálního doplatku, vypočtenou výši doplatku a variabilní symbol.

Před návrhem řešení je potřeba odlišit, zda má systém doplatky pouze evidovat jako podklad, nebo je má také počítat.
Pracovní závěr: systém má doplatek spočítat podle finálních cen a vygenerovat nebo evidovat unikátní variabilní
symbol. Automatické párování plateb je mimo rozsah první fáze, ale systém má podporovat ruční kontrolu plateb proti
výpisu z účtu a sestavu nezaplacených jednotek.

### Otevřená procesní rozhodnutí

- Potvrdit finální formulaci pravidla, že odpověď patří jednotce, ne osobě.
- Kdo potvrdí finální objednávku a kdo nese odpovědnost za doplatek?
- Jak dlouho se budou odpovědi uchovávat po dokončení objednávky?
- Při výběru technologie rozhodnout, zda už bude existovat portálová identita s rolemi, nebo zda MVP musí sbírat identifikaci odpovídající osoby ve formuláři.

## Prioritizace funkcí

### Nutné pro první agendu

- srozumitelná informační stránka,
- formulář pro odpověď za jednotku,
- evidence odpovědí,
- export pro výbor,
- ochrana proti náhodnému vyplnění cizí jednotky,
- jasný text o finálním doplatku, platebních pokynech a variabilním symbolu,
- pravidlo pro jednu platnou odpověď za jednotku,
- seznam jednotek, proti kterému lze kontrolovat úplnost odpovědí,
- postup pro opravy a pozdní odpovědi.

### Vhodné zlepšení

- možnost úpravy odpovědi do uzávěrky,
- automatické potvrzení e-mailem,
- přehled stavu pro výbor,
- jednoduché připomenutí nevyplněným jednotkám,
- vygenerování e-mailu nebo seznamu kontaktů pro jednotky bez odpovědi,
- avízo před uzávěrkou pro jednotky, které dosud neodpověděly.

### Budoucí možnosti

- uživatelské účty,
- neveřejná dokumentová sekce,
- ankety a hlasování,
- elektronické souhlasy,
- historie požadavků za jednotku.