# Roadmap

`mcp-hub` starts as a local developer tool: one MCP endpoint for agents, one CLI for humans, and enough observability to debug a multi-server MCP setup.

The roadmap will change once code and user feedback arrive.

## Milestone 0: project foundation

- Define README, architecture, roadmap, and security posture.
- Choose the initial Python package layout.
- Add `pyproject.toml`, linting, tests, and a CLI entry point.
- Add a minimal config schema for local downstream servers.

## Milestone 1: local stdio gateway

- Read `mhub.yaml`.
- Start configured stdio MCP servers.
- Maintain one MCP client session per downstream server.
- Discover tools, resources, and prompts.
- Expose a single upstream MCP server surface.
- Namespace downstream capabilities.
- Proxy basic `tools/call` requests.

## Milestone 2: inspection and health

- Add `mhub ls` for configured servers and status.
- Add `mhub tools` for aggregated tool discovery.
- Add `mhub inspect <server>` for one-server details.
- Add `mhub doctor` for config validation, startup failures, and capability discovery problems.
- Report partial failures without hiding healthy servers.

## Milestone 3: observability

- Store event metadata in SQLite.
- Record route, server, tool, status, latency, and error class for each proxied call.
- Add `mhub logs` for recent events.
- Add `mhub stats` for call counts, latency, failures, and optional usage metadata.
- Keep payload capture disabled by default.

## Milestone 4: compatibility hardening

- Test against common MCP servers and hosts.
- Handle pagination and list-change notifications where supported.
- Improve resource URI rewriting and prompt namespacing.
- Add protocol version compatibility checks.
- Document known compatibility gaps.

## Later ideas

- Streamable HTTP downstream servers
- Remote upstream transport
- OAuth and auth helper flows
- Config profiles
- Policy controls for allowed servers and tools
- Web dashboard
- Redaction rules for logs
- Provider integrations for verified token usage

## Not planned for the first release

- Sandboxing arbitrary downstream servers
- Billing-grade token accounting
- Prompt-injection prevention claims
- Full remote deployment story
- A plugin marketplace
