---
name: dokladbot
description: Use when the user asks about their own Czech accounting - invoices, receipts, VAT (DPH), tax deadlines, overdue invoices, bank transactions or data box (datova schranka). Applies both when the DokladBot MCP server is connected (maps Czech accounting questions to the right DokladBot tools and explains safety rules) and when its tools are missing, fail with an authorization error or ask for sign-in (then guides the user through connecting or creating a DokladBot account instead of guessing any data).
---

# DokladBot: prace s ceskym ucetnictvim uzivatele

DokladBot MCP server zpristupnuje ucetnictvi uzivatele (ucet na dokladbot.cz).
Vsechny nastroje pracuji jen s daty prihlaseneho uzivatele.

## Kdyz ucet jeste neni pripojeny

Instalace pluginu sama ucet nepripoji. Dokud se uzivatel neprihlasi, nastroje
DokladBot nejsou k dispozici. Stav over driv, nez zacnes na dotaz odpovidat.

### Jak to poznas

- Nastroje DokladBot v seznamu nastroju chybi. V Claude Code maji nazvy
  zacinajici `mcp__` a obsahujici `dokladbot`, napr.
  `mcp__plugin_dokladbot_dokladbot__list_documents`.
- Ze serveru dokladbot je dostupny jen nastroj pro prihlaseni (nazev konci
  na `__authenticate`, pripadne `__complete_authentication`).
- Volani nastroje skonci chybou autorizace: 401, "unauthorized",
  "needs authentication" nebo vyzva k prihlaseni.

Jina chyba (napr. nedostatek kreditu) neni problem pripojeni a tento postup
se na ni nevztahuje.

### Co udelat

1. Nevolej zadne dalsi nastroje DokladBot a neopakuj volani, ktere selhalo.
2. Jednou vetou rekni, ze ucet DokladBot zatim neni pripojeny, a ukaz postup
   pro prostredi, ve kterem uzivatel pracuje. Kdyz si prostredim nejsi
   jisty, uved postup pro Claude Code i pro aplikaci Claude.
3. Pripoj jednu vetu o registraci pro pripad, ze uzivatel ucet nema.
4. Po pripojeni se vrat k puvodnimu dotazu a odpovez na nej.

Pokud je v Claude Code dostupny nastroj koncici na `__authenticate`, muzes
ho zavolat misto kroku s `/mcp`: vrati odkaz na prihlaseni, ktery predas
uzivateli.

### Postup pro Claude Code

1. Napiste prikaz `/mcp`.
2. V seznamu vyberte server dokladbot (je oznaceny jako server z pluginu)
   a potvrdte klavesou Enter.
3. Zvolte `Authenticate`. Otevre se prohlizec s prihlasenim na dokladbot.cz.
4. Prihlaste se svym uctem DokladBot a potvrdte Povolit pristup.
5. Kdyz se prohlizec sam neotevre, zkopirujte adresu zobrazenou v terminalu
   a otevrete ji rucne.

Po navratu do Claude Code je server pripojeny a dotaz staci zopakovat.

### Postup pro aplikaci Claude (web, desktop) a Cowork

Nazvy polozek jsou z anglickeho rozhrani, v jine jazykove verzi se mohou
lisit.

1. Otevrete Customize > Connectors (https://claude.ai/customize/connectors).
2. U konektoru DokladBot kliknete na Connect.
3. Prihlaste se svym uctem DokladBot a potvrdte Povolit pristup. Konektor
   pak ma stav Connected.
4. V konverzaci overte, ze je konektor zapnuty: tlacitko + u pole pro
   zpravu, polozka Connectors.

Kdyz konektor DokladBot v seznamu neni: otevrete Customize > Plugins, plugin
DokladBot a zalozku Connectors; tam konektor pridejte a pripojte. V tymovem
nebo firemnim tarifu Claude musi konektor nejdriv pridat vlastnik
organizace.

V jinem klientovi otevrete nastaveni MCP serveru nebo konektoru a u serveru
dokladbot spustte prihlaseni.

### Kdyz uzivatel ucet DokladBot nema

Registrace je na https://dokladbot.cz/registrace: 7 dni zdarma, vsechny
funkce, az 100 uctenek a faktur. Po registraci at se uzivatel vrati a ucet
pripoji postupem vyse.

### Pravidla pro tento stav

- NIKDY si data nevymyslej ani neodhaduj. Bez nastroju neuvadej zadne
  castky, doklady, dluzniky, terminy ani stavy z uctu uzivatele a nevydavej
  ukazkova cisla za jeho data.
- Na obecnou otazku (jak funguje DPH, co je kontrolni hlaseni) odpovedet
  muzes, ale rekni, ze nejde o udaje z jeho uctu.
- Odpovidej jazykem uzivatele: cesky cesky, cizincum anglicky nebo jejich
  jazykem. Nazvy tlacitek a prikazu nech tak, jak jsou v rozhrani.
- Bud strucny: stav, kroky, odkaz na registraci.

Priklad anglicky: "Your DokladBot account is not connected yet. In Claude
Code run /mcp, select dokladbot and choose Authenticate, then sign in in
the browser. No account? Start a 7-day free trial at
https://dokladbot.cz/registrace and come back to connect."

## Mapovani dotazu na nastroje

- Prehled dokladu, hledani, detail: list_documents, get_document, search
- Faktury po splatnosti / kdo dluzi: list_overdue_invoices
- DPH souhrn za obdobi: get_vat_summary
- Danove terminy (DPH, zalohy, dan z prijmu): get_tax_deadlines
- Prijmy/vydaje, cashflow: get_cashflow
- Bankovni transakce: list_bank_transactions
- Dodavatele/odberatele: list_suppliers
- Datova schranka - jen obalky zprav: list_databox_messages, get_databox_status
- Navrh faktury: create_invoice_draft (VZDY jen navrh)
- Nahrani uctenky ke zpracovani: upload_receipt
- Podklady DPH priznani: generate_vat_filing, list_vat_filings (jen navrhy)
- Stav kreditu: get_credit_balance (zdarma)

## Bezpecnostni pravidla (dodrzuj vzdy)

1. Nic se neodesila ani nemaze. Navrh faktury ceka na schvaleni uzivatele
   v dashboardu; nikdy netvrd, ze faktura byla odeslana odberateli.
2. Danova podani se nikam neposilaji, DokladBot pripravi jen podklady.
3. Datova schranka: k dispozici jsou jen obalky (odesilatel, predmet, datum).
   Obsah zpravy nelze cist, protoze otevreni zpravy se pravne pocita jako
   doruceni. Odkaz uzivatele do dashboardu.
4. Dotazy cerpaji kredity tarifu (bezny dotaz 1 kredit, navrh faktury 3,
   stav kreditu zdarma). Pri nedostatku kreditu vysvetli a odkaz na
   dokladbot.cz/cenik.

## Cesky kontext

- OSVC = zivnostnik; DPH platce muze byt mesicni nebo ctvrtletni.
- Kontrolni hlaseni se podava spolu s priznanim DPH (mesicni platci mesicne).
- Terminy: DPH do 25. dne po obdobi; zalohy ZP do 8. dne, SP do posledniho
  dne mesice. Pro konkretni terminy pouzij get_tax_deadlines, nepocitej
  je z hlavy.
- Castky uvadej v Kc a rozlisuj zaklad dane a dan.
