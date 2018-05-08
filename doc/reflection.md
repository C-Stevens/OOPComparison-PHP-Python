[<-- Return to index](../README.md)
# Reflection

### What reflection abilities are supported?
#### PHP
PHP will automatically use inspection at runtime to determine, for example, if an object being called has a particular method implemented, or that a particular object's method exists if it is being called. 
#### Python
Python has several inspection methods built natively into the language.  These include:
  * [callable()](https://docs.python.org/3/library/functions.html#callable): returns `True` if the provided object can be called.
  * [type()](https://docs.python.org/3/library/functions.html#type): returns the type of the object provided.
  * [isinstance](https://docs.python.org/3/library/functions.html#isinstance): takes two objects as arguments, and will return `True` if the first object provided is an instance of the second.
  * [dir](https://docs.python.org/3/library/functions.html#dir): returns a list of valid attributes for a provided object.
  * [getattr()](https://docs.python.org/3/library/functions.html#getattr): attempts to return the value of a provided attribute from a provided object

### How is reflection used?
#### PHP
By use of a [`ReflectionClass`](https://secure.php.net/manual/en/class.reflectionclass.php) object. You may pass an object's name to an object of this type at creation time to allow inspection of various attributes or conditions of a class. For example, the following will provide a list of available methods for a class called `myClass`:
```php
<?php
    class myClass {
        function foo() {
            print "Foo method";
        }
        function bar($baz) {
            print "Bar method";
        }
    }

    $reflector = new ReflectionClass('myClass');
    var_dump($reflector->getMethods());
?>
```
will yield:
```
array(2) { 
    [0]=> object(ReflectionMethod)#3 (2) {
        ["name"]=> string(3) "foo" 
        ["class"]=> string(7) "myClass" 
    }
    [1]=> object(ReflectionMethod)#4 (2) {
        ["name"]=> string(3) "bar" 
        ["class"]=> string(7) "myClass" 
    }
}
```

#### Python
Various object details can be determined by using the above described and linked reflection method programmatically. For example, to see if an object is an instance of a given class:
```python
class myClass:
    def foo(self):
        print("foo")

a = myClass()

>>>print(isInstance(a, myClass))
True
```
