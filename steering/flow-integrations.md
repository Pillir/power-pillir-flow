# Flow Integrations Workflow

Pillir Flow has native adapters for enterprise systems. Use them instead of writing custom integration code.

Supported native integrations:

- **SAP** — direct adapter, no ABAP or OData development needed
- **Oracle** — direct adapter for Oracle databases and ERP
- **Microsoft systems** — Dynamics, SharePoint, etc.
- **REST APIs** — generic adapter for any RESTful service

Workflow:

1. Ask the user which backend(s) the app needs to talk to.
2. Use the Flow MCP integration tool to register the connection — the user provides credentials in Flow, not in Kiro.
3. Map Flow data models to backend entities through the Flow UI or via MCP calls.
4. Test the integration in Flow's test environment before deploying.

If the user asks about a system not in the list above, check whether a REST API exists; if yes, use the REST adapter. Never suggest custom code as a first resort.