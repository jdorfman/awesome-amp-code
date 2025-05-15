<!--lint ignore awesome-toc-->
<div align="center">

<!-- title -->

<!--lint ignore no-dead-urls-->

# Awesome Amp CLI

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

<!-- subtitle -->

An unofficial curated list of resources for Amp CLI, an AI coding agent by Sourcegraph

<!-- image -->

<a href="https://github.com/jdorfman/awesome-amp-cli/blob/main/amp_cli_docs.md" target="_blank" rel="noopener noreferrer"> <img src="https://github.com/user-attachments/assets/3b152173-e617-463e-825f-14036c04f163" /></a>

<!-- description -->

</div>

<!-- TOC -->

<!--lint disable awesome-toc-->
## Contents

- [Awesome Amp CLI](#awesome-amp-cli)
  - [Contents](#contents)
    - [Integration with Common CLI Tools](#integration-with-common-cli-tools)
      - [ps aux](#ps-aux)
      - [whois](#whois)
      - [curl](#curl)
      - [npm](#npm)
    - [Unofficial Amp CLI Documentation](#unofficial-amp-cli-documentation)
    - [Official Amp Links](#official-amp-links)
    - [Contributing](#contributing)
      - [Contributors](#contributors)

<!-- CONTENT -->

### Integration with Common CLI Tools

Amp CLI can be seamlessly integrated with other command-line tools to enhance your workflow:

#### ps aux

```bash
ps aux > /tmp/psaux.txt && echo "identify processes consuming the most resources" && cat /tmp/psaux.txt | amp
```

#### whois

```bash
 echo "organize and condense the following whois information" && whois example.com | amp
```

#### curl

```bash
echo "convert the cache control max-age value from seconds to days, hours, minutes" $(curl -I https://example.com) | amp
```

```bash
echo "read the http headers and determine what the domains tech stack is." $(curl -Is https://example.com) | amp
```

#### npm

```bash
npm list --json && echo "identify outdated or vulnerable dependencies" | amp
```

### Unofficial Amp CLI Documentation

- [Amp CLI Docs](https://github.com/jdorfman/awesome-amp-cli/blob/main/amp_cli_docs.md)

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

[Thanks goes to these contributors](https://github.com/jdorfman/awesome-amp-cli/graphs/contributors)!
