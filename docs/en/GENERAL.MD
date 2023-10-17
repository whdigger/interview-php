### 1. What data types do you know in PHP and how many of them are there?

<details>
    <summary>PHP supports 10 data types</summary>

* `integer`: Whole numbers without decimal points, for example 42, -10, 0.
* `float`: Numbers with decimal points, for example 3.14, -2.5, 0.0.
* `string`: Sequences of characters enclosed in single or double quotes, for example 'Hello', "World".
* `boolean`: Logical values true or false..
* `array`: Ordered collections of elements, each with its own index or key.
* `object`: Instances of classes that contain properties and methods.
* `resource`: References to external resources such as files or database connections.
* `Null`: Special null value that represents the absence of a value.
* `Callback/Callable`: Function callbacks.
* `pseudo-types`: Some pseudo-types, such as `mixed, number, callback, void, iterable, never` represent special
  categories of data types or constraints..

</details>

### 2. What are magic methods in PHP, have you used them, and what are they used for?

Magic methods in PHP are special methods that begin with a double underscore, for example `__construct()`.
They provide special behavior and functionality in specific contexts within classes.
They are used to perform certain actions during specific events or operations.

<details>
    <summary>List of magic methods</summary>

* `__construct()` Class constructor, called when a new object is created.
* `__destruct()` Class destructor, called when an object is being destroyed.
* `__get()` Called when accessing an inaccessible or non-existent property of an object.
* `__set()` Called when assigning a value to an inaccessible or non-existent property of an object.
* `__call()` Called when invoking an inaccessible or non-existent method of an object.
* `__toString()` Called when attempting to convert an object to a string.
* `__isset()` Called when checking the existence of an inaccessible or non-existent property of an object using isset().
* `__unset()`  Called when unsetting an inaccessible or non-existent property of an object using unset().

</details>

### 3. What is a session in PHP, where is it stored by default, and how does this mechanism work?

<details>
    <summary>In PHP, sessions are a mechanism for storing information about a user's state on the server between consecutive requests.</summary>

Mechanism of operation:

1. When a user opens a web page, PHP generates a unique session identifier, which is typically represented as a cookie
   with the name "PHPSESSID"..
2. This identifier is used to associate session data on the server with a specific user.
3. By default, session data in PHP is stored on the server as temporary files in a designated directory specified in the
   PHP settings (usually in /tmp or another system directory).
4. When a user sends a request to the server, PHP uses the session identifier from the cookie or passed request
   parameter to determine the corresponding session file.
5. Then, the session data is loaded into a special array called $_SESSION, which contains the saved variables and values
   associated with the user.
6. After processing the request and completing script execution, the session data is automatically saved back to the
   server file.
7. Each time a user makes a request to the server, PHP automatically associates the session data with the corresponding
   session identifier, updates them, and returns the updated data to the client-side.

Sessions in PHP allow for preserving user state information between requests, which is useful for implementing features
such as authentication, shopping cart storage, personalization, and other scenarios.
</details>

### 4. What are cookies?

Cookies are small pieces of data that a web server sends and stores on a user's computer through a web browser.
Cookies are used to store information about the user's state and activity on a website.
They can be set both on the backend and the frontend.

### 5. How are they set on the backend?

1. setcookie - Converts data before sending it.
2. setrawcookie - Sends data in raw form.
3. header('Set-Cookie: name=value')

### 6. Can they be made secure to prevent them from being read?

Setting both parameters in setcookie: secure and httponly ensures their protection from being read on the JavaScript
side.

### 7. What is local storage and how is it different from cookies?

The main difference between LocalStorage and Cookies is in the way data is stored, automatic sending, lifetime,
availability, traffic that is generated when sending cookies

### 8. What's new in PHP 7 and PHP 8?

<details>
    <summary>PHP 8: New JIT Compiler, Strong Typing, Nullsafe Operator, Union Types, Named Arguments, Attributes</summary>

1. **New JIT Compiler**: Introduces a new JIT (Just-In-Time) compiler that transforms certain parts of PHP code into
   machine code, resulting in improved performance.
2. **Strong Typing**: Brings stricter typing and introduces support for declaring strict types for function arguments
   and return values.
3. **Nullsafe operator**: Introduces the nullsafe operator "?->", which allows safe access to properties and methods of
   objects even if intermediate values are null.
4. **Union Types**: Introduces support for union types, allowing the specification of multiple types for a variable,
   function parameter, or return value. For example, you can specify a type of int|string, meaning the variable can be
   either an integer or a string.
5. **Named Arguments**: Introduces the ability to pass function arguments by name, making it easier to read and
   understand code, especially when dealing with functions with a large number of arguments.
6. **Attributes**: Introduces attributes, which allow adding metadata to classes, methods, properties, and other code
   elements. Attributes are used for annotation and declarative code description.
7. **Many other improvements**: Includes numerous other enhancements, such as improved error handling and exceptions,
   new features in the standard library, improvements to built-in functions, and more.

</details>

<details>
    <summary>PHP 7: Improved performance, Scalar types and strict typing, Null coalescing operator, Strict error handling, Spaceship operator, Return type declarations. </summary>

1. **Improved performance**: Introduces the new Zend Engine 3.0, which significantly improves code execution
   performance.
2. **Scalar types and strict typing**: Allows for the declaration of scalar types (int, float, string, bool) for
   function arguments and return values. This helps improve code reliability and makes error detection easier.
3. **Null coalescing operator**: the null coalescing operator (??) is introduced, which allows specifying a default
   value if a variable is null. This simplifies and reduces code when working with potentially null variables.
4. **Strict error handling**: Includes stricter error handling and exception throwing for operations that previously
   resulted in implicit warnings or unpredictable results. This helps improve code quality and simplifies debugging.
5. **Spaceship operator**: Adds the spaceship operator (<=>), which allows comparing two values and returning a negative
   number, zero, or a positive number based on their relationship. This simplifies sorting and comparing values.
6. **Return type declarations**: Introduces the ability to specify return types for functions and methods. This helps
   improve code documentation and ensures compliance with expected types.
7. **Syntax improvements**: Includes several syntax improvements, such as using define() for array constants, shorthand
   array syntax, and other minor enhancements that make code more readable and easier to work with.

</details>

### 9. What are generators?

<details>
    <summary>Generators in PHP are a special type of functions</summary>that allow for the creation of iterable objects
for processing large datasets with low memory consumption. They provide a convenient way to generate values "on the fly"
without the need to store all values in memory simultaneously.

Generators in PHP use the keyword "yield" to return a value from the function instead of the "return" keyword. When
the "yield" statement is encountered in a function, the function pauses its execution and returns the value. Upon the
next invocation, the generator resumes its work from where it left off.

Generators can also be used for lazy loading of data from databases or files, iterating over recursive data structures,
and in other situations where processing data in chunks is required.
</details>

### 10. What is serialization?

Serialization in PHP is the process of converting objects, arrays, or other data structures into a format that can be
saved or transmitted over a network and then restored back to its original form.

### 11. Does PHP support multiple inheritance, and how can it be implemented?

PHP does not support multiple inheritance, but it can be achieved using: **interfaces**, **traits**, **composition**,

### 12. What is the difference between an abstract class and an interface?

<details>
    <summary>An abstract class is a class that cannot be instantiated directly and serves as a base class for other classes.</summary>
It can contain both abstract and concrete methods, and only one class can be inherited.
If you need to provide a base functionality and implementation of methods while also allowing for inheritance, use an abstract class.
</details>

<details>
<summary>An interface represents a set of contracts that a class must implement.</summary>
It does not contain the implementation of methods, only their signatures. A class can implement multiple interfaces, and it does not provide method implementations.
If you only need to define a contract and guarantee the implementation of methods in classes, use an
interface.</details>

### 13. What are traits, how are they used, and what are their advantages and disadvantages?

<details>
    <summary>Traits are a mechanism in PHP that allows code reuse across classes.</summary>

Advantages

1. **Code reuse**
2. **Horizontal extension** (gaining functionality from different sources)
3. **Adding methods and properties**

Disadvantages

1. **Potential complexity in interrelated methods and properties**
2. **Dependency on traits** (changes in one place can have unpredictable results)
3. **Possible naming conflicts**
4. **Difficulties in tracking dependencies**

</details>

### 14. What is the difference between an object and a class?

**Class** - is a language construct that describes the properties, structure, and actions of objects. A class is an
abstraction and does not have specific values or state.

**Object** - is an instance of a class. When an object is created, it occupies physical memory and takes on the state
defined in the class.

### 15. What data structures do you know in the STL?

SplDoublyLinkedList, SplStack, SplQueue, SplHeap

### 16. What hashing algorithms do you know?

MD5, SHA-256, Argon2, bcrypt

### 17. What sorting algorithms do you know, and what is O(n)?

Merge Sort (O(n*logn)), Bubble Sort (O(n^2)), Quick Sort (O(n^2))

### 18. What is the purpose of iterators?

Iterators facilitate the iteration over elements of a data structure, abstracting away the complexities of interacting
with the structure itself. They provide a unified interface for accessing elements, regardless of the internal
representation of the data. This makes code more readable and flexible and allows for efficient use of memory resources
when working with large datasets.

### 19. What is the complexity of the strlen function in Big O notation in PHP?

strlen O(1) - retrieves the length from the zval structure
mb_strlen O(n) - depends on the encoding

### 20. What is the difference between multithreading and asynchronous programming?

Multithreading refers to executing multiple threads within a single process. Threads have their own call stacks and
share the process's memory.
Asynchronous programming refers to an execution model where one task doesn't block the execution of other tasks.
Asynchronous programming utilizes events, callbacks, or promises to manage task execution.

### 21. What are semaphores and mutexes?

Semaphores and mutexes are two different synchronization mechanisms used to control access to shared resources in a
multithreaded or multiprocess environment.

A semaphore controls access to a resource using a counter, allowing a limited number of threads or processes to access
it simultaneously.

A mutex provides exclusive access for only one thread or process at a time.

### 22. How does UTF-8 encoding work?

UTF-8 encoding primarily uses 8-bit bytes to represent characters. The encoding is determined either by the Byte Order
Mark (BOM) at the beginning of the document or by analyzing the byte sequence.

The process of encoding in UTF-8 works as follows:

- Each character is translated into its unique Unicode code.
- Each Unicode character is represented as a U+ code point, which is a hexadecimal value of its unique Unicode code.
- Each code point is transformed into its byte representation.

### 23. What complexity evaluations do you know?

<details>
    <summary>Constant Time - O(1)</summary>
O(1) complexity means that the computational complexity of an algorithm does not depend on the size of the input data. 
However, it's important to note that the unit in the formula doesn't necessarily mean that the algorithm executes in one operation or takes very little time.
</details>
<details>
    <summary>Linear Time - O(n)</summary>
O(n) complexity means that the complexity of the algorithm grows linearly with the size of the input array.
Such algorithms can be easily identified by the presence of a loop that iterates over each element in the input array.
</details>
<details>
    <summary>Logarithmic Time - O(n·log n)</summary>
O(n·log n) complexity means that the execution time of the algorithm grows logarithmically with the increase in the size of the input array.
Most divide-and-conquer algorithms have logarithmic complexity.
</details>
<details>
    <summary>Quadratic Time - O(n^2)</summary>
An algorithm with O(n^2) complexity has a time complexity that depends on the square of the size of the input array.
The problem with quadratic time algorithms is that they don't scale well.
</details>

### 24. What advantages do PHP 8 attributes provide compared to annotations?

<details>
    <summary>Native Support</summary>
Attributes are supported directly by the interpreter and do not require the use of third-party frameworks or libraries.
</details>
<details>
    <summary>More Flexible Syntax</summary>
You can define your own attribute classes with specific methods and properties, providing more flexibility for metaprogramming and changing code behavior.
</details>
<details>
    <summary>Better Integration with Development Tools</summary>
Attributes are easily read and processed by development and code analysis tools.
</details>
<details>
    <summary>Semantic Information</summary>
They allow adding semantic information to the code, which can be useful for documentation and understanding its purpose and usage. For example, you can add attributes indicating the types of method arguments, possible exceptions, or other information that helps developers understand how to use your code.
</details>
<details>
    <summary>Wide Support in the PHP Ecosystem</summary>
This means that you can use attributes in your projects with confidence, knowing that they are compatible and supported in various contexts.
</details>