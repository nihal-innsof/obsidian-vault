`ref.watch` is used inside the `build` method of a widget or inside the body of a provider to have the widget/provider listen to a provider.

using `ref.watch` inside provider:

```dart
final filterTypeProvider = StateProvider<FilterType>((ref) => FilterType.none);
final todosProvider = StateNotifierProvider<TodosList, List<Todo>>((ref) => TodoList());
final filteredTodoListProvider = Provider((ref) {
	// obtains both the filter and the list of todos
	final FilterType filter = ref.watch(filterTypeProvider);
	final List<Todo> todos = ref.watch(todosProvider);
	switch (filter) {
		case FilterType.completed:
		// return the completed list of todos
		return todos.where((todo) => todo.isCompleted).toList();
		case FilterType.none:
		// returns the unfiltered list of todos
		return todos;
		}
	}
);
```

using `ref.watch` inside a build method:
```dart
final counterProvider = StateProvider((ref) => 0);

class HomeView extends ConsumerWidget {
  const HomeView({Key? key}): super(key: key);

  @override
  Widget build(BuildContext context, WidgetRef ref) {
    // use ref to listen to a provider
    final counter = ref.watch(counterProvider);

    return Text('$counter');
  }
}
```

#### Note: 
Whenever possible, prefer using `ref.watch` over `ref.read` or `ref.listen` to implement a feature. By relying on `ref.watch`, your application becomes both reactive and declarative, which makes it more maintainable.
	The `watch` method should not be called asynchronously, like inside an `onPressed` of an [ElevatedButton](https://api.flutter.dev/flutter/material/ElevatedButton-class.html). Nor should it be used inside `initState` and other [State](https://api.flutter.dev/flutter/widgets/State-class.html) life-cycles. In those cases, consider using `ref.read` instead.