# Pillir Flow Power for Kiro

Build enterprise apps on [Pillir Flow](https://flow.pillir.ai) directly from the Kiro IDE. This Power connects Kiro agents to the Flow MCP server so you can generate, integrate, and deploy production-ready apps through natural language.

## What this Power does

- Turns business requirements into flows, wireframes, and data models via Flow
- Connects to SAP, Oracle, Salesforce, and REST backends using Flow's native adapters
- Generates test scripts and deploys to web, mobile, offline, and rugged-device targets
- Keeps your Kiro context focused — steering files load on-demand per workflow

## Installation

1. Open Kiro IDE.
2. Go to the Powers panel and click **Add power from GitHub**.
3. Paste this repo's URL: `https://github.com/pillir/power-pillir-flow`
4. When prompted, provide your Pillir Flow API token. It will be stored in `~/.kiro/settings/mcp.json` under the Powers section.
5. Click **Try the power** to run the onboarding flow.

## Activation

The Power activates automatically when you mention any of these keywords in Kiro chat: `pillir`, `flow`, `pillir flow`, `enterprise app`, `low-code`, `sap integration`, `oracle integration`, `salesforce integration`, `wireframe`, `app generation`.

## Requirements

- A Pillir Flow account (Explorer, Creator, or Enterprise edition)
- Kiro IDE 1.0 or later
- A valid Flow API token

## License

MIT. See `LICENSE` for details.