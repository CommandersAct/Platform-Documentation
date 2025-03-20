# Branches

## Introducing the new "Branches" feature

Are you ready to take your TMS experience to the next level? We are thrilled to introduce our latest feature: **Branches**. This powerful tool is designed to elevate your team’s efficiency, allowing multiple users to work simultaneously on the same project without stepping on each other's toes. Imagine a workspace where you can confidently make changes, test them in isolation, and merge them seamlessly—all while keeping your Main project intact. Let’s dive into what makes this feature a game-changer.

## What is "Branches"?

Branches allow you to create a separate, partitioned work environment—a safe space where your work is your own. You can make changes without worrying about interrupting your colleagues’ progress. When you're ready, simply merge your work back into the Main project with confidence, knowing that everything aligns perfectly.

### **Key Benefits**

* **Work independently:** No more waiting for colleagues to finish their tasks. With Branches, everyone can contribute simultaneously without conflicts.
* **Reduce errors:** By isolating changes, you can avoid the dreaded “unfinished work” being deployed to production. Test and validate your changes in a secure environment before merging.
* **Streamlined merging:** Our intuitive interface makes merging a breeze. View changes side-by-side with our diff checker, ensuring nothing slips through the cracks.

### :heart: Why you’ll love Branches :heart:&#x20;

**Say goodbye to workflow interruptions!**

Previously, if two users worked on the same account, their changes would overlap, leading to potential conflicts during container generation. This often resulted in errors that stalled the deployment process, or worse—unfinished work going live. With Branches, you’ll experience a smoother, more controlled workflow. Your team can now focus on what they do best, without the hassle of managing conflicting changes.

### **A seamless User Experience**

* **Visual indicators:** It’s easy to know where you are. When you’re working on the Main (your actual web container), all menu elements are cherry red. \
  Switch to a Branch, and everything turns blue, signaling that you’re in a safe zone to make changes.
* **Effortless Branch creation:** Whether you’re starting a new project, creating a new Branch is just a click away. Our intuitive panel guides you through the process, from naming your Branch to diving straight into editing.
* **Real-time notifications:** Stay updated with any changes made into the Main while you’re working on a Branch. You’ll receive a prompt with options to update your Branch or continue working—keeping you in control at all times.

### Glossary

* **Main:** your usual container, considered as "parent" in a Branch context
* **Branch:** a duplication of your Main to work without impacting your Main configuration
* **Merge:** action to bring the modifications from your Branch live in your Main container

## How it works ?

### **Branch Creation**&#x20;

To open the Branch creation UI use the button in the breadcrumb menu (identified as "Main" when you are on your regular container, or by the Branch name if your are in Branch context).  \
The list of your branches will appears. Click on "Create new branch". \
Just define a Branch name, you can also add a description if needed, \
You can create up to 5 Branches for each container!

<figure><img src="../../../../../../../.gitbook/assets/image (538).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../../.gitbook/assets/image (539).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../../.gitbook/assets/Capture d&#x27;écran 2024-11-21 180202.jpg" alt=""><figcaption></figcaption></figure>

On save, you will redirected in your new Branch environment

Once your Branch is created, all changes you make are isolated to this environment. The blue color of the navigation elements shows you are in a Branch.&#x20;

<figure><img src="../../../../../../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

You can edit or modify any of the elements as if you were in a normal container.

{% hint style="warning" %}
**Limitations**

-Rules cannot be permanently deleted in a Branch, only "Archive" action is possible.\
-Old events formats (deprecated tc\_events) cannot be deleted in a Branch

Be careful on your WebDatalayer modification(s), it may impact all your site

If you create an internalvar in your Branch, you must link it with the Main as well, because internalvars aren't merged
{% endhint %}

### **Branch Comparison with the Main**&#x20;

At any time you can have clear view of the work done on each Branch.\
Simply click on the link "See changes"

<figure><img src="../../../../../../../.gitbook/assets/image (556).png" alt=""><figcaption></figcaption></figure>

The "Comparison" pop in will appears:

<figure><img src="../../../../../../../.gitbook/assets/image (558).png" alt=""><figcaption></figcaption></figure>

You can unfold elements to get details

<figure><img src="../../../../../../../.gitbook/assets/image (537).png" alt=""><figcaption></figcaption></figure>

### **Existing Branch Edition**&#x20;

To access an existing Branch, click on "pen" icon.\
**This pop in is also useful to go back to your Main container.**

<figure><img src="../../../../../../../.gitbook/assets/image (559).png" alt=""><figcaption></figcaption></figure>

Edit/modify any elements as if you where in a regular container.

### Branch Update

If your Branch is not up to date with the newest Main changes, you will see this warning message, inviting you to update your Branch

<figure><img src="../../../../../../../.gitbook/assets/image (540).png" alt=""><figcaption></figcaption></figure>

On click, the pop in "Update" will be displayed, a diff checker.\
You are allowed to keep or discard the changes. \
The checked items will be bring into your Branch.\
If you don't wish to update your Branch now, then click on cancel.

<figure><img src="../../../../../../../.gitbook/assets/image (541).png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
Be careful on items with the items with label "conflict"\
It means there is modification(s) on the Main and on the Branch too

By default they are unchecked. Take time to compare and choose if you wish to keep the modification from the Branch or from the Main
{% endhint %}

<figure><img src="../../../../../../../.gitbook/assets/image (542).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
We recommend to bring all the changes from the Main into your Branch. If you refuse to update some elements, you may impact the Main container on merging.&#x20;
{% endhint %}

### Branch QA & Test

You can generate your Branch as a regular container.

Once your Branch has been merged, you can do your Quality Assurance by 2 different ways: Deploy your Branch in your UAT environment, or use our Chrome Plugin "Commanders Act Tag Assistant"

#### Test on your UAT environment

When you’re ready, deploy your changes in your UAT environment, ensuring everything works flawlessly before merging.

There's a main difference for Branches containers at the deloy step: deployment on Production environment isn't allowed.\
That's why the deploy step has been renamed as "QA - Merge" in Branch context!

The UAT deployment option will push your Branch version on the UAT URL of the Main container.

It means that you can test your Branch directly on your UAT site without IT intervention.

<figure><img src="../../../../../../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### Test with our plugin

Our Commanders Act Assistant is compatible with Branches!

Download it from Chrome Extension Store, once it is installed on your browser, you can use the button "preview" to test your Branch on your website.

<figure><img src="../../../../../../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../../.gitbook/assets/image (3) (1) (1).png" alt="" width="488"><figcaption></figcaption></figure>

For a detailed documentation about our plugin, pease read the following page

### Merge Branch

Ready to bring your changes from Branch into the Main? Use our “Merge” feature, where you can review the differences, see a detailed comparison, and complete the merge effortlessly.

<figure><img src="../../../../../../../.gitbook/assets/image (544).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Merge doesn't consider the generation versions. The UI for merging will ever display the latest updates of your Branch
{% endhint %}

<figure><img src="../../../../../../../.gitbook/assets/image (546).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
If your Branch is not up to date, Merge will be blocked.
{% endhint %}

Take the time to update your Branch now with the latest Main changes!

<figure><img src="../../../../../../../.gitbook/assets/image (543).png" alt=""><figcaption></figcaption></figure>

### After merge

Once you merged your Branch, **the Branch will be deleted** and you will be redirected to your Main

All modifications from Branches are now logged in your Main with \[Branch\*] prefix

<figure><img src="../../../../../../../.gitbook/assets/image (547).png" alt=""><figcaption></figcaption></figure>

At any time after merge, you can view all modifications logs from the merged Branch on your Main Modification History.

{% hint style="success" %}
Don't forget to re-generate your Main container to bring your changes in Production!
{% endhint %}

## Custom User Rights

The native roles 'Administrator', 'Technical' and 'Marketing' are allowed to create, edit and merge branches.&#x20;

If you want to manage these access rights more closely, you can use the dedicated rights in Profile Management, Custom Profile.

<figure><img src="../../../../../../../.gitbook/assets/image (580).png" alt=""><figcaption></figcaption></figure>

## Looking ahead

**Future-Proof Your Workflow**

Although direct production deployment from a Branch is not available, our new QA plugin (currently under development), will offer you another way of testing your Branches, even in a production environment.
