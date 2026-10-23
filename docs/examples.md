# Examples

Real answers from the server on 24 October 2026 (text part of the tool result; links shortened). Figures change daily.

## "What are the top grossing iPhone apps in the US right now?"

`get_top_charts` with `{"chart": "top-grossing", "country": "US", "limit": 5}`:

```text
top-grossing — US (as of 2026-10-23):

1. ChatGPT — OpenAI OpCo, LLC · Productivity · ★4.8 (11,564,299) — 3.2M downloads/30d, $66M revenue/30d
2. YouTube — Google LLC · Photo & Video · ★4.7 (49,548,861) — 790K downloads/30d, $50M revenue/30d
3. TikTok - Videos, Shop & LIVE — TIKTOK PTE. LTD. · Entertainment · ★4.7 (18,404,584) — 1.1M downloads/30d, $64M revenue/30d
4. Snapchat — Snap, Inc. · Photo & Video · ★4.5 (5,997,402) — 520K downloads/30d, $31M revenue/30d
5. Peacock TV: Stream TV & Movies — Peacock TV LLC · Entertainment · ★4.7 (3,734,493) — no public AppTrendKit data

Full chart: https://www.apptrendkit.com/charts/us/top-grossing
Downloads and revenue are AppTrendKit model estimates from public App Store signals (gross consumer spend, last 30 days), not official figures.
```

## "How hard is it to rank for *habit tracker* on the App Store?"

`check_keyword_difficulty` with `{"keyword": "habit tracker"}`:

```text
"habit tracker" on the US App Store: difficulty High, popularity High, opportunity Medium.
The top 10 apps have a median of 13,449 ratings; 8 of 10 put the phrase in their title.
Top apps: #1 Habit Tracker, #2 Habit Tracker - HabitKit, #3 Onrise: Habit Tracker & Focus.
Check it on AppTrendKit: https://www.apptrendkit.com/tools/keyword-difficulty-checker?q=habit%20tracker
```

More keywords, with popularity and the full top 10: [free ASO keyword research tool](https://www.apptrendkit.com/ios-keyword-research-tool).

## "I sell a $9.99 subscription in Germany in the Small Business Program to 1,000 people a month. What do I keep?"

`calculate_app_store_proceeds` with `{"price": 9.99, "plan": "small_business", "vat_percent": 19, "sales_per_month": 1000}`:

```text
Small Business Program (15%): a 9.99 sale (incl. 19% VAT = 1.60) pays Apple 1.26 and leaves 7.14 in proceeds (71.4% of the price).
At 1,000 sales a month: 9,990 spent, 1,260 commission, 7,140 proceeds.
Calculator: https://www.apptrendkit.com/tools/app-store-fee-calculator
```

## More prompts to try

- How much revenue does the Duolingo app make per month?
- Find meditation apps and compare their downloads.
- What are the top free iPhone games in Germany?
- Which productivity apps are climbing the US charts this week?
- What are the new entries on the Japanese top grossing chart?
- Which countries does Spotify earn the most in?

## Calling it directly

The server speaks MCP over Streamable HTTP, so any MCP client library works. A raw JSON-RPC call, for testing:

```bash
curl -s https://www.apptrendkit.com/mcp \
  -H "content-type: application/json" \
  -H "accept: application/json, text/event-stream" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"check_keyword_difficulty","arguments":{"keyword":"pdf scanner"}}}'
```

Or explore it with the [MCP Inspector](https://github.com/modelcontextprotocol/inspector):

```bash
npx @modelcontextprotocol/inspector
```

Choose transport *Streamable HTTP* and the URL `https://www.apptrendkit.com/mcp`.
