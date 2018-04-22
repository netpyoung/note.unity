http://support.hockeyapp.net/kb/client-integration-android-other-platforms/hockeyapp-for-android-sdk


## 다운로드 라이브러리.

* 다운로드 : http://download.hockeyapp.net/sdk/android/HockeySDK-Android-3.0.2.zip
* unzip
* `libs/HockeySDK.jar`를 안드로이드 프로젝트 `libs`폴더에 복사
* ADT 16이하라면, `.jar`파일을 classpath에 추가시켜준다. ADT 17이상이라면 자동대로 추가됨.


## 코드 수정.

* `AndroidManifest.xml`을 연다
* 다음 라인을, 어플리케이션의 child elemnt로 추가해준다.

	<activity android:name="net.hockeyapp.android.UpdateActivity" />


* 베타배포와 크래쉬리포팅을 원한다면, 다음 라인을 추가해준다.

	<uses-permission android:name="android.permission.INTERNET" />
	<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
	
* (구글 플레이와 같이) 크래쉬리포팅만을 원할시, 다음 라인만 추가해준다.	

	<uses-permission android:name="android.permission.INTERNET" />
	
	
* main activity를 열어 다음 라인을 추가한다.

```java
import net.hockeyapp.android.CrashManager;
import net.hockeyapp.android.UpdateManager;

public class YourActivity extends Activity {
 @Override
 protected void onCreate(Bundle savedInstanceState) {
   // Your own code to create the view
   // ...

   checkForUpdates();
 }

 @Override
 protected void onResume() {
   super.onResume();
   checkForCrashes();
 }

 private void checkForCrashes() {
   CrashManager.register(this, APP_ID);
 }

 private void checkForUpdates() {
   // Remove this for store / production builds!
   UpdateManager.register(this, APP_ID);
 }

 // Probably more methods
}
```



* APP_ID를 어플리케이션의 identifier로 교채한다.
 - identifier는 기존 `.apk`를 업로드하거나, HockeyApp을 새로이 만들면 생성된다.
 - APP_ID는 어플리케이션의 페이지 App Info 섹션에서 찾을 수 있다.

 
 
 
 
 
# In-App Feedback 변경.

* `AndroidManifest.xml`을 열어 다음 라인을 추가한다.

	<activity android:name="net.hockeyapp.android.FeedbackActivity" />
	

* 권한을 추가해준다.

	<uses-permission android:name="android.permission.INTERNET" />


* 피드백 뷰를 원하는 곳에 다음과 같은 함수를 추가해준다.

```java
public void showFeedbackActivity() {
  FeedbackManager.register(this, HOCKEYAPP_ID, null);
  FeedbackManager.showFeedbackActivity(this);
}
```

* `onClick`, `onMenuItemSelected`, `onOptionsItemSelected`와 같은 리스너 메소드에 `showFeedbackActivity`를 호출하도록 한다.



# 사용시간 변경.

어플리케이션의 구동시간을 추적하고자 한다면, 다음과 같이 호출해주는 부분이 필요하다.


```java
@Override
protected void onResume() {
  super.onResume();
  Tracking.startUsage(this);
  // Further statements
  // ...
}

@Override
protected void onPause() {
  // Further statements
  // ...
  Tracking.stopUsage(this);                 
  super.onPause();
}
```
 
 API 14이상이 minimum으로 설정되었다면, `ActivityLifecycleCallbacks`를 이용하여, `registerActivityLifecycleCallbacks`에 등록할 수 있다.
 
 
 
# HockeyApp의 크래쉬가 검사항목에서 나타나지 않을시
1. APP_ID가 HokckeyApp의 App ID와 동일한지 확인.
2. `AndroidManifest.xml`에 있는 package 이름과 HockeyApp에 있는 어플리케이션의 package 이름과 동일한지 확인.
3. 크래쉬시, 다이얼로그가 안뜨면, `CrashManager.java`의 `register`메소드에 break포인트를 걸어, 다이얼로그가 왜 안뜨는지 확인.
4. 그래도 안되면 문의넣으셈.