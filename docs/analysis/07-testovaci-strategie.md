# Testovací strategie

## Cíl

Ověřit, že MVP první agendy přístupového systému funguje pro vlastníky, nájemníky, uživatele bytů i výbor SVJ,
neukládá neveřejná data do veřejné části webu a poskytuje výboru použitelná data pro objednávku, doplatky a kontrolu
plateb.

Testovací strategie navazuje na funkční specifikaci a technickou specifikaci k 2026-05-09. Prioritou je ověřit úzký
rozsah MVP, ne budoucí portálové funkce.

## Testovací rozsah

### Testovat v MVP

- veřejný web a odkaz na aplikační část,
- vstup do formuláře přes jednotkový token nebo kód,
- vyplnění a odeslání odpovědi za jednotku,
- validaci počtu čipů a výběru telefonu,
- výpočet doplatku,
- vytvoření variabilního symbolu,
- potvrzení doplatku a platebních pokynů,
- změnu odpovědi do uzávěrky,
- určení poslední platné odpovědi za jednotku,
- administrátorský přehled výboru,
- filtr jednotek bez odpovědi,
- export pro dodavatele,
- export pro kontrolu plateb,
- základní bezpečnost přístupu za jednotku a administrace,
- archivaci finálního souhrnu.

### Netestovat jako součást MVP

- elektronické hlasování,
- dlouhodobý portál pro všechny agendy SVJ,
- automatické párování plateb s bankou,
- automatické rozesílání e-mailů,
- kompletní evidence životního cyklu čipů po instalaci,
- samostatné účty všech spoluvlastníků nebo členů domácnosti.

## Testovací data

Před spuštěním testů připravit malou testovací sadu jednotek, která pokryje různé situace:

| Testovací jednotka | Účel |
| --- | --- |
| jednotka vlastněná fyzickou osobou | běžný vlastník a platební kontakt na vlastníka |
| jednotka SBD Mír | praktický uživatel nebo nájemník jako hlavní adresát agendy |
| jednotka s více opakovanými odpověďmi | ověření poslední platné odpovědi |
| jednotka bez odpovědi | ověření filtru a urgence |
| jednotka s neobvykle vysokým počtem čipů | ověření ruční kontroly výborem |
| jednotka s administrativní změnou po uzávěrce | ověření výjimky a interní poznámky |

Testovací kontakty nesmí být zaměnitelné s ostrými osobními údaji, pokud se testuje v produkčním prostředí. Testovací
data mají být jasně označena nebo použita pouze v testovacím prostředí.

## Testování veřejného webu

Ověřit:

- hlavní stránka se načte,
- existující sekce webu se načtou,
- odkaz na agendu přístupového systému vede na správnou aplikační část,
- veřejná část je použitelná na mobilu i počítači,
- veřejná část neobsahuje odpovědi jednotek,
- veřejná část neobsahuje kontakty jednotek,
- veřejný repozitář neobsahuje neveřejné exporty, tokeny, přístupové kódy ani servisní klíče.

## Testování formuláře jednotky

### Platná odpověď

Scénář:

1. Otevřít formulář platným tokenem jednotky.
2. Zkontrolovat, že se zobrazí správná jednotka.
3. Vyplnit jméno odpovídající osoby, kontakt a vztah k jednotce, pokud nejsou známé z profilu.
4. Zadat platný počet čipů.
5. Vybrat typ telefonu.
6. Ověřit zobrazený doplatek.
7. Potvrdit seznámení s doplatkem a platebními pokyny.
8. Odeslat odpověď.

Očekávaný výsledek:

- odpověď je uložena ke správné jednotce,
- odpověď má stav odeslané nebo platné odpovědi,
- je uložen čas odeslání,
- je vypočten doplatek,
- je přiřazen variabilní symbol,
- uživatel vidí potvrzení o odeslání.

### Povinná pole

Ověřit, že formulář neumožní finálně odeslat odpověď bez:

- jednotky nebo platného jednotkového přístupu,
- počtu čipů,
- typu telefonu,
- potvrzení doplatku a platebních pokynů,
- údajů o odpovídající osobě, pokud nejsou odvozené z přihlášení nebo profilu.

### Validace počtu čipů

Ověřit hodnoty:

- `0` je odmítnuto,
- záporné číslo je odmítnuto,
- desetinné číslo je odmítnuto,
- prázdná hodnota je odmítnuta,
- rozumné kladné celé číslo je přijato,
- neobvykle vysoké kladné celé číslo je buď přijato k ruční kontrole výborem, nebo označeno podle zvoleného návrhu.

### Výběr telefonu

Ověřit:

- lze vybrat pouze aktivní schválenou variantu telefonu,
- základní varianta má doplatek 0 Kč,
- ostatní varianty mají správnou cenu podle datového podkladu,
- aplikace nepředvybírá doporučenou variantu telefonu, pokud to výbor výslovně neschválil.

### Výpočet doplatku

Pro každou testovací variantu ověřit vzorec:

```text
doplatek = počet čipů * 44 Kč + doplatek zvolené varianty telefonu
```

Ověřit také, že částka zobrazená uživateli odpovídá částce uložené v odpovědi a částce v exportu pro platební kontrolu.

### Variabilní symbol

Ověřit:

- každá jednotka má v rámci agendy unikátní variabilní symbol,
- pracovní pravidlo odpovídá technické specifikaci nebo schválené účetní úpravě,
- variabilní symbol je viditelný uživateli v platebních pokynech,
- stejný variabilní symbol je v administraci i exportu pro kontrolu plateb.

## Testování změn odpovědí

### Opakovaná odpověď před uzávěrkou

Scénář:

1. Odeslat první platnou odpověď za jednotku.
2. Stejným jednotkovým přístupem odeslat změněnou odpověď před uzávěrkou.
3. Zkontrolovat administraci a export.

Očekávaný výsledek:

- nová odpověď je považována za poslední platnou,
- starší odpověď není použita pro finální objednávku,
- historie nebo stav starší odpovědi umožní dohledat, že byla nahrazena,
- export pro dodavatele obsahuje pouze poslední platnou odpověď.

### Změna po uzávěrce

Ověřit:

- běžný jednotkový přístup už po uzávěrce neumožní standardní změnu,
- aplikace uživateli srozumitelně sdělí, že má kontaktovat výbor,
- administrátor může provést schválenou výjimku,
- administrativní změna má interní poznámku výboru,
- export po administrativní změně obsahuje správnou finální odpověď.

## Testování administrace výboru

Ověřit, že administrátor může:

- zobrazit přehled všech jednotek,
- vidět stav odpovědi u každé jednotky,
- filtrovat jednotky bez odpovědi,
- zobrazit poslední platnou odpověď za jednotku,
- rozpoznat nahrazené nebo neplatné odpovědi,
- vidět vypočtený doplatek a variabilní symbol,
- připravit seznam pro e-mailovou urgenci,
- uzavřít sběr nebo označit odpovědi pro finální export podle zvoleného procesu,
- exportovat dodavatelský souhrn,
- exportovat platební podklad.

Ověřit, že administrátor nemůže omylem zveřejnit export přes veřejný odkaz bez ověření.

## Testování exportů

### Export pro dodavatele

Ověřit:

- export obsahuje jen poslední platnou nebo finální odpověď za jednotku,
- export neobsahuje jednotky bez odpovědi jako objednávkové řádky, pokud výbor nerozhodne jinak,
- export obsahuje číslo bytu, podlaží, kontakt, počet čipů a zvolený typ telefonu,
- export neobsahuje platební stav, interní poznámky výboru ani historii změn,
- formát CSV se otevře v běžném tabulkovém editoru bez rozbití diakritiky.

### Export pro kontrolu plateb

Ověřit:

- export obsahuje jednotku, kontakt, variabilní symbol, očekávanou částku a stav platby,
- očekávaná částka odpovídá finální odpovědi,
- jednotky bez zaplaceného doplatku lze vyfiltrovat,
- ručně doplněný stav platby se projeví v sestavě.

### Export jednotek bez odpovědi

Ověřit:

- export nebo přehled obsahuje pouze jednotky bez platné odpovědi,
- obsahuje kontakty potřebné pro urgenci,
- neobsahuje jednotky, které již mají platnou odpověď.

## Bezpečnostní testy

### Jednotkový přístup

Ověřit:

- token jednotky A nezobrazí data jednotky B,
- změna URL nebo parametru neumožní přístup k jiné jednotce,
- neplatný token je odmítnut,
- zneplatněný token je odmítnut,
- token ani jeho hash nejsou ve veřejném repozitáři,
- token není uložen v čitelném veřejném HTML.

### Administrátorský přístup

Ověřit:

- nepřihlášený uživatel neotevře administraci,
- běžný jednotkový přístup neotevře administraci,
- administrátorem může být jen schválený člen výboru,
- všichni tři členové výboru mohou mít samostatný administrátorský přístup,
- dodavatel nemá administrátorský přístup.

### Tajné klíče a konfigurace

Ověřit:

- připojovací údaje k databázi nejsou v repozitáři,
- připojovací údaje k databázi nejsou ve frontendovém JavaScriptu,
- skutečný `.env` není commitnutý do Gitu,
- `.env.example` neobsahuje citlivé hodnoty,
- konfigurační hodnoty jsou uložené v prostředí backendu nebo produkčního serveru,
- exporty s osobními údaji nejsou veřejně dostupné.

## Testování použitelnosti

Před ostrým spuštěním vybrat několik testovacích jednotek nebo členů výboru a ověřit:

- zda je text zadání srozumitelný,
- zda je jasné, že odpověď se vztahuje k jednotce,
- zda je jasné, kdo má formulář vyplnit,
- zda je jasné, že může vzniknout doplatek,
- zda je jasná výsledná částka,
- zda je jasný variabilní symbol,
- zda je jasné, do kdy je potřeba odpovědět,
- zda je jasné, jak změnit odpověď do uzávěrky,
- zda je jasné, co dělat po uzávěrce.

## Testování mobilu a přístupnosti

Ověřit alespoň ručně:

- formulář je použitelný na mobilu,
- texty a ovládací prvky se nepřekrývají,
- povinná pole a chyby jsou srozumitelné,
- potvrzovací texty jsou čitelné,
- tabulky v administraci jsou použitelné alespoň na běžném notebooku,
- formulář lze vyplnit bez zbytečně drobných ovládacích prvků.

## Testování datové kvality

Ověřit:

- každá odpověď má jednotku,
- každá finální odpověď má počet čipů, telefon, doplatek, variabilní symbol a čas odeslání,
- neexistují dvě finální odpovědi za jednu jednotku,
- neexistují duplicitní variabilní symboly,
- jednotka bez odpovědi se správně zobrazuje jako neodpovězená,
- jednotka s nahrazenou odpovědí má správně určenou poslední platnou odpověď,
- exporty odpovídají administrátorskému přehledu.

## Testování zálohy a archivace

Ověřit:

- výbor umí exportovat všechna data agendy do tabulkového formátu,
- finální souhrn použitý pro objednávku lze uložit jako archivní podklad,
- podklad pro kontrolu plateb lze uložit jako archivní podklad,
- po testu je jasné, která data jsou testovací a lze je odstranit.

## Kritéria pro spuštění

MVP nemá být spuštěno pro vlastníky a uživatele bytů, dokud neplatí:

- platná odpověď lze odeslat za testovací jednotku,
- opakovaná odpověď před uzávěrkou správně nahradí původní odpověď,
- neplatný počet čipů je odmítnut,
- výpočet doplatku je ověřen pro všechny varianty telefonů,
- variabilní symbol je unikátní a viditelný v platebních pokynech,
- administrátor vidí přehled jednotek a odpovědí,
- lze získat seznam jednotek bez odpovědi,
- export pro dodavatele obsahuje správná data,
- export pro kontrolu plateb obsahuje správná data,
- běžný jednotkový přístup nevidí cizí jednotku,
- administrace není dostupná bez přihlášení,
- neveřejná data, tokeny a servisní klíče nejsou ve veřejném repozitáři,
- testovací člen výboru potvrdil, že data v exportu jsou použitelná pro další práci.

## Testovací checklist před ostrým sběrem

1. Ověřit veřejný web a odkaz na aplikační část.
2. Ověřit formulář pro běžnou jednotku.
3. Ověřit formulář pro jednotku SBD Mír.
4. Ověřit odmítnutí neplatných hodnot počtu čipů.
5. Ověřit výpočet doplatku pro všechny telefonní varianty.
6. Ověřit opakovanou odpověď před uzávěrkou.
7. Ověřit chování po uzávěrce.
8. Ověřit administrátorský přehled.
9. Ověřit filtr jednotek bez odpovědi.
10. Ověřit export pro dodavatele.
11. Ověřit export pro kontrolu plateb.
12. Ověřit bezpečnost jednotkového tokenu.
13. Ověřit administrátorský přístup všech tří členů výboru.
14. Ověřit, že exporty nejsou veřejně dostupné.
15. Ověřit archivaci finálního souhrnu.