# Technologické zadání MVP portálu

## Stav dokumentu

Pracovní technologické zadání k 2026-05-09. Dokument zachycuje nově dohodnutý směr pro MVP portálu SVJ po revizi
managed variant Vercel/Supabase.

## Cíl

Rychle vytvořit MVP portálu pro první agendu přístupového systému tak, aby:

- běželo lokálně zdarma přes Docker Compose,
- šlo později nasadit na levné VPS v EU,
- nebylo povinně závislé na Vercelu, Supabase, Firebase ani jiné managed/serverless platformě,
- mělo oddělený frontend a backend,
- bylo responzivní a dobře použitelné na mobilu,
- umožnilo pozdější rozšíření na PWA nebo mobilní aplikaci,
- bylo dlouhodobě udržitelné,
- mělo nízký vendor-lock.

## Pracovní stack

### Frontend

- React,
- TypeScript,
- Vite,
- responzivní mobile-first UI,
- jednoduchý čistý design,
- bez složitého UI frameworku, pokud nebude prakticky potřeba,
- CSS nebo Tailwind podle jednoduchosti první implementace.

### Backend

- Node.js,
- TypeScript,
- Fastify,
- REST API,
- modulární struktura,
- jednoduchá service/repository architektura.

NestJS se pro MVP nepoužije, pokud nevznikne výslovný důvod. Cílem je rychlá a čitelná aplikace, ne enterprise
framework.

### Databáze a datová vrstva

- PostgreSQL,
- lokálně v Docker Compose,
- později stejný princip na VPS,
- Prisma ORM,
- Prisma schema jako hlavní aplikační datový model,
- Prisma migrations pro změny schématu,
- Prisma Client pro typově bezpečný přístup k databázi,
- raw SQL pouze tam, kde bude účelné.

### Provoz a konfigurace

- Docker Compose pro lokální vývoj,
- `.env.example` v repozitáři,
- skutečný `.env` mimo Git,
- citlivé údaje se nesmí commitovat,
- produkčně Nginx jako reverse proxy,
- HTTPS přes Let's Encrypt až v produkční fázi,
- lokální vývoj bez externích služeb.

### Storage

- soubory ukládat na lokální disk nebo Docker volume,
- dokumenty ani přílohy neukládat přímo do databáze,
- v databázi držet pouze metadata souborů,
- strukturu připravit tak, aby šla zálohovat a migrovat.

## Technologie mimo hlavní směr MVP

Pro první MVP nepoužívat jako povinnou součást architektury:

- Vercel,
- Supabase,
- Firebase,
- Railway,
- Render,
- Neon,
- PlanetScale,
- serverless-first architekturu,
- externí cloud storage,
- externí auth provider,
- Kubernetes,
- mikroservisy,
- složitý event-driven návrh,
- GraphQL bez jasného důvodu.

## Doporučená struktura

Pracovní monorepo struktura aplikační části:

```text
svj-portal/
├── backend/
├── frontend/
├── docker-compose.yml
├── .env.example
├── README.md
└── docs/
```

Veřejný statický web může dál zůstat v repozitáři `svjbzenecka22.github.io` a na portál pouze odkazovat. Před založením
aplikace je potřeba rozhodnout, zda `svj-portal` vznikne jako samostatný repozitář, nebo jako jasně oddělená složka.

## Praktická zásada pro první build

Self-hosted směr nesmí rozšířit první MVP mimo skutečně nutný rozsah. První build má pokrýt jen:

- přístup za jednotku přes token nebo kód,
- formulář odpovědi,
- výpočet doplatku a variabilního symbolu,
- administrátorský přehled výboru,
- exporty,
- základní bezpečnost,
- základní zálohovatelnost.