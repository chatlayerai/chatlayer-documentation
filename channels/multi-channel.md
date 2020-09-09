# Channels

A channel is a way to expose the chatbot you've built in Chatlayer towards users of the bot. The channel you should choose for your bot depends on where the target audience for your bot likes to talk.

For example, if you're building an internal HR bot, it's best to put it on the company HR portal through a web widget, or on Facebook Workplace. However, if you're building a bot that's targeted towards a young demographic, Facebook Messenger might be a better way to go.

Publishing your bot on a channel is quite easy, as you can read in our channel guides:

{% page-ref page="facebook/" %}

{% page-ref page="whatsapp.md" %}

{% page-ref page="google-assistant.md" %}

{% page-ref page="webwidget.md" %}

{% page-ref page="phone-and-voice.md" %}

{% page-ref page="workplace-from-facebook.md" %}

{% page-ref page="../chatlayer-api/webhook-api.md" %}

{% page-ref page="sinch-conversation-api-beta.md" %}

## Multi-channel

If you want to have your users receive a different flow based on the channel they are on you can use Chatlayer.ai's multi-channel functionality. To do this, add a [Go To](../bot-answers/dialog-state/plugins.md) at the point in the flow you want to diverge based on channel.

In this Go To, guide the user based on the botType variable, which contains the channel variable. For example:

![](../.gitbook/assets/image%20%2824%29.png)

The values for botType correspond to the channel names:

* Facebook Messenger: facebook
* Google Home: google
* Chat widget: web
* Facebook Workplace: facebookWorkplace
* Phone: voice
* All channels managed through the Sinch Conversation API: sinchConversationAPI

## Channel comparison

The table below gives an overview of which features are available in which channels. If a feature is not listed below, it's available for all channels.

|  | Chat Widget | Facebook Messenger | Facebook Workplace | WhatsApp | Webhook  API | Zendesk |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Text messages | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Buttons | ✅ | ✅ | ✅ |  | ✅ | ✅ |
| Quick replies | ✅ | ✅ | ✅ |  | ✅ | ✅ |
| Carousel | ✅ | ✅ | ✅ |  | ✅ | ✅ |
| List | ✅ | ✅ | ✅ |  | ✅ | ✅ |
| Media | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| File upload | ✅ |  |  |  |  |  |
| Branding customization | ✅ | \(✅\) | \(✅\) | \(✅\) | ✅ | ✅ |
| iframe | ✅ |  |  |  |  |  |
| Webview | ✅ | ✅ | \(✅\) |  |  |  |

