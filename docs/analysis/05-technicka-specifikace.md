# Technická specifikace

## Stav dokumentu

Pracovní kostra. Konkrétní architektura bude doplněna po výběru technologie.

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

## Budoucí technické varianty

### Statický web plus externí formulář

Vhodné pro rychlé MVP a minimální náklady.

### Statický web plus serverless aplikace

Vhodné pro formuláře, databázi a lepší kontrolu přístupu.

### Plnohodnotná aplikace

Vhodné až ve chvíli, kdy bude jasné, že SVJ potřebuje dlouhodobý portál.

## Oblasti k doplnění

- datový model,
- autentizace nebo přístupové kódy,
- role a oprávnění,
- hosting,
- zálohování,
- monitoring,
- nasazování,
- bezpečnostní pravidla.