<img src="./icon.png" alt="Pillir Flow" width="96" height="96" align="right" />

# Pillir Flow Power for Kiro

Kiro Power for Pillir Flow — build enterprise apps on SAP, Oracle, through natural language in the Kiro IDE.

This Power connects Kiro agents to the [Pillir Flow](https://flow.pillir.ai) so you can generate, integrate, and deploy production-ready apps end-to-end.

## What this Power does

- Harvesting your Legacy via Flow
- Connects to SAP, Oracle and REST backends using Flow's native adapters
- Generates test scripts and deploys to web, mobile, offline, and rugged-device targets
- Keeps your Kiro context focused — steering files load on-demand per workflow

## Installation

1. Open Kiro IDE.
2. Go to the Powers panel and click **Add power from GitHub**.
3. Paste this repo's URL: `https://github.com/pillir/power-pillir-flow`
4. When prompted, provide your Pillir Flow API key. Set it as the `PILLIR_API_KEY` environment variable, or paste it directly into `~/.kiro/settings/mcp.json` under `mcpServers.pillir-flow.headers.X-FLOW-API-KEY`.
5. Click **Try the power** to run the onboarding flow.

## Activation

The Power activates automatically when you mention any of these keywords in Kiro chat: `pillir`, `flow`, `pillir flow`, `enterprise app`, `low-code`, `sap integration`, `oracle integration`, `wireframe`, `app generation`, `work unit`.

## Requirements

- A Pillir Flow account
- Kiro IDE 1.0 or later
- A valid Pillir Flow API key

## Pricing

Pillir Flow uses an outcome-based pricing model called the **Pillir Work Unit**. You pay for completed business transactions that execute end-to-end workflows and deliver measurable outcomes — not for licenses, API calls, tokens, or developer seats. Value scales with the work delivered; complexity doesn't drive cost.

The lifecycle covered by a Work Unit: **Discover → Build → Run → Execute → Act**.

This Power itself is free and MIT-licensed (see below). Use of Pillir Flow's MCP server consumes Work Units against your Pillir Flow account. See [pillir.ai](https://pillir.ai) for current Work Unit pricing and edition details.

## License

This Power (the `POWER.md`, `mcp.json`, steering files, and accompanying docs) is MIT-licensed. See `LICENSE` for details.

Pillir Flow is a commercial service governed by Pillir's Terms of Service and the Pillir Work Unit pricing model.