* ## Different navigation techniques is flutter :-
	1. Passing the `BuildContext` as an argument
	2. Using on `onSuccess` callback
	3. Navigate without context using `navigatorKey` in Navigator 1.0 or usign `goRouter`
 
* ### Different font sizes in flutter
|Google size|Flutter size|
|------------|------------|
|thin|100|
|extra-light|200|
|light|300|
|regular|400|
|medium|500|
|semi-bold|600|
|bold|700|
|extra-bold|800|
|black|900|

* ### How to use a widget at root to unfocus everywhere on the app
```dart
class MyApp extends HookConsumerWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context, WidgetRef ref) {
    return MaterialApp(
      theme: ThemeData(primarySwatch: Colors.red),
      builder: (context, child) {
        return _Unfocus(
          child: child!,
        );
      },
      home: const Portal(child: Home()),
      onGenerateRoute: (settings) {
        if (settings.name == null) {
          return null;
        }
        final split = settings.name!.split('/');
        Widget? result;
        if (settings.name!.startsWith('/characters/') && split.length == 3) {
          result = ProviderScope(
            overrides: [
              selectedCharacterId.overrideWithValue(split.last),
            ],
            child: const CharacterView(),
          );
        }

        if (result == null) {
          return null;
        }
        return MaterialPageRoute<void>(builder: (context) => result!);
      },
      routes: {
        '/character': (c) => const CharacterView(),
      },
    );
  }
}

/// A widget that unfocus everything when tapped.
///
/// This implements the "Unfocus when tapping in empty space" behavior for the
/// entire application.
class _Unfocus extends HookConsumerWidget {
  const _Unfocus({
    Key? key,
    required this.child,
  }) : super(key: key);

  final Widget child;

  @override
  Widget build(BuildContext context, WidgetRef ref) {
    return GestureDetector(
      behavior: HitTestBehavior.opaque,
      onTap: () {
        FocusManager.instance.primaryFocus?.unfocus();
      },
      child: child,
    );
  }
}
```

## Difference between mutable and immutable state management solutions
|mutable|immutable|
|-----|----|
|In mutable state management both the states and the methods which changes the value's of the state exist in a same class|In the case of immutable state-mangement the state and methods/fucntions wchich modifies the state are in separete classes|

