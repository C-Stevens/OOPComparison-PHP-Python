[<-- Return to index](../README.md)
# Classes

### Definition
#### PHP
```php
<?php
    class myClass {
        public $foo = 1
        public function returnFoo() {
            echo $this->foo;
        }
    }
?>
```
#### Python
```python
class myClass:
    foo = 1   
	def returnFoo(self):
    	return self.foo

```

### New instances of a class
#### PHP
```php
$foo = new myClass();
```
#### Python
```python
foo = myClass()
```

### Class construction/initialization
#### PHP
PHP classes are constructed by defining a [`__construct()`](https://secure.php.net/manual/en/language.oop5.decon.php) method.
```php
<?php
	class myClass {
    	function __construct($foo) {
        	$this->foo = $foo;
        }
    }
?>
```
#### Python
Python classes are constructing by defining a [`__init__`](https://docs.python.org/2/reference/datamodel.html#object.__init__) method.
```python
class myClass:
	def __init__(self, foo):
    	self.foo = foo
```

### Class deconstruction/deinitialization
#### PHP
Destructor  in PHP will be called once there exist no references to an object. These are created by defining a [`__destruct()`](https://secure.php.net/manual/en/language.oop5.decon.php#destructor) method.
```php
<?php
	class myClass {
    	function __destruct() {
        	echo "Goodbye";
        }
    }
?>
```
#### Python
Python supports deconstruction in two ways. One, when an object is created with the intention of being a [context managers](https://docs.python.org/3.6/reference/datamodel.html#with-statement-context-managers) and two, by use of the `__del__()` method.

The `__del__()` method will be called when Python's garbage collector deallocates its memory once there are no longer any references to the object. It should be noted that use of this function is generally frowned upon by most Python developers, who instead either construct their objects in such a way to be used as context managers, or let the native Python garbage collector handle object deconstruction.
```python
class myClass:
	def __init__(self, foo):
    	self.foo = foo
    def __del__(self):
    	print("Goodbye")
```

The other form of object deinitialization is when an object is being used as a context manager. This behavior is not called specifically when the object is about to be deallocated, but rather at the end of some logical operation. In this way, developers can manually and specifically call cleanup methods, reset variables, etc. while within a particular context. Practically, this means objects will only have their exit called when being treated in code as a context manager, which means being called with the `with` keyword. The "deconstructor" itself is created by defining a `__exit__()` method:

```python
class myClass:
	def __init__(self):
    	print("Object has been created")
    def __enter__(self):
    	print("Object entered with runtime context")
    def __exit__(self):
        print("Object called as runtime context is ending")
    def doStuff(self):
        print("Object is doing stuff")
```
Here, `__init__()` is called at the time the object is created, or being spawned. `__enter__()` will be called when Python enters a runtime context with the object (see below), and likewise `__exit__()` will be called upon leaving the runtime context (either with error or successfully). To use objects in this way, the `with` keyword is used:
```python
with myClass() as foo:
    foo.doStuff()
```
