Reading note of Effective Python

## Chapter 1
- Use generator (same grammar as list comprehension but use rounded bracket instead) for large data. (9)
- Use `enumerate()` rather than `range()` for loops. (10)
- Use `else` block for codes you don't deal with exceptions there, and minimize `try` block. (13)
- Note `if v:` is equivalent to `if len(v) != 0`. (2)
    - I don't really like the former though.

## Chapter 2
- Throw an exception rather than returning `None`. (14)
- Remember setting a variable in an inner function (closure) just defines the variable within it, not changing the outer function's variable.
    - Use `nonlocal` if necessary, but consider using a helper class to keep readability. (15)
- Consider using `yield` instead of returning a list. (16)
    - But its behavior can be tricky. (17) 
- The default argument is evaluated only once. (20)
- Separate by `*` to begin keyword-only arguments. (21)

## Chapter 3
- Don't overuse dictionary to store complex data. Make a helper class. (22)
    - Or use `collections.namedtuple` if it's not that complex.
- Define `__call__()` to make a class instance callable to use as a stateful hook (a method to customize the behavior of other methods by being called within them). (23)

## Chapter 4
- Use @property decorator instead of getter and @var.setter instead of setter
- Define a descriptor class instead of repeating @property routines
    - Use WeakKeyDictionary, which allows GC to run, to prevent memory leaking

## Chapter 5
- (not very clear what coroutines essentially are) (40)
    - Here’s a clearer explanation: http://dabeaz.com/coroutines/Coroutines.pdf
    - Mixing generator and coroutine isn’t a good idea.
