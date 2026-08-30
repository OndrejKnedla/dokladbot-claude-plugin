---
description: Souhrn DPH za obdobi z DokladBotu
argument-hint: obdobi, napr. "Q3 2026" nebo "srpen 2026"
---

Pomoci nastroje get_vat_summary z DokladBot MCP serveru zjisti souhrn DPH
za obdobi: $ARGUMENTS (pokud neni uvedeno, pouzij posledni ukoncene obdobi
podle toho, zda je uzivatel mesicni nebo ctvrtletni platce - pripadne se
zeptej).

Vystup prehledne: zaklady a dan podle sazeb, celkova danova povinnost nebo
nadmerny odpocet. Pripomen nejblizsi termin podani (nastroj get_tax_deadlines)
a ze podani vzdy odesila uzivatel sam, DokladBot pripravi jen podklady.
