---
title: Android part 2 | Android
layout: post
categories: [Android,Activity]
tags: []
toc: false
published: true
---

# Android Activity Security


| Content                                                     |
| ----------------------------------------------------------- |
|  What is **Activity** ?                                       |
| **Dalvik** & **Smali**                   |
|What is **Android components**?                                    |
|  tools need to setup                                 |
|  Resourse for **Android**                                      |
|  **Labs**                                                 |
| 📕 **Referance**                                            |


## 📚 What is **APK** ?
Each Android Application is composed of basic Android components such as Activity, Service, content Provider, and Broadcast Receiver. Among them, Activity is the main body of the application. It undertakes a lot of display and interaction work, and can even be understood as an "interface" "It's just an Activity.</br>

Activity is a visual user interface displayed for user actions. For example, an activity can display a list of menu items for the user to choose from, or display some photos with descriptions. An SMS application can include an activity that displays a list of contacts to send to, an activity that writes a text message to a selected contact, and an activity that scrolls through previous text messages and changes settings. Although together they form a cohesive user interface, each activity remains independent of the others. Each is implemented as a subclass of the base class Activity class.

An application can have only one activity, or, like the SMS application just mentioned, contain many. The role of each activity, and its number, naturally depends on the application and its design. In general, there is always an application that is marked as the first one the user sees when the application starts. The way to move from one activity to another is to start the next one with the current activity.

## 📚Dalvik & Smali ?
## 📚 What is **Android components** ?

