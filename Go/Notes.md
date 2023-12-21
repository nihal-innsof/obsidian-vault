### `select`
The `select` keyword in golang used to implement a `switch case` like mechanism on channels. The `select` allows us to wait on multiple channel operations simultaneously and execute code based on which channel received data first.
*syntax*:
```go
select {
	case ch1 <- x1:
		// Case 1 executes if x1 can be sent to ch1
	case ch2 <- x2:
		// Case 2 executes if x2 can be sent to ch2
	case <- ch3:
		// Case 3 gets executed if a value can be recieved from ch3
	default:
}
```
