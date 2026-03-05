- Thoughts

- Used [Doom Emacs](./doom emacs.org) for a while.

- using [LunarVim](./LunarVim.org) config for [neovim](./neovim.org) now with [[neovide]] as a gui.

- regex search and replace

- `:%s/<some_pattern>/<replacement>/<options>`

- cool Movements to get into a habit of now

- `viw` selects the word, doesn\'t matter where you are in the word

- `fe` jumps to the next \'`e`\'

- `Fj` jumps backwards to the \'`j`\'

- `vi{` selects everything **inside** the  if you are not inside squirly brackets it will select the next ones

- `va(` selects everyting **including** the brackets

- `yi[` **yanks** everything inside the \[... \]

\*\*

- NAVIGATING OUTSIDE WORLD

- gF open file under cursor

- F open file in new window

- gF open file in new tab

- Commands

- `:` \' \' go to line number.

- HANDY TOGGLES

- `:set nu` number lines on.

- `:set nu!` number lines off.

- Basic Movements 

j h l k

- w = Move to the beginning of next word.

- e = Move to the end of next word

- b = Move to the beginning of the previous word.

- \$ = Move to the end of the line

- 0 = Move to the beginning of the line

- { = Move to the beginning

of the paragraph

- } = move to the end of the paragraph

- ( = Move to the beginning of the sentence

- ) = Move to the beginning of the sentence

- CTRL-\[ = escapes

- \[i\]G = go to line

- i = insert before

- a = append after

- o = insert below line

- O = insert above line

- yy = yanks a line

- yw = yanks a word

- gf = opens files under cursor in a new tab. mapped to gf

- Learning 

-   Check out [easymotion](https://github.com/easymotion/vim-easymotion/blob/master/doc/easymotion.txt)
-   Learn about [macros](https://vim.fandom.com/wiki/Recording_keys_for_repeated_jobs)
-   learn [vim regx](http://vimregex.com/)

<http://www.vimgolf.com/>

- Resources 

-   `vimtutor` command
-   `:help` in vim
-   <http://www.vimgolf.com/>
-   [vim key bindings](https://hea-www.harvard.edu/~fine/Tech/vi.html)

- ESCAPE CHAR

- `\` = escape char

- `\t` = tab

- `\n` = new line

- `\s` = white space

- SEARCH AND REPLACE

- `:%s/foo/bar/g` Find each instance of \'foo\' and replace it with \'bar\'

- `:%s/foo/bar/gc` same as above but require confirmation(g means global)

- WHEN SEARCHING

- ., \*, , \[, \], \^, and \$ are metacharacters.

- +, ?, \|, ,(, and ) must be escaped to use their special function.

- / is / (use backslash + forward slash to search for forward slash)

- i͡s tab, `\s` is whitespace

- `\n` is newline,

- i̊s CR (carriage return = Ctrl-M = ^M^)

- `` is used for repetition.

- /foo. will match foo and the two following characters. The  is not required on the closing } so /foo  will do the same thing.

- (foo) makes a back reference to foo.

- Parenthesis without escapes are literally matched. Here the  is required for the closing ).

- WHEN REPLACING

- i̊s newline,

- `\n` is a null byte (0x00).

- & is ampersand

- (& is the text that matches the search pattern).

- \\1 inserts the text of the first backreference.

- \\2 inserts the second backreference, and so on.

------------------------------------------------------------------------

TOGGLE CASE \~ = toggle case for char under cursor. g\~w = toggle case for word. g\~\~ = toggle case for line. U = (in visual mode)upper case for char. u = (in visual mode)lowercase for char. gUU = upper case for line.

:set spell Toggles the spell checking press z= on the misspelt word to get a list of suggestions. VIMRC OPTIONS [\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_] OPTIONS

Settings last only at a session. Need to edit vimrc to get persistent settings. Should probably back up my vimrc.

:imap ;; \" maps the \` key to

:set guifont=Courier~new~:h12:cANSI [\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_]

------------------------------------------------------------------------

TABS :tabnew Opens up a new tab. :tabedit \[file\] Edit a specified file. :tabclose Close i-th tab. :tabonly Close all other tabs and leave only the current tab. :tab ball Show each buffer in a tab.

In Normal Mode gt = go to next tab. gT = go to previous tab. \[i\]gt = go to the i-th tab.

:tabn Goto the next tab. :tabp Goto the previous tab. [\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_] WINDOWS CTRL-Wn = new window CTRL-Ws = split CTRL-Wv = split vertically

CTRL-Wj = goto window bellow CTRL-Wk = goto window above CTRL-Wh = goto window right CTRL-Wl = goto window left

CTRL-Wc = close window CTRL-Wo = close others

------------------------------------------------------------------------

BUFFERS :b nameOfBuffer shows a buffer :ball opens all buffers [\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_] MACROS q = start/ stop recording macros

------------------------------------------------------------------------

TIPS set bash alias for gvim --remote-tab-silent so when the command is used, things get added to existing instance of vim use vim as a wiki <http://www.swaroopch.com/notes/Vim_en:Personal_Information_Management> command to remove trailing spaces %s/`\s`+\$// [\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_] COLUMN EDITING to enter into column editing mode select the colums you want o enter text shift-i to go into insert mode in column editing mode type text in to apply change (or )

, then \" to insert the last yank.

------------------------------------------------------------------------

VIMDIFF do - changes from other window to current dp - changes from current window to other \]c - next change \[c - previous change :diffupdate [\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_] Tutorials Vimeo Vim tutorials <http://vimeo.com/user1690209/videos>

------------------------------------------------------------------------

PLUGINS Try these plug-ins. Surround <http://www.vim.org/scripts/script.php?script_id=1697> ds\[mov\] deletes surrounding of selection cs\[mov\] changes surrounding of selection ys\[mov\] surrounds the sellection yss selects line to add surrounding symbols ysw Snipmate <http://www.vim.org/scripts/script.php?script_id=2540> with key word to complete can customise snips

TComment <http://www.vim.org/scripts/script.php?script_id=1173>

MRU <http://www.vim.org/scripts/script.php?script_id=521>

FuzzyFinder <http://www.vim.org/scripts/script.php?script_id=1984>

NERDTree <http://www.vim.org/scripts/script.php?script_id=1658>

Matchit <http://www.vim.org/scripts/script.php?script_id=39>

BONUS: Matrix! <http://www.vim.org/scripts/script.php?script_id=1189>
