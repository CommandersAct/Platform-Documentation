# Facebook Custom Audiences

[Facebook ](https://www.facebook.com/)is an online social media and social networking service owned by [Meta](https://www.meta.com).\
​An API based Facebook Connector can be set up with the following procedure. The connector will send users data of all the users belonging to a given segment. The audience sent can contain both FB subscribers and non subscribers.

## User variables mapping <a href="#user-variables-mapping" id="user-variables-mapping"></a>

More information you send to Facebook, better is the matching with Facebook. You can choose to send email, phone number or any other information to increase the matching with Facebook.

If users don't have enough information, we will reject them (example: if a user only have a zip code, Facebook will not be able to match this user with only this information).

It takes up to 24 hours for Facebook to match users.

<figure><img src="../../../../.gitbook/assets/Capture d’écran 2022-12-07 à 11.38.21.png" alt=""><figcaption></figcaption></figure>

## Configuration <a href="#configuration" id="configuration"></a>

You need 2 information for the Facebook connector:

* Ad Account ID
* Access Token

<figure><img src="../../../../.gitbook/assets/Capture d’écran 2022-12-07 à 11.38.52.png" alt=""><figcaption></figcaption></figure>

### Where can I find the Ad Account ID? <a href="#where-can-i-find-the-ad-account-id" id="where-can-i-find-the-ad-account-id"></a>

You have to go on Facebook Business [https://business.facebook.com/](https://business.facebook.com/) and login to your account.

Then you have to go to ‘Ad Account settings’:

![](https://2406699966-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-LlBEwG5kQoxsckaoAZh%2F-M9XdQPuLipbdPkbWJl1%2F-M9Xh49TcBPbE8UTl3ud%2FCapture%20d%E2%80%99e%CC%81cran%202020-06-10%20a%CC%80%2010.50.21.png?alt=media\&token=bc4004eb-961a-479c-9fc2-75b741727e89)

And you will find the Ad Account ID:

![](https://2406699966-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-LlBEwG5kQoxsckaoAZh%2F-M9XdQPuLipbdPkbWJl1%2F-M9XgyL7RIyFnGMU6jKh%2FCapture%20d%E2%80%99e%CC%81cran%202020-06-10%20a%CC%80%2011.33.39.png?alt=media\&token=293d02df-f048-4c53-ba0c-7cf9fd3c9e38)

Copy and paste it on our Facebook connector.

### Where can I find the Access Token? <a href="#where-can-i-find-the-access-token" id="where-can-i-find-the-access-token"></a>

For this part, you have to go to Facebook Developers [https://developers.facebook.com/](https://developers.facebook.com/) and create or login to your account (you need to have a dedicated account for Facebook Developer).

Create a new app

Add the product ‘Marketing API’.

Go on ‘Settings’ and ‘Advanced’ section

Link your app to your Business Manager account and add your Ad Account ID in the ‘Authorized Ad Account ID’ section:

![](https://2406699966-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-LlBEwG5kQoxsckaoAZh%2F-M9XdQPuLipbdPkbWJl1%2F-M9XhMTu3uhk2ndkeJnU%2FCapture%20d%E2%80%99e%CC%81cran%202020-06-10%20a%CC%80%2011.01.44.png?alt=media\&token=7e344337-0c2d-4c9a-9c3e-d1b784dd06fd)

Then click on 'App Review' and 'Permissions and features'.\
Find the 'Ads Management Standard Access' component and, if you don't already have it, submit a request:

![](https://2406699966-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-LlBEwG5kQoxsckaoAZh%2F-MK9F2M3b2lh7DHy53vX%2F-MK9FVSXBTOqmwHk1TKN%2FMarketing%20API%20Standard%20access%20request.png?alt=media\&token=37d9e495-2a94-4963-aa8d-fa82e8f86552)

[https://developers.facebook.com/docs/marketing-api/access#standard](https://developers.facebook.com/docs/marketing-api/access#standard)​

Wait for the validation of your request.

Now you have an App linked to your Facebook Business Manager Account ([https://business.facebook.com/](https://business.facebook.com/)).\
Please check this page to be sure that the App is well associated with the Business account:

![](https://2406699966-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-LlBEwG5kQoxsckaoAZh%2F-Ma2qyxWuqeIvtNXLCIg%2F-Ma2rkqvFA5px8jSno8e%2FCapture%20d%E2%80%99e%CC%81cran%202021-05-19%20a%CC%80%2010.55.23.png?alt=media\&token=883787b9-6f0c-4449-8965-2f55826a47dd)

You should see in your Facebook Business account the new App you created.

### Generate the access token <a href="#generate-the-access-token" id="generate-the-access-token"></a>

You can choose here to generate a token without any expiration date (1st method, recommended) or with an expiration date (60 days - 2nd method, not recommended).

#### 1st method: generate a token without any expiration date <a href="#id-1st-method-generate-a-token-without-any-expiration-date" id="id-1st-method-generate-a-token-without-any-expiration-date"></a>

You have to create a system user on your Facebook Business Account ([https://business.facebook.com/](https://business.facebook.com/)).

{% hint style="warning" %}
This system user should have **admin** rights for the ad account and for the app you created.
{% endhint %}

![](https://2406699966-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-LlBEwG5kQoxsckaoAZh%2F-Ma2tlwZHdZbXEDou9iQ%2F-Ma2v-Sz535B9cqmdcgk%2FCapture%20d%E2%80%99e%CC%81cran%202021-05-19%20a%CC%80%2010.55.58.png?alt=media\&token=b6135a3d-95ef-4000-93e4-c587d62b6570)

When it is done, you can Generate New Token:

![](https://2406699966-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-LlBEwG5kQoxsckaoAZh%2F-Ma2tlwZHdZbXEDou9iQ%2F-Ma2vCHFA52RMRQH8Ano%2FCapture%20d%E2%80%99e%CC%81cran%202021-05-19%20a%CC%80%2010.57.44.png?alt=media\&token=de993c18-13d9-4304-afb7-d598ad997bde)

Select the App you have created before and select the right permission:

![](https://2406699966-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-LlBEwG5kQoxsckaoAZh%2F-Ma2tlwZHdZbXEDou9iQ%2F-Ma2vRM4u-gQ-95hsM7I%2FCapture%20d%E2%80%99e%CC%81cran%202021-05-19%20a%CC%80%2010.58.58.png?alt=media\&token=163075c5-44b2-4b3b-b58c-c0c9fa03f8be)

Then copy and paste the generated token on our connector:

![](https://2406699966-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-LlBEwG5kQoxsckaoAZh%2F-Ma2tlwZHdZbXEDou9iQ%2F-Ma2vkpUr_fPie9UzRtg%2Fimage.png?alt=media\&token=4f7b11b3-4983-4d73-b600-a5247596e34e)

#### 2nd method: generate an access token with an expiration date (60 days) <a href="#id-2nd-method-generate-an-access-token-with-an-expiration-date-60-days" id="id-2nd-method-generate-an-access-token-with-an-expiration-date-60-days"></a>

On the Facebook developers, on your App you created, click on ‘Marketing API’ and ‘Tools’.

On ‘Get Access Token’, tick ‘ads\_management’ and click on ‘Get Token’.

![](https://2406699966-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-LlBEwG5kQoxsckaoAZh%2F-M9XdQPuLipbdPkbWJl1%2F-M9XhW8e0jVMiNtoP9SI%2FCapture%20d%E2%80%99e%CC%81cran%202020-06-10%20a%CC%80%2011.02.09.png?alt=media\&token=7429ca3d-d0c2-4dc1-8af4-b39373aa1814)

You can now copy and paste this token on our Facebook connector.

{% hint style="warning" %}
Be careful: Each time you click on Get Token it will generate a new one that you have to use (the previous one will be not valid anymore)
{% endhint %}

### Common errors <a href="#common-errors" id="common-errors"></a>

{% hint style="danger" %}
Before to save the connector, be sure you have accepted Facebook general conditions for custom audiences.

Go on this link and replace the AD\_ACCOUNT\_ID per your own Ad Account ID:

[https://www.facebook.com/ads/manage/customaudiences/tos/?act=AD\_ACCOUNT\_ID](https://www.facebook.com/ads/manage/customaudiences/tos/?act=AD_ACCOUNT_ID)
{% endhint %}

{% hint style="danger" %}
Be sure you have the admin rights for your Facebook Business account
{% endhint %}

## Check new audience created on Facebook <a href="#check-new-audience-created-on-facebook" id="check-new-audience-created-on-facebook"></a>

Save the connector and users who will enter the segment will be pushed to Facebook new custom audience.

Then on Facebook, click on Audiences.

![](https://2406699966-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LlBEwG5kQoxsckaoAZh%2Fuploads%2FCcMCljiGyyAk13A92c4N%2FCapture%20d%E2%80%99e%CC%81cran%202021-11-25%20a%CC%80%2018.09.45.png?alt=media\&token=b50ce462-0213-4069-a0da-f27e8455a84c)

A new custom audience will be created.

{% hint style="success" %}
The name of the new audience will start with `CA_{name}`
{% endhint %}

![](<../../../../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1) (1) (1).png>)
