---
id: Classes
aliases: []
tags: []
---

## Constructors

A class in kotlin can have a primary constructor and one or more secondary constructors. The primary constructor is the part of the class header and it goes after the class name and optional type parameter

```kotlin
class Person constructor(firstName: String) {
/**/
}
```

If we are not providing any annotations or visibility modifier to the constructor then the _constructor_ keyword can be omitted.

```kotlin
class Person(firstName: String) {
/**/
}
```

The constructor of a class cannot contain any code. If there is some code to be executed during the initialization of a instance, then it has to be placed in the initializer block which will be defined using the _init_ keyword.

If there are multiple initializer blocks in a class, then they will be executed in the order they are defined.

```kotlin
class InitOrderDemo(name: String) {
    val firstProperty = "First property: $name".also(::println)

    init {
        println("First initializer block that prints $name")
    }

    val secondProperty = "Second property: ${name.length}".also(::println)

    init {
        println("Second initializer block that prints ${name.length}")
    }
}
```

## Creating an instance of a class

To create an instance of a class, call the class constructor as it were a regular function.

```kotlin
val invoice = Invoice()
val customer = Customer("Joe Smith")
```

### Note:

    Kotlin does not have the *new* keyword

## Class members

Classes can contain:

- Constructors and initializer blocks
- Functions
- Properties
- Nested and Inner Classes
- Object declarations

## Abstract Classes

Class can be declared _abstract_ with some or all of its members. An abstract member will not have implementation for it in its class. We don't need to mark abstract classes or functions _open_

```kotlin
abstract class Polygon {
	abstract fun draw()
}
class Rectangle : Polygon() {
	override
	fun draw() {
		// draw the rectangle
	}
}
```

We can override a non-abstract open member with an abstract one.

```kotlin
open class Polygon {
    open fun draw() {
        // some default polygon drawing method
    }
}

abstract class WildShape : Polygon() {
    // Classes that inherit WildShape need to provide their own
    // draw method instead of using the default on Polygon
    abstract override fun draw()
}
```
