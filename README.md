# Netiker for ChatGPT and Codex

Official source package for the Netiker plugin. Analyze saved Google Search Console, Bing Webmaster Tools, Ahrefs and other reports from your Netiker account.

This repository contains the plugin, not the Netiker application or its server implementation. The hosted backend is https://app.netiker.com/mcp.

## Package

- `plugin.json`: portable manifest, listing metadata and public publisher links.
- `mcp.json`: remote Streamable HTTP connection with OAuth, DCR and S256 PKCE.
- `skills/netiker/SKILL.md`: report discovery, source interpretation, pagination and aggregation guidance.
- `assets/icon.png`: Netiker listing icon, 512 × 512 pixels.

Tools are read-only: `list_reports`, `get_report`, `read_report_rows`, `list_sync_runs`. Provider credentials stay in Netiker. Reading reports does not refresh sources or modify data. Account Data API limits apply.

## Validate and build

Run `node scripts/validate.mjs` using Node.js 24. No npm dependencies are required.

GitHub Actions validates each push and builds a ZIP containing the manifests at its root. Download the `netiker-chatgpt-plugin` artifact from a successful Actions run; unpack the artifact wrapper and submit the `netiker-plugin-<version>.zip` inside it.

Alternatively, using a system ZIP utility from the repository root:

```sh
zip -r netiker-plugin.zip plugin.json mcp.json README.md assets skills
```

## Submit to OpenAI

1. Open https://platform.openai.com/plugins and select your verified developer identity.
2. Upload the plugin ZIP, including the MCP configuration from the initial submission.
3. Connect the declared MCP server using OAuth and complete the domain challenge supplied by the portal.
4. Resolve metadata and tool findings, provide a dedicated reviewer account with sample data, test cases and a video walkthrough.
5. Submit for review. Publish from the portal after approval.

OpenAI assigns the plugin identity. No pre-existing app ID or private connection is required to start the ZIP submission. Do not reuse another plugin's registered app ID. A public-directory listing is not created merely by publishing this GitHub repository.

Directory status: not yet published. There is no fictional install link or registered-app mapping in this package.

Product: https://netiker.com/chatgpt
Privacy: https://netiker.com/privacy
Terms: https://netiker.com/terms
Support: https://netiker.com/contact

Official submission documentation: https://developers.openai.com/plugins/deploy/submission
