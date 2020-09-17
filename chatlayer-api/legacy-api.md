# Legacy API

{% hint style="danger" %}
The Webhook Channel API is deprecated, please refer to the [V1 API reference](https://api.chatlayer.ai/v1/docs/) for new integrations.
{% endhint %}

## Introduction

Chatlayer.ai provides a REST JSON API to retrieve, create data and manipulate data from third party applications and a webhook configuration to notify you when a variety of interactions or events happen, including when a bot sends a message. Webhook events are sent by Chatlayer.ai as POST requests to your webhook.

This document describes what can be done, under which conditions and the expected input and output formats and communication mechanism.

Note that the API can easily be tested from any web browser, command line terminal or API development environment.

The Chatlayer.ai Webhook API is often used to integrate Chatlayer.ai into a mobile app.

## Building HTTP request

### Scheme and hostname

Request **must** be done with https scheme. Depending on the environment, the API hostname will be: 

{% hint style="info" %}
**Endpoints:**

Staging: [https://api.staging.chatlayer.ai](https://api.staging.chatlayer.ai)

Production: [https://api.chatlayer.ai](https://api.chatlayer.ai)
{% endhint %}

All API paths are prefixed by /api.

### Access token

You **must** provide an access token on each of your API calls. This access token can be created [here](https://cms.staging.chatlayer.ai/tokens). For posting a webhook message the access token is not required and replaced by a verify token that you can configure in the bots settings in Chatlayer.ai together with the webhook configuration url.

![](../.gitbook/assets/image%20%28124%29.png)

### User id

A user id or sender id should have at least 32 characters.

### Example

We suppose you have an Chatlayer.ai bot instance accessible from the Chatlayer staging environment with bot id 11 and an access token with value `bot22`.

To get all chat messages on the source accessible by the token’s users, you’ll need to build your request with access\_token request query with proper value. The HTTP request will look like this:

```text
GET /api/chatMessage/11?access_token=abc42&from=2019-09-11 HTTP/1.1
Host: api.staging.chatlayer.ai
```

## Response

All responses are formatted in JSON using utf-8 encoding. The returned content-type is : application/json; charset=utf-8. Here is an example:

```javascript
{
 "text": "Hello World",
 "created_at": "2012-05-21T01:19:49Z", "available": true,
 "message_count": 4
}
```

Chatlayer.ai will retry sending the message 3 times upon receiving a failing HTTP code from your API.

## API methods

{% api-method method="get" host="" path="/api/bots/:botId/history/:senderId" %}
{% api-method-summary %}
Get Messages by senderId
{% endapi-method-summary %}

{% api-method-description %}
This method gets the messages by senderId.   
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="senderId" type="string" required=false %}
The id of the sender
{% endapi-method-parameter %}

{% api-method-parameter name="botId" type="string" required=false %}
The id of your bot
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="access\_token" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="offset" type="string" required=false %}
The amount of messages to skip
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="string" required=false %}
The size of the results
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "rows": [
        {
            "isIntro": false,
            "message": {
                "attachment": {
                    "type": "template",
                    "payload": {
                        "template_type": "button",
                        "text": "button text",
                        "buttons": [
                            {
                                "title": "go to button title",
                                "type": "postback",
                                "payload": "{\"title\":\"go to button title\",\"caption\":\"go to button title\",\"type\":\"button\",\"originalTitle\":\"go to button title\",\"nextDialogstateId\":\"eedeb3df-ffff-46c0-836f-b8534ge4c42b1\",\"parameters\":[{\"order\":0,\"key\":\"location\",\"value\":\"meulebeke\",\"__typename\":\"Parameter\"}]}"
                            },
                            {
                                "title": "URL button",
                                "url": "https://www.google.com",
                                "type": "web_url"
                            },
                            {
                                "title": "tel",
                                "type": "phone_number",
                                "payload": "+32 477 99 00 22"
                            }
                        ]
                    }
                }
            },
            "id": "5ddfffd8888c7bf11ebsss14",
            "actor": "bot",
            "createdAt": "2019-11-21T16:48:20.465Z"
        },
        {
            "isIntro": false,
            "message": {
                "text": "quick reply text",
                "quick_replies": [
                    {
                        "title": "go to button",
                        "payload": "{\"title\":\"go to button\",\"caption\":\"go to button\",\"type\":\"quickreply\",\"parameters\":[],\"nextDialogstateId\":\"e38fl4df-kkb1-46c0-836f-b8ffff4c42b1\",\"originalTitle\":\"go to button\"}",
                        "content_type": "text"
                    }
                ]
            },
            "id": "5dd64448988888811eb21a15",
            "actor": "bot",
            "createdAt": "2019-11-21T16:48:20.466Z"
        },
        {
            "isIntro": false,
            "message": {
                "attachment": {
                    "type": "template",
                    "payload": {
                        "template_type": "generic",
                        "elements": [
                            {
                                "title": "title",
                                "image_url": "https://www.chatlayer.ai/image.jpg",
                                "subtitle": "subtitle",
                                "buttons": [
                                    {
                                        "title": "url button test",
                                        "url": "https://www.chatlayer.ai",
                                        "type": "web_url"
                                    }
                                ],
                                "default_action": {
                                    "url": "https://www.chatlayer.ai",
                                    "type": "web_url"
                                }
                            }
                        ]
                    }
                }
            },
            "id": "5dd6kkkkbac7b4444b213kj",
            "actor": "bot",
            "createdAt": "2019-11-21T16:48:20.467Z"
        },
        {
            "isIntro": false,
            "message": {
                "attachment": {
                    "type": "image",
                    "payload": {
                        "is_reusable": false,
                        "url": "https://images.pexels.com/photos/67636/rose-blue-flower-rose-blooms-67636.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500"
                    }
                }
            },
            "id": "5dd6b2229bac74444eb21a17",
            "actor": "bot",
            "createdAt": "2019-11-21T16:48:20.468Z"
        },
        {
            "isIntro": false,
            "message": {
                "text": "ok test123"
            },
            "id": "5dd6bfd89b23456111b21a18",
            "actor": "bot",
            "createdAt": "2019-11-21T16:48:20.469Z"
        }
    ],
    "count": 5
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Sending User Messages & Receiving Bot messages

Chatlayer.ai provides:

* a Webhook message API endpoint to send a user message to the bot
* a Webhook configuration to be notified when bot messages are returned as response to a user messages sent to the webhook message API as described in [this section](../channels/webhook-api.md#save-user-session-data). This API is almost realtime and the purpose is to be able to trigger event-based behavior as soon as a bot message response occurs . This way you will be able to integrate the bot flow logic in your own application or message channel.

The overall mechanism is loosely based on Pubsub protocol , and rely on HTTP request containing the bot message response being sent to a consumer Endpoint URL. The customer webhook Endpoint URL can be configured in Chatlayer.ai as described in [this section](../channels/webhook-api.md#register-a-webhook-api).

{% api-method method="post" host="" path="/api/webhookMessage/:botId" %}
{% api-method-summary %}
Sending a user message to the bot
{% endapi-method-summary %}

{% api-method-description %}
This method sends a user message to the bot. The user message can be a simple text message or a button payload object which represents the state data when a user clicks the button or quick reply. The bot messages that come as a response will be sent to your webhook URL. The button payload is available in the messages received from the bot.  
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="botId" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="locale" type="string" required=false %}
ISO 2 letter language code \(en, nl, fr, de, ...\)
{% endapi-method-parameter %}

{% api-method-parameter name="verifyToken" type="string" required=true %}
The webhook verify token you should configure in the webhook configuration of the bot settings in Chatlayer.ai.
{% endapi-method-parameter %}

{% api-method-parameter name="sender" type="object" required=true %}
The Sender Object
{% endapi-method-parameter %}

{% api-method-parameter name="text" type="string" required=true %}
The user text message
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
EVENT_RECEIVED
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Example

```javascript
{
  "text": "hi",
  "sender":  {
    "id": "a7355930-fa92-11e7-8308-2f056e75d1ee"
  },
  "verifyToken": "8wMsLZkdDPT64nqh",
  "locale": "fr"
}
```

{% hint style="info" %}
No access token is required for this POST request and is replaced by a verify token you should configure in the webhook configuration of the bot settings.
{% endhint %}

**Sender object:**

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| id | string | The user identifier which can be used to identify the user when receiving a bot response on the webhook. |

**Request format for button click**

```javascript
{
  "text": "{\"params\": [{\"key\": \"userLangSelected\", \"value\": 
          \"en-en\"}], \"nextDialogstateId\": \"3050\", \"type\": \"button\", 
          \"caption\":
           \"Dutch\"}",
  "sender":  {
    "id": "a7355930-fa92-11e7-8308-2f056e75d1ee"
  },
  "verifyToken": "8wMsLZkdDPT64nqh"
}
```

**Text stringified object**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| params | array with key/value objects | The key - value configuration settings of the button/quick reply. This data will be saved in to the user session state data when he clicks this button or quick reply. |
| nextDialogstateId | string | The dialog state to which the user will be navigated after the button/quick reply click |
| type | string | UI component type \(button or quick reply\) |
| caption | string | The button/quick reply caption |

{% api-method method="post" host="" path="/api/webview" %}
{% api-method-summary %}
Asynchronous Actions
{% endapi-method-summary %}

{% api-method-description %}
This endpoint can be used to trigger a dialog state, send messages or save session data asynchronously.  
A typical use case is an action based on the triggering of a custom component.  
  
Note that for the request to succeed you will have to include either:   
- at least one message in the `messages` field  
- `action.nextDialogstate` with the id of the dialogstate to trigger.  
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="botId" type="string" required=true %}
The bot ID
{% endapi-method-parameter %}

{% api-method-parameter name="senderId" type="string" required=true %}
The user identifier
{% endapi-method-parameter %}

{% api-method-parameter name="session" type="object" required=false %}
Use this to add data to the user session.
{% endapi-method-parameter %}

{% api-method-parameter name="action" type="object" required=false %}
Use this parameter to include a nextDialogstate ID to define where the flow should go next.
{% endapi-method-parameter %}

{% api-method-parameter name="messages" type="array" required=false %}
The bot message object. The object structure depends on the message type.   
See appendix for all message structures.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```



```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Example request

```javascript
{
    "botId": "1234",
    "senderId": "the senderId of the conversation to act on",
    "session": {
        "namespace": "options",
        "data": {
            "example": true
        }
    },
    "action": {
        "nextDialogstate": "12345"
    },
    "messages": [
        {
            "type": "text",
            "config": {
                "textMessages": [ {"text": "This is a sample text message." } ]
            }
        }
    ]
}
```

#### Example request with a carousel

```javascript
{
    "botId": "1234",
    "senderId": "the senderId of the conversation to act on",
    "session": {
        "namespace": "options",
        "data": {
            "example": true
        }
    },
    "action": {
        "nextDialogstate": "12345"
    },
    "messages": [
        {
            "type": "carousel",
            "config": {
                "elements": [
                    {
                        "imageUrl": "https://www.chatlayer.ai/image.jpg",
                        "subTitle": "subtitle",
                        "title": "title",
                        "webUrl": "https://www.chatlayer.ai",
                        "buttons": [
                            {
                                "type": "web_url",
                                "title": "url button test",
                                "url": "https://www.chatlayer.ai"
                            }
                        ]
                    }
                ]
            }
        }
    ]
}
```

{% api-method method="post" host="" path="/api/bots/:botId/extract/:version" %}
{% api-method-summary %}
Extract NLP \(beta\)
{% endapi-method-summary %}

{% api-method-description %}
This endpoint may be used to fetch an NLP result for a single expression. This NLP extract contains your matched intents, entities and their performance scores.   
  
**Expect the in- and output of this endpoint to change in the future. Existing fields will remain the same but we reserve the right to add new fields at our discretion.**  
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="botId" type="string" required=true %}
Your bot's unique ID
{% endapi-method-parameter %}

{% api-method-parameter name="version" type="string" required=true %}
The version to extract NLP data from. This value can contain DRAFT or LIVE.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="access\_token" type="string" required=true %}
The API access token
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="language" type="string" required=true %}
The language to use, in lowercase 2-letter notation.
{% endapi-method-parameter %}

{% api-method-parameter name="expression" type="string" required=true %}
The expression to gather an NLP result for
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The following response is the result of extracting the expression "I'd like a train ticket to Brussels at 1AM" in English \(language "en"\)
{% endapi-method-response-example-description %}

```javascript
{
    "data": {
        "extract": {
            "score": 0.9998863854559811,
            "intent": "book train ticket",
            "query": "I'd like a train ticket to Brussels at 1AM tomorrow",
            "exactMatchedIntent": null,
            "intents": [
                {
                    "intent": "book train ticket",
                    "score": 0.9998863854559811,
                    "__typename": "ExtractResultIntent"
                },
                {
                    "intent": "define train class",
                    "score": 0.00005304149680909305,
                    "__typename": "ExtractResultIntent"
                },
                {
                    "intent": "yes",
                    "score": 0.000040271091743810046,
                    "__typename": "ExtractResultIntent"
                }
            ],
            "entities": [
                {
                    "name": "arrival_date",
                    "value": "Tomorrow",
                    "score": 0.61095,
                    "startIndex": 55,
                    "endIndex": 63,
                    "systemEntity": false,
                    "__typename": "ExtractResultEntity"
                },
                {
                    "name": "time",
                    "value": "2020-05-13T01:00:00.000+00:00",
                    "score": 1,
                    "startIndex": 48,
                    "endIndex": 63,
                    "systemEntity": true,
                    "__typename": "ExtractResultEntity"
                },
                {
                    "name": "time_grain",
                    "value": "hour",
                    "score": 1,
                    "startIndex": 48,
                    "endIndex": 63,
                    "systemEntity": true,
                    "__typename": "ExtractResultEntity"
                }
            ],
            "entityThreshold": 0.7,
            "intentThreshold": 0.8,
            "__typename": "ExtractResult"
        }
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="warning" %}
This is an Chatlayer.ai Enterprise or Corporate feature. Please contact your Chatlayer.ai sales representative before using this API endpoint.
{% endhint %}

## 

