# Perimeters & constraints

_Perimeters_ and _Constraints_ are two methods to **conditionally** fire your tags.&#x20;

* Under the _Perimeter_ panel, tags fire if at least **one rule** is true.
* Under the _Constraints_ panel, tags fire if **all rules** are true.

## Variable

The “**Variables**” tab allows you to create rules based on your data layer variables (external variables, internal variables, events attributes, events variables):

**Condition and behavior**

“**If Variable Equals**“: Tag activated if the variable equals the specified value.

“**If Variable is Not Equal**“: Tag activated if the variable differs from the specified value.

“**OR Condition (One Variable)**“: Tag activated if the variable equals at least one of the specified values. \
In case of multiple values: enter all the values in the field separated by a comma ",". Don't use space between.

“N**AND Condition (One Variable)**“: Tag activated if the variable equals two or more specified values.\
In case of multiple values: enter all the values in the field separated by a comma ",". Don't use space between.

“**OR Condition (Up To Six Possible Variables)**“: Tag activated if at least one of the variables equals the specified value.&#x20;

“**AND Condition (Up To Six Possible Variables)**“: Tag activated if all the variables equal all the specified values.

“**Greater than condition**“: Tag activated if the variable is greater than the specified value.

“**Less than condition**“: Tag activated if the variable is less than the specified value.

“**If Variable Contains**“: Tag activated if the variable contains the specified value.\
In case of multiple values: enter all the values in the field separated by a comma ",". Don't use space between.

“**If Variable Does Not Contain**“: Tag activated if the variable does not contain the specified value.\
In case of multiple values: enter all the values in the field separated by a comma ",". Don't use space between.

“**If Variable Matches**“: Tag activated if the variable matches the specified value (regular expressions allowed: \* to match any character and ^ for “variable begins with”).\
In case of multiple values: enter all the values in the field separated by a comma ",". Don't use space between.

“**If Variable Doesn’t Match**“: Tag activated if the variable does not match the specified value (regular expressions allowed: \* to match any character and ^ for “variable begins with”).\
In case of multiple values: enter all the values in the field separated by a comma ",". Don't use space between.

<figure><img src="../../../../../../../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>

**In which case using “external variables” for the mapping?**

When you want to create a rule based on a tc\_vars from the data layer implemented on your website.

Example: your technical team has implemented an env\_country variable, and you want to create a rule based on it:

<figure><img src="../../../../../../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

**In which case using “internal variables” for the mapping?**

When you want to create a rule based on a variable that you have created by yourself, from the internal variable interface.

**In which case using “event variables” for the mapping?**

When you want to create a rule based on a variable specific to an event.

Example: The following event is implemented in your site’s source code:

```
tC.event.add_to_cart(this, {"product_name":"iphone", "product_id":"1234"})
```

To call a tag only if the product name is “iphone”, you have to select the event variable named “product\_name” and configure it in the following manner:

<figure><img src="../../../../../../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

## Cookie

The “**Cookie**” tab allows you to create rules based on cookies you have previously created in the Commanders Act interface or which are available for your site’s domain name (first-party cookies).

**Condition and behavior**

“**If Cookie Equals**“: Tag activated if the cookie’s value equals the specified value.

“**If Cookie Is Not Equal**“: Tag activated if the cookie’s value differs from the specified value.

“**If Cookie Contains**“: Tag activated if the cookie’s value contains the specified value. \
In case of multiple values : enter all the values in the field separated by a comma ",". Don't use space between.

“**If Cookie Doesn’t Contain**“: Tag activated if the cookie’s value does not contain the specified value.\
In case of multiple values : enter all the values in the field separated by a comma ",". don't use space between.

Example with multiple values: In order to call a tag when your “consent\_status” cookie equals “exempt” or "optin", you must select the “If Cookie Equals” rule and configure it in the following manner:

<figure><img src="../../../../../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

## URL

This tab allows you to create rules based on your site’s URLs (note: we **recommend** that you use rules based on variables instead of URLs since the rule will become obsolete if your URL changes in the future):

**Condition and behavior**

“**If URL Equals**“: Tag activated if the URL equals the specified value.

“**If URL Contains**“: Tag activated if the URL contains the specified value. \
In case of multiple values : enter all the values in the field separated by a comma ",". Don't use space between.

“**If URL Doesn’t Contain**“: Tag activated if the URL does not contain the specified value.

“**If URL Matches**“: Tag activated if the URL matches the specified value (regular expressions allowed: \* to match any character and ^ for “variable begins with”).

“**If URL Doesn’t Match**“: Tag activated if the URL does not match the specified value (regular expressions allowed: \* to match any character and ^ for “variable begins with”).

Example: to call a tag when your URL indicates that the user is on the product page (providing your product page URLs are all structured the same: https://www.site.com/$category$/$subcategory$/product\_$product\_ID$), you have to select the “If URL Matches” rule and configure it in the following manner:

<figure><img src="../../../../../../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

## **Browser**

This tab allows you to create rules based on browsers.

**Condition and behavior**

“**If Browser Is**“: Tag activated if the browser is (choose from the list).

“**If Browser Is Not**“: Tag activated if the browser is not (choose from the list).

<figure><img src="../../../../../../../.gitbook/assets/image (61).png" alt=""><figcaption></figcaption></figure>

## Mobile

This tab allows you to create rules based on the type of device.

**Condition and behavior**

“**If Device / OS Is**“: Tag activated if the device is (choose from the list).

“**If Device / OS Is Not**“: Tag activated if the device is not (choose from the list).

“**If Device / OS Is Android Tablet**“: Tag activated if the device is an Android tablet.

“**If Device / OS Is Android Mobile**“: Tag activated if the device is an Android mobile device.

“**If Device / OS Is Not Android Tablet**“: Tag activated if the device is not an Android tablet.

“**If Device / OS Is Not Android Mobile**“: Tag activated if the device is not an Android mobile device.

Example: to prevent a tag from being called on an Android mobile device, you must select the “If Device Is Not Android Mobile” rule and configure it:

<figure><img src="../../../../../../../.gitbook/assets/image (97).png" alt=""><figcaption></figcaption></figure>

## DataCommander

This tab allows you to create rules based on the type of audience segments created in DataCommander.

**Condition and behavior**

&#x20;“**DataCommander OR condition (up to six variables)**“: Tag activated if at least one of the audiences equals the specified value.

“**DataCommander AND condition (up to six variables)**“: Tag activated if all the audiences equal all the specified values.

“**DataCommander Event activation**“: Tag activated on an event

<figure><img src="../../../../../../../.gitbook/assets/image (57).png" alt=""><figcaption></figcaption></figure>

## Advanced rules

This tab allows you to create all types of advanced rules. For example, you can create sampling rules or even “**Custom**” rules:

**Condition and behaviour**

“**Sampling (1/X) (Page Based)**“: Tag activated in X% of page views.

“**Sampling (1/X) (Session Based)**” : Tag activated in X% of visits.

“**Sampling (1/X) (Visitor Based)**“: Tag activated for X% of visitors.

“**(A or B or C or D or E) AND (F or G or H or I or J)**“: Tag activated if at least one of the variables in the first group AND at least one of the variables in the second group equal the specified values.

“**(A and B and C and D and E) AND (F or G or H or I or J)**“: Tag activated if all the variables in the first group AND at least one of the variables in the second group equal the specified values.

“(**A and B and C and D and E) OR (F and G and H and I and J)**“: Tag activated if all the variables in the first group OR all the variables in the second group equal the specified values.

“**(A and B and C and D and E) OR (F or G or H or I or J)**“: Tag activated if all the variables in the first group OR at least one of the variables in the second group equal the specified values.

“**(A different than VALUE1) OR (B different than VALUE2)**“: Tag activated if the first variable is not equal to a value OR the second variable is not equal to a value.

“**(A different than VALUE1) OR (B equals VALUE2)**“: Tag activated if the first variable is not equal to a value OR the second variable is equal to a value.

“**(A different than VALUE1) AND (B different than VALUE2)**“: Tag activated if the first variable is not equal to a value AND the second variable is not equal to a value.

“**(A different than VALUE1) AND (B equals VALUE2)**“: Tag activated if the first variable is not equal to a value AND the second variable equals a value.

“**In Array**“: Tag activated if the variable is present in the variable array.

“**In Sub Array**“: Tag activated if the variable is present in a variable array key.

“**Array Intersectio**n”: Tag activated if two variables from two variable arrays are equal.

“**Custom**“: Custom rule (to define in JavaScript).

Example: In order to call a tag for 25% of site visitors, you must select the “Sampling (1/X) (Visitor Based)” and configure it in the following manner:\


<figure><img src="../../../../../../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>
