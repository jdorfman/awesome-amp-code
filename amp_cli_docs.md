# Unofficial Amp CLI Documentation

---

[Amp](https://ampcode.com) is an AI coding agent, in research preview from Sourcegraph. This is the CLI for Amp; you can also use [Amp in VS Code](https://marketplace.visualstudio.com/items?itemName=sourcegraph.amp).

## Table of Contents

- [Unofficial Amp CLI Documentation](#unofficial-amp-cli-documentation)
  - [Table of Contents](#table-of-contents)
  - [Installation](#installation)
  - [Getting Started](#getting-started)
  - [Usage Modes](#usage-modes)
    - [Interactive Mode](#interactive-mode)
    - [Non-Interactive Mode](#non-interactive-mode)
  - [Authentication](#authentication)
    - [Web-Based Login](#web-based-login)
    - [API Key Authentication](#api-key-authentication)
      - [Connected Mode (Default)](#connected-mode-default)
      - [Isolated Mode](#isolated-mode)
  - [Command Line Options](#command-line-options)
  - [Environment Variables](#environment-variables)
  - [Configuration](#configuration)
    - [Allowing Terminal Commands](#allowing-terminal-commands)
  - [Tool Usage](#tool-usage)
  - [Advanced Features](#advanced-features)
    - [History Navigation](#history-navigation)
    - [File Mentions](#file-mentions)
    - [Debugging](#debugging)
  - [Troubleshooting](#troubleshooting)
    - [Node.js Version](#nodejs-version)
    - [Authentication Issues](#authentication-issues)
    - [Out of Credits](#out-of-credits)
  - [Requirements](#requirements)

## Installation

Install the Amp CLI globally using your preferred package manager:

```bash
npm install -g @sourcegraph/amp
```

Or with Yarn:

```bash
yarn global add @sourcegraph/amp
```

Or with pnpm:

```bash
pnpm add -g @sourcegraph/amp
```

## Getting Started

After installation, you can start using Amp CLI immediately:

```bash
amp
```

On first run, Amp will guide you through the authentication process.

## Usage Modes

### Interactive Mode

Interactive mode provides a conversational interface where you can have a dialogue with Amp:

```bash
amp
```

In interactive mode:

- Type your questions or commands at the prompt (`>`)
- Use `\` followed by `Enter` to insert newlines, or use `Shift+Enter` in supported terminals
- Press `Ctrl+C` to interrupt the agent or exit
- Type `help` to see what Amp can help you with
- Use arrow keys or Ctrl+P/Ctrl+N to navigate through message history
- Use PageUp and PageDown to jump directly in history
- Type @ followed by a pattern to fuzzy-search and mention files (use Tab/Shift+Tab to navigate results)

### Non-Interactive Mode

You can use Amp in non-interactive mode by piping content to it:

```bash
echo "commit all my unstaged changes" | amp
```

Or by using input/output redirection:

```bash
amp < prompt.txt > output.txt
```

## Authentication

Amp CLI supports two authentication methods:

### Web-Based Login

By default, Amp uses a web-based login flow:

1. Run `amp` for the first time
2. A browser window will open to authenticate with ampcode.com
3. After successful authentication, you can continue using Amp CLI

### API Key Authentication

You can also authenticate using API keys:

#### Connected Mode (Default)

1. Go to [ampcode.com/settings](https://ampcode.com/settings)
2. Copy your API key
3. Set it as an environment variable:

```bash
export AMP_API_KEY=your_amp_api_key_here
```

#### Isolated Mode

Isolated mode requires an Anthropic API key:

1. Get an API key from [Anthropic](https://console.anthropic.com/settings/keys)
2. Set it as an environment variable:

```bash
export ANTHROPIC_API_KEY=your_anthropic_api_key_here
```

3. Run Amp in isolated mode:

```bash
amp --isolated
```

## Command Line Options

Amp CLI supports the following options:

| Option               | Description                                                          |
| -------------------- | -------------------------------------------------------------------- |
| `-h, --help`         | Show help information                                                |
| `-v, --version`      | Show version information                                             |
| `--isolated`         | Run in isolated mode (requires ANTHROPIC_API_KEY)                    |
| `--notifications`    | Enable sound notifications (enabled by default in interactive mode)  |
| `--no-notifications` | Disable sound notifications                                          |
| `--color`            | Enable color output (enabled by default when stdout/stderr are TTYs) |
| `--no-color`         | Disable color output                                                 |
| `--log-level`        | Set log level (debug, info, warn, error)                             |
| `--log-file`         | Set log file location                                                |

## Environment Variables

| Variable            | Description                                            |
| ------------------- | ------------------------------------------------------ |
| `AMP_API_KEY`       | API key for connected mode                             |
| `AMP_URL`           | URL of the Amp server (default is https://ampcode.com) |
| `ANTHROPIC_API_KEY` | Required for isolated mode                             |
| `ANTHROPIC_API_URL` | Custom Anthropic API endpoint (optional)               |
| `AMP_LOG_LEVEL`     | Set log level                                          |
| `AMP_LOG_FILE`      | Set log file location                                  |

## Configuration

Amp CLI stores configuration in a settings file located at:

- Linux/macOS: `~/.config/amp/settings.json`
- Windows: `%APPDATA%\amp\settings.json`

### Allowing Terminal Commands

To allow specific terminal commands to run without confirmation, add them to the allowlist in your settings file:

```json
{
	"amp.commands.allowlist": ["git status", "ls -la"]
}
```

## Tool Usage

Amp can use various tools to help with your tasks. When Amp wants to use a tool (like running a terminal command), it will ask for your confirmation:

```
Amp wants to run: git status

Allow this command? [y/n/!]
```

Options:

- `y`: Allow this command once
- `n`: Reject this command
- `!`: Allow and add to allowlist (won't ask again for this command)

## Advanced Features

### History Navigation

Amp CLI allows you to navigate through your message history:

- Use the arrow keys or Ctrl+P/Ctrl+N to navigate through adjacent messages in history
- PageUp and PageDown keys jump directly in the history regardless of cursor position
- Your current draft is available at the end of the history
- Press Ctrl+C or Esc to cancel and return to your draft

### File Mentions

You can quickly reference files in the CLI by using the file mention feature:

- Type @ followed by a pattern to start fuzzy-searching for files
- Use Tab or Shift+Tab to navigate through the search results
- Press Enter to confirm and insert the file mention

### Debugging

For debugging purposes, you can use:

```bash
amp --log-level debug --log-file amp.log
```

To see available tools (for debugging):

```bash
amp --debug-show-tools
```

## Troubleshooting

### Node.js Version

Amp CLI requires Node.js v22 or higher. If you encounter errors, check your Node.js version:

```bash
node --version
```

### Authentication Issues

If you're having trouble with web-based authentication, try using the API key method described in the [Authentication](#authentication) section.

### Out of Credits

If you see an "Out of free credits" message, visit [ampcode.com/settings](https://ampcode.com/settings) to upgrade your account.

## Requirements

- Node.js v22 or higher
- Internet connection (for connected mode)
- Anthropic API key (for isolated mode)