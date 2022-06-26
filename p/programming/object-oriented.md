# Object Oriented

### Design Principles

#### **Encapsulation**&#x20;

Each object keeps its state private. It can only be accessed by member functions.&#x20;

#### **Polymorphism**&#x20;

Polymorphism lets us use a class exactly like its parent so there is no confusion with mixing types, but each child sub-class keeps its own functions/methods as they are. If we had a superclass called Mammal that has a method called mammalSound(). The sub-classes of Mammals could be Dogs, whales, elephants, and horses. Each of these would have their own iteration of a mammal sound (dog-barks, whale-clicks).&#x20;

#### **Inheritance**&#x20;

Inheritance is the ability of one object to acquire some/all properties of another object. For example, a child inherits the traits of his/her parents. With inheritance, reusability is a major advantage. You can reuse the fields and methods of the existing class.&#x20;

#### **Abstraction**&#x20;

Each object should only expose a high-level mechanism for using it, and should hide internal implementation details

### SOLID Principles

#### The Single Responsibility Principle&#x20;

The Single Responsibility Principle states that a class should do one thing and therefore it should have only a single reason to change. So only one potential change (database logic, logging logic, and so on.) in the software’s specification should be able to affect the specification of the class.

#### The Open-Closed Principle&#x20;

The Open-Closed Principle requires that classes should be open for extension and closed to modification.

Modification means changing the code of an existing class, and extension means adding new functionality.

We should be able to add new functionality without touching the existing code for the class. This is because whenever we modify the existing code, we are taking the risk of creating potential bugs. This is usually done with the help of interfaces and abstract classes.

#### The Liskov Substitution Principle&#x20;

The Liskov Substitution Principle states that subclasses should be substitutable for their base classes.

This means that, given that class B is a subclass of class A, we should be able to pass an object of class B to any method that expects an object of class A and the method should not give any weird output in that case.

This is the expected behavior, because when we use inheritance we assume that the child class inherits everything that the superclass has. The child class extends the behavior but never narrows it down.

#### The Interface Segregation Principle&#x20;

Segregation means keeping things separated, and the Interface Segregation Principle is about separating the interfaces.

The principle states that many client-specific interfaces are better than one general-purpose interface. Clients should not be forced to implement a function they do no need.

#### The Dependency Inversion Principle&#x20;

The Dependency Inversion principle states that our classes should depend upon interfaces or abstract classes instead of concrete classes and functions.
