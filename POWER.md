---
name: "pillir-flow"
displayName: "Pillir Flow"
description: "Build enterprise apps on Pillir Flow through natural language - SAP, Oracle, Salesforce, and REST integrations, spec-driven and deployment-ready."
keywords: ["pillir", "flow", "pillir flow", "enterprise app", "low-code", "sap integration", "oracle integration", "salesforce integration", "wireframe", "app generation"]
author: "Pillir"
---

# Pillir Flow Power

Guide the Kiro agent to build enterprise-ready applications on Pillir Flow using the Flow MCP server. Flow turns natural-language requirements into deployable web, mobile, and offline-capable apps with native connectors to SAP, Oracle, Salesforce, and REST APIs.

## Onboarding

### Step 1: Verify Flow credentials (BLOCKING)

Before proceeding to any other step, check that the user has a valid API key configured.

1. Check `mcp.json` for the `X-FLOW-API-KEY` header value.
2. If it references an environment variable (e.g., `${PILLIR_API_KEY}`), ask the user whether they have set that variable.
3. **If the key is missing or the user hasn't set it up, STOP here.** Walk them through:
   - Generating a key from their Flow workspace at `https://flow.pillir.ai`
   - Either setting `PILLIR_API_KEY` as an environment variable, or pasting the key directly into `~/.kiro/settings/mcp.json`
   - Restarting Kiro to pick up the change
4. Do NOT proceed to Step 2 or Step 3 until the user confirms the key is in place. Acceptable confirmation: the user says "done", "set", "configured", shares a masked key, or explicitly tells you to continue. A different question or silence is NOT confirmation — re-ask.
5. Once confirmed, verify by making a minimal MCP discovery call (list available Flow tools). Interpret the response:
   - **200 with a tool list** → key is valid, proceed to Step 2
   - **401 or 403** → key is wrong or expired. Return to step 3; do not proceed
   - **404 or connection hangs** → the key may be fine, but the endpoint URL or `transport` in `mcp.json` is wrong. Flag this separately and diagnose before continuing

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
- **Prefer native connectors over custom APIs.** If integrating with SAP, Oracle, or Salesforce, use Flow's built-in adapters — no ABAP, no OData.
- **Design for offline first** when the app is field-facing. Flow supports patented offline sync; enable it in the spec.
- **Export test scripts** Flow generates automatically and run them in your QA pipeline before deployment.
- **Use Creator or Enterprise edition** for anything involving system integration, custom workflows, or production deployment.

## Steering map

Route to the right guidance based on what the user is doing:

- Generating or editing a flow → `steering/flow-app-generation.md`
- Connecting to SAP, Oracle, Salesforce, or REST → `steering/flow-integrations.md`
- Preparing for staging or production release → `steering/flow-deployment.md`