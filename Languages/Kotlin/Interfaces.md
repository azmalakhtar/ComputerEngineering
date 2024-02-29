> [!Definition]
> Interfaces can contain declarations of abstract methods, as well as method implementations. What makes them different from abstract classes is that interfaces cannot store state. The can have properties, but these need to be abstract or provide accessor implementations.

- It describes what a class should do, but not how it should do it.
- ==The place at which independent and often unrelated systems meet and act on or communicate with each other.==
- When implementing a member of an interface, you must use the `override` modifier.
- An enumeration can implement an interface.
```kt
interface X {
	val a: Int
	// val b: Int = 12 // Property initializers are not allowed in interfaces
	val c: Int
		get() = 12
	fun f(): String
	fun g(): String = "Hello"
}
```
## Functional(SAM) Interfaces
> [!definition]
> An interface with only one abstract method is called a functional interface, or a Single Abstract Method(SAM) interface. 


```kt
fun interface X {
	val b: Boolean
		get() = false
	// val c: Int // Fun Interfaces can't have abstract properties.
	fun f(): Int // Abstract Method
	fun g(): String = "Functional Interface"
}
```
- You can implement a SAM interface in the ordinary verbose way, or by passing it a lambda; the latter is called a SAM conversion. In a SAM conversion, the lambda becomes the implementation for the single method in the interface
```kt
class VerboseX: X {
	override fun f() = 11
}
val samX = X { 11 }
```
- You can pass a lambda where a SAM interface is expected, without first wrapping it into an object. Kotlin automatically creates an object from this lambda.