- Questions

- Basics

``` 
;; This is a comment
```

- Define Global Variables

``` 
(defparameter *small* 1)
;; asterisks, called 'earmuffs' do nothing, just a convention to make global variables clearer to see
(defparameter *big* 100)
;; defparameter ceclariations can be overridden
(defvar *foo* 200)
;; defvar works more like a constant, can't be overridden
```

- Define Functions

``` 
(defun some_function_name (argument)
  )
;; defines a function that does othing

(defun return_five ()
  (+ 2 3))
;; the function returns a value of 5

```

- REPL

- Load File

``` 
(load "myfile.lisp")
;; loads a file named "myfile.lisp"
```

- elisp

[star-here](https://github.com/chrisdone/elisp-guide) <https://www.youtube.com/watch?v=1HspB643qdw&feature=youtu.be> <https://www.emacswiki.org/emacs/LearnEmacsLisp>

- Resources

-   <http://www.gigamonkeys.com/book/introduction-why-lisp.html>

- Settings
