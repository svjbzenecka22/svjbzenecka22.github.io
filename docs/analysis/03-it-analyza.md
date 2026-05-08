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

## Předběžné doporučení

Pro veřejný web ponechat GitHub Pages.

Pro první datovou agendu vybrat až po doplnění odpovědí na procesní otázky. Pokud bude hlavní důraz na rychlost
a nulové náklady, začít variantou Google Forms nebo Google Sheets. Pokud má být první agenda základem budoucího
soukromého portálu, zvážit Supabase a jednoduchou webovou aplikaci.