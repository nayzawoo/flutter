# Android

```
flutter create newapp
```

`pubspec.yaml`

```yaml
dependencies:
  http: ^0.12.0+2
  firebase_admob: ^0.8.0+3
  firebase_core: ^0.2.5  # add dependency for Firebase Core
  firebase_analytics: ^1.0.4
```

## Change Package Name

Change the label name in your AndroidManifest.xml file:

```xml
 <application
    android:name="io.flutter.app.FlutterApplication"
              android:label="TheNameOfYourApp">
   <manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="your.package.name">
  </minifest>
</aplication>

```

build.gradle file inside app folder

```gradle
defaultConfig {
    applicationId "your.package.name"
    minSdkVersion 16
    targetSdkVersion 27
    versionCode 1
    versionName "1.0"
    testInstrumentationRunner "android.support.test.runner.AndroidJUnitRunner"
}
```




