# Vyhodnocování aritmetického výrazu

Například "5 + 4 * 3".

Běžně se používá AST = abstraktní syntaktický strom.

	  +
	 / \
	5   *
	   / \
	  4   3

## Spočtení výsledku

Když mám strom, volám rekurzivně na každém podstromu volám funkci, která vrátí číselný výsledek.

## Vytvoření stromu

Pomocí gramatiky udělám zápis:

	E -> F + E
	E -> F
	F -> N * F
	F -> N
	N -> číslo

E je celý výraz složený z několika sčítání, F je výraz jen z násobení. Šipka značí, že se jedna část skládá z dalších.

Celý výraz nejprve pošlu do **lexeru**, který jej rozseká na tokeny, např. *číslo(5)*, *plus* a podobně. Tyto tokeny nasypu do **parseru**, který vyřeší závislosti mezi nimi a sestaví strom.

## Parsování

Zde využijeme gramatiku. Vezmu soubor tokenů z lexeru, nejprve naprogramuju typ N. Ten z tokenu udělá podstrom -- číslo. Pak implementuju typ F. Ten za první token považuje číslo. Poté očekává krát a další F a vrací násobení dvou podstromů. Pokud tam další F není, vrátím jenom číslo.

Pro E postupuju analogicky. Akorát při zjišťování, co následuje, nechci vybrat token ze seznamu, takže se na něj jen podívám a znovu jej vrátím. Teprve pokud následuje další E, tak jej skutečně odeberu.

Pokud chci, můžu již za běhu parseru počítat mezivýsledky a strom vůbec nesestavovat.

## Lexování

Začnu trikem, k celému vstupu přidám mezeru, což mi jej přirozeně ukončí. Pokud narazím na číslo, které může mít více znaků, tento fakt si poznačím a při prvním nečíslicovém znaku jej zpracuji do tokenu.

Na konci se ještě vyplatí přidat speciální token *EOT*, kterým si ověřím, že parsování doběhlo správně.

 ## Aplikace

 Pokud bych takto zpracovával kód, vzniknou mi i další typy operátorů. Třeba if by bral tři typy: podmínku, větev then a větev else.

 ## Závorky

 Díky tomuto systematickému přístupu stačí do gramatiky přidat `F -> (E)`.