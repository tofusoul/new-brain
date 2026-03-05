- Starters

- Elm Pages

<https://elm-pages.com/>

- Elm- SPA

probably won\'t be using this

- **Libraries**

- [[Elm UI]]

- [[Elm Charts]]

- Resources

- <https://orasund.gitbook.io/elm-cookbook/>

\*\*

- 23 delph

- 31 colman

\*\*

- Language

- Function

-   arguments are seperated by space
-   name the arguments as variables after the function name

`over9000 powerLevel = if powerlevel > 9000 then "it's over 9000!!!" else "meh"`

- Local Variables

-   *Let* code block will allow you to declair local variables.

- Currying

-   parcially complete a function to create a curry function

- Piping

-   \'\|\>\' allows you to put take the output of the first function and send it as input in the second function

- Anonymous Functions

-   \'\' declares an Anonymous function

- Infix functions

-   all non-alpha numeric symbol combination can be used as names of infix functions
-   back ticks lets you use pre-fix functions as infix functions
-   parenthesis allow infix functions to be pre-fix functions.

- Composition

-   you can compose functions with the composition opporatore \"\>\>\"

- Lists

-   values in the list must all have the same type.
-   List function takes a list and does stuff to it.

- Tuples

-   tuplees can hold a fixed number of values. `(True, "Name Accepted")`

- Records

-   a record is a set of key-value pairs. it is written like this:

    `bill = `

-   this will update values in a record

    ``

-   updates are non-destructive. New records are created

- Union Types

declaring a type composed of other types separated by \'\|\'

e.g.

pattern matching case msg of

- Maybes

- Types

-   type aliases can be used as a function to construct objests from types

- Higher Order Function

-   e.g List.map

-   Elm Architecture

-   Model

-   model type alias

-   model initial state

    -   Update

    what can happen in our app, how should the model change when these things happen.

-   msg is usually a union type listing all the things that can happen in our app

-   an update function that recieves a msg, a model and return 2 parameters

\'

- Libraries

- Elm-spa

<https://www.elm-spa.dev> a framework for elm

- Elm-Pages

<https://package.elm-lang.org/packages/dillonkearns/elm-pages/latest/> Static site generation with elm

- Tooling

<https://medium.com/@byteshiva/how-to-install-elm-on-archlinux-dcc1b2e2c525>

- Libraries and Tools

- Create Elm Apps

<https://github.com/halfzebra/create-elm-app>

- Elm Ui

-   Shows how to build UI with elm ui

<https://korban.net/elm/elm-ui-patterns/tabs>

- Elm Narrative Engine

<https://github.com/jschomay/elm-narrative-engine>

- Monocle

<https://package.elm-lang.org/packages/arturopala/elm-monocle/latest/?utm_campaign=Elm%20Weekly&utm_medium=email&utm_source=Revue%20newsletter>

- Elm Colour Palette

<https://package.elm-lang.org/packages/tesk9/palette/latest/>

- Elm 3d Scene

<https://github.com/ianmackenzie/elm-3d-scene>

- Elm-Graphql

- Elm-Geometry

<https://github.com/ianmackenzie/elm-geometry>

- Elm Visualization

<https://package.elm-lang.org/packages/gampleman/elm-visualization/latest/>

- Elm Line Chart

<https://package.elm-lang.org/packages/terezka/line-charts/latest>

- Elm Particles

<https://package.elm-lang.org/packages/BrianHicks/elm-particle/latest/>

- Elm Units

<https://package.elm-lang.org/packages/ianmackenzie/elm-units/latest/>

- Community

- Game Jam

<https://itch.io/jam/elm-game-jam-4?utm_campaign=Elm%20Weekly&utm_medium=email&utm_source=Revue%20newsletter>

- Videos to Watch

- Teresa Sokol on Parsers

<https://www.youtube.com/watch?v=M9ulswr1z0E>

- Tutorials

-   Elm example <https://dev.to/nimmo/the-basic-elm-example-that-i-wish-id-had-40m8>
-   Another Elm example <https://dev.to/selbekk/my-first-elm-app-c70>
-   Exercises <https://exercism.io/tracks/elm/exercises>
-   Elm Koans <https://github.com/robertjlooby/elm-koans>
-   Elm Wrokshop <https://github.com/rtfeldman/elm-0.19-workshop>

- Books

-   <https://www.brianthicks.com/json-survival-kit/> Consider getting this. Json decoding and encodinig seems hard.
-   <https://elmprogramming.com/>

- Data Types

type is inffered, but we can annotate types. type names are capitalised\* Elm notes

- Language

- Function

- arguments are seperated by space

- name the arguments as variables after the function name

`over9000 powerLevel = if powerlevel > 9000 then "it's over 9000!!!"
else "meh"` - Local Variables

- *Let* code block will allow you to declair local variables.

``` example
- Currying
```

- parcially complete a function to create a curry function

``` example
- Piping
```

- \'\|\>\' allows you to put take the output of the first function and send

it as input in the second function

``` example
- Anonymous Functions
```

- \'\' declares an Anonymous function

``` example
- Infix functions
```

- all non-alpha numeric symbol combination can be used as names of infix

functions

- back ticks lets you use pre-fix functions as infix functions

- parenthesis allow infix functions to be pre-fix functions.

``` example
- Composition
```

- you can compose functions with the composition opporatore \"\>\>\"

- Lists

- values in the list must all have the same type.

- List function takes a list and does stuff to it.

- Tuples

- tuplees can hold a fixed number of values. `(True, "Name Accepted")`

- Records

- a record is a set of key-value pairs. it is written like this:

`bill = `

- this will update values in a record

``

- updates are non-destructive. New records are created

- Union Types

declaring a type composed of other types separated by \'\|\'

e.g.

pattern matching case msg of

``` example
- Maybes

- Types
```

- type aliases can be used as a function to construct objests from types

- Higher Order Function

- e.g List.map

- Elm Architecture

- Model

- model type alias

- model initial state

- Update

what can happen in our app, how should the model change when these things happen.

- msg is usually a union type listing all the things that can happen in

our app

- an update function that recieves a msg, a model and return 2

parameters

\'

``` example
- Libraries
    - Elm-spa
```

<https://www.elm-spa.dev> a framework for elm

``` example
- Elm-Pages
```

<https://package.elm-lang.org/packages/dillonkearns/elm-pages/latest/> Static site generation with elm

- Tooling

<https://medium.com/@byteshiva/how-to-install-elm-on-archlinux-dcc1b2e2c525>

- Libraries and Tools

- Create Elm Apps <https://github.com/halfzebra/create-elm-app>

- Elm Ui

- Shows how to build UI with elm ui

<https://korban.net/elm/elm-ui-patterns/tabs>

- Elm Narrative Engine

<https://github.com/jschomay/elm-narrative-engine>

- Monocle

<https://package.elm-lang.org/packages/arturopala/elm-monocle/latest/?utm_campaign=Elm%20Weekly&utm_medium=email&utm_source=Revue%20newsletter>

- Elm Colour Palette

<https://package.elm-lang.org/packages/tesk9/palette/latest/>

- Elm 3d Scene <https://github.com/ianmackenzie/elm-3d-scene>

- Elm-Graphql

- Elm-Geometry <https://github.com/ianmackenzie/elm-geometry>

- Elm Visualization

<https://package.elm-lang.org/packages/gampleman/elm-visualization/latest/>

- Elm Line Chart

<https://package.elm-lang.org/packages/terezka/line-charts/latest>

- Elm Particles

<https://package.elm-lang.org/packages/BrianHicks/elm-particle/latest/>

- Elm Units

<https://package.elm-lang.org/packages/ianmackenzie/elm-units/latest/>

- Community

- Game Jam

<https://itch.io/jam/elm-game-jam-4?utm_campaign=Elm%20Weekly&utm_medium=email&utm_source=Revue%20newsletter>

- Videos to Watch

- Teresa Sokol on Parsers <https://www.youtube.com/watch?v=M9ulswr1z0E>

- Tutorials

- Elm example

<https://dev.to/nimmo/the-basic-elm-example-that-i-wish-id-had-40m8>

- Another Elm example <https://dev.to/selbekk/my-first-elm-app-c70>

- Exercises <https://exercism.io/tracks/elm/exercises>

- Elm Koans <https://github.com/robertjlooby/elm-koans>

- Elm Wrokshop <https://github.com/rtfeldman/elm-0.19-workshop>

- Books

- <https://www.brianthicks.com/json-survival-kit/> Consider getting this.

Json decoding and encodinig seems hard.

- <https://elmprogramming.com/>

- Data Types

type is inffered, but we can annotate types. type names are capitalised

- :PROPERTIES: :ID: pa7YFV13S :END: #+title: Elm

- Starters

- Elm Pages <https://elm-pages.com/>

- Elm- SPA

- Language

- Function

-   arguments are seperated by space
-   name the arguments as variables after the function name

`over9000 powerLevel = if powerlevel > 9000 then "it's over 9000!!!" else "meh"`

- Local Variables

-   *Let* code block will allow you to declair local variables.

- Currying

-   parcially complete a function to create a curry function

- Piping

-   \'\|\>\' allows you to put take the output of the first function and send it as input in the second function

- Anonymous Functions

-   \'\' declares an Anonymous function

- Infix functions

-   all non-alpha numeric symbol combination can be used as names of infix functions
-   back ticks lets you use pre-fix functions as infix functions
-   parenthesis allow infix functions to be pre-fix functions.

- Composition

-   you can compose functions with the composition opporatore \"\>\>\"

- Lists

-   values in the list must all have the same type.
-   List function takes a list and does stuff to it.

- Tuples

-   tuplees can hold a fixed number of values. `(True, "Name Accepted")`

- Records

-   a record is a set of key-value pairs. it is written like this:

    `bill = `

-   this will update values in a record

    ``

-   updates are non-destructive. New records are created

- Union Types

declaring a type composed of other types separated by \'\|\'

e.g.

pattern matching case msg of

- Maybes

- Types

-   type aliases can be used as a function to construct objests from types

- Higher Order Function

-   e.g List.map

-   Elm Architecture

-   Model

-   model type alias

-   model initial state

    -   Update

    what can happen in our app, how should the model change when these things happen.

-   msg is usually a union type listing all the things that can happen in our app

-   an update function that recieves a msg, a model and return 2 parameters

\'

- Libraries

- Elm-spa

<https://www.elm-spa.dev> a framework for elm

- Elm-Pages

<https://package.elm-lang.org/packages/dillonkearns/elm-pages/latest/> Static site generation with elm

- Tooling

<https://medium.com/@byteshiva/how-to-install-elm-on-archlinux-dcc1b2e2c525>

- Libraries and Tools

- Create Elm Apps

<https://github.com/halfzebra/create-elm-app>

- Elm Ui

-   Shows how to build UI with elm ui

<https://korban.net/elm/elm-ui-patterns/tabs>

- Elm Narrative Engine

<https://github.com/jschomay/elm-narrative-engine>

- Monocle

<https://package.elm-lang.org/packages/arturopala/elm-monocle/latest/?utm_campaign=Elm%20Weekly&utm_medium=email&utm_source=Revue%20newsletter>

- Elm Colour Palette

<https://package.elm-lang.org/packages/tesk9/palette/latest/>

- Elm 3d Scene

<https://github.com/ianmackenzie/elm-3d-scene>

- Elm-Graphql

- Elm-Geometry

<https://github.com/ianmackenzie/elm-geometry>

- Elm Visualization

<https://package.elm-lang.org/packages/gampleman/elm-visualization/latest/>

- Elm Line Chart

<https://package.elm-lang.org/packages/terezka/line-charts/latest>

- Elm Particles

<https://package.elm-lang.org/packages/BrianHicks/elm-particle/latest/>

- Elm Units

<https://package.elm-lang.org/packages/ianmackenzie/elm-units/latest/>

- Community

- Game Jam

<https://itch.io/jam/elm-game-jam-4?utm_campaign=Elm%20Weekly&utm_medium=email&utm_source=Revue%20newsletter>

- Videos to Watch

- Teresa Sokol on Parsers

<https://www.youtube.com/watch?v=M9ulswr1z0E>

- Tutorials

-   Elm example <https://dev.to/nimmo/the-basic-elm-example-that-i-wish-id-had-40m8>
-   Another Elm example <https://dev.to/selbekk/my-first-elm-app-c70>
-   Exercises <https://exercism.io/tracks/elm/exercises>
-   Elm Koans <https://github.com/robertjlooby/elm-koans>
-   Elm Wrokshop <https://github.com/rtfeldman/elm-0.19-workshop>

- Books

-   <https://www.brianthicks.com/json-survival-kit/> Consider getting this. Json decoding and encodinig seems hard.
-   <https://elmprogramming.com/>

- Settings

-   Data Types

type is inffered, but we can annotate types. type names are capitalised
