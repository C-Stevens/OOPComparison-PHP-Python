[<-- Return to index](../README.md)
# Inheritance/Extension

### How are classes inherited/extended?
#### PHP
Classes are extended by use of the `extends` keyword.
```php
<?php
    class myClass {
        private $foo;
        public function setFoo($value) {
            $this->foo = $value;
        }
    }

    class myOtherClass extends myClass {
        public $bar;
        public function baz() {
            print "This is a unique method that myClass doesn't have";
        }
    }
?>
```
#### Python
Classes are inherited as they are defined:
```python
class myClass:
    foo = 1
    def setFoo(value):
        self.foo = value

class myOtherClass(myClass):
    bar = "apples"
    def baz():
        print "This method is unique to myOtherClass and isn't in myClass"
```
