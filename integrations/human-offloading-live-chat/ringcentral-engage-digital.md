---
description: >-
  Learn how to connect your Chatlayer.ai bot to the RingCentral Engage Digital
  human handover platform
---

# RingCentral Engage Digital

RingCentral Engage Digital \(formerly known as Dimelo\) is a platform to manage every digital interaction with your customers. Read more [here](https://www.ringcentral.com/digital-customer-engagement.html).

## Connecting RingCentral Engage Digital to Chatlayer.ai

If not yet present in the flow, configure two dialogs for ‘contact center opened’ and ‘contact center closed’ \(naming is free\). No need to further configure them at this point. Exact use of these dialogs will be detailed later in the document, but it’s important that they already exist, as you will need to refer to them during the setup wizard.

In the Chatlayer.ai platform, go to Settings -&gt; Offloading

Click the "+" sign next to RingCentral Engage Digital

![](../../.gitbook/assets/image%20%28118%29.png)

Enter the API URL of your RingCentral Engage Digital instance. Typically, this URL contains .api after the name of your instance, for example: https://chatlayer.api.engagement.dimelo.com/

Inside of RingCentral Engage Digital, go to Admin&gt;Advanced Settings&gt;API access tokens

![](../../.gitbook/assets/image%20%28217%29.png)

  
Create a new access token in RingCentral Engage Digital by clicking on the + icon. Paste the token inside of the Chatlayer.ai configuration screen.

The next step is to set up a webhook so Chatlayer can receive events from RingCentral Engage Digital. Go to RingCentral Engage Digital, Admin&gt;Advanced settings&gt;Webhooks. Select the created access token and toggle ‘Active’ and paste the URL from the wizard.

Select the right source\(s\) for this webhook. Select the 4 events indicated in the Chatlayer.ai configuration screen.

Select the two dialogs \(created before\) that need to be launched in case of contact center opened/closed. 

Click "Save" to complete the set-up

RingCentral Engage Digital is now set up as an offload provider and Enabled by default. Use the slider to \(temporarily\) disable the offload if necessary.

## Sending a user to RingCentral Engage Digital

To have your user transferred to a live agent in RingCentral Engage Digital, create an action at the point in the flow where you want your user to be handed over.

![](../../.gitbook/assets/image%20%28159%29.png)

Add the action "Send to offload provider" to your bot dialog and configure it with the correct settings for RingCentral Engage Digital.

![](../../.gitbook/assets/image%20%2882%29.png)

Once a user reaches this part of the conversation, the offload towards RingCentral Engage Digital will be triggered. The bot will automatically be paused when a user reaches this action. When the agent closes the conversation, the bot will be resumed. 

