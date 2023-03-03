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
