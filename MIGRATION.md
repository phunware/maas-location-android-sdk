# Location SDK Migration Guide

## Upgrade from 3.7.x to 3.7.3

#### General

This release has bug fixes and performance improvements.

#### Upgrade Steps

1. Open the `build.gradle` from your project and change the implementation statement to `com.phunware.location:location:3.7.3` and then sync the project.


## Upgrade from 3.6.x to 3.7.0

#### General

Updated locate algorithm .

#### Upgrade Steps

1. Open the `build.gradle` from your project and change the implementation statement to `com.phunware.location:location:3.7.0` and then sync the project.

## Upgrade from 3.5.x to 3.6.0

#### General

No major changes,  updated Google Play Services.

#### Upgrade Steps

1. Open the `build.gradle` from your project and change the compile statement to `com.phunware.location:location:3.6.0` and then sync the project.

## Upgrade from 3.1+ to 3.5.0

#### General

Debug dot mechanism has been moved into the Mapping SDK (v3.7.0 or later)

#### Upgrade Steps

1. Open the `build.gradle` from your project and change the compile statement to `com.phunware.location:location:3.5.0` and then sync the project.
2. Remove all references to `PwAzulDebugLocationListener`. This class has been removed.
Some of these debug APIs have been moved to `PwAzulDebugListener`.
All of the debug dot callbacks have been internalized into the Mapping SDK.
3. If using debug dots, you will need to also import the Phunware Mapping SDK (v3.7.0 or later).
Open the `build.gradle` from your project and change the compile statement to `com.phunware.mapping:mapping:3.7.0` and then sync the project.
4. After creating a `PhunwareMapManager` object, call the `showDebugDots(boolean)` method to enable or disable the debug dot functionality.

## Upgrade from 3.4.x to 3.4.5

#### General

No major changes,  updated Locate algorithm.

#### Upgrade Steps

1. Open the `build.gradle` from your project and change the compile statement to `com.phunware.location:location:3.4.5` and then sync the project.

## Upgrade from 3.3.x to 3.4.0

### Library updates
- compileSdkVersion - 27
- buildToolsVersion - 27.0.3
- targetSdkVersion - 26
- Support Library version - 27.1.0
- Google Play Services version - 11.8.0
- Okhttp version - 3.10.0
- Gson version - 2.8.2

#### General

This release includes support for our new BLE provider, Locate.

#### Upgrade Steps

1. Open the `build.gradle` from your project and change the compile statement to `com.phunware.location:location:3.4.0` and then sync the project.

## Upgrade from 3.2.x to 3.3.0

#### General

This release includes support for our new BLE provider, Locate.

#### Upgrade Steps

1. Open the `build.gradle` from your project and change the compile statement to `com.phunware.location:location:3.3.0` and then sync the project.

#### Deprecated

`provider-senion` and `provider-accuware` are no longer supported. 
