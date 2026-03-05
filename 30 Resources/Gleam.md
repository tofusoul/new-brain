---
id: Gleam
aliases: []
tags: []
date: "2024-03-12"
title: Gleam
---

A promising new programming language, inspired by all the interesting languages I have been fascinated by (e.g. Elm, Elixir, Rust, Go etc. )

It's built on the Beam virtual machine. Which is built on the following principles:

- Everything is a process.
- Processes are strongly isolated.
- Process creation and destruction is a lightweight operation.
- Message passing is the only way for processes to interact.
- Processes have unique names.
- If you know the name of a process you can send it a message.
- Processes share no resources.
- Error handling is non-local.
- Processes do what they are supposed to do or fail.

However, it's simple like go, and lua, but has the awesome ml type system like Elm and Ocaml

# Learn Gleam
- Nice [overview video](https://www.youtube.com/watch?v=yHe_wzFg4W8) from one of the core contributors
- [ ] try a building a todo app with [this tutorial](https://gleaming.dev/articles/building-your-first-gleam-web-app/)


## Installation
> [!info] on Bluefin Linux
> all you need to do is:
```bash
brew install gleam
```
which is great!
```
