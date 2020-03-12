# Kryptografie

kódování = převod 1:1
šifrování = složitější manipulace, potřebuji speciální klíč

cleartext = původní zpráva
ciphertext = zašifrovaný

## Symetrická šifra

(víceméně) stejný klíč pro šifrování i dešifrování
pro každou komunikaci potřebuji jiný klíč
např. Vigenerova šifra

## Asymetrická šfira

dva jiné klíče, public a private
pomalejší
stačí jednou pro každého uživatele
z privátního lze jednoduše získat veřejný, ne naopak

## Prolomení šifry

Frekvenční analýza

## Hashování

ověření, že zpráva není poškozená
zhuštění obsahu zprávy do pár bitů (~16)
kryptografická hash funkce = dvě rozdílné zprávy téměř určitě nebudou mít stejný hash

## Příklady

HTTPS: asymetrickou šifrou se zařídí spojení, poté se vytvoří jednorázový klíč pro další komunikaci