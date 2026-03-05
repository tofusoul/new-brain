---
id: Nushell
aliases: []
tags: []
date: "2024-02-19"
title: Nushell
---

> [!info] Data oriented shell written in rust, with a SQL like query utilities built in to the shell

- [usage tuorial](https://gofore.com/en/nushell-a-second-shell-to-supercharge-your-workflow/)
- [nice intro vid](https://www.youtube.com/watch?v=uJsZATwQ3R8)

## Nifty Basics
- `ctr-r` gives selectable history
  - although I am using [[Atuin]] for my history everywhere, so that doesn't matter as much
- `help commands | explore` lets you explore command in the help

## Important Differences in How Nushell Works
- Implicit returns
  ```py
  "Hello, World" == (echo "Hello, World")
  # => true
  ```
- Single return value per expression
- Every command returns a value
- Think of Nushell as a Complied Language
> [!info] every time something is run in Nushell:
> 1. the entire source is parsed
> 2. the entire source is evaluated 
  - Constants however are resolved during parsing.
- Variables are immutable by default
- Environment is Scoped
  - blocks control their own environment


## Data Commands
- `explore` when data is 

## Strings
- String interpolations are done with brackets and dollar signs
```py
> let name = "Alice"
> $"greetings, ($name)!"
greetings, Alice!
```
## Custom Commands
```py
def func []{
  something
  something-else --now
}
```
- if you want the commands executed in here to change the current shell's variables use the `--env flag` i.e.:
  * 
