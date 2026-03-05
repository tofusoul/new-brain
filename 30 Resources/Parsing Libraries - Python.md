---
Type: Resource
tags: [resource, python, parsing, libraries, programming]
---

# Parsing Libraries - Python

**Last Updated:** 2024-02-15

## Overview
A parser is a function from strings to a list of pairs of things and strings.

## Python Parsing Libraries

### Lark
**Approach:** Grammar-based parser generation

**How it works:**
- Write grammar definition in separate mini-language as a string
- Parser generated for you (rather than writing grammar in Python)

**Advantages:**
- Speed
- Ability to use different parsing algorithms
- Clean separation of grammar and implementation

### Pyparsing
**Approach:** Combinator parsing

**Characteristics:**
- Combinator approach
- Less cleanly implemented than Lark
- Scattered documentation
- More built-in functionality for certain parsing tasks

**Best for:** When you need lots of built-in utilities

### Parsy
**Repository:** https://github.com/python-parsy/parsy

**Status:** Seems inactive but maybe a solved problem with stable implementation

**Characteristics:**
- Combinator approach
- Similar to other combinator parsers
- Stable implementation

### FuncParserLib
**Approach:** Functional parsing

**Similar to:** Parsy

**Differences from Parsy:**
- Normally uses separate tokenization phase
- Lacks convenience of `generate()` method for creating parsers

**Best for:** When you want fine-grained control over tokenization

## Parsing Techniques

### Progressive Descent
Top-down parsing technique

### PEG (Parsing Expression Grammar)
A more expressive alternative to regular expressions, widely used in parsing

### BNE
[Document needed]

## Related Resources
- [[Python]] - Programming language
- [[Lark]] - Specific parser
- [[Regular Expressions]] - Alternative for simple parsing
- [[Compilers]] - More advanced parsing theory

## Notes
- Lark is recommended for most use cases due to speed and flexibility
- Pyparsing has more utilities but less clean implementation
- Parsy is stable but inactive
- FuncParserLib gives more control over tokenization

---
*Last updated: 2025-02-01*
