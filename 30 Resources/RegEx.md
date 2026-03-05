---
title: RegEx
---

- Regex Basics

- ![](../assets/image_1669088846269_0.png)

- Expresses patterns.

- `$` matches end of new line

- `\s` matches white space

- `\S` anything but white space

- `\w` matches alpha numeric

- `\W~matches non-appha numeric
* ~\d` matches digits

- `[a-z]+` matches anything that has a-z one or more times matches chunks instead of characters

- this is greedy, `?` will make it non-greeedy

- `\w` will match any sequenc of alphanumerics that is 4 long

- `(cat)` denotes a capture group of \'cat\' which can be referenced with `\1`

- `cool(?=\ dog)` will gt

- `(?mx)` at the beginning of the expression allows you to break the expression up to seperate lines, and comment etc.

\* \* \*

- \| Symbol \| What it Does \| Example \| Explanation \|

  --------- --------------------------------------------------------------------------------------- --------------- ------------------------------------------------------
  `.`       Select wild card 1 char wide                                                            `d.g`           will match \'dog\' \'dig\' and \'dag\'
  `\d`      Selects any digit between 0-9                                                           `\d1`           will match \'01\', \'11\', \'21\' etc.
  `\`       Escape char                                                                             `\.`            match fullstop char,
  `[abc]`   chars match whats between brackets                                                      `[aeiou]`       matches a vowel
  `[^x]`    excludes a char                                                                         `A[^x]e`        excludes Axe
  `[A-Z]`   select a range                                                                          `[A-Za-z0-9]`   selects alpha numeric chars
  `a`    selects 3 a\'s                                                                          `a`        match \'a\' nor more than 3 times, no less than once
  `^`       denotes from the begining of a new line, but inside a character class, it is negation   `^Apr`          matches a places where the line starts with \'Apr\'
  `\vert`   or                                                                                      `[a]\vert[b]`   means either a or b
  --------- --------------------------------------------------------------------------------------- --------------- ------------------------------------------------------

- Vim Search and Replace

`[range]s/[Search]/[Replace]/g`

`%S` Selects the whole file

- Examples

- Match lines that contain a word

``` 
^.*John.*$.
```

Matches lines that contains the word John

- Match Email Address

``` 
/^
(
  (
    (
      [hH][tT][tT][pP][sS]?
      |
      [fF][tT][pP]
    )
    \:\/\/
  )?
  (
    [\w.\-]+
    (\:[\w\.\&%\$\-]+)*@
  )?
  (
  )
)

```

``` 
(?:[a-z0-9!#$%&'*+/=?^_`~-]+(?:\.[a-z0-9!#$%&'*+/=?^_`~-]+)*|"(?:[\x01-\x08\x0b\x0c\x0e-\x1f\x21\x23-\x5b\x5d-\x7f]|\\[\x01-\x09\x0b\x0c\x0e-\x7f])*")@(?:(?:[a-z0-9](?:[a-z0-9-]*[a-z0-9])?\.)+[a-z0-9](?:[a-z0-9-]*[a-z0-9])?|\[(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.)(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?|[a-z0-9-]*[a-z0-9]:(?:[\x01-\x08\x0b\x0c\x0e-\x1f\x21-\x5a\x53-\x7f]|\\[\x01-\x09\x0b\x0c\x0e-\x7f])+)\])
```

-   Railroad Diagram explaining above.

\[\[./General-Email-Regex-Railroad-Diagram-emailregex.com\_.png

- Resources

-   Udemy Tutorial <https://www.udemy.com/course/regex-academy-an-introduction-to-text-parsing-sorcery/learn/lecture/8040016#overview>
-   [Facts](https://en.wikipedia.org/wiki/Regular_expression) about regex
-   tutorials from [regexone](https://regexone.com/lesson)
-   [regex 101](https://regex101.com/)
-   [Regex Builder](https://regexr.com/)
-   [grep and regex](https://ryanstutorials.net/linuxtutorial/grep.php)
-   [tutorial](https://likegeeks.com/regex-tutorial-linux/)
-   <https://pythex.org/>
-   <https://github.com/ziishaned/learn-regex>

- References To Digest

-   [ ] [RE2 syntax](https://github.com/google/re2/blob/main/doc/syntax.txt)
-   [ ] [Regullar-Expressions.info](https://www.regular-expressions.info/reference.html)

- Examples

``` regex
[0-9]
```

- Tutorials

-   [ ] [RegexOne](https://regexone.com/)

- RegEx games

-   <https://regexcrossword.com/>
-   [Slash Escape](https://www.therobinlord.com/projects/slash-escape)
