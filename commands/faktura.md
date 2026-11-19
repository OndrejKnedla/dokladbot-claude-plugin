---
description: Pripravit navrh faktury v DokladBotu (ceka na schvaleni v dashboardu)
argument-hint: komu a za co, napr. "Novak s.r.o., 15000 Kc, konzultace"
---

Nejdriv over pripojeni: kdyz nastroje DokladBot nejsou dostupne nebo vyzaduji
prihlaseni, nevolej nic dalsiho, nic neodhaduj a ukaz uzivateli postup
pripojeni uctu podle skillu dokladbot (sekce "Kdyz ucet jeste neni
pripojeny").

Pomoci nastroje create_invoice_draft z DokladBot MCP serveru priprav navrh
faktury podle zadani uzivatele: $ARGUMENTS

Postup:
1. Pokud chybi odberatel, castka nebo popis plneni, doptej se.
2. Pokud si nejsi jisty odberatelem, nejdriv ho vyhledej nastrojem
   list_suppliers nebo search, at pouzijes spravne IC/DIC.
3. Vytvor navrh a uzivateli zduraznis, ze faktura NENI odeslana - ceka na
   jeho schvaleni v dashboardu DokladBot (dokladbot.cz/doklady).
4. Nikdy netvrd, ze faktura byla odeslana odberateli.
