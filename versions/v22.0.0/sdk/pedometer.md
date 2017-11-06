---
title: Pedometer
---

Use Core Motion (iOS) or Google Fit (Android) to get the user's step count.

![sketch](S1gdfOb4Z)

### `Expo.Pedometer.isAvailableAsync()`

Determine whether the pedometer is available.

#### Returns

- Returns a promise that resolves to a `Boolean`, indicating whether the pedometer is available on this device.

### `Expo.Pedometer.getStepCountAsync(start, end)`

Get the step count between two dates.

#### Arguments

- **start (_Date_)** -- A date indicating the start of the range over which to measure steps.
- **end (_Date_)** -- A date indicating the end of the range over which to measure steps.

#### Returns

- Returns a promise that resolves to an `Object` with a `steps` key, which is a `Number` indicating the number of steps taken between the given dates.

### `Expo.Pedometer.watchStepCount(callback)`

Subscribe to pedometer updates.

#### Arguments

- **callback (_function_)** A callback that is invoked when new step count data is available. The callback is provided a single argument that is an object with a `steps` key.

#### Returns

- An EventSubscription object that you can call remove() on when you would like to unsubscribe the listener.

#### attention
for worked correctly pedometer on the apk you should follow this instruction : 
Get an OAuth client ID for your app

Build a standalone app and download the apk, or find one that you have already built.
Go to the Google Developer Credentials.
Click Create credentials, then OAuth client ID, then select the Android radio button.
Run keytool -list -printcert -jarfile growler.apk | grep SHA1 | awk '{ print $2 }' (where growler.apk is the name of the apk produced in step 1).
Take the output from the previous step and insert it in the Signing-certificate fingerprint field.
Add your android.package from app.json (eg: ca.brentvatne.growlerprowler) to the Package name field.
Press Create.
https://forums.expo.io/t/pedometer-fails-after-building-standalon-app/4470/3
