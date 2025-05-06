<div align="center">

<!-- title -->

<!--lint ignore no-dead-urls-->

# Awesome Amp CLI [![Awesome](https://awesome.re/badge.svg)](https://awesome.re) [![lint](https://github.com/jdorfman/awesome-amp-cli#/actions/workflows/lint.yaml/badge.svg)](https://github.com/jdorfman/awesome-amp-cli#/actions/workflows/lint.yaml)

<!-- subtitle -->

An unofficial curated list of resources for Amp CLI, an AI coding agent by Sourcegraph

<!-- image -->

<a href="" target="_blank" rel="noopener noreferrer">
  <img src="https://private-user-images.githubusercontent.com/398230/440639830-aaff0ad1-a4b5-4ac8-a58b-e7dfb02ec64a.jpg?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDY1MDY3OTYsIm5iZiI6MTc0NjUwNjQ5NiwicGF0aCI6Ii8zOTgyMzAvNDQwNjM5ODMwLWFhZmYwYWQxLWE0YjUtNGFjOC1hNThiLWU3ZGZiMDJlYzY0YS5qcGc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwNTA2JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDUwNlQwNDQxMzZaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT05YzM2YTJmNzcwNjdlMmMzZjQyZjFmYjg2YjkxMWY2MmE0MzI4OGQ1YzQ5OThlODJlZTlkODRmYmVjNDVlOGU0JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.7VvP5EppCE0uAZ5ZKB7zvmx6sUOjX87jeBjEDad51iY" />
</a>

<!-- description -->

</div>

<!-- TOC -->

## Contents

- [Awesome Amp CLI  ](#awesome-amp-cli--)
  - [Contents](#contents)
  - [Integration with Common CLI Tools](#integration-with-common-cli-tools)
    - [ps aux](#ps-aux)
    - [whois](#whois)
    - [curl](#curl)
    - [npm](#npm)
  - [Official Amp Links](#official-amp-links)
  - [Contributing](#contributing)
    - [Contributors](#contributors)

<!-- CONTENT -->

## Integration with Common CLI Tools

Amp CLI can be seamlessly integrated with other command-line tools to enhance your workflow:

### ps aux

```bash
ps aux > /tmp/psaux.txt && echo "identify processes consuming the most resources" && cat /tmp/psaux.txt | amp
```

### whois

```bash
 echo "organize and condense the following whois information" && whois example.com | amp
```

### curl

```bash
echo "convert the cache control max-age value from seconds to days, hours, minutes" $(curl -I https://example.com) | amp
```

```bash
echo "read the http headers and determine what the domains tech stack is." $(curl -Is https://example.com) | amp
```

### npm

```bash
npm list --json && echo "identify outdated or vulnerable dependencies" | amp
```

## Official Amp Links

- [Amp](https://ampcode.com)
- [Amp CLI](https://www.npmjs.com/package/@sourcegraph/amp)
- [Amp for VS Code](https://marketplace.visualstudio.com/items?itemName=sourcegraph.amp)
- [Raising an Agent Podcast](https://ampcode.com/podcast)
- [Amp on X](https://x.com/ampcode)
- [How to Build an Agent](https://ampcode.com/how-to-build-an-agent)

## Contributing

[Contributions of any kind welcome, just follow the guidelines](contributing.md)!

### Contributors

[Thanks goes to these contributors](https://github.com/jdorfman/awesome-amp-cli/graphs/contributors)!
