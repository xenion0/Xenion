# Android Activity Security


| Content                                                     |
| ----------------------------------------------------------- |
|  What is **Activity** ?                                       |
| **Knowledge points**                   |
|What is **Android components**?                                    |
|  tools need to setup                                 |
|  Resourse for **Android**                                      |
|  **Labs**                                                 |
| 📕 **Referance**                                            |


## 📚 What is **Activity** ?
Each Android Application is composed of basic Android components such as Activity, Service, content Provider, and Broadcast Receiver. Among them, Activity is the main body of the application. It undertakes a lot of display and interaction work, and can even be understood as an "interface" "It's just an Activity. </br>

Activity is a visual user interface displayed for user actions. For example, an activity can display a list of menu items for the user to choose from, or display some photos with descriptions. An SMS application can include an activity that displays a list of contacts to send to, an activity that writes a text message to a selected contact, and an activity that scrolls through previous text messages and changes settings. Although together they form a cohesive user interface, each activity remains independent of the others. Each is implemented as a subclass of the base class Activity class.

An application can have only one activity, or, like the SMS application just mentioned, contain many. The role of each activity, and its number, naturally depends on the application and its design. In general, there is always an application that is marked as the first one the user sees when the application starts. The way to move from one activity to another is to start the next one with the current activity.

##  **Knowledge points** ?

Reference: http://developer.android.com/guide/components/activities.html

**The life cycle**

![](https://i.imgur.com/4Ilj5v9.png)

**Start method**
show start
Register components in the configruation file Android Manifest.xml
```
<activity android:name=".ExampleActivity" android:icon="@drawable/app_icon">
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity>
```

Directly use the intent object to specify application and activity startup

```
Intent intent = new Intent(this, ExampleActivity.class);
startActivity(intent);
```

implicit start

```
Intent intent = new Intent(Intent.ACTION_SEND);
intent.putExtra(Intent.EXTRA_EMAIL, recipientArray);
startActivity(intent);
```
**launch mode**

Activity has four loading modes:

standard : Default behavior. Every time an activity is started, the system creates a new instance in the target task.</br>
singleTop : If an instance of the target activity already exists on the top of the stack of the target task, the system will use the instance directly and call the activity's onNewIntent() (it will not be recreated)</br>
singleTask : Creates an instance of the activity on top of a new task's stack. If the instance already exists, the system will use the instance directly and call the activity's onNewIntent() (it will not be recreated)</br>
singleInstance : Similar to "singleTask", but no other activities will run in the target activity's task, and there will always be only one activity in that task.</br>
The location of the setting is in the android:launchMode attribute of the activity element in the AndroidManifest.xml file:
```
<activity android:name="ActB" android:launchMode="singleTask"></activity>
```
