https://www.pythonmorsels.com/terms
https://www.pythonmorsels.com/every-dunder-method/
https://realpython.com/python-all-attribute/
https://realpython.com/python-with-statement/
https://docs.python.org/3/library/asyncio-task.html

```
sys.intern
```

```
a = [1, 2]
b = a
b is a  # True

b = [1, 2]
b is a  # False

c = b.copy()
c == a  # True
c is a  # False
```

https://rszalski.github.io/magicmethods/

```
my_coroutine = a_coroutine()
next(my_coroutine)           # advance to first yield in coroutine
my_coroutine.send(val)
```

```
def switcher():
    choice = yield "choose 1 or 2"
    if choice == 1:
        yield from generator_1
    elif choice == 2:
        yield from generator_2
```




