[<-- Return to index](../README.md)
# Memory Management

### How is memory handled?
#### PHP
PHP is a managed memory environment, meaning it will automatically allocate and deallocate memory space as necessary without any specific thought necessarily being given by the user.
#### Python
Likewise, Python is also a managed memory environment. The language environment will manage memory as necessary on its own, and requires no explicit programmatic consideration for day-to-day code.

### How does memory management work?
#### PHP
PHP uses the [Zend Memory Manager](https://secure.php.net/manual/en/internals2.memory.php) to act as a go-between for PHP's requests for memory space and the traditional C libraries for asking the operating system for resources.
#### Python
Python uses the [Python Memory Manager](https://docs.python.org/3/c-api/memory.html) to act as a go-between for the language and the OS-level memory allocation layer.

### Is there a garbage collection service?
#### PHP
[Yes](https://secure.php.net/manual/en/features.gc.php)
#### Python
[Yes](https://docs.python.org/3/library/gc.html), and is directly accessible at the module level.

### Is there automatic reference counting?
#### PHP
[Yes](https://secure.php.net/manual/en/features.gc.refcounting-basics.php). PHP stores the reference count internally in an `refcount` variable inside a `zval` container attached to all variables.
#### Python
[Yes](https://docs.python.org/2.0/ext/refcounts.html), the memory manager will automatically return an objects memory space to the OS-level if its reference count reaches zero.
