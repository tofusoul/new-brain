- Org-Mode Notes

- Sources:

- Literate Programming Tutorial

- Org-Example

get more indepth understanding of how to properly use org-mode with these guides

-   [Example of how to use orgmode](example.org) do this first, seems to be the least amount of required time

- Keys and Commands

  Action                      Key                           Mode      Note
  --------------------------- ----------------------------- --------- ------------------------------------------------
  Export to other formats     `[space] [m]ode [e]`          Command   in org mode
  Time Stamp                  `[Ctrl]+[c] [.]`              Input     
  Set Tag                     `[Space] [m]ode [q]`          Command   works only in orgmode
  lists todos in subfolders   `[Space] [p] [t]`             Command   might do different things in differnt projects
  Insert link                 `[Space] [m]ode [l]ink [l]`   Command   
  Toggle checkboxes           `[Ctrl]+[c] [Ctrl]+[c]`       Both      toggles the checkboxes in the line
  store link                  `[Space] [m] [l] [s]`         Command   yanks the link to the current place
  place stored link           `[Space] [m] [l] [s]`         Command   Place the last yanked link to under key
  Add Another Item in list    `[Alt]+[Enter]`               Input     
  Add another heading         `[Ctrl]+[Enter]`              Input     
                                                                      

- Search and Navigating

  Action        Key                Mode   Note
  ------------- ------------------ ------ -------------------------------------------------------
  Sparse tree   `[alt]+[c] [/ ]`   Both   Collapses all headings that doesn\'t fit the criteria

- Agenda

- Keys and Commands

  Action                               Key                             Mode      Note
  ------------------------------------ ------------------------------- --------- --------------------------------------------------------
  Add file to agenda                   `(org-agenda-files-to-front)`   Command   run this command to add the current file to org agenda
  Schedule                             `[Space] [m] [d] [s]`           Command   
  Set deadline                         `[Space] [m] [d] [d]`           Command   
  open the agenda                      `[Space] [n] [a] [a]`           Command   
  Write the current agenda to a file   `(org-agenda-write)`            Agenda    when you have an angenda file open

to schedule something for just some days of the week `SCHEDULED: <%%(memq (calendar-day-of-week date) '(1 3 5)) 08:25 >`

- Add Agenda Files Recursively

``` elisp
;; Recursively find all org files in a directory tree and add to agenda files
(setq org-agenda-file-regexp "\\`[^.].*\\.org$\\|.txt$\\'") ;Looks for .org and .txt files
(defun load-org-agenda-files-recursively (dir) "Find all directories in DIR."
       (unless (file-directory-p dir) (error "Not a directory `%s'" dir))
       (unless (equal (directory-files dir nil org-agenda-file-regexp t) nil)
         (add-to-list 'org-agenda-files dir)
         )
       (dolist (file (directory-files dir nil nil t))
         (unless (member file '("." ".."))
           (let ((file (concat dir file "/")))
             (when (file-directory-p file)
               (load-org-agenda-files-recursively file)
               )
             )
           )
         )
       )
(load-org-agenda-files-recursively "~/Life/") ;; This is the root where the search starts
```

- Code Blocks

  Action             Key                       Mode   Note
  ------------------ ------------------------- ------ ------
  execute the code   `[Ctrl]+[c] [Ctrl]+[c]`   Both   

-   type `<s` for code snipped then press `[tab]` to start a code block

- General Syntax

    <body>

code can be excecuted when you press `[Ctrl]+[c] [Ctrl]+[c]` in the heading

- Executable Bash Script

``` 
- [code here]
```

1.  execute with command \[org-bable-execute-maybe\]

    fe\*\* Export

- Export To Reveal JS Slides

-   export to revel.js is built in.

`(org-re-reveal-export-to-revealjs)` <https://gitlab.com/oer/org-re-reveal>

- OX-Hugo :

-   export to hugo flavoured markdown
-   Super quick and easy blog publishing workflow

--[Example Post](https://ox-hugo.scripter.co/images/one-post-per-subtree.png)

Export to blog

- Formatting

-   **bold**
-   *italic*
-   [underline]
-   ~~strike through~~
-   `verbatim`
-   `code`
-   <http://orgmode.org>

``` example
small example
```

```
#+comment: this will not be exported
```
- Lists

  Action                                   Key                Mode   Note
  ---------------------------------------- ------------------ ------ ------
  cycle item type OR turn into list item   `[ctrl]+[c] [-]`   both   

- Time & Effort

-   Set the [[Column Mode]] make effort estimates easier to work with :
-   Set the Property for EFFORT~ALL~ so you can use shift left and right to input effort

```
#+PROPERTY: Effort_ALL 0:05 0:10 0:15 0:20 0:30 0:45 1:00 1:30 3:00 5:00 8:00 10:00 15:00 20:00 40:00 80:00 100:00 120:00
```
- Keys and Commands

  Action       Key                     Mode      Note
  ------------ ----------------------- --------- ----------------------------------------
  Set Effort   `[Space] [m] [c] [E]`   Command   sets the effort of the current heading

- Tables and Spreadsheet

- References to lookup

-   <https://orgmode.org/manual/The-Spreadsheet.html>
-   <https://orgmode.org/worg/org-tutorials/org-spreadsheet-intro.html>
-   <https://orgmode.org/worg/org-tutorials/org-spreadsheet-lisp-formulas.html>
-   <https://www.youtube.com/watch?v=5vGGgfs0q3k&feature=youtube>
-   <https://www.flutterbys.com.au/stats/tut/tut16.1.html>
-   <https://orgmode.org/worg/org-tutorials/org-lookups.html>

- Keys and Commands

  Action              Key                Mode      Note
  ------------------- ------------------ --------- -----------------------------------------------------
  Show cell numbers   `[Ctrl]+[c] [}]`   Command   so you can reference cells without needing to count

- Column Mode

-   you can set what columns to show like below

```
#+COLUMNS: %32ITEM(Item) %10TODO(Status) %8EFFORT(Effort) %CLOCKSUM
```
- Keys and Commands

  Action                  Key                                  Mode      Note
  ----------------------- ------------------------------------ --------- ---------------------------------------
  Switch to column mode   `[Ctrl]+[c] [Ctrl]+[x] [Ctrl]+[c]`   Command   Default Emacs binding for column mode

- [ ] Figure out how to use column mode properly 

<https://orgmode.org/manual/Column-View.html#Column-View>

- [ ] figure out how timers work 

- [ ] change monday to first day of week 

- [ ] create a short cut for org-create-table 

- Minor-Modes

- Org-Chef

supports extracting recipes from: <http://allrecipes.com/> <http://www.geniuskitchen.com/> <https://www.simplyrecipes.com/> <https://www.marthastewart.com/> <https://www.budgetbytes.com/> <https://www.culturesforhealth.com/> <https://www.seriouseats.com/> <http://www.marmiton.org/> (french) <https://www.reluctantgourmet.com/> <https://www.chefkoch.de/> <https://steamykitchen.com/> <https://showmetheyummy.com/> <https://nytimes.com/> <http://www.xiachufang.com/> (下厨房 Chinese) <https://www.finecooking.com/> Any recipe site based on wordpress <https://taste.com.au/>

- Diary-mode

Technically not part of org-mode, but I can\'t see myself using it in any other context could use it to do morning pages <https://www.emacswiki.org/emacs/DiaryMode>

- Calendar Sync

<https://orgmode.org/worg/org-tutorials/org-google-sync.html> out of that, probabaly the best solution is with <https://github.com/dengste/org-caldav>

-   Google makes you jump through hoops to make this work probably worth setting up nextcloud or own cloud instances

- Lookups

<https://orgmode.org/worg/org-tutorials/org-lookups.html>
