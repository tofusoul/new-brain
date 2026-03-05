- `set~ without ~merge` will overwrite a document or create it if it doesn\'t exist yet

- \~set\~ with \~merge\~ will update fields in the document or create it if it doesn\'t exists

- \~update\~ will update fields but will fail if the document doesn\'t exist

- `create~ will create the document but fail if the document already exists
* There's also a difference in the kind of data you provide to ~set~ and ~update`.

- For \~set\~ you always have to provide document-shaped data:

- #+BEGIN~SRC~

set( {a: {b: ,  )

```
#+END_SRC
```
- With \~update\~ you can also use field paths for updating nested values:

- #+BEGIN~SRC~

update()

```
#+END_SRC
```
\*

- <https://www.youtube.com/watch?v=Tck4tN4b360>

\*
