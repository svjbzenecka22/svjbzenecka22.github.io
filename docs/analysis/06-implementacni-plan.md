# Implementační plán

## Stav dokumentu

Realizační implementační plán k 2026-05-09. Dokument navazuje na funkční specifikaci, technickou specifikaci a revizi
technologického směru na self-hosted MVP bez zásadního vendor-locku.

Cílem není založit obecný portálový framework, ale dodat první použitelnou agendu: sběr počtu čipů a volby bytového
telefonu za jednotky, administraci výboru, výpočet doplatku a exporty.

## Schválené pracovní defaulty

Pro další implementaci platí tyto pracovní předpoklady:

- aplikační část vznikne v samostatném repozitáři `svj-portal`, ideálně pod GitHub organizací `svjbzenecka22`,
- repozitář má být zpočátku neveřejný, aby se snížilo riziko náhodného zveřejnění pracovních provozních podkladů,
- veřejný web `svjbzenecka22.github.io` zůstane samostatný a na portál bude pouze odkazovat,
- pracovní monorepo struktura bude `backend/`, `frontend/`, `docker-compose.yml`, `.env.example`, `README.md`, `docs/`,
- první build začne s testovacími jednotkami a testovacími kontakty,
- ostrý import jednotek a kontaktů se připraví až po ověření toku na testovacích datech,
- neveřejný seznam jednotek a kontaktů nesmí být uložen do veřejného repozitáře ani commitnut do Gitu,
- pracovní pravidlo variabilního symbolu je `2605 + číslo jednotky doplněné zleva nulami na 3 číslice`,
- termín avíza neodpovězeným jednotkám zůstává pracovně 2026-05-19,
- uzávěrka a předání souhrnu dodavateli zůstává pracovně 2026-05-24,
- první export pro dodavatele bude CSV,
- XLSX export je volitelný až po funkčním CSV exportu,
- administrátorské účty budou pro MVP založené ručně nebo seedem,
- přístup jednotky bude řešen náhodným tokenem nebo kódem, v databázi pouze jako hash,
- produkční VPS, doména a Nginx se připraví až po lokálně funkčním MVP.

## Fáze 0: aktuální hotový základ

Hotovo:

- sjednocený veřejný web je založen,
- existující sekce shromáždění a balkóny jsou převzaty do hlavního repozitáře,
- web je publikován přes GitHub Pages,
- první agenda přístupového systému je popsána ve funkční specifikaci,
- technologický směr je revidován na self-hosted MVP,
- testovací strategie je připravena.

Výstup fáze: veřejný web a dokumentační základ jsou připraveny pro založení samostatné aplikační části.

## Fáze 1: založení aplikačního repozitáře

Cíl: připravit čisté místo pro vývoj portálu oddělené od veřejného statického webu.

Kroky:

1. Založit nový repozitář `svj-portal`, doporučeně jako private repozitář pod `svjbzenecka22`.
2. Nepřidávat do repozitáře žádná reálná data jednotek, kontakty, tokeny ani produkční `.env`.
3. Připravit základní `README.md` s účelem projektu a lokálním spuštěním.
4. Připravit `.gitignore` pro Node.js, build výstupy, `.env`, databázové dumpy a lokální uploady.
5. Připravit `.env.example` s prázdnými nebo ukázkovými hodnotami bez tajných údajů.
6. V dokumentaci veřejného webu ponechat jen odkaz nebo poznámku na samostatný portál, nikoliv interní data portálu.

Kritéria dokončení:

- repozitář existuje,
- neobsahuje tajné údaje ani ostrá osobní data,
- je jasné, jaký je vztah mezi veřejným webem a portálem,
- lokální struktura je připravena pro scaffold aplikace.

## Fáze 2: technický skelet MVP

Cíl: vytvořit minimální běžící aplikaci s odděleným frontendem, backendem a databází.

Kroky:

1. Vytvořit monorepo strukturu:
   - `frontend/`,
   - `backend/`,
   - `docs/`,
   - `docker-compose.yml`,
   - `.env.example`.
2. Založit frontend přes Vite s Reactem a TypeScriptem.
3. Založit backend přes Node.js, TypeScript a Fastify.
4. Přidat PostgreSQL službu do Docker Compose.
5. Přidat backend službu do Docker Compose.
6. Připravit lokální proměnné prostředí:
   - `DATABASE_URL`,
   - `SESSION_SECRET`,
   - `TOKEN_SECRET` nebo ekvivalent pro hashování tokenů,
   - `APP_BASE_URL`,
   - `CORS_ORIGIN`.
7. Ověřit, že frontend, backend a databáze běží lokálně bez externích služeb.
8. Připravit základní health check endpoint backendu, například `GET /api/health`.

Kritéria dokončení:

- `docker compose up` spustí databázi a backend,
- frontend jde spustit lokálně,
- backend se připojí k PostgreSQL,
- žádná citlivá konfigurace není v Gitu.

## Fáze 3: databázový model a seed dat

Cíl: připravit Prisma datový model pro první agendu a testovací data pro vývoj.

Kroky:

1. Přidat Prisma do backendu.
2. Vytvořit první `schema.prisma` s entitami:
   - `Unit`,
   - `UnitContact`,
   - `UnitAccessToken`,
   - `PhoneVariant`,
   - `ChipProduct`,
   - `Response`,
   - `Payment`,
   - `AdminUser`,
   - `ExportRun`.
3. Připravit Prisma migration pro počáteční schéma.
4. Připravit seed testovacích jednotek bez reálných osobních údajů.
5. Načíst pracovní varianty telefonů a čipu z připravených CSV podkladů nebo je pro MVP převést do seed dat.
6. Připravit generování jednotkových tokenů a ukládání pouze jejich hashů.
7. Připravit seed administrátorského účtu pro lokální vývoj.

Kritéria dokončení:

- databáze jde založit přes Prisma migration,
- testovací data lze znovu vytvořit seedem,
- tokeny nejsou uložené čitelně,
- datový model odpovídá technické specifikaci.

## Fáze 4: backend REST API

Cíl: připravit serverovou logiku pro jednotkový formulář, administraci a exporty.

Minimální API oblasti:

- health check,
- ověření jednotkového tokenu,
- načtení dat jednotky pro formulář,
- načtení aktivních telefonních variant a ceny čipu,
- výpočet doplatku,
- odeslání odpovědi za jednotku,
- nahrazení starší odpovědi novější odpovědí do uzávěrky,
- admin login a logout,
- načtení administrátorského přehledu,
- seznam jednotek bez odpovědi,
- uzavření sběru a označení finálních odpovědí,
- CSV export pro dodavatele,
- CSV export pro kontrolu plateb.

Bezpečnostní pravidla:

- frontend nikdy nepřistupuje přímo do databáze,
- jednotkový token smí načíst a měnit jen data své jednotky,
- administrátorská API vyžadují admin session,
- hesla administrátorů jsou uložená pouze jako hash,
- exporty nejsou dostupné přes veřejný URL bez ověření.

Kritéria dokončení:

- všechny kritické operace běží přes backend,
- běžný token neotevře cizí jednotku,
- nepřihlášený uživatel neotevře admin API,
- exporty lze vytvořit jen přes administrátorský přístup.

## Fáze 5: frontend MVP

Cíl: vytvořit jednoduché, mobilně použitelné rozhraní pro jednotky a výbor.

Obrazovky pro jednotku:

1. vstup přes token nebo kód,
2. formulář odpovědi,
3. zobrazení vypočteného doplatku a variabilního symbolu,
4. potvrzení platebních pokynů,
5. potvrzení odeslání,
6. možnost zobrazit aktuální odpověď a do uzávěrky ji změnit.

Obrazovky pro výbor:

1. admin login,
2. přehled všech jednotek,
3. filtr jednotek bez odpovědi,
4. detail odpovědi jednotky,
5. exporty,
6. podklad pro kontrolu plateb.

UI pravidla:

- mobile-first,
- jednoduchý čistý design,
- bez zbytečného UI frameworku, pokud nebude prakticky potřeba,
- formulář musí být čitelný a použitelný na telefonu,
- administrace může být primárně optimalizovaná pro notebook, ale nesmí být nepoužitelná na běžném mobilu.

Kritéria dokončení:

- testovací jednotka zvládne vyplnit odpověď na mobilu,
- uživatel vidí výslednou částku před odesláním,
- uživatel vidí variabilní symbol,
- výbor vidí stav odpovědí,
- CSV export lze stáhnout z administrace.

## Fáze 6: import neveřejných dat a příprava ostrého běhu

Cíl: bezpečně připravit reálná data bez jejich commitování do repozitáře.

Kroky:

1. Připravit neveřejný zdroj jednotek a kontaktů mimo veřejný repozitář.
2. Připravit importní skript nebo administrátorský import pro jednotky a kontakty.
3. Import spustit nejdříve v lokálním nebo testovacím prostředí.
4. Zkontrolovat počty jednotek, kontakty a typ vlastnictví.
5. Vygenerovat ostré jednotkové tokeny.
6. Připravit komunikační podklad pro rozeslání odkazů nebo kódů jednotkám.
7. Připravit seznam administrátorských účtů pro všechny tři členy výboru.

Kritéria dokončení:

- ostrá data nejsou v Gitu,
- počet jednotek sedí na očekávaný stav domu,
- tokeny jsou vygenerované a uložené jen jako hash,
- výbor má připravený bezpečný způsob distribuce odkazů nebo kódů.

## Fáze 7: testování a akceptace

Cíl: ověřit MVP podle testovací strategie před ostrým spuštěním.

Testovací okruhy:

- platná odpověď za jednotku,
- povinná pole,
- validace počtu čipů,
- výběr telefonu,
- výpočet doplatku,
- variabilní symbol,
- opakovaná odpověď před uzávěrkou,
- změna po uzávěrce pouze přes výbor,
- jednotkový token A nevidí jednotku B,
- neplatný nebo zneplatněný token je odmítnut,
- nepřihlášený uživatel neotevře administraci,
- exporty nejsou veřejné,
- CSV export obsahuje správné sloupce,
- administrace ukazuje jednotky bez odpovědi,
- aplikace je použitelná na mobilu.

Kritéria dokončení:

- všechny kritické scénáře z testovací strategie jsou ověřené,
- výbor otestoval alespoň několik testovacích jednotek,
- před spuštěním neexistuje známá chyba, která by umožnila číst nebo měnit cizí data,
- finální texty formuláře jsou srozumitelné.

## Fáze 8: lokální zálohování a produkční příprava

Cíl: nepustit ostrý sběr bez minimálního provozního základu.

Kroky:

1. Připravit postup zálohy PostgreSQL přes `pg_dump`.
2. Připravit postup obnovy databáze ze zálohy.
3. Připravit pravidlo, kde budou uložené zálohy mimo běžný pracovní adresář.
4. Připravit oddělení testovacích a ostrých `.env` souborů.
5. Připravit produkční Docker Compose nebo produkční poznámky pro VPS.
6. Připravit návrh Nginx reverse proxy.
7. Připravit poznámku k HTTPS přes Let's Encrypt.

Kritéria dokončení:

- existuje vyzkoušený postup zálohy,
- existuje vyzkoušený postup obnovy alespoň na testovací databázi,
- produkční konfigurace není commitnutá,
- je jasné, co je nutné udělat při nasazení na VPS.

## Fáze 9: spuštění sběru

Cíl: zpřístupnit první agendu vlastníkům a uživatelům jednotek.

Kroky:

1. Nasadit aplikaci do zvoleného prostředí.
2. Ověřit produkční health check.
3. Ověřit přístup vybrané testovací jednotky v produkčním prostředí.
4. Ověřit administrátorský přístup výboru.
5. Ověřit export v produkčním prostředí.
6. Doplnit odkaz z veřejného webu nebo připravit rozesílku s odkazy/kódy.
7. Spustit sběr.
8. 2026-05-19 zkontrolovat jednotky bez odpovědi a poslat avízo.
9. 2026-05-24 uzavřít sběr, zkontrolovat data a připravit finální export pro dodavatele.

Kritéria dokončení:

- partaje mohou odpovědět online,
- výbor průběžně vidí stav odpovědí,
- finální export lze předat dodavateli,
- podklad pro kontrolu plateb je dostupný výboru.

## Fáze 10: vyhodnocení po první agendě

Cíl: rozhodnout, zda zvolený směr potvrdit pro další agendy.

Kroky:

1. Vyhodnotit použitelnost pro vlastníky, nájemníky a výbor.
2. Vyhodnotit administrativní zátěž výboru.
3. Vyhodnotit technickou náročnost provozu.
4. Zkontrolovat kvalitu exportů a platebních podkladů.
5. Rozhodnout, zda pokračovat stejnou technologií.
6. Rozhodnout, které části zobecnit pro další agendy.
7. Rozhodnout pravidla uchování nebo anonymizace dat po dokončení agendy.

Kritéria dokončení:

- výbor má zpětnou vazbu k prvnímu provozu,
- je jasné, zda self-hosted portál zůstává dlouhodobý směr,
- jsou zapsaná poučení pro další agendy.

## Co zatím neimplementovat

Do první verze nepatří:

- obecný dokumentový portál,
- právně závazné elektronické hlasování,
- bankovní integrace,
- automatické párování plateb,
- složitý systém rolí mimo administrátory výboru,
- osobní účty pro každého vlastníka nebo nájemníka,
- PWA režim,
- mobilní aplikace,
- GraphQL,
- Kubernetes,
- mikroservisy,
- externí auth provider jako povinná součást MVP.
