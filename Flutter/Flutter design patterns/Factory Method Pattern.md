## Definition
Factory method is to define an interface for creating an object but we let subclasses decide which class to instantiate. Factory method lets a class defer instantiation to subclasses.

```dart
abstract class Employee {
	void work();
	// Factory method pattern
	factory Employee(String type) {
		switch(type) {
			case 'programmer':
				return Programmer()
			case 'hrmanager':
				return HRManager()
			case 'boss':
				return Boss()
			default:
				throw UnimplementedError()
		}
	}
}

class Programmer implements Employee {
	@override
	void work() {
		print('coding');	
	}
}

class HRManager implements Employee {
	@override
	void work() {
		print('recruiting');	
	}
}

class Boss implements Employee {
	@override
	void work() {
		print('leading');	
	}
}
```
There is one more way to define factory method pattern apart from the above example, by taking out the factory method pattern from the `Employee` class and putting in a separate class. This approach is recommended if the code base get larger.
```dart
abstract class Employee {
	void work();
}

class Programmer extends Employee {
	@override
	void work() {
		print('coding');	
	}
}

class HRManager extends Employee {
	@override
	void work() {
		print('recruiting');	
	}
}

class Boss extends Employee {
	@override
	void work() {
		print('leading');	
	}
}

class FactoryMethod {
	static Employee getEmployee(String type) {
		switch(type) {
			case 'programmer':
				return Programmer()
			case 'hrmanager':
				return HRManager()
			case 'boss':
				return Boss()
			default:
				throw UnimplementedError()
		}
	}
}
```
## Disadvantages
* Makes code more difficult to read, as most of the codes are behind abstractions.
* More heirarchies of classes (this issue can be solved using the prototype design pattern)

## Related Design Patterns
* Abstract Factory - Implemented with factory method
* Prototype - Avoids heirarchies of classes
* Template method - Implemented with factory methods