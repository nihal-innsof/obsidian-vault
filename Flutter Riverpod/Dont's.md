* #### Don't call `read` inside the body of a provider
	```dart
	final myProvider = Provider((ref) {
		final value = ref.read(anotherProvider);
	})
	```
	If we want to avoid unwanted rebuilds of the object exposed by the provider, then refer to [My provider updates too often, what can I do ?](https://riverpod.dev/docs/concepts/combining_providers#my-provider-updates-too-often-what-can-i-do)