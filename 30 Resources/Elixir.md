---
id: Elixir
aliases:
  - first one is index zerore, second one is index one
tags: []
---

- #note Putting this idea on hold for now. Elixir is a bit too out there as a language for what I want to do.
- #note this note was a mess, hell of a lot of stuff to clean up. Where it was too hard, it was just removed.

- Tasks

## [ ] learn the inss and outs of elixir structs 

- Concepts

## Immutable Data

all variables are immutable by default

## Basic Types

### Functions

-   Bare words are functions or variables
-   question mark (?) can be used in function names
    -   convention is to only use question mark for functions that return a boolean

1.  Passing reference to a function

    ``` elixir 
    def build_grid(some_list_of_lists) do
        some_list_of_lists
        |> Enum.chunk(3)
        |> Enum.map(&mirror_row/1)
        - the ampersand before a function and the arity number after it passes the reference to the function below
      end

      def mirror_row(row) do
        [first, second | _tail] = row
        row ++ [second, first]
      end
    ```

### Atoms

-   looks like ":ok"
-   Symbols whose name is its value. ​
-   Booleans are also atoms ​
-   module names are atoms (even if not declared) ​
-   Use atoms to reference modules from erlang
-   generally used to codify strings used for programe control

### Strings

-   Strings are UTF-8
-   Supports breaks and escape sequences

1.  Functions

    ```elixir
    iex> "hello" <> " world"
    "hello world"
    ```

## Patern Match

pattern matching is elixir's equivalent of assignment everytime you have the equal sign you are pattern matching

``` elixir
colour1 = ["red"] # assings the whole list to clour one
# whereas...
[colour1] = ["red"] # assigns the string "red" to the variable colour1
```

## Operations

### Arithmetic

The usual stuff, but

1.  "/" will always return float.

2.  Modulo Operation

    ``` elixir
    rem(10, 3)
    ```

### Boolean

Boolean operators *can take all types*.

  Operation   Operator   Notes
  ----------- ---------- --------------------------------------
  Or                     Requires first argument to be boolea
  And         &&         Ditto
  Negation    !          

### Comparison

allows comparison between int and float - String Interpolation Same as Ruby: iex> var = "Andy" iex> "hello " "Hello Andy" String Concatenation "Hello " <> var -- joins the string

------------------------------------------------------------------------

### Pipe

pipes pipe the output to the first argument of the next function

## Collections

### Lists

1.  Lists can include multiple types. ​

2.  Prepend and append lists with ++ (prepend fast)

3.  ​Subtract with -- ​

4.  hd == head ​

5.  tl == tail ​

6.  Use cons operator `|` to split list into head and tail

    ``` elixir
    [head | tail] = [3.14, :pie, "Apple"]
    [3.14, :pie, "Apple"] 
    iex> head 3.14 
    iex> tail [:pie, "Apple"]
    ```

### Tuples

e.g. Fast to access but slow to modify, stored in memory. Commonly used to return additional information from functions

``` elixir
toopil = 
# first one is index zerore, second one is index one
```

### Maps

1.  Key-value store, but unlike keyword lists:

    -   Keys can be any type,
    -   unordered.
    -   Deined with %syntax
    -   Variables are allowed as map keys
    -   If duplicates of keys are added to the Map, it will replace the previous value e.g. : iex> map = % %

    Below is the notation to access the value with the key iex> map[:foo] "Bar" iex> map["hello"] :world Special syntax for declaring maps that contain only atom keys

    ``` elixir
    iex> map = %
    %
    ```

2.  Special syntax for accessing atom keys

    ``` elixir
    iex> map.hello
    "World"
    ```

    Maps have their own syntax for updates

    Either with a function functions listed in the [official docs](https://hexdocs.pm/elixir/Map.html) or with a special syntex

    ``` elixir
    iex> map = %
    %
    iex> %
    %
    ```

### Keyword Lists

Keyword Lists e.g. [foo: "bar", hello: "world"] A list of tuples (key value pairs) effectively like writing: [, ]

-   you can youse the same key for multiple pairs
-   Keys are atoms
-   Keys are ordered
-   Keys may not be unique Commonly used to pass options to functions

``` elixir
```

### Struct

Like a map but with default

## Case Statements

switch between the various cases (don't use nested ifs)

``` elixir
case status do
  :ok -> :erlang.binary_to_term(binary)
  :error -> "Dude.. No file... "
end
```

## List Comprehension

effectively a map

``` elixir
def create_deck do
    values = ["Ace", "Two", "Three", "Four", "Five", "Jack", "Queen", "King"]
    suits = ["Spades", "Clubs", "Hearts", "Diamonds"]

    for suit <- suits do
      for value <- values do
      "- of #"
      end
    end
    - this creates a nested list
    for suit <- suits, value <- values do
      "- of #"
      - this createsa flat list
    end
```

## String Templating

effectively string interploation

``` elixir
name = "Andrew"
state = "happy"
tweet = "- is #"
```

## Docs

``` elixir
@moduledoc """
After including ex_docs as deps, include these in comments, and compile with "mix docs"
"""

@doc """
put this in front of function to document the function
"""
```

# Shell Commands

## Installation and other tools

  command            what it does              notes
  ------------------ ------------------------- -------
  pacman -S elixir   installs elixir in arch   

## Mix

package and build tool

  command                 what it does                          notes
  ----------------------- ------------------------------------- -------
  mix new *projectname*   cr eate a project                     
  mix deps.get            fetches dependencies                  
  mix docs                generates documentation from source   
  mix test                runs tests                            

### mix.exs

configurations for the project

## iex

### interactive elixir

  command      what it does          notes
  ------------ --------------------- -------
  iex -S mix   runs iex on project   

### functions inside the shell

  command          what it does          notes
  ---------------- --------------------- -------------------------------------
  recompile        recompiles the file   any updates to the files gets built
  [ctrl]+[c]   shuts the shell       

- Tests

## Doc test

run tests on the examples in the documentation specific requirements for examples to be compiled as such

-   start with '## Examples'
-   three tabs (or 6 spaces) then code

- Modules

collection of functions and methods

- Core Library

## [Enum](https://hexdocs.pm/elixir/Enum.html#content)

- Libraries

<https://github.com/devinus/poison> <https://github.com/codedge-llc/scribe>

- Erlang

erlang interop

-   `:erlang` calls erlang functions

- Learning Resources

-   Udemy Course <https://www.udemy.com/course/the-complete-elixir-and-phoenix-bootcamp-and-tutorial/learn/lecture/5427958#overview>
-   Elixir Docs <https://elixir-lang.org/docs.html>
-   Learn Elixir in y minutes <https://learnxinyminutes.com/docs/elixir/>
-   30 Days of Elixir <https://github.com/seven1m/30-days-of-elixir>
-   Awesome Elixir <https://github.com/h4cc/awesome-elixir>
-   Elixir School <https://elixirschool.com/en/>
-   Elixir Examples <https://elixir-examples.github.io/>
-   Elixir recipes <http://elixir-recipes.github.io/>
-   Elixir Koans <http://elixirkoans.io/>
-   Elixir Course <https://coursesity.com/course-detail/elixir--start-programming-on-best-concurrent-language>
-   Elixir Udemy Course <https://www.udemy.com/course/learn-elixir-beginner/?siteID=Fh5UMknfYAU-XqYjZCwCPH7zQAlBeVnySQ>

- Phoenix

## Leaarning tasks

### Understand [[30 Resources/Reference/Plug]]

<https://github.com/elixir-plug/plug>

-   the readme

<https://hexdocs.pm/plug/Plug.Conn.html>

-   the conn struct

## Resources

### live view course

<https://pragmaticstudio.com/courses/phoenix-liveview>

## Concepts

### Application flow

1.  Phoenix.Endpoint

    contains the common/ and initial paths that all requests goes through, if something needs to happen to all requests it goes to the endpoint

2.  Phoenix.Router

    dispatches verb/path pairs to controllers also allows us to scope functionalities (e.g. authentication)

3.  Phoenix.Controller

    Retrieve request, talk to business logic, and prepare data for presentation

4.  Phoenix.View

    handles the structured data from the controller and converts it to a presentation to be shown to users

### Resources

for every resource there will be:

-   1 controller
-   1 model
-   1 view
-   1 folder inside templates directory

## Setup

### Setup DB

used the instruction [here](https://wiki.archlinux.org/index.php/PostgreSQL) to install and initiate the postgresql server

## Commands

  ---------------------------------------------------------------------------------------------------------------------------------------------
  command                                    what it does                           notes
  ------------------------------------------ -------------------------------------- -----------------------------------------------------------
  mix phoenix.new *project~name~*            Creates a pheonix project              
  mix ecto.create                            initiates the database                 have to set up the db server first
  mix phoenix.server                         starts a live server for the project   
  iex -S mix phoenix.server                  runs server inside iex                 
  mix ecto.gen.migration *migration~name~*   generates a db migration               edit the generated file in the file generated
  mix ecto.migrate                           migrates the db                        
  mix phx.routes                             lists the routes                       
  ---------------------------------------------------------------------------------------------------------------------------------------------

## Keywords

  keyword   purpose
  --------- -----------------------------------------------------------------------------
  import    take all the functions from the imported module to give to the other moduel
  alias     don't have to have the module name before the function call
  used      fancy

## CSS

Phoenix bundles Bootstrap css by default you can just include any CSS and you will be able to use it in the project

### tailwind css

I want to try tailwind css <https://pragmaticstudio.com/tutorials/adding-tailwind-css-to-phoenix>

## Project Structure

## Nameing Conventions

naming conventions are important

## Database

priv/repo/migrations

## Router

Matches http requests to controller actions

  ----------------------------------------------------- ------------------------- --------------------------
  Intent                                                Action                    Controller function Name
  <30>                                                                           Note:this is convenional
  see the form to create new topic                      GET '/topics/new'       new
  submit the form to create new topic                   POST "/topics"          create
  get list of all topics                                GET '/topics'           index
  delete topic with id of 12                            DELETE '/topics/12'     delete
  See the form to update an existing topic with id 12   GET '/topics/12/edit'   edit
  submit a form to update a topic with id 12            PUT 'topics/12'         update
  ----------------------------------------------------- ------------------------- --------------------------

## Plug

The heart of Phoenix's http layer, Endpoints, Routers and Controllers are all just plugs. Plugs are both:

1.  A specification for composable module between web applications
2.  Connection Adaptors for different web servers in BEAM

There are two types of plugs, function plug and module plug

### Function Plugs

Any functions that accepts a [[Conn]] struct (%Plug.Conn) and options, then returns a conn. is a function plug

### Module Plugs

Connection Transformation can be defined in a module. The module needs two functions:

-   init/1
-   call/2

### Conn

the massive struct that gets passed around <https://hexdocs.pm/plug/Plug.Conn.html>

## View

### Templates

1.  Layout
> layout template is at 'lib/hello~web~/templates/layout/app.html.eex' <%= @innercontent %> is where the normal template file is inserted

2.  EEX
    2.1.  Assigns
        values passed from the controller to the view as <%= @massenger %>

# Coding Challenges
## A function that generates palindrome numbers

## A Palindrome checker for word lists
