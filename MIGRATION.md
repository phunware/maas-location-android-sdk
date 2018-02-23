# Location SDK Migration Guide
## Upgrade from 3.2.x to 3.3.0

#### General

This release includes support for our new BLE provider, Locate.

#### Upgrade Steps

1. Open the `build.gradle` from your project and change the compile statement to `com.phunware.location:location:3.3.0` and then sync the project.

#### Deprecated

`provider-senion` and `provider-accuware` are no longer supported. 
