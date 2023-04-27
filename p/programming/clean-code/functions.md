# Functions

* First rule of functions is that they should be small. Functions should do one thing, well, and only that one thing.
* Try not to mix levels of abstraction in functions. Every function should be followed by those at the next level of abstraction for readability.
* Don't be afraid of making function names long - a long descriptive name is better than a short enigmatic one. You are working on clean code when each method does what you would expect. Choosing descriptive names can also clarify the module design.
* Try to keep the number of arguments for a function as minimal as possible.

#### Common Monadic Forms&#x20;

Functions with one argument are called monadic. Reasons to pass a single argument to a function:

1. Asking a question about the argument

For example, `boolean fileExists("MyFile")`



2\. Transforming the argument into something else and returning it

For example, `InputStream fileOpen("MyFile")`



3\. An event with no return value where the arguments can be used to alter the state of the system

For example, `void passwordAttemptFailedNTimes(int attempts)`

#### Flag Arguments

Try to not use flag arguments as they can complicate method signatures as it suggests that the method does two things - one is the flag is true, and another if the flag is false. It's better to split these into two separate methods.



When a function needs two or three arguments it's very possible those arguments can be wrapped up into a class or object of their own, for example: Circle makeCircle(double x, double y, double radius) becomes Circle makeCircle(Point x, double radius)

Try/catch blocks - extract the bodies of each try and catch out into functions of their own as they can get confusing and ugly
