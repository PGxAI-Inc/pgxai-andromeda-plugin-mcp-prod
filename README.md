# PGxAI Andromeda

Drug interaction reference. PGxAI Andromeda is an educational reference tool for exploring published drug-drug interactions, gene-drug associations, and drug-disease interactions.

## Tell your agent

> Connect the MCP server at https://app.pgx.ai/mcp/text and read https://app.pgx.ai/llms.txt for the details.

That is enough for most agents: [`llms.txt`](llms.txt) in this repository (also served at https://app.pgx.ai/llms.txt) lists the endpoints and the exact install
command for each client.

This repository is the plugin package for **PGxAI Andromeda**: it connects your agent to the PGxAI Andromeda MCP server.
It contains configuration and metadata only. The reference data and the lookup logic run on the PGxAI service.

## What you get

| Tool | What it does |
|---|---|
| `review_medication_evidence` | Looks up published drug-drug interactions, gene-drug associations and drug-disease information for the drugs, genes and terms you name, with excerpts and links to the original sources. |
| `get_condition_category` | Lists the accepted disease and population names, so a term can be matched to the exact entry the lookup accepts. |

Besides the two tools, the package carries one skill, `medication-evidence-reference`: instructions for a reference and teaching assistant for
clinicians and clinical educators (map terms first, run the lookup once, report the published findings separately from the educational
explanation, no identifying information, not medical advice).

Example prompts:

- What do published sources say about metoprolol and CYP2D6 ultrarapid metabolism? Include the source link.
- For a pharmacology lesson, check fexofenadine and hepatic impairment. Explain the result with a source link.
- What do published drug labels say about the interaction between fexofenadine and erythromycin? Include the source link.

## Install

The server is `https://app.pgx.ai/mcp/text` (streamable HTTP, no account or sign-in needed). Each platform reads its own file from this repository:

| Platform | File | How |
|---|---|---|
| Claude Code | `.claude-plugin/`, `.mcp.json` | `/plugin marketplace add PGxAI-Inc/pgxai-andromeda-plugin-mcp-prod`, then `/plugin install pgxai-andromeda@pgxai` |
| Cursor | `.cursor-plugin/plugin.json`, `mcp.json` | Add the plugin from this repository (see the Cursor plugin documentation). |
| xAI Grok | `.grok-plugin/plugin.json`, `.mcp.json` | Install from the xAI plugin marketplace once listed, or add this repository. |
| Antigravity | `.antigravity-plugin/plugin.json`, `plugin.json`, `mcp_config.json` | `agy plugin install https://github.com/PGxAI-Inc/pgxai-andromeda-plugin-mcp-prod` |
| Any MCP client | - | Add the URL above as a remote (streamable HTTP) server. |

## Network and data

- The plugin talks to one endpoint only: `https://app.pgx.ai/mcp/text`.
- It does not run code on your machine and has no hooks, scripts or local servers.
- This is an educational reference tool. Do not enter personal information; the server refuses inputs that look like direct identifiers.
- Not medical advice. The results are published reference information, not a recommendation for any individual.

## Links

- Product: https://pgx.ai/andromeda
- Privacy policy: https://pgx.ai/andromeda/privacy
- Terms of service: https://pgx.ai/andromeda/terms
- Support: https://pgx.ai/support-help

## License

The files in this repository are released under the MIT license (see `LICENSE`). Use of the service is governed by the
terms of service above.
