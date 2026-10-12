<!-- machine_translated: true -->

<!-- pre-align:aligned sig=42d42959910d -->

<a id="nhn-cloud-sdk-user-guide-getting-started-ios"></a>
## NHN Cloud > SDK User Guide > Getting Started > iOS { #nhn-cloud-sdk-user-guide-getting-started-ios }

<a id="supported-environment"></a>
## Supported Environment { #supported-environment }

* iOS 11.0 or higher
* The latest version of Xcode

<a id="nhn-cloud-sdk-components"></a>
## NHN Cloud SDK Components { #nhn-cloud-sdk-components }

* NHN Cloud SDK for iOS consists of the following:
    * [Logger](./log-collector-ios) SDK
    * [Push](./push-ios) SDK
    * [Credit-Card OCR](./creditcard-recognizer-ios) SDK
    * [ID-Card OCR](./idcard-recognizer-ios) SDK

* You can selectively apply the required feature among the services provided by NHN Cloud SDK.

| Service | Cocoapods Pod Name | Carthage | Framework | Deployment Target | Dependency | Build Settings |
| --- | --- | --- | --- | --- | --- | --- |
| All | NHNCloudSDK | binary "[https://nh.nu/sdk](https://nh.nu/sdk) | NHNCloudCore.framework<br>NHNCloudCommon.framework<br>NHNCloudLogger.framework<br>NHNCloudPush.framework<br>NHNCloudOCR.framework |  |  |  |
| Mandatory | NHNCloudCore<br>NHNCloudCommon |  | NHNCloudCore.framework<br>NHNCloudCommon.framework | 11.0 |  | OTHER\_LDFLAGS = (<br>"-ObjC",<br>"-lc++"<br>); |
| Log & Crash | NHNCloudLogger |  | NHNCloudLogger.framework | 11.0 | [External & Optional]<br> CrashReporter.framework(NHNCloud) |  |
| Push | NHNCloudPush |  | NHNCloudPush.framework | 11.0 | UserNotifications.framework<br> PushKit.framework |  |
| OCR | NHNCloudOCR |  | NHNCloudOCR.framework | 11.0 | Vision.framework<br> AVFoundation.framework |  |

<a id="apply-nhn-cloud-sdk-to-xcode-projects"></a>
## Apply NHN Cloud SDK to Xcode Projects { #apply-nhn-cloud-sdk-to-xcode-projects }

<a id="apply-nhn-cloud-sdk-with-cococapods"></a>
### 1. Apply NHN Cloud SDK with Cococapods { #apply-nhn-cloud-sdk-with-cococapods }

* Create a Podfile and add a pod for NHN Cloud SDK.

```podspec
platform :ios, '11.0'
use_frameworks!

target '{YOUR PROJECT TARGET NAME}' do
    pod 'NHNCloudSDK'
end
```

<a id="apply-nhn-cloud-sdk-with-swift-package-manager"></a>
### 2. Apply NHN Cloud SDK with Swift Package Manager { #apply-nhn-cloud-sdk-with-swift-package-manager }

* Go to **File > Add Packages...** from XCode.
* For the Package URL, enter 'https://github.com/nhn/nhncloud.ios.sdk' and select **Add Package**.
* Select a library you want to add.

<a id="apply-nhn-cloud-sdk-with-carthage"></a>
### 3. Apply NHN Cloud SDK with Carthage { #apply-nhn-cloud-sdk-with-carthage }

* Create a Cartfile and add NHN Cloud SDK.

```sh
# Full URL
binary "https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_f9e3dc598ca142d3820e1c19343d5428/carthage/NHNCloudSDK.json" 

# Short URL
binary "https://nh.nu/sdk"
```

* Add the frameworks in the created Carthage/Build folder to the Xcode project.

* To use NHN Cloud SDK, you must perform [Framework setting](./getting-started-ios/#frameworks-setup) and [Project setting](./getting-started-ios/#set-up-project).

!!! tip "Note"
    To use desired features among the services selectively, you need to choose only the required frameworks per service and add them to the project.
    For details on required frameworks per service, see [NHN Cloud SDK Components](./getting-started-ios/#nhn-cloud-sdk-components).

<a id="apply-nhn-cloud-sdk-by-downloading-binaries"></a>
### 4. Apply NHN Cloud SDK by Downloading Binaries { #apply-nhn-cloud-sdk-by-downloading-binaries }

* You can download the full iOS SDK from the NHN Cloud [Downloads](../../Download/#nhn-cloud-sdk) page.
* Select the required Framework and add it to your project.

<a id="frameworks-setup"></a>
### Framework Setting { #frameworks-setup }

* To use the Crash Report feature of Logger, you must add CrashReporter.xcframework, which is distributed together in the External folder of the SDK, to the project.
* To use the Push feature, you must add the system framework UserNotifications.framework to the project.
* To use the OCR feature, you must add the system frameworks Vision.framework and AVFoundation.framework to the project.

<a id="set-up-project"></a>
### Project settings { #set-up-project }

* If you integrated NHN Cloud SDK into your project using a method other than CocoaPods, the following additional settings are required.
* Add **-lc++** and **-ObjC** to **Other Linker Flags** of **Build Settings**.
    * **Project Target > Build Settings > Linking > Other Linker Flags**

![other_linker_flags](https://static.toastoven.net/toastcloud/sdk/ios/overview_settings_flags_202206.png)

<a id="import-framework"></a>
### Import Framework { #import-framework }

* Import the frameworks to use.

```objc
#import <NHNCloudCore/NHNCloudCore.h>
#import <NHNCloudLogger/NHNCloudLogger.h>
#import <NHNCloudPush/NHNCloudPush.h>
#import <NHNCloudOCR/NHNCloudOCR.h>
```

<a id="set-user-id"></a>
## Set User ID { #set-user-id }

* User ID can be set for NHN Cloud SDK.
* The configured User ID is commonly used in each module of NHN Cloud SDK.
* Whenever Log Sending API of NHN Cloud Logger is called, the configured User ID is sent to a server along with logs.

<a id="specification-for-user-id-setting-api"></a>
### Specification for User ID Setting API { #specification-for-user-id-setting-api }

```objc
+ (void)setUserID:(NSString *)userID;
```

<a id="usage-example-of-user-id-setting"></a>
### Usage Example of User ID Setting { #usage-example-of-user-id-setting }

```objc
[NHNCloudSDK setUserID:@"NHNCLOUD-USER"];
```

<a id="set-debug-mode"></a>
## Set Debug Mode { #set-debug-mode }

* To check logs within NHN Cloud SDK, the debug mode can be set.
* When you make an inquiry regarding NHN Cloud SDK, sending the logs with the debug mode enabled can be helpful for faster response.

<a id="specification-for-debug-mode-api"></a>
### Specification for Debug Mode API { #specification-for-debug-mode-api }


```objc
+ (void)setDebugMode:(BOOL)debugMode;
```

<a id="usage-example-of-debug-mode-setting"></a>
### Usage Example of Debug Mode Setting { #usage-example-of-debug-mode-setting }

```objc
[NHNCloudSDK setDebugMode:YES];    // or NO
```

> [Caution] The debug mode must be disabled before releasing an app.

<a id="use-nhn-cloud-service"></a>
## Use NHN Cloud Service { #use-nhn-cloud-service }

* [Log & Crash](./log-collector-ios) User Guide
* [Push](./push-ios) User Guide
* [Credit-Card OCR](./creditcard-recognizer-ios) User Guide
* [ID-Card OCR](./idcard-recognizer-ios) User Guide
