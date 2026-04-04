---
source: https://github.com/pathintegral-institute/mcpm.sh
date_accessed: 2026-04-04
published: 2025-01-01
author: pathintegral-institute / MCP-Club community
company: Open Source
level_mapping: [5]
tags: [mcp, mcpm, cli, package-manager, registry, tooling, developer-experience]
agent: agent-3b
---

## Summary
MCPM (MCP Package Manager) is an open-source CLI tool for managing MCP servers, analogous to how npm manages Node packages or pip manages Python packages. It provides a simplified global configuration model: install servers once, organize them with profiles, and integrate them into any MCP client. MCPM v2.13.0 was released January 15, 2026. It represents the "developer experience layer" on top of the MCP ecosystem — the practical tool a Gen AI engineer uses day-to-day to install, configure, and switch between MCP servers.

## Key Concepts

### Core Capabilities
- **Global Server Management**: Install MCP servers once; use across multiple clients (Claude Desktop, Cursor, Windsurf, etc.)
- **Server Discovery**: Browse and install from the official MCP Registry
- **Direct Execution**: Run servers over stdio or HTTP for testing/debugging
- **Profile System**: Organize servers into named profiles (e.g., "coding", "research", "local") and switch contexts
- **Public Sharing**: Share server configs through secure tunnels for team collaboration
- **Client Integration**: Manage configurations for Claude Desktop, Cursor, Windsurf, and other MCP clients

### Key Commands Pattern
```bash
mcpm search <query>          # discover servers from registry
mcpm install <server-name>   # install a server globally
mcpm list                    # list installed servers
mcpm profile create <name>   # create a named profile
mcpm profile use <name>      # switch active profile
mcpm run <server-name>       # run a server for testing
mcpm config <client>         # manage client configurations
```

### Ecosystem Variants
Multiple MCPM implementations exist:
- **pathintegral-institute/mcpm.sh**: Most mature, v2.13.0, supports all major clients
- **MCP-Club/mcpm**: Claude Desktop focused, also serves as an MCP server itself
- **IBM/mcp-cli**: Enterprise variant with package management docs
- **ascii27/mcpm**: Python-native implementation on PyPI

### PulseMCP Registry
- Community registry at pulsemcp.com — complementary to official MCP Registry
- Lists hundreds of available servers with trust scores and metadata
- Acts as a discovery layer — search servers, view documentation, assess trust
- Major contributor to the official public MCP registry alongside Anthropic/GitHub/Microsoft

### Integration Landscape
As of April 2026, MCP has moved beyond Anthropic-only: every major AI platform supports it. MCPM enables engineers to manage this cross-platform complexity without manually editing JSON config files per client.

## Quotes / Evidence
> "MCPM v2.0 provides a simplified approach to managing MCP servers with a global configuration model." — MCPM GitHub, 2026

> "As of April 2026, MCP has moved beyond being an Anthropic-only platform, with every major AI platform supporting it and the ecosystem growing faster than any developer tool standard since Docker." — npm/MCPM description

## Related Terms
- MCP (Model Context Protocol)
- MCP Registry (official)
- PulseMCP (community registry)
- Claude Desktop / Cursor / Windsurf (MCP clients)
- Claude Code Skills (related concept — custom slash commands)

## Relevance to Generative AI Engineer Role
At Level 5, MCPM is the day-to-day CLI tool for managing the MCP server ecosystem. A Gen AI Engineer uses it to: quickly install servers for specific tasks (GitHub, filesystem, databases, APIs), create profiles for different project types, and integrate servers into coding tools like Cursor or Claude Desktop. Understanding MCPM's profile system is key to efficiently switching contexts between projects.
