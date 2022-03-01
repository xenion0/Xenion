---
title: Android Pentent Series P1
layout: post
categories: [Android]
tags: []
toc: true
published: true
---
# Android Pentent Series P1

| Content                              |
| ------------------------------------ |
| What is **APK** ?                    |
| What is **Apk components**           |
| What is **Android components**?      |
| tools need to setup                  |
| **Reverse APK**                      |
| Resourse for **Android Programming** |
| **Labs**                             |
| **Referance**                        |


## What is **APK** ?
APK stands for Android Package (sometimes Android Package Kit or Android Application Package). It's the file format that Android uses to distribute and install apps. As a result, APKs contain all the elements that an app needs to install correctly on your device.

APK is basically ZIP file. (You can rename the file extension to .zip to open and see its contents.)

![](https://i.imgur.com/dTqgxKC.png)

![](https://i.imgur.com/o3WUwTG.png)

but in this way files will be unreadable 
![](https://i.imgur.com/UuusyXc.png)
so that in later part will show the write way to see in readable form

## What is apk components ?
![](https://i.imgur.com/Df9M19d.png)

###  **AndroidManifest.xml** <br/>
The manifest file describes the app structure, its components (activities, services, content providers, and intent receivers), and requested permissions. It also contains general app metadata, such as the app's icon, version number, and theme. 

Here is an example of a manifest file, including the package name (the convention is a reversed URL, but any string is acceptable). It also lists the app version, relevant SDKs, required permissions, exposed content providers, broadcast receivers used with intent filters and a description of the app and its activities:

```
<manifest
    package="com.owasp.myapplication"
    android:versionCode="0.1" >

    <uses-sdk android:minSdkVersion="12"
        android:targetSdkVersion="22"
        android:maxSdkVersion="25" />

    <uses-permission android:name="android.permission.INTERNET" />

    <provider
        android:name="com.owasp.myapplication.MyProvider"
        android:exported="false" />

    <receiver android:name=".MyReceiver" >
        <intent-filter>
            <action android:name="com.owasp.myapplication.myaction" />
        </intent-filter>
    </receiver>

    <application
        android:icon="@drawable/ic_launcher"
        android:label="@string/app_name"
        android:theme="@style/Theme.Material.Light" >
        <activity
            android:name="com.owasp.myapplication.MainActivity" >
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
            </intent-filter>
        </activity>
    </application>
</manifest>
```

### **Classes.dex** <br/>
This is the actual code of the app. “dex” is the short form of Dalvik Executable. The source code will be in the extension “.java or .kt”. When it is compiled it will become “.class”. But in android all these class files are further optimized and packed into dex file for running easily in the android run time.
### **lib/** <br/>
Native libraries for the application, Under the lib/ directory, there are the cpu-specific directories. Ex: armeabi, mips
is used for storing libraries and precompiled code and savelinux shared object (.so) files.The .so files are libraries created by the developer or from  third-party If an attacker found a way to modify or replace these file and get them to execute this could result in arbitrary code execution
### **assets/** <br/>
Any other files that may be needed by the app.
Additional native libraries or DEX files may be included here. This can happen especially when malware authors want to try and “hide” additional code, native or Dalvik, by not including it in the default locations.
### **META-INF/**<br/>
contains files related to the integrity and authenticity of the app
**This folder contains 3 files**

MANIFEST.MF
: It contains various information used by the java run-time environment when loading the jar file, such as which is the main class to be run from the jar file, version of package, build number, creator of the package, security policies/permissions of java applets and java webstart packages, the list of file names in the jar along with their SHA1 digests, etc.

CERT.SF
: This contains the list of all files along with their SHA-1 digest.

CERT.RSA
: This contains the signed contents of the CERT.SF file along with the certificate chain of the public key used for signing the contents

### **res/** 

![](https://i.imgur.com/AkO2dQo.png)

res is where the resources of app which is not compiled to resources.arsc is stored. As you can see there are many sub folders inside it. Each folder contains different type of resources. 
For example values folder have file   strings.xml  which have all const for app may be have api key for example  or aws Cognito <br/>
##  What is **Android components** ?

### **Activities :** <br/>
An activity is the entry point for interacting with the user.
in-short Activity performs actions on the screen. <br/>
Each activity needs to be declared in the Android Manifest with the following syntax:
```
<activity android:name="ActivityName">
</activity>
```

**Fragments :** represents a behavior or a portion of the user interface within the activity.
Fragments don't need to be declared in manifest files because they depend on activities.

Example in Java:
```
public class MyFragment extends Fragment {
    ...
}
```

### **Services :** <br/>
A service is a component that runs in the background to perform long-running operations. For example, a service might play music in the background while the user is in a different application
```
<service android:name=".ExampleService" />
```
### **Broadcast receivers :** <br/>
They handle communication between Android OS and applications.


### **Content provicers :** <br/>
content provider component supplies data from one application to others on request.
The data may be stored in the file system, the database or somewhere else entirely.

every component will be in anothe part in future so here just intro .

## Tools need to setup 

1. **Apktool :** <br/>
 can use **apktool** to decode the apk and make change in smali code and then return it to apk and then signing it . <br/>
![apktool](https://i.imgur.com/Yah96RP.png)  <br/>
2. **keytool & apksigner** <br/>
3. **Android studio** <br/>
4. **emulator** <br/>
5. **apk studio** <br/>
6. **jadx-gui** <br/>
7. **drozer** [learn drozer from here](https://book.hacktricks.xyz/mobile-apps-pentesting/android-app-pentesting/drozer-tutorial)
8. **frida**  [learn frida](https://www.youtube.com/watch?v=iMNs8YAy6pk&ab_channel=sambal0x)

You can install tools in windows and add it in path of env that will make use of tools more easy from cmd.
![](https://i.imgur.com/rXe90W8.png)


## Reverse APK 
This is just a quick intro about Reverse APK 

Reverse Apk
: application reverse engineering is used to find bugs like Tampring code or source cod can be reviewed bu using Reverse engineering

Decompiling the APK 
: APKs are zip file archives that store the android app. They are no longer the java source code files, so decompiling them only gives you the “compiled” byte code.

The tool apktool supports decompiling:
`  apktool file.apk `
Use -r to avoid decompiling the resources (e.g., images, etc.). This is useful if you want to later re-compile it because you made changes, etc.

or can use tool like jadx-gui will be more easy or mobsf

[Reverse Engineering Android Applications](https://www.youtube.com/watch?v=m9UZnWLLurY)

### Source code obfuscation 
Android Runtime (ART) executes .dex files, which are part of the APK package. Dalvik bytecod (.dex) can be translated to equivalent Java bytecode. Conversion is not perfect and cannot be reversed, but Java code can be easily read and analyzed. Understanding the code, specifically implemented security mechanisms gives the attacker great advantage and  significantly increases the chance of exploiting the application. 

To mitigate that risk, developers can obfuscate the source code. Obfuscation is a process of making a code difficult to understand by humans, but without changing its semantics and functionality. The most typical techniques used by obfuscators are changing methods/parameters names, modifying the flow of the code and encrypting string and assets. 

Most popular obfuscators for Android code are ProGuard and DexGuard. The first one is available for free, but offers less protection against reverse engineering. 

![](https://i.imgur.com/xxi6i7r.png)

### Code Signing 

Apks have to be signed by the developer.But you can be your own developer. 
But you still have to sign them. So after you have decompile the apk, you can recompile it as follows: 
`apktool b <path-to-decompiled>  -o unsigned.apk `

A signing program is available from the following git repository:
https://github.com/glitterballs/release-tools.git 
Go to its SignApk directory and run the following: 
java -jar signapk.jar certificate.pem key.pk8 unsigned.apk signed.apk 
You can create your own certificate and key to do the signing if you want. 

Once you download app from the play store that is secure download and then you can reverse apk and tampring code and then build apk again and sign it to install app in device 

It use to sign apk this app Easy way  https://m.apkpure.com/ar/apk-signer/com.haibison.apksigner 

Or you can do that with manual way with keytool & jarsigner

### Dalvik & Smali ?
Most android applications are written in java , kotlin is also supported and interoprable with java <br/>

Instead of the Java code being run in Java Virtual Machine (JVM) like desktop applications, in Android, the Java is compiled to the Dalvik Executable (DEX) bytecode format. <br/>
For earlier versions of Android, the bytecode was translated by the Dalvik virtual machine. For more recent versions of Android, the Android Runtime (ART) is used. <br/>
If developers, write in Java and the code is compiled to DEX bytecode <br/>
![](https://i.imgur.com/JPJsb8q.png)
<br/> to reverse engineer, do the opposite direction <br/>
![](https://i.imgur.com/dHK1fYY.png)

Smali is the human readable version of Dalvik bytecode. Technically, Smali and baksmali are the name of the tools (assembler and disassembler, respectively), but in Android, we often use the term “Smali” to refer to instructions. <br/>
 SMALI is like the assembly language: between the higher level source code and the bytecode. <br/>






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
6. [**MSTG OWASP TOP 10 MOB**](https://mobile-security.gitbook.io/mobile-security-testing-guide/overview/0x03-overview)
