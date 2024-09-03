---
id: ref.listen
aliases: []
tags:
  - riverpod
---

Using `ref.listen` inside a provider:

```dart
final counterProvider = StateNotifierProvider<Counter, int>((ref) => Counter(ref));

final anotherProvider = Provider((ref) {
  ref.listen<int>(counterProvider, (int? previousCount, int newCount) {
    print('The counter changed $newCount');
  });
  // ...
});
```

or inside a build method:

```dart
final counterProvider = StateNotifierProvider<Counter, int>((ref) => Counter(ref));

class HomeView extends ConsumerWidget {
  const HomeView({Key? key}): super(key: key);

  @override
  Widget build(BuildContext context, WidgetRef ref) {
    ref.listen<int>(counterProvider, (int? previousCount, int newCount) {
      print('The counter changed $newCount');
    });

    return Container();
  }
}
```

#### Differences between `ref.watch`, `ref.listen`:

| **`ref.watch`**                                                                                 | **`ref.listen`**                                                                                                                                                                                                                        |
| ----------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| When a change occurs in the provider it reacts to the change, by rebuilding the widget/provider | When a change occurs, instead of reacting and rebuilding a widget/provider, it call a custom function. That can be useful for performing actions when a certain change happens, such as showing a snackbar when an error happens. etc.. |

#### Note:

The `ref.listen` method should not be called asynchronously, like inside an `onPressed` of an [ElevatedButton](https://api.flutter.dev/flutter/material/ElevatedButton-class.html). Nor should it be used inside `initState` and other [State](https://api.flutter.dev/flutter/widgets/State-class.html) life-cycles.
