# Edict IQ for Claude

This lightweight Claude plugin refers to the existing Edict IQ remote MCP service. No Edict IQ backend code, private source registry, APS configuration, or AI-provider secrets are distributed here.

MCP: https://edictiq.com/api/mcp

## Features

- Search approved source-backed regulatory changes and bounded evidence
- Retrieve organisation-specific impact assessments and open work
- List authorised Edict IQ organisations/workspaces and saved monitors
- On explicit request only, create a new target monitor in a selected authorised workspace with OAuth `monitor.write`
- Start secure first-party browser uploads for documents, portfolio statements, corporate groups and legal entities
- When permitted by the connected user’s existing roles and OAuth scopes, read bounded portfolio/entity summaries and document-check status
- Keep the paid analysis run and analysis-credit charges inside the existing Edict IQ browser flow

## Upload workflow

Ask Claude to show your connected Edict IQ workspaces and request a secure document, portfolio or legal-entity upload link. Claude calls `prepare_upload_handoff` and returns an Edict IQ URL. Open the link, authenticate in Edict IQ, upload directly there, then review the parsed proposals or document-check page quote before confirming. Never attach confidential source files to Claude or submit binary/base64 content through MCP.

The existing Edict IQ importer and document job/credit ledger remain authoritative, with no parallel storage or charging workflow. Claude can verify bounded inventory results through `get_workspace_inventory` and see document-check status through `list_document_checks` only with separate permissions.

## Authentication

Use the normal Edict IQ OAuth consent. The connection can see all organisations and workspaces that the signed-in user is already authorised to access; workspace-specific calls still require an explicit target. Target-monitor creation requires a user request, `monitor.write` authorisation and plan limits. API-key MCP credentials do not support monitor creation.

## Custom remote connector (no GitHub required)

In Claude Settings > Connectors, create a custom remote connector and enter:

https://edictiq.com/api/mcp

## Claude Plugin / public directory

Publish this directory as its own small GitHub repository and use the corresponding Anthropic developer portal review workflow. The public repository contains only this small plugin package and its documentation. Never upload the main Edict IQ application repository.

Review account: synthetic, entitled workspace with monitor creation permission and a sample regulatory assessment.

## Boundaries

Never import Claude chat history, memories or uploaded files. The plugin accesses only Edict IQ-controlled product data. No credit purchase, checkout, bulk corpus access or automatic compliance approvals.
