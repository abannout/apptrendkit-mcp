<p align="center">
  <a href="https://www.apptrendkit.com"><img src="assets/logo.png" alt="AppTrendKit" width="88" height="88"></a>
</p>

<h1 align="center">AppTrendKit MCP server</h1>

<p align="center">
  App Store market data inside ChatGPT, Claude, Cursor and any other MCP client:<br>
  estimated downloads and revenue, top charts by country and category, and ASO keyword difficulty.
</p>

<p align="center">
  <a href="https://www.apptrendkit.com/app-store-mcp-server">Setup guide</a> ·
  <a href="docs/tools.md">Tools</a> ·
  <a href="docs/examples.md">Examples</a> ·
  <a href="https://www.apptrendkit.com">AppTrendKit</a>
</p>

---

```
https://www.apptrendkit.com/mcp
```

A free, hosted, **remote MCP server** (Streamable HTTP). No account, API key or install needed: paste the URL into your assistant and ask.

- "How much does the ChatGPT app make per month?"
- "What are the top grossing iPhone games in Japan right now?"
- "Who are Calm's biggest competitors, and how many downloads do they get?"
- "How hard is it to rank for *habit tracker* on the App Store?"
- "If I sell a $9.99 subscription in Germany in the Small Business Program, what do I keep?"

The assistant picks the right tool, answers with the numbers, and links each app to its [AppTrendKit](https://www.apptrendkit.com) page. In ChatGPT and Claude the results also show as a compact inline list or app card.

## Connect

| Client | How |
|---|---|
| **ChatGPT** | Settings → Apps → Advanced settings → turn on Developer mode → Create app → paste the URL, authentication: **No authentication**. |
| **Claude** (web, desktop, mobile) | Settings → Connectors → Add custom connector → name `AppTrendKit`, URL above. |
| **Claude Code** | `claude mcp add --transport http apptrendkit https://www.apptrendkit.com/mcp` |
| **Cursor** | Settings → MCP → Add new MCP server, or [`examples/cursor-mcp.json`](examples/cursor-mcp.json) in `~/.cursor/mcp.json`. |
| **VS Code** | Command Palette → *MCP: Add Server* → HTTP → the URL, or [`examples/vscode-mcp.json`](examples/vscode-mcp.json) in `.vscode/mcp.json`. |
| **Windsurf, Cline, Zed, Gemini CLI, Codex** | Add a remote (Streamable HTTP) server with the URL. See [`docs/clients.md`](docs/clients.md). |
| **Clients without remote MCP** | Bridge it with `mcp-remote`: [`examples/claude-desktop-mcp-remote.json`](examples/claude-desktop-mcp-remote.json). |

Most clients accept this JSON:

```json
{
  "mcpServers": {
    "apptrendkit": { "url": "https://www.apptrendkit.com/mcp" }
  }
}
```

Step-by-step setup with copy buttons: **[apptrendkit.com/app-store-mcp-server](https://www.apptrendkit.com/app-store-mcp-server)**.

## Tools

Five read-only tools. Nothing is changed, saved or bought. Full input schemas in [`docs/tools.md`](docs/tools.md).

| Tool | What it does |
|---|---|
| `search_apps` | Find apps among AppTrendKit's top 300 by name, publisher or topic, with publisher, category, rating and estimated 30-day downloads and revenue. |
| `get_app_details` | One app: listing, chart ranks, how it makes money, similar apps, estimated downloads and revenue for 7 and 30 days with growth, top countries. |
| `get_top_charts` | Top free, paid and grossing charts for any country and category, AppTrendKit's most downloaded and highest revenue, the fastest climbers and new entries. |
| `check_keyword_difficulty` | How hard a US App Store search is to rank for: difficulty, popularity and opportunity, the reasons, and the top 3 apps. |
| `calculate_app_store_proceeds` | What a developer keeps from a sale after VAT/GST and Apple's 30% or 15% commission, optionally per month. |

Example output:

```text
"habit tracker" on the US App Store: difficulty High, popularity High, opportunity Medium.
The top 10 apps have a median of 13,449 ratings; 8 of 10 put the phrase in their title.
Top apps: #1 Habit Tracker, #2 Habit Tracker - HabitKit, #3 Onrise: Habit Tracker & Focus.
```

More in [`docs/examples.md`](docs/examples.md).

## The data

- **Estimates, not official figures.** Downloads and revenue are AppTrendKit model estimates built from public App Store signals (chart positions, ratings, prices). Revenue is gross consumer spend through Apple, before Apple's commission. [How we estimate](https://www.apptrendkit.com/#how-we-estimate).
- **Coverage.** The MCP server shares what anyone sees on AppTrendKit without an account: estimates for the top 300 apps, store details and chart positions for every charting app, and US keyword difficulty for the keywords AppTrendKit records daily.
- **iPhone first.** Charts cover App Store storefronts worldwide; Google Play has very few tracked apps so far.
- Need more apps, keyword rankings, reviews or history? That's on [apptrendkit.com](https://www.apptrendkit.com).

Free tools on the site that use the same data:
[ASO keyword research tool](https://www.apptrendkit.com/ios-keyword-research-tool) ·
[Keyword difficulty checker](https://www.apptrendkit.com/tools/keyword-difficulty-checker) ·
[App revenue estimator](https://www.apptrendkit.com/app-revenue-estimator) ·
[App Store fee calculator](https://www.apptrendkit.com/tools/app-store-fee-calculator) ·
[Best free ASO tools](https://www.apptrendkit.com/free-aso-tools) ·
[Top grossing apps by month](https://www.apptrendkit.com/top-grossing-apps)

## Privacy

The server only receives the lookup your assistant sends (an app name, a chart, a keyword or a price). It never sees your conversation or your assistant account, and needs no sign-in. Details: [privacy policy](https://www.apptrendkit.com/privacy) · [terms](https://www.apptrendkit.com/terms).

## This repository

The server is hosted by AppTrendKit; its code lives in AppTrendKit's private application and is not published here. This repository holds the public documentation, client configs, the [MCP Registry](https://registry.modelcontextprotocol.io) entry ([`server.json`](server.json)) and the [changelog](CHANGELOG.md).

- Bug, wrong figure or missing app? [Open an issue](../../issues/new/choose) or write to support@apptrendkit.com.
- Security reports: see [SECURITY.md](SECURITY.md).

Docs and examples are MIT licensed ([LICENSE](LICENSE)). The AppTrendKit name, logo and data are not covered by that license.
