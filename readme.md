<!--lint ignore awesome-toc-->
<div align="center">

<!-- title -->

<!--lint ignore no-dead-urls-->

# Awesome Amp Code

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

<!-- subtitle -->

An **unofficial** curated list of resources for Amp, an AI coding agent by Sourcegraph

<!-- image -->

<img src="https://github.com/user-attachments/assets/44099391-3976-473d-bcf8-95fd7b980f99" />

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

- [Unofficial Amp CLI Documentation](https://github.com/jdorfman/awesome-amp-code/blob/main/docs/amp_cli_docs.md)
- [Multimeter](https://www.multimeter.dev/)
- [MyScratchpad Vscode Extension](https://marketplace.visualstudio.com/items?itemName=jccoder.myscratchpad)
- [Unofficial Amp Supervisor](https://github.com/ctrl-cheeb-del/manager)
- [llm-rules MCP](https://www.npmjs.com/package/llm-rules)
- [amp.el - Emacs integration for Amp](https://github.com/shaneikennedy/amp.el)
- [Amp in a Container](https://github.com/madhukarkumar/amp-in-a-container)
- [Remote Code](https://remote-code.com/)
- [Sourcegraph Amp AUR](https://github.com/AnirudhKonduru/sourcegraph-amp-aur)

### Amp CLI

#### Integration with Common CLI Tools

Amp CLI can be seamlessly integrated with other command-line tools to enhance your workflow:

##### ps aux

```bash
ps aux > /tmp/psaux.txt && echo "identify processes consuming the most resources" && cat /tmp/psaux.txt | amp
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
