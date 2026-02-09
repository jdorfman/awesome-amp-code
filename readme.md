<!--lint ignore awesome-toc-->
<div align='center'>

<!-- title -->

<!--lint ignore no-dead-urls-->

# Awesome Amp Code

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

<!-- subtitle -->

An **unofficial** curated list of resources for Amp, an AI coding agent by Sourcegraph

<!-- image -->

<img width=60% src='https://github.com/user-attachments/assets/00c0b998-0c2c-4b7b-bed7-913039bf00b5' />

<!-- description -->

</div>

<!-- TOC -->

<!--lint disable awesome-toc-->

## Contents

- [Official Resources](#official-resources)
- [Agent Files & Context](#agent-files--context)
- [MCP Servers](#mcp-servers)
- [Projects & Tools](#projects--tools)
- [Editor & IDE Integrations](#editor--ide-integrations)
- [CLI Usage](#cli-usage)
- [Security & Best Practices](#security--best-practices)
- [Contributing](#contributing)

<!-- CONTENT -->

### Official Resources

- [Amp](https://ampcode.com) - Main Amp website.
- [Amp Owner's Manual](https://ampcode.com/manual) - Comprehensive official documentation covering installation, usage, and best practices.
- [Amp CLI](https://www.npmjs.com/package/@sourcegraph/amp) - Official CLI package on npm.
- [Amp for VS Code](https://marketplace.visualstudio.com/items?itemName=sourcegraph.amp) - Official VS Code extension.
- [Amp SDK](https://ampcode.com/manual/sdk) - Official SDK documentation for building on Amp.
- [Raising an Agent Podcast](https://ampcode.com/podcast) - Podcast featuring insights from the Amp team.
- [Amp 101 YouTube Playlist](https://www.youtube.com/playlist?list=PL6zLuuRVa1_hLpciEULtzC3g3u4NJ6TVz) - Official video tutorials.
- [How to Build an Agent](https://ampcode.com/how-to-build-an-agent) - Guide to building AI agents.
- [Amp Chronicle](https://ampcode.com/chronicle) - Official news and announcements.
- [Amp Status](https://ampcodestatus.com) - Service status page.
- [Amp on X](https://x.com/ampcode) - Official Twitter/X account.

### Agent Files & Context

AGENTS.md files provide context and instructions to AI coding agents about your codebase. They help agents understand project structure, coding standards, and specific requirements.

**Examples of AGENTS.md in open source projects:**

- [LangGraph](https://sourcegraph.com/github.com/langchain-ai/langgraph/-/blob/AGENTS.md) - LangChain's graph-based agent framework.
- [Zoekt](https://sourcegraph.com/github.com/sourcegraph/zoekt/-/blob/AGENT.md) - Fast code search by Sourcegraph.
- [Ultimate MCP Client](https://github.com/Dicklesworthstone/ultimate_mcp_client/blob/main/AGENT.md) - Comprehensive MCP client implementation.
- [MCP Advisor](https://sourcegraph.com/github.com/istarwyh/mcpadvisor/-/blob/AGENT.md) - MCP server advisor tool.
- [Use MCP](https://sourcegraph.com/github.com/modelcontextprotocol/use-mcp/-/blob/AGENT.md) - Official MCP usage examples.

### MCP Servers

Model Context Protocol (MCP) enables AI agents to interact with external tools and services. These MCP servers extend Amp's capabilities:

- [llm-rules MCP](https://www.npmjs.com/package/llm-rules) - Access Cursor rules dynamically via MCP.
- [CleanShot MCP](https://github.com/jdorfman/cleanshot-mcp) - MCP server for CleanShot X screenshot and recording integration.
- [MCP Advisor](https://github.com/istarwyh/mcpadvisor) - Tool to help discover and configure MCP servers.
- [Ultimate MCP Client](https://github.com/Dicklesworthstone/ultimate_mcp_client) - Comprehensive MCP client for testing and debugging servers.
- [Use MCP](https://github.com/modelcontextprotocol/use-mcp) - Official examples and utilities for MCP usage.

### Projects & Tools

**Documentation & Guides:**

- [Unofficial Amp CLI Documentation](https://github.com/jdorfman/awesome-amp-code/blob/main/docs/amp_cli_docs.md) - Comprehensive documentation for Amp CLI with examples and best practices.
- [File-Based Amp Prompting Workflows](https://github.com/PriNova/amp-prompting-workflows) - Collection of file-based sub-agent orchestration workflows for Amp.

**Development Tools:**

- [Sandboxed.sh](https://github.com/Th0rgal/sandboxed.sh) - Self-hosted cloud orchestrator for AI coding agents with isolated Linux environments.
- [Unofficial Amp Supervisor](https://github.com/ctrl-cheeb-del/manager) - TUI control panel for managing multiple Amp CLI instances in parallel.
- [Conductor](https://x.com/charliebholtz/status/1963345520543633742) - Run a bunch of Amps in parallel.
- [Amp Code Review CI](https://github.com/madhukarkumar/amp-code-review-ci) - Continuous integration tool for automated code reviews using Amp.
- [Tokscale](https://github.com/junhoyeo/tokscale) - CLI tool for tracking token usage from AmpCode and other coding agents.
- [Sniff](https://github.com/conikeec/sniff) - Misalignment detection in Vibe Coding loops.
- [CodeForge](https://github.com/entrepeneur4lyf/CodeForge) - Golang Development tool built with Amp.

**Applications Built with Amp:**

- [Jazzberry AI](https://jazzberry.ai/) - The AI Bug Finder.
- [0.email](https://0.email/) - AI-native email client that manages your inbox.
- [Remote Code](https://remote-code.com/) - Mobile coding platform that brings AI coding agents to your iPhone.
- [SageMap](https://sagemap.netlify.app/) - Interactive belief mapping tool for journal entries.
- [VT Chat](https://vtchat.io.vn/) - Privacy-first AI chat application.
- [HTTPie Collection Viewer](https://httpie.bolaji.de/) - Upload and explore your HTTPie collections.
- [Quad Ops](https://trly.github.io/quad-ops/) - Lightweight GitOps framework for podman containers.
- [PromptVault](https://hex.pm/packages/prompt_vault) - Library for managing prompts and templates in Elixir.
- [CircuitPython Deploy](https://github.com/shantanugoel/circuitpython-deploy) - CircuitPython deployment tool.

**Browser & Misc:**

- [Sourcegraph Chrome Extension](https://chromewebstore.google.com/detail/sourcegraph/dgjhfomjieaadpoljlnidmbg) - Chrome extension for code search and navigation.
- [Sourcegraph Amp AUR](https://github.com/AnirudhKonduru/sourcegraph-amp-aur) - Arch Linux AUR package for Sourcegraph Amp.

### Editor & IDE Integrations

- [amp.nvim](https://github.com/sourcegraph/amp.nvim) - Official Neovim plugin for Amp coding agent.
- [nvim-amp](https://github.com/aliou/nvim-amp) - Neovim plugin providing syntax highlighting and support for Amp permission and agent files.
- [amp.el](https://github.com/shaneikennedy/amp.el) - Emacs integration for Amp coding agent.
- [Amp ACP](https://github.com/tao12345666333/amp-acp) - ACP adapter for Amp Code, enabling Amp to work in the Zed editor.
- [MyScratchpad VS Code Extension](https://marketplace.visualstudio.com/items?itemName=jccoder.myscratchpad) - VS Code extension for global and workspace-specific scratch files.
- [Amp Dash X](https://www.raycast.com/jdorfman/sourcegraph-amp-dash-x) - Raycast extension for organizing and executing Amp Code prompts.
- [VibeKanban](https://www.vibekanban.com/) - CLI tool for managing your Kanban boards.

### CLI Usage

Amp CLI can be integrated with other command-line tools. Use the `-x` flag for execute mode or pipe input directly:

```bash
# Analyze processes
ps aux > processes.txt | amp -x 'identify processes consuming the most resources in processes.txt'

# Parse whois data
whois example.com | amp -x 'organize and condense this whois information'

# Analyze HTTP headers
curl -Is https://github.com > headers.txt && amp -x 'analyze the http headers in headers.txt and determine the tech stack'

# Check npm dependencies
npm list --json | amp -x 'identify outdated or vulnerable dependencies'
```

### Security & Best Practices

When using AI coding agents, consider these security aspects:

- [Amp Security Reference](https://ampcode.com/security) - Official security documentation and guidelines.
- [Amp Permissions](https://ampcode.com/manual/permissions) - Control what actions the agent can perform.

**Key recommendations:**
- Always review AI-generated code before committing
- Never include API keys or secrets in prompts or AGENTS.md files
- Consider running agents in isolated environments for sensitive projects
- Vet MCP servers before installation

### Contributing

[Contributions of any kind welcome, just follow the guidelines](contributing.md)!

#### Contributors

[Thanks goes to these contributors](https://github.com/lfglabs-dev/awesome-amp-code/graphs/contributors)!

---

### Credits

Originally created and maintained by [Justin Dorfman](https://www.justindorfman.com/).
