[<-- Return to index](../README.md)
# Singletons

### How are singletons implemented?
#### PHP
There exists no native support for singletons in PHP, but they can be approximated programmatically most easily by implementing a factory class. The following example comes from a [stack overflow response](https://stackoverflow.com/questions/203336/creating-the-singleton-design-pattern-in-php5):
```php
<?php
    final class UserFactory {
        public static function Instance() {
            static $instance = NULL;
            if($instance === NULL) {
                $instance = new UserFactory();
            }
            return $instance;
        }
        private function __construct() { } // Empty constructor to prevent unintended initialization
    }

    // Foo and bar are comparatively equal
    $foo = UserFactory::Instance();
    $bar = UserFactory::Instance();
?>
```
#### Python
Singletons are not native to Python, but their design pattern can be approximated. This can be done due to Python's ability to have an object inherit properties of two super classes, but it can be approximated in a more clean matter by using [metaclasses](https://stackoverflow.com/questions/100003/what-are-metaclasses-in-python). The following example is taken from [this stackoverflow response](https://stackoverflow.com/questions/6760685/creating-a-singleton-in-python):
```python
class Singleton:
    __instances = {}
    def __call__(cls, *args, **kwargs):
        if cls not in cls._instances:
            cls._instances[cls] = super(Singleton, cls).__call__(*args, **kwargs)
        return cls._instances[cls]

class myClass(SuperClass, metaclass=Singleton):
    pass
```
### Can they be made thread safe?
#### PHP
Not easily or natively. PHP has less well defined threading functions than Python so while the Singleton behavior can be approximated with classes and constructors, making them strictly thread-safe is more difficult without something similar to Python's built-in thread locking.
#### Python
[Yes](https://gist.github.com/werediver/4396488), by leveraging some library tools from Python's threading abilities:
```python
import threading
class Singleton:
    __singleton_lock = threading.Lock()
    __singleton_instance = None

    @classmethod
    def instance(cls):
        if not cls.__singleton_instance:
            with cls.__singleton_lock:
                if not cls.__singleton_instance:
                    cls.__singleton_instance = cls() # See https://docs.python.org/3/library/functions.html#classmethod
        return cls.__singleton_instance
```

### Can the singleton instance be lazily instantiated?
#### PHP
Yes, and the previous examples employ this kind of instantiation checking. Singleton data structures can maintain whether or not they have been instantiated in their internal scopes and spawn them only once.
#### Python
Yes, and both previous examples approximate this behavior in similar ways. By having the base `Singleton` class keep track of if the instance is initialized it can be spawned only once, either in a `__init__()` method, or an overloaded `__call__()` method.
