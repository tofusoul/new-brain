- #+BEGIN~SRC~ python

from pathlib import Path

print(f\"Current Working Directory: \") print(f\"Home directory: \")

path = Path.cwd() / \"somefile.blah\"

print(path.exists())

with path.open() as file:

path.read~text~()

full)path = path.resolve()

full~path~.parent.parent

#this will check if the pthath is a directory path.is~dir~()

path.is~file~()

new~file~ = Path.cwd() / \"newfile.txt\" new~file~.touch() new~file~.write~text~(\"woo hoo\")

new~file~.unlink

new~dir~ = Path.cwd() / \"newdir\" new~dir~.mkdir()

new~dir~.rmdir()

```
#+END_SRC
```
