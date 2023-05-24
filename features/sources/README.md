# Sources

Check out the [Sources catalog](sources-catalog/) if you merely want to look at the Commanders Act sources and how each is implemented.

## Sources vs Destinations <a href="#sources-vs-destinations" id="sources-vs-destinations"></a>

The platform has [Sources](./) and [Destinations](../destinations/). Sources send data _into_ the platform, while Destinations receive data _from_ the platform.

{% hint style="info" %}
A source is an emitter of events, more information [here](../../getting-started/concepts/#source).
{% endhint %}

## Source key

The source key is a unique identifier for each Source. It allows Commanders Act to identify which Source is transmitting the data and which destinations should be the recipients of that data. It is also employed to deactivate a source when necessary.

To locate a source key, you initially need to have or create a source like a website, server, or mobile source.

Next, within the Source, navigate to “Settings", and then proceed to “source key".
