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

 The location library is broken into separate components so that you can import only the parts of the library needed for your project. All packages can be imported by adding the following to your app's `build.gradle` file
 ```
 compile 'com.phunware.location:provider-managed:3.0.1'
 compile 'com.phunware.location:provider-senion:3.0.1'
 compile 'com.phunware.location:provider-cmx:3.0.1'
 compile 'com.phunware.location:provider-fused:3.0.1'
 compile 'com.phunware.location:provider-gps:3.0.1'
 compile 'com.phunware.location:provider-mock:3.0.1'
 compile 'com.phunware.location:core:3.0.1'
 ```
 Importing any of the providers will automatically include the `core` package. When you import `provider-managed`, all associated location provider libraries are included.

Needed Permissions
-----------
In the Android manifest, the following permissions are needed:

```
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
<uses-permission android:name="android.permission.CHANGE_WIFI_STATE" />
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
<uses-permission android:name="android.permission.BLUETOOTH"/>
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN"/>
<uses-permission android:name="android.permission.WAKE_LOCK"/>
<uses-feature android:name="android.hardware.bluetooth_le" android:required="false"/>
```

Note that BLE and Android SDK version 4.3 (API 18) or above are required if Bluetooth is actually is going to be used. If your users only are going to use Bluetooth for positioning, you should change the android:required attribute to true (this will filter out non-BLE devices at Google Play). Observe that the WAKE_LOCK permission can be removed, but background navigation performance might become worse.

Integration
-----------
  All the location provider types extend `PwLocationProvider`

####PwSlLocationProvider
The PwSlLocationProvider class defines the interface for configuring the delivery of BLE location-related events to your application. You use an instance of this class to establish the parameters that determine when location events should be delivered and to start and stop the actual delivery of those events.

```java
// Create floorId mapping
Map<String, Long> floorIDMapping = new HashMap<String, Long>();
floorIdMap.put("<YOUR_SL_FLOOR_ID_1>", <!-- YOUR_PW_FLOOR_ID_1 -->);

// Create PwSlLocationProvider
PwSlLocationProvider locationProvider = SenionProviderFactory.create(this,
                    getSenionCustomerId(),
                    getSenionMapKey(),
                    floorIdMap)
                    .createLocationProvider();
```

####PwFusedLocationProvider
The PwFusedLocationProvider class defines the interface for configuring the delivery of BLE/MSE/QC location-related events to your application. You use an instance of this class to establish the parameters that determine when location events should be delivered and to start and stop the actual delivery of those events.

```java
// Create PwLocationProviderFactory
PwLocationProviderFactory pwLocationProviderFactory = new PwLocationProviderFactory();

// Create default location provider, which is applied when no valid location reported from given indoor location provider.
<!-- The GPS location provider will be used when default location provider is null. -->
PwLocationProvider defaultLocationProvider = null;
// locationProviderFactory.getPwGPSLocationProvider(getApplicationContext());

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

####PwCmxLocationProvider
The PwCmxLocationProvider class defines the interface for configuring the delivery of Cisco Mobility Services Engine (CMX) location-related events to your application. You use an instance of this class to establish the parameters that determine when location events should be delivered and to start and stop the actual delivery of those events.
```java
// Create PwMseLocationProvider
PwLocationProvider locationProvider = CMXProviderFactory.create(mContext, <!-- YOUR_VENUE_GUID -->)
.createLocationProvider();
```

If for some reason multiple copies of  your building exist in MaaS, only the first one registered with CMX will report the correct floorIDs. For any other building copies, you will need to pass a map of MSE floor IDs to MaaS floor IDs like so:
```java
// Create floor ID mappin
Map<String, Long> floorIdMap = new ArrayMap<String, Long>();

int[] cmxFloorIds = getResources().getIntArray(R.array.cmx_floor_ids);
int[] pwFloorIDs = getResources().getIntArray(R.array.pw_floor_ids);

if (cmxFloorIds.length != pwFloorIDs.length
        || mseFloorIds.length == 0) {
    Log.d(TAG, "The floorIdMapping length doesn't match");
    return null;
}

int length = cmxFloorIds.length;
for (int i = 0; i < length; i++) {
    floorIdMap.put(String.valueOf(cmxFloorIds[i]), (long) pwFloorIDs[i]);
}
// Create PwMseLocationProvider
PwLocationProvider locationProvider = CMXProviderFactory.create(mContext, <!-- YOUR_VENUE_GUID -->,
floorIdMap).createLocationProvider();
```

####PwMockLocationProvider
The PwMockLocationProvider class allows you to implement a mock provider for testing and validation. This is extremely useful for location testing when you are not able to be on location at a venue which was a proper location provider. The mock location provider is initialized with configuration object which is populated with JSON data.

```java
// Specify mock JSON filename
String jsonFileName = <!-- YOUR_MOCK_JSON_FILE -->;

// Specify app package name
String appPackageName = <!-- YOUR_APP_PACKAGE_NAME -->;

// Create MockLocationsDisabledListener listener handles when "Allow mock locations" is disabled in "Developer options"
MockLocationsDisabledListener listener = new MockLocationsDisabledListener() {
  public void onMockLocationsDisabled() {
    // handles when "Allow mock locations" is disabled in "Developer options"
  }
};
// Create PwMockLocationProvider
PwMockLocationProvider locationProvider = (PwMockLocationProvider) MockProviderFactory.create(mContext, appPackageName, jsonFileName, listener);
```

####PwManagedLocationProvider
The PwManagedLocationProvider class allows you to implement Phunware's managed location software to further improve upon locations from your location provider hardware. Currently supported location providers are: CMX, CMX + Senion, Senion, and BeaconPoint. From a code standpoint, setting up a managed location provider is the same regardless of your setup. All of these attributes are set through the MaaS portal.

```java
// Create ManagedLocationProviderFactoryBuilder
ManagedProviderFactory.ManagedProviderFactoryBuilder builder = new ManagedProviderFactory.ManagedProviderFactoryBuilder();

//build location provider
PwManagedLocationProvider provider = builder.application(mApplication)
      .context(mContext)
      .venueId(<!--YOUR_BUILDING_ID-->)
      .slCustomerId(<!--YOUR_SL_CUSTOMER_ID-->)
      .slMapKey(<!--YOUR_SL_MAP_ID-->)
      .bpOrgId(<!--YOUR_BEACONPOINT_ORG_ID-->)
      .build()
      .createLocationProvider();
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
