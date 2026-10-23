# Tools

All five tools are read-only (`readOnlyHint: true`), need no authentication, and return both a text answer and `structuredContent` for the inline view. Schemas below are what `tools/list` returns from `https://www.apptrendkit.com/mcp`.

| Tool | Title |
|---|---|
| [`search_apps`](#search_apps) | Search apps |
| [`get_app_details`](#get_app_details) | Get app details |
| [`get_top_charts`](#get_top_charts) | Get top charts |
| [`check_keyword_difficulty`](#check_keyword_difficulty) | Check keyword difficulty |
| [`calculate_app_store_proceeds`](#calculate_app_store_proceeds) | Calculate App Store proceeds |

## search_apps

Find iPhone and iPad apps among AppTrendKit's top 300 by name, publisher or a word in the name or category (for example "Duolingo", "photo editor", "Google"). Returns up to 20 apps with publisher, category, rating, estimated downloads and revenue for the last 30 days, and a link to each app's AppTrendKit page. Apps outside the top 300 are not returned. Use it to identify an app before get_app_details, or to list competitors in a niche. It does not search App Store reviews or keywords.

| Input | Type | Required | Default | Description |
|---|---|---|---|---|
| `query` | string | yes |  | App name, publisher or topic to search for. (max 120 chars) |
| `platform` | string (`ios`, `android`, `all`) | no | `"all"` | Store: 'ios' (Apple App Store), 'android' (Google Play, very few apps tracked) or 'all'. |
| `limit` | integer | no | `10` | How many apps to return (1-20). (min 1, max 20) |

## get_app_details

Look up one of AppTrendKit's top 300 apps: listing (subtitle, publisher, category, price, rating), current App Store chart ranks, how it makes money, similar apps, estimated downloads and revenue for the last 7 and 30 days with growth, and the top countries. Pass an App Store id ("284882215"), a Google Play package ("com.spotify.music"), or an App Store / Google Play / AppTrendKit URL. Use search_apps first when you only know the app's name.

| Input | Type | Required | Default | Description |
|---|---|---|---|---|
| `app` | string | yes |  | App Store id, Google Play package name, or a store/AppTrendKit URL for the app. (max 400 chars) |
| `platform` | string (`ios`, `android`, `auto`) | no | `"auto"` | Store of the app; 'auto' works it out from the id or URL. |

## get_top_charts

List the apps at the top of an App Store chart for a country and category: top free, top paid, top grossing, AppTrendKit's most downloaded or highest revenue, or the apps rising fastest and new entries. Returns up to 50 apps with chart position, publisher and rating. Apps in AppTrendKit's top 300 also have estimated 30-day downloads and revenue and a link to their AppTrendKit page; other entries show only their position. Use it for questions like "top grossing games in Germany" or "which productivity apps are climbing the charts".

| Input | Type | Required | Default | Description |
|---|---|---|---|---|
| `chart` | string (`top-free`, `top-paid`, `top-grossing`, `most-downloaded`, `highest-revenue`, `rising-free`, `rising-grossing`, `new-entries`) | no | `"top-grossing"` | Which chart: Apple's top-free/top-paid/top-grossing, AppTrendKit's most-downloaded/highest-revenue estimates, rising-free/rising-grossing (biggest climbers) or new-entries. |
| `country` | string | no | `"US"` | Two-letter storefront code, e.g. 'US', 'GB', 'DE', 'JP'. |
| `category` | string | no | `"all"` | App Store category name or slug such as 'games', 'productivity', 'Health & Fitness', 'photo-video', 'finance', 'education', or 'all'. (max 80 chars) |
| `platform` | string (`ios`, `android`, `all`) | no | `"all"` | Store: 'ios' (Apple App Store), 'android' (Google Play, very few apps tracked) or 'all'. |
| `limit` | integer | no | `20` | How many apps to return (1-50). (min 1, max 50) |

## check_keyword_difficulty

Check how hard it is to rank for a search term on the US App Store (App Store Optimization). Returns difficulty, popularity and opportunity as High/Medium/Low, the reasons (how many ratings the top apps have, how many put the phrase in their title, whether it's a brand search) and the top 3 apps. Only covers keywords AppTrendKit records daily in the US store; for unknown phrases it suggests similar recorded ones.

| Input | Type | Required | Default | Description |
|---|---|---|---|---|
| `keyword` | string | yes |  | The App Store search phrase, e.g. 'habit tracker' or 'pdf scanner'. (max 60 chars) |

## calculate_app_store_proceeds

Work out what a developer keeps from one App Store sale or subscription payment after VAT/GST and Apple's commission: 30% standard, 15% in the Small Business Program, 15% for subscriptions after a subscriber's first year. Optionally multiply by a number of sales per month. Pure arithmetic on Apple's standard terms; EU alternative terms and web-purchase links are not modelled.

| Input | Type | Required | Default | Description |
|---|---|---|---|---|
| `price` | number | yes |  | Customer price of one sale or payment, in the storefront's currency. (min 0, max 100000) |
| `plan` | string (`standard`, `small_business`, `subscription_year_two`) | no | `"standard"` | 'standard' (30%), 'small_business' (15%) or 'subscription_year_two' (15%). |
| `vat_percent` | number | no | `0` | VAT/GST included in the price, in percent (0 for US prices, where tax is added on top; e.g. 19 for Germany, 20 for the UK). (min 0, max 50) |
| `sales_per_month` | integer | no |  | Optional number of sales or payments per month to total. (min 0, max 1000000000) |
