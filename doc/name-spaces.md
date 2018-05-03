[<-- Return to index](../README.md)
# Name Spaces

### How are name spaces implemented?
#### PHP
foo
#### Python
Names in python are treated similarly to variables in most other languages. Since Python is very loosely typed, names can be very dynamic and applied to pretty much anything. 

### How are name spaces used?
#### PHP
foo
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