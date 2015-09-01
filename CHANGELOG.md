#PWLocation SDK for Android Change log

##1.1.0 (August 31th, 2015)
 *  Updated PwSLLocationProvider internals to provide more accurate and battery efficent location updates.
 #  IMPORTANT: This update changes the map identifier value used to initialize PWSLLocationManager. Please contact Phunware for your new map identifier values. These new values apply only to PWLocation v1.1.0 and beyond.
 *  Added a new location provider, PwFusedLocationProvider that allows you to fused multiple location provider updates based on polygons and floor identifiers. Please read more about this provider and how to use it here: https://confluence.phunware.com/pages/viewpage.action?pageId=12551886
 *  Added updateInterval to PWMSELocationManager that allows you to modify the update frequency of the MSE location provider. The default update frequency is 3 seconds.

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
