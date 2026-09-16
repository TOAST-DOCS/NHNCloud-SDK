<!-- pre-align:aligned sig=edc80b83f7a3 -->

<a id="nhn-cloud-sdk-user-guide-getting-started-ios"></a>
## NHN Cloud > SDK 사용 가이드 > 시작하기 > iOS { #nhn-cloud-sdk-user-guide-getting-started-ios }

<a id="supported-environment"></a>
## 지원 환경 { #supported-environment }

* iOS 11.0 이상
* XCode 최신 버전

<a id="nhn-cloud-sdk-components"></a>
## NHN Cloud SDK의 구성 { #nhn-cloud-sdk-components }

* iOS용 NHN Cloud SDK의 구성은 다음과 같습니다.
    * [Logger](./log-collector-ios) SDK    
    * [Push](./push-ios) SDK
    * [OCR](./creditcard-recognizer-ios) SDK

* NHN Cloud SDK가 제공하는 서비스 중 원하는 기능을 선택해 적용할 수 있습니다.

| Service | Cocoapods Pod Name | Carthage | Framework | Deployment Target | Dependency | Build Settings |
| --- | --- | --- | --- | --- | --- | --- |
| All | NHNCloudSDK | binary "[https://nh.nu/nhncloudsdk](https://nh.nu/nhncloudsdk) | NHNCloudCore.framework<br>NHNCloudCommon.framework<br>NHNCloudLogger.framework<br>NHNCloudPush.framework<br>NHNCloudOCR.framework |  |  |  |
| Mandatory | NHNCloudCore<br>NHNCloudCommon |  | NHNCloudCore.framework<br>NHNCloudCommon.framework | 11.0 |  | OTHER\_LDFLAGS = (<br>"-ObjC",<br>"-lc++"<br>); |
| Log & Crash | NHNCloudLogger |  | NHNCloudLogger.framework | 11.0 | [External & Optional]<br>\* CrashReporter.framework (NHNCloud) |  |
| Push | NHNCloudPush |  | NHNCloudPush.framework | 11.0 | \* UserNotifications.framework<br><br>[Optional]<br>\* PushKit.framework |  |
| OCR | NHNCloudOCR |  | NHNCloudOCR.framework | 11.0 | \* Vision.framework<br>\* AVFoundation.framework |  |

<a id="apply-nhn-cloud-sdk-to-xcode-projects"></a>
## NHN Cloud SDK를 Xcode 프로젝트에 적용 { #apply-nhn-cloud-sdk-to-xcode-projects }

<a id="apply-nhn-cloud-sdk-with-cococapods"></a>
### 1. Cococapods를 사용해 NHN Cloud SDK 적용 { #apply-nhn-cloud-sdk-with-cococapods }

* Podfile을 생성하여 NHN Cloud SDK에 대한 Pod을 추가합니다.

```podspec
platform :ios, '11.0'
use_frameworks!

target '{YOUR PROJECT TARGET NAME}' do
    pod 'NHNCloudSDK'
end
```

<a id="apply-nhn-cloud-sdk-with-swift-package-manager"></a>
### 2. Swift Package Manager를 사용해 NHN Cloud SDK 적용 { #apply-nhn-cloud-sdk-with-swift-package-manager }

* XCode에서 **File > Add Packages...** 메뉴를 선택합니다.
* Package URL에 'https://github.com/nhn/nhncloud.ios.sdk'를 넣고 **Add Package** 버튼을 선택합니다.
* 추가를 원하는 Library를 선택합니다.

<a id="apply-nhn-cloud-sdk-with-carthage"></a>
### 3. Carthage를 사용해 NHN Cloud SDK 적용 { #apply-nhn-cloud-sdk-with-carthage }

* Cartfile을 생성하여 NHN Cloud SDK를 추가합니다.

```sh
# Full URL
binary "https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_f9e3dc598ca142d3820e1c19343d5428/carthage/NHNCloudSDK.json" 

# Short URL
binary "https://nh.nu/sdk"
```

* 생성된 Carthage/Build 폴더의 Framework를 Xcode 프로젝트에 추가합니다.
* NHN Cloud SDK를 사용하려면 [프레임워크 설정](./getting-started-ios/#frameworks-setup)과 [프로젝트 설정](./getting-started-ios/#set-up-project)을 해야 합니다.

!!! tip "알아두기"
    서비스 중 원하는 기능을 선택하여 사용하기 위해서는 서비스별로 필요한 Framework만 선택하여 프로젝트에 추가해야 합니다.
    서비스별로 필요한 Framework는 [NHN Cloud SDK의 구성](./getting-started-ios/#nhn-cloud-sdk-components)에서 확인할 수 있습니다.

<a id="apply-nhn-cloud-sdk-by-downloading-binaries"></a>
### 4. 바이너리를 다운로드하여 NHN Cloud SDK 적용 { #apply-nhn-cloud-sdk-by-downloading-binaries }

* NHN Cloud의 [Downloads](../../Download/#nhn-cloud-sdk) 페이지에서 전체 iOS SDK를 다운로드할 수 있습니다.
* 필요한 Framework를 선택하여 프로젝트에 추가합니다.

<a id="frameworks-setup"></a>
### 프레임워크 설정 { #frameworks-setup }

* Logger의 Crash Report 기능을 사용하려면 SDK의 External 폴더에 함께 배포되는 CrashReporter.xcframework를 프로젝트에 추가해야 합니다.
* Push 기능을 사용하려면 프로젝트에 시스템 프레임워크인 UserNotifications.framework를 추가해야 합니다.
* OCR 기능을 사용하려면 프로젝트에 시스템 프레임워크인 Vision.framework와 AVFoundation.framework를 추가해야 합니다.

<a id="set-up-project"></a>
### 프로젝트 설정 { #set-up-project }

* Cocoapods 이외의 방식으로 프로젝트에 NHN Cloud SDK를 통합한 경우 아래 설정이 추가로 필요합니다.
* **Build Settings**의 **Other Linker Flags**에 **-lc++**와 **-ObjC** 항목을 추가합니다.
    * **Project Target > Build Settings > Linking > Other Linker Flags**

![other_linker_flags](https://static.toastoven.net/toastcloud/sdk/ios/overview_settings_flags_202206.png)

<a id="import-framework"></a>
### 프레임워크 가져오기 { #import-framework }

* 사용하려는 프레임워크를 가져옵니다(import).

```objc
#import <NHNCloudCore/NHNCloudCore.h>
#import <NHNCloudLogger/NHNCloudLogger.h>
#import <NHNCloudPush/NHNCloudPush.h>
#import <NHNCloudOCR/NHNCloudOCR.h>
```

<a id="set-user-id"></a>
## 사용자 아이디 설정 { #set-user-id }

* NHN Cloud SDK에 사용자 아이디를 설정할 수 있습니다.
* 설정한 사용자 아이디는 NHN Cloud SDK의 각 모듈에서 공통으로 사용됩니다.
* NHN Cloud Logger의 로그 전송 API를 호출할 때마다 설정한 사용자 아이디를 로그와 함께 서버로 전송합니다.

<a id="specification-for-user-id-setting-api"></a>
### 사용자 아이디 설정 API 명세 { #specification-for-user-id-setting-api }

```objc
+ (void)setUserID:(NSString *)userID;
```

<a id="usage-example-of-user-id-setting"></a>
### 사용자 아이디 설정 사용 예 { #usage-example-of-user-id-setting }

```objc
[NHNCloudSDK setUserID:@"NHNCloud-USER"];
```

<a id="set-debug-mode"></a>
## 디버그 모드 설정 { #set-debug-mode }

* NHN Cloud SDK의 내부 로그를 확인하기 위해 디버그 모드를 설정할 수 있습니다.
* NHN Cloud SDK와 관련해 문의하실 때는 디버그 모드를 활성화한 후 콘솔 로그를 전달해 주시면 빠르게 지원해드릴 수 있습니다.

<a id="specification-for-debug-mode-api"></a>
### 디버그 모드 설정 API 명세 { #specification-for-debug-mode-api }


```objc
+ (void)setDebugMode:(BOOL)debugMode;
```

<a id="usage-example-of-debug-mode-setting"></a>
### 디버그 모드 설정 사용 예 { #usage-example-of-debug-mode-setting }

```objc
[NHNCloudSDK setDebugMode:YES];    // or NO
```

> [주의] 애플리케이션 배포시에는 디버그 모드를 `반드시` 비활성화해야 합니다.

<a id="use-nhn-cloud-service"></a>
## NHN Cloud Service 사용 { #use-nhn-cloud-service }

* [Log & Crash](./log-collector-ios) 사용 가이드
* [Push](./push-ios) 사용 가이드
* [OCR](./creditcard-recognizer-ios) 사용 가이드
