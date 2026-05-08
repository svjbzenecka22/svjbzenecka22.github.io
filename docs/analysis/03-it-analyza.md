# IT analýza

## Cíl dokumentu

Porovnat možné technické přístupy a jejich dopady na náklady, bezpečnost, provoz a udržitelnost.

## Základní rozdělení

### Veřejný statický web

Vhodný pro informační obsah, dokumenty a rozcestníky.

Možné technologie:

- GitHub Pages s čistým HTML/CSS,
- statický generátor,
- později framework se statickým exportem.

### Soukromá datová část

Potřebuje databázi, autentizaci nebo alespoň řízený přístup a administrativní výstupy.

GitHub Pages samo o sobě nestačí, protože neumí serverovou logiku ani bezpečné ukládání dat.

## Kandidátní řešení pro první agendu

### Varianta A: Google Forms / Google Sheets

Silné stránky:

- velmi rychlé spuštění,
- nulové náklady,
- jednoduchý export,
- nízká technická náročnost.

Slabé stránky:

- horší uživatelský dojem,
- slabší řízení přístupu,
- horší kontrola jedné odpovědi za jednotku,
- menší flexibilita pro budoucí portál.

### Varianta B: Google Sheets + Apps Script

Silné stránky:

- stále bez nákladů,
- možnost vlastního formuláře,
- data v tabulce,
- možnost doplnit jednoduchou logiku.

Slabé stránky:

- omezenější technická čistota,
- vyšší riziko křehkého řešení,
- závislost na Google účtu a skriptech.

### Varianta C: Vercel nebo Netlify + Supabase free tarif

Silné stránky:

- databáze,
- lepší formuláře,
- možnost přístupových kódů nebo přihlášení,
- dobrý základ pro budoucí portál.

Slabé stránky:

- více technické práce,
- free tarify nejsou garantované navždy,
- nutnost řešit bezpečnostní pravidla databáze.

### Varianta D: vlastní server nebo placený hosting

Silné stránky:

- vysoká kontrola nad řešením,
- možnost provozovat plnohodnotnou aplikaci.

Slabé stránky:

- pravidelné náklady,
- správa serveru,
- vyšší provozní odpovědnost.

## Bezpečnostní a provozní témata

- ochrana osobních údajů,
- oddělení veřejných a neveřejných dat,
- řízení přístupu za jednotku,
- audit změn odpovědí,
- zálohování a export,
- správa administrátorů,
- ukončení free služby nebo změna jejích podmínek.

## Platební kontrola první agendy

První agenda má pracovat s finálními cenami čipů a telefonů a má umět určit výsledný doplatek za jednotku. Každá
objednávka nebo odpověď za jednotku má mít unikátní variabilní symbol.

Pro MVP není požadováno automatické napojení na banku ani automatické párování plateb. Důležitější je, aby výbor
mohl porovnat výpis z účtu s evidencí podle variabilního symbolu a částky a následně získat sestavu jednotek, které
v daném termínu nezaplatily.

## Exporty a uchování dat první agendy

Export pro dodavatele má být pracovně tabulka obsahující poslední platnou odpověď za jednotku. Předpokládané údaje
jsou jméno, příjmení, kontakt, číslo bytu, podlaží, počet čipů a typ telefonu. Rozsah osobních a kontaktních údajů
je potřeba před spuštěním potvrdit podle skutečných potřeb dodavatele.

Systém má umožnit generovat export až po uzavření sběru objednávek a průběžně filtrovat jednotky bez odpovědi.
Délka uchování odpovědí a historie změn zatím není stanovena. Technicky může být uchování v řádu měsíců nebo let,
ale konkrétní rozhodnutí závisí na zvoleném systému, kapacitě databáze, pravidlech zálohování a pravidlech uchování dat.

## Předběžné doporučení

Pro veřejný web ponechat GitHub Pages.

Pro první datovou agendu vybrat až po doplnění odpovědí na procesní otázky. Pokud bude hlavní důraz na rychlost
a nulové náklady, začít variantou Google Forms nebo Google Sheets. Pokud má být první agenda základem budoucího
soukromého portálu, zvážit Supabase a jednoduchou webovou aplikaci.