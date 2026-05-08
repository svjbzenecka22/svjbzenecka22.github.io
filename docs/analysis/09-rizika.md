# Rizika

## Riziko: předčasný výběr technologie

Popis: Technologie může být vybrána podle první agendy, ale později nemusí stačit pro dokumenty, souhlasy nebo hlasování.

Mitigace: Nejprve popsat veřejné a neveřejné procesy, až poté vybrat technologii.

## Riziko: zveřejnění citlivých informací

Popis: Veřejný GitHub Pages web je dostupný komukoli.

Mitigace: Veřejné a neveřejné dokumenty evidovat odděleně. Citlivá data neukládat do veřejného repozitáře.

## Riziko: nejasná odpovědnost za jednotku

Popis: Není jasné, zda za jednotku odpovídá vlastník, nájemník nebo jiná osoba.

Mitigace: Před sběrem požadavků definovat pravidlo pro jednu finální odpověď za jednotku.

## Riziko: online hlasování bez právního posouzení

Popis: Hlasování SVJ může mít pravidla daná zákonem, stanovami a povahou rozhodnutí.

Mitigace: Hlasování řešit až samostatně, s ověřením právních a organizačních podmínek.

## Riziko: free tarif přestane stačit

Popis: Bezplatná služba může změnit podmínky nebo limity.

Mitigace: Volit řešení s exportem dat a možností migrace.

## Riziko: výbor nebude schopen systém spravovat

Popis: Příliš složité řešení může být provozně neudržitelné.

Mitigace: Preferovat jednoduché procesy, dobrou dokumentaci a nízkou provozní náročnost.

## Riziko: více rozdílných odpovědí za jednu jednotku

Popis: Za jednu jednotku může odpovědět více osob, například vlastník, spoluvlastník a nájemník, a odpovědi se mohou lišit.

Mitigace: Před spuštěním sběru stanovit pravidlo jedné finální odpovědi za jednotku, včetně pravidla pro změny a spory.

## Riziko: nejasné potvrzení doplatku

Popis: Partaj nemusí rozumět výši doplatku nebo platebním pokynům, zejména pokud nebude jasně zobrazen finální výpočet, částka a variabilní symbol.

Mitigace: Formulář má zobrazit finální cenu podle počtu čipů a zvoleného telefonu, celkovou částku jedné platby a variabilní symbol. Text potvrzení má jasně uvádět, že jde o finální doplatek podle aktuální odpovědi.

## Riziko: sběr nadbytečných osobních údajů

Popis: Formulář může z pohodlnosti sbírat více údajů, než je pro objednávku nutné.

Mitigace: Před návrhem formuláře určit minimální povinné údaje a volitelné údaje povolit jen s jasným účelem.

Poznámka: pokud nebude existovat portálová identita s rolemi a přístupy, může být důvodné sbírat jméno odpovídající
osoby, kontakt a vztah k jednotce. Volná poznámka má být povolena jen pro dotazy a připomínky k agendě a má být
doplněna upozorněním, aby uživatelé neuváděli zbytečné osobní nebo citlivé údaje.

## Riziko: opomenutí neonline odpovědí

Popis: Některé osoby mohou odpovědět e-mailem, telefonicky, osobně nebo na papíře. Pokud se tyto odpovědi nedostanou do stejné evidence, souhrn bude chybný.

Mitigace: Připravit náhradní postup a označovat ručně doplněné odpovědi v evidenci.

## Riziko: nevhodný export pro dodavatele

Popis: Dodavatel může potřebovat jiné členění nebo formát dat, než výbor předpokládá.

Mitigace: Před spuštěním sběru ověřit u dodavatele požadovaný formát objednávkového souhrnu a technické údaje potřebné k montáži.

Poznámka: pracovní návrh počítá s tabulkou obsahující jméno, příjmení, kontakt, číslo bytu, podlaží, počet čipů a typ telefonu. Rozsah osobních a kontaktních údajů je potřeba potvrdit s dodavatelem a nepředávat údaje, které pro objednávku nebo montáž nepotřebuje.

## Riziko: nejasná doba uchování odpovědí

Popis: Bez stanovené doby uchování mohou v systému zůstat odpovědi a historie změn déle, než je prakticky nebo právně vhodné.

Mitigace: Při výběru technologie stanovit pravidlo uchování odpovědí, historie změn, exportů a platebních podkladů. Zohlednit kapacitu systému, potřebu dohledatelnosti a minimalizaci osobních údajů.

## Riziko: pozdní změny po objednávce

Popis: Partaje mohou chtít změnit počet čipů nebo typ telefonu po uzávěrce nebo po předání objednávky dodavateli.

Mitigace: Předem zveřejnit uzávěrku, pravidla změn a dopad pozdních změn na cenu, dodání nebo individuální řešení.

## Riziko: neobvykle vysoký počet čipů

Popis: Počet čipů na jednotku nemá stanovený horní obchodní limit, takže některá odpověď může obsahovat neobvykle vysoký počet.

Mitigace: Formulář má přijímat kladné celé číslo, ale výbor má před objednávkou zkontrolovat neobvykle vysoké hodnoty a případně je individuálně ověřit. Hodnota 0 má být odmítnuta jako chyba.

## Riziko: ztracené nebo zneužitelné čipy

Popis: Ztracený čip může po nálezu použít neoprávněná osoba, pokud nebude vyřazen z evidence nebo deaktivován.

Mitigace: Připravit provozní postup pro hlášení ztráty nebo poškození čipu, deaktivaci nebo vyřazení čipu a objednání náhradního čipu přes výbor. Výbor má zvážit rezervní zásobu čipů v domě.

## Riziko: nedostatečná zásoba náhradních čipů

Popis: Pokud výbor nebude mít žádné náhradní čipy, bude řešení ztrát nebo poškození závislé na dodávce od dodavatele.

Mitigace: Při první objednávce zvážit objednání rezervních čipů do zásoby. Pracovní úvaha je přibližně 60 čipů, finální množství má výbor rozhodnout samostatně.

## Riziko: chybně přiřazená nebo nezaplacená platba

Popis: Platba může přijít bez správného variabilního symbolu, v jiné částce nebo po termínu.

Mitigace: Každá objednávka má mít unikátní variabilní symbol a systém má evidovat očekávanou částku. Výbor má kontrolovat výpis z účtu podle variabilního symbolu a částky a generovat sestavu jednotek, které v termínu nezaplatily.