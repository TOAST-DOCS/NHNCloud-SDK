<!-- machine_translated: true -->

<!-- pre-align:aligned sig=610da5e47de1 -->

<a id="nhn-cloud-sdk-user-guide-release-notes-windows-c"></a>
## NHN Cloud > SDK User Guide > Release Notes > Windows C++ { #nhn-cloud-sdk-user-guide-release-notes-windows-c }

<a id="110-september-15-2026"></a>
## 2.1.1.0 (September 15, 2026) { #110-september-15-2026 }

Download : [nhncloud-sdk-windows-2.1.1.0.zip](https://static.toastoven.net/toastcloud/sdk_download/toast/windows/2.1.1/nhncloud-sdk-windows-2.1.1.0.zip)
* Applied Log & Crash Search API domain changes
    * Changed the log collection API domain from api-logncrash.cloud.toast.com to api-logncrash.nhncloudservice.com.
    * Changed the settings API domain from setting-logncrash.cloud.toast.com to api-setting-logncrash.nhncloudservice.com.

<a id="002-20240123"></a>
## 2.0.0.2 (January 23, 2024) { #002-20240123 }

Download : [nhncloud-sdk-windows-2.0.0.2.zip](https://static.toastoven.net/toastcloud/sdk_download/toast/windows/2.0.0/nhncloud-sdk-windows-2.0.0.2.zip)
* Improved duplicate logs filtering
* Fixed handdle leak issues when executing CrashReporter
* Improved stability


<a id="001-20220712"></a>
## 2.0.0.1 (July 12, 2022) { #001-20220712 }

Download : [nhncloud-sdk-windows-2.0.0.1.zip](https://static.toastoven.net/toastcloud/sdk_download/toast/windows/2.0.0/nhncloud-sdk-windows-2.0.0.1.zip)
* Changed the module name to NHNCloudLogger
	* ToastLogger has been deprecated.
* Fixed issues of memory leak when sending logs
* Fixed an issue where User ID is reflected differently according to MBCS or Unicode functions
* Fixed an issue where setting Log Types Filter is not applied when sending crash logs

<a id="005-20210331"></a>
## 1.0.0.5 (March 31, 2021) { #005-20210331 }

Download : [toast-sdk-windows-1.0.0.5.zip](https://static.toastoven.net/toastcloud/sdk_download/toast/windows/1.0.0/toast-sdk-windows-1.0.0.5.zip)
* Bug fixes
* Changed some API interfaces
* Added a feature to validate input values when using custom fields
* Fixed issues of intermittent Base64 decoding failure
* Fixed issues of intermittent failure when sending crash dumps to external processes
* Changed the structure of distributed binary
	* Sample project included

<a id="943-20191010"></a>
## 0.9.4.3 (October 10, 2019) { #943-20191010 }

Download : [toast-sdk-windows-0.9.4.3.zip](https://static.toastoven.net/toastcloud/sdk_download/toast/windows/0.9.4/toast-sdk-windows-0.9.4.3.zip)


<a id="toast-log-crash"></a>
### TOAST Log & Crash { #toast-log-crash }

<a id="toast-log-crash-bug-fixes"></a>
#### Bug Fixes

* Fixed an issue where no crash log remains for pure virtual call / invalid parameter on x86

<a id="930-20190723"></a>
## 0.9.3.0 (July 23, 2019) { #930-20190723 }

Download : [toast-sdk-windows-0.9.3.0.zip](https://static.toastoven.net/toastcloud/sdk_download/toast/windows/0.9.3/toast-sdk-windows-0.9.3.0.zip)

<a id="930-20190723-toast-log-crash"></a>
### TOAST Log & Crash { #930-20190723-toast-log-crash }

<a id="930-20190723-toast-log-crash-added-features"></a>
#### Added Features

* Initialize() function success/failure handling
	* Changed the return value to bool
* Added SessionId to general log
* When setting information cannot be retrieved, process with the previously saved setting information.
* Provides a static library
	* Visual studio 2015 (vc14) version provided
* Provides xp version

<a id="9012-20180904"></a>
## 0.9.0.12 (September 4, 2018) { #9012-20180904 }

Download : [toast-sdk-windows-0.9.0.12.zip](https://static.toastoven.net/toastcloud/sdk_download/toast/windows/0.9.0/toast-sdk-windows-0.9.0.12.zip)

<a id="9012-20180904-toast-log-crash"></a>
### TOAST Log & Crash { #9012-20180904-toast-log-crash }

<a id="9012-20180904-toast-log-crash-added"></a>
#### Added

* New Functions

