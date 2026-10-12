<!-- machine_translated: true -->

<!-- pre-align:aligned sig=c4d6d5f779f7 -->

<a id="nhn-cloud-sdk-user-guide-overview"></a>
## NHN Cloud > SDK使用ガイド > 概要 { #nhn-cloud-sdk-user-guide-overview }
 
NHN Cloud SDKは、[NHN Cloud](https://nhncloud.com/)の多様なサービスライブラリ(SDK)を簡単に適用できるようにした統合ライブラリ(SDK)です。 NHN Cloudサービスを使用してアプリケーションを開発する時、個別サービスのライブラリをそれぞれ適用する煩わしさがなく、一度に適用できます。 
複数のサービスの統合開発環境を提供しますが、希望する機能だけを選択できるため、使用スペースを節約できます。NHN Cloud SDKは、使用するプログラミング言語とプラットフォームに最適化されたライブラリで、慣れた開発環境を提供します。 
 
> 現在はiOS、Android、Windows C++の開発環境のみ提供します。今後さらに多様なプログラミング言語とプラットフォームをサポートする予定です。 
 
<a id="supported-services"></a>
## サポートするサービス { #supported-services }
 
NHN Cloud SDKは、次のようなサービスを提供します。 
 
- [Log & Crash Search](https://www.nhncloud.com/service/data-analytics/log-crash-search)
- [Push](https://www.nhncloud.com/service/notification/push)
- [OCR](https://www.nhncloud.com/service/ai-service/ocr)
 
> 個別SDKを提供するサービスは、今後NHN Cloud SDKを通して開発できるようにサポートする予定です。 
 
<a id="features"></a>
## 特徴 { #features }
 
- AndroidはGradle、iOSはCocoaPodsを活用したビルド環境をサポートします。 
- 使用するには、サービス全体または一部サービスを選択して適用できます。 
- 個別サービスで独自に提供していたSDKの不便な点を改善しました。 
 
<a id="getting-started-with-nhn-cloud-sdk"></a>
## NHN Cloud SDKを開始する { #getting-started-with-nhn-cloud-sdk }
 
<a id="android"></a>
### Android { #android }
 
NHN Cloud Android SDKは、**mavenCentral**で配布され、簡単なGradle設定だけで使用できます。 
 
- [Androidで開始する](./getting-started-android) 
 
<a id="ios"></a>
### iOS { #ios }
 
NHN Cloud iOS SDKは、**Github**で配布され、簡単な**CocoaPods**, **Carthage**, **Swift Package Manager**設定だけで使用できます。 
 
 
- [iOSで開始する](./getting-started-ios) 
 
<a id="windows-c"></a>
### Windows C++ { #windows-c }
 
NHN Cloud Windows C++ SDKは、Windows 7、10(32/64bit)、11(64bit)環境をサポートします。 
 
- [Windows C++で開始する](./getting-started-windows) 
 
<a id="log-crash"></a>
## Log & Crash { #log-crash }
 
Log & Crash Search収集サーバーにログを送信する機能を提供します。収集されたログは、NHN Cloudコンソールの**Log & Crash Search**メニューをクリックして確認できます。 
 
- [Log & Crash Searchサービス確認](https://nhncloud.com/service/data-analytics/log-crash-search) 
 
<a id="main-features"></a>
### 主な機能 { #main-features }
 
| 機能   | 説明                                    | 
| ------- | ---------------------------------------- | 
| ログ送信 | ログを収集サーバーに送信します。                        | 
| 照会および検索 | NHN Cloudコンソールでログを照会したり、条件に合ったログを検索できます。 | 
| クラッシュレポート | 予期せぬクラッシュが発生した場合、Log & Crash Search収集サーバーにクラッシュログを送信します。 | 
 
<a id="user-guides"></a>
### 使用ガイド { #user-guides }
 
- [Log & Crash > Android](./log-collector-android)使用ガイド 
- [Log & Crash > iOS](./log-collector-ios)使用ガイド 
- [Log & Crash > Windows C++](./log-collector-windows)使用ガイド 

<a id="nhn-cloud-push"></a>
## NHN Cloud Push { #nhn-cloud-push }
 
NHN Cloud Push SDKを使用して、Pushサービスを簡単に適用できます。 
コンソールから通知メッセージを安定的に送信し、送信結果を確認できます。 
 
<a id="nhn-cloud-push-user-guides"></a>
### 使用ガイド { #nhn-cloud-push-user-guides }
 
- [Push > Android](./push-android)使用ガイド 
- [Push > iOS](./push-ios)使用ガイド 

<a id="nhn-cloud-ocr"></a>
## NHN Cloud OCR { #nhn-cloud-ocr }

NHN Cloud OCR SDKを使用して、OCRサービスを簡単に適用できます。
クレジットカードと身分証を認識し、データを抽出できます。

<a id="nhn-cloud-ocr-user-guides"></a>
### 使用ガイド { #nhn-cloud-ocr-user-guides }

- [OCR(Credit Card)> Android](./creditcard-recognizer-android)
- [OCR(Credit Card)> iOS](./creditcard-recognizer-ios)

- [OCR(ID Card)> Android](./idcard-recognizer-android)
- [OCR (ID Card)> iOS](./idcard-recognizer-ios)
