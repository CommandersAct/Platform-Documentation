# Troubleshooting

If you notice that a tag is slowing down your pages, please try the following:

* Have the tag load after the **DOM Loaded** event. Caution: not all tags are compatible with this method and the more you delay a tag’s execution the more you loose data in your reports.

This code block allows calling a tag during the **DOM Loaded** event:

tC\_ready = function(){

// Code du tag

}

if (window.addEventListener)

window.addEventListener(‘load’, tC\_ready, false)

else if (window.attachEvent)

window.attachEvent(‘onload’, tC\_ready)

*   Get in touch with the tag’s editor and request they improve their tag in terms of size or server response. Note: it is possible to include the tag’s JavaScript file in the Commanders Act container while on the “EDIT” tab from the Commanders Act interface.

    <figure><img src="../../../../../../../.gitbook/assets/image (358).png" alt=""><figcaption></figcaption></figure>
*   Sample the tag from the “**RULES**” tab from the  Commanders Act interface. This will improve the average loading time of your site’s pages.

    <figure><img src="../../../../../../../.gitbook/assets/image (359).png" alt=""><figcaption></figcaption></figure>
*   Shifting the tag’s execution order from the “GENERATION” tab from the  Commanders Act  interface (place the one taking longer to load at the end of the queue).\


    <figure><img src="../../../../../../../.gitbook/assets/image (360).png" alt=""><figcaption></figcaption></figure>
*   Use a timeout on your tags from the “GENERATION” tab from the  Commanders Act  interface. This feature interrupts the tag’s execution if it takes too long to load.

    <figure><img src="../../../../../../../.gitbook/assets/image (361).png" alt=""><figcaption></figcaption></figure>
*   Deactivate the tag from the “GENERATION” tab from the  Commanders Act interface \
    \


    <figure><img src="../../../../../../../.gitbook/assets/image (362).png" alt=""><figcaption></figcaption></figure>
* Use your tag in a **serverside** configuration (this entails activating an **additional** module from the Commanders Act product, please contact your account manager or our Support Department for further information). Caution: not all tags are compatible with this method.

For more detailed information on how to set up these methods, please contact our Support Department (support@commandersact.com).
