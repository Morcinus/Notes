# Hardware

Počítač nutně potřebuje základní desku, procesor, RAM a BIOS.

V telefonu je to samé, v menším, navíc baterka.

## Základní deska

Socket, na něj se přidělává procesor
RAM sloty
Na zadní straně PCI = připojení rozšiřujícího hardwaru, grafická, zvuková, síťová karta.
BIOS = Firmware, první program po spuštění, vypálený na ROM, zkontroluje, že existují základní komponenty, z pevného disku natáhne zavaděč operačního systému. Zinicializuje grafiku, předá velení dál.

### Procesor

ALU = aritmeticko-logická jednotka
Cache - rozdělené na (typicky tři) úrovně L1 (32 kB), L2 (256 kB), L3 (8 MB), každé jádro má vlastní L1, L3 je typicky sdílená. L1 je rozdělená na Instruction cache a Data cache. Vždy se současně vyšle požadavek do všech úrovní, z té nejrychlejší, kde je, tak jde zpátky a zároveň se nakopíruje do nižších cache.
Registry - místo v paměti, kam se vejde jedno číslo (64bit procesor -> je velké právě tolik).
Hodiny, posílají impulzy = ticky
Memory controler - komunikuje s cache a RAM

## Zdroj

Velká krabice s drátama, jedna část kouká na uživatele. Přivádí elektřinu k základní desce, mechanice, disku, větrákům.
Leze z něj stejnosměrných 5 V (Graetzovo zapojení, vyhlazení).

## Hard disk

Plochý široký datový kabel

## Chlazení

Aktivní = větrák
Pasivní = odvod na kovovou desku

## Myš

Dvě tlačítka, kolečko, třetí tlačítko pod ním, fotorezistor, dioda.

## Spuštění operačního systému

Z pevného disku, externí paměti nebo z jiného počítače v síti.

## Maturita

Když tam něco rveš, podívej se, jak tam jsou výkusy. Základní deska může být i z routeru - nemá grafiku, spoustu čipů obsluhujících připojené počítače, hlavní čip.