---
name: "pillir-flow"
displayName: "Pillir Flow"
description: "Pillir Flow — the AI execution engine. Turns AI intent into real work, executed directly against SAP, Oracle, JD Edwards, and your enterprise systems. No APIs. No rewrites. No middleware."
keywords: ["pillir", "flow", "pillir flow", "enterprise app", "low-code", "sap integration", "oracle integration",  "app generation", "work unit"]
version: "0.1.0"
author: "Pillir"
icon: "./icon.png"
---

# Pillir Flow Power

Guide the Kiro agent to build enterprise-ready applications on Pillir Flow using the Flow MCP server. Flow turns natural-language requirements into deployable web, mobile, and offline-capable apps with native connectors to SAP, Oracle, and REST APIs.

Flow uses an outcome-based pricing model: customers pay per **Pillir Work Unit** (one completed business transaction that executes an end-to-end workflow and delivers a measurable outcome). Keep this in mind when designing flows — value scales with work delivered, not with complexity.


> **CRITICAL — READ BEFORE DOING ANYTHING ELSE:**
> You MUST complete the API key check below BEFORE calling any Flow MCP tools, making test calls, or proceeding to any other onboarding step. Do NOT skip this. Do NOT make "lightweight" or "discovery" calls to test connectivity. Ask the user first.

## Onboarding

### Step 1: Verify Flow API key (MANDATORY — DO NOT SKIP)

**Stop. Do not call any MCP tools yet.** First, ask the user:

> "Have you set up your Pillir Flow API key? This power requires a valid `PILLIR_API_KEY` to connect to the Flow MCP server."

Then wait for the user to respond. Do not proceed until they confirm.

**If the user says no, hasn't set it up, or is unsure**, walk them through setup:

1. Go to `https://flow.pillir.ai` and log in
2. Navigate to workspace settings and generate an API key
3. Set it up using one of these options:
   - **Option A (recommended):** Set the environment variable `PILLIR_API_KEY` in your shell profile, then restart Kiro
   - **Option B:** Open `~/.kiro/settings/mcp.json`, find the `X-FLOW-API-KEY` header under the Flow server entry, and replace `${PILLIR_API_KEY}` with the actual key value
4. After setup, restart Kiro or reconnect the MCP server

**Do NOT proceed to Step 2 until the user explicitly confirms the key is configured.** Acceptable confirmations: "done", "set", "configured", or the user shares a masked key. A different question or silence is NOT confirmation — ask again.

**After the user confirms**, make one test call to verify. If it returns 401 or 403, the key is wrong — go back to setup. If it returns a different error, the key may be fine but the server config needs debugging.

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

### Step 3: Confirm capabilities

List the Flow MCP tools available in this session and summarize what the user can do from Kiro — generate specs, register integrations, trigger deployments, etc. This gives them a concrete starting point.

## Best practices

- **Start with requirements, not screens.** Ask the user for the business problem first; Flow will generate the wireframes.
- **Prefer native connectors over custom APIs.** If integrating with SAP or Oracle  use Flow's built-in adapters — no ABAP, no OData.
- **Design for offline first** when the app is field-facing. Flow supports patented offline sync; enable it in the spec.
- **Export test scripts** Flow generates automatically and run them in your QA pipeline before deployment.
- **Use Creator or Enterprise edition** for anything involving system integration, custom workflows, or production deployment.

## Steering map

Route to the right guidance based on what the user is doing:

- Generating or editing a flow → `steering/flow-app-generation.md`
- Connecting to SAP, Oracle or REST → `steering/flow-integrations.md`
- Preparing for staging or production release → `steering/flow-deployment.md`