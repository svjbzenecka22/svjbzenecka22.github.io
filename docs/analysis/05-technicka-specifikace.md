# Technická specifikace

## Stav dokumentu

Předimplementační technická specifikace k 2026-05-09. Dokument navazuje na funkční specifikaci MVP první agendy a
rozpracovává doporučený technický směr do detailu použitelného pro první build.

Nejde ještě o finální SQL migrace, kód aplikace ani produkční bezpečnostní audit. Dokument ale stanovuje cílovou
architekturu, obrazovky, datové entity, stavy, výpočty, exporty, bezpečnostní pravidla a checklist před implementací.

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
- aplikační část vznikne jako jednoduché monorepo s odděleným frontendem a backendem,
- frontend bude React + TypeScript + Vite,
- backend bude Node.js + TypeScript + Fastify s REST API,
- data budou uložena v PostgreSQL,
- databázovou vrstvu bude řídit Prisma ORM a Prisma migrations,
- lokální vývoj poběží přes Docker Compose,
- produkční směr je pozdější nasazení na levné VPS v EU za Nginx reverse proxy,
- administrátorský přístup výboru je oddělen od běžného přístupu za jednotku,
- exporty jsou dostupné výboru, nikoliv dodavateli přímo.

Tento směr lépe splňuje požadavky MVP než čistý Google Forms, zejména poslední platnou odpověď za jednotku, změny do
uzávěrky, administrátorský přehled, výpočet doplatků, exporty a budoucí rozšíření na další agendy.

První build má být co nejmenší použitelná aplikace pro jednu agendu, nikoliv obecný portálový framework. Technické
volby proto mají podporovat budoucí rozšíření, ale nemají do první verze přidávat funkce mimo aktuální sběr.

Managed služby typu Vercel, Supabase, Firebase, Railway, Render, Neon nebo PlanetScale nejsou pro MVP povinnou součástí
architektury a nemají být použity jako hlavní provozní předpoklad. Jejich pozdější využití lze znovu zvážit pouze jako
vědomé provozní rozhodnutí, nikoliv jako základ datového modelu nebo aplikační logiky.

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
- přehled a detail aktuální odpovědi za jednotku,
- možnost změny odpovědi do uzávěrky,
- administrátorský přehled pro výbor,
- export finálního souhrnu pro dodavatele,
- export nebo sestavu pro kontrolu plateb.

Pracovní obrazovky první verze:

- veřejná informační stránka nebo odkaz z veřejného webu,
- vstup do formuláře za jednotku přes jedinečný odkaz nebo kód,
- formulář odpovědi za jednotku,
- potvrzení odeslané odpovědi,
- zobrazení aktuální odpovědi za jednotku do uzávěrky,
- administrátorský přehled jednotek a odpovědí,
- administrátorský detail odpovědi,
- exportní obrazovka nebo exportní akce pro výbor.

### Datová část

Datová část má být mimo veřejný repozitář. Má ukládat jednotky, kontakty, varianty telefonů, odpovědi, stavy odpovědí,
variabilní symboly, výpočty doplatků a případně stav platby.

## Přístup a oprávnění

### Přístup za jednotku

První agenda nemá ověřovat osobní identitu každého vlastníka, spoluvlastníka nebo nájemníka. Pracovní model je přístup
za jednotku nebo domácnost.

Technicky to může znamenat například jedinečný přístupový odkaz nebo přístupový kód pro každou jednotku. Přístup musí
umožnit zobrazit a změnit pouze odpověď dané jednotky do uzávěrky. Nesmí umožnit procházet odpovědi jiných jednotek.

Pracovní doporučení pro první build:

- každá jednotka má náhodný neveřejný přístupový token,
- uživatel vstupuje do formuláře přes URL s tokenem nebo přes kód zadaný do formuláře,
- v databázi se neukládá token v čitelné podobě, ale pouze jeho hash,
- token slouží pouze pro danou agendu,
- ztracený nebo chybně rozeslaný token musí být možné zneplatnit a vytvořit nový,
- token nesmí být uložen ve veřejném HTML ani v repozitáři.

Validace tokenu má probíhat na serverové straně ve Fastify backendu. Klientská část nesmí obsahovat databázové
přihlašovací údaje a frontend nemá mít přímý přístup do PostgreSQL.

### Administrátorský přístup

Administrátorský přístup mají mít všichni tři členové výboru. Administrátor má vidět stav všech jednotek, filtrovat
neodpovězené jednotky, exportovat data a po uzávěrce řešit schválené výjimky.

Administrátorský přístup má být oddělen od přístupu za jednotku. Dodavatel administrátorský přístup nemá.

Pracovní doporučení pro první build:

- administrátoři jsou evidováni e-mailem,
- administrátorské přihlášení má být řešeno v backendu aplikace,
- hesla administrátorů mají být ukládána pouze jako bezpečný hash,
- administrátorská session má být vedena přes bezpečnou HTTP-only cookie nebo srovnatelný serverový mechanismus,
- administrátor nesmí používat jednotkový token jako náhradu za admin přístup,
- exporty s osobními údaji jsou dostupné pouze administrátorům.

## Návrh datového modelu

### Přehled entit

První build má pracovat s těmito entitami. Názvy jsou pracovní a mohou se při implementaci upravit podle zvoleného
frameworku nebo konvence databáze.

#### `units`

Evidence bytových jednotek.

| Pole | Význam | Poznámka |
| --- | --- | --- |
| `id` | interní identifikátor | primární klíč |
| `unit_number` | číslo bytu nebo jednotky | unikátní v rámci agendy |
| `floor` | podlaží | pro export dodavateli |
| `entrance` | vchod | volitelné, pokud bude potřeba |
| `ownership_type` | typ vlastnictví | například `physical_owner`, `sbd_mir` |
| `is_active` | aktivní jednotka | umožní skrýt chybný nebo historický záznam |
| `created_at` | čas založení | technický údaj |
| `updated_at` | čas poslední úpravy | technický údaj |

#### `unit_contacts`

Kontakty pro komunikaci výboru s jednotkou nebo domácností.

| Pole | Význam | Poznámka |
| --- | --- | --- |
| `id` | interní identifikátor | primární klíč |
| `unit_id` | vazba na jednotku | cizí klíč na `units` |
| `primary_email` | primární kontaktní e-mail | kontaktní údaj, ne stabilní identifikátor |
| `primary_phone` | hlavní kontaktní telefon | kontaktní údaj, ne stabilní identifikátor |
| `contact_name` | pracovní jméno kontaktu | volitelné podle dostupných podkladů |
| `note` | interní poznámka výboru | neveřejná |
| `updated_at` | čas poslední úpravy | technický údaj |

#### `unit_access_tokens`

Přístup za jednotku pro první agendu.

| Pole | Význam | Poznámka |
| --- | --- | --- |
| `id` | interní identifikátor | primární klíč |
| `unit_id` | vazba na jednotku | cizí klíč na `units` |
| `agenda_code` | kód agendy | například `access-2026` |
| `token_hash` | hash přístupového tokenu | token neukládat čitelně |
| `status` | stav tokenu | `active`, `revoked`, `expired` |
| `created_at` | čas vytvoření | technický údaj |
| `revoked_at` | čas zneplatnění | volitelné |

#### `phone_variants`

Varianty bytových telefonů.

| Pole | Význam | Poznámka |
| --- | --- | --- |
| `id` | interní identifikátor | primární klíč |
| `code` | kód varianty | například podle CSV podkladu |
| `name` | název varianty | zobrazovaný název |
| `price_czk` | doplatek varianty v Kč | základní varianta má `0` |
| `description` | stručný popis | volitelné |
| `image_path` | cesta k obrázku | pokud se bude v aplikaci zobrazovat |
| `is_active` | aktivní varianta | pouze aktivní varianty lze vybrat |

#### `chip_product`

Parametry čipu pro výpočet doplatku.

| Pole | Význam | Poznámka |
| --- | --- | --- |
| `id` | interní identifikátor | primární klíč |
| `code` | kód položky | například `rfid-klicenka-cerna` |
| `name` | název čipu | zobrazovaný název |
| `unit_price_czk` | cena jednoho čipu | pracovně `44` |
| `is_active` | aktivní položka | pro aktuální sběr |

#### `responses`

Odpovědi za jednotku. Pro jednoduchost může každá změna vytvořit nový záznam; finální odpověď se určí podle poslední
platné odpovědi před uzávěrkou.

| Pole | Význam | Poznámka |
| --- | --- | --- |
| `id` | interní identifikátor | primární klíč |
| `unit_id` | vazba na jednotku | cizí klíč na `units` |
| `submitted_by_name` | jméno odpovídající osoby | pokud není známo z profilu |
| `submitted_by_contact` | kontakt pro nejasnosti | e-mail nebo telefon |
| `relationship_to_unit` | vztah k jednotce | vlastník, spoluvlastník, nájemník, uživatel, pověřená osoba |
| `chip_count` | počet čipů | kladné celé číslo |
| `phone_variant_id` | zvolený telefon | cizí klíč na `phone_variants` |
| `total_amount_czk` | vypočtený doplatek | uložit hodnotu použitou při odeslání |
| `variable_symbol` | variabilní symbol | unikátní v rámci agendy |
| `payment_confirmed` | potvrzení doplatku a pokynů | musí být `true` pro finální odpověď |
| `note` | poznámka uživatele | volitelná, k agendě |
| `status` | stav odpovědi | viz stavy níže |
| `submitted_at` | čas odeslání | rozhoduje pro poslední odpověď |
| `source` | zdroj odpovědi | `unit_form`, `admin_edit` |
| `admin_note` | poznámka výboru | pro administrativní změny |

#### `payments`

Platební kontrola.

| Pole | Význam | Poznámka |
| --- | --- | --- |
| `id` | interní identifikátor | primární klíč |
| `unit_id` | vazba na jednotku | cizí klíč na `units` |
| `response_id` | vazba na finální odpověď | cizí klíč na `responses` |
| `variable_symbol` | variabilní symbol | stejný jako u odpovědi |
| `expected_amount_czk` | očekávaná částka | podle finální odpovědi |
| `paid_amount_czk` | zaplacená částka | ručně doplněná podle výpisu |
| `status` | stav platby | viz stavy níže |
| `paid_at` | datum platby | volitelné |
| `payment_note` | poznámka výboru | volitelné |

#### `admin_users`

Administrátoři z výboru.

| Pole | Význam | Poznámka |
| --- | --- | --- |
| `id` | interní identifikátor | primární klíč |
| `email` | e-mail administrátora | unikátní |
| `name` | jméno administrátora | volitelné |
| `password_hash` | hash hesla | pokud bude použito heslové přihlášení |
| `role` | role | pro MVP stačí `committee_admin` |
| `is_active` | aktivní oprávnění | umožní odebrat přístup |

#### `export_runs`

Evidence vytvořených exportů.

| Pole | Význam | Poznámka |
| --- | --- | --- |
| `id` | interní identifikátor | primární klíč |
| `export_type` | typ exportu | dodavatel, výbor, platby, neodpovězené jednotky |
| `created_by` | administrátor | vazba na admin uživatele |
| `created_at` | čas vytvoření | technický údaj |
| `row_count` | počet řádků | kontrolní údaj |
| `file_name` | název souboru | pokud se ukládá |

### Stavy odpovědí

Pracovní hodnoty `responses.status`:

- `draft`: rozepsaná nebo technicky nekompletní odpověď, pokud bude takový stav implementován,
- `submitted`: odeslaná odpověď,
- `superseded`: nahrazená novější odpovědí stejné jednotky,
- `final`: odpověď použitá pro objednávku,
- `invalid`: neplatná nebo vyřazená odpověď,
- `admin_adjusted`: administrativně upravená odpověď po zásahu výboru.

Minimální implementace může pracovat pouze se stavy `submitted`, `superseded`, `final`, `invalid` a `admin_adjusted`.

### Stavy plateb

Pracovní hodnoty `payments.status`:

- `not_due`: platba zatím není očekávána nebo se teprve připravuje,
- `expected`: platba je očekávána,
- `paid`: platba odpovídá variabilnímu symbolu a částce,
- `partial`: zaplacená částka neodpovídá očekávané částce,
- `unmatched`: platbu se nepodařilo jednoznačně přiřadit,
- `overdue`: platba není uhrazena po termínu.

Pro první verzi může být stav platby veden ručně výborem.

## Pravidla odpovědí

- Každá odpověď musí být přiřazena ke konkrétní jednotce.
- Do uzávěrky může být odpověď jednotky změněna samoobslužně.
- Pro objednávku se použije poslední platná odpověď za jednotku před uzávěrkou.
- Starší odpovědi nesmí vstupovat do finální objednávky.
- Po uzávěrce může změnu provést jen výbor administrativně a pouze jako výjimku.
- Odpověď bez potvrzení doplatku a platebních pokynů není finální.
- Při nové odpovědi stejné jednotky před uzávěrkou se předchozí platná odpověď označí jako nahrazená.
- Finální export pro dodavatele pracuje jen se stavem `final` nebo s poslední platnou odpovědí, kterou výbor při uzavření označí jako finální.
- Administrativní úprava po uzávěrce musí mít interní poznámku výboru.

## Výpočet doplatku a variabilní symbol

Doplatek se počítá podle vzorce:

```text
doplatek = počet čipů * cena jednoho čipu + doplatek zvolené varianty telefonu
```

Cena jednoho čipu je v pracovních podkladech 44 Kč. Varianty telefonů a jejich ceny se mají načítat z datového podkladu
nebo databázové tabulky odpovídající dokumentu `12-telefonni-varianty.md`.

Variabilní symbol musí být v rámci agendy unikátní. Pracovní pravidlo pro první build:

```text
VS = 2605 + číslo jednotky doplněné zleva nulami na 3 číslice
```

Příklad: jednotka `7` má pracovní variabilní symbol `2605007`, jednotka `42` má `2605042`. Prefix `2605` označuje
agendu přístupového systému v květnu 2026. Pokud výbor používá jinou účetní konvenci, má být toto pravidlo před
implementací upraveno.

## Exporty

Systém má umožnit alespoň tyto exporty:

- finální souhrn pro dodavatele s poslední platnou odpovědí za jednotku,
- přehled pro výbor se stavem odpovědí všech jednotek,
- seznam jednotek bez odpovědi pro urgenci,
- podklad pro kontrolu plateb podle variabilního symbolu a částky,
- seznam jednotek bez zaplaceného doplatku po termínu platby.

Exportní formát má být tabulkový, minimálně CSV; pokud to zvolená technologie snadno umožní, také XLSX.

### Sloupce exportu pro dodavatele

Pracovní sloupce:

- `unit_number`,
- `floor`,
- `contact_name`,
- `contact_email`,
- `contact_phone`,
- `chip_count`,
- `phone_variant_name`,
- `phone_variant_code`,
- `note_for_committee`, pokud ji výbor po kontrole uzná za relevantní pro dodavatele.

Export pro dodavatele nemá automaticky obsahovat interní poznámky výboru, historii změn, platební stav ani údaje,
které dodavatel nepotřebuje pro objednávku nebo montáž.

### Sloupce exportu pro kontrolu plateb

Pracovní sloupce:

- `unit_number`,
- `contact_name`,
- `contact_email`,
- `contact_phone`,
- `variable_symbol`,
- `expected_amount_czk`,
- `paid_amount_czk`,
- `payment_status`,
- `payment_note`.

### Sloupce exportu neodpovězených jednotek

Pracovní sloupce:

- `unit_number`,
- `floor`,
- `contact_name`,
- `primary_email`,
- `primary_phone`,
- `last_response_at`, pokud existuje neúplná nebo neplatná odpověď,
- `status`.

## Bezpečnostní pravidla

- Neveřejná data nesmí být součástí veřejného repozitáře.
- Veřejná stránka nesmí zobrazovat odpovědi jednotlivých jednotek.
- Přístup za jednotku nesmí umožnit číst nebo měnit jinou jednotku.
- Administrátorská část musí být dostupná jen členům výboru.
- Dodavatel nemá mít přímý přístup do systému.
- Přístupové kódy nebo tokeny nesmí být ukládány do veřejného HTML v čitelné podobě.
- Databázová pravidla musí omezovat čtení a zápis podle role nebo přístupového režimu.
- Exporty s osobními údaji mají být určeny pouze pro výbor a pro nezbytný rozsah předání dodavateli.

### Doporučené bezpečnostní rozdělení

- Běžný uživatel jednotky komunikuje s aplikací přes jednotkový token.
- Serverová část ověří token proti hashi v databázi.
- Serverová část zapisuje odpověď do databáze.
- Administrátor se přihlašuje samostatně a má roli výboru.
- Připojovací údaje k PostgreSQL smí být pouze v backendovém prostředí, nikdy ve frontendovém kódu.
- Frontend komunikuje s daty pouze přes REST API backendu.

### Minimální bezpečnostní testy před spuštěním

- jednotkový token A nesmí zobrazit ani změnit jednotku B,
- neplatný nebo zneplatněný token nesmí zobrazit formulář,
- nepřihlášený uživatel nesmí otevřít administraci,
- běžný jednotkový přístup nesmí stáhnout export,
- exporty nesmí být dostupné přes veřejný URL bez ověření,
- žádný servisní klíč nesmí být zapsán v repozitáři.

## Importní podklady

Před implementací nebo nejpozději před ostrým spuštěním je potřeba připravit importní tabulky.

### Jednotky

Minimální sloupce:

- `unit_number`,
- `floor`,
- `ownership_type`,
- `primary_email`,
- `primary_phone`,
- `contact_name`.

### Varianty telefonů

Zdroj: `docs/analysis/data/telefonni-varianty.csv`.

Minimální sloupce pro aplikaci:

- `code`,
- `name`,
- `price_czk`,
- `description`,
- `image_path`.

### Čip

Zdroj: `docs/analysis/data/cipy.csv`.

Minimální sloupce pro aplikaci:

- `code`,
- `name`,
- `unit_price_czk`.

## Návrh aplikačních cest

Konkrétní URL se může změnit podle zvoleného frameworku. Pracovní návrh:

- `/` nebo `/pristupovy-system` - vstupní informace k agendě,
- `/pristupovy-system/odpoved?t=...` - formulář jednotky přes token,
- `/pristupovy-system/potvrzeni` - potvrzení odeslání,
- `/admin` - vstup do administrace,
- `/admin/odpovedi` - přehled odpovědí,
- `/admin/jednotky-bez-odpovedi` - seznam pro urgenci,
- `/admin/exporty` - exporty pro dodavatele, výbor a platby.

## Návrh API nebo serverových akcí

Pokud bude použita serverová část, minimální operace jsou:

- ověřit jednotkový token,
- načíst data jednotky pro formulář,
- načíst aktivní varianty telefonů a cenu čipu,
- spočítat doplatek,
- uložit novou odpověď,
- označit předchozí odpověď jednotky jako nahrazenou,
- načíst administrátorský přehled,
- uzavřít sběr a označit finální odpovědi,
- vytvořit export pro dodavatele,
- vytvořit export pro platby,
- zneplatnit nebo obnovit jednotkový token.

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
2. Aplikační část se připraví jako samostatný portál s frontendem a backendem.
3. Datová část se připraví jako PostgreSQL databáze spravovaná přes Prisma migrations.
4. Veřejný web bude na aplikační část pouze odkazovat.
5. Lokální vývoj poběží přes Docker Compose.
6. Produkční nasazení se připraví pro VPS v EU s Nginx reverse proxy a HTTPS přes Let's Encrypt.
7. Před spuštěním se ověří testovací jednotky, výpočet doplatku, změna odpovědi, exporty a administrátorský přístup.

### Prostředí

Pracovní rozdělení prostředí:

- lokální vývojové prostředí,
- testovací nebo preview nasazení,
- produkční nasazení pro ostrý sběr.

Produkční databáze nemá být plněna testovacími osobními údaji, pokud to není nezbytné. Testovací data mají být jasně
označena nebo oddělena.

### Konfigurační údaje

Konfigurační údaje a tajné klíče mají být vedeny v prostředí hostingu, ne v repozitáři. Minimálně půjde o:

- `DATABASE_URL` pro PostgreSQL,
- tajemství pro aplikační session nebo podpis cookie,
- salt nebo tajemství pro hashování jednotkových tokenů, pokud bude potřeba,
- administrátorské účty nebo seed pro jejich založení,
- produkční doménu, CORS a další provozní nastavení backendu.

Součástí repozitáře má být `.env.example` bez citlivých hodnot. Skutečný `.env` nesmí být commitnutý do Gitu.

## Body k doplnění před implementací

- založení samostatného repozitáře `svj-portal`, doporučeně jako private repozitář pod `svjbzenecka22`,
- potvrzení nebo úprava pracovního pravidla tvorby variabilního symbolu,
- seznam jednotek a primárních kontaktů pro import,
- forma distribuce přístupových odkazů nebo kódů jednotkám,
- finální nastavení administrátorů,
- finální rozsah exportu pro dodavatele,
- pravidla uchování dat po dokončení agendy,
- základní provozní postup zálohování databáze a souborového úložiště.

## Implementační checklist první verze

1. Založit aplikační část oddělenou od veřejného statického webu.
2. Připravit monorepo strukturu `frontend/`, `backend/`, `docker-compose.yml` a `.env.example`.
3. Připravit PostgreSQL v Docker Compose.
4. Připravit Prisma schema a první migrace databáze.
5. Připravit import jednotek a kontaktů.
6. Naimportovat varianty telefonů a čipu z připravených CSV podkladů.
7. Vygenerovat jednotkové tokeny a uložit pouze jejich hashe.
8. Připravit REST API pro jednotkový přístup, odpovědi, administraci a exporty.
9. Připravit formulář odpovědi za jednotku.
10. Implementovat výpočet doplatku a variabilního symbolu.
11. Implementovat uložení odpovědi a nahrazení starší odpovědi.
12. Připravit administrátorské přihlášení a role výboru.
13. Připravit administrátorský přehled odpovědí a jednotek bez odpovědi.
14. Připravit export pro dodavatele.
15. Připravit export pro kontrolu plateb.
16. Připravit základní zálohovací a obnovovací postup.
17. Ověřit bezpečnostní pravidla přístupu.
18. Ověřit testovací scénáře podle testovací strategie.
19. Doplnit odkaz z veřejného webu na aplikační část.
20. Připravit instrukce pro vlastníky, nájemníky a uživatele bytů.