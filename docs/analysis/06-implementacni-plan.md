# Implementační plán

## Fáze 0: aktuální hotový základ

- Sjednocený veřejný web je založen.
- Existující sekce shromáždění a balkóny jsou převzaty do hlavního repozitáře.
- Web je publikován přes GitHub Pages.

## Fáze 1: analýza

- Doplnit byznys zadání.
- Vyjasnit veřejné a neveřejné části.
- Popsat první agendu přístupového systému.
- Rozhodnout minimální potřebnou úroveň přístupu a ochrany dat.
- Připravit srovnání nákladů a funkcionality vlastního řešení a hotových portálů pro SVJ nebo bytové domy.
- Vyřešit hlavní architektonické body tak, aby první agenda nebyla slepou uličkou.
- Vybrat technologickou variantu pro MVP.

Pracovní stav k 2026-05-09: po revizi technologického směru se pro MVP doporučuje self-hosted jednoduchý portál bez
povinné závislosti na Vercelu, Supabase, Firebase nebo podobných managed/serverless platformách. Aplikační část má být
oddělená od veřejného GitHub Pages webu a má vzniknout jako monorepo s frontendem React + TypeScript + Vite, backendem
Node.js + TypeScript + Fastify, REST API, PostgreSQL databází a Prisma ORM. Lokální vývoj má běžet přes Docker Compose,
produkční směr je pozdější levné VPS v EU. Google Sheets + Apps Script zůstává nouzová záložní varianta, pokud by
self-hosted MVP nebylo možné včas bezpečně dokončit.

## Fáze 2: MVP pro přístupový systém

- Připravit informační sekci.
- Rozhodnout, zda portál vznikne jako samostatný repozitář, nebo jako jasně oddělená složka mimo veřejné HTML.
- Připravit monorepo strukturu `frontend/`, `backend/`, `docker-compose.yml`, `.env.example` a `docs/`.
- Připravit frontend React + TypeScript + Vite s mobile-first formulářem.
- Připravit backend Node.js + TypeScript + Fastify s REST API.
- Připravit PostgreSQL v Docker Compose.
- Připravit Prisma schema a migrace pro jednotky, kontakty, tokeny, varianty telefonů, čipy, odpovědi, platby, administrátory a exporty.
- Připravit přístup za jednotku nebo domácnost.
- Připravit administrátorský přístup pro všechny tři členy výboru.
- Připravit export pro výbor a dodavatele.
- Připravit seznam jednotek bez odpovědi pro urgenci.
- Připravit základní zálohovací postup pro PostgreSQL a případné souborové úložiště.
- Ověřit proces s několika testovacími jednotkami.
- Zveřejnit instrukce pro vlastníky a nájemníky.

## Fáze 3: vyhodnocení

- Vyhodnotit použitelnost řešení.
- Vyhodnotit administrativní zátěž výboru.
- Rozhodnout, zda pokračovat stejnou technologií, postavit robustnější vlastní portál, nebo zvolit hotové portálové řešení.

## Fáze 4: rozšíření webu

- Doplnit dlouhodobé sekce webu.
- Připravit pravidla publikace dokumentů.
- Připravit případné soukromé části.
- Teprve poté řešit hlasování a pokročilejší agendy.