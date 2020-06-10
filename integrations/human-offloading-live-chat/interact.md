---
description: Learn how to configure Interact with your chatbot
---

# \#Interact

Proximus \#Interact is a live chat solution that allows you to manage replies to your customers on all your social networks in one place. Read more [here](https://www.proximus.be/en/id_cl_customer_relationships/companies-and-public-sector/it-services/customer-relationships.html).

## Configure \#Interact offloading

Create an access token in \#Interact by going to Settings &gt; Tokens &gt; Add token.  The access token will automatically be copied to your clipboard.

![](../../.gitbook/assets/image%20%2875%29.png)

Now head over to your bot's offloading settings. In Chatlayer, go to Settings &gt; Offloading and create a new \#Interact offloading provider. Paste the newly created access token in the configuration modal.

![](../../.gitbook/assets/image%20%2861%29.png)

## Add the Chatlayer access token to \#Interact

Create a new Chatlayer access token. \#Interact will use this token to safely communicate with your Chatlayer bot.

![](../../.gitbook/assets/image%20%28100%29.png)



![](../../.gitbook/assets/image%20%28114%29.png)

Copy the newly created access token and paste it in Interact under Settings &gt; Chatbot &gt; Connect Chatlayer

![](../../.gitbook/assets/image%20%2883%29.png)

## Offload a user to \#Interact

To have your user transferred to a live agent in \#Interact, create an action at the point in the flow where you want your user to be handed over.

![](../../.gitbook/assets/image%20%28159%29.png)

Add the action "Send to offload provider" to your bot dialog and configure it with the correct settings for \#Interact.

![](../../.gitbook/assets/image%20%2882%29.png)

Once a user reaches this part of the conversation, the offload towards \#Interact will be triggered. The bot will automatically be paused when a user reaches this action. When the agent closes the conversation, the bot will be resumed. 

