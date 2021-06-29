# Sinch Contact

It is now also possible to connect your bot with Sinch Contact, ensuring a seamless offloading experience from bot to human agent.

This article will explain how to set this up:

## Configuration in Sinch Contact

* Log into your Sinch Contact Domain
* Configure a new **agent** that will act as the bot
* Set-up a new **queue** specifically for chatbots 
* Open the configuration panel

![](../../.gitbook/assets/image%20%28582%29.png)

* Click “Create new configuration” and go to “Common settings” 
* Find the Visitor ECF Server URL



![](../../.gitbook/assets/image%20%28578%29.png)



* Copy this **URL**, you need it later for the Chatlayer configuration.



* Lastly, select your newly created Chatbot queue in the Sinch Contact Configuration Panel and click “Save”

![](../../.gitbook/assets/image%20%28580%29.png)

## Configuration in Chatlayer

### Setting up channel

* Go to 'Channels' on the left hand side
* Click on the '+' sign in the 'Sinch Contact' row to see the pop-up below:

![](../../.gitbook/assets/image%20%28574%29.png)

* Toggle 'Is On Premise' when your Sinch Contact environment is on Premise. Fill in 

Looking at the URL you copied before, you can identify _Region_ and _Tenant Name:_

https://prod-_region_._domain_**.**com/_tenantname_/visitor/ecfs

* Now fill in the following:
  * Your region  - https://prod-_**region**_._domain_**.**com/_tenantname_/visitor/ecfs
  * Tenant name -  https://prod-_region_._domain_**.**com/_**tenantname**_/visitor/ecfs

The other fields can be found back in Sinch Contact:

* Username and password: fill these fields in from the newly created virtual agent 
* Now click 'Continue' to save your configuration 

### Setting up offload action

* Add an “Action” bot dialog to your flow that contains a “Send to offload provider” plugin \(for example, after “Not understood”\). 
* Select Sinch Contact in that plugin and the queue you want to offload to.

![](../../.gitbook/assets/image%20%28573%29.png)



## Final steps

* Open the page where you’ve configured your Sinch Contact Widget
* Fill in your contact details, select the “Chatlayer Agents” queue and start the conversation

![](../../.gitbook/assets/image%20%28579%29.png)



![](../../.gitbook/assets/image%20%28575%29.png)

After being transferred to an agent, open the right queue and take over the conversation:

![](../../.gitbook/assets/image%20%28581%29.png)

And there you go, your Sinch Contact offloading is all set up!



