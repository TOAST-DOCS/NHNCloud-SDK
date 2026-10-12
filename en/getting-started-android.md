<!-- machine_translated: true -->

<!-- pre-align:aligned sig=05f610b13df2 -->

<a id="nhn-cloud-sdk-user-guide-getting-started-android"></a>
## NHN Cloud > SDK User Guide > Getting Started > Android { #nhn-cloud-sdk-user-guide-getting-started-android }

<a id="supported-environment"></a>
## Supported Environment { #supported-environment }

* Android 5.1(API 22) or higher

<a id="nhn-cloud-sdk-components"></a>
## NHN Cloud SDK Components { #nhn-cloud-sdk-components }

NHN Cloud SDK for Android consists of the following:

* Common SDK
* Core SDK
* [Logger](./log-collector-android) SDK
* [Native Crash Reporter](./log-collector-ndk) SDK
* Push Core SDK
* [Push Firebase Cloud Messaging](./push-android) SDK
* [Credit Card Recognizer](./creditcard-recognizer-android) SDK

You can selectively apply the required feature among the services provided by NHN Cloud SDK.

| Gradle Dependency                           | Service           |
| ------------------------------------------- | ----------------- |
| com.nhncloud.android:nhncloud-common:1.14.0       | Common      |
| com.nhncloud.android:nhncloud-core:1.14.0         | Core        |
| com.nhncloud.android:nhncloud-logger:1.14.0       | Log & Crash |
| com.nhncloud.android:nhncloud-crash-reporter-ndk:1.14.0       | Native Crash Reporter |
| com.nhncloud.android:nhncloud-push-core:1.14.0    | Push Core   |
| com.nhncloud.android:nhncloud-push-fcm:1.14.0    | Push <br>Firebase Cloud Messaging |
| com.nhncloud.android:nhncloud-creditcard-recognizer:1.14.0    | Credit Card Recognizer |

<a id="apply-nhn-cloud-sdk-to-android-studio-projects"></a>
## Apply NHN Cloud SDK to Android Studio Projects { #apply-nhn-cloud-sdk-to-android-studio-projects }

<a id="build-android-with-gradle"></a>
### 1. Build Android with Gradle { #build-android-with-gradle }

To use all NHN Cloud SDK services, set dependency as shown below.

```groovy
repositories {
  mavenCentral()
}

dependencies {
  implementation 'com.nhncloud.android:nhncloud-sdk:1.14.0'
}
```

The following describes how to set dependency for each product of NHN Cloud SDK.

- [Logger Library Settings](./log-collector-android/#library-setting)
- [Native Crash Reporter Library Settings](./log-collector-ndk/#library-setting)
- [Push Library Settings](./push-android/#library-setting)
- [Credit Card Recognizer Library Settings](./creditcard-recognizer-android/#add-dependency)

- [ID Card Recognizer Library Settings](./idcard-recognizer-android/#add-dependency)

<a id="build-android-with-aar"></a>
### 2. Build Android with AAR { #build-android-with-aar }

Android SDK can be downloaded from the [Downloads](/Download/#nhn-cloud-sdk) page.

<a id="set-user-id"></a>
## Set User ID { #set-user-id }

User ID can be set for NHN Cloud SDK.
The configured User ID is commonly used in each module of NHN Cloud SDK.
Whenever Log Sending API of NhnCloudLogger is called, the configured User ID is sent to a server along with logs.

<a id="specification-for-user-id-setting-api"></a>
### Specification for User ID Setting API { #specification-for-user-id-setting-api }

```java
/* NhnCloudSdk.java */
public static void setUserId(String userId);
```

| Parameters | |
| -- | -- |
| userId | String: User ID|

<a id="example-of-user-id-setting"></a>
### Example of User ID Setting { #example-of-user-id-setting }

<a id="example-of-user-id-setting-login"></a>
#### Login

```java
// Login.
NhnCloudSdk.setUserId(userId);
```

<a id="example-of-user-id-setting-logout"></a>
#### Logout

```java
// Logout.
NhnCloudSdk.setUserId(null);
```

<a id="set-debug-mode"></a>
## Set Debug Mode { #set-debug-mode }

To check internal logs of NHN Cloud SDK, the debug mode can be set.
When you make an inquiry regarding NHN Cloud SDK, sending the logs with the debug mode enabled can be helpful for faster response.

<a id="specification-for-debug-mode-setting-api"></a>
### Specification for Debug Mode Setting API { #specification-for-debug-mode-setting-api }

```java
/* NhnCloudSdk.java */
public static void setDebugMode(boolean debug);
```

| Parameters | |
| -- | -- |
| debug | boolean: true to enable debug mode, false otherwise.|

<a id="usage-example-of-debug-mode-setting"></a>
### Usage Example of Debug Mode Setting { #usage-example-of-debug-mode-setting }

<a id="usage-example-of-debug-mode-setting-enable-debug-mode"></a>
#### Enable Debug Mode

```java
// Enable debug mode.
NhnCloudSdk.setDebugMode(true);
```

<a id="usage-example-of-debug-mode-setting-disable-debug-mode"></a>
#### Disable Debug Mode

```java
// Disable debug mode.
NhnCloudSdk.setDebugMode(false);
```

> [Caution] The debug mode must be disabled before releasing an app.

<a id="use-nhn-cloud-services"></a>
## Use NHN Cloud Services { #use-nhn-cloud-services }

* [Log & Crash](./log-collector-android) User Guide
* [Native Crash Reporter](./log-collector-ndk) User Guide
* [Push](./push-android) User Guide
* [Credit Card Recognizer](./creditcard-recognizer-android) User Guide
* [ID Card Recognizer](./idcard-recognizer-android) User Guide
