# Exports

## Manual or Scheduled export

You can export the raw consent data in the Options menu.&#x20;

<figure><img src="../../../.gitbook/assets/image (135).png" alt=""><figcaption></figcaption></figure>

You can download consent data once, or schedule a recurrent export, by email or FTP.

<figure><img src="../../../.gitbook/assets/image (136).png" alt=""><figcaption></figcaption></figure>

## Export fields

The export includes the following fields:

| Field            | Description                                                                                                                                                                                          |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id\_hit          | ID of the hit (autoincrement id)                                                                                                                                                                     |
| id\_tagcommander | ID of the TagCommander container that installed the privacy banner that initiated the consent hit.                                                                                                   |
| id\_privacy      | ID of the privacy banner that initiated the consent hit.                                                                                                                                             |
| version          | Version of the privacy banner at the time the consent hit was initiated.                                                                                                                             |
| cookie           | Consent categories that were accepted in the privacy center.                                                                                                                                         |
| tcpid            | cookie ID of the consent (hashed).                                                                                                                                                                   |
| date\_hit        | Timestamp of the consent hit.                                                                                                                                                                        |
| privacy\_action  | <p>Action that initiated the hit. </p><ul><li>V: View of the banner</li><li>1: Opt-In click</li><li>0: Opt-out click</li><li>-1: User refused all consent (only on deprecated version 1.0)</li></ul> |
| type\_action     | <p>Type of action that generated the hit.</p><p>Ex of possible values: </p><ul><li>banner : click in the banner</li><li>pc : action in the privacy center</li></ul>                                  |
| device           | device type identifier (1=phone, 2=tablet, 3=desktop, 0=other)                                                                                                                                       |

{% hint style="info" %}
In case vendors are activated for the account, it is possible to include vendor optins in the export by switching the "Include Vendors in Export" toggle. This will increase export size considerably.
{% endhint %}

{% hint style="success" %}
IP address is not stored
{% endhint %}

## Storage retention

The option "**Consent storage duration in database**" allows to set a duration (in month) the consent data is stored in the consent database (which is used to prove consent). Be careful when changing the setting to not lose old consents by accident! You will be shown a prompt after changing the value to confirm the new duration. The maximum storage duration is 13 months. In case you need a longer storage duration, please contact your Commanders Act support or consultant.

<figure><img src="../../../.gitbook/assets/image (137).png" alt=""><figcaption></figcaption></figure>
