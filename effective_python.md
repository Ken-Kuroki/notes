Reading note of Effective Python

## Chapter 1
- Use generator (same grammar as list comprehension but use rounded bracket instead) for large data. (9)
```
it = (len(x) for x in open("file.txt", "r"))
print(it)
print(it)
```

- Use `enumerate()` rather than `range()` for loops. (10)
```
for num, value in enumerate(some_list, 1):  # counting starts from 1 (NOT SKIPPING the first entry in the list!)
    print("{0}: {1}".format(num, value))
```

- Use `else` block for codes you don't deal with exceptions there, so that you can minimize `try` block. (13)
- Note `if v:` is equivalent to `if len(v) != 0`. (2)
    - I don't really like the former though.
```
if not s:
    print("len(s) is zero!")
```

## Chapter 2
- Remember setting a variable in an inner function (closure) just defines the variable within it, not changing the outer function's variable.
    - Use `nonlocal` if necessary, but consider using a helper class to keep readability. (15)
```
def f():
    i = 0
    def g():
        nonlocal i
        i = 1
    
    g()
    return i

print(f())  # returns zero without the nonlocal !!!
```

- Consider using `yield` instead of returning a list. (16)
    - But its behavior can be tricky. (17) 
```
def f():
    for i in range(5):
        yield i

list(f())  # [0,1,2,3,4]
```

- The default argument is evaluated only once. (20)
```
def f(when=datetime.now()):  # NO! This is evaluated only once
    ...
```

- Separate by `*` to begin keyword-only arguments. (21)
```
def f(i, j, *, foo=True, bar=False):  # foo and bar can only be assigned by keyword, not by position
    ...
```

## Chapter 3
- Don't overuse dictionary to store complex data. Make a helper class. (22)
    - Or use `collections.namedtuple` if it's not that complex.
- Define `__call__()` to make a class instance callable to use as a stateful hook (a method to customize the behavior of other methods by being called within them). (23)

## Chapter 4
- Use @property decorator instead of getter and @\[variable_name\].setter instead of setter (29)
```
class GetterSetter:
    def __init__(self):
        self._v = 0
    
    @property
    def v(self):
        return self._v
    @v.setter
    def v(self, new_value):
        self._v = new_value
```

- Define a descriptor class instead of repeating @property routines (31)
    - Use WeakKeyDictionary, which allows GC to run, to prevent memory leaking

## Chapter 5
- (not very clear what coroutines essentially are) (40)
    - Here’s a clearer explanation: http://dabeaz.com/coroutines/Coroutines.pdf
    - Mixing generator and coroutine isn’t a good idea.
