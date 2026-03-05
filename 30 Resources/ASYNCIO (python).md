---
title: ASYNCIO
date: 2023-12-14
---
- [Nice Demo](https://www.youtube.com/watch?v=6RbJYN7SoRs) and tutorial from some youtuber
- [another relatively terse tutorial](https://www.youtube.com/watch?v=GpqAQxH1Afc) from ArjanCodes
- [official docs](https://docs.python.org/3/library/asyncio-task.html)
- [nice tutorial](https://builtin.com/data-science/asyncio) that explains a little bit of the concetps 

- It's an abstraction over an event loop
  - works A bit like generators 
  - maps to callback functions
  - the `await` keyword demarcating when it's safe to context switch
    - it functiopns a bit like `yield` keyword for generators
    - tells the compiler when it's safe to go to another co-routine

- example:

``` python
import asyncio
import time

counter = 0

async def func1():
  global counter
  while true:
    counter += 1
    counter -= 1
    await asyncio.sleep(0)

async def func2():
  global counter
  while true:
    counter += 1
    counter -= 1
    await asyncio.sleep(0)

asyncio.gather(func1(), func2())
asyncio.get_event_loop().run_forever()
```

- we will always get 0 as the value of a counter compared to doing this with threading

- no need for locks or message queues between threads or processes

- it\'s effectively a while true loop like:

```python
while True: wait~foranyfdtobecomeready~() handle~fdcallback~()
```

- so everything is run in one thread one callback at a time.
- Can't do any kind of blocking IO e.g. `read()`
- `await` keyword also creates an event listener, that suspends the function until a response is recieved, and the event loop moves on to do other things

- e.g:

``` python
async def get_users():
  users = await client.do_query("select * from users")
  return users
asyncio.run(get_users())
```

- `await` is also the keyword for calling another coroutine

- e.g.:

``` python
async def main():
  users = await get_users()
  print(users)
```

- calls the `get_users()` function above, so it will have to await the results in the same way the `get_users()` function has to

- the event loop gets started with something like:

```python
asyncio.run(main())
```
- to run the co-routines in parallel use `asyncio.gather(...)`:

- e.g the main function will look something like:

``` python
async def main():
  await asyncio.gather(
    get_users(),
    get_data(),
  )
```

- this means, awaiting for the outcome of the coroutines concurrently before moving on

- if you use `task = asyncio.create_task(func())` you can \~\~
