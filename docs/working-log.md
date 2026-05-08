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

Doplnění: pokud to nebude technicky příliš náročné, má systém pomoci výboru s připomenutím neodpovězených jednotek,
například vygenerováním seznamu kontaktů nebo e-mailu. Vhodné je také avízo před uzávěrkou pro jednotky, které dosud
neodpověděly.

## Průběžný záznam 2026-05-08: rozsah údajů

Byla doplněna odpověď k rozsahu údajů. Pro samotnou objednávku stačí jednotka, počet čipů a typ telefonu. Vhodné je
umožnit volnou poznámku pro dotazy a připomínky k agendě.

Jméno odpovídající osoby, kontakt a vztah k jednotce závisí na zvolené technologické variantě. Pokud bude existovat
obecná portálová identita s rolemi a přístupy, mají se tyto údaje odvodit z přihlášení nebo profilu. Pokud půjde
o MVP bez takové identity, je vhodné tyto údaje sbírat ve formuláři, aby výbor věděl, kdo odpověď za jednotku vyplnil.

## Průběžný záznam 2026-05-08: čipy a typy telefonů

Byla doplněna pravidla pro čipy a typy bytových telefonů. Počet čipů na jednotku nemá stanovený horní obchodní limit,
ale ve formuláři má jít o kladné celé číslo. Každý objednaný čip se platí; neexistuje základní počet čipů zahrnutý
v ceně.

Všechny typy bytového telefonu mají být dostupné pro všechny jednotky. Varianta bez doplatku se má řešit jako
základní verze telefonu s doplatkem 0 Kč. Výbor ani dodavatel nemají doporučenou výchozí variantu telefonu pro
nerozhodnuté partaje.

Doplnění: počet čipů má mít neomezený horní limit, ale hodnota 0 čipů má být považována za chybu. Cena jednoho čipu
je 44 Kč. Přesné typy telefonů, obrázky a ceny jsou k dispozici a nejvhodnější je předat je jako tabulku variant
s obrázky uloženými samostatně.

## Průběžný záznam 2026-05-08: doplatky a kontrola plateb

Byla doplněna pravidla pro doplatky. Ceny čipů i telefonů jsou známé a finální, takže formulář má zobrazovat finální
výši doplatku podle počtu čipů a zvoleného telefonu. Čipy i telefon mají být hrazeny jednou společnou platbou.

Každá objednávka nebo odpověď za jednotku má mít unikátní variabilní symbol. Kontrola plateb má probíhat porovnáním
výpisu z účtu s údaji v systému podle variabilního symbolu a částky. Systém má ideálně umožnit vygenerovat sestavu
jednotek, které v daném termínu nezaplatily. Automatické napojení na banku není požadavkem první fáze.

## Průběžný záznam 2026-05-08: exporty a kontrola

Byly doplněny odpovědi k exportům. Formát objednávky pro dodavatele zatím nebyl stanoven, ale pracovně se předpokládá
tabulka. Tabulka má obsahovat jméno, příjmení, kontakt, číslo bytu, podlaží, počet čipů a typ telefonu; rozsah údajů
je potřeba ještě potvrdit s dodavatelem podle jeho skutečných potřeb.

Export pro dodavatele i hlavní přehled pro výbor mají obsahovat poslední platnou odpověď za jednotku a generovat se
po uzavření sběru objednávek. Pro výbor má být dostupná filtrace jednotek bez odpovědi. Délka uchování odpovědí
a historie změn zatím není stanovena a závisí na zvoleném systému, kapacitě databáze a pravidlech uchování dat.

## Průběžný záznam 2026-05-08: dodavatelský termín a náhradní čipy

Byly doplněny odpovědi k dodavateli. Dodavatel pro objednávku a montáž potřebuje identifikaci vlastníka nebo nájemníka,
kontakt, číslo bytu, podlaží, počet čipů a typ telefonu. Finální souhrn má být dodavateli předán do 2026-05-24,
aby mohl připravit objednávku, konečnou cenu, smlouvu a podklady k úhradě.

Přibližně 5 dní před finálním termínem má výbor ručně zkontrolovat neodpovězené jednotky a poslat e-mailovou urgenci.
Po předání finálního souhrnu už se běžně nemá měnit počet čipů ani typ telefonu. Pro budoucí provoz je potřeba počítat
se ztracenými nebo poškozenými čipy, jejich deaktivací nebo vyřazením z evidence a objednáváním náhrad přes výbor.
Výbor má zvážit rezervní zásobu čipů, pracovně přibližně 60 kusů.

## Průběžný záznam 2026-05-08: podklady telefonních variant

Byly připraveny pracovní podklady k variantám bytových telefonů podle dodaného screenshotu a produktových stránek ABB.
Vznikl dokument `docs/analysis/12-telefonni-varianty.md`, datový soubor `docs/analysis/data/telefonni-varianty.csv`
a lokální obrázky ve složce `docs/analysis/assets/telefony/`.

Podklady obsahují čtyři varianty: základní audiotelefon, handsfree audiotelefon, videotelefon 4,3" a videotelefon 7".
U obrázků je potřeba před veřejným publikováním ověřit možnost použití produktových obrázků ABB nebo použít podklady
výslovně poskytnuté dodavatelem.

## Průběžný záznam 2026-05-08: podklad RFID čipu

Byl doplněn pracovní podklad k černé RFID klíčence pro přístupový systém. Vznikl dokument
`docs/analysis/13-cipy.md`, datový soubor `docs/analysis/data/cipy.csv` a lokální obrázek
`docs/analysis/assets/cipy/rfid-klicenka-cerna.jpg`.

Pro agendu SVJ zůstává pracovní cena čipu 44 Kč za kus. U obrázku je stejně jako u telefonů potřeba před veřejným
publikováním ověřit možnost použití produktové fotografie nebo použít podklady výslovně poskytnuté dodavatelem.

## Průběžný záznam 2026-05-08: komunikace před sběrem

Byly doplněny odpovědi výboru k přípravě komunikace s vlastníky a uživateli bytů. Nebude se připravovat samostatné
oficiální komunikační kolo před spuštěním sběru, protože problematika byla představena na shromáždění dne 2026-04-27.
Samotná existence doplatku se nebude zvlášť vysvětlovat; případné stručné vysvětlení úhrady má uvést, že dodavatel
uzavírá jednu smlouvu se SVJ jako celkem, nikoliv samostatné smlouvy s jednotlivými partajemi.

Standardní cestou odpovědi má být pouze online formulář. Samostatná evidence odpovědí mimo online formulář se pro
první agendu neplánuje. Sběr bude spuštěn po publikování příslušné verze webu nebo portálu. Uzávěrka zůstává
2026-05-24. Kontroly úplnosti proběhnou nejméně 2026-05-19 formou avíza neodpovězeným jednotkám a 2026-05-24 jako
finální kontrola chybějících odpovědí a zjevných nesrovnalostí.
