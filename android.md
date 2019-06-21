# Android

```
flutter create newapp
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


## Release
### Signing the app

```bash
keytool -genkey -v -keystore ~/key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias key
```

```
vim android/key.properties
```

```properties
storePassword=<password from previous step>
keyPassword=<password from previous step>
keyAlias=key
storeFile=<location of the key store file, such as /Users/<user name>/key.jks>
```

Configure signing for your app by editing the `<app dir>/android/app/build.gradle` file.
  
```
  def keystoreProperties = new Properties()
   def keystorePropertiesFile = rootProject.file('key.properties')
   if (keystorePropertiesFile.exists()) {
       keystoreProperties.load(new FileInputStream(keystorePropertiesFile))
   }

   android {}
   
signingConfigs {
       release {
           keyAlias keystoreProperties['keyAlias']
           keyPassword keystoreProperties['keyPassword']
           storeFile file(keystoreProperties['storeFile'])
           storePassword keystoreProperties['storePassword']
       }
   }
   buildTypes {
       release {
            minifyEnabled true
            useProguard true
           signingConfig signingConfigs.release
           proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
       }
   }
   
   
```

Configure Proguard

```
vim android/app/proguard-rules.pro
```

```pro
## Flutter wrapper
-keep class io.flutter.app.** { *; }
-keep class io.flutter.plugin.**  { *; }
-keep class io.flutter.util.**  { *; }
-keep class io.flutter.view.**  { *; }
-keep class io.flutter.**  { *; }
-keep class io.flutter.plugins.**  { *; }
```


`AndroidManifest.xml`

```xml
<uses-permission android:name="android.permission.INTERNET"/>
```

For Admob `AndroidManifest.xml`

```xml
<manifest>
    <application>
        <!-- Sample AdMob App ID: ca-app-pub-3940256099942544~3347511713 -->
        <meta-data
            android:name="com.google.android.gms.ads.APPLICATION_ID"
            android:value="YOUR_ADMOB_APP_ID"/>
    </application>
</manifest>
```

```
flutter build appbundle
```
