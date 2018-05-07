[<-- Return to index](../README.md)
# Types

### What types does the language support?
#### PHP
Supported types include:
  * String
  * Integer
  * Float
  * Boolean
  * Array
  * Object

As well as `null`.
#### Python
For numbers, Python will dynamically change types internally as needed (for specificity, length, etc.). However, you can manually force Python to use a specific number type if needed. Number types include `int`, `long`, and `complex`, and types can be manually set by use of their respective methods, [`int()`](https://docs.python.org/3.6/library/functions.html#int), [`float()`](https://docs.python.org/3.6/library/functions.html#float), and [`complex()`](https://docs.python.org/3.6/library/functions.html#complex).
Other supported types include:
  * String
  * List (array)
  * Tuple
  * Dictionary 
  * Object

As well as `None`.

### Are reference and value types supported?
#### PHP
By default, PHP will pass types by value.

However, PHP allows for variables and references returned from functions to be passed and referred to by reference by prefacing variables with `&`.
```php
<?php
	function foo(&$bar) {
    	$bar++;
    }
    $baz = 5;
    foo();
    print($baz);
?>
```
Will yield `6`.

#### Python
Python has no explicit rules for declaring how variable types are passed. If an object, tuple, array, etc. is passed in Python the object's reference will be passed rather than its value.
```python
def foo(bar):
	bar.append(3)
baz = [0, 1, 2]

>>>print(baz)
[0, 1, 2]

foo(baz)

>>>print(baz)
[0, 1, 2, 3]
```

However when passing strings or numbers, Python will behave as if they are passed by value. For example, when passing a number:
```python
def foo(bar):
	bar+=1
    print("Bar from inside foo: %d"%bar)
baz = 4

>>>print(baz)
4
>>>foo(baz)
Bar from inside foo: 5
>>>print(baz)
4
```


### Can new value types be created?
#### PHP
PHP does not allow for creation of new types. The closest you can get to this behavior would be to define a new class, but PHP treats all defined classes generically as [class objects](https://secure.php.net/manual/en/language.types.object.php).
#### Python
Not natively. Python allows for extensions and has [documentation for defining new types](https://docs.python.org/3.4/extending/newtypes.html), but this requires a separate compilation step and programming in C, the functionality is not native to in-language tools.
