---
id: Freezed - Flutter
aliases: []
tags:
  - freezed
---

## Deep Copy

Consider the following example

```dart
@freezed
class Company with _$Company {
	factory Company({String? name, required Director director}) = _Company;
}

@freezed
class Director with _$Director {
	factory Director({String? name, Assistant? assistant}) = _Director;
}

@freezed
class Assistant with _$Assistant {
	factory Assistant({String? name, int? age}) = _Assistant;
}
```

Then, from a reference on `Company`, we may want to perform changes on `Assistant`.  
For example, to change the `name` of an assistant, using `copyWith` we would have to write:

```dart
	 Company company;

		Company newCompany = company.copyWith(
		  director: company.director.copyWith(
		    assistant: company.director.assistant.copyWith(
		      name: 'John Smith',
		    ),
		  ),
		);
```

This _works_, but is relatively verbose with a lot of duplicates.  
This is where we could use [Freezed](https://pub.dartlang.org/packages/freezed)'s "deep copy".

If a Freezed model contains properties that are also Freezed models, then the code-generator will offer an alternate syntax to the previous example:

```dart
Company company;
Company newCompany = company.copyWith.director.assistant(name: 'John Smith');
```

This snippet will achieve strictly the same result as the previous snippet (creating a new company with an updated assistant name), but no longer has duplicates.

## Note:

- ### How to add methods, getters etc to a freezed class
  To add getters etc to a freezed model, we have to create private empty constructor for it.

```dart
@freezed
class Person with _$Person {
  // Added constructor. Must not have any parameter
  const Person._();

  const factory Person(String name, {int? age}) = _Person;

  void method() {
    print('hello world');
  }
}
```
