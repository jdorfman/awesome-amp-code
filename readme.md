<!--lint ignore awesome-toc-->
<div align="center">

<!-- title -->

<!--lint ignore no-dead-urls-->

# Awesome Amp Code

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

<!-- subtitle -->

An **unofficial** curated list of resources for Amp, an AI coding agent by Sourcegraph

<!-- image -->

<img width=60% src="https://github.com/user-attachments/assets/00c0b998-0c2c-4b7b-bed7-913039bf00b5" />

<!-- description -->

</div>

<!-- TOC -->

<!--lint disable awesome-toc-->

## Contents

- [Awesome Amp Code](#awesome-amp-code)
  - [Contents](#contents)
    - [AGENT.md](#agentmd)
    - [Demos](#demos)
    - [Built with Amp](#built-with-amp)
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

### AGENT.md

- [Sourcegraph Cody](https://sourcegraph.com/github.com/sourcegraph/cody/-/blob/AGENT.md)
- [Zoekt](https://sourcegraph.com/github.com/sourcegraph/zoekt/-/blob/AGENT.md)
- [Ultimate MCP Client](https://github.com/Dicklesworthstone/ultimate_mcp_client/blob/main/AGENT.md)

### Demos

- [Vibecoding a compiler](https://x.com/GeoffreyHuntley/status/1921336503805886894)
- [Use Amp & Zapier MCP to turn `*//todo` code comments into Linear issues](https://x.com/jdorfman/status/1926007226969231861)
- [Building a VSCode Extension with Amp](https://youtu.be/l-VUgg6NmDs?si=5M-D1YOyG4TWk6xS)
- [Fun with pie charts](https://x.com/jdorfman/status/1935196938024243551)

### Built with Amp

- [Unofficial Amp CLI Documentation](https://github.com/jdorfman/awesome-amp-code/blob/main/docs/amp_cli_docs.md) - Comprehensive documentation for Amp CLI with examples and best practices.
- [Multimeter](https://www.multimeter.dev/) - Coding agent sentiment analysis platform with social features.
- [MyScratchpad VS Code Extension](https://marketplace.visualstudio.com/items?itemName=jccoder.myscratchpad) - VS Code extension for global and workspace-specific scratch files.
- [Unofficial Amp Supervisor](https://github.com/ctrl-cheeb-del/manager) - TUI control panel for managing multiple Amp CLI instances in parallel.
- [llm-rules MCP](https://www.npmjs.com/package/llm-rules) - Model Context Protocol server for accessing Cursor rules dynamically.
- [amp.el](https://github.com/shaneikennedy/amp.el) - Emacs integration for Amp coding agent.
- [Amp in a Container](https://github.com/madhukarkumar/amp-in-a-container) - Docker container for running Amp CLI with long-running and async tasks.
- [Remote Code](https://remote-code.com/) - Mobile coding platform that brings AI coding agents to your iPhone.
- [Sourcegraph Amp AUR](https://github.com/AnirudhKonduru/sourcegraph-amp-aur) - Arch Linux AUR package for Sourcegraph Amp.
- [PromptVault](https://hex.pm/packages/prompt_vault) - A library for managing prompts and templates in Elixir. [Watch stream](https://www.youtube.com/live/ojaoe3h8hXA?feature=share).
- [Unofficial Amp Owner's Manual](https://superpromptor.com/amp-owners-manual/) - Comprehensive guide to getting the most out of Amp coding agent.
- [VibeKanban](https://www.vibekanban.com/) - CLI tool for managing your Kanban boards.
- [Sourcegraph Chrome Extension](https://chromewebstore.google.com/detail/sourcegraph/dgjhfomjieaadpoljlnidmbg) - Chrome extension for code search and navigation.
- [CircuitPython Deploy](https://github.com/shantanugoel/circuitpython-deploy) - CircuitPython deployment tool.
- [File-Based Amp Prompting Workflows](https://github.com/PriNova/amp-prompting-workflows) - Comprehensive collection of file-based sub-agent orchestration workflows for Amp with persistent document-based communication.

### Amp CLI

#### Integration with Common CLI Tools

Amp CLI can be seamlessly integrated with other command-line tools to enhance your workflow:

##### ps aux

```bash
echo "identify processes consuming the most resources" && ps aux | amp
```

##### whois

```bash
 echo "organize and condense the following whois information" && whois example.com | amp
```

##### curl

```bash
echo "convert the cache control max-age value from seconds to days, hours, minutes" $(curl -I https://example.com) | amp
```

```bash
echo "read the http headers and determine what the domains tech stack is." $(curl -Is https://example.com) | amp
```

##### npm

```bash
npm list --json && echo "identify outdated or vulnerable dependencies" | amp
```

### Official Amp Links

- [Amp](https://ampcode.com)
- [Amp CLI](https://www.npmjs.com/package/@sourcegraph/amp)
- [Amp for VS Code](https://marketplace.visualstudio.com/items?itemName=sourcegraph.amp)
- [Raising an Agent Podcast](https://ampcode.com/podcast)
- [Amp on X](https://x.com/ampcode)
- [How to Build an Agent](https://ampcode.com/how-to-build-an-agent)

### Contributing

[Contributions of any kind welcome, just follow the guidelines](contributing.md)!

#### Contributors

[Thanks goes to these contributors](https://github.com/jdorfman/awesome-amp-code/graphs/contributors)!
