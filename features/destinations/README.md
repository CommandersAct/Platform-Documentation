# Destinations

Check out the Destinations catalog if you merely want to look at the Commanders Act destinations and how each is implemented.

## Sources vs Destinations <a href="#sources-vs-destinations" id="sources-vs-destinations"></a>

The platform has Sources and Destinations. Sources send data _into_ the platform, while Destinations receive data _from_ the platform.

Server-side destinations include automatic retries when delivery fails due to a timeout, a network error, a temporary destination error (5xx), or rate limiting (429). This helps recover deliveries affected by temporary issues. Events successfully delivered after a retry are reported in [Event Delivery](event-delivery.md).
