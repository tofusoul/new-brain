# Obsidian MCP Plugin

## Overview
The **Obsidian MCP Plugin** is a powerful integration that connects AI assistants to your Obsidian vault through the Model Context Protocol (MCP). This plugin enables AI tools like [[Claude Code]] and [[OpenCode]] to directly access, search, and manipulate your vault contents with semantic understanding.

## Repository
- **GitHub**: https://github.com/aaronsb/obsidian-mcp-plugin
- **License**: MIT

## Key Features

### Core Functionality
- **MCP Integration**: Connects AI assistants to Obsidian vaults through Model Context Protocol
- **Semantic Graph Navigation**: AI can understand and traverse the relationships between notes
- **Content Operations**: Full read/write access to vault contents
- **Search Capabilities**: Advanced search across notes with semantic understanding

### Available MCP Tools
- **Vault Operations**: List, read, create, update, delete, search, and organize notes
- **Content Editing**: Window-based editing with fuzzy matching, append, patch operations
- **Graph Navigation**: Explore note connections, backlinks, and forward links
- **Metadata Management**: Access frontmatter, tags, and note properties
- **Dataview Integration**: Execute DQL queries for structured data retrieval
- **Obsidian Bases**: Full integration with Obsidian Bases for structured data management

## Installation & Setup

### Requirements
- Obsidian v1.0.0 or higher
- MCP-compatible AI assistant (Claude Desktop, etc.)
- Community plugins enabled in Obsidian

### Configuration
1. Install the plugin through Obsidian Community Plugins
2. Enable MCP server in your AI assistant configuration
3. Configure the vault path and connection settings

## Integration with AI Tools

### Claude Code Integration
- Seamless vault access for AI development workflows
- Automated note organization and content management
- Real-time file operations with link preservation

### OpenCode Integration
- Enhanced AI capabilities for knowledge management
- Direct vault access through MCP tools
- Intelligent content creation and linking
- [[Obsidian Bases]] support for structured data operations

## Benefits

### For Knowledge Management
- **Automated Organization**: AI can help restructure and organize notes
- **Enhanced Search**: Semantic search capabilities beyond simple text matching
- **Content Creation**: AI can create well-linked notes in appropriate PARA categories

### For Development Workflows
- **Code Documentation**: AI can generate and update documentation
- **Project Management**: Integration with task management and project notes
- **Knowledge Base**: AI can query and utilize the vault as a knowledge base

## Usage Examples

### AI-Assisted Note Creation
1. AI analyzes existing content structure
2. Creates new notes with appropriate linking
3. Organizes content according to [[PARA Methodology]] structure

### Content Management
1. AI searches for related content across the vault
2. Identifies opportunities for better organization
3. Performs restructuring operations while preserving links
4. Manages [[Obsidian Bases]] for structured data operations

## Technical Details

### MCP Protocol Support
- Standard MCP tool definitions
- Resource-based architecture
- Asynchronous operations support

### Bases Integration Support
- **List Bases**: Access all `.base` files in the vault
- **Read Base Configuration**: Retrieve YAML configuration and view definitions
- **Create Bases**: Generate new bases with custom views, filters, and formulas
- **Query Data**: Execute filters and queries on vault notes using base expressions
- **View Operations**: Retrieve table/card view data with pagination and sorting
- **Export Functionality**: Export base data to CSV, JSON, or Markdown formats
- **Formula Evaluation**: Test and validate base formulas and expressions

## Related Tools
- [[Claude Code]]: AI development environment with MCP support
- [[OpenCode]]: AI-powered code assistant with vault integration
- [[AI]]: General AI tools and models information
- [[PARA Methodology]]: Organization structure for the vault
- [[Obsidian Bases]]: Structured data management system

## Future Enhancements
- Enhanced semantic search capabilities
- More sophisticated graph analysis tools
- Integration with additional AI models and platforms
- Advanced [[Obsidian Bases]] operations and analytics