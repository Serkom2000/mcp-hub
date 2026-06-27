# Agent instructions

These instructions apply to the whole repository.

## Rules

- Treat the project as an early-stage Python CLI and MCP gateway.
- Keep documentation honest about shipped behavior. Do not describe commands, transports, security controls, or package installation as released until code exists.
- Prefer small, testable modules over framework-heavy architecture.
- Do not store secrets, access tokens, request payloads, or captured tool outputs in committed examples.
- Keep MCP terminology precise: upstream MCP hosts connect to `mcp-hub` as a server; `mcp-hub` maintains MCP client sessions to downstream servers.
- Avoid broad compatibility claims until tests prove them against real MCP clients, servers, protocol versions, and transports.

## Tech stack

- Language: Python
- CLI: planned around Typer or a similarly small CLI framework
- Terminal output: planned around Rich
- Config: planned YAML config
- Local event store: planned SQLite
- Protocol: Model Context Protocol

Exact dependencies should live in `pyproject.toml` once implementation starts.

## Commands

No project commands exist yet. Add this section when the repository has a real `pyproject.toml`, test runner, formatter, and CLI entry point.

Expected future commands:

```bash
uv sync
uv run pytest
uv run ruff check .
uv run mhub --help
```

## Architecture boundaries

- `mcp-hub` should act as an MCP server to upstream hosts.
- `mcp-hub` should act as an MCP client to each configured downstream MCP server.
- Downstream server sessions should stay isolated from each other.
- Namespacing should make exposed tools, prompts, and resource identifiers collision-free.
- Observability should record routing, status, latency, errors, and optional usage metadata without assuming MCP provides token counts.
- Security-sensitive behavior needs explicit opt-in and clear docs, especially payload capture and environment variable handling.

## Documentation style

- Use sentence case headings.
- Prefer concrete examples over broad claims.
- Mark unstable design choices as planned or proposed.
- Keep README focused on what the project is, why it exists, and how the first usable workflow should feel.
- Move longer design notes into `docs/`.
