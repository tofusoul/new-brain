---
id: Computer_Setup
aliases:
  - Computer Setup
tags: []
title: Computer Setup
---
These are the things I do on most computers to make my time on it happier

- [>]  Assuming the desktop is based on [[Universal Blue]]

# What I do after OS install 
- [x] update OS 
# Keymaps 
- [x] map escape to caps lock
- [x] map workspace keys for jumping between desktops 
# Applications
- [x] install [[Zen Browser]]
	- [x] sign in for Firefox sync
- [ ]
- [x] Install and Setup Neovim
	- [>]  in [[Universal Blue|ublue]] use homebrew to install neovim
	- 
	- [ ] 
	- [ ] 
## CLI
- [x] install `starship` for prompts
- [x] install `chezmoi` to pull and manage dot files
- [x] [install](https://carapace-sh.github.io/carapace-bin/install.html) `carapace` for completion
- [ ] install `ripgrep` 
- [ ] install `fd`
- [ ] install `python3.10` for work app dev
  - thought about using containers for this, but it's still much nicer to use just venv 
 
# Gnome Config 
## Shell Extensions
- [x] desktop  cube
	- [ ] configure
- [ ] clipboard indicator
- [x] burn my window
	- [ ] set effect to tv glitch 
- [x] coverflow alt tab
	- [i] no config 
- [x] forge for windows tiling
	- [ ] configure
# Terminal
## Terminal Emulator
I like:
### [[WezTerm]]
- Lua config seems like a great idea
- has a session manager that can be scripted
- Tabs
- GPU accellerated
* ligatures
### [[Kitty]]
- Nice
- reliable
- ligatures
- easy to setup

## Shell 
### [[zsh]]
### [[ohmyzsh]]

### Starship prompt
> *It's basically how I would have designed my prompt if I could and have the time*

### Chezmoi
what I use to
# Neovim

\*\*

- [x] [[2022-10-15 Saturday]] #\@night copy the stuff that is general to all computers here from my notes on [Asus Vivo Book 14 Pro M3401QA](./Asus Vivo Book 14 Pro M3401QA.org) 

- Goals

Get my computer to a point where my mind can naturally flow in to it. i.e. Get my Computer back into happy

- Machines and their specific setups go in their page

- main computer [Asus Vivo Book 14 Pro M3401QA](./Asus Vivo Book 14 Pro M3401QA.org)

- [[Dill]]\'s Chromebook

- XPS13

-   Note taken on \[2020-09-17 Thu 10:08\]\
    Still like KDE plasma the best

- Nexus 6p

- Raspberry Pi

- Phone

- System

- Package Management

- [Dot Files](./dot_files.org)

- Gnome

- Keyboard shortcuts

need to install dconf-editor for lots of things to be configured

- Look and feel

-   Nice looking setup. Might have to try it <https://github.com/WillPower3309/dotfiles>

- Fonts I like

- Firacode

most used to it as a coding font. supports ligatures

- Theme

- Emacs

- Setup Doom Emacs

- Setup mu4e

mu4e hbzgavmsrtiulzmh

-   Consulted links
    -   --> this link is still the best <https://wiki.archlinux.org/index.php/Isync>
    -   <https://www.chrislockard.net/posts/2019-11-14-notes-on-configuring-mu4e-and-doom-emacs/>
    -   <https://gist.github.com/areina/3879626>
    -   <https://www.reddit.com/r/emacs/comments/8q84dl/tip_how_to_easily_manage_your_emails_with_mu4e/>
    -   <https://www.djcbsoftware.nl/code/mu/mu4e/Gmail-configuration.html>

- [x] Write up how to setup Mu4e 

1.  Setup mbsync and maildir install isync type out .mbsyncrc with gmail credentials <https://wiki.archlinux.org/index.php/Isync>
2.  Index the maildir install mu and run `$ mu index --maildir=~/.mail/gmail`
3.  Configure Doom emacs
    -   add this line in email section of init.el `(mu4e +gmail)`
    -   add the configuration in config.el as <https://www.chrislockard.net/posts/2019-11-14-notes-on-configuring-mu4e-and-doom-emacs/>
4.  refresh doom `.emacs.d/bin/doom refresh`

- Set Firacode up for emacs

trying

-   [firacode\'s instructions](https://github.com/tonsky/FiraCode/wiki/Emacs-instructions)

I used the second set of instructions which effectively created a firacode mode

-   didn\'t work. use these instrucitons instead: much easier and works: `(pretty-code +fira)` <https://www.reddit.com/r/emacs/comments/fenvti/how_can_i_add_font_ligatures_to_doom_emacs/fjswqg7/>

- Configure Autosave when leaving focus

``` elisp
(defun save-all ()
    (interactive)
    (save-some-buffers t))
(add-hook 'focus-out-hook 'save-all)
```

- [x] Add sensible doom emacs shortcut for org-toggle-narrow-to-subtree [[keys]] 

- Web

- Firefox

- Google Codes

  ----------- -----------
  7416 2998   7038 3707
  2872 4530   8591 6475
  7304 6394   0000 9346
  8356 4956   5043 8944
  7119 6637   2577 7464
  ----------- -----------

- Google Chrome

Don\'t like chrome nowadays. don\'t like google nowadays

- Application

- Shell Applications

- bat

does a way better job at showing text files than less

- fx

browse json

- speed-test

report the speed of the computer

- Emacs

more than an editor

- Video Player: VLC

- Dropbox

- File Manager

- Ranger

I like ranger

- Colour picker

- [ ] Scheduling Software
-   org-mode is great for this

- Gimp
- Mypaint
- Inksacpe
- Scribus
- Dropbox
- Video Player: VLC
- PDF/zathura
- Drawing: My Paint
- E-books
Calibre and foliate <https://www.omgubuntu.co.uk/2019/05/foliate-ebook-reader-linux>

htop

- Speedcrunch

- Spotify

<https://github.com/khanhas/spicetify-cli/>

- Application Stack

- elm

front end. 0.19 took a while to settle. frankly sucked at the start. I am ready to head back into building things with elm.

-   tool stack seems broken

- rust

rustacions seems to produce good software

- haskell

maybe. still seems hard.

- python

good for scripting

- Lua

not sure how alive lua is, it was good when using love2d







