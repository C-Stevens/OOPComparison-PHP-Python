[<-- Return to index](../README.md)
# Comparisons of References and Values

### How are values compared?
#### PHP
When objects are compared with the comparison operator `==`, the objects will be considered equal if their attributes and values match and are both instances of the same class.

When objects are compared with the identity operator `===`, the objects will be considered equal if they both refer to the same reference of an object.
```php
<?php
	class myClass {
    	public $foo;
        public $bar;
    	function __construct($foo, $bar) {
        	$this->foo = $foo;
            $this->bar = $bar;
        }
    }
    
    $a = new myClass("apples", "oranges");
    $b = new myClass("apples", "oranges");
    $c = $a;
    
   	($a == $b) ? print "a equals b" : print "a does not equal b";
	($a === $b) ? print "a and b reference the same object" : print "a and b do not reference the same object";
	($a === $c) ? print "a and c reference the same object" : print "a and c do not reference the same object";
?>
```
Will yield:
```
a equals b
a and b do not reference the same object
a and c reference the same object
```
#### Python
Equality in Python is compared with the `==` operator. To check if two objects share the same reference, Python uses the `is` keyword. However when comparing objects, Python does not necessarily natively verify that the objects are identical purely by value like PHP. This can be resolved by manually overriding the `__eq__()` method.
```python
class myClass:
    def __init__(self, foo, bar):
        self.foo = foo
        self.bar = bar
    def __eq__(self, other):
        return self.__dict__ == other.__dict__

a = myClass("apples", "oranges")
b = myClass("apples", "oranges")
c = a

print("a equals b") if (a == b) else print("a does not equal b")
print("a and c reference the same object") if (c is a) else print("a and c do not reference the same object")
```
Will yield:
```
a equals b
a and c reference the same object
```
