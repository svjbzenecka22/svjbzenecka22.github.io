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

Pracovní stav k 2026-05-09: pro MVP se jako doporučený směr jeví jednoduchá webová aplikace s oddělenou datovou
vrstvou Supabase a samostatným hostingem aplikační části. Google Sheets + Apps Script zůstává záložní varianta, pokud
by doporučený směr nebylo možné včas bezpečně dokončit.

## Fáze 2: MVP pro přístupový systém

- Připravit informační sekci.
- Připravit aplikační část pro sběr odpovědí za jednotky.
- Připravit datovou vrstvu pro jednotky, odpovědi, varianty telefonů, čipy, variabilní symboly a stavy plateb.
- Připravit přístup za jednotku nebo domácnost.
- Připravit administrátorský přístup pro všechny tři členy výboru.
- Připravit export pro výbor a dodavatele.
- Připravit seznam jednotek bez odpovědi pro urgenci.
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