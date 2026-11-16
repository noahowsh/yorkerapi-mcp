# YorkerAPI MCP server

[![MCP Registry](https://img.shields.io/badge/MCP%20Registry-listed-0b7285?style=flat-square)](https://registry.modelcontextprotocol.io/v0/servers?search=io.github.noahowsh/yorkerapi)

**The cricket data API.** Ball by ball for 23,241 matches in every format, men's and women's, from Tests and ODIs to the IPL, the Big Bash and The Hundred, with players, venues, our own Elo ratings and per-ball win probability. From mid-2020, each sportsbook's match-winner price sits beside the match it belongs to. REST API and MCP server. 500 free credits every month, no card.

Website: https://yorkerapi.com · Docs: https://yorkerapi.com/docs · Get a key: https://yorkerapi.com/signup

```
You:    "How has Jasprit Bumrah bowled at the death in the IPL, season by season?"
Claude: [calls search_players, then get_player_stats with phase=death]
```

## Connect

Most clients connect to `https://mcp.yorkerapi.com/mcp` directly with the header `x-api-key: YOUR_KEY`:

```json
{ "mcpServers": { "yorkerapi": { "type": "http", "url": "https://mcp.yorkerapi.com/mcp", "headers": { "x-api-key": "YOUR_KEY" } } } }
```

The key can also be sent as `Authorization: Bearer`, or as `?key=` on the URL for clients that cannot send headers. Connecting and listing tools works without a key; calling a tool needs one.

For a client that launches a local process instead:

```bash
git clone https://github.com/noahowsh/yorkerapi-mcp.git && cd yorkerapi-mcp && npm install
YORKERAPI_API_KEY=your_key node index.js
```

It forwards to the hosted server with your key, so every tool and credit cost is the same.

## Use it in

- **Claude, ChatGPT, Cursor, VS Code, Gemini CLI, Grok, Perplexity, Le Chat:** add `https://mcp.yorkerapi.com/mcp` as a remote MCP server. Step-by-step for each: https://yorkerapi.com/mcp
- **Gemini CLI:** `gemini extensions install https://github.com/noahowsh/yorkerapi-mcp`
- **Cursor:** the [SportsDataHQ plugins for Cursor](https://github.com/noahowsh/sportsdatahq-cursor-plugins)
- **Google Sheets:** `=SDHQ("yorkerapi","list_competitions")` fills a live table: https://sportsdatahq.com/sheets
- **REST:** `POST https://mcp.yorkerapi.com/v1/<tool>` with an `x-api-key` header: https://yorkerapi.com/docs

## Tools (18)

| Tool | What it returns |
|------|-----------------|
| `list_competitions` | Every competition we hold with its key, format, match count and seasons |
| `list_teams` | Team ids for international sides and franchises, men's and women's |
| `search_players` | Find a player's id by name, or list a team's players |
| `get_schedule` | Upcoming and live matches in every competition, with both sides' ratings |
| `get_matches` | Results by competition, season, team, venue or date, with scores and margins |
| `get_ratings` | Our Elo ratings by format, best first |
| `get_match` | One match in full: batting and bowling cards, ratings and every book's opening and closing price |
| `get_player` | A career by format: runs, average, strike rate, wickets, economy, hundreds, best figures |
| `get_player_stats` | A player split by season, competition, phase (powerplay, middle, death) or format |
| `get_player_matches` | A player's matches with batting and bowling in each innings |
| `get_matchup` | A batter against a bowler: balls, runs, strike rate, dots and every dismissal |
| `get_leaders` | Leaders in runs, average, strike rate, sixes, wickets, economy |
| `get_venue` | How a ground plays: par totals, batting first against chasing, toss effect |
| `get_odds` | Match-winner prices by sportsbook, opening and closing, from mid-2020 |
| `get_deliveries` | Ball-by-ball rows for a match, a batter or a bowler, with our win probability |
| `get_win_probability` | A match's win-probability worm over by over, and the balls that swung it |
| `get_market_vs_model` | In-play prices beside our win probability, lined up to the exact ball |
| `get_line_movement` | Every pregame snapshot by book, the market line over time, and in-play prices |

Competitions are filters on one dataset: Tests, ODIs and T20Is, the IPL, Big Bash, PSL, CPL, T20 Blast, The Hundred, SA20, ILT20, county cricket, the WBBL, WPL and more (`list_competitions`).

## Coverage

- Ball by ball for 23,241 matches since December 2001 in every format, men's and women's
- Batting and bowling cards, careers by format, splits by season, competition and phase (powerplay, middle, death), batter against bowler
- Our Elo ratings by format and our per-ball win probability for limited-overs matches
- Sportsbook match-winner prices from mid-2020, opening and closing by book, with in-play prices kept apart from pregame lines

## Pricing

500 free credits every month, no card. Plans: Starter $19/mo (10,000 credits), Pro $49/mo (30,000), Scale $149/mo (125,000). Wallet top-ups from $5, never expire. https://yorkerapi.com/pricing

## Data credits

Ball-by-ball cricket data from Cricsheet (cricsheet.org), licensed under the Open Data Commons Attribution License (ODC-BY), combined with our own models.

Ratings and win probabilities are ours. Not affiliated with the ICC or any league, board or team.
