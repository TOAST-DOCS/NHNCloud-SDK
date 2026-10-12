<!-- machine_translated: true -->

<!-- pre-align:aligned sig=edc80b83f7a3 -->

<a id="nhn-cloud-sdk-user-guide-getting-started-ios"></a>
## NHN Cloud > SDK使用ガイド > 開始する > iOS { #nhn-cloud-sdk-user-guide-getting-started-ios }

<a id="supported-environment"></a>
## サポート環境 { #supported-environment }

* iOS 11.0以上
* Xcode最新バージョン

<a id="nhn-cloud-sdk-components"></a>
## NHN Cloud SDKの構成 { #nhn-cloud-sdk-components }

* iOS用NHN Cloud SDKの構成は次のとおりです。
    * [Logger](./log-collector-ios) SDK
    * [Push](./push-ios) SDK
    * [Credit-Card OCR](./creditcard-recognizer-ios) SDK
    * [ID-Card OCR](./idcard-recognizer-ios) SDK

* NHN Cloud SDKが提供するサービスの中から、希望する機能を選択して適用できます。

| Service | Cocoapods Pod Name | Carthage | Framework | Deployment Target | Dependency | Build Settings |
| --- | --- | --- | --- | --- | --- | --- |
| All | NHNCloudSDK | binary "[https://nh.nu/sdk](https://nh.nu/sdk) | NHNCloudCore.framework<br>NHNCloudCommon.framework<br>NHNCloudLogger.framework<br>NHNCloudPush.framework<br>NHNCloudOCR.framework |  |  |  |
| Mandatory | NHNCloudCore<br>NHNCloudCommon |  | NHNCloudCore.framework<br>NHNCloudCommon.framework | 11.0 |  | OTHER\_LDFLAGS = (<br>"-ObjC",<br>"-lc++"<br>); |
| Log & Crash | NHNCloudLogger |  | NHNCloudLogger.framework | 11.0 | [External & Optional]<br> CrashReporter.framework(NHNCloud) |  |
| Push | NHNCloudPush |  | NHNCloudPush.framework | 11.0 | UserNotifications.framework<br> PushKit.framework |  |
| OCR | NHNCloudOCR |  | NHNCloudOCR.framework | 11.0 | Vision.framework<br> AVFoundation.framework |  |

<a id="apply-nhn-cloud-sdk-to-xcode-projects"></a>
## NHN Cloud SDKをXcodeプロジェクトに適用 { #apply-nhn-cloud-sdk-to-xcode-projects }

<a id="apply-nhn-cloud-sdk-with-cococapods"></a>
### 1. Cococapodsを使用してNHN Cloud SDK適用 { #apply-nhn-cloud-sdk-with-cococapods }

* Podfileを作成してNHN Cloud SDKのPodを追加します。

```podspec
platform :ios, '11.0'
use_frameworks!

target '{YOUR PROJECT TARGET NAME}' do
    pod 'NHNCloudSDK'
end
```

<a id="apply-nhn-cloud-sdk-with-swift-package-manager"></a>
### 2. Swift Package Managerを使用してNHN Cloud SDK適用 { #apply-nhn-cloud-sdk-with-swift-package-manager }

* XCodeで**File > Add Packages...**メニューを選択します。
* Package URLに'https://github.com/nhn/nhncloud.ios.sdk'を入れて**Add Package**ボタンを選択します。
* 追加したいLibraryを選択します。

<a id="apply-nhn-cloud-sdk-with-carthage"></a>
### 3. Carthageを使用してNHN Cloud SDK適用 { #apply-nhn-cloud-sdk-with-carthage }

* Cartfileを作成してNHN Cloud SDKを追加します。

```sh
# Full URL
binary "https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_f9e3dc598ca142d3820e1c19343d5428/carthage/NHNCloudSDK.json" 

# Short URL
binary "https://nh.nu/sdk"
```

* 作成されたCarthage/BuildフォルダのFrameworkをXcodeプロジェクトに追加します。

* NHN Cloud SDKを使用するには[フレームワーク設定](./getting-started-ios/#frameworks-setup)と[プロジェクト設定](./getting-started-ios/#set-up-project)を行う必要があります。

!!! tip "ポイント"
    サービスのいずれかの機能を選択して使用するには、サービスごとに必要なFrameworkのみ選択してプロジェクトに追加する必要があります。
    サービスごとに必要なFrameworkは[NHN Cloud SDKの構成](./getting-started-ios/#nhn-cloud-sdk-components)で確認できます。

<a id="apply-nhn-cloud-sdk-by-downloading-binaries"></a>
### 4. バイナリをダウンロードしてNHN Cloud SDK適用 { #apply-nhn-cloud-sdk-by-downloading-binaries }

* NHN Cloudの[Downloads](../../Download/#nhn-cloud-sdk)ページから、iOS SDK全体をダウンロードできます。
* 必要なFrameworkを選択してプロジェクトに追加します。

<a id="frameworks-setup"></a>
### フレームワーク設定 { #frameworks-setup }

* LoggerのCrash Report機能を使用するには、SDKのExternalフォルダに同梱されているCrashReporter.xcframeworkをプロジェクトに追加する必要があります。
* Push機能を使用するには、プロジェクトにシステムフレームワークであるUserNotifications.frameworkを追加する必要があります。
* OCR機能を使用するには、プロジェクトにシステムフレームワークであるVision.frameworkとAVFoundation.frameworkを追加する必要があります。

<a id="set-up-project"></a>
### プロジェクト設定 { #set-up-project }

* Cocoapods以外の方法でプロジェクトにNHN Cloud SDKを統合した場合、以下の設定が追加で必要です。
* **Build Settings**の**Other Linker Flags**に**-lc++**と**-ObjC**を追加します。
    * **Project Target > Build Settings > Linking > Other Linker Flags**

![other_linker_flags](https://static.toastoven.net/toastcloud/sdk/ios/overview_settings_flags_202206.png)

<a id="import-framework"></a>
### フレームワークのインポート { #import-framework }

* 使用するフレームワークをインポートします(import)。

```objc
#import <NHNCloudCore/NHNCloudCore.h>
#import <NHNCloudLogger/NHNCloudLogger.h>
#import <NHNCloudPush/NHNCloudPush.h>
#import <NHNCloudOCR/NHNCloudOCR.h>
```

<a id="set-user-id"></a>
## UserID設定 { #set-user-id }

* NHN Cloud SDKにユーザーIDを設定できます。
* 設定したUserIDは、NHN Cloud SDKの各モジュールで共通使用されます。
* NHN Cloud SDK Loggerのログ送信APIを呼び出すたびに、設定したユーザーIDをログと一緒にサーバーに送信します。

<a id="specification-for-user-id-setting-api"></a>
### UserID API仕様 { #specification-for-user-id-setting-api }

```objc
+ (void)setUserID:(NSString *)userID;
```

<a id="usage-example-of-user-id-setting"></a>
### UserID設定使用例 { #usage-example-of-user-id-setting }

```objc
[NHNCloudSDK setUserID:@"NHNCloud-USER"];
```

<a id="set-debug-mode"></a>
## デバッグモード設定 { #set-debug-mode }

* NHN Cloud SDKの内部ログを確認するために、デバッグモードを設定できます。
* NHN Cloud SDKに関するお問い合わせの際は、デバッグモードを有効にしていただくと、迅速にサポートできます。

<a id="specification-for-debug-mode-api"></a>
### デバッグモード設定API仕様 { #specification-for-debug-mode-api }


```objc
+ (void)setDebugMode:(BOOL)debugMode;
```

<a id="usage-example-of-debug-mode-setting"></a>
### デバッグモード設定使用例 { #usage-example-of-debug-mode-setting }

```objc
[NHNCloudSDK setDebugMode:YES];    // or NO
```

> [注意]アプリをリリースする場合、デバッグモードを無効化する必要があります。

<a id="use-nhn-cloud-service"></a>
## NHN Cloud SDK Service使用 { #use-nhn-cloud-service }

* [Log & Crash](./log-collector-ios)使用ガイド
* [Push](./push-ios)使用ガイド
* [Credit-Card OCR](./creditcard-recognizer-ios) 使用ガイド
* [ID-Card OCR](./idcard-recognizer-ios) 使用ガイド
