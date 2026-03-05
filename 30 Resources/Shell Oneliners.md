---
title: Shell Oneliners
---
- Check out
      [commandline Fu](https://www.commandlinefu.com/commands/browse/sort-by-votes)

# Movements
- Go to the previous working dir
    ``` sh
    cd -
    ```
# Manipulating file Names

- Remove the .bak extension from the backup files
  ``` sh 
  rename 's/\.bak$//' *.bak
  ```
- Find word files in folder and convert them to markdown using [[Pandoc]]
  ``` sh 
  find . -name \*.docx -type f -exec pandoc  -f docx -t markdown-o .md  \;~
  ```

- Replace a file name extension with another
  ``` sh
  rename .htm .html *.htm
  ```

# Manipulating Files
- replace specific instances of one text pattern with another in the whole directory
  ``` sh
  find . -type f -exec sed -i.bak 's/^\-/\*/g'  \;
  # replace the regEx with what ever patter that fits your need.
  ```
  
- Backup and Storage
- Recursively copy all the files of one kind in a folder structure while preserving the folder structure. 
  ``` sh
  Rsync -a --prune-empty-dirs --include '*/' --include '*.csv' --exclude '*' source/ target/
  ```
- Make a tarball
  ``` sh 
  tar pcvfX - [list of files to exclude] [directory] | gzip -c > target.tar.gz~
  ```

# [[Git]]

- remove all the csv in the github repo without remove the actual files (in ZSH)
  ``` sh
  git rm -r --cached **/*.csv
  ```

- show the lines of code in a local github repo (requires cloc installed)
  ``` sh
  cloc --vcs git
  ```

- add user when setting up git on a new computer
  ``` sh
  git config --global user.email "haoyen.shih@gmail.com"
  git config --global user.name "Andrew Shih"
  ```
-
- Remove everything that is in git ignore without remove the files themselves
  ``` sh
  git ls-files -i -X .gitignore | xargs -I git rm --cached ""
  ```
- compares the difference between two files
  ``` sh 
  grep -v -f _file1_ _file2
  ```

- 1 line quick for loop
  
  ``` sh
  for f in *.rar; do unrar "$f"; done
  - e.g. unrar all the rar files
  ```
- find a file and open it (requires fd installed)
  
  ``` sh 
  fd something -X xdg-open
  ```
- read logs in real time
  
  ``` 
  tail -f path_to_Log
  ```
- reuse the last argument from the previous command
  
  ``` sh
  command !$
  - applies 'command' to the previous file
  ```
- Add directory to $PATH
  
  ``` sh
  export PATH=$PATH:/opt
  ```
-
- Say yes to everything in interactive scripts or commands
  
  ``` sh
  yes | commandOrScript
  ```

- Find every markdown file in the folder and and regex replace patterns:
``` bash
find . -type f -name "*.md" -exec sed -i 's/# /- /g' {} \;
```
- Shell one liner template
  template:: Shell One Liner
  ``` sh
  sl
  - see the trains
  ```
