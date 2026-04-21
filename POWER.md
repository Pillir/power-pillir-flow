---
name: pillir-flow
description: Build enterprise apps on Pillir Flow through natural language — SAP, Oracle, Salesforce, and REST integrations, spec-driven and deployment-ready.
version: 0.1.0
author: Pillir
keywords:
  - pillir
  - flow
  - pillir flow
  - enterprise app
  - low-code
  - sap integration
  - oracle integration
  - salesforce integration
  - wireframe
  - app generation
steering:
  - pattern: "**/*flow*"
    file: steering/flow-app-generation.md
  - pattern: "**/integration*"
    file: steering/flow-integrations.md
  - pattern: "**/deploy*"
    file: steering/flow-deployment.md
---

# Pillir Flow Power

Guide the Kiro agent to build enterprise-ready applications on Pillir Flow using the Flow MCP server. Flow turns natural-language requirements into deployable web, mobile, and offline-capable apps with native connectors to SAP, Oracle, Salesforce, and REST APIs.

## Onboarding

### Step 1: Verify Flow credentials

Before calling any Flow MCP tools, confirm the user has:

- A Pillir Flow account at `https://flow.pillir.ai`
- A valid **Pillir Flow API key** stored as the `PILLIR_API_KEY` environment variable (or pasted directly into `~/.kiro/settings/mcp.json` under `mcpServers.pillir-flow.headers.X-FLOW-API-KEY`)
- The edition (Explorer, Creator, or Enterprise) that matches what they want to do — integrations and deployment require Creator or Enterprise

If the API key is missing, instruct the user to generate one from their Flow workspace settings and add it to their Kiro MCP configuration.

### Step 2: Install the recommended hook

Add this hook to `.kiro/hooks/review-flow-spec.kiro.hook`:

​```json
{
  "enabled": true,
  "name": "Review Flow Spec",
  "description": "Validate the generated Flow spec against enterprise best practices before deployment",
  "version": "1",
  "when": { "type": "userTriggered" },
  "then": {
    "type": "askAgent",
    "prompt": "Review the current Flow spec for missing requirements, unmapped integrations, and deployment readiness. Flag any gaps before publishing."
  }
}
​```

### Step 3: Confirm the MCP server is reachable

Run a lightweight discovery call against the Flow MCP server to list available tools. If the call fails with a 401 or 403, the API key is missing or invalid. If it fails with a 404 or hangs, the endpoint URL or transport in `mcp.json` is wrong.

## Best practices

- **Start with requirements, not screens.** Ask the user for the business problem first; Flow will generate the wireframes.
- **Prefer native connectors over custom APIs.** If integrating with SAP, Oracle, or Salesforce, use Flow's built-in adapters — no ABAP, no OData.
- **Design for offline first** when the app is field-facing. Flow supports patented offline sync; enable it in the spec.
- **Export test scripts** Flow generates automatically and run them in your QA pipeline before deployment.
- **Use Creator or Enterprise edition** for anything involving system integration, custom workflows, or production deployment.

## Steering map

Route to the right guidance based on what the user is doing:

- Generating or editing a flow → `steering/flow-app-generation.md`
- Connecting to SAP, Oracle, Salesforce, or REST → `steering/flow-integrations.md`
- Preparing for staging or production release → `steering/flow-deployment.md`