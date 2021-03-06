# Location SDK Changelog

## 3.7.9 (Thursday, July 23rd, 2020)
#### Bug fixes / performance enhancements
* Upgraded to Mist 2.0.110 to support Android 10 devices
* Upgraded to Core 3.5.2
* Updated other third party dependencies

## 3.7.8 (Friday, February 28th, 2020)
#### Bug fixes / performance enhancements
* Added support for Centrak beacons
* Added support for GPS only venues
* Fixed issues with vBLE provider

## 3.7.7 (Wednesday, January 8th, 2020)
#### Bug fixes / performance enhancements
* Improved accuracy for managed compass
* Improved walking vs stationary detection
* Improved blue dot accuracy when transitioning between indoor and outdoor navigation
* Improved code stability and performance

## 3.7.6 (Friday, Dec 20th, 2019)
#### Bug fixes / performance enhancements
* Fixed an issue where blue dot re-acquisitions were taking too long
* Fixed a crash caused by bad values in beacon data
* Internal performance updates

## 3.7.5 (Friday, Nov 15th, 2019)
#### Bug fixes / performance enhancements
* Improved blue dot accuracy when initially transitioning from GPS to BLE location providers
* Improved managed compass
* Increase threshold for dead reckoning

## 3.7.4 (Wednesday, Sep 25th, 2019)
#### Bug fixes / performance enhancements
* Improved transition between GPS and BLE
* Improved blue dot accuracy
* Floor detection works better with GPS enabled

## 3.7.3 (Wednesday, Sep 19th, 2019)
#### Bug Fixes
* Added unique names for modules to address issues with duplicate kotlin_module files

## 3.7.2 (Tuesday, Sep 3rd, 2019)
#### Bug fixes / performance enhancements
* Updated guava to 28.1-android

## 3.7.1 (Tuesday, Jun 11th, 2019)
#### Bug fixes / performance enhancements
* Fixed an issue in the native layer

## 3.7.0 (Tuesday, Apr 2nd, 2019)
#### Features
* Ability to blend GPS with indoor location providers
* Add Managed Compass for use with Mapping SDK to improve heading experience

## 3.6.0 (Thursday, Dec 20th, 2018)
#### Features
* Updated to Google Play Services 16.0.0
* Updated to Core 3.5.0
* Built with Android Support Library 28.0.0

## 3.5.1 (Monday, Oct 8th, 2018)
#### Features
* Updated Locate algorithm

## 3.5.0 (Wednesday, Sept 19th, 2018)
#### Features
* Updated debug dot mechanism
* Updated Locate algorithm

#### Bug fixes / performance enhancements
* Internal performance updates

## 3.4.5 (Thursday, Aug 30th, 2018)
#### Bug fixes / performance enhancements
* Updated Locate algorithm
* Improved floor change detection
* BLE restart logic for certain BLE chipsets

## 3.4.4 (Tuesday, Jul 31st, 2018)
#### Features
* Updated Locate algorithm
* Various Bug fixes

## 3.4.3 (Wednesday, Jun 27th, 2018)
#### Features
* Updated Locate algorithm
* Various Bug fixes

## 3.4.2 (Friday, May 25th, 2018)
#### Features
* Updated Locate algorithm
* Various Bug fixes

## 3.4.1 (Tuesday, Apr 17th, 2018)
#### Features
* Updated Locate algorithm

## 3.4.0 (Thursday, Apr 5th, 2018)
#### Features
* Updated Google Play Services to 11.8.0
* Mist updated to 1.4.22
* Various Bug fixes

## 3.3.1 (Tuesday, Mar 20th, 2018)
#### Features
* Updates made to Locate algorithm
* Various Bug fixes

## 3.3.0 (Friday, Feb 23rd, 2018)
#### Features
* New BLE provider (Phunware Locate)

#### Bug fixes / performance enhancements
* Added additional logging for troubleshooting

## 3.2.1 (Oct 19, 2017)
#### Bug fixes / performance enhancements
 * Mist updated to 1.3.1

## 3.2.0 (Oct 11, 2017)
#### Bug fixes / performance enhancements
 * Updated Google Play Services to 11.4.0
 * Updated to Core 3.2.0
 * Various Bug fixes

##3.1.5 (July 21, 2017)
#### Bug fixes / performance enhancements
 * Mist v1.1.3
 * latency fix

##3.1.4 (June 30, 2017)
#### Bug fixes / performance enhancements
 * Mist fix for multiple instantiations

##3.1.3 (June 27, 2017)
#### Bug fixes / performance enhancements
 * Mist updated to 1.1.0
 * Algorithm rework

##3.1.2 (June 2, 2017)
#### Bug fixes / performance enhancements
 * ManagedProvider gracefully supports API 18 (API 21 required)
 * Mist algorithm rework

##3.1.1 (March 28th, 2017)
#### Bug fixes / performance enhancements
 * Managed provider updated to pull keys from portal
 * Minor bug fixes and enhancements

##3.1.0 (January 27th, 2017)
#### Bug fixes / performance enhancements
 * Initial release of Managed Provider
 * Minor bug fixes and enhancements

##3.0.1 (October 6th, 2016)
#### Bug fixes / performance enhancements
 *  Using the latest PWCore 3.0.2
 * Updated Google Play Services to 9.6.1

##3.0.0 (August 1st, 2016)
#### Bug fixes / performance enhancements
 *  Using the latest PWCore 3.0.0
 *  Updated `PwMSELocationProvider` to re-bind to MARS after timeout
 * Upgrade SenionLab SDK to 4.7.0
 * Updated Google Play Services to 9.0.2
 * Switched from Retrofit to OkHttp

##1.1.1 (October 2nd, 2015)
#### Bug fixes / performance enhancements
 *  Change the endpoints of phunware.com to use HTTPS
 *  Upgrade SenionLab SDK to v4.1.3
 *  Rename the lib name from MaaSLocation.jar to PWLocation.jar

##1.1.0 (August 31st, 2015)
#### Bug fixes / performance enhancements
 *  Added a new location provider

##1.1.0 (August 31st, 2015)
#### Bug fixes / performance enhancements
 *  Added a new location provider, `PwFusedLocationProvider` that allows you to fused multiple location provider updates based on polygons and floor identifiers. Please read more about this provider and how to use it here: https://confluence.phunware.com/pages/viewpage.action?pageId=12551886
 *  Added updateInterval to `PwMSELocationProvider` that allows you to modify the update frequency of the MSE location provider. The default update frequency is `3` seconds.
 *  Updated `PwSLLocationProvider` internals to provide more accurate and battery efficient location updates.
* IMPORTANT: This update changes the map identifier value used to initialize PwSLLocationProvider. Please contact Phunware for your new map identifier values. These new values apply only to PWLocation v1.1.0 and beyond.
* IMPORTANT: You have to add the service ```<service android:name="com.senionlab.slutilities.service.SLIndoorLocationService" />``` to the manifest.xml of your project.

##1.0.0 (January 6th, 2015)
#### Bug fixes / performance enhancements
 * Updated SLDistribution to 3.0.10
 * Updated MaaSCore to 1.3.11

##0.9.2 (Monday, November 24th, 2014)
#### Bug fixes / performance enhancements
 * Updated SLDistribution to 3.0.7

##0.9.1 (Tuesday, October 7th, 2014)
#### Bug fixes / performance enhancements
 * Fix building warnings
 * Add location update failure callback
 * Updated MaaSCore to 1.3.8

##0.9.0 (Friday, September 19th, 2014)
#### Bug fixes / performance enhancements
 * Added Mock Location Manager
 * Bug fixes

##0.5.0 (Wednesday, July 30th, 2014)
#### Bug fixes / performance enhancements
 * Initial release (BETA)
