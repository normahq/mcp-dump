# mcp-dump

[![test](https://github.com/normahq/mcp-dump/actions/workflows/test.yml/badge.svg?branch=main)](https://github.com/normahq/mcp-dump/actions/workflows/test.yml)
[![lint](https://github.com/normahq/mcp-dump/actions/workflows/lint.yml/badge.svg?branch=main)](https://github.com/normahq/mcp-dump/actions/workflows/lint.yml)
[![security](https://github.com/normahq/mcp-dump/actions/workflows/security.yml/badge.svg?branch=main)](https://github.com/normahq/mcp-dump/actions/workflows/security.yml)
[![release](https://github.com/normahq/mcp-dump/actions/workflows/omnidist-release.yml/badge.svg)](https://github.com/normahq/mcp-dump/actions/workflows/omnidist-release.yml)
[![npm](https://img.shields.io/npm/v/@normahq/mcp-dump)](https://www.npmjs.com/package/@normahq/mcp-dump)
[![License](https://img.shields.io/github/license/normahq/mcp-dump)](LICENSE)
[![Version](https://img.shields.io/github/v/tag/normahq/mcp-dump?label=version)](https://github.com/normahq/mcp-dump/tags)

**Inspect MCP servers before connecting tools or agents.**

`mcp-dump` starts any stdio Model Context Protocol (MCP) server command and
prints initialize, capability, tool, prompt, resource, and resource-template
metadata.

Use it when you need to confirm what an MCP server actually exposes before
adding it to an agent, IDE, gateway, or automation workflow.

## What You Get

| Capability | Behavior |
| --- | --- |
| MCP preflight | Starts a stdio MCP server command and initializes a client session. |
| Capability inventory | Prints protocol version, server info, and server capabilities. |
| Tool discovery | Lists tools with input parameters and response schemas. |
| Prompt/resource discovery | Shows prompts, resources, and resource templates when supported. |
| JSON output | Emits machine-readable output for scripts, CI checks, and debugging artifacts. |
| Quiet by default | Keeps inspector lifecycle logs out of the result unless `--debug` is enabled. |

## Try It

Install globally:

```sh
npm install -g @normahq/mcp-dump@latest
```

Run once with `npx`:

```sh
npx @normahq/mcp-dump@latest -- <mcp-server-cmd> [args...]
```

Inspect an MCP server:

```sh
mcp-dump -- codex mcp-server
mcp-dump --json -- codex mcp-server --sandbox workspace-write
mcp-dump --debug -- <mcp-server-cmd> [args...]
```

## Provider Commands

| Provider | Command |
| --- | --- |
| Codex MCP server | `mcp-dump -- codex mcp-server` |
| Codex with sandbox | `mcp-dump --json -- codex mcp-server --sandbox workspace-write` |
| Generic MCP | `mcp-dump -- <mcp-server-cmd> [args...]` |

The `--` separator is required. Arguments before `--` are treated as
`mcp-dump` flags; arguments after it are passed to the MCP server command.

## Output

Human-readable output includes:

- server name and version
- protocol version
- server capabilities
- tools with input parameters and response schemas
- prompts, resources, and resource templates status

Use `--json` when you want stable output for scripts, test fixtures, issue
reports, or CI logs.

## Use Cases

- Verify an MCP server before registering it with an agent runtime.
- Compare tool schemas across local and remote server commands.
- Capture a compact diagnostic artifact for bug reports.
- Check whether a local command is actually speaking MCP over stdio.

## Flags

| Flag | Purpose |
| --- | --- |
| `--json` | Print machine-readable JSON output. |
| `--debug` | Enable debug logs for the inspector. |
| `-h`, `--help` | Show command help. |

## Repository

- GitHub: <https://github.com/normahq/mcp-dump>

## Contact

- Issues: <https://github.com/normahq/mcp-dump/issues>
- Maintainer: [@metalagman](https://github.com/metalagman)

## License

MIT. See the repository [LICENSE](https://github.com/normahq/mcp-dump/blob/main/LICENSE).
