# Flow Deployment Workflow

Flow deploys apps to multiple targets from a single spec:

- Web app
- Mobile app (iOS and Android)
- Offline-capable field interface
- Rugged-device interface (Zebra scanners, etc.)
- Workflow / barcode-scanner UI

Deployment checklist:

1. Confirm the spec is complete — all roles, approvals, and integrations defined.
2. Run the generated test scripts in the user's QA pipeline.
3. Choose the deployment target based on edition:
   - Explorer Edition → Pillir test environment only
   - Creator Edition → Pillir public cloud
   - Enterprise Edition → user's own cloud (AWS, Azure, GCP, on-prem)
4. Use the Flow MCP deployment tool to trigger the release.
5. Monitor rollout and confirm the app is reachable at the target URL.

Never deploy directly to production without a staging pass. If the user asks to skip staging, push back and explain the risk.