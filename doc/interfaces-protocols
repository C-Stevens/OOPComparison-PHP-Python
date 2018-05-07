[<-- Return to index](../README.md)
# Interfaces/Protocols

### Does the language support interfaces/protocols?
#### PHP
Yes, PHP natively includes functionality for creating abstract classes in a way familiar to Java. Like Java, any class that contains at least one abstract method must also be abstract itself.
#### Python
Interfaces are not necessarily native to python as there is no need for them since Python supports multiple inheritances of objects. However, Python can still approximate abstract classes by inheriting from the Abstract Base Class (which Python calls `ABC`)

### If so, what abilities do they have?
#### PHP
Abstract classes can define required methods as well as define common methods.
#### Python
In Python, abstract methods can only declare what methods are required in the objects implementation by use of the `@abstractmethod` decorator. Other decorators not specifically designed for abstract methods can be used as well, but `@abstractmethod` must be the inner-most decorator.

### If they exist, how are interfaces/protocols used?
#### PHP
Abstract classes can be defined in the following way:
```php
<?php
	abstract class myAbstractClass {
    	abstract protected function foo();
        
        public function bar() { // Common method
        	print "Hello world"
        }
    }
?>
```
And can be implemented in the following way (assuming the previously defined abstract class exists):
```php
<?php
	class myConcreteClass extends myAbstractClass {
    	protected function foo() {
        	print "This is my implementation of the foo method";
        }
    }
?>
```
### Python
Abstract classes can be created in the following way (Note: the `ABC` class *must be imported!*) the following examples are based off of [this documentation](https://www.python-course.eu/python3_abstract_classes.php):
```python
from abc import ABC, abstractmethod

class myAbstractClass(ABC):
	@abstractmethod
    def foo(self):
    	pass
```
And abstract classes can be "implemented" in the following way (assuming the previously defined abstract class exists):
```python
class myClass(myAbstractClass):
	def foo(self):
    	print("This is my implementation of the foo method")
```
If a class that inherits an abstract class is created and does not implement one of the abstract methods, a `TypeError` exception will be raised.
