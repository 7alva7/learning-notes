## Name convention

| Type               | Convention               | Example                     |
|--------------------|--------------------------|-----------------------------|
| Variable/Function  | Snake Case              | `my_variable`, `calculate_sum()` |
| Class              | Camel Case              | `MyClass`, `DataProcessor`  |
| Constant           | Uppercase Snake Case    | `MAX_SIZE`, `PI_VALUE`      |
| Private Variable   | Single Leading Underscore | `_internal_variable`        |
| Private Method     | Double Leading Underscore | `__private_method()`        |
| Module/Package     | Lowercase with Underscores | `my_module.py`             |

## How to create package

1. Create a directory for your package.
2. Inside that directory, create a file named `__init__.py`. This file can be empty, but it tells Python that this directory should be treated as a package.
3. Create your module files (e.g., `module1.py`, `module2.py`) inside the package directory.
4. Optionally, create a `setup.py` file to make your package installable. This file should include metadata about your package, such as its name, version, author, and any dependencies it has.

## Generator

Generators are a simple way of creating iterators using a function that yields values. The function is paused and can be resumed later, allowing it to produce a series of values over time.

```python

def simple_gen():
    for i in range(3):
        yield i

for number in simple_gen(): # This will print 0, 1, 2
    print(number)

gen = simple_gen()
next(gen) # Output: 0
next(gen) # Output: 1
next(gen) # Output: 2
```