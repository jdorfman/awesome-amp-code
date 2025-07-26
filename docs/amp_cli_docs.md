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
  - [Command Line Options](#command-line-options)
  - [Commands](#commands)
  - [Environment Variables](#environment-variables)
  - [Examples](#examples)
  - [Configuration](#configuration)
    - [Settings Reference](#settings-reference)
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
  - [Last updated](#last-updated)

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

1. Go to [ampcode.com/settings](https://ampcode.com/settings)
2. Copy your API key
3. Set it as an environment variable:

```bash
export AMP_API_KEY=your_amp_api_key_here
```

## Command Line Options

Amp CLI supports the following options:

| Option                       | Description                                                          |
| ---------------------------- | -------------------------------------------------------------------- |
| `-V, --version`              | Output the version number                                            |
| `--visibility <visibility>`  | Set thread visibility (private, public, team)                       |
| `--notifications`            | Enable sound notifications (enabled by default when not in execute mode) |
| `--no-notifications`         | Disable sound notifications                                          |
| `--settings-file <value>`    | Custom settings file path (overrides the default location)          |
| `--log-level <value>`        | Set log level (error, warn, info, debug, audit)                     |
| `--log-file <value>`         | Set log file location                                                |
| `--dangerously-allow-all`    | Disable all command confirmation prompts (agent will execute all commands without asking) |
| `-x, --execute [message]`    | Use execute mode, optionally with user message. In execute mode, agent will execute provided prompt (either as argument, or via stdin). Only last assistant message is printed. Enabled automatically when redirecting stdout. |

## Commands

Amp CLI includes several subcommands for enhanced functionality:

| Command                    | Description                                                          |
| -------------------------- | -------------------------------------------------------------------- |
| `logout`                   | Log out by removing stored API key                                   |
| `login`                    | Log in to Amp                                                        |
| `threads`                  | Thread management commands                                           |
| `threads new`              | Create a new thread and print its ID                                |
| `threads continue`         | Continue an existing thread (uses last used thread if no ID provided) |
| `threads fork`             | Create a new thread by forking an existing one and print its ID     |
| `threads list`             | List all your threads with their titles and share status            |
| `threads share`            | Change thread visibility or share with support                      |
| `threads compact`          | Compact a thread by creating a summary to reduce token usage        |
| `tools`                    | Tool management commands                                             |
| `tools show`               | Show available tools                                                 |
| `doctor`                   | Generate a support bundle for troubleshooting                       |
| `update`                   | Update Amp CLI to the latest version                                |

## Environment Variables

| Variable            | Description                                                          |
| ------------------- | -------------------------------------------------------------------- |
| `AMP_API_KEY`       | API key for Amp (see https://ampcode.com/settings)                  |
| `AMP_URL`           | URL for the Amp service (default is https://ampcode.com/)           |
| `AMP_LOG_LEVEL`     | Set log level (can also use --log-level)                            |
| `AMP_LOG_FILE`      | Set log file location (can also use --log-file)                     |
| `AMP_SETTINGS_FILE` | Set settings file path (can also use --settings-file, default: ~/.config/amp/settings.json) |

## Examples

Start an interactive session:

```bash
amp
```

Start an interactive session with a user message:

```bash
echo "commit all my unstaged changes" | amp
```

Use execute mode (`--execute` or `-x`) to send a command to an agent, have it execute it, print only the agent's last message, and then exit:

```bash
amp -x "what file in this folder is in markdown format?"
```

Use execute mode and allow agent to use tools that would require approval:

```bash
amp --dangerously-allow-all -x "Rename all .markdown files to .md. Only print list of renamed files."
```

Pipe a command to the agent and use execute mode:

```bash
echo "commit all my unstaged changes" | amp -x --dangerously-allow-all
```

Execute a prompt from a file and store final assistant message output in a file (redirecting stdout is equivalent to providing `-x`/`--execute`):

```bash
amp < prompt.txt > output.txt
```

## Configuration

Amp can be configured using a JSON settings file located at `~/.config/amp/settings.json`. All settings use the "amp." prefix.

Sample configuration:

```json
{
  "amp.notifications.enabled": true,
  "amp.mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": [
        "@modelcontextprotocol/server-filesystem",
        "/path/to/allowed/dir"
      ]
    }
  },
  "amp.tools.disable": [
    "browser_navigate",
    "builtin:edit_file"
  ],
  "amp.commands.allowlist": [
    "git status",
    "ls -la",
    "npm run build"
  ],
  "amp.commands.strict": false,
  "amp.dangerouslyAllowAll": false,
  "amp.git.commit.coauthor.enabled": true,
  "amp.git.commit.ampThread.enabled": true,
  "amp.updates.autoUpdate.enabled": true
}
```

### Settings Reference

- **`amp.notifications.enabled`**: Enable system sound notifications when agent completes tasks
- **`amp.mcpServers`**: Model Context Protocol servers to connect to for additional tools
- **`amp.tools.disable`**: Array of tool names to disable. Use 'builtin:toolname' to disable only the builtin tool with that name (allowing an MCP server to provide a tool by that name).
- **`amp.commands.allowlist`**: Array of shell commands that can be executed without confirmation
- **`amp.commands.strict`**: Enable strict command validation. When disabled, certain commands like Bazel get relaxed path validation.
- **`amp.dangerouslyAllowAll`**: Disable all command confirmation prompts (agent will execute all commands without asking)
- **`amp.git.commit.coauthor.enabled`**: Enable adding Amp as co-author in git commits
- **`amp.git.commit.ampThread.enabled`**: Enable adding Amp-Thread trailer in git commits
- **`amp.updates.autoUpdate.enabled`**: Enable automatic updates of the Amp CLI

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

- Use the arrow keys or `Ctrl+P`/`Ctrl+N` to navigate through adjacent messages in history
- `PageUp` and `PageDown` keys jump directly in the history regardless of cursor position
- Your current draft is available at the end of the history
- Press `Ctrl+C` or `Esc` to cancel and return to your draft

### File Mentions

You can quickly reference files in the CLI by using the file mention feature:

- Type `@` followed by a pattern to start fuzzy-searching for files
- Use Tab or `Shift+Tab` to navigate through the search results
- Press `Enter` to confirm and insert the file mention

### Debugging

For debugging purposes, you can use:

```bash
amp --log-level debug --log-file amp.log
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
- Internet connection

## Last updated

2025-07-25