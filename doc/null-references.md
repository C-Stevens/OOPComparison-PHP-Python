[<-- Return to index](../README.md)
# Null/Nil References

### What does the language call these?
#### PHP
PHP calls variables with no value [`NULL`](https://secure.php.net/manual/en/language.types.null.php). Variables are NULL if they are manually assigned as such, their value has never been set to anything before, or they are unset via the [`unset()`](https://secure.php.net/manual/en/function.unset.php) method.
#### Python
Python calls variables with no value [`None`](https://docs.python.org/3/library/constants.html#None). 

### What are the features of handling these?
#### PHP
Variables can be unset via the [`unset()`](https://secure.php.net/manual/en/function.unset.php) method and will become NULL.

Variables can be checked against null via the [`is_null()`](https://secure.php.net/manual/en/function.is-null.php) method.
#### Python
In Python, `None` is actually an object, and behaves like one. Under the hood, `None` is of type `NoneType`. Variables can be checked against None programmatically just like any other object comparison:
```python
class myClass:
    def __init__(self, foo, bar):
        self.foo = foo
        self.bar = bar

a = myClass("apples", "oranges")
b = None

print("a is not None") if (a is not None) else print("a is None")
print("b is not None") if (b is not None) else print("b is None")
```
Will yield:
```
a is not None
b is None
```
