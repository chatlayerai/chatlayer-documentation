# Sinch Contact Pro

It is now possible to connect your bot with Sinch Contact Pro and ensure a seamless offloading experience from bot to human agent.

Keep reading for a step-by-step guide on how to set this up!

## 1 – Configuration in Sinch Contact Pro

* Log into your Sinch Contact Pro Domain
* Configure a new **agent** that will act as the bot
* Set-up a new **queue** specifically for chatbots&#x20;
* Open the configuration panel

![](<../../.gitbook/assets/image (582).png>)

* Click “Create new configuration” and go to “Common settings”&#x20;
* Find the Visitor ECF Server URL

![](<../../.gitbook/assets/image (578).png>)

* Copy this **URL**, you need it later for the Chatlayer configuration
* Lastly, select your newly created Chatbot queue in the Sinch Contact Configuration Panel and click “Save”&#x20;

![](<../../.gitbook/assets/image (672) (1) (1) (1) (1) (1).png>)

## 2 – Configuration in Chatlayer

### Setting up the channel

* Go to 'Channels' on the left hand side
* Click on the '+' sign in the 'Sinch Contact' row to see the pop-up below:

![](<../../.gitbook/assets/image (693).png>)

Looking at the URL you copied before, you can identify _Region_ and _Tenant Name:_

https://prod-_**region**_._domain_**.**com/_**tenantname**_/visitor/ecfs

* Now fill in the following:
  * Your region  - https://prod-_**region**_._domain_**.**com/_tenantname_/visitor/ecfs
  * Tenant name -  https://prod-_region_._domain_**.**com/_**tenantname**_/visitor/ecfs

The other fields can be found in Sinch Contact Pro:

* Username and password: fill these fields in from the newly created virtual agent&#x20;

Now click 'Continue' to save your configuration&#x20;

> The Cloud Configuration has following regions:
>
> * **na**: 'login-na-w2.cc.sinch.com'
> * **eu**: 'login-eu-c1.cc.sinch.com'
> * **au**: 'login-au-s2.cc.sinch.com'
> * **af**: 'login-af-s1.cc.sinch.com'

{% hint style="info" %}
Do you have an On Premise environment of Sinch Contact Pro? Toggle 'Is On Premise' and fill out the following: For the URL

[_https://mywebsite.com/integrations/sinch-contact/tenantname_](https://mywebsite.com/integrations/sinch-contact/%3Ctenantname%3E)__

&#x20;The **host** is 'mywebsite.com', and the **tenant name** will be 'integrations/sinch-contact/tenantname'
{% endhint %}

### Setting up offload action

* Add an “Action” bot dialog to your flow that contains a “Send to offload provider” plugin (for example, after “Not understood”)
* Select Sinch Contact in that plugin and the queue you want to offload to

![](<../../.gitbook/assets/image (573).png>)

### Sharing variables to Sinch Contact Pro

Chatlayer shares the following information to Sinch Contact Pro:

* **First Name**: `sinchContactPro.firstName` OR `internal.user.firstName`
* **Last Name**: `sinchContactPro.lastName` OR `internal.user.lastName`
* **Phone** **Number**: `sinchContactPro.phoneNumber`
* **Email**: `sinchContactPro.email`

It is recommended to fill in the above listed variables, so the agent in Sinch Contact Pro knows who they are talking to.

You may want to pass additional information about the user to Sinch Contact Pro, next to the  above fields. To do this, you can declare additional session variables with the following format: `sinchContactPro.customFields`. All these will be added as `attached data` fields in Sinch Contact Pro.&#x20;

For example, to add the user's location as a custom field, you would adjust your bot's flow to ask the users location and store the answer as a variable under `sinchContactPro.customFields.location`

## Final steps

{% hint style="info" %}
In the example below, we'll use the Sinch Contact Pro web widget as a channel. You can also use channels like WhatsApp, Facebook Messenger, or the Chatlayer web widget.
{% endhint %}

* Open the page where you’ve configured your Sinch Contact Pro Widget
* Fill in your contact details, select the “Chatlayer Agents” queue and start the conversation

![](<../../.gitbook/assets/image (579).png>)



![](<../../.gitbook/assets/image (575).png>)

After being transferred to an agent, open the right queue and take over the conversation:

![](<../../.gitbook/assets/image (581).png>)

## Restart bot after offloading is complete

This only works if you are using channels connected to your bot that are different from Sinch Contact Pro web [widget](sinch-contact.md#final-steps), only works in [this ](sinch-contact.md#setting-up-channel)setting.

The returning part of your bot flow after offloading is complete will look like this:

![](<../../.gitbook/assets/image (687) (1) (1).png>)

Three things need to be set up for this use case to work:

1. The variables that are going to identify the bot conversation and offloaded conversation are still active or paused need to be created:

In this example, we created `internal.isPaused` toidentify when the bot is paused and internal.offload to identify when the&#x20;

![](<../../.gitbook/assets/image (706) (1).png>)

2\. The bot needs to identify that the offloading isn't active anymore:&#x20;

For that, we built a Go To bot dialog with the conditions: if the variable `internal.offload` does not exist, trigger the desired bot dialog to get user feedback, in the example below we named it "Feedback flow start", otherwise go to an empty bot dialog, "do nothing" as we named it in our example, because the offloaded conversation is still active.

![](<../../.gitbook/assets/image (698) (1).png>)

3\. The bot needs to identify when the offloaded conversation is no longer active

An event needs to be created by accessing the tab Events from the left-side menu, under the Bot Dialogs section. That event that will be triggered when the offloading variable is paused when the bot dialog from step 1 is visited.



![](<../../.gitbook/assets/image (719).png>)

Once the offloaded conversation is ended by the agent, like in the screenshot below, the bot will be able to identify that `internal.offload` is inexistent.

![](<../../.gitbook/assets/image (722) (1) (1).png>)

Ant the bot will restart the conversation, following the first condition of the Go To bot dialog

![](<../../.gitbook/assets/image (708) (1).png>)

And there you go, your Sinch Contact Pro offloading is all set up!

