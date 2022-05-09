---
title: Android Pentest Setup Environment
layout: post
categories: [Android]
tags: [Setup]
toc: true
published: true
---
# Android pentesting Setup Environment

### I creat small bash script to install and setup environment in android emulator 

#### tools setup with script
1. Adb
2. jadx
3. apktool
4. apkleads
5. fireBase Scanner
6. drozer
7. frida
8. burp
9. nucli

#### Language install  will script 
1. python3 python2
2. pip3 pip2
3. go
4. java


## Requirement to Run Script 
### 1- Install burp suite
Now you would need to set up a Burp CA’s certificate into the emulated 
Navigate to <br/> Burp -> Proxy -> Options -> Export CA certificate -> Certificate in DER format.
Certificate DER will be input to Script <br/>
<br/>
3- Install Genymotion <br/>
![](https://i.imgur.com/dh90oev.png) <br/>
![](https://i.imgur.com/nnkFwbL.png) <br/>
![](https://i.imgur.com/zwjQswc.png) <br/>

## Usage Script
![](https://i.imgur.com/PoLRDwo.png)



## After Run Script 

### 1- Burp 
The certificate should now be installed as a system trusted CA certificate <br/> which you can confirm by navigating the emulated device in <br/> **Settings -> Security & Location -> Encryption & Credentials -> Trusted Credentials** <br/>
![](https://i.imgur.com/eyBOLsX.png) <br/>
**The last thing to do is on the emulated device you should also set up the WiFi** 
![](https://i.imgur.com/EszDRUi.png)

### 2- Drozer 
allows you to search for security vulnerabilities in apps and devices by assuming the role of an app and interacting with the Dalvik VM, other apps' IPC endpoints and the underlying OS.<br/>

Drozer Agent will be installed in Genymotion emulator
**settings. Navigate to WiFi -> Long press WiFi name -> Modify Network -> Advanced Options -> Change proxy None to Manual.**
#### Run Drozer without open agent
```
adb forward tcp:31415 tcp:31415 
adb shell am startservice -n com.mwr.dz/.services.ServerService -c com.mwr.dz.START_EMBEDDED   
drozer
```
### 3- Frida<br/>
 This is a dynamic code instrumentation toolkit which lets you dynamically inject snippets of code into running processes of the app in order to change its behavior.
 
when Script finish will find frida server in /data/local/tmp <br/>
![](https://i.imgur.com/2aNdszM.png) <br/>

run frida
```
adb shell "/data/local/tmp/frida-server &"
frida-ls-devices
frida-ps -U
```
