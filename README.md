# DokladBot plugin for Claude

Czech accounting inside Claude: invoices, receipts, VAT summaries, tax
deadlines, bank transactions and data box overview from your
[DokladBot](https://dokladbot.cz) account. Works in Claude.ai chat, Cowork
and Claude Code.

Ceske ucetnictvi primo v Claude: faktury, uctenky, DPH, danove terminy,
banka a datova schranka z vaseho uctu DokladBot. Ceska verze je nize.

## What the plugin does

- Documents and invoices: list, search and inspect receipts and invoices,
  including VAT breakdowns
- Overdue invoices: who owes you and for how long
- VAT summaries for any month or quarter
- Czech tax deadlines: VAT, income tax and social and health insurance advances
- Income and spending overview, bank transactions, supplier list
- Data box (datova schranka): envelopes of received messages only
- Invoice draft from one sentence (waits for your approval in the dashboard)
- Receipt upload for processing

## How it works

The plugin connects to the remote DokladBot MCP server at
`https://dokladbot.cz/api/mcp` over HTTPS with OAuth 2.1. On first use Claude
opens the DokladBot sign-in page; sign in with your DokladBot account and
confirm "Povolit pristup" (Allow access). No API keys or passwords are copied
anywhere. You need a DokladBot account
([free trial](https://dokladbot.cz/registrace)).

Install in Claude Code:

```
/plugin marketplace add OndrejKnedla/dokladbot-claude-plugin
/plugin install dokladbot@dokladbot
```

## Commands

- `/dokladbot:faktura Novak s.r.o., 15000 Kc, konzultace`: invoice draft
- `/dokladbot:dph Q3 2026`: VAT summary for a period
- `/dokladbot:terminy`: upcoming tax deadlines
- `/dokladbot:splatnosti`: overdue invoices

## Safety

The plugin is designed so that the assistant cannot do anything irreversible
behind your back:

- It never makes payments and never sends invoices to customers. An invoice
  draft waits for your approval in the DokladBot dashboard.
- Tools with consequences (moving a document to the recycle bin, rejecting
  documents, filing a VAT return) are annotated as destructive, so Claude asks
  you to approve each call. Deleted documents go to the recycle bin and can be
  restored.
- A VAT return can be filed with the tax office only after a person has
  reviewed it in the DokladBot dashboard. Without explicit confirmation the
  tool only shows a preview.
- Data box: envelopes only. Opening a message counts as legal delivery under
  Czech law, so message content is read exclusively in the dashboard.
- Access is scoped to your account and can be revoked anytime in Settings,
  API keys.

## Pricing

The connection is part of the DokladBot subscription. Queries use plan credits
(a regular query 1 credit, an invoice draft 3 credits, credit balance free).
Full price list: https://dokladbot.cz/cenik

## Privacy policy

Data collection and processing, including AI connectors, are described in
our [privacy policy](https://dokladbot.cz/ochrana-osobnich-udaju)
(section 10 covers AI assistant connections). Terms of service:
https://dokladbot.cz/obchodni-podminky. The plugin connects only to
first-party DokladBot APIs (dokladbot.cz) over HTTPS with OAuth 2.1; no data
is shared with third parties beyond what the privacy policy states.

## Support

- E-mail: podpora@dokladbot.cz
- Web: https://dokladbot.cz/funkce/ai-asistent
- Security reports: podpora@dokladbot.cz (subject SECURITY)

## Cesky

Plugin propoji Claude s vasim uctem DokladBot pres vzdaleny MCP server
`https://dokladbot.cz/api/mcp` (HTTPS, OAuth 2.1). Pri prvnim pouziti se
otevre prihlaseni na dokladbot.cz, prihlaste se svym uctem a potvrdte
Povolit pristup. Zadne API klice ani hesla se nikam nekopiruji.
Potrebujete ucet DokladBot: [registrace zdarma](https://dokladbot.cz/registrace).

Co plugin umi: doklady a faktury (vypisy, hledani, detail vcetne rozpisu
DPH), faktury po splatnosti, podklady DPH za mesic nebo ctvrtleti, danove
terminy, prehled hospodareni a bankovni transakce, datova schranka (jen
obalky prijatych pisemnosti), navrh faktury jednou vetou (ceka na schvaleni
v dashboardu) a nahrani uctenky ke zpracovani.

Bezpecnost: plugin nic neodesila ani nemaze, danova podani se nikam
neposilaji, obsah datove schranky se cte vyhradne v dashboardu (otevreni
zpravy se pravne pocita jako doruceni) a pristup kdykoli zrusite v Nastaveni,
sekce API klice. Ceny: soucast predplatneho DokladBot, dotazy cerpaji kredity
tarifu, kompletni cenik na https://dokladbot.cz/cenik. Ochrana osobnich udaju:
https://dokladbot.cz/ochrana-osobnich-udaju (sekce 10), podminky:
https://dokladbot.cz/obchodni-podminky. Podpora: podpora@dokladbot.cz.
