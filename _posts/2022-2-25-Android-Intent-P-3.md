# Android Intent P-3


| Content                |
|:---------------------- |
| **What is Intent?**    |
| **Type of Intent**     |
| **Intent Component**   |
| **Intent Filter**      |
| **Example of Intent**  |
| **Attacks in Intents** |
|                        |

## What is Intent ?
Intent is a messaging object you can use to request an action from another application components (activities , services and Broadcast Receivers) 

Intents themselves are object containing information on operations to be performed .

Intent is data structure designed to hold info on events or operations to be performed.

Let’s look upon the informal way of defining Intents. You can think of Intents as a messaging service that is used to communicate between various components of the Android application.
 For example, if you want to send some message from Egypt to USA using the Post Office facility then you can do so by buying an Envelope and then pass the message in the Envelope and send the message to the desired location.
 
 
 ## Intent Types
 There are two type of Intent:
 
 ### 1-Explicit Intents
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
