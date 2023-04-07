---
layout: posts
author: Kiran Manoj
author-img: "/media/kiran.jpg"
title: Adding Mappable Actions to Android App
description: Wrapping up a few key features on the Android app
img: /media/Blogs/Kiran/ui.png
---

As our hardware and firmware for the ring was finalized, the final feature we are adding is the ability to allow users to map input methods to features of their preference. This is not a critical must have feature, it is a very nice to have feature.

We had a total of 5 different inputs the ring was able to process. They were: Single tap, Double tap, Triple tap, Long press, and Double tap + Long press. We had exactly 5 actions which our app could perform as well: SOS Emergency Broadcast, Toggle Music, Play Next, Play Previous, and Find My Phone. This meant that each input from the ring could be mapped to exactly one action.

In order to implement this in the app, we had to consider several cases. Firstly, we needed a default mapping which would be present when they first opened the application and had not customized it. This original mapping was selected to be: 

- Single tap -> Toggle Music
- Double tap -> Play Previous
- Triple tap -> Play Next
- Long press -> Find My Phone
- Double tap + Long press -> Emergency SOS Broadcast

One note to make is that we chose the default Emergency SOS Broadcast trigger to be Double tap + Long press to minimize the chance of it being automatically triggered by users.

In order to save user mappings of the inputs to actions, we made use of the local storage of the application. This is used to persist the mappings that users have selected, so that when the application is closed and reopened, the mappings are saved. We use the SharedPreferences library to do this within code. Also, when users update the mappings, we synchronously write to the disc to ensure after updating the mappings, the application will be able to immediately use the new input mappings in the Bluetooth service.

Here is the final completed UI of the app before symposium:

<img src="/media/Blogs/Kiran/ui.png">
*Main menu of the Ringify Android app*
