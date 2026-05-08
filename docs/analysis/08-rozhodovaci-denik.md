# Rozhodovací deník

## 2026-05-08: sjednocení veřejného webu

Rozhodnutí: založit jeden hlavní veřejný web v repozitáři `svjbzenecka22.github.io`.

Důvod:

- hlavní web běží na adrese `https://svjbzenecka22.github.io/`,
- existující tematické weby lze zařadit jako podsložky,
- projekt bude přehlednější pro budoucí rozvoj.

## 2026-05-08: ponechání původních repozitářů

Rozhodnutí: původní repozitáře `shromazdeni_260427` a `balkony` zatím nemazat.

Důvod:

- nový hlavní repozitář už obsahuje potřebné zdroje,
- původní repozitáře mohou zůstat jako historická záloha,
- jejich mazání není nutné pro provoz nového webu.

## 2026-05-08: nevybírat technologii před analýzou

Rozhodnutí: před návrhem soukromé části webu nejprve připravit byznys a IT analýzu.

Důvod:

- budoucí požadavky zahrnují veřejný web, soukromé sekce, dokumenty, souhlasy a možné hlasování,
- některé funkce mají právní, bezpečnostní a procesní dopady,
- první datová agenda k přístupovému systému může být MVP, ale nemá předčasně svázat celý budoucí portál.

## 2026-05-08: první agenda se vede po jednotkách

Rozhodnutí: pro první agendu přístupového systému se bude pracovat s odpovědí za bytovou jednotku, nikoliv s více
samostatnými osobními odpověďmi za vlastníky, nájemníky nebo uživatele bytu.

Důvod:

- v první fázi neexistuje spolehlivý systém, proti kterému by bylo možné ověřit totožnost osoby a její oprávnění za jednotku,
- praktickým cílem je získat použitelnou objednávkovou odpověď za každou jednotku,
- případné opakované vyplnění za stejnou jednotku se má chápat jako změna odpovědi jednotky,
- do uzávěrky má pro další analýzu platit poslední odpověď za jednotku,
- dlouhodobě je vhodným směrem stabilní přístup nebo účet za jednotku, použitelný i pro další agendy.

Poznámka: u bytů vlastněných fyzickou osobou zůstává odpovědnost vůči SVJ na vlastníkovi. U bytů ve vlastnictví
Stavebního bytového družstva Mír se předpokládá praktická role uživatele bytu při volbě počtu čipů a typu telefonu;
platební komunikace a platba mají směřovat na nájemníky, nikoliv přes SBD Mír jako zprostředkovatele platby.
U spoluvlastnictví stačí odpověď jedné osoby jednající za jednotku. U bytů vlastněných fyzickou osobou budou
oficiálně oslovováni vlastníci, nikoliv nájemníci.

## 2026-05-08: změny odpovědí do uzávěrky a po ní

Rozhodnutí: do uzávěrky má být změna odpovědi za jednotku samoobslužná a jako finální má platit poslední odpověď
za jednotku před uzávěrkou. Po uzávěrce už se změny nemají řešit běžnou uživatelskou částí systému.

Důvod:

- před uzávěrkou je praktické umožnit partajím opravit odpověď bez administrativní zátěže výboru,
- po uzávěrce už výbor potřebuje stabilní podklad pro objednávku,
- individuální pozdní změny mají jít přes výbor e-mailem, telefonicky nebo přes WhatsApp,
- pokud výbor pozdní změnu přijme, zapíše ji administrativně ze své strany,
- jednotky bez odpovědi budou po uzávěrce připomenuty e-mailem.

## 2026-05-08: rozsah údajů pro první sběr

Rozhodnutí: pro samotnou objednávku přístupového systému stačí jednotka, počet čipů a typ telefonu. Formulář má ale
umožnit i volnou poznámku pro dotazy a připomínky k agendě.

Důvod:

- dodavatelský souhrn pravděpodobně potřebuje hlavně objednávkové údaje,
- výbor může potřebovat dohledat, kdo odpověď za jednotku vyplnil,
- pokud nebude existovat portálová identita s rolemi a přístupy, je vhodné ve formuláři sbírat jméno odpovídající
  osoby, kontakt a vztah k jednotce,
- pokud portálová identita existovat bude, mají se tyto údaje přednostně odvodit z přihlášení nebo profilu,
- volná poznámka má být omezena na dotazy a připomínky k agendě, aby se nesbíraly zbytečné osobní nebo citlivé údaje.

## 2026-05-08: pravidla pro čipy a typy telefonů

Rozhodnutí: počet čipů na jednotku nemá stanovený horní obchodní limit, ale hodnota 0 čipů má být považována za
chybu. Každý objednaný čip se platí a cena jednoho čipu je 44 Kč. Všechny typy bytového telefonu mají být dostupné
pro všechny jednotky. Varianta bez doplatku má být vedena jako základní verze telefonu s doplatkem 0 Kč.

Důvod:

- výbor nechce předem omezovat horní počet čipů na jednotku,
- hodnota 0 čipů by znamenala nefunkční přístup uživatele jednotky do domu nebo společných částí,
- neexistuje základní počet čipů zahrnutý v ceně,
- dostupnost telefonů nemá být omezena podle jednotky,
- výbor ani dodavatel nemají doporučenou výchozí variantu telefonu pro nerozhodnuté partaje,
- konkrétní názvy a ceny variant je potřeba převzít z aktuální nabídky nebo ceníku dodavatele.

## 2026-05-08: doplatky a kontrola plateb

Rozhodnutí: ceny čipů i telefonů jsou známé a finální. Formulář má zobrazovat finální výši doplatku. Čipy i telefon
mají být hrazeny jednou společnou platbou. Každá objednávka nebo odpověď za jednotku má mít unikátní variabilní symbol.

Důvod:

- není potřeba pracovat s orientační cenou nebo pozdějším zpřesněním,
- jednotná platba za čipy i telefon je administrativně jednodušší,
- variabilní symbol umožní výboru kontrolovat platby proti výpisu z účtu,
- kontrola má porovnávat variabilní symbol a částku s údaji v systému,
- systém má ideálně umožnit vygenerovat sestavu jednotek, které v daném termínu nezaplatily,
- automatické napojení na banku není požadavkem první fáze.

## 2026-05-08: exporty pro dodavatele a výbor

Rozhodnutí: formát objednávky pro dodavatele zatím nebyl dodavatelem stanoven, ale pracovně se předpokládá tabulkový
export. Export má obsahovat poslední platnou odpověď za jednotku a má se generovat po uzavření sběru objednávek.

Důvod:

- tabulka je praktický předávací formát pro výbor i dodavatele,
- pracovní rozsah exportu pro dodavatele je jméno, příjmení, kontakt, číslo bytu, podlaží, počet čipů a typ telefonu,
- rozsah osobních a kontaktních údajů je potřeba ještě potvrdit podle skutečných potřeb dodavatele,
- výbor potřebuje filtrovat jednotky bez odpovědi, aby je mohl kontaktovat,
- délka uchování odpovědí a historie změn zatím není stanovena a závisí na zvoleném systému, kapacitě databáze a pravidlech uchování dat.

## 2026-05-08: termín dodavatelského souhrnu a náhradní čipy

Rozhodnutí: finální souhrn má být dodavateli předán do 2026-05-24. Přibližně 5 dní před tímto termínem má výbor
zkontrolovat neodpovězené jednotky a poslat jim e-mailovou urgenci. Po předání finálního souhrnu už se běžně nemá
měnit počet čipů ani typ telefonu v rámci objednávky.

Důvod:

- dodavatel potřebuje finální seznam pro přípravu objednávky, konečné ceny, smlouvy a podkladů k úhradě,
- partaje mohou hradit finální částku podle formuláře bez čekání na další potvrzení dodavatele,
- pozdní změny po předání souhrnu by narušily objednávku,
- u ztracených nebo poškozených čipů bude potřeba čip deaktivovat nebo vyřadit z evidence,
- náhradní čipy se budou objednávat přes výbor,
- výbor má zvážit objednání rezervních čipů do zásoby, pracovně přibližně 60 kusů.
