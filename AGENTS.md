# mcp-dump Agent Notes

`mcp-dump` is a small Go CLI that starts a stdio Model Context Protocol (MCP)
server command, initializes a client session, and prints server capabilities,
tools, prompts, resources, and resource templates.

## Project Layout

- `cmd/mcp-dump/main.go`: executable entrypoint.
- `cmd/mcp-dump/cmd/command.go`: Cobra command, flags, examples, and argument validation.
- `internal/apps/mcpdump`: MCP inspection workflow and output formatting.
- `internal/apps/appio`: synchronized writer helpers.
- `internal/logging`: process-wide structured logging setup.

## Development Rules

- Keep stdout reserved for user-facing inspection output. Debug and server
  process logs must go to stderr.
- Keep MCP server examples in README/help current with supported servers.
  Do not add abandoned provider examples.
- Preserve the `-- <mcp-server-cmd> [args...]` contract. Arguments before `--`
  are CLI flags; arguments after it are passed to the MCP server.
- Prefer small, focused changes. Avoid unrelated workflow, orchestration, or
  product-policy docs in this repository.

## Commands

```sh
task test
task lint
task
```

Equivalent direct commands:

```sh
go test ./...
go tool golangci-lint run ./...
go build -o bin/mcp-dump ./cmd/mcp-dump
```
