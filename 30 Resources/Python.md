---
id: Python
aliases: []
tags: []
---

- [ ] split this docs into multiple subjects, for readability

# Online Resources 
## Basics 
- [w3schools python tutorial](https://www.w3schools.com/python/default.asp)
- [Python Practice Book](https://anandology.com/python-practice-book/getting-started.html)
- [Think Python](https://greenteapress.com/thinkpython/html/index.html)
- [How to think like a computer scienteist](https://runestone.academy/runestone/books/published/thinkcspy/index.html)
## Advanced
- [James Powel, "So you want to be a python expert?"](https://www.youtube.com/watch?v=cKPlPJyQrt4&t=3325s)
# - General
- [Real Python](https://realpython.com/)
- [Python Cheat Sheet](https://www.pythoncheatsheet.org/)
- [bokeh](https://github.com/bokeh/bokeh)

# Syntax 

- `?` with a function name will return the docstrin

## Decorators 

- Wraps a function in another function, e.g:

```python
@dataclass(kw_only = True) # this is a decorator on a class that enables the dataclass way of constructing objects 
class Square(Shape):
    width: int 

@property # 
def area(self)-> int:
   return width * width
```

## Generators 
- for loop with yields function inside, lazy evaluates
- no storage of returned value
- effectively a co-routine
- yield with no value to yield control of execution

## Protocols 

- [read the docs](https://mypy.readthedocs.io/en/stable/protocols.html)

## Import

- [how to import other files](https://stackoverflow.com/questions/2349991/how-do-i-import-other-python-files)

## Types 

- [x] read the docs on [python typing](https://docs.python.org/3/library/typing.html) 
- Python is *Dynamically typed*, i.e. type is resolved at runtime and not compile time, however the tooling around typing is pretty good for checks while editing if *type hints* are used. 
- Strictly speaking python uses *Duck typing* or technically called *protocol oriented programming*
    - As long as the relevant *protocol* is implemented in the object, python will treat it like that object. i.e the proverbial "if it looks like a duck and it quacks like a duck..."
    - Corey Schafer has a [great explanation of this ](https://www.youtube.com/watch?v=x3v9zMX1s4s&t=35s) which includes error handling
- Type-Checker helps with keeping types consistant
- Type Aliases are done through the mechanisms of [NewType](https://stackoverflow.com/questions/58755948/what-is-the-difference-between-typevar-and-newtype/58775376#58775376)

``` python

    from typing import NewType 

    UserId = NewType('UserId', int)

    def getuser(x: UserId): ...

    getuser(UserId(123456)) 
    # this is fine getuser(123456) - that's an int, not a UserId

    UserId(123456) + 123456 
    # fine, because UserId is a subclass of int

```

2.  from [this link](https://stackoverflow.com/questions/58755948/what-is-the-difference-between-typevar-and-newtype/58775376#58775376) on stack overflow


## Built in Types:
- [[Strings (python)]] 

##  Generators 

1.  [ ] corey schafer's [generators tutorial](https://www.youtube.com/watch?v=bD05uGo_sVI) is great, note the contents here
2.  [ ] this guy's [tutorial on generators and itterators](https://www.youtube.com/watch?v=u3T7hmLthUU) is less clear but more detailed

## [[Python Data Structures]]
### Enums 
Enums are classes you can inherit
### Lists 
- order is preserved
- each list item is an object
# list comprehension
1.  Examples:

```python
# the form of python list comprehention
newlist = [expression for item in iterable if condition == True]

# e.g.
obj = ["Even" if i%2==0 else "Odd" for i in range(10)]
# ['Even', 'Odd', 'Even', 'Odd', 'Even', 'Odd', 'Even', 'Odd', 'Even', 'Odd']

# you could also apply the expression in a nested way
matrix = [[1, 2], [3,4], [5,6], [7,8]]
transpose = [[row[i] for row in matrix] for i in range(2)]
# assign transpose as: [[1, 3, 5, 7], [2, 4, 6, 8]]
```

## Dictionaries 
- name value pairs, name is a string, value is an object
- basically JSON with different brackets

### Dictionary Comprehension

1.  [Python dictionary comprehension](https://cdn.programiz.com/sites/tutorial2program/files/Python-dictionary-comprehension.png)


##   Sets 
- members must have unique, no duplicates
- can only have immutable objects( no lists, dictionaries etc)

### Set methods:

1.  `set.remove(member)`
    - throws a key error if member isn't in the set
2.  `Set.discard(member)`
    - not throw an error when member isn't in the set
3.  Set Operations
    1.  union
        - can use '&' as binary operator
    2.  intersection
        1.  can use or as binary operator


- [Video Tutorial for ReST apis in Python](https://www.youtube.com/watch?v=Sg5VTTBIhqo&t=776)

# Tools 
## ipython
- is built in to the python distribution now

# - Jupyter Notebooks

## - <https://towardsdatascience.com/9-magic-command-to-enhance-your-jupyter-notebook-experience-101fb5f3a84>

## [[Dataclasses]]

# Dunder Methods 


## Unary operators and functions

```python 
__new__(cls)
# To get called in an object's instantiation.

__init__(self)
# To get called by the __new__ method.

__del__(self) 
# Destructor method.
def__abs__(self) 
# To get called by built-in abs() function.

__invert__(self) 
# To get called for inversion using the \ operator. 

__round__(self,n) 
# To get called by built-in round() function. 

__floor__(self) 
# To get called by built-in math.floor() function. 

__ceil__(self) # To get called by built-in math.ceil() function. 

__trunc__(self) 
# To get called by built-in math.trunc() function. Augmented Assignment Description 
```

Binary Operators 

```python

__iadd__(self, other) 
# To get called on addition with assignment e.g. a +=b. 

__isub__(self, other) 
# To get called on subtraction with assignment e.g. a -=b. 
__imul__(self, other) 
# To get called on multiplication with assignment e.g. a \*=b. 

__ifloordiv__(self, other) 
# To get called on integer division with assignment e.g. a //=b. 
__idiv__(self, other)  
#To get called on division with assignment e.g. a /=b. 

__itruediv__(self, other) 
# To get called on true division with assignment 
__imod__(self,\ other) 
# To get called on modulo with assignment e.g. a%=b. 

__ipow__(self, other) 
# To get called on exponentswith assignment e.g. a **= b. 
__ilshift__(self, other) 
# To get called on left bitwise shift with assignment e.g. a<<=b. 
__irshift__(self, other) 
# To get called on right bitwise shift with assignment e.g. a >>=b. 
__iand__(self, other) 
# To get called on bitwise AND with assignment e.g. a&=b. 
__ior__(self, other) 
#To get called on bitwise OR with assignment e.g. a|=b. 
__ixor__(self, other) 
#To get called on bitwise XOR with assignment e.g. a \^=b. Type Conversion Magic Methods Description 
__int__(self) #To get called by built-int int() method to convert a type to an int. 
__float__(self) #To get called by built-int float() method to convert a type to float. 
__complex__(self) #To get called by built-int complex() method to convert a type to complex. 
__oct__(self) #To get called by built-int oct() method to convert a type to octal. 
__hex__(self) #To get called by built-int hex() method to convert a type to hexadecimal. 
__index__(self) #To get called on type conversion to an int when the object is used in a slice expression. 
__trunc__(self) #To get called from math.trunc() method. String Magic Methods Description 
__str__(self) #To get called by built-int str() method to return a string representation of a type. 
__repr__(self) #To get called by built-int repr() method to return a machine readable representation of a type. 
__unicode__(self) #To get called by built-int unicode() method to return an unicode string of a type. 
__format__(self, formatstr) #To get called by built-int string.format() method to return a new style of string. 
__hash__(self) #To get called by built-int hash() method to return an integer. 
__nonzero__(self) #To get called by built-int bool() method to return True or False. 
__dir__(self) #To get called by built-int dir() method to return a list of attributes of a class. 
__sizeof__(self) #To get called by built-int sys.getsizeof() method to return the size of an object. Attribute Magic Methods Description 
__getattr__(self, name) # Is called when the accessing attribute of a class that does not exist. 
__setattr__(self, name, value) #Is called when assigning a value to the attribute of a class. 
__delattr__(self, name) #Is called when deleting an attribute of a class. Operator Magic Methods Description 
__add__(self, other) #To get called on add operation using + operator 
__sub__(self, other) #To get called on subtraction operation using - operator. 
__mul__(self, other) #To get called on multiplication operation using \* operator. 
__floordiv__(self, other) #To get called on floor division operation using // operator. 
__truediv__(self, other) #To get called on division operation using / operator. 
__mod__(self, other) #To get called on modulo operation using % operator. 
__pow__(self, other[modulo]) #To get called on calculating the power using \*\* operator. 
__lt__(self, other) #To get called on comparison using \< operator. 
__le__(self, other) #To get called on comparison using \<= operator. 
__eq__(self, other) #To get called on comparison using == operator. 
__ne__(self, other) #To get called on comparison using != operator. 
__ge__(self, other) #To get called on comparison using \>= operator.
```
# Testing

## [[Pytest]]
# Libraries 

## Standard Libary 

- [ ] [PyMOTW3](https://pymotw.com/3/) has some highlights on cool standard libary usage 

### Datetime 

- strptime()
    1.  <https://docs.python.org/3/library/datetime.html#strftime-and-strptime-behavior>
    2.  converts a string to a date-time

###  [[Pathlib]]

## External Libraries 
- [Keybert](https://github.com/MaartenGr/KeyBERT)

- [Google Drive API](https://towardsdatascience.com/how-to-manage-files-in-google-drive-with-python-d26471d91ecd)

- [py5](http://py5coding.org/)

## - [[Pandas]]

## - <https://github.com/msiemens/tinydb>

## - <https://github.com/graphql-python/graphene/>

# - <https://www.crummy.com/software/BeautifulSoup/bs4/doc/>

# - Json

## - <https://realpython.com/python-json/>

# - Gspread

## - <https://docs.gspread.org/en/latest/>

# - [[gspread-pandas]]

# - [[SQLAlchemy]]

- [[ASYNCIO (python)]]

- [pydoit](https://pydoit.org/)
- Pip

# - generate requirements.txt like `pipreqs /path/to/project`

# - tips form [[Stanger]]
- you can method chain in python by returning `self`
- `**kwargs` packages up undefined arguments as a dictionary for functions (inputs to callables)
    - `**` unpacks dictionary to key value pairs in, ready\'s them for arguments
- \*args is positional undefined extras
- could use that for requests.
- [[FastAPI]]!

# Editor Tooling
## Pyright
use: 
```python
 # pyright: ignore [reportUnusedCoroutine]
```
## MyPy 
- [MyPy Cheetsheet ](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html)
to ignore specific errors

# Documentation
## Docstrings
Module docstrings are bare tripple quote strings at the top of the `__init__.py` for the module, should include things like:
- A brief description of the module and its purpose
- A list of any classes, exception, functions, and any other objects exported by the module
- The docstring for a module function should include the same items as a class method:
- A brief description of what the function is and what it’s used for
- Any arguments (both required and optional) that are passed including keyword arguments
- Label any arguments that are considered optional
- Any side effects that occur when executing the function
- Any exceptions that are raised
- Any restrictions on when the function can be called

Script docstrings are likewise at the top of the script

