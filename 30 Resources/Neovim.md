---
id: Neovim
aliases:
  - neovim
tags: []
author: Andrew Shih
title: Neovim
---
- [ ] checkout and integrate [flash.nvim](https://github.com/folke/flash.nvim) [[Neovim]] #neovim
- [ ] checkut and integrate some of these [plugins](https://www.reddit.com/r/neovim/comments/14f0t0n/your_favourite_neovim_plugins/) into my [[Neovim]]
- [ ] readup on #neovim terminal with the help, to see what I can do with it
    - [ ] maybe check out toggle term


# Plugins I use
- [x] [[Telescope]]
- [x] [[Telekasten]]
	-  Depreciating, I am using [[Obsidian]], which has most of the features I need including syncing. 
	- 
- [ ] make macros nicer(https://alpha2phi.medium.com/neovim-101-macros-and-registers-5e08781d9d27)

- [ ] setup [himalaya email](https://github.com/soywod/himalaya) with [[Neovim]] 
- [ ] setup Write-Good for markdown and plain txt
- [ ] get a surround plugin going
- [ ] ~~setup neovim for [ipynb](https://alpha2phi.medium.com/neovim-pde-for-data-science-e1cc4c82a424)~~ doesn't seem like there is a very good solution.

## Fix
- [x] `<S-K>` for lsp config isn't working
- [ ] can't get autoformat to work in python for some reason

## My Config
- tried nvchad didn't liek it too much 
- tried Lunavim, worked well, but didn't really understand what was going on
    - I like how it works,
    - but I need to understand exactly what my config is doing.

- Using TJ Dvere's kickstart conf worked:
    - Had to modularize my config, was too hard to follow what is going on in that config, so:
    - built a config based on [this video](https://www.youtube.com/watch?v=J9yqSdvAKXY)
    - Using [lazy.nvim](https://www.youtube.com/watch?v=2ahI8lYUYgw) instead of packer
	- kickstart uses lazy now too
    - LSP setup [lsp](https://www.youtube.com/watch?v=lpQMeFph1RE)
    - setup [autocomplete and snippets](https://www.youtube.com/watch?v=h4g0m0Iwmys&list=PLsz00TDipIffxsNXSkskknolKShdbcALR&index=3&t=209s)
    - using [this post](https://pythops.com/post/the-ultimate-python-development-environment.html) to setup the python environment
- [x] setup up ruff in the neovim setup again 
- **To get to the base build I want:**
- [x] setup the base build 
- [x] <https://github.com/nvim-orgmode/orgmode> 
    - stopped using orgmode, it's not that nice in neovim
## Keys
- `shift-v` select lines
- [keys cheatsheet](https://devhints.io/vim)
- 
## Learn Neovim
- [ ] check out [neovim lua guide](https://github.com/nanotee/nvim-lua-guide)
- [ ] rtfm 


## Plugins to Try
- [gkeep](https://github.com/stevearc/gkeep.nvim) 
- [nvim-dap](https://github.com/mfussenegger/nvim-dap)
- [nvim-dap-ui](https://github.com/rcarriga/nvim-dap-ui)
- [toggleterm](https://github.com/akinsho/toggleterm.nvim)
- [vim-illuminate](https://github.com/RRethy/vim-illuminate)
- [structlog](https://github.com/Tastyep/structlog.nvim)
- [firenvim](https://github.com/glacambre/firenvim)
- config
## Try Building an Simple Plugin with pyenvim
- [pynvim](https://github.com/neovim/pynvim) support for python plugin in nvim

## RegEx Search and replace
- `:%s/old/new/g`
- `:%` selects all
- `:%s` substitutes

- `:%s/old/new/g`


## Nice Tricks
- to append a block of text to the end another set of lines [source](https://stackoverflow.com/questions/20050070/in-vim-how-do-i-paste-a-column-of-text-to-the-end-of-irregular-length-lines?lq=1):
    - block-wise select (`ctrl-v`) the first block (you want to paste later), and press `y`
    - line-wise select (`shift-v`) the lines you want to paste to, press command `:right` to right aligh
    - move cursor to the end of the first line(`$`), paste the yanked text
    - gv re-select the lines to be pasted, press `:left`

- `:%s/$/\=line('.')-1` add the line number minus 1 into the end of the line
- `:put=join(map(range(5), 'v:val+1'), ' potato, ')` generates '1 potato, 2 potato, 3 potato, 4 potato, 5'

## Registers
- [ ] learn vim registers
