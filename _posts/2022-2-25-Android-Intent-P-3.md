# Android Intent P-3


| Content                |
|:---------------------- |
| **What is Intent?**    |
| **Type of Intent**     |
| **Use Cases**          |
| **Intent Component**   |
| **Intent Filter**      |
| **Example of Intent**  |
| **Attacks in Intents** |
                      

## What is Intent ?
Intent is a messaging object you can use to request an action from another application components (activities , services and Broadcast Receivers) 

Intents themselves are object containing information on operations to be performed .

Intent is data structure designed to hold info on events or operations to be performed.

Let’s look upon the informal way of defining Intents. You can think of Intents as a messaging service that is used to communicate between various components of the Android application.
 For example, if you want to send some message from Egypt to USA using the Post Office facility then you can do so by buying an Envelope and then pass the message in the Envelope and send the message to the desired location.
 
 
## Intent Types
 There are two type of Intent:
 
### 1- Explicit Intents
 ![](https://i.imgur.com/vd7pS0m.png)
if you want communication between the components of your application only then you can use the Explicit Intent.
Explicit Intents are used to communicate with a particular component of the same application

provide the component name (class name ) This is usually for inter-application components.

  for example , if you want to launch an Activity by clicking some button  on the present Activity then you go to target activity 
         code example for Explict Intent https://developer.android.com/guide/components/intents-filters#ExampleExplicit

### 2-Implicit Intent
used to invoke components of different application 

They don’t  provide the specific component name to be invoked but rely on system to find the best available component to be invoked


don't name a specific component , but instead declare a general action to perform , which allow a component from another app to handle 
For example , if you want to show the user a location on a map , you can use an implicit intent to request that another capable app show a specified location on a map 
code example for Implicit Intent   https://developer.android.com/guide/components/intents-filters#ExampleSend

### How Implicit Intent find component for Intent ??
If you call the Implicit Intent then , the Android system will search for all the available components that can be used to start that activity ,
This process is done by comparing the content of the intent with the content present in the intent-filters declared in the AndroidManifest.xml
If there is only one intent-filter that is compatible with the content of the intent the android system will start the desired component . <br/>
But if there are am number of intent-filters that are compatible with the content of the intent then the android system will show you a list of application that can be used to perform 

## Use cases Example  of Intents :
1. start Activity
2. Start a service
3. Delivering a broadcast 

![](https://i.imgur.com/qLfMfBM.png)

## Intent Component 

Intent is a data structure designed to hold information on events or operation that android system used to determine which component to start  (such as the exact component name or component category that should receive the intent)

1-Component Name:  <br/>
This is optional , but it's critical piece of information that makes an Intent explicit , meaning that intent should be delivered only to the app component defined by the component name .
without a component name the intent is implicit and Android system will decides which component should recive the intent  <br/>

2-Action: <br/>
A string that specifies the generic action to perform (such as view or pick)
example of action   ACTION_VIEW
Use this action in an intent with startActivity()  when you have some information that an activity can show to the user And developer can make custom action  to perform  by define app package name
```c++
static final String ACTION_TIMETRAVEL = "com.example.action.TIMETRAVEL";
```
3- Extras :  <br/>
you can add extra data to intent in the for of key-value pairs and this extras information can be passed from one activity to the other <br/>
4-Category :  <br/>
Category is used in case of Explicit Intents where you need to specify the type of application that will be used to perform a particular action.  <br/>
5-Data : <br/>
important to specify the type of data (its MIME type) on which the action is to be performed by Android system which the help of intents  <br/>
 
## Intent Filter
Each components can provide Intent-filters   structures that provide information on which Intents can be handled by particular components.

The system then compares filters to the Intent object and select the best available components for it 
If a component does not have Intent-filters, it can only receive explicit Intents.
Note that Intent-filters cannot be relied on for security because one can always send an explicit Intent to it, thus bypassing the filters. 
Component specific permissions should always be defined to restrict who can access a particular component through Intents. In addition, limited data can be passed through Intents. 
However, any sensitive information, such as passwords, should never be sent through Intents, as these can be received by malicious components. 

### Intent Filter component

![](https://i.imgur.com/191sWkn.png)

In each app component that includes an <intent-filter> element,
 explicitly set a value for android:exported.<br/>
 This attribute indicates whether the app component is accessible to other apps.
    
In the example scenario below, MainActivity is sending sensitive data to MainActivity2 via intent. But the malicious app did the same definition of <intent-filter> to itself. Because of this situation, the implict intent scenario exposed and the relevant data was transmitted to the 3rd party application.    

![](https://i.imgur.com/2TU79n9.png)

Example: if we have a component file which will use implicit intent (action, data, category) like action call a tel and there are more than one component with the same contents of call a tel, and uses the same intent. You may see the option Open with: Call Phone - Truecaller - etc.. and that's because of the existing of more than one component matches and handles same intent.

When intent filters are mentioned for a component in the Manifest file that component automatically becomes exported unless the developer overrides that by mentioning `exported=FALSE` in the component attribute.
    
Example: if we have a component file which will use implicit intent (action, data, category) like action call a tel and there are more than one component with the same contents of call a tel, and uses the same intent. You may see the option Open with: Call Phone - Truecaller - etc.. and that's because of the existing of more than one component matches and handles same intent.

When intent filters are mentioned for a component in the Manifest file that component automatically becomes exported unless the developer overrides that by mentioning exported=FALSE in the component attribute.

