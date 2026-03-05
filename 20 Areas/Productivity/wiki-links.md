# wiki-links

**Type**: Resource  
**Created**: 2025-09-24  
**Last Updated**: 2025-09-24  

## Overview

Wiki links are the primary method for connecting notes in [[Obsidian]]. They use the format `[[keyword]]` to create bidirectional links between related concepts.

## Syntax

### Basic Wiki Links
```
[[Note Title]]           # Link to note with exact title
[[Note Title|Display Text]]  # Link with custom display text
[[Note Title#Heading]]   # Link to specific heading in note
```

### Examples
```
[[PARA Methodology]]                    # Exact title match
[[Customizing Opencode|Opencode Project]]  # Custom display text
[[Obsidian Setup#Automation Requirements]]  # Link to section
```

## Automation Rules

### When Creating Notes
1. **Extract keywords** from note content
2. **Scan existing notes** for matching titles/concepts
3. **Add wiki links** to most relevant connections
4. **Prioritize** by:
   - Exact title matches first
   - Semantic relevance
   - Recent access frequency
   - PARA category relationships

### Link Selection Criteria
- **Relevance**: Direct conceptual relationship
- **Specificity**: Prefer specific over general concepts
- **Recency**: Recently modified notes get priority
- **Connections**: Notes with many existing links

### Best Practices
1. **Limit links**: 3-7 relevant links per note typically
2. **Be specific**: Use exact titles when possible
3. **Bidirectional**: Ensure relationships make sense in both directions
4. **Maintain consistency**: Use same link format throughout

## Implementation in Opencode

### Auto-Linking Process
1. **Content Analysis**: Identify key concepts in new note
2. **Existing Note Scan**: Search ~/notes/ for related content
3. **Relevance Scoring**: Rank potential links by relevance
4. **Link Insertion**: Add top N links to note content
5. **User Review**: Allow user to approve/modify auto-links

### Keyword Extraction
- Look for capitalized terms, proper nouns
- Identify technical terms and jargon
- Extract project names, file paths, commands
- Consider PARA categories and tags

### Context Awareness
- Consider note's PARA category
- Weight links within same category higher
- Prioritize cross-category links when semantically relevant
- Account for user's recent work context

## Related Notes

- [[Obsidian Setup]] - Main vault configuration
- [[Customizing Opencode for Personal Workflow]] - Automation project
- [[PARA Methodology]] - Organization system using wiki links

---

*Tags: #wiki-links #Obsidian #automation #notetaking #linking*