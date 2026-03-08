# hiero-plugin-camp

[![Node.js](https://img.shields.io/badge/Node.js-18+-339933?logo=node.js&logoColor=white)](https://nodejs.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org)
[![Hedera](https://img.shields.io/badge/Hedera-Hiero%20CLI-8259EF?logo=hedera)](https://hedera.com)
[![Tests](https://img.shields.io/badge/Tests-37%20passing-brightgreen)](.)

Hiero CLI plugin for camp workspace management -- Hedera developer tooling.

Part of the [Obey Agent Economy](https://github.com/lancekrogers/Obey-Agent-Economy) project.

## Overview

hiero-plugin-camp extends the [Hiero CLI](https://github.com/hiero-ledger/hiero-cli) with workspace management commands under the `hcli camp` namespace. It wraps the `camp` binary to provide Hedera-specific project initialization, status reporting, and workspace navigation, bundling three scaffold templates for common Hedera development patterns.

Built for **Hedera Track 4** at ETHDenver 2026.

> **TL;DR** — A Hiero CLI plugin that brings `camp` workspace management to Hedera developers. Scaffolds projects from templates (dApp, agent, smart contract, 0G), manages multi-project workspaces, and provides fuzzy-find navigation.

### Built with Obedience Corp

This project is part of an [Obedience Corp](https://obediencecorp.com) campaign — built and planned using **camp** (campaign management) and **fest** (festival methodology). This repository, its git history, and the planning artifacts in `festivals/` are a live example of these tools in action.

The plugin wraps the **camp** binary directly, bringing Obedience Corp's campaign workspace management into the Hiero CLI ecosystem.

## Quick Start

```bash
# Register the plugin with Hiero CLI
hcli plugin-management add -p /path/to/hiero-plugin-camp/dist

# Initialize a Hedera dApp project
hcli camp init --name my-hedera-app --template hedera-dapp

# Check workspace status
hcli camp status

# Navigate projects
hcli camp navigate my-app
```

## Prerequisites

- Node.js >= 18
- [Hiero CLI](https://github.com/hiero-ledger/hiero-cli) installed (`npm install -g @hiero-ledger/hiero-cli`)
- `camp` binary installed and on PATH
- Hedera testnet account for template projects ([portal.hedera.com](https://portal.hedera.com))

## Installation

```bash
git clone https://github.com/lancekrogers/hiero-plugin-ethden-2026.git
cd hiero-plugin-ethden-2026
npm install
npm run build

# Register with Hiero CLI
hcli plugin-management add -p $(pwd)/dist
```

## Commands

| Command | Description |
|---------|-------------|
| `hcli camp init` | Initialize a camp workspace with Hedera templates |
| `hcli camp status` | Show project status across the workspace |
| `hcli camp navigate` | Fuzzy-find navigation within the workspace |

See [docs/usage-guide.md](docs/usage-guide.md) for detailed usage examples.

## Templates

| Template | Language | Description |
|----------|----------|-------------|
| `hedera-smart-contract` | TypeScript/Solidity | Hardhat project with Hedera testnet JSON-RPC config |
| `hedera-dapp` | TypeScript/React | Vite + React app with HashConnect wallet integration |
| `hedera-agent` | Go | Agent with HCS messaging and HTS token operations |
| `0g-agent` | Go | 0G Compute inference agent with session auth and DA |
| `0g-inft-build` | Solidity/Go | ERC-7857 iNFT minting with encrypted metadata on 0G Chain |

## Project Structure

```
hiero-plugin/
├── src/
│   ├── index.ts               # Plugin manifest and entry point
│   ├── commands/
│   │   ├── init.ts            # Initialize workspace with templates
│   │   ├── status.ts          # Show project status
│   │   └── navigate.ts        # Fuzzy-find navigation
│   └── templates/
│       ├── hedera-smart-contract/
│       ├── hedera-dapp/
│       ├── hedera-agent/
│       ├── 0g-agent/
│       └── 0g-inft-build/
├── dist/                      # Compiled output
├── justfile                   # Task runner recipes
└── package.json
```

## Development

```bash
just install    # Install dependencies
just build      # Compile TypeScript
just test       # Run tests (37 tests)
just lint       # Type-check without emitting
just dev        # Watch mode
```

## Architecture

See [docs/architecture.md](docs/architecture.md) for design decisions and component overview.

## Hedera Track 4 Alignment

This project targets the **Hedera Track 4: Developer Tooling** ($5k) bounty.

| Requirement | Implementation |
|-------------|----------------|
| Extends Hiero ecosystem | Plugin for the official Hiero CLI via `plugin-management add` |
| Developer productivity | Three scaffold templates eliminate boilerplate for common Hedera patterns |
| Workspace management | `init`, `status`, and `navigate` commands for multi-project Hedera workspaces |
| Template variety | Smart contract (Solidity/Hardhat), dApp (React/HashConnect), Agent (Go/HCS/HTS) |
| Production quality | 37 passing tests, TypeScript throughout, modular command architecture |
| Documentation | Usage guide, architecture doc, and template design notes included |

### What Developers Get

1. **`hcli camp init --template hedera-dapp`**: Scaffolds a complete React + Vite + HashConnect dApp with Hedera testnet config in seconds
2. **`hcli camp init --template hedera-agent`**: Scaffolds a Go agent with HCS topic messaging and HTS token operations pre-wired
3. **`hcli camp status`**: See all projects in a workspace at a glance
4. **`hcli camp navigate`**: Fuzzy-find jump to any project in the workspace

## License

MIT
