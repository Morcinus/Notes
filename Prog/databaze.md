# Databáze

## Access

Jednotlivé tabulky a odkazy mezi nimi
- Seznam jízd - každá v sobě má odkaz na náklaďák
- Náklaďák - informace o hmotnosti, rozměrech, SPZ. Náklaďáky v sobě ale jízdy neukládají, databázi vždy spočítám a díky tomu získám zpětnou informaci.

Řádky jsou jednotlivé záznamy, sloupce jsou data. Odkaz na jinou tabulku je jakoby samostatný typ, říká se mu *foreign key*. Prakticky odkazuje na id záznamu a id tabulky, ve které je. Id funguje jako *primary key*.

Všechny databáze by měly mít vlastnosti ACID *(Atomicity, Consistency, Isolation, Durability)*.

## SQL

Structured Query Language, jazyk, který lze používat pro všechny databázové programy.

Příkaz `SELECT` vybere několik sloupců a dám jim jména, s nimi pracuju skrze příkaz `FROM`. Příkaz `JOIN` spojí sloupce do pracovní tabulky, potřebuje upřesnění `ON`, které definuje, jak je pospojovat.

```sql
SELECT
mesto.jmeno Město,
kraj.jmeno Kraj
FROM
mesto
JOIN kraj ON (mesto.kraj = kraj.id)
WHERE
(mesto.obyvatel > 20000)
```

Tento kód zobrazí jméno města a kraje, ve kterém se nachází. Pomocí `WHERE` provádím další filtraci.

```sql
SELECT
kraj.jmeno Kraj,
COUNT(mesto.id) "Počet měst",
SUM(mesto.obyvatel) Obyvatel
FROM
mesto
JOIN kraj ON (kraj.id = mesto.kraj)
GROUP BY
kraj.id
```

Chci-li spočítat, kolik měst je v jakém kraji, použiji `COUNT`. Pracovní tabulku ale musím odpovídajícím způsobem rozdělit do skupin.

## Jízdy

SELECT
*
FROM
jizda
JOIN ridic ON (jizda.ridic = ridic.id)
JOIN vozidlo ON (jizda.vozidlo = vozidlo.id)

1

	SELECT
	jmeno
	FROM
	ridic
2

	SELECT
	*
	FROM
	vozidlo
3

	SELECT
	jizda.datum,
	vozidlo.spz,
	jizda.vzdalenost
	FROM
	jizda
	JOIN ridic ON (jizda.ridic = ridic.id)
	JOIN vozidlo ON (jizda.vozidlo = vozidlo.id)