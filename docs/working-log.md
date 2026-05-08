# Pracovní záznam projektu

Datum založení záznamu: 2026-05-08

## Smysl dokumentu

Tento dokument slouží jako průběžný pracovní záznam k projektu webu SVJ Bzenecká 22, Brno,
aby bylo možné navázat na dosavadní úvahy i mimo aktuální chat.

Nejde o doslovný export konverzace, ale o stručný a verzovatelný záznam rozhodnutí, pracovních úvah
a otevřených bodů.

## Dosavadní rozhodnutí

1. Projekt bude veden jako jeden sjednocený web SVJ, nikoli jako sada zcela oddělených webů bez hlavní stránky.
2. Pracovní lokální adresář je založen v `C:\Projects\Active\Private\svj-bzenecka-22-web`.
3. Dva existující weby byly vybrány jako výchozí obsah pro první sjednocení:
   - `https://github.com/svjbzenecka22/shromazdeni_260427.git`
   - `https://github.com/svjbzenecka22/balkony.git`
4. Hlavní veřejný web má být dlouhodobě koncipován jako jedna zastřešující stránka s tematickými sekcemi.
5. Pro budoucí neveřejné nebo datové funkce, například sběr údajů k přístupovému systému, není GitHub Pages samo o sobě dostačující.
6. Rozpočet projektu má být pokud možno nulový nebo co nejnižší.

## Co bylo uděláno

1. Byl založen pracovní adresář pro nový sjednocený projekt.
2. Byly naklonovány dva existující repozitáře jako výchozí obsah.
3. Byla vytvořena hlavní stránka `index.html`, která slouží jako rozcestník na aktuální sekce webu.
4. Byl založen tento pracovní záznam a základní README.

## Otevřené otázky pro další analýzu

1. Jaké sekce má mít budoucí oficiální web SVJ v první verzi a jaké až později.
2. Co má být veřejně dostupné a co nesmí být zveřejněno na veřejném webu.
3. Jak bude probíhat správa obsahu a kdo bude web upravovat.
4. Zda má budoucí část k přístupovému systému fungovat jen informativně, nebo i jako neveřejná aplikace pro sběr objednávek.
5. Jak silný má být přístupový režim pro neveřejné části a jaké údaje se budou sbírat.
6. Zda bude celý projekt publikován jako GitHub Pages web v repozitáři `svjbzenecka22.github.io`.

## Doporučený další postup

1. Udělat pečlivou analýzu budoucích očekávání od webu.
2. Rozdělit očekávání na veřejnou část a případnou neveřejnou aplikační část.
3. Až poté rozhodnout o výsledné technologii a publikační architektuře.

## Navazující analytická dokumentace

Dne 2026-05-08 byla založena složka `docs/analysis/` jako pracovní prostor pro standardní vývojový cyklus:
byznys zadání, byznys analýza, IT analýza, funkční specifikace, technická specifikace, implementační plán a testy.

Prvním konkrétním use casem pro analýzu je sekce k přístupovému systému, zejména sběr počtu čipů a volby typu
bytového telefonu za jednotlivé partaje.

## Průběžný záznam 2026-05-08: rozpracování první agendy

Byla rozšířena analýza první agendy přístupového systému bez výběru technologie. Důraz je na procesní pravidla,
zejména jednu finální odpověď za jednotku, oprávněnou osobu, možnost změny odpovědi, rozsah sbíraných údajů,
doplatky, exporty a náhradní neonline postup.

Další krok je položit prioritní otázky výboru a dodavateli, aby bylo možné rozhodnout, zda první agenda potřebuje
jen jednoduchý formulářový sběr, nebo robustnější neveřejnou datovou část.

## Průběžný záznam 2026-05-08: odpověď k pravidlu za jednotku

Byla zodpovězena první skupina prioritních otázek k tomu, kdo odesílá odpověď za jednotku. Pracovní závěr je, že
první agenda se má vést po jednotkách, ne po osobách. Přístup k odpovědi za jednotku má prakticky reprezentovat
danou jednotku, protože zatím neexistuje samostatný systém ověření osoby proti evidenci vlastníků nebo nájemníků.

Do uzávěrky se má odpověď za jednotku dát změnit a jako finální má platit poslední odpověď za jednotku. U bytů
vlastněných fyzickou osobou zůstává odpovědnost vůči SVJ na vlastníkovi. U bytů ve vlastnictví Stavebního bytového
družstva Mír se předpokládá praktická role uživatele bytu při volbě čipů a telefonu.

Doplnění: u spoluvlastnictví stačí odpověď jedné osoby jednající za jednotku. U bytů vlastněných fyzickou osobou
budou oficiálně oslovováni vlastníci, nikoliv nájemníci. U nájemních bytů ve vlastnictví Stavebního bytového družstva
Mír má platba směřovat na nájemníky a SBD Mír nemá vystupovat jako zprostředkovatel platby.

## Průběžný záznam 2026-05-08: změny a uzávěrka

Byla doplněna pravidla pro změny odpovědí. Do uzávěrky má být změna odpovědi za jednotku samoobslužná a jako finální
má platit poslední odpověď za jednotku. Po uzávěrce už se změny nemají řešit běžnou uživatelskou částí systému;
odpovídající osoba musí kontaktovat výbor individuálně e-mailem, telefonicky nebo přes WhatsApp.

Výjimky po uzávěrce řeší výbor. Pokud výbor pozdní změnu přijme, zapíše ji nebo upraví administrativně ze své strany.
Jednotky bez odpovědi mají být kontaktovány e-mailem.
