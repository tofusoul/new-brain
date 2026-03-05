---
title: IPython
date: 2023-12-19
---

## Input and Output Caching
input and output 
## Magic Functions
- `%` are line magic functions
- `%%` are cell magic functions 

### `%run`
- will run a file in the same directory
- with the -d arg run the file through the pdb (ipdb) debugger
    - it will put the breakpoint at the first line of the file

### `%time`
- excecution time of the script
### `%timeit` or `%%timeit`
- execution time of the line

### `%prun`
- profiles the run, e.g. how many times are which functions executed
## Debugging
### Embedding ipython
```python 
from IPython import embed; embed()
```

- if you execute the script, will run the programme untill the point of the 'embed()' funciton, we can then poke around the enviroment and test things. when we exit ipython, the code execution will continue

### `%run -d`
- will run a python file setting the breakpoint to the start
### `%debug`
- will run the code in the debugger at the last exception
