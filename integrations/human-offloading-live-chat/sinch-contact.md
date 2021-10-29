# Sinch Contact Pro

It is now possible to connect your bot with Sinch Contact Pro, ensuring a seamless offloading experience from bot to human agent.

This article will explain how to set this up.

## Configuration in Sinch Contact Pro

* Log into your Sinch Contact Pro Domain
* Configure a new **agent **that will act as the bot
* Set-up a new **queue **specifically for chatbots&#x20;
* Open the configuration panel

![](<../../.gitbook/assets/image (582).png>)

* Click “Create new configuration” and go to “Common settings”&#x20;
* Find the Visitor ECF Server URL



![](<../../.gitbook/assets/image (578).png>)



* Copy this **URL**, you need it later for the Chatlayer configuration.



* Lastly, select your newly created Chatbot queue in the Sinch Contact Configuration Panel and click “Save”

![](<../../.gitbook/assets/image (580).png>)

## Configuration in Chatlayer

### Setting up channel

* Go to 'Channels' on the left hand side
* Click on the '+' sign in the 'Sinch Contact' row to see the pop-up below:

![](<../../.gitbook/assets/image (574).png>)

Looking at the URL you copied before, you can identify _Region _and _Tenant Name:_

https://prod-_region_._domain_**.**com/_tenantname_/visitor/ecfs

* Now fill in the following:
  * Your region  - https://prod-_**region**_._domain_**.**com/_tenantname_/visitor/ecfs
  * Tenant name -  https://prod-_region_._domain_**.**com/_**tenantname**_/visitor/ecfs

The other fields can be found back in Sinch Contact Pro:

Username and password: fill these fields in from the newly created virtual agent&#x20;

* Now click 'Continue' to save your configuration&#x20;

> The Cloud Configuration has following regions:
>
> * **na**: 'login-na-w2.cc.sinch.com'
> * **eu**: 'login-eu-c1.cc.sinch.com'
> * &#x20;**au**: 'login-au-s2.cc.sinch.com'

{% hint style="info" %}
Do you have an On Premise environment of Sinch Contact Pro? Toggle 'Is On Premise' and fill out the following: For the URL

[_https://mywebsite.com/integrations/sinch-contact/tenantname_](https://mywebsite.com/integrations/sinch-contact/%3Ctenantname%3E)__

&#x20;The **host **is 'mywebsite.com', and the **tenant name** will be 'integrations/sinch-contact/tenantname'
{% endhint %}

### Setting up offload action

* Add an “Action” bot dialog to your flow that contains a “Send to offload provider” plugin (for example, after “Not understood”).&#x20;
* Select Sinch Contact in that plugin and the queue you want to offload to.

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

And there you go, your Sinch Contact offloading is all set up!

