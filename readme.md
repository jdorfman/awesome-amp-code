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

- [Awesome Amp Code](#awesome-amp-code)
  - [Contents](#contents)
    - [AGENTS.md](#agentsmd)
    - [Built with Amp](#built-with-amp)
    - [Amp Integrations](#amp-integrations)
    - [Amp CLI](#amp-cli)
      - [Integration with Common CLI Tools](#integration-with-common-cli-tools)
        - [ps aux](#ps-aux)
        - [whois](#whois)
        - [curl](#curl)
        - [npm](#npm)
    - [Official Amp Links](#official-amp-links)
    - [Contributing](#contributing)
      - [Contributors](#contributors)

<!-- CONTENT -->

### AGENTS.md

- [LangGraph](https://sourcegraph.com/github.com/langchain-ai/langgraph/-/blob/AGENTS.md)
- [Sink](https://sourcegraph.com/github.com/ccbikai/Sink/-/blob/AGENT.md)
- [Zoekt](https://sourcegraph.com/github.com/sourcegraph/zoekt/-/blob/AGENT.md)
- [Ultimate MCP Client](https://github.com/Dicklesworthstone/ultimate_mcp_client/blob/main/AGENT.md)
- [MCP Advisor](https://sourcegraph.com/github.com/istarwyh/mcpadvisor/-/blob/AGENT.md)
- [Use MCP](https://sourcegraph.com/github.com/modelcontextprotocol/use-mcp/-/blob/AGENT.md)

### Built with Amp

- [Unofficial Amp CLI Documentation](https://github.com/jdorfman/awesome-amp-code/blob/main/docs/amp_cli_docs.md) - Comprehensive documentation for Amp CLI with examples and best practices.
- [MyScratchpad VS Code Extension](https://marketplace.visualstudio.com/items?itemName=jccoder.myscratchpad) - VS Code extension for global and workspace-specific scratch files.
- [Unofficial Amp Supervisor](https://github.com/ctrl-cheeb-del/manager) - TUI control panel for managing multiple Amp CLI instances in parallel.
- [llm-rules MCP](https://www.npmjs.com/package/llm-rules) - Model Context Protocol server for accessing Cursor rules dynamically.
- [amp.el](https://github.com/shaneikennedy/amp.el) - Emacs integration for Amp coding agent.
- [Remote Code](https://remote-code.com/) - Mobile coding platform that brings AI coding agents to your iPhone.
- [Sourcegraph Amp AUR](https://github.com/AnirudhKonduru/sourcegraph-amp-aur) - Arch Linux AUR package for Sourcegraph Amp.
- [PromptVault](https://hex.pm/packages/prompt_vault) - A library for managing prompts and templates in Elixir. [Watch stream](https://www.youtube.com/live/ojaoe3h8hXA?feature=share).
- [Unofficial Amp Owner's Manual](https://superpromptor.com/amp-owners-manual/) - Comprehensive guide to getting the most out of Amp coding agent.
- [Sourcegraph Chrome Extension](https://chromewebstore.google.com/detail/sourcegraph/dgjhfomjieaadpoljlnidmbg) - Chrome extension for code search and navigation.
- [CircuitPython Deploy](https://github.com/shantanugoel/circuitpython-deploy) - CircuitPython deployment tool.
- [File-Based Amp Prompting Workflows](https://github.com/PriNova/amp-prompting-workflows) - Comprehensive collection of file-based sub-agent orchestration workflows for Amp with persistent document-based communication.
- [Amp Code Review CI](https://github.com/madhukarkumar/amp-code-review-ci) - Continuous integration tool for automated code reviews using Amp.
- [CodeForge](https://github.com/entrepeneur4lyf/CodeForge) - Golang Development tool built with Amp.
- [Quad Ops](https://trly.github.io/quad-ops/) - A lightweight GitOps framework for podman containers managed by Quadlet.
- [HTTPie Collection Viewer](https://httpie.bolaji.de/) - Upload and explore your HTTPie collections with style.
- [CleanShot MCP](https://github.com/jdorfman/cleanshot-mcp) - Model Context Protocol server for CleanShot X screenshot and recording.
- [SageMap](https://sagemap.netlify.app/) - Interactive belief mapping tool that transforms journal entries into visual networks revealing contradictions and connections in your thoughts.
- [Jazzberry AI](https://jazzberry.ai/) - The AI Bug Finder.
- [0.email](https://0.email/) - Zero is an AI-native email client that manages your inbox.
- [VT Chat](https://vtchat.io.vn/) - A minimal, privacy-first AI chat application with advanced AI capabilities.
- [Sniff](https://github.com/conikeec/sniff) - Misalignment detection in Vibe Coding loops.

### Amp Integrations

- [Amp Dash X](https://www.raycast.com/jdorfman/sourcegraph-amp-dash-x) - A Raycast extension for organizing and executing Amp Code prompts with the `-x` (execute) flag.
- [VibeKanban](https://www.vibekanban.com/) - CLI tool for managing your Kanban boards.
- [Conductor](https://x.com/charliebholtz/status/1963345520543633742) - Run a bunch of Amps in parallel.
- [amp.nvim](https://github.com/sourcegraph/amp.nvim) - Official Neovim plugin for Amp coding agent.
- [nvim-amp](https://github.com/aliou/nvim-amp) - Neovim plugin providing syntax highlighting and support for Amp permission and agent files.
- [Amp ACP](https://github.com/tao12345666333/amp-acp) - ACP adapter for Amp Code, enabling Amp to work in the Zed editor.
- [Tokscale](https://github.com/junhoyeo/tokscale) - A CLI tool for tracking token usage from AmpCode and other coding agents (OpenCode, Claude Code, Codex, Gemini CLI, Cursor IDE, and Factory Droid)

### Amp CLI

#### Integration with Common CLI Tools

Amp CLI can be seamlessly integrated with other command-line tools to enhance your workflow. Use the `-x` flag for execute mode or pipe input directly:

##### ps aux

```bash
ps aux > processes.txt | amp -x 'identify processes consuming the most resources in processes.txt'
```

##### whois

```bash
whois example.com | amp -x 'organize and condense this whois information'
```

##### curl

```bash
curl -Is https://github.com > headers.txt && amp -x 'analyze the http headers in headers.txt and determine the tech stack'
```

##### npm

```bash
npm list --json | amp -x 'identify outdated or vulnerable dependencies'
```

### Official Amp Links

- [Amp](https://ampcode.com)
- [Amp CLI](https://www.npmjs.com/package/@sourcegraph/amp)
- [Amp for VS Code](https://marketplace.visualstudio.com/items?itemName=sourcegraph.amp)
- [Raising an Agent Podcast](https://ampcode.com/podcast)
- [Amp on X](https://x.com/ampcode)
- [How to Build an Agent](https://ampcode.com/how-to-build-an-agent)
- [Amp 101 YouTube Playlist](https://www.youtube.com/playlist?list=PL6zLuuRVa1_hLpciEULtzC3g3u4NJ6TVz)

### Contributing

[Contributions of any kind welcome, just follow the guidelines](contributing.md)!

#### Contributors

[Thanks goes to these contributors](https://github.com/jdorfman/awesome-amp-code/graphs/contributors)!
