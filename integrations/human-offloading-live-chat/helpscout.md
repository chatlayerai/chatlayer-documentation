---
description: Learn how to configure Help Scout on you Chatlayer.ai chatbot
---

# Help Scout

Help Scout is a tool that offers simple service software. Read more [here](https://www.helpscout.com/).

## Help Scout Offloading

### Configure the offloading provider

In the Chatlayer CMS, go to Settings &gt; Offloading and create a Help Scout integration

You'll be prompted to authorize Chatlayer in your Help Scout account

![](../../.gitbook/assets/image%20%28266%29.png)

![](../../.gitbook/assets/image%20%28136%29.png)



## Sending a user to Help Scout

To have your user transferred to a live agent in Help Scout, create an action at the point in the flow where you want your user to be handed over.

![](../../.gitbook/assets/image%20%28159%29.png)

Add the action "Send to offload provider" to your bot dialog and configure it with the correct settings for Help Scout.

![](../../.gitbook/assets/image%20%2882%29.png)

Once a user reaches this part of the conversation, the offload towards Help Scout will be triggered. The bot will automatically be paused when a user reaches this action. When the agent closes the conversation, the bot will be resumed. 

