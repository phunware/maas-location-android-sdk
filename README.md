#PWLocation SDK for Android (BETA)
================

Version 0.5.0

This is Phunware's Android SDK for the Location module. Visit http://maas.phunware.com/ for more details and to sign up.



Requirements
------------

* Latest MaaS Core



Documentation
-------------

MaaS Location documentation is included in the Documents folder in the repository as both HTML and as a .jar. You can also find the latest documentation here: http://phunware.github.io/maas-location-android-sdk/


Prerequisites
-------------

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


Integration
-----------

TBD
