# Android Pentent Series

| Content                                                     |
| ----------------------------------------------------------- |
|  What is **APK** ?                                       |
| **Dalvik** & **Smali**                   |
|What is **Android components**?                                    |
|  tools need to setup                                 |
|  Resourse for **Android**                                      |
|  **Labs**                                                 |
| **Referance**                                            |


## What is **APK** ?
Android applicatins are in the APK file formate.
APK is basically ZIP file. (You can rename the file extension to .zip to open and see its contents.)
#### What is apk components ?
![](https://i.imgur.com/Df9M19d.png)

1.  **AndroidManifest.xml** <br/>
This file contains the meta information about the app such as name of the app, package name, different activities and services, permissions required, supported version of Android etc.

2. **Classes.dex** <br/>
This is the actual code of the app. “dex” is the short form of Dalvik Executable. The source code will be in the extension “.java or .kt”. When it is compiled it will become “.class”. But in android all these class files are further optimized and packed into dex file for running easily in the android run time.
3. **lib/** <br/>
Native libraries for the application, Under the lib/ directory, there are the cpu-specific directories. Ex: armeabi, mips
is used for storing libraries and precompiled code and savelinux shared object (.so) files.The .so files are libraries created by the developer or from  third-party If an attacker found a way to modify or replace these file and get them to execute this could result in arbitrary code execution
4. **assets/** <br/>
Any other files that may be needed by the app.
Additional native libraries or DEX files may be included here. This can happen especially when malware authors want to try and “hide” additional code, native or Dalvik, by not including it in the default locations.
5. **META-INF/**<br/>
contains files related to the integrity and authenticity of the app
**This folder contains 3 files** <br/>
1.MANIFEST.MF<br/>
2.CERT.SF <br/>
3.CERT.RSA <br/>
6. **res/** <br/>

![](https://i.imgur.com/AkO2dQo.png)
<br/>
res is where the resources of app which is not compiled to resources.arsc is stored. As you can see there are many sub folders inside it. Each folder contains different type of resources. 
For example values folder have file   strings.xml  which have all const for app may be have api key for example  or aws Cognito <br/>
## Dalvik & Smali ?
Most android applications are written in java , kotlin is also supported and interoprable with java <br/>

Instead of the Java code being run in Java Virtual Machine (JVM) like desktop applications, in Android, the Java is compiled to the Dalvik Executable (DEX) bytecode format. <br/>
For earlier versions of Android, the bytecode was translated by the Dalvik virtual machine. For more recent versions of Android, the Android Runtime (ART) is used. <br/>
If developers, write in Java and the code is compiled to DEX bytecode <br/>
![](https://i.imgur.com/JPJsb8q.png)
<br/> to reverse engineer, do the opposite direction <br/>
![](https://i.imgur.com/dHK1fYY.png)

Smali is the human readable version of Dalvik bytecode. Technically, Smali and baksmali are the name of the tools (assembler and disassembler, respectively), but in Android, we often use the term “Smali” to refer to instructions. <br/>
 SMALI is like the assembly language: between the higher level source code and the bytecode. <br/>


##  What is **Android components** ?

1. **Activities :** <br/>
An activity is the entry point for interacting with the user.
in-short Activity performs actions on the screen. <br/>
**Fragments :** Represents a portion of user interface in an Activity.
2. **Services :** <br/>
A service is a component that runs in the background to perform long-running operations. For example, a service might play music in the background while the user is in a different application
3. **Broadcast receivers :** <br/>
They handle communication between Android OS and applications.

4. **Content provicers :** <br/>
content provider component supplies data from one application to others on request.
The data may be stored in the file system, the database or somewhere else entirely.

## Tools need to setup 

1. **Apktool :** <br/>
 can use **apktool** to decode the apk and make change in smali code and then return it to apk and then signing it . <br/>
![apktool](https://i.imgur.com/Yah96RP.png)  <br/>
2. **keytool & apksigner** <br/>
3. **Android studio** <br/>
4. **emulator** <br/>
5. **apk studio** <br/>
6. **jadx-gui** <br/>
7. **drozer** <br/>
8. **frida** <br/>


## **Resourse for Android :** 
[**English playlist for basic Android**](https://www.youtube.com/playlist?list=PLa2a0gT4SdEeCoYDX-5SkmL81U7atDZVd)
## **Labs :** 

1. [**InjuredAndroid**](https://github.com/B3nac/InjuredAndroid) will be better if sovle lab first and then see how he solve it [**Solve**](https://docs.google.com/presentation/d/1gK2vYdvwFn8r8dSawIWRRIF4yDF4qmMY2qEelS1M7rI/edit#slide=id.p)
2. [**Insecureshop**](https://github.com/optiv/Insecureshop)
3. [**InsecureBankv2**](https://github.com/dineshshetty/Android-InsecureBankv2)
4. [**ovaa**](https://github.com/oversecured/ovaa) 

will be better if you solve labs in this order.


## **Referance :** 
1. [**Oversecured**](https://blog.oversecured.com/)
2. [**Android Notes**](https://techvomit.net/android-security-notes/)
3. [**awesome Android security**](https://github.com/saeidshirazi/awesome-android-security)
4. [**Android Reverse**](https://www.ragingrock.com/AndroidAppRE/app_fundamentals.html)
5. [**Reports**](https://github.com/B3nac/Android-Reports-and-Resources)
