# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [4.3.0][] - 2022-12-19

### Changed

- Reduced location aquisition time for BLE location providers

## [4.2.1][] - 2022-10-21

### Changed

- Bumped analytics-core dependency to 4.1.1

## [4.2.0][] - 2022-08-22

### Changed

- Bumped targetSdkVersion to API 31
- Bumped compileSdkVersion to API 32

## [4.1.0][] - 2022-07-21

### Changed

- Improved loading time for large venues
- Reduced logging during initialization

### Fixed

- Updated all used hardware and sensors to be considered optional

## [4.0.0][] - 2021-08-11

### Added

- Added a new `BeaconCoverageAreaChangedListener` type for detecting when inside/outside the range of a venue's beacon coverage area.
- Added support for multiple location listeners in `PwManagedLocationProvider`

### Changed

- Migrated to AndroidX
- Simplified initialization routine
- Improved beacon scanning
- Bumped minSdkVersion to API 23 (Android 6.0)
- Bumped targetSdkVersion to API 30 (Android 11)
- Updated to modern Google play services
- Updated to modern Firebase dependencies
- Updated Phunware dependencies to 4.0.0

### Removed

- Removed all existing deprecated API

### Fixed

- Fixed several crashes
- Fixed several performance issues

## [3.7.9][] - 2020-06-23

### Changed

- Upgraded to Mist 2.0.110 to support Android 10 devices
- Upgraded to Core 3.5.2
- Updated other third party dependencies

## [3.7.8][] - 2020-02-28

### Added

- Added support for Centrak beacons
- Added support for GPS only venues

### Fixed

- Fixed issues with vBLE provider

## [3.7.7][] - 2020-01-08

### Changed

- Improved accuracy for managed compass
- Improved walking vs stationary detection
- Improved blue dot accuracy when transitioning between indoor and outdoor navigation

### Fixed

- Fixed performance issues

## [3.7.6][] - 2019-12-20

### Fixed

- Fixed an issue where blue dot re-acquisitions were taking too long
- Fixed a crash caused by bad values in beacon data
- Fixed performance issues

## [3.7.5][] - 2019-11-15

### Changed

- Improved blue dot accuracy when initially transitioning from GPS to BLE location providers
- Improved managed compass
- Increase threshold for dead reckoning

## [3.7.4][] - 2019-09-25

### Changed

- Improved transition between GPS and BLE
- Improved blue dot accuracy
- Floor detection works better with GPS enabled

## [3.7.3][] - 2019-09-19

### Fixed

- Added unique names for modules to address issues with duplicate kotlin_module files

## [3.7.2][] - 2019-09-03

### Changed

- Updated guava to 28.1-android

## [3.7.1][] - 2019-06-11

### Fixed

- Fixed an issue in the native layer

## [3.7.0][] - 2019-04-02

### Added

- Ability to blend GPS with indoor location providers
- Added Managed Compass for use with Mapping SDK to improve heading experience

## [3.6.0][] - 2018-12-20

### Changed

- Updated to Google Play Services 16.0.0
- Updated to Core 3.5.0
- Built with Android Support Library 28.0.0

## [3.5.1][] - 2018-10-08

### Changed

- Updated Locate algorithm

## [3.5.0][] - 2018-09-19

### Changed

- Updated debug dot mechanism
- Updated Locate algorithm

### Fixed

- Fixed performance issues

## [3.4.5][] - 2018-08-30

### Added

- BLE restart logic for certain BLE chipsets

### Changed

- Updated Locate algorithm
- Improved floor change detection

## [3.4.4][] - 2018-07-31

### Changed

- Updated Locate algorithm

### Fixed

- Various bug fixes

## [3.4.3][] - 2018-06-27

### Changed

- Updated Locate algorithm

### Fixed

- Various bug fixes

## [3.4.2][] - 2018-05-25

### Changed

- Updated Locate algorithm

### Fixed

- Various bug fixes

## [3.4.1][] - 2018-04-17

### Changed

- Updated Locate algorithm

## [3.4.0][] - 2018-04-05

### Changed

- Updated Google Play Services to 11.8.0
- Mist updated to 1.4.22

### Fixed

- Various bug fixes

## [3.3.1][] - 2018-03-20

### Changed

- Updated Locate algorithm

### Fixed

- Various bug fixes

## [3.3.0][] - 2018-02-23

### Added

- New BLE provider (Phunware Locate)

### Changed

- Added additional logging for troubleshooting

## [3.2.1][] - 2017-10-19

### Changed

- Mist updated to 1.3.1

## [3.2.0][] - 2017-10-11

### Changed

- Updated Google Play Services to 11.4.0
- Updated to Core 3.2.0

### Fixed

- Various bug fixes

## [3.1.5][] - 2017-07-21

### Changed

- Mist updated to 1.1.3

### Fixed

- Latency fix

## [3.1.4][] - 2017-06-30

### Fixed

- Mist fix for multiple instantiations

## [3.1.3][] - 2017-06-27

### Changed

- Mist updated to 1.1.0
- Algorithm rework

## [3.1.2][] - 2017-06-02

### Changed

- ManagedProvider now supports API 18 (API 21 required)
- Mist algorithm rework

## [3.1.1][] - 2017-03-28

### Changed

- Managed provider updated to pull keys from portal

### Fixed

- Various bug fixes

## [3.1.0][] - 2017-01-27

### Added

- Initial release of Managed Provider

### Fixed

- Various bug fixes

## [3.0.1][] - 2016-10-06

### Changed

- Using the latest PWCore 3.0.2
- Updated Google Play Services to 9.6.1

## [3.0.0][] - 2016-08-01

### Changed

- Updated PwMSELocationProvider to re-bind to MARS after timeout
- Updated PWCore to 3.0.0
- Upgrade SenionLab SDK to 4.7.0
- Updated Google Play Services to 9.0.2
- Switched from Retrofit to OkHttp

## [1.1.0][] - 2015-08-31

### Added

- Added a new location provider, PwFusedLocationProvider that allows you to fused multiple location provider updates based on polygons and floor identifiers. Please read more about this provider and how to use it [here](https://confluence.phunware.com/pages/viewpage.action?pageId=12551886)
- Added updateInterval to PwMSELocationProvider that allows you to modify the update frequency of the MSE location provider. The default update frequency is 3 seconds.

### Changed

- Updated PwSLLocationProvider internals to provide more accurate and battery efficient location updates.
- IMPORTANT: This update changes the map identifier value used to initialize PwSLLocationProvider. Please contact Phunware for your new map identifier values. These new values apply only to PWLocation v1.1.0 and beyond.
- IMPORTANT: You have to add the service `<service android:name="com.senionlab.slutilities.service.SLIndoorLocationService" />` to the manifest.xml of your project.

## [1.0.0][] - 2015-01-06

### Changed

- Updated SLDistribution to 3.0.10
- Updated MaaSCore to 1.3.11

## 0.9.2 - 2014-11-24

### Changed

- Updated SLDistribution to 3.0.7

## 0.9.1 - 2014-10-07

### Added

- Add location update failure callback

### Changed

- Updated MaaSCore to 1.3.8

### Fixed

- Fixed building warnings

## [0.9.0][] - 2014-09-19

### Added

- Added Mock Location Manager

### Fixed

- Various bug fixes

## 0.5.0 - 2014-07-30

### Added

- Initial release (BETA)

[4.3.0]: https://github.com/phunware/maas-location-android-sdk/compare/4.2.1...4.3.0
[4.2.1]: https://github.com/phunware/maas-location-android-sdk/compare/4.2.0...4.2.1
[4.2.0]: https://github.com/phunware/maas-location-android-sdk/compare/4.1.0...4.2.0
[4.1.0]: https://github.com/phunware/maas-location-android-sdk/compare/4.0.0...4.1.0
[4.0.0]: https://github.com/phunware/maas-location-android-sdk/compare/v3.7.9...4.0.0
[3.7.9]: https://github.com/phunware/maas-location-android-sdk/compare/v3.7.8...v3.7.9
[3.7.8]: https://github.com/phunware/maas-location-android-sdk/compare/v3.7.7...v3.7.8
[3.7.7]: https://github.com/phunware/maas-location-android-sdk/compare/v3.7.6...v3.7.7
[3.7.6]: https://github.com/phunware/maas-location-android-sdk/compare/v3.7.5...v3.7.6
[3.7.5]: https://github.com/phunware/maas-location-android-sdk/compare/v3.7.4...v3.7.5
[3.7.4]: https://github.com/phunware/maas-location-android-sdk/compare/v3.7.3...v3.7.4
[3.7.3]: https://github.com/phunware/maas-location-android-sdk/compare/v3.7.2...v3.7.3
[3.7.2]: https://github.com/phunware/maas-location-android-sdk/compare/v3.7.1...v3.7.2
[3.7.1]: https://github.com/phunware/maas-location-android-sdk/compare/v3.7.0...v3.7.1
[3.7.0]: https://github.com/phunware/maas-location-android-sdk/compare/v3.6.0...v3.7.0
[3.6.0]: https://github.com/phunware/maas-location-android-sdk/compare/v3.5.1...v3.6.0
[3.5.1]: https://github.com/phunware/maas-location-android-sdk/compare/v3.5.0...v3.5.1
[3.5.0]: https://github.com/phunware/maas-location-android-sdk/compare/v3.4.5...v3.5.0
[3.4.5]: https://github.com/phunware/maas-location-android-sdk/compare/v3.4.4...v3.4.5
[3.4.4]: https://github.com/phunware/maas-location-android-sdk/compare/v3.4.3...v3.4.4
[3.4.3]: https://github.com/phunware/maas-location-android-sdk/compare/v3.4.2...v3.4.3
[3.4.2]: https://github.com/phunware/maas-location-android-sdk/compare/v3.4.1...v3.4.2
[3.4.1]: https://github.com/phunware/maas-location-android-sdk/compare/3.4.0...v3.4.1
[3.4.0]: https://github.com/phunware/maas-location-android-sdk/compare/3.3.1...3.4.0
[3.3.1]: https://github.com/phunware/maas-location-android-sdk/compare/3.3.0...3.3.1
[3.3.0]: https://github.com/phunware/maas-location-android-sdk/compare/3.2.1...3.3.0
[3.2.1]: https://github.com/phunware/maas-location-android-sdk/compare/3.2.0...3.2.1
[3.2.0]: https://github.com/phunware/maas-location-android-sdk/compare/v3.1.5...3.2.0
[3.1.5]: https://github.com/phunware/maas-location-android-sdk/compare/v3.1.4...v3.1.5
[3.1.4]: https://github.com/phunware/maas-location-android-sdk/compare/3.1.3...v3.1.4
[3.1.3]: https://github.com/phunware/maas-location-android-sdk/compare/3.1.2...3.1.3
[3.1.2]: https://github.com/phunware/maas-location-android-sdk/compare/v3.1.0...3.1.2
[3.1.1]: https://github.com/phunware/maas-location-android-sdk/compare/v3.1.0...v3.1.1
[3.1.0]: https://github.com/phunware/maas-location-android-sdk/compare/v.3.0.1...v3.1.0
[3.0.1]: https://github.com/phunware/maas-location-android-sdk/compare/v3.0.0...v.3.0.1
[3.0.0]: https://github.com/phunware/maas-location-android-sdk/compare/v1.1.0...v3.0.0
[1.1.0]: https://github.com/phunware/maas-location-android-sdk/compare/v1.0.0...v1.1.1
[1.0.0]: https://github.com/phunware/maas-location-android-sdk/compare/v0.9.0...v1.0.0
[0.9.0]: https://github.com/phunware/maas-location-android-sdk/tree/v0.9.0
