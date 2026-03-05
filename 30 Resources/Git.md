---
title: Git
---

- Related

- [Github](id:eace1bab-675d-4733-9dbb-37e9befda3a5)

- Basic Commands

``` 
git init                         - Starts the repo
git add .                        - Adds all files in the current directory; adds all changes
git rm somefile.blah             - Removes the file from the repository
git rm --cached somefile.blah    - only removes the file from the repo
git commit -m                    - Commits the outstanding changes; write commit message in command line
git commit -a                    - Commits the outstanding changes; opens up the editor
git remote add origin /repo url/ - Sets the remote repo; give the url to push to
git push origin master           - Pushes the changes to the remote repo
git log                          - Lists changes
git checkout commitIDHash        - Check out the code at a commit
git checkout branchname          - Checks out a branch
git branch                       - Lists the branches
git branch BranchName            - Creates a branch
git merge                        - Merges the branches back into master

```

\*

- the Github app in windows is pretty good

- Trouble Shooting

- current branch behind remote counterpart

<https://codewithhugo.com/fix-git-failed-to-push-updates-were-rejected/>

- Git Lab

j4whqAzdsfMsMq-VeQdu

- Resources

- Visual Git guide

<http://marklodato.github.io/visual-git-guide/index-en.html>

- Git Simple guide

<http://rogerdudler.github.io/git-guide/>

- Learn Git Branching

<https://learngitbranching.js.org/>
