---
name: dokladbot
description: Use when the user asks about their Czech accounting - invoices, receipts, VAT (DPH), tax deadlines, overdue invoices, bank transactions or data box (datova schranka) - and the DokladBot MCP server is connected. Maps Czech accounting questions to the right DokladBot tools and explains safety rules.
---

# DokladBot: prace s ceskym ucetnictvim uzivatele

DokladBot MCP server zpristupnuje ucetnictvi uzivatele (ucet na dokladbot.cz).
Vsechny nastroje pracuji jen s daty prihlaseneho uzivatele.

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
