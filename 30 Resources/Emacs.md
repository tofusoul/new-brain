---
title: emacs
---
# Emacs 
## [[Emacs Lisp]]
- [ ] ~~setup interop between [org-roam and logseq](https://coredumped.dev/2021/05/26/taking-org-roam-everywhere-with-logseq/)~~

- Emacs is basically a repl for elisp

- [[Doom Emacs]]

- [ ] write some notes on how to setup Emacs with org roam on Windows 

- Setting up emacs in WSL in windows 11

- from [this guide](https://emacsredux.com/blog/2021/12/19/using-emacs-on-windows-11-with-wsl2/)

- Install git

- install autoconf

``` sh
git clone <git://git.sv.gnu.org/emacs.git> 
sudo apt install build-essential libgtk-3-dev libgnutls28-dev libtiff5-dev libgif-dev libjpeg-dev libpng-dev libxpm-dev libncurses-dev texinfo 
cd emacs 
./autogen.sh 
./configure --with-pgtk 
make -j8 
sudo make install

```

``` 
(defun copy-selected-text (start end) (interactive \"r\") (if (use-region-p) (let ((text (buffer-substring-no-properties start end))) (shell-command (concat \"echo \'\" text \"\' \| clip.exe\")))))
```
- install [[Doom Emacs]]

