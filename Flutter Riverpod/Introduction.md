### Providers (in riverpod)

Declaring provider with name `myStringProvider` which provides the `Hello world` string wherever we need.
```dart
// Provider declaration should be top level (global)
final myStringProvider = Provider((ref) => "Hello world");
```
Above example is the most basic type of provider, which exposes a read only value. The `ref` parameter is of type `ProviderReference` which is used for accessing other providers etc.