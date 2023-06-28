# Dry mode (lab)

{% hint style="info" %}
This feature is flagged to "**LAB**" (aka Laboratory feature), it means that interfaces are not definitive and may evolve in the future.

This feature is currently in private preview.
{% endhint %}

The Dry mode allows you to simulate sending events, **but events are not sent** to the destination.

Once this feature is activated, all outbound HTTP requests of the destination are mocked in order to test it before going live. The payload, the request, is visible in Event Inspector to let you see events and correct the format if needed.&#x20;

As soon as you deactivate the dry mode, events will be sent to the destination.

When available, a switch is displayed on the destination interface:

<figure><img src="../../.gitbook/assets/destination_dry_mode_settings.png" alt=""><figcaption></figcaption></figure>

The 'Use real authentication' option allows you to test your credentials by not mocking potential authentication requests. It is only applicable to some destinations, such as Google Enhanced Conversions or Snapchat.
