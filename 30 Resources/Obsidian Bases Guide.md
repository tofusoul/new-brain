# Obsidian Bases: Complete Guide and Reference

## Overview
**Obsidian Bases** provides database-like functionality for your Obsidian vault, allowing you to create structured data tables using existing notes as data sources, with filtering, sorting, and multiple view types.

**Current Implementation**: Your vault uses the Semantic Vault MCP plugin with expression-based syntax. There are two different syntax formats in use:

1. **Expression-based format** (used in Beverages.base) - RECOMMENDED
2. **Property-based format** (used in Books.base) - LEGACY/ALTERNATIVE

**Key Finding**: The expression-based format is more reliable and consistent. Stick to this format for new bases.

## Key Issues with Previous Implementation

### ❌ Incorrect Syntax (Causing Parse Errors)
```yaml
filters:
  - property: "category"
    operator: "="
    value: "beer"
```

### ✅ Correct Syntax (Expression-Based)
```yaml
filters:
  and:
    - "frontmatter.category == \"beer\""
```

## Core Syntax Structure

### RECOMMENDED: Expression-Based Format (Beverages.base style)
```yaml
name: My Collection
filters:
  and:
    - file.inFolder("30 Resources/My Folder")
    - frontmatter.category != null

views:
  - type: table
    name: All Items
    order:
      - frontmatter.title
      - frontmatter.category
    sort:
      - property: frontmatter.title
        direction: ASC
```

### ALTERNATIVE: Property-Based Format (Books.base style)
```yaml
filters:
  or:
    - file.tags.contains("book")
    - note["relevant notes"].contains(link("Books"))
    - '!note["book source"].isEmpty()'
properties:
  note.book source:
    displayName: book source
  note.priority:
    displayName: Priority Higher Better
views:
  - type: table
    name: Table
    order:
      - file.name
      - book source
    sort:
      - property: tags
        direction: ASC
```

**IMPORTANT**: The expression-based format is more reliable and consistent. Use this format for all new bases.

## Allowed Filter Expressions

### Comparison Operators
```yaml
filters:
  and:
    - "frontmatter.rating == 5"           # Equal to
    - "frontmatter.rating != 3"           # Not equal to
    - "frontmatter.rating > 4"             # Greater than
    - "frontmatter.rating >= 4"            # Greater than or equal
    - "frontmatter.rating < 3"             # Less than
    - "frontmatter.rating <= 3"            # Less than or equal
    - "frontmatter.category != null"       # Not null
```

### String Operations
```yaml
filters:
  and:
    - "frontmatter.title.contains(\"IPA\")"        # Contains substring
    - "frontmatter.title.startsWith(\"Thief\")"     # Starts with
    - "frontmatter.title.endsWith(\"Brewery\")"     # Ends with
```

### File Operations
```yaml
filters:
  and:
    - "file.inFolder(\"30 Resources/Beverages\")"   # In specific folder
    - "file.hasTag(\"beverage\")"                   # Has specific tag
    - "file.name != \"template\""                   # File name not equal
```

### Logical Operators
```yaml
filters:
  and:
    - "condition1"
    - "condition2"
  or:
    - "condition1"
    - "condition2"
```

## View Types and Configuration

### Table View
```yaml
views:
  - type: table
    name: "All Items"
    order:
      - "frontmatter.title"
      - "frontmatter.category"
      - "frontmatter.rating"
    sort:
      - property: "frontmatter.rating"
        direction: "DESC"    # ASC or DESC
```

### Card View
```yaml
views:
  - type: card
    name: "Featured Items"
    filters:
      and:
        - "frontmatter.rating >= 4"
    order:
      - "frontmatter.title"
      - "frontmatter.type"
    sort:
      - property: "frontmatter.rating"
        direction: "DESC"
```

## Supported Property Types

Based on working examples in your vault:

### String Properties
```yaml
# In note frontmatter:
title: "Thief Brewery IPA"
type: "India Pale Ale"
category: "beer"
producer: "Gebbie Family Brewery"
flavor_profile: "Bold hop character with citrus notes"

# In base filter:
- "frontmatter.title == \"Thief Brewery IPA\""
- "frontmatter.category == \"beer\""
- "frontmatter.flavor_profile.contains(\"citrus\")"
```

### Number Properties
```yaml
# In note frontmatter:
rating: 4.5
abv: 6.5
price: 6.99

# In base filter:
- "frontmatter.rating >= 4"
- "frontmatter.abv > 6.0"
- "frontmatter.price < 10"
```

### Date Properties
```yaml
# In note frontmatter:
consumed_date: 2024-02-26
date: 2024-02-26

# In base filter:
- "frontmatter.consumed_date != null"
- "frontmatter.date > \"2024-01-01\""
```

### Array Properties
```yaml
# In note frontmatter:
ingredients: ["Pale Malt", "Cascade Hops", "Yeast", "Water"]
tags: [ipa, craft-beer, thief-brewery]

# In base filter:
- "frontmatter.tags.contains(\"craft-beer\")"
- "frontmatter.ingredients.contains(\"Cascade\")"
```

## Complete Working Examples

### Beverages Base (Expression-Based - RECOMMENDED)
```yaml
name: Beverages Collection
filters:
  and:
    - file.inFolder("30 Resources/Beverages")
    - frontmatter.category != null
views:
  - type: table
    name: All Beverages
    order:
      - frontmatter.title
      - frontmatter.type
      - frontmatter.category
      - frontmatter.producer
      - frontmatter.rating
      - frontmatter.abv
      - frontmatter.serving_temperature
    sort:
      - property: frontmatter.title
        direction: ASC
  - type: table
    name: Beer Collection
    filters:
      and:
        - frontmatter.category == "beer"
    order:
      - frontmatter.title
      - frontmatter.producer
      - frontmatter.abv
      - frontmatter.rating
      - frontmatter.flavor_profile
      - frontmatter.serving_temperature
    sort:
      - property: frontmatter.rating
        direction: DESC
  - type: card
    name: Top Rated
    filters:
      and:
        - frontmatter.rating >= 4
    order:
      - frontmatter.title
      - frontmatter.type
      - frontmatter.producer
      - frontmatter.rating
      - frontmatter.flavor_profile
    sort:
      - property: frontmatter.rating
        direction: DESC
```

### Books Base (Property-Based - LEGACY)
```yaml
filters:
  or:
    - file.tags.contains("book")
    - note["relevant notes"].contains(link("Books"))
    - '!note["book source"].isEmpty()'
properties:
  note.book source:
    displayName: book source
  note.priority:
    displayName: Priority Higher Better
  note.rating (1-5):
    displayName: Rating
views:
  - type: table
    name: Table
    order:
      - file.name
      - book source
      - book author
      - fiction?
      - started
      - finished
      - book url
      - book genre
      - ISBN
      - est. read time (hrs)
      - language
      - pages
      - publisher
      - publish date
      - priority
      - tags
      - rating (1-5)
      - relevant notes
    sort:
      - property: tags
        direction: ASC
      - property: priority
        direction: ASC
      - property: rating (1-5)
        direction: DESC
    columnSize:
      note.book url: 105
      note.book genre: 110
      note.priority: 102
      note.tags: 169
    rowHeight: medium
```

## Common Errors and Solutions

### Error: "filters having keys that are not allowed"
**Cause**: Using property-based syntax instead of expression-based
**Solution**: Change from property/operator/value to expression format

### Error: "Unknown property in expression"
**Cause**: Property doesn't exist in note frontmatter
**Solution**: Ensure all referenced properties exist in your notes

### Error: "Invalid operator"
**Cause**: Using unsupported operators
**Solution**: Use only supported operators: `==`, `!=`, `>`, `>=`, `<`, `<=`, `contains`, `startsWith`, `endsWith`

### Error: "Unclosed string literal"
**Cause**: Improper quoting in expressions
**Solution**: Use proper escaping: `"frontmatter.title == \"IPA\""`

## Best Practices

### 1. Consistent Frontmatter
Ensure all notes in a base have consistent property names and types.

### 2. Folder Organization
Use specific folder filters to limit search scope and improve performance.

### 3. Progressive Complexity
Start with simple filters, then build complexity as needed.

### 4. Test Incrementally
Test each filter expression individually before combining with logical operators.

### 5. Documentation
Document your base structure and property conventions.

## Installation and Setup

### Option 1: Install Obsidian Bases Plugin
1. Go to `Settings` > `Community Plugins`
2. Disable `Safe Mode`
3. Click `Browse` and search for "Obsidian Bases"
4. Install and enable the plugin

### Option 2: Use Current MCP Implementation
Your current setup uses the Semantic Vault MCP plugin which provides base functionality with the expression-based syntax shown above.

## Related Resources
- [[Obsidian Bases]]: Plugin functionality
- [[Obsidian MCP Plugin]]: MCP integration
- [[Beverages.base]]: Fixed beverage collection base
- [[PARA Methodology]]: Organization structure