---
id: Obsidian
aliases: []
tags: []
date: "2024-01-08"
title: Obsidian
---
*very popular note taking app. Considering  switching to obsidian. seems pretty powerful.* 
- [x] look at the pros and cons
    - [x] vs [[Telekasten]]
    - [x] vs [[Logseq]]

# Formatting
## Callouts
```markdown
> [!note] Title 
> content
```
### Possible Callout Types
- `> [!note]`
> [!note] note
- `> [!abstract]`
> [!abstract] abstract
- `> [!info]`
> [!info] info
- `> [!todo]`
> [!todo] todo
- `> [!tip]`
> [!tip] tip
- `> [!success]`
> [!success] success
- `> [!question]`
> [!question] question
- `> [!failure]`
> [!failure] failure
- `> [!danger]`
> [!danger] danger
- `> [!bug]`
> [!bug] bug
- `> [!example]`
> [!example] example
- `> [!quote]`
> [!quote] quote

# Obsidian Compared with other things I have tried#p

## VS [[Telekasten]]
**Obsidian Pros**
- Obsidian has a mobile app that works pretty well. So I can get the notes on the go 
- Obsidian is more feature complete e.g.:
  - Telekastan is a bit too simplistic
  - Calendar view
  - Plugins
    * Dataview 
    * Templatr seems really good. But a bit of a learning curve
    * Periodic notes makes modeling a workflow better

** Telekastan Pros**
- Obsidian is way more complex, lots more to learn and lots more design decisions to make and be tempted by.

## VS [[Logseq]]
**Obsidian Pros**
- the plugin echo system in Obsidian is way more mature and the quality seems better
- I like the integration with standard markdown in obsidian more than in Logseq
  * e.g. Logseq tasks are marked by `TODO` and `DONE` etc, like they are in orgmode. Which Is a bit more of a visual clutter than I like.
  * Markdown rendering checkboxes are great. 
- Neovim support is way better in obsidian, through both markdown and obsidian.nvim
**Logseq Pros**
- Logseq is Open Source
- Logseq is an outliner instead of markdowns, which I actually like more as a data Structure 

# Plugins
## [[Obsidian Dataview]]
[[Obsidian Templater]]

# Queries
## Obsidian TODOs in Other Notes
```dataview
TASK FROM ""
WHERE contains(tags, "#Obsidian") AND !completed AND !checked
GROUP BY file.link
```
- [x] ☝obsidian Tasks querie #Obsidian/Dataview/Queries ✅ 2024-05-27

## Obsidian Done
``` dataview
TASK FROM ""
WHERE contains(tags, "#Obsidian")
WHERE checked
WHERE completed
GROUP BY file.link
```
- [x] ☝obsidian work done query #Obsidian/Dataview/Queries ✅ 2024-05-27


