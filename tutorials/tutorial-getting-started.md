# Getting started

This tutorial will show you how to set up a new project and create a chatbot from scratch.

Are you working on an existing project? Then you don't need to set up a new one. Feel free to skip ahead to the next tutorial.

## Getting started with chatbots

Never built a chatbot before? This short tutorial video explains you the key steps to creating a chatbot   
and the terminology used on the Chatlayer.ai platform. 

{% embed url="https://www.youtube.com/watch?v=QYLPu9Z1V08&list=PLDWxiKsSIVPJl0zssvGATGsib6Luj0WSH" %}

## Creating a new bot

For this tutorial, we’ll create a conversational interface called Choo-choo: a digital assistant to help people book train tickets. 

To get started, please make sure you have valid log-in credentials to access the Chatlayer.ai platform.

{% hint style="info" %}
If you don't have log-in credentials yet, please request them [here](https://www.chatlayer.ai/contact).
{% endhint %}

* Log in using your credentials on [https://cms.staging.chatlayer.ai/](https://cms.staging.chatlayer.ai/)
* To start, click the `+ Add bot` button to create a new bot

![](../.gitbook/assets/image%20%28196%29.png)

* Enter `Choo Choo (your first name)` as the name of your bot
* Choose `English` as the primary language. This is the language your bot will use
* \(Optional: you can add other languages if you want a multilingual bot\)
* Click `Create` to create your new bot

![](../.gitbook/assets/createbot.png)

{% hint style="warning" %}
Be aware that you can't add additional languages once the bot is created.   
Contact our support team [here](https://chatlayer.zendesk.com/hc/en-us) if you want to add an additional language to an existing bot.
{% endhint %}

In the menu on the left, click on `Bot dialogs`. Enter the `General` flow by clicking the flow icon 

{% hint style="info" %}
Flows are a way to group your bot dialogs. You will learn more about this in a later tutorial.
{% endhint %}

![](../.gitbook/assets/image%20%28186%29.png)

After entering the flow, you will see an empty chatbot flow containing only the standard predefined dialog states. Your screen should look something like this:

![](../.gitbook/assets/image%20%28246%29.png)

### Adding a greeting

The first thing we need to do is create a greeting. Greetings allow your bot to introduce itself and help users understand its functionalities and personality. Greetings are an important way to set the proper expectations of a bot.

Our Choo Choo bot will start each conversation. You can edit this greeting in the `introduction` bot dialog.

{% hint style="info" %}
**What is a bot dialog?** A bot dialog is a something that the bot will do or say when triggered by a user. This can be anything from a message to a user, to making a connection to an external system, to jumping to another part of the conversation.
{% endhint %}

* Zoom in \(or out\) by use the scrolling wheel. Click and drag to move through the dialog tree.
* Click on the edit icon of the`introduction` bot dialog

![](../.gitbook/assets/image%20%28143%29.png)

Chatlayer.ai supports multiple content types. Depending on the channel your bot will use \(Facebook, Slack, Skype, Google Home, ...\) these will be rendered slightly differently. Since this is our first bot and our first message, let's start with a simple text message:

* Delete the predefined greeting message by clicking on the Trash icon.

> Hello. Please configure the introduction dialog state with a meaningful message.

* Replace it with the following text:

> Hello there! My name is Choo Choo, a digital assistant that will keep you on track.

* Click on `Text`  in the section 'Add bot message' to add a second message and enter the following text:

> How can I help you today?

The result will be:

![](../.gitbook/assets/bot-message.png)

Just like in normal conversations, your users won't like it when your bot always replies with the exact same messages. That's why Chatlayer.ai supports random messages. In a Text Message block, you can add multiple alternatives to the same message. Chatlayer.ai will randomly pick one of these messages, making your dialogue feel more natural and human.

* Just below 'How can I help you today?', click on  `Add random message` and enter the following text:

> What can I do for you?

Tip: you can add as many random messages as you like. 

![](../.gitbook/assets/image%20%2891%29.png)

Click on `Save` to save all the changes you made in the `introduction` bot dialog.

### Testing your greeting

Time to check if we configured everything correctly. To do so, it's not necessary to publish your bot to a channel like Facebook Messenger or Slack. You can see how your bot replies by using our built-in emulator.

* Click on the Emulator icon in the lower right corner to test your bot.

![](../.gitbook/assets/image%20%2876%29.png)

If you have configured everything correctly, Choo Choo will now reply with the right messages. You can ignore the debug button for now, but this will be useful later when you want to debug more complicated flows.

![](../.gitbook/assets/image%20%28228%29.png)

{% hint style="info" %}
In the [next tutorial](tutorial-adding-content.md), you will learn how to configure some questions the user can ask the bot.
{% endhint %}

