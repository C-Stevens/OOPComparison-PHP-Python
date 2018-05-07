[<-- Return to index](../README.md)
# Object Properties

### Getters and setters
#### PHP
Object variables can be set by defining [`__get()`](http://us1.php.net/manual/en/language.oop5.overloading.php#object.get) and [`__set()`](http://us1.php.net/manual/en/language.oop5.overloading.php#object.set). PHP will call the getter and setter methods when normally inaccessable (eg. not public) properties are being either read or written respectively. The following example is based off of a [stackoverflow response](https://stackoverflow.com/questions/4478661/getter-and-setter):
```php
<?php
	class myClass {
    	private $foo;
        private $bar;
        
        public function __get($property) {
    		if (property_exists($this, $property)) {
     			return $this->$property;
    		}
  		}

 	 	public function __set($property, $value) {
    		if (property_exists($this, $property)) {
        		$this->$property = $value;
    		}
    		return $this;
  		}
    }
?>
```
Public properties can be accessed directly.
```php
<?php
	class myClass {
    	public $foo = 4;
    }
    $bar = new MyClass();
    $bar->foo = 5;
?>
```
#### Python
Python naturally assumes all attributes to be public, so the use of a getter or setter is not necessary. One can be constructed if you want in a way similar to this:
```python
class myClass():
	foo = 4
    def getFoo():
    	return self.foo
    def setFoo(value):
    	self.foo = value
```
However it's far easier to just access the properties directly, like so:
```python
class myClass():
	foo = 4

bar = myClass()

>>>>>>print(bar.foo)
4
>>>bar.foo = 5
>>>print(bar.foo)
5
```
Python can impliment getter and setters by having a variable a of the [`property` class](https://docs.python.org/3/library/functions.html#property). Since this allows for computed properties, an example of this behavior is provided in a later section.

### Do backing variables exist?
#### PHP
Backing variables can be implemented due to the ability for object properties to be either `protected` or `private` in PHP. 
#### Python
They do not exist because they aren't necessary, as object properties are presumed to all be public.

### Do computed properties exist?
#### PHP
PHP does not have built-in support for computed properties and has no good ways to simulate them. The alternative is just to created methods that do the appropriate logic on object properties when needed.
#### Python
Python can create computed properties by use of the `@property` and use of the `property` [class](https://docs.python.org/3/library/functions.html#property).  A simple example to create a property that computes the middle of a width is as follows:
```python
class myClass():
	def __init__(self, width):
    	self.width = width
    @property
    def middle(self):
        return self.width/2
```
In this instance, the `middle()` method can be accessed as if it were a normal property of the object, even though its value is computed:
```python
foo = myClass(11)
>>>print(foo.middle) # Note the lack of parenthesis (eg. not foo.middle())
5.5
```
By use of properties getters, setters, and deleters can be manually defined if specific logic is required for the individual cases. The following code is nearly identical to an example in the [Python documentation](https://docs.python.org/3/library/functions.html#property):
```python
class myClass():
	def __init__(self, width):
    	self.width = width
       @property
       def width(self): # Functions like a getter
           return self.width
       @width.setter
       def width(self, value): # Functions like a setter
           self.width = value
       @width.deleter
       def width(self):
           del self.width
```
