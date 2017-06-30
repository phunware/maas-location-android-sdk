#PWLocation SDK for Android Change log

##3.1.4 (June 30, 2017)
 * Mist fix for multiple instantiations

##3.1.3 (June 27, 2017)
 * Mist updated to 1.1.0
 * Algorithm rework

##3.1.2 (June 2, 2017)
 * ManagedProvider gracefully supports API 18 (API 21 required)
 * Mist algorithm rework

##3.1.1 (March 28th, 2017)
 * Managed provider updated to pull keys from portal
 * Minor bug fixes and enhancements

##3.1.0 (January 27th, 2017)
 * Initial release of Managed Provider
 * Minor bug fixes and enhancements

##3.0.1 (October 6th, 2016)
 *  Using the latest PWCore 3.0.2
 * Updated Google Play Services to 9.6.1

##3.0.0 (August 1st, 2016)
 *  Using the latest PWCore 3.0.0
 *  Updated `PwMSELocationProvider` to re-bind to MARS after timeout
 * Upgrade SenionLab SDK to 4.7.0
 * Updated Google Play Services to 9.0.2
 * Switched from Retrofit to OkHttp

##1.1.1 (October 2nd, 2015)
 *  Change the endpoints of phunware.com to use HTTPS
 *  Upgrade SenionLab SDK to v4.1.3
 *  Rename the lib name from MaaSLocation.jar to PWLocation.jar

##1.1.0 (August 31st, 2015)
 *  Added a new location provider

##1.1.0 (August 31st, 2015)
 *  Added a new location provider, `PwFusedLocationProvider` that allows you to fused multiple location provider updates based on polygons and floor identifiers. Please read more about this provider and how to use it here: https://confluence.phunware.com/pages/viewpage.action?pageId=12551886
 *  Added updateInterval to `PwMSELocationProvider` that allows you to modify the update frequency of the MSE location provider. The default update frequency is `3` seconds.
 *  Updated `PwSLLocationProvider` internals to provide more accurate and battery efficient location updates.
* IMPORTANT: This update changes the map identifier value used to initialize PwSLLocationProvider. Please contact Phunware for your new map identifier values. These new values apply only to PWLocation v1.1.0 and beyond.
* IMPORTANT: You have to add the service ```<service android:name="com.senionlab.slutilities.service.SLIndoorLocationService" />``` to the manifest.xml of your project.

##1.0.0 (January 6th, 2015)
 * Updated SLDistribution to 3.0.10
 * Updated MaaSCore to 1.3.11

##0.9.2 (Monday, November 24th, 2014)
 * Updated SLDistribution to 3.0.7

##0.9.1 (Tuesday, October 7th, 2014)
 * Fix building warnings
 * Add location update failure callback
 * Updated MaaSCore to 1.3.8

##0.9.0 (Friday, September 19th, 2014)
 * Added Mock Location Manager
 * Bug fixes

##0.5.0 (Wednesday, July 30th, 2014)
 * Initial release (BETA)
