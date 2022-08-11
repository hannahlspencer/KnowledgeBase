# Kotlin

#### Scope functions

1. Let&#x20;

Usually used for a null check as it’s thread safe, unlike null checking with an if statement.

`val x = number?.let { val number2 = it + 1 number2 } ?: 3`

2\. Apply&#x20;

Used when we are going to use more than one property or one property of a class many times.

`val intent = Intent().apply { putExtra("", "") putExtra("", 0) action = "" }`

3\. Run&#x20;

An extension function that works like with

`val intent2 = Intent().run { putExtra("", "") putExtra("", 0) action = "" this }`

4\. With

The context object passed as an argument, and the return value is a lambda result. Very like apply.

`val intent3 = with(Intent()) { putExtra("","") }`

5\. Also&#x20;

Good for performing actions that take the context object as an argument - use for actions that need a reference to the object rather than its properties and functions.

`fun getSquaredI() = (i * i).also { i++ }`

#### Articles

* [9 Java patterns Kotlin made obselete](https://spitzbueb.medium.com/9-java-patterns-in-kotlin-eac0cca1599f)
* [Stop writing hard to read Kotlin](https://towardsdev.com/stop-writing-hard-to-read-kotlin-900842fb82f)
* [Reduce and Fold in Kotlin](https://medium.com/@sujitpanda/do-you-know-what-is-reduce-and-fold-method-is-in-kotlin-c3aec2dc1df1)
* [Tips and tricks for Kotlin efficiency](https://medium.com/simform-engineering/kotlin-tips-and-tricks-for-efficient-programming-c4eefb27ea1b)

#### Courses

* [Kotlin for Java developers](https://www.coursera.org/learn/kotlin-for-java-developers)
