---
description: Learn how to configure and use Zendesk Chat on Chatlayer
---

# Zendesk Chat

Zendesk is a service-first CRM company that builds software designed to improve customer relationships.

## Configure Zendesk 

In Zendesk, your Chatlayer.ai bot will be a separate agent that will handle incoming messages for its own  department. The Agent account should not be accessed by live agents, as this may disrupt the chatbot. We provide the necessary action dialogs to transfer the conversation to a department with live agents of your choosing.

### Create a new agent for the chatbot

First off, create the chatbot agent in Zendesk Chat by going to Settings &gt; Agents &gt; Add Agent. 

![](../../.gitbook/assets/image%20%28277%29.png)

### Create a department for the chatbot

Create a new department for the chatbot by going to Settings &gt; Departments &gt; Add Department.  Pick a recognizable name and **add the chatbot agent as the Department Agent.**

![](../../.gitbook/assets/image%20%28269%29.png)

### Configure your Zendesk Chat Widget

You should now create or adjust your Zendesk Chat Widget to automatically connect to your newly configured Chatbot department. To do so, in Zendesk Chat, go to Settings &gt; Widget and copy the code under "Embed Web Widget".

![](../../.gitbook/assets/image%20%28280%29.png)

Here's an example of how you could adjust the Widget to automatically connect to the previously created **Chatbot** department:

```markup
<!-- Start of Zendesk Widget script -->
<script
  id="ze-snippet"
  src="https://static.zdassets.com/ekr/snippet.js?key=abc123
></script>
<script>
  window.zESettings = {
    webWidget: {
      chat: {
        departments: {
          select: "Chatbot"
        }
      }
    }
  };
</script>
<!-- End of chatlayerai Zendesk Widget script -->
```

More information on this topic can be found in the [Zendesk Chat documentation](https://developer.zendesk.com/embeddables/docs/widget/settings#departments).

## Configure your Zendesk Chat channel

In Chatlayer.ai, go to the Channels overview to start setting up your Zendesk Chat integration. Start the channel creation by clicking the + icon.

#### Finding your subdomain

You will be prompted to enter your subdomain for **zendesk.com**. 

![](../../.gitbook/assets/image%20%28270%29.png)

When using Zendesk in a webbrowser, the subdomain is the first part of your Zendesk URLs. The example image below shows the subdomain "chatlayerai".

![](../../.gitbook/assets/image%20%28272%29.png)

#### Authorize Chatlayer

When prompted to authorize Zendesk, log in to the Zendesk Agent account that should act as the bot agent. This is the agent you created earlier.

### Start using your bot

You can now talk to your bot through the Zendesk Chat widget. Every incoming message from a visitor will be answered by the bot. 

### Synchronized session variables

It's possible for the chatbot to collect information about the user. The following session variables will automatically be synchronized to your visitor info in Zendesk:

* zendeskChat.email
* zendeskChat.displayName
* zendeskChat.phone
* zendeskChat.notes
* zendeskChat.tags\[0\] \(array\)

![](../../.gitbook/assets/image%20%28271%29.png)

## Configure offloading

To transfer the conversation from the chatbot to a different department, you can create an Action dialog containing an Offload setting. Configure the Zendesk Chat offload provider and the department to which you want to offload the conversation.

![](../../.gitbook/assets/image%20%28274%29.png)

Once this Action is triggered and the chosen department has at least one agent online, the chatbot will be paused and the user will be transferred to that department. The "Offloading Closed" bot dialog will be triggered should no-one in that department be online.

## Going Live

To go live, you should configure a Zendesk channel for the Live environment on [cms.chatlayer.ai](https://cms.chatlayer.ai). We recommend creating a seperate Bot Agent, Department and Widget connected to that Department for both your Draft and Live environments. This assures no collisions will happen between your bot's versions.

