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
`https://dokladbot.cz/api/mcp` over HTTPS with OAuth 2.1. You sign in on
dokladbot.cz with your DokladBot account and confirm "Povolit pristup"
(Allow access). No API keys or passwords are copied anywhere. You need a
DokladBot account ([7-day free trial](https://dokladbot.cz/registrace), all
features, up to 100 receipts and invoices).

Install in Claude Code:

```
/plugin marketplace add OndrejKnedla/dokladbot-claude-plugin
/plugin install dokladbot@dokladbot
```

## Connect your account

Installing the plugin does not sign you in. Until your DokladBot account is
connected, the tools are not available and Claude shows you these steps
instead of answering from guesses.

In Claude Code:

1. Run `/mcp`.
2. Select the `dokladbot` server (marked as coming from a plugin) and press
   Enter.
3. Choose `Authenticate`. Your browser opens the DokladBot sign-in page.
4. Sign in with your DokladBot account and confirm "Povolit pristup"
   (Allow access).

If the browser does not open, copy the URL shown in the terminal and open it
manually. Back in Claude Code the server is connected; ask your question
again.

In the Claude app (web, desktop) and Cowork:

1. Open Customize > Connectors (https://claude.ai/customize/connectors).
2. Click Connect next to DokladBot.
3. Sign in with your DokladBot account and confirm "Povolit pristup"
   (Allow access). The connector then shows Connected.
4. In a chat, check that the connector is on: the + button in the message
   box, then Connectors.

If DokladBot is not in the list, open Customize > Plugins, select the
DokladBot plugin and its Connectors tab, then add and connect the connector
there. On Team and Enterprise plans an Owner adds the connector for the
organization first.

No DokladBot account yet? Sign up at https://dokladbot.cz/registrace (7 days
free, all features, up to 100 receipts and invoices), then come back and
connect.

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
`https://dokladbot.cz/api/mcp` (HTTPS, OAuth 2.1). Prihlasujete se na
dokladbot.cz svym uctem a potvrdite Povolit pristup. Zadne API klice ani
hesla se nikam nekopiruji. Potrebujete ucet DokladBot:
[registrace](https://dokladbot.cz/registrace), 7 dni zdarma, vsechny funkce,
az 100 uctenek a faktur.

Pripojeni uctu: instalace pluginu vas sama neprihlasi. Dokud ucet
nepripojite, nastroje nejsou k dispozici a Claude vam misto odhadu ukaze
tento postup.

V Claude Code:

1. Napiste prikaz `/mcp`.
2. Vyberte server `dokladbot` (je oznaceny jako server z pluginu) a potvrdte
   klavesou Enter.
3. Zvolte `Authenticate`. Otevre se prohlizec s prihlasenim na dokladbot.cz.
4. Prihlaste se svym uctem DokladBot a potvrdte Povolit pristup.

Kdyz se prohlizec neotevre, zkopirujte adresu zobrazenou v terminalu a
otevrete ji rucne. Po navratu do Claude Code je server pripojeny a dotaz
staci zopakovat.

V aplikaci Claude (web, desktop) a v Cowork (nazvy polozek jsou z anglickeho
rozhrani):

1. Otevrete Customize > Connectors (https://claude.ai/customize/connectors).
2. U konektoru DokladBot kliknete na Connect.
3. Prihlaste se svym uctem DokladBot a potvrdte Povolit pristup. Konektor
   pak ma stav Connected.
4. V konverzaci overte, ze je konektor zapnuty: tlacitko + u pole pro
   zpravu, polozka Connectors.

Kdyz konektor DokladBot v seznamu neni, otevrete Customize > Plugins, plugin
DokladBot a zalozku Connectors; tam konektor pridejte a pripojte. V tymovem
nebo firemnim tarifu Claude musi konektor nejdriv pridat vlastnik
organizace.

Ucet DokladBot jeste nemate? Zaregistrujte se na
https://dokladbot.cz/registrace (7 dni zdarma, vsechny funkce, az 100
uctenek a faktur), pak se vratte a ucet pripojte.

Co plugin umi: doklady a faktury (vypisy, hledani, detail vcetne rozpisu
DPH), faktury po splatnosti, podklady DPH za mesic nebo ctvrtleti, danove
terminy, prehled hospodareni a bankovni transakce, datova schranka (jen
obalky prijatych pisemnosti), navrh faktury jednou vetou (ceka na schvaleni
v dashboardu) a nahrani uctenky ke zpracovani.

Bezpecnost: plugin nikdy neplati a neposila faktury odberatelum. Nastroje
s nasledky (presun dokladu do kose, zamitnuti dokladu, podani priznani k DPH)
jsou oznacene jako destruktivni a Claude si pred kazdym volanim vyzada vas
souhlas; doklad presunuty do kose jde obnovit. Priznani k DPH lze podat az po
kontrole clovekem v dashboardu DokladBot. Obsah datove schranky se cte vyhradne v dashboardu (otevreni
zpravy se pravne pocita jako doruceni) a pristup kdykoli zrusite v Nastaveni,
sekce API klice. Ceny: soucast predplatneho DokladBot, dotazy cerpaji kredity
tarifu, kompletni cenik na https://dokladbot.cz/cenik. Ochrana osobnich udaju:
https://dokladbot.cz/ochrana-osobnich-udaju (sekce 10), podminky:
https://dokladbot.cz/obchodni-podminky. Podpora: podpora@dokladbot.cz.
