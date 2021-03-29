# Webhook Channel

## Sending User Messages & Receiving Bot messages

Our platform provides the following features:

* a Webhook message API endpoint to send a user message to the bot
* a Webhook configuration to be notified when bot messages are returned as response to a user messages sent to the webhook message API as described in [this section](webhook-api.md#registering-a-webhook-api). This API is almost realtime and the purpose is to be able to trigger event-based behavior as soon as a bot message response occurs . This way you will be able to integrate the bot flow logic in your own application or message channel.

The overall mechanism is loosely based on Pubsub protocol and relies on HTTP request containing the bot message response being sent to a consumer Endpoint URL. The customer webhook Endpoint URL can be configured on our platform as described in [this section](webhook-api.md#registering-a-webhook-api).

## Registering a webhook API

You can register a webhook API by adding a new channel type webhook in your channel configuration:

![](../.gitbook/assets/0%20%282%29.png)

Now configure both settings:

* **Webhook URL**: this URL must either be publicly available, or at least available from our platform's IP range. We strongly advise using HTTPS for this endpoint.
* **Verify token**: This can be any arbitrary string, but it is recommended to be chosen at random.

![](../.gitbook/assets/1%20%281%29.png)

{% api-method method="post" host="" path="customer webhook endpoint URL configured in Chatlayer.ai" %}
{% api-method-summary %}
Webhook messages
{% endapi-method-summary %}

{% api-method-description %}
When a user message is sent to the webhook message API, the bot response\(s\) will be sent to the customer webhook endpoint URL. The bot response body payload object will include the bot message. This message can have a different object structure based on the message type.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
  "recipient": {
    "id": "default-b94215f0-0c7e-11ea-9c43-7174cba76asdfoijadsfoiadsiojadfiojasodijfb12"
  },
  "verifyToken": "eenheeluniekeverifytoken",
  "message": {
    "text": "test tekst message"
  }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Message objects

A bot message sent to the customer webhook endpoint URL and returned as response of a user messages can have different object structures, depending on the message type. Want to learn how to build these message objects? Read about it here:

{% page-ref page="../integrations/chat-message-structure-for-apis.md" %}

