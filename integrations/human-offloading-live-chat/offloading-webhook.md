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

## Configuration

To configure your Chatlayer Offloading Webhook, head over to **Settings > Offloading **and create a **Webhook** integration.

![](<../../.gitbook/assets/image (312).png>)

Enter the API URL for your webservice and a Verify Token allowing you to validate incoming requests.

We will send a test request to your API URL when you press Save to validate whether your webservice is alive and ready to take requests, described in the Health Check method.

Congratulations! You are ready to start using your custom human handover integration.

## Webservice Implementation Reference

Your webservice will need to implement the following API methods for us to communicate with. All requests will arrive in JSON format at the API URL configured during the setup of the offloading webhook in Chatlayer. Every JSON POST request has a body with an **event **parameter that allows you to distinguish between the different types of data coming in. Different types are explained below.

We expect a HTTP status code of 200 for every request made to the webservice. Response data should be in JSON format.

{% swagger baseUrl="<your_api_url>" path="" method="get" summary="API Health Check" %}
{% swagger-description %}
You must send the response as described in the Response tab. 
{% endswagger-description %}

{% swagger-parameter in="query" name="challenge.verifyToken" type="string" %}
The verifyToken allows you to validate the request is made by Chatlayer
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{ "status": "ok" }
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="<your_api_url>" path="" method="post" summary="Messages" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="challenge.verifyToken" type="string" %}
The verifyToken allows you to validate the request is made by Chatlayer
{% endswagger-parameter %}

{% swagger-parameter in="body" name="timestamp" type="string" %}
The time at which the message was generated
{% endswagger-parameter %}

{% swagger-parameter in="body" name="messages" type="array" %}
An array of user and bot messages
{% endswagger-parameter %}

{% swagger-parameter in="body" name="event" type="string" %}
The type of request, in this case 

**`messages`**
{% endswagger-parameter %}

{% swagger-parameter in="body" name="channel" type="string" %}
The channel type
{% endswagger-parameter %}

{% swagger-parameter in="body" name="sessionId" type="string" %}
The user's session ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="version" type="string" %}
The bot version, either DRAFT or LIVE
{% endswagger-parameter %}

{% swagger-parameter in="body" name="botId" type="string" %}
The bot ID
{% endswagger-parameter %}

{% swagger-response status="200" description="We do not expect a response body." %}
```
```
{% endswagger-response %}
{% endswagger %}

The items in the messages array have the following format -

```javascript
{
    "actor": "bot" | "user",
    "message": UserMessage | BotMessage
}
```

**BotMessage **objects follow the same structure as that of the Webhook Channel API, documented [here](https://docs.chatlayer.ai/channels/webhook-api#message-objects).

```javascript
// BotMessage example
{ "text": "Hi, I'm a chatbot" }
```

**UserMessage **objects may have the following structures:

```javascript
// UserMessage examples

// Intro
{ 
    "messageType": "intro", 
    // These fields are also included in every other UserMessage example
    // For brievity, we'll only document them once:
    "channelType": "web",
    "sender": {
        // The sender object differs between channelTypes, but will always include:
        "id": "123",
        "botId": "123"
    },
    "timestamp": "2020-09-22T19:34:16.049Z" 
}

// Text
{ 
    "messageType": "text", 
    "text": "Hi, I'm a user and I'd like to talk to an agent" 
}

// Upload
{ 
    "messageType": "upload", 
    "urls": [] 
}

// Location
{ 
    "messageType": "location", 
    "coordinates": { "lat": 0, "long": 0 } 
}

// Postback
{ 
    "messageType": "postback", 
    "title": "I'm a button" 
}
```

{% swagger baseUrl="<your_api_url>" path="" method="post" summary="Offload" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="payload" type="object" %}
The payload you configured in the action dialogstate
{% endswagger-parameter %}

{% swagger-parameter in="body" name="channel" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="transcript" type="array" %}
An array containing all messages sent throughout the conversation.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="event" type="string" %}
The type of request, in this case 

**`offload`**
{% endswagger-parameter %}

{% swagger-parameter in="body" name="timestamp" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="sessionId" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="version" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="botId" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "offloadSuccess": true,
    "pauseBot": true
}
```
{% endswagger-response %}
{% endswagger %}

The items in the transcript array have the same format as in the **messages** method described above.

## Recipes

### User-requested human handover

Use a "Send to offload provider" bot action dialog to trigger an **offload **call to your API.

![](<../../.gitbook/assets/image (313).png>)

### Sending messages as an agent

Use the [conversation actions API ](https://api.chatlayer.ai/v1/docs/#operation/executeConversationAction)to send messages as an agent. 



