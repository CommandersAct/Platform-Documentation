# Triggers

## Default triggers

You can select a default trigger in the container options.

This means that each time you will add a tag to your container, the default trigger(s) will apply on this tag.

To select your default trigger(s), go in the container options, “advanced” part:

<figure><img src="../../../../../../../.gitbook/assets/image (47).png" alt=""><figcaption></figcaption></figure>

## Container loaded

This trigger allows calling tags when the container is loaded on a page. It is the default trigger for all the tags you add to your container. This means that the tag will only be called when your JavaScript container loads on your site, but it will not be the case for other event types (such as a click, a page change within an “single page applications” environment, etc.).\
In order to trigger tags when a container loads on your page, all you need to do is selecting them from the list.

<figure><img src="../../../../../../../.gitbook/assets/image (96).png" alt=""><figcaption></figcaption></figure>

## DOM Ready

This trigger allows calling tags when the page’s structure is built (on the “DOM Ready” event). To launch tags on this event, all you need to do is selecting them. They will be called on the DOM Ready event when the page loads.

<figure><img src="../../../../../../../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

## Click



This trigger allows calling tags whenever elements of the page are clicked.\
Example: if you would like to call a tag when a user clicks a button (ex: “add to cart” button), select the desired tag(s) and enter the code allowing to target the button or the link on your page in the “CSS Selector” field.

<figure><img src="../../../../../../../.gitbook/assets/image (75).png" alt=""><figcaption></figcaption></figure>

_Must know:_

* _To retrieve the CSS selector, open your browser’s console and use its targeting tool to target one of your page’s elements. Then right-click, the code appearing in your console, click “Copy” and “Copy selector”. All you have to do next is pasting this code in the interface._

<figure><img src="../../../../../../../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>

* _You can enter many selectors in the interface; you will have to separate them with commas._

## Form submission

This trigger allows calling tags when a user submits a form properly filled.\
Example: when they click the “submit” button or press the Enter key.\
To call a tag when a form is submitted, follow the same steps you followed to call a tag upon a click. Indicate your trigger’s name (ex: “account creation confirmation”), select the desired tag(s) and enter the code allowing targeting the form submission button on your page in the “CSS Selector” field.

<figure><img src="../../../../../../../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>

## Scroll

This trigger allows calling tags when a user scrolls the page vertically or horizontally. In order to execute a tag on scrolling, you will need to enter your trigger’s name (ex: “30% vertical scrolling”), select the desired tag(s), choose the scrolling type (horizontal/vertical) from the dropdown menu, the expected scrolling and measuring unit (page percentage or pixels).

<figure><img src="../../../../../../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

## Custom

This trigger allows calling tags whenever a Commanders Act event function (tC.event.xxx) is identified on the page. If you wish to execute a tag on a custom eventm, please indicate your trigger’s name (ex: “add to cart click”), select the desired tag(s) and enter the implemented event function’s name (ex : “tC.event.add\_to\_cart”).

You can also use the [Javascript SDK](../../../../web/js-sdk/#use-javascript-sdk-in-tms) to track events & create custom triggers\


<figure><img src="../../../../../../../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>
