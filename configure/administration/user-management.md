# User management

The “User Management” interface is available to administrators only, from the “**Administration**” menu.

Then click “User management”. This interface allows you to grant access or modify user access to the Commanders Act interface on your account(s).

<figure><img src="../../.gitbook/assets/image (388).png" alt=""><figcaption></figcaption></figure>

## Creating a new user

_Note: only an administrator can create a new user._

Follow these steps to create a new user:

1/ Select the account(s) you wish to make changes to (you can start on step2 as well).

2/ Click the “Add / edit user(s)” button.

<figure><img src="../../.gitbook/assets/image (390).png" alt=""><figcaption></figcaption></figure>

3/ Fill in all required information about the new user:

(A) The account(s) you wish to grant access to

(B) User Roles. You can choose between 7 built-in roles:

* **Read only**: Users can visualize all of the interface’s elements but do not have the possibility to perform any action.
* **Marketing**: This role was conceived for users that do not wish to interact with the advanced technical elements of the interface. “Marketing” rights do not allow a user to create or edit containers, or to modify tags’ JavaScript code.
* **Technical**: This role provides access to every feature within the interface, except for a few advanced options that are available to account administrators only (please refer to the “Administrator” role to know more).
* **Custom**: “Custom” rights provide access to very specific parts of the interface, depending on your needs. For more information please refer to the “Modifying/customizing user rights” article.
* **Administrator**: The Administrator has access to every feature in the user interface and can create new users as well. Advanced options are only made available for administrators: renaming containers, creating “commander1.com” subdomains, connector setup…
* **Privacy manager**: The Administrator for the privacy module only.
* **Privacy technical**: This role gives access to the privacy module's features except for the options section.

If you created custom roles in the “profile management” tab (please refer to the “Creating User Profiles” article) , they will also be available from the “Role” drop down menu.

Please note: If you select multiple sites (A), only user profiles shared by all these sites will be available from the “Role” drop down menus.

(C) User type. You can choose between 3 types of user types:

* End user: clients
* Technology partner of an end customer: tag editors
* Service provider of an end customer: agencies working for end users

(D) Language. Note: at present the interface is only available in English and French.

(E) User Email. If the user is already present in Commanders Act’s database, the email, name and surname fields will automatically be filled in. We do not recommend giving access to generic email addresses: it could affect tracking of user actions within the interface and jeopardize security in case employees leave your company.

(F) User name and surname.

(G) You can also add/change account settings by clicking the “+” button.

<figure><img src="../../.gitbook/assets/image (389).png" alt=""><figcaption></figcaption></figure>

## Modifying user rights

_Note: Only an administrator has the possibility to modify/customize rights._

Follow these steps to modify user rights:

1/ Select a specific account from the drop down menu.

2/ Select the user(s) whose rights you wish to modify.

3/ Select “Change Role” from the drop down menu and click “Apply”.

<figure><img src="../../.gitbook/assets/image (391).png" alt=""><figcaption></figcaption></figure>

## Revoking access to the interface

_Note: Only an administrator has the possibility to cut access to the interface._

Follow these steps to cut access to the interface:

1/ Select the account to perform this action on from the drop down menu.

2/ Select the user(s) you wish to revoke access to.

3/ Select “Revoke access” and click “Apply”.

<figure><img src="../../.gitbook/assets/image (393).png" alt=""><figcaption></figcaption></figure>

## Reset user passwords

_Note: Only an administrator has the possibility to reset passwords._

Follow these steps to reset a password:

1/ Select the account to perform this action on from the drop down menu.

2/ Select the affected users.

3/ Select “Reset Password” from the drop down menu and click “Apply”.

<figure><img src="../../.gitbook/assets/image (394).png" alt=""><figcaption></figcaption></figure>



## Accessing users' information and seeing sites they have access to

_Note: Only an administrator has the possibility to consult users’ information and the sites they have access to._

Follow these steps to see users’ information and the list of sites they have access to:

1 ) Click the selected user in the column to the left

2 ) See the user’s information in the “User information” column on the right: the email address that is used to log in, the type of access, the company they work for, name/surname, position, mobile phone number, language, date and time of last connection.

3 ) To see what sites the user has access to, click the “Site(s) Access” button:

4 ) To manage the sites a given user has access to, choose the action to take and then click the “Apply” button.

5 ) Click “See Roles Details” to see what every type of role grants access to.

<figure><img src="../../.gitbook/assets/image (395).png" alt=""><figcaption></figcaption></figure>

## Managing custom user profiles

User profiles let you create custom rights working for one or more interface users.

The profile creation interface is accessible by Administrators only, from the “**Administration**” menu

### Creating a new profile:

To create a new profile, go to the “**Administration**”  > “**Profile management**” section and click the “Add Profile” button:

<figure><img src="../../.gitbook/assets/image (396).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (397).png" alt=""><figcaption></figcaption></figure>

1\) Enter the profile’s name.

2\) Select the default role from which you wish to create your custom profile (read only, technical, etc.).

3\) Select the site(s) you wish to create the profile for from those available in the list.

4\) If you wish to customize or limit access to certain containers, select the container’s name (only one at a time) from the list. Please note: if you select multiple sites this option will not be available.

5\) If you wish to customize or limit access to certain tags, select the tag’s name (only one at a time) from the list. Please note: if you select multiple sites this option will not be available.

6\) Select the product features you wish to add/revoke access to by clicking YES/NO.

7\) By clicking Yes/No at the top of the columns, changes will impact all of the column’s items.

When saving, the profile will be created on all selected sites.

<figure><img src="../../.gitbook/assets/image (398).png" alt=""><figcaption></figcaption></figure>

When the profile is created, you will be able to link it to all desired users from the “User management” interface. To learn more, please refer to these articles: “[Creating a new user](user-management.md#creating-a-new-user)” or “[Modifying user rights](user-management.md#modifying-user-rights)”.

### Modifying a profile:

To modify a profile, click the “pencil” icon from the column.

Please note: you cannot change default profiles (administrator, technical, marketing and read only), but you can see their settings.

You can make changes to all elements available when you created the profile, except the sites each profile is linked to. To copy a profile from one site to another, go to the “Copy Management” interface (please refer to the “[Copying custom user profiles](user-management.md#copying-custom-user-profiles)” article).

<figure><img src="../../.gitbook/assets/image (399).png" alt=""><figcaption></figcaption></figure>

Please note: Changes made to a profile will affect all sites said profile was created for.

You can also activate the double factor authentication (2FA) on this section, please refer to [<mark style="color:orange;">Double factor authentication (2FA)</mark>](broken-reference)

### Denying access to a specific container or tag

To deny access to a specific container, go to the user management interface.

The user’s role needs to be the “CUSTOM” type (please refer to the “[CREATING A NEW USER](user-management.md#creating-a-new-user)” article to learn how to give a custom-type role to new users; or to the [“MODIFYING USER RIGHTS”](user-management.md#modifying-user-rights) article to learn how to change a role type to custom).

1\) Click the pencil icon next to the profile name. The custom role configuration poppin appears.

<figure><img src="../../.gitbook/assets/image (400).png" alt=""><figcaption></figcaption></figure>

2\) Select the container you wish to deny access to.

3\) Click “NO” in the upper, right-hand side of the screen to turn all buttons to “NO” and save; the selected user no longer has access to the current container’s settings.

<figure><img src="../../.gitbook/assets/image (401).png" alt=""><figcaption></figcaption></figure>

A similar operation is required to prevent a user from having access to a specific tag. In the custom role configuration poppins, follow these steps :

1\) Select the tag you wish to deny access to

2\) Click “NO” in the upper, right-hand side of the screen to turn all buttons to “NO” and save; the selected user no longer has access to the current tag’s settings.

<figure><img src="../../.gitbook/assets/image (402).png" alt=""><figcaption></figcaption></figure>

### Modifying custom roles

Follow these steps to modify custom rights:

1/ Click the pencil icon next to “Custom”:

2/ Select the **Commanders Act** product you wish to revoke access to.

3\) Select the **container/tag** you wish to revoke or grant access to.

4\) Select the **predefined** role level to be used as starting point for customization (this is “**Read Only**” by default).

5\) Finally, select the features you wish to customize rights for in the products’ feature list. Click “YES/NO”

6\) Note: If you click Yes/No at the top of every column, the change will affect all features.

### Deleting a profile:

To delete a profile, click the trash bin icon from the “Actions” column.

Please note: you cannot delete default profiles (administrator, technical, marketing and read only).

The profile will be deleted and place in the trash. Access of all users linked to this profile will automatically change into “Read only”.

You can restore profiles at anytime by clicking the two arrows from the trash bin (3).

You can also delete the profile permanently by clicking the trash bin (4). Please note: this profile deletion will affect all sites said profile was created for. Access of all users linked to this profile will automatically change into “Read only”.

<figure><img src="../../.gitbook/assets/image (403).png" alt=""><figcaption></figcaption></figure>

## Copying custom user profiles

Please note: only administrators can copy custom user profiles (to learn more about user profiles, please refer to the Managing Custom User Profiles section).

Follow these steps to copy a user profile:

1\) – In the “Administration” section, click the “Copy Management” tab

2\) – Select “User Profiles” from the drop down menu

3\) – Select the site containing the profiles you wish to copy

4\) – Select the custom profiles you wish to copy

Please note: if you have created profiles with specific settings by container or tags, they will not appear in the list of available profiles to copy.

5\) – Select one or many target sites

6\) – Click “Copy”

<figure><img src="../../.gitbook/assets/image (405).png" alt=""><figcaption></figcaption></figure>
