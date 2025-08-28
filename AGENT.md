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

## Add link to Built With section

When `/builtwith` followed by a link is included in a prompt, you will add the link to the Built With section of the README.md file. If there is a numbered list of urls, create subagents to complete the tasks.

## Add link to @docs/amp_faq.md

When `/faq` followed by a link is included in a prompt, you will add the link to the @docs/amp_faq.md file in between `---` and `---` Place it above the last question. The update the Last Modified date
