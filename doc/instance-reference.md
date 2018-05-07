[<-- Return to index](../README.md)
# Instance reference

### How are names referenced from within objects?
#### PHP
By use of the `this` keyword.
```php
<?php
	class myClass {
    	public $foo = 4;
        private $bar = 5;
        
        function baz() {
        	echo $this->foo;
            echo $this->bar;
        }
    }
?>
```
Will echo both variables of the class, public and private. Private variables, however, cannot be accessed directly from outside of the objects namespace.
#### Python
By use of the `self` keyword.
```python
class myClass:
	foo = 4
    def baz():
    	print(self.foo)
```
