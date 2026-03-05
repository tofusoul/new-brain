---
id: Obsidian Nvim
aliases: []
tags: []
---


- website [obsidian-nvim](https://github.com/epwalsh/obsidian.nvim)
- [youtube intro](https://www.youtube.com/watch?v=5ht8NYkU9wQ)

## Quirks
- The link generation does  a weird zettlekasten thing with a separate id. Need to configure with the following to get a simple text link. 

```lua
    note_id_func = function(title)
      return title
    end,
```
- The auto add title as alias thing in the copypasta config
