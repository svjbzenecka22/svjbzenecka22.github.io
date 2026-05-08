# IT analýza

## Cíl dokumentu

Porovnat možné technické přístupy a jejich dopady na náklady, bezpečnost, provoz a udržitelnost.

## Základní rozdělení

Strategický požadavek z 2026-05-08: technické řešení má hledat rovnováhu mezi rychlým spuštěním první agendy a
rozumnou dlouhodobou architekturou. První verze nemá být zbytečně rozsáhlá, ale nemá ani vytvořit slepou uličku, která
by později vyžadovala výrazný refaktoring.

Před finálním výběrem technologie má být připraveno srovnání nákladů a funkcionality. Vedle vlastní nízkonákladové
varianty je vhodné porovnat také hotové portály pro SVJ nebo bytové domy dostupné na trhu. Pracovní rozpočtová ambice
je velmi nízký provoz, orientačně kolem 100 Kč měsíčně, ale reálnost této hranice zatím není potvrzena.

Hlavní architektonické body, které je potřeba vyřešit ještě před implementací první agendy:

- oddělení veřejné a neveřejné části,
- způsob evidence odpovědí a změn,
- export dat pro výbor a dodavatele,
- přístupová práva nebo přístup za jednotku,
- možnost budoucího rozšíření na dokumenty, další agendy a případně portálové funkce.

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

### Varianta E: hotový portál pro SVJ nebo bytový dům

Silné stránky:

- hotové funkce pro správu domu,
- pravděpodobně vyřešená přístupová práva a role,
- nižší vývojová zátěž výboru,
- možná podpora dokumentů, komunikace, požadavků nebo hlasování podle konkrétní služby.

Slabé stránky:

- pravidelné náklady mohou překročit nízký rozpočtový cíl,
- menší kontrola nad vzhledem, daty a integrací s vlastním webem,
- závislost na dodavateli služby,
- nutnost ověřit export dat, migraci, právní podmínky a rozsah funkcí.

Poznámka: konkrétní portály, ceny a funkce je potřeba doplnit v samostatném srovnání. Toto srovnání má být jedním z
podkladů pro rozhodnutí, zda pokračovat vlastním nízkonákladovým řešením, nebo zvolit hotovou službu.

## Bezpečnostní a provozní témata

- ochrana osobních údajů,
- oddělení veřejných a neveřejných dat,
- řízení přístupu za jednotku,
- pracovní model domácnosti nebo jednotky s primárním kontaktním e-mailem a telefonem,
- audit změn odpovědí,
- zálohování a export,
- správa administrátorů,
- ukončení free služby nebo změna jejích podmínek.

Pracovní model přístupu z 2026-05-09 počítá spíše s přístupem za domácnost nebo jednotku než s plnohodnotným osobním
účtem pro každého vlastníka, spoluvlastníka nebo nájemníka. Primární e-mail a telefon mohou sloužit pro komunikaci a
případně jako praktický přístupový údaj, ale stabilním identifikátorem má zůstat jednotka. Sdílený login v rámci
domácnosti je pro první fázi přijatelný, ale omezuje přesnost auditní stopy konkrétní osoby.

Administrátorský přístup mají mít všichni tři členové výboru. Zvolená technologie proto musí umožnit více
administrátorů a ideálně rozumné oddělení běžného uživatelského přístupu od administrace výboru.

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

Pro podklady k typům telefonů je vhodné pracovat s tabulkou variant, která bude obsahovat název, cenu, stručný popis
a odkaz na obrázek. Obrázky je vhodné držet jako samostatné soubory v repozitáři nebo ve zvoleném úložišti podle
budoucí technologie.

Finální souhrn má být dodavateli předán do 2026-05-24. Přibližně 5 dní před tímto termínem má systém nebo evidence
umožnit zjistit neodpovězené jednotky pro ruční e-mailovou urgenci. Po předání finálního souhrnu už se běžně nemají
měnit počty čipů ani typy telefonů v rámci objednávky.

Budoucí provoz bude potřebovat evidenci ztracených, poškozených a náhradních čipů. Minimálně procesně je nutné umět
ztracený nebo poškozený čip deaktivovat nebo vyřadit z evidence a objednat náhradu přes výbor. Rozhodnutí, zda tato
evidence bude součástí stejného systému jako první sběr, je otevřený technický bod.

## Vyhodnocení variant proti MVP specifikaci

Po doplnění funkční specifikace MVP z 2026-05-09 je možné varianty posoudit konkrétněji.

### Varianta A: Google Forms / Google Sheets

Tato varianta je nejrychlejší a provozně nejlevnější, ale hůře splňuje klíčové požadavky MVP. Slabým místem je hlavně
řízení jedné poslední platné odpovědi za jednotku, samoobslužná změna odpovědi do uzávěrky, přístup za jednotku,
výpočet doplatku před odesláním a administrátorský přehled pro tři členy výboru.

Závěr: vhodné jen jako nouzový fallback, pokud by nebylo možné včas připravit lepší řešení.

### Varianta B: Google Sheets + Apps Script

Tato varianta umí oproti čistému Google Forms doplnit vlastní formulář, výpočet doplatku, práci s jednotkami a
jednoduchou administraci nad tabulkou. Stále může běžet s nulovými přímými náklady a rychleji než plnohodnotná
aplikace.

Slabým místem je dlouhodobá udržitelnost, křehkost skriptů, omezené bezpečnostní modelování a horší návaznost na
budoucí portál SVJ.

Závěr: přijatelný fallback pro rychlé MVP, pokud by rozhodovala hlavně rychlost a nulový provozní náklad.

### Varianta C: jednoduchá webová aplikace + Supabase

Tato varianta nejlépe odpovídá MVP specifikaci i dlouhodobému směru portálu. Umožňuje samostatnou databázi, přístup za
jednotku, administrátorský přístup pro více členů výboru, výpočet doplatků, filtrování neodpovězených jednotek,
exporty a pozdější rozšíření na další agendy.

Veřejný web může zůstat na GitHub Pages a pouze odkazovat na neveřejnou datovou agendu. Samotná agenda může běžet jako
jednoduchá webová aplikace hostovaná odděleně, například přes Vercel nebo Netlify, s datovou vrstvou v Supabase. Pokud
se ukáže, že serverless funkce nejsou nutné, může být frontend technicky velmi jednoduchý; citlivá data ale musí zůstat
mimo veřejný repozitář a mimo GitHub Pages.

Slabým místem je vyšší implementační náročnost a nutnost pečlivě nastavit přístupová pravidla databáze. Free tarify
také nejsou garantované navždy.

Závěr: doporučený pracovní směr pro MVP, pokud je cílem nezablokovat budoucí portál a současně držet nízké náklady.

### Varianta D: vlastní server nebo placený hosting

Tato varianta by splnila technické požadavky, ale je zbytečně provozně náročná pro první agendu. Přináší správu
serveru, aktualizace, monitoring a pravidelné náklady.

Závěr: pro MVP první agendy nedoporučeno.

### Varianta E: hotový portál pro SVJ nebo bytový dům

Hotový portál může být vhodný pro dlouhodobý směr, zejména pro dokumenty, komunikaci, požadavky, případně budoucí
hlasování. Pro aktuální agendu ale pravděpodobně znamená smluvní, cenové a migrační rozhodování, které může být pomalé
vzhledem k termínu 2026-05-24.

Závěr: vhodné dál porovnat pro dlouhodobou strategii, ale nemělo by blokovat MVP první agendy.

## Předběžné doporučení

Pro veřejný web ponechat GitHub Pages.

Pro MVP první datové agendy dále rozpracovat variantu jednoduché webové aplikace s datovou vrstvou Supabase a
samostatným hostingem aplikační části. Variantu Google Sheets + Apps Script držet jako záložní cestu, pokud by se
ukázalo, že doporučený směr není možné včas bezpečně dokončit. Hotové portály pro SVJ porovnat samostatně pro
dlouhodobý rozvoj, ne jako blokující podmínku aktuálního sběru.