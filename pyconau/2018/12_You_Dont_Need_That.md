# You Don't Need That!
## Christopher Neugebauer 

* Python is very flexible
* Think of languages in terms of features rather than paradigms
* Design patterns
    * Let you express ideas that are not specific to your language in your language
    * circa-90's
        * Rigid languages like C++, Java
    * Python features make certain design patterns unneccessary
* Singleton
    * A class that can only be constructed once
    * Pythonic implementation:
        * Create class def, create instance, delete def
    * What do we want to achieve?
        * Namespacing - required for pure OO
        * Functionality that can be passed around
        * Prevents construction more than once
        * Can be passed as args to a function 
    * Alternative:
        * Everything is a variable
        * Python module system
        * `import` only every import a single copy of a module (even if deleted)    
* Dependency Injections
    * Provide deps to classes as constructor arguments
    * Pass in a function as a parameter then call it directly in a method.
    * Pythonic implementation:
        * `import` the function
    * Java does this for testing - you can pass in a mock
    * Pythonic implementation
        `unittest.mock`
* Threads - use asyncio instead!
* Iterator
    * Built in to Python
    * The for loop is designed to implement the iterator pattern
    * Generators make it much easier to write your own Iterators
* Visitor
    * Perform a common operation on a collection
    * Acceptor - Collection
    * Visitor - Operation to perform on items in the collection
    * Aim: 
        * Separate the structure of the collection from the operation
        * Make it easier to recognise how the operation will be performed
        * Older languages had Iterators as 1st-class primitives
    * So implement `__iter__` because it behaves in a known 
    * Generators separate structure from operations
        * So no need for the visitor pattern
* Factory
    * Makes sense in Python - constructors in python have to return instances of the base class
    * In Python construction uses the same callable paradigms as functions
* Book
    * python-patterns.guide
