# Flutter

## OnReady/After Layout

https://github.com/fluttercommunity/flutter_after_layout

```dart
@override
void initState() {
  super.initState();
  WidgetsBinding.instance.addPostFrameCallback((_) => onReady(context));
}

void onReady(BuildContext context) {
  // show showSnackBar
  // show dialog
}
```

## BuildContext

```dart
class _MyHomePageState extends State<MyHomePage> {
  final _scaffoldKey = GlobalKey<ScaffoldState>();
  
  void _showSnackBar() {
    final snackbar = SnackBar(
        content: Text("Fetching ... "),
        duration: new Duration(milliseconds: 700));
    _scaffoldKey.currentState.showSnackBar(snackbar);
  }
  
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      key: _scaffoldKey,
      // ..
    );
  )
}
```

## Utils

```dart
class Util {
  bool get isInDebugMode {
    bool inDebugMode = false;
    assert(inDebugMode = true);
    return inDebugMode;
  }
}
```

## Firebase

https://firebase.google.com/docs/flutter/setup
