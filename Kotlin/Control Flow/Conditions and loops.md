## When expression
*when* is similar to *switch* statement in C-like languages. Its simple form looks like:
```kotlin
when (x) {
    1 -> print("x == 1")
    2 -> print("x == 2")
    else -> {
        print("x is neither 1 nor 2")
    }
}
```

*when* can be used as an expression or as a statement. If used as an expression, the value of the first matching brach becomes the value of the overall expression.

If *when* is used as an expression the *else* brach is mandatory, unless the compiler can prove that all possible cases are covered with the branch conditions, for eg, with enum class entries and sealed class subtypes.

```kotlin
enum class Bit {
  ZERO, ONE
}

val numericValue = when (getRandomBit()) {
    Bit.ZERO -> 0
    Bit.ONE -> 1
    // 'else' is not required because all cases are covered
}
```

We can also define a common behaviour for multiple branches by combining multiple conditions in a single line using a comma:
```kotlin
	when (x) {
    0, 1 -> print("x == 0 or x == 1")
    else -> print("otherwise")
}
```

We can also use use arbitary expressions as branch conditions:
```kotlin
when (x) {
    s.toInt() -> print("s encodes x")
    else -> print("s does not encode x")
}
```

We can also check a value for being *in* or *!in* a range or collection:
```kotlin
when (x) {
    in 1..10 -> print("x is in the range")
    in validNumbers -> print("x is valid")
    !in 10..20 -> print("x is outside the range")
    else -> print("none of the above")
}
```

Checking whether a value *is* or *!is* of a particular type:
```kotlin
fun hasPrefix(x: Any) = when(x) {
    is String -> x.startsWith("prefix")
    else -> false
}
```

As a replacement for *if* *else* chain. If no argument is supplied, the branch conditions are simply boolean expressions, and a branch is executed when its condition is true: 
```kotlin
when {
    x.isOdd() -> print("x is odd")
    y.isEven() -> print("y is even")
    else -> print("x+y is odd")
}
```

We can capture the when subject in variable using the following syntax:
```kotlin
fun Request.getBody() =
    when (val response = executeRequest()) {
        is Success -> response.body
        is HttpError -> throw HttpException(response.status)
    }
```

