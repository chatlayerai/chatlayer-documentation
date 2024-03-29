---
description: >-
  The Webhook channel provides a way to build a custom integration with
  Chatlayer that acts as a channel.
---

# Webhook channel

With the Webhook channel you can enrich the information sent via certain Channels. For example, instead of using the 'regular' Facebook Messenger or Whatsapp channel, you can use Webhook as a channel and send your messages via Webhook to Messenger or Whatsapp.

![With a regular channel integration, the channel is directly connected to Chatlayer](<../.gitbook/assets/image (652).png>)



![By using the Webhook channel, the channel of choice is indirectly connected with Chatlayer](<../.gitbook/assets/image (653).png>)

The two images above show the difference between using the channel of your choice directly, or if you would like to use Webhook to enhance the channel possibilities.&#x20;

{% hint style="warning" %}
Don't confuse the Webhook channel, a custom integration channel, with [Webhook offloading](https://docs.chatlayer.ai/integrations/human-offloading-live-chat/offloading-webhook), designed for offloading to human agents.
{% endhint %}

## Sending User Messages & Receiving Bot messages

Our platform provides the following features:

* a Webhook message API endpoint to send a user message to the bot
* a Webhook configuration to be notified when bot messages are returned as response to a user messages sent to the webhook message API as described in [this section](webhook-api.md#registering-a-webhook-api). This API is almost realtime and the purpose is to be able to trigger event-based behavior as soon as a bot message response occurs . This way you will be able to integrate the bot flow logic in your own application or message channel.

The overall mechanism is loosely based on Pubsub protocol and relies on HTTP request containing the bot message response being sent to a consumer Endpoint URL. The customer webhook Endpoint URL can be configured on our platform as described in [this section](webhook-api.md#registering-a-webhook-api).

## Registering a webhook API

You can register a webhook API by adding a new channel type webhook in your channel configuration:

![](<../.gitbook/assets/0 (2).png>)

Now configure both settings:

* **Webhook URL**: this URL must either be publicly available, or at least available from our platform's IP range. We strongly advise using HTTPS for this endpoint.
* **Verify token**: This can be any arbitrary string, but it is recommended to be chosen at random.

![](<../.gitbook/assets/1 (1).png>)

{% swagger baseUrl="" path="customer webhook endpoint URL configured in Chatlayer.ai" method="post" summary="Webhook messages" %}
{% swagger-description %}
When a user message is sent to the webhook message API, the bot response(s) will be sent to the customer webhook endpoint URL. The bot response body payload object will include the bot message. This message can have a different object structure based on the message type.
{% endswagger-description %}

{% swagger-response status="200" description="" %}
```
  "recipient": {
    "id": "default-b94215f0-0c7e-11ea-9c43-7174cba76asdfoijadsfoiadsiojadfiojasodijfb12"
  },
  "verifyToken": "eenheeluniekeverifytoken",
  "message": {
    "text": "test tekst message"
  }
```
{% endswagger-response %}
{% endswagger %}

## Message objects

A bot message sent to the customer webhook endpoint URL and returned as response to a user messages can have different object structures, depending on the message type. Want to learn how to build these message objects? Read about it here:

{% content-ref url="../integrations/chat-message-structure-for-apis.md" %}
[chat-message-structure-for-apis.md](../integrations/chat-message-structure-for-apis.md)
{% endcontent-ref %}
