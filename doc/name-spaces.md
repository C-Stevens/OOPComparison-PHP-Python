[<-- Return to index](../README.md)
# Name Spaces

### How are name spaces implemented?
#### PHP
PHP allows for the manual creation of seperate namespaces to solve issues of inheritance and name collisions.
#### Python
Names in python are treated similarly to variables in most other languages. Since Python is very loosely typed, names can be very dynamic and applied to pretty much anything. 

### How are name spaces used?
#### PHP
* Namespaces must be manually and explicitly defined at the *very beginning* of the file.
```php
<?php
    namespace myPackage;
?>
```
* Namespace heirarchy must also be explictly defined. Sublevels between namespaces are denoted with a `\`.
```php
<?php
    namespace myPackage\namespace2;
?>
```
* Multiple namespaces can exist in a single file, but you must switch between them explicitly. The PHP manual does [not recommend](https://secure.php.net/manual/en/language.namespaces.definitionmultiple.php) this practice.
```php
<?php
    namespace myNamespace {
        $foo = "bar";
    }
    namespace myOtherNamespace {
        $foo = "baz";
    }
?>
```

* Global variables are simply names that exist in an unnamed namespace. Without any namespace definition, the default will be global space.
```php
<?php
    namespace myNamespace {
        const foo = "bar";
    }
    
    namespace { 
        $foo = "baz";
	echo "Global namespace: ".$foo;
	echo "Specific namespace: ".myNamespace\foo;
    }
?>
```
Will yeild:
```
Global namespace: baz
Specific namespace: bar
```

* PHP allows for inspection of the current namespace with the built-in `__NAMESPACE__` constant.
```php
<?php
    namespace myNamespace;
    echo '"', __NAMESPACE__, '"';
?>
```

* You can redefine or alias a valid namespace with the `use` keyword.
```php
<?php
    namespace foo;
    use bar\namespace\namespace2 as baz;
?>
```
Will yeild `"myNamespace"`.

* Also, you can select namespaces manually with the `use` keyword.
```php
<?php
    use ArrayObject; // Global class
    use function bar\namespace\myFunction; // Imports a method called `myFunction` from the bar\namespace namespace
    use function bar\namespace\myFunction as myNewFunction; // Aliases bar\namespace's `myFunction` method to the name `myNewFunction`
?>
```

#### Python
* Names can be given to entire methods:
  ```python
  def return4():
      return 4
  idLikeFourPlease = return4

  >>> return4()
  4
  >>> idLikeFourPlease()
  4
  ```

* Since Python is dynamically typed, names can be changed at a whim:
  ```python
  idLikeFourPlease = return4

  >>> type(idLikeFourPlease)
  <class 'function'>

  idLikeFourPlease = "foo"

  >>> type(idLikeFourPlease)
  <class 'str'>
  ```

* When importing modules, namespaces can be imported or merged into the current namespace.
	- Importing an entire module allows for accessing that modules namespace from within the current namespace:
	```python
    import yourModule
    print(yourModule.return4())
    ```
    - Importing specific modules (or all modules) will merge the methods into the current namespace:
    ```python
    from yourModule import return4
    print(return4())
    ```
    or:
    ```python
    from yourModule import *
    print(return4())
    
* Scopes and globals
	- Python provides scope isolation for names and will follow heirarchal rules from the inside out for determining namespace in scopes.
	```python
	var = "apples"
	def foo():
	    print(var)
	def bar():
	    var = "bananas"
	    print(var)
	
	>>> print(var)
	apples
	>>> foo()
	apples
	>>> bar()
	bananas
	>>> print(var)
	apples
	```
	- Scope can be manually overridden to the global scope by use of the global keyword.
	```python
	var = "apples"
	def foo():
	    print(var)
	def bar():
	    global var
	    var = "bananas"
	
	>>> foo()
	apples
	>>> bar()
	>>> foo()
	bananas
	```
