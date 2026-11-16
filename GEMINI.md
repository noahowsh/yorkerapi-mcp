# YorkerAPI for Gemini CLI

This extension connects Gemini CLI to the YorkerAPI MCP server at https://mcp.yorkerapi.com/mcp.
YorkerAPI is a sports data API for cricket: ball by ball in every format, men's and women's,
plus fixtures, results, players, ratings and match-winner prices.

## Setup

1. Get a free key at https://yorkerapi.com/signup. The free tier includes 500 credits per month.
2. Set the key as an environment variable before you start Gemini CLI:

   export YORKERAPI_API_KEY=your_key

3. Restart Gemini CLI. The extension sends the key in the x-api-key header.

Connecting and listing tools works without a key. Calling a tool needs one.

## How to use it

- Ask for cricket data in plain language. Gemini picks the matching MCP tool.
- Each tool call uses credits from your monthly allowance.
- If a call fails with an auth error, check that YORKERAPI_API_KEY is set in the shell that launched Gemini CLI.
- Docs: https://yorkerapi.com/docs
