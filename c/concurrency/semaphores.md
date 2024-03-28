# Semaphores

A semaphore is like a gatekeeper that controls access to a shared resource in a program that runs multiple tasks at the same time. It ensures that only a certain number of tasks can use the resource simultaneously.

Here's how it works:

1. **Wait Operation**: When a task wants to use the resource, it performs a "wait" operation on the semaphore. If the gatekeeper says it's ok (meaning the resource isn't fully used up), the task gets to go through and use the resource. Otherwise, it waits until the gatekeeper says it's clear.
2. **Signal Operation**: When a task finishes using the resource, it tells the gatekeeper it's done by performing a "signal" operation. This lets the gatekeeper know that the resource is available again. If any tasks were waiting, the gatekeeper picks one and lets it through.

There are two types of semaphores:

1. **Binary Semaphore**: It's like a gate with only two states: open and closed. It's typically used to make sure only one task at a time can use the resource. Think of it as a bathroom with a sign saying "Occupied" when someone's inside and "Vacant" when it's free.
2. **Counting Semaphore**: This type allows a certain number of tasks to use the resource at once. It's like a gate with a counter showing how many more tasks can go through. Once the limit is reached, other tasks have to wait until some are done.

Semaphores help manage the chaos of multiple tasks trying to access the same resource simultaneously in a program, ensuring everything runs smoothly without conflicts.

Example of a binary semaphore in code:

```kotlin
import java.util.concurrent.Semaphore

class SharedResource {
    private val semaphore = Semaphore(1) // Binary semaphore with initial permit of 1

    fun useResource() {
        try {
            semaphore.acquire()
            println("Resource being used by ${Thread.currentThread().name}")
            Thread.sleep(1000)
        } finally {
            semaphore.release()
            println("Resource released by ${Thread.currentThread().name}")
        }
    }
}

fun main() {
    val sharedResource = SharedResource()

    repeat(5) {
        Thread {
            sharedResource.useResource()
        }.start()
    }
}

```
