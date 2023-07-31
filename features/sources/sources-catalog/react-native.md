---
description: Installation Instructions for Commanders Act with React Native.
---

# React native

We currently don't offer an official bridge for ReactNative as it's usualy quite easy for developpers to create it themselves.

!!Short version step by step process to use our solutions with React Native are as follow:
------------

1.  Read our SDKs documentations here: [iOS](https://github.com/CommandersAct/iOSV5) & [Android](https://github.com/CommandersAct/AndroidV5)
2.  Create your bridges for Android and iOS
3.  Create an Android and/or iOS sources in our plateform.
4.  Code the events and start sending them!

!!Long version:
--------

!Read our documentation

Before starting to code you will need to read our documentation here : [iOS](https://github.com/CommandersAct/iOSV5) & [Android](https://github.com/CommandersAct/AndroidV5)
We have many ways of using our solutions so you need to find the one fitting your needs.
You might need the consent module for example.

Understanding this documentation will make the next step easier.

!Create your bridges

It usually consist of one file translating the native functions to React Native.
You'll most likely need one method to initialize the ServerSide class, several methods to create the events you need and one to send data.

!Creating a source

To send and validate data to CommandersAct you need a SourceKey. To get it, you need to create a source inside our plateform.
(!Sarah, add link to doc)

The source type is actually only here to help you sort your sources.

This source will also contain information about what is collected and the health of the implementation.
Since you're using React Native you might only need to create one source and get one key. But you might also want to separate information coming from Android and the information from iOS it that's the case, simply create one source of each and in the wrappers check that you're giving the right key in the right wrapper.

!Send events

This should be quite easy and straightforward now!

!!FAQ
------

- What will happen if you release an official wrapper afterwards
Nothing. We will simply do the same thing as you've already done so you won't need to change anything!

