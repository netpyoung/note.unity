http://support.hockeyapp.net/kb/client-integration-ios-mac-os-x/hockeyapp-for-ios



HockeyApp for iOS


hockeyapp SDK는 iOS 6.0 이상 디바이스에서만 돌아감.


## 다운로드.

1. http://www.hockeyapp.net/releases/ - wtf Site temporarily disabled
2. unzip 하면, `HockeySDK-iOS` 폴더가 생길것임.
3. xcode project 폴더에, `Vendor`라는 서브디렉토리에 넣으셈.



## Xcode 설정.

1. `HockeySDK.embeddedframework`를 Xcode project 로 드래그&드랍한다.
2. `Vendor`도 마찬가지.
3. `Create groups for any added folders`를 선택, `Finish`를 선택.
![aaa](http://support.hockeyapp.net/help/assets/3deca95261817c709be3c9bd9e1a86d26884208c/XcodeCreateGroups_normal_normal.png)

4. `Project Navigator`에 있는 project 선택. (meta+1)
5. app target 선택.
6. `Build Phases`탭 선택.
7. `Link Binary With Libraries` 확장시키기.
8. 다음 프레임워크중, 빠진것 채워넣기.

	AssetsLibrary
	CoreText
	CoreGraphics
	Foundation
	MobileCoreServices
	QuartzCore
	QuickLook
	Security
	SystemConfiguration
	UIKit
	

## 코드 수정.
1. `AppDelegate.m`파일 수정
2. 기존에 있는 `#import` 구문 다음에, 다음 문장 추가

	#import <HockeySDK/HockeySDK.h>


3. `application:didFinishLaunchingWithOptions:` 메소드 검색.
4. 다음 문장 추가.

	[[BITHockeyManager sharedHockeyManager] configureWithIdentifier:@"APP_ID"];
	[[BITHockeyManager sharedHockeyManager] startManager];
	[[BITHockeyManager sharedHockeyManager].authenticator authenticateInstallation];

* APP_ID는, HockeyApp에 설정된 것으로 등록.