# Location SDK Migration Guide

## Upgrade from 3.4.0 to 3.4.1

#### General

No major changes,  updated Locate algorithm.

#### Upgrade Steps

1. Open the `build.gradle` from your project and change the compile statement to `com.phunware.location:location:3.4.1` and then sync the project.

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
