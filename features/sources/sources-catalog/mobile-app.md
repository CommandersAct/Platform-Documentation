# Mobile APP

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-cover data-type="files"></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td></td><td>ANDROID SDK</td><td></td><td><a href="../../../.gitbook/assets/Android_symbol_green_RGB[1].png">Android_symbol_green_RGB[1].png</a></td><td><a href="android.md">android.md</a></td></tr><tr><td></td><td>IOS SDK</td><td></td><td><a href="../../../.gitbook/assets/apple-logo-png-dallas-shootings-don-add-are-speech-zones-used-4[1].png">apple-logo-png-dallas-shootings-don-add-are-speech-zones-used-4[1].png</a></td><td><a href="ios.md">ios.md</a></td></tr><tr><td></td><td>FLUTTER SDK</td><td></td><td><a href="../../../.gitbook/assets/flutter5786[1].jpg">flutter5786[1].jpg</a></td><td><a href="flutter.md">flutter.md</a></td></tr><tr><td></td><td>REACT NATIVE SDK</td><td></td><td><a href="../../../.gitbook/assets/2300px-React-icon.svg[1].png">2300px-React-icon.svg[1].png</a></td><td><a href="react-native.md">react-native.md</a></td></tr><tr><td><p></p><p>HTTP TRACKING API</p></td><td></td><td></td><td><a href="../../../.gitbook/assets/HTTP (2).jpg">HTTP (2).jpg</a></td><td><a href="https://doc.commandersact.com/features/sources/sources-catalog/server/http-tracking-api">https://doc.commandersact.com/features/sources/sources-catalog/server/http-tracking-api</a></td></tr></tbody></table>

## Introduction to mobile app tagging

CommandersAct’s **SDK** allows you to trigger destinations from a mobile application.

Commanders Act offers a so-called “super light” SDK you can include in your mobile app’s code; its purpose is to reduce calls to partner solutions as much as possible in order to improve your app’s performance and user experience. A unique call is issued to CommandersAct’s servers per action recorded in the app. Information related to the page browsed or the element that is clicked is then sent separately to partner solutions by CommandersAct’s servers; this allows to prevent applications’ loading speed from slowing down.

**Note**: Not all solutions are compatible with this method. Since the light SDK sends app information to partner solutions’ servers, they cannot “go back” to the app. Adserving solutions (those displaying ads) and push notification providers are thus not compatible with this method.

The basic operational principle of Commanders light SDK is:

– **Step 1**: the mobile data layer and CommandersAct’s SDK are called in the app’s source code every time the screen loads or that an element is clicked. (your IT staff should have implemented this at the start of the project).

– **Step 2**: CommandersAct’s SDK issues calls to CommandersAct’s servers and automatically sends the mobile data layer’s contents. This is the server-side hits’ structure: https://collect.commander1.com/events?tc\_s=`${siteID}`\&token=`${YOUR_SOURCE_KEY}`

`${siteID}` and `${YOUR_SOURCE_KEY}` are to be provided to the SDK and will be replaced automatically.

The rest of the parameters are send in the body in POST like presented here:

{% content-ref url="../../../developers/tracking/about-events/mobile-sdk-event-specificity.md" %}
[mobile-sdk-event-specificity.md](../../../developers/tracking/about-events/mobile-sdk-event-specificity.md)
{% endcontent-ref %}

– **Step 3**: CommandersAct’s servers send the received information to the different destinations. There are as many outgoing hits as there are partner solutions you wish to send information to.

<figure><img src="../../../.gitbook/assets/image (15) (1).png" alt="" width="563"><figcaption></figcaption></figure>

Ex: if you wish to issue a call to both Criteo and Google, a hit will be sent to either solution’s servers.

Implementing our SDKs on a mobile application is a project that consists of the steps listed hereunder:

* Definition of the mobile application’s tagging plan: selection and definition of the events.
* Creation of a mobile source and destinations
* CommandersAct SDK implementation in the app’s source code.
* Acceptance testing of the implementation in a test environment.
* Publishing

## Step #1: defining the application's tagging plan

The tagging plan corresponds to the list of events that will be sent.

## Step #2: creating a mobile source and configuring destinations in the CommandersAct interface

* **Creating a source for iOS, Android or both.**
* **Implement or select destinations.**

Implementing mobile destination is the same as implementing cloud-base destinations

## Step #3: implementing the SDK in the applications' source code

The SDK implementation is performed by technical staff or IT departments.

These elements must be provided:

* The app’s CommandersAct tagging plan, which lets IT staff know which events to declare and on which screens or elements.
* Technical documentation referring to each and every app. It must contain elements that are key to setting up the SDK and screenshots of setup examples.

Click here to read the corresponding technical documentation. iOS: [https://github.com/CommandersAct/iOSV5/](https://github.com/CommandersAct/iOSV5/) android: [https://github.com/CommandersAct/androidv5/](https://github.com/CommandersAct/androidv5/)

The site’s ID (Commanders Act account number) and that of the source key are necessary to set-up the SDK. These two elements can be retrieved in the interface.

## Step #4: Testing the setup in a test environment

Commanders Act SDK can be tested with many different tools:

### **Tests for iOS with XCode**

Commanders Act SDK for iOS can be tested with Apple’s developing software “XCode”:

[https://itunes.apple.com/fr/app/xcode/id497799835](https://itunes.apple.com/fr/app/xcode/id497799835)

You will need to connect your iPhone to your Mac.

Open XCode, go to “Window” ), > “Devices” (2), then select your device in thecolumn to the left (3):

![](../../../.gitbook/assets/xcode_1\[1].png)

These elements will be displayed when you analyze mobile logs:

* Commanders Act SDK’s version number \
  example for consent module: “Commanders Act Privacy module init with version: 5.2.0”
* Commanders Act site ID&#x20;
* Sended Server-Side events containing all the properties you have sent to Commanders Act servers (POST method). For more information about events construction, you can refer to our [events codes examples](../../../developers/tracking/events-reference/)

![](../../../.gitbook/assets/xcode_2\[1].png)

\*\*\*

### **Running tests for Android or iOS with Charles Debugger**

Commanders Act SDK for both iOS and Android operating systems can be tested with the “Charles Debugger” proxy, downloadable for free here: [https://www.charlesproxy.com/](https://www.charlesproxy.com)

The first thing to do is to configure your phone so it can communicate with Charles.

In your phone’s settings, go to the Wi-fi configuration tab.

Select your network and proceed to the advanced options to edit Wi-fi settings.

Add a proxy manually:

* Proxy’s name (server)(1): Computer’s IP (you can find it in the “Local IP address” tab from Charles’ options)
* Port (2): 8888

Save.

![](../../../.gitbook/assets/charles_1\[1].png)

Go to the Charles app and authorize it to connect to the phone.

![](../../../.gitbook/assets/charles_2\[1].png)

Browse the web with your phone and in Charles (on your computer) apply a “Commander” filter to see server-side hits displayed in the “Overview” section. They look like this: \
[https://collect.commander1.com/events?tc\_s=XXXX\&token=XYZZ](https://collect.commander1.com/events?tc_s=XXXX\&token=XYZZ)

When you go to the “Request” area, you will be able to see all variables and the corresponding values that are sent through the Commanders Act SDK.

![](../../../.gitbook/assets/charles_3\[1].png)

HTTPS Protocol:

Most of the time, server-side calls are issued through an https protocol.

Seeing https hits with Charles requires a more complex configuration. You will need to open your phone’s browser while Charles runs on your computer and go to this URL on your phone [http://www.charlesproxy.com/getssl/](http://www.charlesproxy.com/getssl/)

Download the certificate and install it; you will need to enter its name for two applications “VPN and applications” and “Wi-fi”.

Go back to Charles > “SSL proxy settings” > “SSL Proxying” > check “Enable SSL Proxying” > Click “Add” and type “\*” in the “Host” field (to authorize any given host).

Then proceed to running tests the same way you do for http hits.

## Step #5: publishing

When the implementation is ok on your testing environment, you need to submit your app to app stores (Apple Store or Android Market) and wait for them to approve changes and include the new version in their catalogues.
