[<-- Return to index](../README.md)
# Unique Features

### Does the language have any unique features?
#### PHP
* Loosely typed
	- PHP does not require specific type declaration of variables at creation. Instead, their types can be inferred based upon what is stored in them.
	```php
    $foo = 4;
    $bar = "Hello";
    $baz = array();
    ```
    PHP also does not restrict variables to specific types, even after their type is inferred.
    ```php
    $foo = 4;
    $foo = "string";
    ```
* Built-in regular expression support
	- PHP natively can use regular expressions programatically. Complex string parsing can be achieved this way, for example extracting a domain name from a URL ([via the PHP manual](https://secure.php.net/manual/en/function.preg-match.php))
	```php
    preg_match('@^(?:http://)?([^/]+)@i', "http://www.php.net/index.html", $matches);
	$host = $matches[1];
    ```
* Single inheritance
	- PHP allows for a subclass to extend only one super class. This allows for greater code reusability.
#### Python
* Loosely and dynamically typed
	- Like PHP, Python does not require variable type declarations at creation time, and variables can change type even after their type is inferred from initial assignment.
	```python
    foo = 1
    bar = "Hello"
    baz = []
    
    foo = "string"
    ```
* Multiple inheritance
	- Unlike PHP, Python allows a subclass to extend multiple super classes. This carries with it increased complexity but allows for complicated and sophisticated object oriented code in the correct hands.
	```python
    class SubClass(SuperClass, SuperClass2, SuperClass3, ...):
    	pass
    ```
* Easy modualization and packaging
	- Python allows for the modularization and packaging of any code, aided by its simple import behavior. Python allows for select methods to be imported as well.
	```python
    import yourPackage
   	from yourOtherPackage import method1, method2
    ```
* Built-in memory management
	- Python will automatically allocate and deallocate memory with its native garbage collection service.
