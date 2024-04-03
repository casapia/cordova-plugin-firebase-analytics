# Cordova plugin for [Firebase Analytics](https://firebase.google.com/docs/analytics/)

## Index

<!-- MarkdownTOC levels="2,3" autolink="true" -->

- [Supported platforms](#supported-platforms)
- [Installation](#installation)
    - [Disabling analytics data collection](#disabling-analytics-data-collection)
    - [Disabling automatic screen collection](#disabling-automatic-screen-collection)
    - [Adding required configuration files](#adding-required-configuration-files)
- [Functions](#functions)
    - [logEvent](#logevent)
    - [resetAnalyticsData](#resetanalyticsdata)
    - [setCurrentScreen](#setcurrentscreen)
    - [setDefaultEventParameters](#setdefaulteventparameters)
    - [setEnabled](#setenabled)
    - [setUserId](#setuserid)
    - [setUserProperty](#setuserproperty)

<!-- /MarkdownTOC -->

## Supported platforms

- iOS
- Android

## Installation

    $ cordova plugin add cordova-plugin-firebase-analytics

If you get an error about CocoaPods being unable to find compatible versions, run
    
    $ pod repo update

Use variables `ANDROID_FIREBASE_BOM_VERSION` or `IOS_FIREBASE_POD_VERSION` to override dependency versions for Firebase SDKs:
    
    $ cordova plugin add cordova-plugin-firebase-analytics \
        --variable IOS_FIREBASE_POD_VERSION="9.3.0" \
        --variable ANDROID_FIREBASE_BOM_VERSION="30.3.1"

NOTE: on iOS in order to collect demographic, age, gender data etc. you should additionally [include `AdSupport.framework`](https://firebase.google.com/support/guides/analytics-adsupport) into your project.

### Disabling analytics data collection
In some cases, you may wish to temporarily or permanently disable collection of Analytics data. You can set the value of variable `ANALYTICS_COLLECTION_ENABLED` to `false` to prevent collecting any user data:

    $ cordova plugin add cordova-plugin-firebase-analytics \
        --variable ANALYTICS_COLLECTION_ENABLED=false

Later you can re-enable analytics data collection (for instance after getting end-user consent) using method [setEnabled](#setenabledenabled).

### Disabling automatic screen collection
In order to [disable automatic collection of screen view events](https://firebase.googleblog.com/2020/08/google-analytics-manual-screen-view.html) set the value of variable `AUTOMATIC_SCREEN_REPORTING_ENABLED` to `false`:

    $ cordova plugin add cordova-plugin-firebase-analytics \
        --variable AUTOMATIC_SCREEN_REPORTING_ENABLED=false

### Adding required configuration files

No required.

<!-- TypedocGenerated -->

## Functions

### logEvent

**logEvent**(`name`, `params`): `Promise`<`void`\>

Logs an app event.

**`Example`**

```ts
cordova.plugins.firebase.analytics.logEvent("my_event", {param1: "value1"});
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `name` | `string` | Enent name |
| `params` | `Record`<`string`, `string` \| `number` \| `object`[]\> | Event parameters |

#### Returns

`Promise`<`void`\>

Callback when operation is completed

___

### resetAnalyticsData

**resetAnalyticsData**(): `Promise`<`void`\>

Clears all analytics data for this instance from the device and resets the app instance ID.

**`Example`**

```ts
cordova.plugins.firebase.analytics.resetAnalyticsData();
```

#### Returns

`Promise`<`void`\>

Callback when operation is completed

___

### setCurrentScreen

**setCurrentScreen**(`screenName`): `Promise`<`void`\>

Sets the current screen name, which specifies the current visual context in your app. This helps identify the areas in your app where users spend their time and how they interact with your app.

**`Example`**

```ts
cordova.plugins.firebase.analytics.setCurrentScreen("User dashboard");
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `screenName` | `string` | Current screen name |

#### Returns

`Promise`<`void`\>

Callback when operation is completed

___

### setDefaultEventParameters

**setDefaultEventParameters**(`defaults`): `Promise`<`void`\>

Adds parameters that will be set on every event logged from the SDK, including automatic ones.

**`Example`**

```ts
cordova.plugins.firebase.analytics.setDefaultEventParameters({foo: "bar"});
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `defaults` | `Record`<`string`, `string` \| `number` \| `object`[]\> | Key-value default parameters map |

#### Returns

`Promise`<`void`\>

Callback when operation is completed

___

### setEnabled

**setEnabled**(`enabled`): `Promise`<`void`\>

Sets whether analytics collection is enabled for this app on this device.

**`Example`**

```ts
cordova.plugins.firebase.analytics.setEnabled(false);
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `enabled` | `boolean` | Flag that specifies new state |

#### Returns

`Promise`<`void`\>

Callback when operation is completed

___

### setUserId

**setUserId**(`userId`): `Promise`<`void`\>

Sets the user ID property. This feature must be used in accordance with Google's Privacy Policy.

**`See`**

https://www.google.com/policies/privacy

**`Example`**

```ts
cordova.plugins.firebase.analytics.setUserId("12345");
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `userId` | `string` | User's indentifier string |

#### Returns

`Promise`<`void`\>

Callback when operation is completed

___

### setUserProperty

**setUserProperty**(`name`, `value`): `Promise`<`void`\>

Sets a user property to a given value. Be aware of automatically collected user properties.

**`See`**

https://support.google.com/firebase/answer/6317486?hl=en&ref_topic=6317484

**`Example`**

```ts
cordova.plugins.firebase.analytics.setUserProperty("name1", "value1");
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `name` | `string` | Property name |
| `value` | `string` | Property value |

#### Returns

`Promise`<`void`\>

Callback when operation is completed
