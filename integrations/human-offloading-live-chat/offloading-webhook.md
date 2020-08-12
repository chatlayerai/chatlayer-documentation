---
description: >-
  Learn how to create your own human handover integration through the Offloading
  Webhook
---

# Offloading Webhook

The offloading webhook allows you to integrate any human handover live chat platform. You can use the webhook to:

* Receive incoming user messages
* Receive outgoing bot messages
* Act upon offloading requests from a user

{% hint style="info" %}
This feature is currently in beta. If you would like access, please [get in touch](../../support/get-in-touch.md).
{% endhint %}

## Configuration

To configure your Chatlayer Offloading Webhook, head over to **Settings &gt; Offloading** and create a **Webhook** integration.

![](../../.gitbook/assets/image%20%28312%29.png)

Enter the API URL for your webservice and a Verify Token allowing you to validate incoming requests.

We will send a test request to your API URL when you press Save to validate whether your webservice is alive and ready to take requests, described in the Health Check method.

Congratulations! You are ready to start using your custom human handover integration.

## API Methods

All requests will arrive in JSON format at the API URL configured during the setup of the offloading webhook in Chatlayer. Every JSON POST request has a body with a **type** parameter that allows you to distinguish between the different types of data coming in. Different types are explained below.

We expect a status code of 200 for every request made to the webservice. Response data should be in JSON format.

{% api-method method="get" host="<your\_api\_url>" path="" %}
{% api-method-summary %}
API Health Check
{% endapi-method-summary %}

{% api-method-description %}
You must send the response as described in the Response tab. 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="challenge.verifyToken" type="string" required=false %}
The verifyToken allows you to validate the request is made by Chatlayer
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{ "status": "ok" }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="<your\_api\_url>" path="" %}
{% api-method-summary %}
Messages
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="timestamp" type="string" required=false %}
The time at which the message was generated
{% endapi-method-parameter %}

{% api-method-parameter name="messages" type="array" required=false %}
An array of user and bot messages
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=false %}
The type of request, in this case **`messages`**
{% endapi-method-parameter %}

{% api-method-parameter name="channel" type="string" required=false %}
The channel type
{% endapi-method-parameter %}

{% api-method-parameter name="sessionId" type="string" required=false %}
The user's session ID
{% endapi-method-parameter %}

{% api-method-parameter name="version" type="string" required=false %}
The bot version, either DRAFT or LIVE
{% endapi-method-parameter %}

{% api-method-parameter name="botId" type="string" required=false %}
The bot ID
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
We do not expect a response body.
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

The items in the messages array have the following format -

```javascript
{
    "type": "bot" | "user",
    "message": UserMessage | BotMessage
}
```

**BotMessage** objects follow the same structure as that of the Webhook Channel API, documented [here](https://docs.chatlayer.ai/channels/webhook-api#message-objects).

```javascript
// BotMessage example
{
    "type": "bot",
    "message": { "text": "Hi, I'm a chatbot" }
}
```

**UserMessage** objects may have the following structures:

```javascript
// UserMessage examples

// Intro
{ "messageType": "intro" }

// Text
{ "messageType": "text", "text": "Hi, I'm a user and I'd like to talk to an agent" }

// Upload
{ "messageType": "upload", "urls": [] }

// Location
{ "messageType": "location", "coordinates": { "lat": 0, "long": 0 } }

// Postback
{ "messageType": "postback", "title": "I'm a button" }
```

{% api-method method="post" host="<your\_api\_url>" path="" %}
{% api-method-summary %}
Offload
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="channel" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="transcript" type="array" required=false %}
An array containing all messages sent throughout the conversation.
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=false %}
The type of request, in this case **`offload`**
{% endapi-method-parameter %}

{% api-method-parameter name="timestamp" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="sessionId" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="version" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="botId" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "offloadSuccess": true,
    "pauseBot": true
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Recipes

### User-requested human handover

Use a "Send to offload provider" bot action dialog to trigger an **offload** call to your API.

![](../../.gitbook/assets/image%20%28313%29.png)

### Taking over the conversation

An agent may want to manually take over the user's conversation with the bot. To do this, you can pause the bot through the REST API.



