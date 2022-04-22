---
description: >-
  You can easily integrate your Chatlayer bot to Freshdesk Messaging, also known
  as Freshchat, and offload customers from the bot to your customer support
  lines in Freshdesk
---

# Freshdesk Messaging App integration

When to use each one?

As a Channel:

If you’re using Freshdesk’s webchat, you can automate your customer support work with a conversational bot trained to reply your frequently asked questions, to open tickets, query your systems and give personalized answers to your customers who reached you via this channel.

As an Offloading provider:

Most of your interactions will probably be answered by the bot, lowering your time of response to the minimum, but your customer might ask things to which the bot hasn’t been trained yet, or talk about a more difficult or delicate subject. In these cases, you’ll probably want to offload this user from the bot to an agent in your customer support. One good practice is to always offer this as a fallback from your bot and communicate it to the customer, asking if they want to talk to an agent.

Here are the tutorials for these integrations.

**As a Channel:**

Create 1 group and 1 topic exclusive to the bot in Freshdesk Messaging

![](<../../.gitbook/assets/image (687) (2).png>)

Don’t include any agents in the exclusive bot group:

![](<../../.gitbook/assets/image (688).png>)

Assign the topic to the bot group

![](<../../.gitbook/assets/image (714).png>)

To use Freshdesk Messaging as a channel, click in Channels > App Integration Channel and follow these instructions:

![](<../../.gitbook/assets/image (682).png>)

Choose Freshdesk Messaging

![](<../../.gitbook/assets/image (684) (1).png>)

Either choose one of the connected accounts or connect new account:

![](<../../.gitbook/assets/image (703) (1).png>)

This is the pop up that will show when you choose to Connect new account:

![](<../../.gitbook/assets/image (716).png>)

Choose your region and paste the API Key that can be found in Freshdesk > Admin panel > API Tokens:

![](<../../.gitbook/assets/image (693) (1).png>)

![](<../../.gitbook/assets/image (705).png>)

![](<../../.gitbook/assets/image (707) (1).png>)

Once the account is connected, Copy the Custom Webhook URL to paste it on Freshdesk Messaging:

![](<../../.gitbook/assets/image (715).png>)

Go to Freshdesk Messaging > Admin > Webhook

![](<../../.gitbook/assets/image (685) (1).png>)

Paste the Custom Webhook URL copied from Chatlayer in the first field; copy the Authentication field, then paste it on Chatlayer:

![](<../../.gitbook/assets/image (711) (1).png>)

![](<../../.gitbook/assets/image (671) (1).png>)

To deploy the Freshdesk Messenger on your website, go to Freshdesk Messaging > Admin > Web Messenger:

![](<../../.gitbook/assets/image (677).png>)

In “Deploy”, copy the code snippet and paste it on your source code.

![](<../../.gitbook/assets/image (684) (1) (1).png>)

You’ll be able to see the webchat icon and interact with your Chatlayer bot:

![](<../../.gitbook/assets/image (695) (1).png>)![](<../../.gitbook/assets/image (699) (1).png>)

**As an Offloading provider:**

Make sure you followed all the previous steps to connect Freshdesk Messaging as a Channel.

Create a topics in Freshdesk Messaging:

![](<../../.gitbook/assets/image (712).png>)

![](<../../.gitbook/assets/image (708) (1) (1).png>)

You can assign different groups to different topics, depending on your customer support structure, skills and lines of attention.

![](<../../.gitbook/assets/image (704) (1).png>)

![](<../../.gitbook/assets/image (718) (1).png>)

Once you have all your topics and groups created, when you reach the points of your flow that will enable the customer to talk to an agent, create an Action dialog state and click on Send to Offload Provider:

![](<../../.gitbook/assets/image (680).png>)

Configure Freshdesk Messaging and the respective Topic and Group to which this Action should transfer the conversation.

You can create steps in your bot that will help you route the users to the most pertinent support line and offload them via each Action dialog state that will refer to those lines.

![](<../../.gitbook/assets/image (720).png>)

![](<../../.gitbook/assets/image (717).png>)

After the offloading is completed, this is how you’ll see the conversation in your Freshdesk Messaging team inbox:

![](<../../.gitbook/assets/image (721) (1).png>)

And that's it, your Freshdesk Messaging connection is set up and ready to go!
