---
description: Learnings from Clean Code - Robert C. Martin
---

# Clean Code

### What is clean code?

* Code that does one thing well&#x20;
* Efficient
* Elegant&#x20;
* Exhibits close attention to detail&#x20;
* Focused&#x20;
* Readable&#x20;
* Can be read and enhanced by others

### Naming

* Use intention-revealing names - why the function, variable, class exists, what it does, and how it is used. eg. `elapsedTimeInDays`
* Avoid disinformation

For example, don't called a collection of accounts `accountList` unless it's literally a list; `accounts` or `accountGroup` would be better (although it's also probably best to not specify the data structure used in the variable name too)

Don't use variable names that are too similar, eg. `XYZControllerForEfficientHandlingOfStrings` vs. `XYZControllerForEfficientStorageOfStrings`

* Make meaningful distinctions&#x20;

When two things in the same scope can't have the same name, don't change one in an arbitrary way. If names must be different, they must also mean something.

* Use pronounceable names&#x20;

Programming is a social activity, using non-pronounceable names makes discussing the code much more complicated

* Use searchable names&#x20;

Longer names trump shorter names, and single letter names should only be used as a local variable inside short methods

* Avoid mental mapping&#x20;

Readers shouldn't have to mentally translate one name into another

* Don't use colloquialisms or slang
* Pick one word per concept&#x20;

For example, don't have get, retrieve, and fetch as equivalent terms in different classes, but only if they are semantically identical, eg. add is used for concatenating two existing values, it shouldn't also be used to insert an element into a list



Class Names - Classes and objects should have Noun or Noun phrase names eg. `Customer`, `Account`

Method Names - methods should have verb or verb phrase names like `postPayment`, `deletePage`

When constructors are overloaded, use static factory methods to describe the arguments eg.

`Complex fulcrumPoint = Complex.FromRealNumber(23)`

is much more descriptive than

`Complex fulcrumPoint = Complex(23)`

Use of these can be enforced by making other constructors private

### Functions

First rule of functions is that they should be small. Functions should do one thing, well, and only that one thing.

Try not to mix levels of abstraction in functions. Every function should be followed by those at the next level of abstraction for readability.
