---
id: ref.read
aliases: []
tags:
  - riverpod
---

It is a method to obtain the state of a provider, without listening to it. Commonly used inside functions that are triggered by user interaction's
Eg:

```dart
final counterProvider = StateNotifierProvider<Counter, int>((ref) => Counter(ref));
class HomeView extends ConsumerWidget {
	const HomeView({Key? key}): super(key: key);
	@override
	Widget build(BuildContext context, WidgetRef ref) {
		return Scaffold(
			floatingActionButton: FloatingActionButton(
				onPressed: () {
				// Call `increment()` on the `Counter` class
				ref.read(counterProvider.notifier).increment();
				},
			),
		);
	}
}
```

- #### Don't call `read` inside the body of a provider
      ```dart
      // Don't do
      final myProvider = Provider((ref) {
      	final value = ref.read(anotherProvider);
      })
      ```
  If we want to avoid unwanted rebuilds of the object exposed by the provider, then refer to [My provider updates too often, what can I do ?](https://riverpod.dev/docs/concepts/combining_providers#my-provider-updates-too-often-what-can-i-do)
