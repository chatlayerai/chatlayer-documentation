# Channels

Users can use your chat bot via a channel. The channel you choose for your bot depends on where its users will most likely look for help or hang out.

For example, if you are building an internal HR bot, we think it's best to put it on the company HR portal using a web widget, or perhaps on Facebook Workplace. However, if you're building a bot that targets a young\(er\) demographic, Facebook Messenger might be a better channel.

Publishing your bot on a channel is quite easy if you follow our channel guides:

{% page-ref page="facebook/" %}

{% page-ref page="whatsapp.md" %}

{% page-ref page="google-assistant.md" %}

{% page-ref page="webwidget.md" %}

{% page-ref page="phone-and-voice.md" %}

{% page-ref page="workplace-from-facebook.md" %}

{% page-ref page="webhook-api.md" %}

{% page-ref page="sinch-conversation-api-beta.md" %}

## Multi-channel

Chatlayer.ai allows you to connect one bot to multiple channels at the same time.

If you want your users to follow a different flow based on the channel they are using, you can use our multi-channel functionality. To do this, add a [Go To](../bot-answers/dialog-state/plugins.md) to the point in your flow where you wish to diverge, based on the channel.

Within this 'Go To', guide the user based on the botType variable, which contains the channel variable. For example:

![](../.gitbook/assets/image%20%2824%29.png)

The values for botType correspond to the channel names:

* Facebook Messenger: facebook
* Webhook: webHook
* Google Home: google
* Chat widget: web
* Facebook Workplace: facebookWorkplace
* Phone: voice
* All channels managed through the Sinch Conversation API \(SMS, RCS, WhatsApp, Viber\): sinchConversationAPI

## Channel comparison

The table below gives an overview of which features are available in which channels. If a feature is not listed below, it's available for all channels.

|  | Chat Widget | Facebook Messenger | Facebook Workplace | WhatsApp | Webhook  API | Zendesk |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Text messages | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Buttons | ✅ | ✅ | ✅ |  | ✅ | ✅ |
| Quick replies | ✅ | ✅ | ✅ | ✅\*2 | ✅ | ✅ |
| Carousel | ✅ | ✅ | ✅ |  | ✅ | ✅ |
| List | ✅ | ✅ | ✅ |  | ✅ | ✅ |
| Media | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| File upload | ✅ |  |  |  |  |  |
| Rich text | ✅ |  |  |  |  |  |
| Branding customization | ✅ | ✅\*1 | ✅ |  | ✅ | ✅ |
| iframe | ✅ |  |  |  |  |  |
| Webview |  | ✅ | ✅ |  |  |  |

\*1: Only possible to change the color scheme

\*2: Only through [WhatsApp message templates](https://developers.facebook.com/docs/whatsapp/message-templates/creation) approved by Facebook.



