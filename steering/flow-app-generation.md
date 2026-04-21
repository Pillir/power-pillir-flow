# Flow App Generation Workflow

When the user wants to build a new app on Pillir Flow:

1. **Gather requirements in plain language.** Ask what the business problem is, who the users are, and what devices they'll use (web, mobile, rugged scanner).
2. **Call the Flow MCP tool to generate a spec.** Flow produces flows, wireframes, data models, and test scripts from the requirements.
3. **Review the generated spec with the user.** Flag missing roles, unclear approval steps, or data-model gaps before proceeding.
4. **Iterate on the spec, not the code.** Flow regenerates the app from the spec — changing code directly defeats the round-trip.
5. **Preview the app** in Flow's test environment (Explorer Edition) or deploy to Pillir cloud (Creator Edition) or the user's own cloud (Enterprise Edition).

Key constraints:

- Explorer Edition is single-user and can't do system integrations — escalate to Creator/Enterprise if the user needs SAP, Oracle, Salesforce, or REST connections.
- Offline capability must be declared in the spec; it can't be added post-generation without regeneration.