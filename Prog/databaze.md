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

Chci-li spočítat, kolik měst je v jakém kraji, použiji `COUNT`. Pracovní tabulku ale musím odpovídajícím způsobem rozdělit do skupin. Skupiny lze dále filtrovat pomocí `HAVING`.

## Vytvoření tabulky

```sql
CREATE TABLE vozidlo (
    `id` INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT,
    `spz` TEXT NOT NULL,
    `typ` TEXT NOT NULL,
    `nosnost` INTEGER NOT NULL
);
```

`NOT NULL` mi říká, že záznam nesmí být prázdný, `PRIMARY KEY` zase zajišťuje unikátnost.

Stejně tak lze data přidávat, měnit a mazat. Pokud záznam nechci nastavit, mám možnost `NULL`.

```sql
INSERT INTO vozidlo
    ( id, nosnost, spz, typ )
    VALUES ( 5, 5000, "1A9 89-45", "dodávka" )

UPDATE vozidlo SET spz="1A8 89-45" WHERE id = 5

DELETE FROM vozidlo WHERE id = 5
```
## Vypsání seznamu tabulek

Záleží na poskytovateli, třeba `SHOW TABLES`, `DESCRIBE TABLES`, `SELECT * FROM sqlite_master`.