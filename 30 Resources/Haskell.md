- Overview

- Only Expressions

-   Haskell has no statements only expressions

- Execution as Reduction

-   programs are executed via reduction
-   convert an expression into a simpler expression

e.g. :

``` haskell
3 * (4+5)
--  >
3 * 9
--  >
27
```

-   you can have multiple reduction paths but the Chruch-Rosser Theorem states that *every terminating reduction paths gives the same result* which means that
    -   Correctness doesn\'t depend on order of evaluation
    -   changing the order

- Laziness

elements are evaluated lazily-- i.e. as expressions are only evaluated when they are used. e.g.:

``` haskell
answer = 42
yourlist = [7, answer+1, 7*8]
-- > would only evaluate to:
  [ 7, 43, 56]
-- when it's needed by other functions
```

- Prelude

Standard libraries is called the *prelude*

- Some Symbols and their meanings

  Symbols   Use   Notes
  --------- ----- ----------------------------------------------------
  \_              represents a variable we don\'t know or care about
                  
                  

- Mechanisms

- Hello World

``` haskell
main = putStrLn "Helloo world"
```

- Comments

``` haskell
-- this is a single line comment
{- This is a ..
.. multi line
.. Comment
-}
```

- Imports

``` haskell
import           Data.List
import           System.IO
```

- Conditionals

``` haskell
max x y =
  if x > y
  then x
  else y

max 10 24
```

- prefix and infix operators

-   you can use backticks `` ` `` around function names to make them infix operators e.g.

    ``` haskell
    42 `max` 32
    ```

-   you can use brackets `()` around an infix operator to make them prefix

- Guards

similar to case statements e.g. this is a recursive definition of the length function using guards

``` haskell
length lst
  | lst == [] = 0
  | otherwise = let x:xs = lst in 1 + length xs
```

- Function

A function takes one ore more arguments and computes a result

``` haskell
whichBigger :: Int -> Int -> IO() --shows the type declaration
whichBigger x y ~ print (show (max x y) ++ " is bigger") --function 'show' prints output
whichBigger 2 16
```

Many functions are pre-defined in the library called *prelude*

a function can only return one result (multiple results are returned in a list)

- Defining a function

A function is defined by an equation

``` haskell
f = \x -> x + 1  -- a lambda function
-- or
f x = x + 1 -- named function
```

- Function Application

how function application works

``` haskell
f = \x -> x + 1
  f 3
-- > (bind x = 3)
  (x+1) where x = 3
-- >  (substitue 3 for x )
  3+1
-- >
  4
```

Example of function application with multiple arguments

``` haskell
addsums = \x y z -> x + y + z

  10 + 4* add3nums 1 2 3
= 
  10 + ( 4* (add3nums 1 2 3) )
  -- >
  10 + (4*(1+2+3) )
  -- >
  10 + (4*6)
  -- >
  10 + 24
  -- >
  34
```

a function can **only return one result** if there is more than one value returned it can be wrapped up in a List

- Function Composition

haskell uses `.` as the function composition operator

``` haskell
(f.g) x = f (g x)
```

- Recursion

example

``` haskell
-- recursively calculate the length of a list
length :: [a] -> Int           -- function type
length [] = 0                  -- base case
length (x:xs) = 1 + length xs  -- recursion case
```

- Types

- Bool

  Operator   What it does                                    example
  ---------- ----------------------------------------------- --------------------
  ==         whether one thing is equal to another           12 == 12
  /=         whether onething is not the same as the other   23 /= 22
  \<         whether something is smaller than another       11 \< 32
  &&         and (ture if both ture)                         True && True
  \| \|      or (true if one is true)                        True \| \| False
  elem       see whether something is a member of a list     elem 10 \[1..100\]
  \`xor\`    exclusive or, backticks to make it infix        True \`xor\` False

- Int

- Float

- Double

- Char

- String

Strings are just lists of chars, so list functions works on strings

- List

-   list is a single value that contains several other values.

-   **Syntax:** elements are written in square parentheses separated by commas.

-   `[1,2,3]` is just syntactic sugar for `1:2:3:[]`

``` haskell
primeNum = [3, 5, 7, 11]
morePrime = primeNum ++ [13, 17, 19, 23, 29] -- '++' is append
2 : [4,6,8] ++ morePrime -- ':' is the  cons operator, adds things to the front, it's super fast.
-- you can only add one item with cons.
```

Sompe playing

``` haskell
fiveTo10 = [5..10] -- creates the list [5, 6, ,7 8, 9, 10]
oneToFour = [1..4]
oneToTen = oneToFour ++ fiveTo10
0 : oneToTen
```

- Operations

- head

`head [1, 2, 3, 4]` gives `[1]`

- tail

`tail [1, 2, 3, 4]` gives `[2, 3, 4]`

- last

`last [1, 2, 3, 4]` gives `[4]`

- init

`init [1, 2, 3, 4]` gives `[1, 2, 3]`

- zip

``` haskell
zip [ "fish", "bread", "salt"] ["chips", "butter", "pepper"]
```

-   you can also zip 3 lists with `zip3`

```
<!-- -->
```
-   `zipWith` can uses a function to generate the list

    ``` haskell
    zipWith (+) [1,2,3] [2,4,8]
    ```

      --- --- ----
      3   6   11
      --- --- ----

    `zipWith` is more general than zip. i.e. zip can be implemented with:

``` haskell
zipWith (\x-> (\y-> (x,y))) [ "fish", "bread", "salt"] ["chips", "butter", "pepper"]
```

comma `,` can also be used to produce pairs i.e.:

``` haskell
zipWith (,) ['a', 'b', 'c'] [ 1,2,3]
```

- Map

performs a computation on each element of the list

``` haskell
map f [x0,x1,x2] -- > [f x0, f x1, f x2]
```

common pattern is to use function composition to make applying multiple functions to a list more readable

``` haskell
map f (map g xs) = map (f . g) xs
```

- Foldr / Foldl

iterate over a list from left to right (`foldl`) or right to left (`foldr`) recursive definition of foldl:

``` haskell
--
foldl    :: (b -> a -> b) -> b -> [a] -> b
foldl f z0 xs0 = lgo z0 xs0
             where
                lgo z []     =  z
                lgo z (x:xs) = lgo (f z x) xs

```

- Filter

takes a boolean function and a list and returns a list of elements that fits the truth condition sets

``` haskell
-- a filter function written with guards
filter :: (a -> Bool) -> [a] -> [a]
filter pred []    = []
filter pred (x:xs)
  | pred x         = x : filter pred xs
  | otherwise      = filter pred xs

```

else defined on a single line

``` haskell
filter pred lst
  | null lst = []
  | otherwise = if pred x
     then x:filter pred xs
     else filter pred xs
       where x:xs=lst
```

- List Comprehension

pass a list to a function

``` haskell
[2*x+1 | x <- [ 0..10]] -- makes a list of odd numbers
```

``` haskell
[[a,b] | a <- [1,2,3], b <- [4,5]] -- makes a list of tuples
```

- Indexing a list

get the nth element of a list (zero indexed)

``` haskell
[0..10] !! 2 --0 indexed  get the 3rd element of the list
```

- Monads

- Succinct Explinations

<https://www.youtube.com/watch?v=jMDRlBy8VDw&t=307s>

- Sources to read

<http://blog.sigfpe.com/2006/08/you-could-have-invented-monads-and.html?m=1>

- IO

-   Use `Do` to sequence actions.
-   Use \<- inside a do to associate input values with names
-   any values that inolv inside a do to associate input values with names
-   any values that involves I/O has IO in its type
-   a sequence of I/O actions is seen as being in the IO monad I/O has IO in its type
-   a sequence of I/O actions is seen as being in the IO monad = \<- =

- Tooling

- Commands

  Command                               What it Does                         note
  ------------------------------------- ------------------------------------ --------------------
  `runhaskell`                          runs the code without complilation   
  `ghc –make` filename                  Compiles the code                    
  `ghcid –command 'ghci filename.hs'`                                        install with stack
  `stack install package`               installs a package from stackage     

- GHCI

``` haskell
:l filename
-- without the file extensions, this will load the .hs files to GHCI

:t function
-- gives you the type signatue of the function

:r
-- reloads the files loaded

:set +m
-- make multiline
-- press enter twice to get out of the multiline
```

- Formatter

<https://github.com/jaspervdj/stylish-haskell>

- Functions

- Functions I made up to learn

``` haskell
whichBigger x y ~ print (show (max x y) ++ " is bigger than " ++ show (min x y))
whichBigger 12 30
-- my first function
```

- IO functions

-   `putStrLn 'string'` prints functions

doubleMe x = 2 \* x

- Libraries

- System.Process

do this to run a command

``` haskell
module Main where

import System.Process

main :: IO ()
main = system "ls -al" >>= \exitCode -> print exitCode
```

- Haskell Servant

<https://www.servant.dev/>

- Built With Haskell

- Duckling

<https://github.com/facebook/duckling>

- Learning Projects

- Robot that reads out the words that Dylan needs to learn how to write

- Version 0.1

-   use [[System.Process]] to call espeak and use haskell to do parsing and flow control and simple terminal ui.

- Learning Resources to Checkout

-   <https://typeclasses.com/phrasebook>
-   <https://learnxinyminutes.com/docs/haskell/>
-   <https://github.com/krispo/awesome-haskell#readme>
-   <https://www.edx.org/course/introduction-to-functional-programming>
-   <https://channel9.msdn.com/Series/C9-Lectures-Erik-Meijer-Functional-Programming-Fundamentals>
-   [learn haskell in 1 video](https://www.youtube.com/watch?v=02_H3LjqMr8)
-   <https://www.seas.upenn.edu/~cis194/fall16/> <https://www.youtube.com/watch?v=b9FagOVqxmI&list=PLA6CF1CC303C49F02&index=2&t=0s>

- Haskell Thinking

-   <https://www.snoyman.com/blog/2019/11/boring-haskell-manifesto>
-   <https://www.parsonsmatt.org/2018/03/22/three_layer_haskell_cake.html>

- Settings
