# DokladBot plugin pro Claude Code

Ceske ucetnictvi primo v Claude: faktury, uctenky, DPH, danove terminy,
banka a datova schranka z vaseho uctu [DokladBot](https://dokladbot.cz).

Czech accounting inside Claude: invoices, receipts, VAT summaries, tax
deadlines, bank transactions and data box overview from your
[DokladBot](https://dokladbot.cz) account.

## Instalace

```
/plugin marketplace add OndrejKnedla/dokladbot-claude-plugin
/plugin install dokladbot@dokladbot
```

Po instalaci se pri prvnim pouziti otevre prihlaseni na dokladbot.cz -
prihlaste se svym uctem a potvrdte Povolit pristup. Zadne API klice ani
hesla se nikam nekopiruji.

Potrebujete ucet DokladBot: [registrace zdarma](https://dokladbot.cz/registrace).

## Co plugin umi

- Doklady a faktury: vypisy, hledani, detail vcetne rozpisu DPH
- Faktury po splatnosti: kdo vam dluzi a jak dlouho
- Podklady DPH: souhrn za mesic nebo ctvrtleti
- Danove terminy: DPH, zalohy na pojisteni, dan z prijmu
- Prehled hospodareni a bankovni transakce
- Datova schranka: prehled prijatych pisemnosti (jen obalky)
- Navrh faktury jednou vetou (ceka na schvaleni v dashboardu)
- Nahrani uctenky ke zpracovani

## Prikazy

- `/dokladbot:faktura Novak s.r.o., 15000 Kc, konzultace` - navrh faktury
- `/dokladbot:dph Q3 2026` - souhrn DPH za obdobi
- `/dokladbot:terminy` - nejblizsi danove terminy
- `/dokladbot:splatnosti` - faktury po splatnosti

## Bezpecnost

Plugin je navrzeny tak, aby AI nemohla nic pokazit:

- Nic neodesila ani nemaze. Navrh faktury ceka na vase schvaleni v dashboardu.
- Danova podani se nikam neposilaji, pripravuji se jen podklady.
- Datova schranka jen ke cteni obalek: otevreni zpravy se pravne pocita jako
  doruceni, proto se obsah cte vyhradne v dashboardu.
- Pristup je vazany na vas ucet a kdykoli ho zrusite v Nastaveni, sekce
  API klice.

## Ceny

Pripojeni je soucasti predplatneho DokladBot. Dotazy cerpaji kredity tarifu
(bezny dotaz 1 kredit, navrh faktury 3 kredity, stav kreditu zdarma).
Kompletni cenik: https://dokladbot.cz/cenik

## Privacy Policy

Zpracovani osobnich udaju vcetne AI konektoru popisuji
[zasady ochrany osobnich udaju](https://dokladbot.cz/ochrana-osobnich-udaju)
(sekce 10). Podminky sluzby: https://dokladbot.cz/obchodni-podminky

Data collection and processing, including AI connectors, are described in
our [privacy policy](https://dokladbot.cz/ochrana-osobnich-udaju)
(section 10 covers AI assistant connections). The plugin connects only to
first-party DokladBot APIs (dokladbot.cz) over HTTPS with OAuth 2.1; no
data is shared with third parties beyond what the privacy policy states.

## Podpora

- E-mail: podpora@dokladbot.cz
- Web: https://dokladbot.cz/funkce/ai-asistent
- Hlaseni bezpecnostnich problemu: podpora@dokladbot.cz (predmet SECURITY)
