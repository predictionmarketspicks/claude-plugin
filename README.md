# PredictionMarketsPicks — Claude plugin

Live Kalshi and Polymarket market data inside Claude (claude.ai, Cowork and Claude Code): NFL player-prop prices by venue, cross-venue price gaps, Kalshi weather and 15-minute crypto and metals boards, perps and liquidation math, Fed rate odds, the 2026 Senate map, NHL, and EV / Kelly / Bayes calculators. **Free, read-only, no API key.** Pro members sign in with their PredictionMarketsPicks account to unlock the model's game and prop edges, the mispricing scanner and the live alerts feed.

- Docs and setup for every host: https://predictionmarketspicks.com/mcp/setup
- The graded record behind every engine: https://predictionmarketspicks.com/track-record

## What's in the plugin

| Component | What it does |
|---|---|
| `.mcp.json` | Connects the hosted MCP server (`https://predictionmarketspicks.com/api/mcp/apps`, Streamable HTTP). Nothing to install, nothing runs locally. |
| `skills/prediction-markets-desk` | Routes any prediction-market question to the right tool and sets the rules for quoting prices (numbers only from tool results, venue labelled, an edge is disagreement not a guarantee). |
| `skills/nfl-props-desk` | The in-season NFL flow: prop board → ladder → combo → win probability → the Pro edge tools. |
| `skills/fifteen-minute-desk` | Kalshi 15-minute markets and perps: windows, targets, settlement sources, liquidation math. |

## Install

**From the Claude Directory**: add the PredictionMarketsPicks plugin.

**Claude Code, from a local clone**:

```
git clone https://github.com/predictionmarketspicks/claude-plugin
claude --plugin-dir ./claude-plugin
```

Or point any MCP host at the server directly — see https://predictionmarketspicks.com/mcp/setup.

## Data and privacy

- Every tool is read-only. Nothing places an order; trade links open the exchange in your browser.
- The server receives the tool call (its arguments) and your client's user-agent, and returns market data. No credentials are read from your machine, and the plugin asks for none.
- Pro is optional and uses OAuth sign-in on the connector (`/api/mcp/connect`); the plugin itself never handles a token.
- Privacy policy: https://predictionmarketspicks.com/privacy · Terms: https://predictionmarketspicks.com/tos · Support: predictionmarketspicks@gmail.com

## Not financial advice

Market data and model reads are informational. An "edge" is where our model disagrees with the market; it is not a guarantee. Trade responsibly.

MIT licensed — see `LICENSE`.
