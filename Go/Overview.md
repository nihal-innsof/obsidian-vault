---
id: Overview
aliases: []
tags: []
---

### Diff between `struct` in go and `class` in other languages

1. `struct` can have methods, but they are not bound to `struct` as with languages that have `classes`. Instead of defining the methods, we usually have a function outside of the struct which uses the struct as a parameter.
2. Cannot be instantiated directly.

### Golang Concrete types

All non-interface types are concrete types

1. `int`
2. `array`
3. `slice`
4. `func`
5. `string`
6. `struct`
7. `map`
8. `float64`
9. `chan`

### Pointer Dereferencing

In Golang when we try access to the field of a struct through pointer, pointer dereferencing doesn't have to be done explicitly, golang does it implicitly, as it one of the feature provided by golang.

### Receiver Parameter

A receiver is a parameter in a method declaration that is followed by the method's name and parameters. It indicates which type the method is associated with. The receiver can be either a value receiver or a pointer receiver.

```go
// Value receiver
func (v T) MethodName() {
    // Method implementation
}

// Pointer receiver
func (p *T) MethodName() {
    // Method implementation
}
```

### Visibility Rules

Code objects in a package is made available to other packages outside the parent package by making first letter off the code object identifier uppercase.
