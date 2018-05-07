[<-- Return to index](../README.md)
# Lambda Expressions and Closures

### How do lambda expressions work?
#### PHP
PHP allows for the assignment of anonymous inner functions to variables. The keyword for their creation is still `function`, identical to standard named function creation.
```php
<?php
    $celciusToFarenheight = function($t) { return (9/5)*t+32; };
    print $celciusToFarenheight(13);
?>
```
Will yield `55.4`.
#### Python
Python allows [lambda expressions](https://docs.python.org/3/tutorial/controlflow.html#lambda-expressions) as small anonymous (unnamed) functions. These are defined with the `lambda` keyword, and can consist of only a single expression.
```python
celciusToFarenheight = lambda t: (float(9)/5)*t+32
print(celciusToFarenheight(13))
```
Will yield `55.400000000000006`.

### How do closures expressions work?
#### PHP
PHP can access variables outside of its own scope with the `use` keyword.
```php
<?php
    $padding = 30;
    $width = function($w) use ($padding) { return $w+($padding*2); };
    print($width(100));
?>
```
Will yield `160`.
#### Python
Python can remember values in an enclosed scope even if the values are not present in memory. This can avoid use of global variables and allow for neater code. The following example was borrowed from [this documentation](https://www.learnpython.org/en/Closures) and provides an example of closure in Python:
```python
def multiplier_of(n):
    def multiplier(number):
        return number*n
    return multiplier

multiplywith5 = multiplier_of(5)
print(multiplywith5(9))
```
Will yield `45`.
