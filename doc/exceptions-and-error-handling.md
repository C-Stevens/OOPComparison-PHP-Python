[<-- Return to index](../README.md)
# Errors and Exception Handling

### How are errors/exceptions treated?
#### PHP
Errors in PHP can be detected with a `try` block and a `catch` block. The code in the `try` block will be attempted and if any errors are encountered, the code in the `catch` block will execute. If there were no errors in the `try` code execution, the code in the `catch` block will be skipped.

Exceptions can be thrown manually with the `throw` keyword. Since exceptions [are classes](https://secure.php.net/manual/en/class.exception.php) in PHP, you can still access all their inherited methods and properties.
```php
<?php
function foo($bar) {
	if($bar == "baz") {
    	throw new Exception("Bar is equal to baz!");
    }
    return true;
}

try {
	foo("baz");
catch(Exception $e) {
	print "An exception was caught: ".$e->getMessage();
}
?>
```
Will yield:
```
An exception was caught: Bar is equal to baz!
```

Custom exceptions can also be defined, since exceptions are objects:
```php
<?php
	class myError extends Exception {
    	public function reportError() {
        	return "There was an error!";
        }
    }
?>
```
#### Python
Python differentiates between syntax errors and exceptions. Syntax errors raise at execution time and as one would expect only raise when there is invalid structure to the Python code.

Exceptions are raised when an error is encountered at some point during code execution. Exceptions can be caught using the `except` keyword. in a `try` block. If the code in a `try` block encounters any error, the code in the `except` block will be executed. Otherwise, the code in the `except` block will be skipped.

The `try` block can match a specific exception or catch all exceptions. If an exception is raised that is not handled by the `try` block, the exception will raise uncaught and terminate the program execution.

```python
>>> 10/0 // An uncaught exception
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ZeroDivisionError: division by zero

try:
	10/0
except ZeroDivisionError: // Catch only ZeroDivisionError exceptions
	print("Divided by zero!")

try:
	10/0
except: // Catch any exception thrown
	print("Some exception was thrown!")
```

Exceptions can be manually thrown as well:
```python
>>>raise NameError
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError
```

Python has many [built-in exceptions](https://docs.python.org/3/library/exceptions.html#bltin-exceptions), but you can also make your own by subclassing the `Exception` class:
```python
class myError(Exception):
	pass

>>>raise myError
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  __main__.myError
```
