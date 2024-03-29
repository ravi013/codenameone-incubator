Codename One Offline Build Tools
Author: Steve Hannah <steve@weblite.ca>

Synopsis
========

A set of tools for building CodenameOne applications offline (i.e. without using the build server).

Currently there is support only for iOS and Android builds, but I plan to work on the rest as required.

Requirements
============

1. Running Mac OS X 10.6 or higher
2. JDK 1.7 or higher installed
3. Xcode 4 or higher installed

Installation:
=============

1. Check out the build tools from SVN:

$ svn checkout https://codenameone-incubator.googlecode.com/svn/trunk/shannah/offline-build-tools codenameone-build-tools

2. Install the build tools using the ant install script:

$ cd codenameone-build-tools
$ ant install

3. Assuming the installation went properly, you should see a file named build-ios.xml inside the dist directory.  You just
need to include this file inside the build.xml file of the codenameone applicaton project that you are developing.

e.g.

<import file="/path/to/codenameone-build-tools/dist/build-ios.xml"/>

This will add an ANT target called "build-for-ios-device-locally".

Building Your Application for iOS
==================================

Assuming you have added the <import> into your application's build.xml file, you can either build this target from the command line:

$ cd /path/to/my-project
$ ant build-for-ios-device-locally

Or you can do it from inside Netbeans's File tab, by right-clicking "build.xml", then select "Run Target" > "Other Targets" > "build-for-ios-device-locally".

This will compile your application, convert it to and Objective-C Xcode project using XMLVM, and open up this project in Xcode.
Once you are in Xcode, you should be able to run/build the app like a normal native iOS app.

**Note**  You can't build for the simulator, only an iOS device.  This is because the project is linked to the libzbar.a archive which includes binaries only for arm (not i386).

If you have your iPhone connected with a valid provisioning profile, you should be able to run and debug your application directly on your iPhone (or iPad).


Building Your Application for Android
=====================================

Assuming you have added the <import> into your application's build.xml file, you can either build this target from the command line:

$ cd /path/to/my-project
$ ant build-for-android-device-locally

Or you can do it from inside Netbeans's File tab, by right-clicking "build.xml", then select "Run Target" > "Other Targets" > "build-for-android-device-locally".

This will compile your application and build the apk.  If you have an appropriate Android device 
connected  to your computer, it will attempt to install the apk onto the device.

Building Your Application for JavaSE (i.e. the Simulator)
=========================================================

Assuming you have added the <import> into your application's build.xml file, you can either build this target from the command line:

$ cd /path/to/my-project
$ ant build-for-JavaSE-locally

Or you can do it from inside Netbeans's File tab, by right-clicking "build.xml", then select "Run Target" > "Other Targets" > "build-for-JavaSE-locally".

This will compile the application and run it locally on your computer.  This is effectively the equivalent of just running the project in Netbeans, but it can be handy if you have made changes to the Codename One core and you need to test them.


Building Your Application for Blackberry
=========================================================

** NOTE: The RIM offline building doesn't work currently without modifying all CN1 files
to comply with CLDC.  This is because retroweaving is required to make code compatible and
it is not working yet in the offline build.....  IE.  BlackBerry offline builds are currently broken for the most part***

Assuming you have added the <import> into your application's build.xml file, you can either build this target from the command line:

$ cd /path/to/my-project
$ ant build-for-rim-locally

Or you can do it from inside Netbeans's File tab, by right-clicking "build.xml", then select "Run Target" > "Other Targets" > "build-for-rim-locally".

This will compile the application and run it locally on your computer.  This is effectively the equivalent of just running the project in Netbeans, but it can be handy if you have made changes to the Codename One core and you need to test them.