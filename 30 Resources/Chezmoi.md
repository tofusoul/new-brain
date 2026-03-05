- [quickstart](https://www.chezmoi.io/quick-start/#start-using-chezmoi-on-your-current-machine)

- install chezmoi

``` 
sh -c "$(curl -fsLS get.chezmoi.io)"
```

- To add a file or folder to track in chezmoi

``` bash
chezmoi add $FILE 
```

- To update the changes made on the working file

``` 
chezmoi re-add
```

- To see the difference between the repo and the working files

``` 
chezmoi diff
```

- To apply the changes:

``` 
chezmoi apply -v
```

- to reinstate the repo

``` 
$ chezmoi init https://github.com/username/dotfiles.git
```

or clone the github repo into: `/home/user/.local/share/chezmoi/` and apply the difference
