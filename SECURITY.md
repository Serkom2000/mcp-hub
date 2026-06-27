# Security

`mcp-hub` is not ready for production use yet. The repository currently defines the project direction and early design docs.

## Supported versions

No released versions are supported yet.

| Version | Supported |
| --- | --- |
| unreleased | No |

## Reporting a vulnerability

Please report security issues through GitHub Security Advisories if available for this repository. If advisories are not enabled, open a private contact path with the maintainer before sharing exploit details in a public issue.

## Security model

`mcp-hub` is expected to sit between an upstream MCP host and one or more downstream MCP servers. That position can expose sensitive data:

- MCP server configs may include commands, paths, environment variables, and auth hints.
- Tool calls may include private user input or workspace data.
- Tool responses may include secrets returned from downstream systems.
- Observability data may reveal which tools were called, when they failed, and how long they ran.

The project should default to metadata-only observability. Capturing request or response payloads should require explicit configuration and clear retention rules.

## Planned controls

- Redact common secret fields in logs and diagnostics.
- Keep payload capture disabled by default.
- Separate per-server auth and environment handling.
- Make dangerous server configs visible in `mhub doctor`.
- Document trust boundaries before adding remote transports.

## Non-goals for early releases

- `mcp-hub` will not sandbox arbitrary downstream MCP servers in the first milestone.
- `mcp-hub` will not claim to prevent prompt injection.
- `mcp-hub` will not provide billing-grade token accounting without verified provider integrations.
