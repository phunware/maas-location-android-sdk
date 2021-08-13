# Phunware Location SDK for Android

[![Nexus](https://img.shields.io/nexus/r/com.phunware.location/provider-managed?color=brightgreen&server=https%3A%2F%2Fnexus.phunware.com)](https://nexus.phunware.com/content/groups/public/com/phunware/location/provider-managed/)

Phunware's Location SDK for Android. Visit https://www.phunware.com/ for more information or [sign into the MaaS Portal](http://maas.phunware.com/) to set up your venue.

### Requirements
* minSdk 23.
* AndroidX.

### Supported Architectures
* armeabi-v7a
* arm64-v8a
* x86_64
* x86

### Download
Add the following repository to your top level `build.gradle` file.
 ```groovy
repositories {
    maven {
            url "https://nexus.phunware.com/content/groups/public/"
        }
}
 ```

 Add the following dependency to your app level `build.gradle` file.
```groovy
dependencies {
    implementation "com.phunware.location:provider-managed:<version>"
}
```

### Android project setup
##### Keys
To use any of the Phunware MaaS SDKs you'll need to add the following entries to your AndroidManifest.xml, making sure to replace the `value` properties with your actual App ID and Access Key:

``` xml
<meta-data
    android:name="com.phunware.maas.APPLICATION_ID"
    android:value="YOUR_APP_ID"/>

<meta-data
    android:name="com.phunware.maas.ACCESS_KEY"
    android:value="YOUR_ACCESS_KEY"/>
```

##### Permissions
```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_BACKGROUND_LOCATION" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
```

### Usage
#### Creating a Location Provider
To get location updates from the Location SDK, you first need to create a Location Provider. You can do so by instantiating a `PwManagedLocationProvider` like in the example below:

```kotlin
val provider = PwManagedLocationProvider(application: Application, buildingId: Long, errorListener: PwErrorListener?)
```

#### Listening to location updates
After creating your provider, you can listen to location updates by calling `requestLocationUpdates()` on your provider and passing an implementation of `PwLocationListener`:

```kotlin
provider.requestLocationUpdates(object : PwLocationListener {
        override fun onLocationChanged(location: Location) {
            // Handle new location.
        }

        override fun onLocationUpdateFailed(pwLocationUpdateResult: PwLocationUpdateResult?) {
            // Handle failure.
        }
    }
)
```

You're all set to receive location updates in your App!

Privacy
-----------
You understand and consent to Phunware’s Privacy Policy located at www.phunware.com/privacy. If your use of Phunware’s software requires a Privacy Policy of your own, you also agree to include the terms of Phunware’s Privacy Policy in your Privacy Policy to your end users.

Terms
-----------
Use of this software requires review and acceptance of our terms and conditions for developer use located at http://www.phunware.com/terms/
