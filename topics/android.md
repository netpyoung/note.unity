in app billing
cloud message

# local notification

ios = UILocalNotification
https://developer.android.com/reference/android/app/AlarmManager.html


## notification

nm = getSystemService(NOTIFICATION_SERVICE)
PendingIntent intent
Notification notification
notification.setLatestEventInfo
nm.notifiy(1234, notification)

## alarm
AlarmManager am
am.set()




# component


## activity


## broadcast receiver
sendBoradcast(new Intent("com.hello.world.message"));

<receiver android:name=".TestReceiver">
    <intent-filter>
        <action android:name="com.hello.world.message" />
    </intent-filter>
</receiver>  

public class TestReceiver extends BroadcastReceiver {
    @override
    public void onReceive(Context context, Intent intent) {
        String name = intent.getAction();
    }
}


~~~
    FLAG_INCLUDE_STOPPED_PACKAGES
    FLAG_EXCLUDE_STOPPED_PACKAGES
~~~

## content provider

<provider android:name=".provider.DataProvider"
        android:authorities="com.hello.world.contentproviderdataa">
</provider>
content://AUTHORITY
## service
* background

### startService() 

intent = new Intent("com.hello.world.startService")
startService(intent)
stopService(intent)

<service android:name=".TestService">
    <intent-filter>
        <action android:name="com.hello.world.startService" />
    </intent-filter>
</service>

onCreate() -> onStartCommand() ***

### bindService()

