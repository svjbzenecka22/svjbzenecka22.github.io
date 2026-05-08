# Analýza webu SVJ Bzenecká 22

Tato složka obsahuje pracovní dokumenty pro postupný návrh a vývoj webu SVJ Bzenecká 22.

Cílem je držet se standardního vývojového cyklu software, ale v přiměřené podobě pro malé SVJ o 60 bytech.
Dokumenty mají být praktické, stručné a použitelné pro výbor i pro případné budoucí technické pokračování.

## Doporučený postup

1. Ujasnit byznys zadání a cíle.
2. Popsat uživatele, procesy, pravidla a omezení.
3. Oddělit veřejnou část webu od soukromé části a datových agend.
4. Popsat MVP pro první konkrétní agendu: výběr počtu čipů a typu bytového telefonu.
5. Teprve poté vybrat technologii.
6. Zapsat funkční specifikaci, technickou specifikaci, plán implementace a testy.

## Dokumenty

- `01-byznys-zadani.md` - výchozí zadání, cíle a hranice projektu
- `02-byznys-analyza.md` - uživatelé, procesy, potřeby a pravidla
- `03-it-analyza.md` - technologické možnosti, omezení, bezpečnost a provoz
- `04-funkcni-specifikace.md` - co má systém umět z pohledu uživatele
- `05-technicka-specifikace.md` - jak bude řešení technicky postavené
- `06-implementacni-plan.md` - kroky realizace a pořadí prací
- `07-testovaci-strategie.md` - ověření funkčnosti, bezpečnosti a použitelnosti
- `08-rozhodovaci-denik.md` - přijatá rozhodnutí a jejich důvody
- `09-rizika.md` - rizika, otevřené otázky a mitigace
- `10-otevrene-otazky.md` - otázky pro výbor a vlastníky před návrhem řešení
- `11-pracovni-prompt.md` - opakovaně použitelný prompt pro další analytické kroky

## Pracovní pravidla

- Každé podstatné rozhodnutí zapsat do rozhodovacího deníku.
- Nevybírat technologii dříve, než budou jasné procesy a citlivost dat.
- Soukromé a veřejné části posuzovat odděleně.
- U každé funkce rozlišit, zda jde o nutnost, vhodné zlepšení nebo budoucí možnost.
- U osobních údajů a hlasování postupovat opatrně a ověřovat právní i organizační souvislosti.