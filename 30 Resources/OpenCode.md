# OpenCode Configuration for Obsidian Notes Repository

## Overview
This repository is an Obsidian vault and primarily contains Markdown notes. The following guidelines help maintain consistency while respecting Obsidian's features.

## File Management
- **Naming Conventions**: Obsidian handles filenames with spaces well for `[[Wikilinks]]`. While descriptive names are good, strict hyphenated-lowercase is not required if it conflicts with your linking style. Consistency is key. (e.g., `My New Note.md` or `my-new-note.md` are both acceptable).
- **Directory Structure**: Organize notes into logical subdirectories.
- **Attachments**: Store images or other attachments in a relevant subdirectory, like `attachments/` or as configured in your Obsidian settings.

## Markdown Style
- **Formatting**: Use standard Markdown syntax, compatible with Obsidian's rendering.
- **Headings**: Use `#` for titles, `##` for major sections, and `###` for sub-sections.
- **Links**:
    - **Internal Links**: Prefer Obsidian's `[[Wikilink]]` format for internal links (e.g., `[[My Other Note]]`).
    - **External Links**: Use descriptive link text: `[useful link text](URL)` instead of just the URL.
- **Code Blocks**: For any code snippets, use appropriate language identifiers for syntax highlighting.

## Content Guidelines
- **Atomic Notes**: Prefer smaller, focused notes over monolithic documents where appropriate.
- **Linking**: Actively link between related notes using `[[Wikilinks]]` to create a connected knowledge base.
- **Tags/Keywords**: Use `#tags` for organization and easier searching within Obsidian.
- **Frontmatter**: Utilize YAML frontmatter for metadata like aliases, tags, creation dates, etc. (e.g., `aliases: [alias1, alias2]`).

## Commands
- As this is an Obsidian notes repository, there are no standard build, lint, or test commands.
- Version control is managed with Git. Commit messages should be clear and describe the changes made to the notes.

## Future Considerations
- If more structured data or scripts are introduced, this file should be updated with relevant commands and style guides.
## Obsidian MCP Integration
OpenCode is configured to work with the [[Obsidian MCP Plugin]], providing seamless access to the vault through Model Context Protocol for AI-assisted development workflows.

### Integration Benefits
- Direct vault access through MCP tools
- Automated content organization and linking
- Enhanced AI capabilities for knowledge management
- Real-time collaboration between AI and vault operations