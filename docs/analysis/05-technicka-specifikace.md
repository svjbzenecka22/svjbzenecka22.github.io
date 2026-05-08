# Technická specifikace

## Stav dokumentu

Pracovní technický návrh k 2026-05-09. Dokument navazuje na funkční specifikaci MVP první agendy a rozpracovává
doporučený technický směr. Nejde ještě o detailní implementační dokument ani o hotový datový model v SQL.

## Současný stav

- Hlavní veřejný web běží z repozitáře `svjbzenecka22.github.io`.
- Zdrojový kód je lokálně v `C:\Projects\Active\Private\svj-bzenecka-22-web`.
- Web je nyní statický HTML/CSS bez build procesu.
- Existující sekce jsou umístěny ve složkách:
  - `shromazdeni_260427/`,
  - `balkony/`.

## Technické principy

- Veřejný web má být jednoduchý a stabilní.
- Citlivá data nemají být ukládána do GitHub Pages ani do veřejného repozitáře.
- Formulářové a neveřejné agendy mají být řešeny oddělenou datovou vrstvou.
- Každé řešení musí mít možnost exportu dat mimo aplikaci.
- Technické řešení první agendy nemá být slepou uličkou pro budoucí portál.
- Správa musí být možná pro všechny tři členy výboru.

## Doporučený pracovní směr

Pro MVP první agendy se jako pracovní technický směr doporučuje jednoduchá webová aplikace s oddělenou datovou vrstvou:

- veřejný web zůstává na GitHub Pages,
- veřejný web odkazuje na samostatnou aplikační část pro sběr odpovědí,
- aplikační část běží odděleně, například přes Vercel nebo Netlify,
- data jsou uložena v Supabase,
- administrátorský přístup výboru je oddělen od běžného přístupu za jednotku,
- exporty jsou dostupné výboru, nikoliv dodavateli přímo.

Tento směr lépe splňuje požadavky MVP než čistý Google Forms, zejména poslední platnou odpověď za jednotku, změny do
uzávěrky, administrátorský přehled, výpočet doplatků, exporty a budoucí rozšíření na další agendy.

## Záložní technický směr

Záložní variantou je Google Sheets + Apps Script s vlastním formulářem a tabulkovou evidencí. Tato varianta může být
rychlejší a levnější na spuštění, ale hůře navazuje na budoucí portál a má slabší bezpečnostní model.

Čistý Google Forms / Google Sheets ponechat jen jako nouzovou variantu, protože hůře splňuje požadavky na přístup za
jednotku, změny odpovědi a administraci výboru.

## Navržená architektura MVP

### Veřejná část

Veřejná část zůstává statická. Obsahuje informace o SVJ a případně veřejnou informační stránku k přístupovému systému.
Nesmí obsahovat neveřejné odpovědi, seznamy jednotek s kontakty ani interní exporty.

### Aplikační část

Aplikační část má obsahovat:

- online formulář pro odpověď za jednotku,
- přehled a detail odpovědi za jednotku,
- možnost změny odpovědi do uzávěrky,
- administrátorský přehled pro výbor,
- export finálního souhrnu pro dodavatele,
- export nebo sestavu pro kontrolu plateb.

### Datová část

Datová část má být mimo veřejný repozitář. Má ukládat jednotky, kontakty, varianty telefonů, odpovědi, stavy odpovědí,
variabilní symboly, výpočty doplatků a případně stav platby.

## Přístup a oprávnění

### Přístup za jednotku

První agenda nemá ověřovat osobní identitu každého vlastníka, spoluvlastníka nebo nájemníka. Pracovní model je přístup
za jednotku nebo domácnost.

Technicky to může znamenat například jedinečný přístupový odkaz nebo přístupový kód pro každou jednotku. Přístup musí
umožnit zobrazit a změnit pouze odpověď dané jednotky do uzávěrky. Nesmí umožnit procházet odpovědi jiných jednotek.

### Administrátorský přístup

Administrátorský přístup mají mít všichni tři členové výboru. Administrátor má vidět stav všech jednotek, filtrovat
neodpovězené jednotky, exportovat data a po uzávěrce řešit schválené výjimky.

Administrátorský přístup má být oddělen od přístupu za jednotku. Dodavatel administrátorský přístup nemá.

## Návrh datového modelu

Pracovní datové entity:

- `units`: bytové jednotky a základní identifikace jednotky,
- `unit_contacts`: primární e-mail a telefon jednotky nebo domácnosti,
- `phone_variants`: dostupné varianty bytových telefonů a jejich ceny,
- `chip_product`: cena čipu a případné základní parametry,
- `unit_access`: přístupové údaje nebo tokeny pro jednotky,
- `responses`: odpovědi jednotek, počet čipů, typ telefonu, potvrzení doplatku a čas odeslání,
- `response_history`: starší nebo nahrazené odpovědi, pokud to zvolená implementace oddělí od hlavní tabulky,
- `payments`: variabilní symbol, očekávaná částka a stav platby,
- `admin_users`: členové výboru s administrátorským oprávněním,
- `exports`: evidence vytvořených finálních exportů nebo archivních souhrnů.

Minimální implementace může některé entity sloučit, pokud tím neutrpí přehlednost, bezpečnost a exporty.

## Pravidla odpovědí

- Každá odpověď musí být přiřazena ke konkrétní jednotce.
- Do uzávěrky může být odpověď jednotky změněna samoobslužně.
- Pro objednávku se použije poslední platná odpověď za jednotku před uzávěrkou.
- Starší odpovědi nesmí vstupovat do finální objednávky.
- Po uzávěrce může změnu provést jen výbor administrativně a pouze jako výjimku.
- Odpověď bez potvrzení doplatku a platebních pokynů není finální.

## Výpočet doplatku a variabilní symbol

Doplatek se počítá podle vzorce:

```text
doplatek = počet čipů * cena jednoho čipu + doplatek zvolené varianty telefonu
```

Cena jednoho čipu je v pracovních podkladech 44 Kč. Varianty telefonů a jejich ceny se mají načítat z datového podkladu
nebo databázové tabulky odpovídající dokumentu `12-telefonni-varianty.md`.

Variabilní symbol musí být v rámci agendy unikátní. Konkrétní pravidlo tvorby variabilního symbolu je potřeba doplnit
před implementací, například podle čísla jednotky a identifikátoru agendy.

## Exporty

Systém má umožnit alespoň tyto exporty:

- finální souhrn pro dodavatele s poslední platnou odpovědí za jednotku,
- přehled pro výbor se stavem odpovědí všech jednotek,
- seznam jednotek bez odpovědi pro urgenci,
- podklad pro kontrolu plateb podle variabilního symbolu a částky,
- seznam jednotek bez zaplaceného doplatku po termínu platby.

Exportní formát má být tabulkový, minimálně CSV; pokud to zvolená technologie snadno umožní, také XLSX.

## Bezpečnostní pravidla

- Neveřejná data nesmí být součástí veřejného repozitáře.
- Veřejná stránka nesmí zobrazovat odpovědi jednotlivých jednotek.
- Přístup za jednotku nesmí umožnit číst nebo měnit jinou jednotku.
- Administrátorská část musí být dostupná jen členům výboru.
- Dodavatel nemá mít přímý přístup do systému.
- Přístupové kódy nebo tokeny nesmí být ukládány do veřejného HTML v čitelné podobě.
- Databázová pravidla musí omezovat čtení a zápis podle role nebo přístupového režimu.
- Exporty s osobními údaji mají být určeny pouze pro výbor a pro nezbytný rozsah předání dodavateli.

## Zálohování a archivace

Minimální požadavky:

- možnost exportovat všechna data agendy do tabulkového formátu,
- archivovat finální souhrn použitý pro objednávku,
- archivovat podklad pro kontrolu plateb,
- po dokončení agendy rozhodnout o době uchování odpovědí a historie změn.

Přesná doba uchování dat zůstává právní a provozní otázkou. Technické řešení musí umožnit data exportovat a případně
později odstranit nebo anonymizovat podle rozhodnutí výboru.

## Nasazení

Pracovní model nasazení:

1. Veřejný web zůstane publikovaný přes GitHub Pages.
2. Aplikační část se připraví jako samostatná webová aplikace.
3. Datová část se připraví v Supabase.
4. Veřejný web bude na aplikační část pouze odkazovat.
5. Před spuštěním se ověří testovací jednotky, výpočet doplatku, změna odpovědi, exporty a administrátorský přístup.

## Body k doplnění před implementací

- konečné rozhodnutí, zda aplikační část poběží přes Vercel, Netlify nebo jiný hosting,
- konkrétní pravidlo tvorby variabilního symbolu,
- seznam jednotek a primárních kontaktů pro import,
- forma distribuce přístupových odkazů nebo kódů jednotkám,
- finální nastavení administrátorů,
- finální rozsah exportu pro dodavatele,
- pravidla uchování dat po dokončení agendy,
- ověření, zda free tarify zvolených služeb postačí očekávanému provozu.