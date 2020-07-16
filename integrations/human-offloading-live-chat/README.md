# Human handover & live chat

Bots are great as a first line of defense. However, they are not \(yet\) as smart as a real human agent worker. From our experience at Chatlayer, we have noticed that hybrid forms of chatbots in combination with live agents offer the best user experience. This is called human handover or offloading.

## When is a user handed over to a live agent?

You can configure when a user is transferred to a live agent yourself by adding a plugin called 'Send to offload provider'. When that plugin is reached, the user status will change to 'Offloaded'. The user will be transferred to one of the three predefined bot dialogs.

As long as a live agent has not taken over the chat session, the bot will remain active so the user can ask other questions and keep interacting with the bot. The live agent will have a full transcript of the chat session with the user available.

### Typical patterns that lead to a handover

Human handover, or disabling the bot and allowing a human agent to take over can happen in four situations:

* User explicitly requests talking to a live agent. E.g. by typing “I want to speak to a real agent”. This can be captured in a separate intent and bot dialog, that refers to the human handover platform.
* User reaches the ‘not understood’ bot dialog. This happens when the NLP has low confidence in the understanding of the user’s messages. This can be configured to trigger the bot to ask a question “Do you want to talk to a human agent?”
* User reaches a point in the conversation that is not supported yet. For example, this could be at the end of the ‘send paper to a new address’ conversation flow. The bot will be used to collect the necessary information and when reaching the end of the flow will be connected to a live agent for manual input in the backend system. This is already way more efficient than having the user collect all necessary information.
* An option “Request live agent” can be added in the hamburger \(overflow\) menu in both the web widget and Facebook messenger channel.

## Configuring human handover

In the Settings menu under Offloading you can set-up a new offloading provider. Chatlayer supports multiple market-leading offloading providers.

The specific configuration will depend on the offloading provider you want to integrate with. Currently we integrate with the most popular offloading providers of our customers.

![](../../.gitbook/assets/image%20%28214%29.png)

{% page-ref page="intercom-integration.md" %}

{% page-ref page="interact.md" %}

{% page-ref page="helpscout.md" %}

{% page-ref page="genesys-purecloud.md" %}

{% page-ref page="ringcentral-engage-digital.md" %}

{% page-ref page="zendesk-chat.md" %}

{% page-ref page="sparkcentral-beta.md" %}

If you want to connect to a platform that's not in this list, [get in touch](../../support/get-in-touch.md)!

## Human handover bot dialogs

There are three predefined dialog states specifically for human offloading.

* **Offloading disabled**: human offloading can temporarily be disabled, e.g. due to peak an incident within the contact center. When this happens, the message in this bot dialog will be displayed.
* **Offloading closed**: message to be displayed when a user reaches the 'offloaded' state but the live chat is not open \(configurable: typically at night, lunch or weekends\)
* **Offloading opened**: temporary waiting message that is displayed once the user has reached the 'offloaded' state. Typically a message similar to "Please wait for a couple of minutes while a live agent connects to this chat session."

## Human handover comparison

Different live chat platforms support different feature sets. Below you can find a list of what's supported by which provider.

|  | Zendesk | Sparkcentral | Genesys Cloud | \#Interact | Help Scout | Intercom |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Chatlayer.ai widget & channel configuration |  |  | ✅ | \(✅\) | ✅ |  |
| Provider widget & channel configuration | ✅ | ✅ |  | ✅ |  | ✅ |
| Rich templates \(buttons, carousels, ...\) | ✅ |  | ✅ | ✅ | ✅ |  |
| Bot history visible to agent | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Agent conversations in Chatlayer.ai history |  |  | ✅ |  | ✅ |  |

