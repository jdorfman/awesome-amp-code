# Agent Guidelines for awesome-amp-cli Repository

## Build, Lint & Test Commands

- Lint readme: `npx awesome-lint readme.md`
- Link check: `awesome_bot --allow-redirect --white-list https://github.com/jdorfman/awesome-amp-code,https://example.com readme.md`
- Node.js version: Use v21.6.0 (as specified in .tool-versions)

## Code Style Guidelines

- **Markdown Format**: Follow standard Markdown formatting for documentation
- **List Items**: Add items at the bottom of existing lists
- **Item Format**: `- [item name](https link) - Description beginning with capital, ending in period.`
- **Commits**: Always create a new branch for proposed changes
- **PR Process**: Check spelling and grammar before submitting
- **Code of Conduct**: All contributions must adhere to the Code of Conduct

## Project Structure

- Documentation is the primary focus of this repository
- Main content is in amp_cli_docs.md and readme.md
- CI pipeline uses awesome-lint and awesome_bot to validate content

## Subagents

- If the prompt is "1. Task 1, 2. Task 2", you MUST use subagents to accomplish the tasks

## Git Command Instructions

When `/git` is included in a prompt, you will exclusively use the following Git commands (each in a separate subagent AND in order) to help you accomplish the following tasks:

- `git add` - To stage files for commit
- `git --no-pager diff` - To view changes between commits or working directory and index
- `git commit` - To record changes to the repository (summarizing git status and git diff)
- `git push` - To push changes to the remote repository
- `gh pr create --fill` - Use GitHub CLI to create a pull request
