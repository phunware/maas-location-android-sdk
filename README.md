#PWLocation SDK for Android
================

Version 3.0.1

This is Phunware's Android SDK for the Location module. Visit http://maas.phunware.com/ for more details and to sign up.



Requirements
------------
* Android SDK 4.0.3+ (API level 15) or above


Documentation
-------------

Phunware Location documentation is included both in the Documents folder in the repository as HTML and via maven. You can also find the latest documentation here: http://phunware.github.io/maas-location-android-sdk/


Prerequisites
-------------

Add the following to your `repositories` tag in your top level `build.gradle` file.

 ```XML
 projects {
   repositories {
     ...
     maven {
         url "https://nexus.phunware.com/content/groups/public/"
     }
     ...
   }
 }
 ```

 Import the Phunware Location Library by adding the following to your app's `build.gradle` file
 ```
 compile 'com.phunware.location:location:3.0.1'
 ```

 Install the module in the `Application` `onCreate` method before registering keys. For example:
 ``` Java
 @Override
 public void onCreate() {
     super.onCreate();
     /* Other code */
     PwCoreSession.getInstance().installModules(PwLocationModule.getInstance(), ...);
     /* Other code */
 }
 ```
#Needed Permissions
-----------
In the Android manifest, the following permissions are needed:

```
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
<uses-permission android:name="android.permission.CHANGE_WIFI_STATE" />
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.READ_PHONE_STATE" />
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_COARSE_UPDATE" />
<uses-permission android:name="android.permission.BLUETOOTH"/>
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN"/>
<uses-permission android:name="android.permission.WAKE_LOCK"/>
<uses-feature android:name="android.hardware.bluetooth_le" android:required="false"/>
```

Note that BLE and Android SDK version 4.3 (API 18) or above are required if Bluetooth is actually is going to be used. If your users only are going to use Bluetooth for positioning, you should change the android:required attribute to true (this will filter out non-BLE devices at Google Play). Observe that the WAKE_LOCK permission can be removed, but background navigation performance might become worse.

To use the positioning service, the Android manifest needs to have the following tag in its application tag
```
<service android:name="com.senionlab.slutilities.service.SLIndoorLocationService">
</service>
```

Integration
-----------

####PwSlLocationProvider
The PwSlLocationProvider class defines the interface for configuring the delivery of BLE location-related events to your application. You use an instance of this class to establish the parameters that determine when location events should be delivered and to start and stop the actual delivery of those events.

```java
// Add the following service to the AndroidManifest.xml
<service android:name="com.senionlab.slutilities.service.SLIndoorLocationService" />

// Create PwLocationProviderFactory
PwLocationProviderFactory pwLocationProviderFactory = new PwLocationProviderFactory();

// Create floorId mapping
Map<String, Long> floorIDMapping = new HashMap<String, Long>();
floorIdMap.put("<YOUR_SL_FLOOR_ID_1>", <!-- YOUR_PW_FLOOR_ID_1 -->);

// Create PwSlLocationProvider
PwLocationProvider locationProvider = pwLocationProviderFactory.getPwSlLocationProvider(mContext,
    new PwLocationProviderConnectivityDetector(), new PwFloorIdMapLocationInterceptor(floorIDMapping),
    new PwSlLocationManager(mContext, <!-- YOUR_SL_MAP_ID -->, <!-- YOUR_SL_CUSTOMER_ID -->)));
```

####PwFusedLocationProvider
The PwFusedLocationProvider class defines the interface for configuring the delivery of BLE/MSE/QC location-related events to your application. You use an instance of this class to establish the parameters that determine when location events should be delivered and to start and stop the actual delivery of those events.

```java
// Create PwLocationProviderFactory
PwLocationProviderFactory pwLocationProviderFactory = new PwLocationProviderFactory();

// Create default location provider, which is applied when no valid location reported from given indoor location provider.
<!-- The GPS location provider will be used when default location provider is null. -->
PwLocationProvider defaultLocationProvider = null; // locationProviderFactory.getPwGPSLocationProvider(getApplicationContext());

// Create zone configuration for location provider
<!-- Create an indoor location provider -->
PwLocationProvider indoorLocationProvider = locationProviderFactory.getPwSlLocationProvider(context, connectivityDetector, locationInterceptor, pwSlLocationManager);
<!-- Create zones for the indoor location provider -->
// Setup our zone coordinates
PolygonOptions polygonOptions = new PolygonOptions();
polygonOptions.add(new LatLng(30.0,-97.0));
polygonOptions.add(new LatLng(30.1,-97.9));
polygonOptions.add(new LatLng(30.2,-97.8));
polygonOptions.add(new LatLng(30.3,-97.7));
// Setup floorIDs that the polygon is applied
List<Long> zoneFloorIDs = new ArrayList<Long>();
zoneFloorIDs.add(10001L);
zoneFloorIDs.add(10002L);
zoneFloorIDs.add(10003L);
// Instantiate fused location provider zone
PwFusedLocationProviderZone zone = new PwFusedLocationProviderZone(polygonOptions, zoneFloorIDs);
List<PwFusedLocationProviderZone> zones = new ArrayList<PwFusedLocationProviderZone>();
zones.add(zone);
<!-- Create zone configuration based on location provider & zones  -->
PwFusedLocationProviderZoneConfiguration zoneConfiguration = new PwFusedLocationProviderZoneConfiguration(indoorLocationProvider, zones);
List<PwFusedLocationProviderZoneConfiguration> zoneConfigurations = new ArrayList<PwFusedLocationProviderZoneConfiguration>;
zoneConfigurations.add(zoneConfiguration);

// Create PwFusedLocationProvider
PwLocationProvider fusedLocationProvider = locationProviderFactory.getPwFusedLocationProvider(getApplicationContext(), defaultLocationProvider, zoneConfigurations);
```

####PwMseLocationProvider
The PwMseLocationProvider class defines the interface for configuring the delivery of Cisco Mobility Services Engine (MSE) location-related events to your application. You use an instance of this class to establish the parameters that determine when location events should be delivered and to start and stop the actual delivery of those events.
```java
// Create PwLocationProviderFactory
PwLocationProviderFactory pwLocationProviderFactory = new PwLocationProviderFactory();

// Create PwMseLocationProvider
PwLocationProvider locationProvider = pwLocationProviderFactory.getPwMseLocationProvider(mContext,
    new PwLocationProviderConnectivityDetector(), <!-- YOUR_VENUE_GUID -->);
```

####PwMockLocationProvider
The PwMockLocationProvider class allows you to implement a mock provider for testing and validation. This is extremely useful for location testing when you are not able to be on location at a venue which was a proper location provider. The mock location provider is initialized with configuration object which is populated with JSON data.

```java
// Create PwLocationProviderFactory
PwLocationProviderFactory pwLocationProviderFactory = new PwLocationProviderFactory();

// Specify mock JSON filename
String jsonFileName = <!-- YOUR_MOCK_JSON_FILE -->;

// Specify repeat
boolean repeat = true;

// Create MockLocationsDisabledListener listener handles when "Allow mock locations" is disabled in "Developer options"
MockLocationsDisabledListener listener = new MockLocationsDisabledListener() {
  public void onMockLocationsDisabled() {
    // handles when "Allow mock locations" is disabled in "Developer options"
  }
};

// Create PwMockLocationProvider
PwMockLocationProvider locationProvider = (PwMockLocationProvider) pwLocationProviderFactory.getPwMockLocationProvider(mContext, jsonFileName, listener, repeat);
```

####Location Updates
```java
PwLocationListener listener = new PwLocationListener() {
  @Override
  public void onConnectionFailed(PwConnectionResult pwConnectionResult) {
    // handle failure...    
  }

  @Override
  public void onLocationChanged(Location location) {
    // handle update...
  }

  @Override
  public void onStatusChanged(String s, int i, Bundle bundle) {
    // handle status change...
  }

  @Override
  public void onProviderEnabled(String s) {
    // handle provider change...
  }

  @Override
  public void onProviderDisabled(String s) {
    // handle provider change...  
  }
};

locationProvider.requestLocationUpdates(listener);
```
