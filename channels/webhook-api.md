# Webhook Channel API

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

{% api-method method="get" host="" path="/api/sessionData/:botId/:senderId/:namespace" %}
{% api-method-summary %}
Get the user session data
{% endapi-method-summary %}

{% api-method-description %}
This method can be used to retrieve user session data from a namespace. A namespace is used to save your session data into. You can use this data for interpolation of session variable values in messages, API requests, etc.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="access\_token" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-query-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="botId" type="string" required=false %}
The bot ID you want to send the message to
{% endapi-method-parameter %}

{% api-method-parameter name="senderId" type="string" required=false %}
The user's sender ID
{% endapi-method-parameter %}

{% api-method-parameter name="namespace" type="string" required=false %}
The namespace of the variables to get
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "myAwesomeVar": "myAwesomeValue",
  "myAwesomeVarDeep":  {
    "aa": "bb"
  }
}

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=302 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Sending User Messages & Receiving Bot messages

Chatlayer.ai provides:

* a Webhook message API endpoint to send a user message to the bot
* a Webhook configuration to be notified when bot messages are returned as response to a user messages sent to the webhook message API as described in [this section](webhook-api.md#save-user-session-data). This API is almost realtime and the purpose is to be able to trigger event-based behavior as soon as a bot message response occurs . This way you will be able to integrate the bot flow logic in your own application or message channel.

The overall mechanism is loosely based on Pubsub protocol , and rely on HTTP request containing the bot message response being sent to a consumer Endpoint URL. The customer webhook Endpoint URL can be configured in Chatlayer.ai as described in [this section](webhook-api.md#register-a-webhook-api).

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

### Register a webhook API

Add a new channel type webhook in your channel configuration in Chatayer.

![](../.gitbook/assets/0%20%282%29.png)

Configure both settings

* **Webhook URL**: this URL must either be publicly available, or at least available from Chatlayer.ai’s IP range. We strongly advise to use HTTPS for this endpoint
* **Verify token**: This can be any arbitrary string, but it is recommended to be chosen randomly.

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

{% api-method method="post" host="" path="/api/webview" %}
{% api-method-summary %}
Asynchronous actions
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

## Message objects

Chatlayer.ai bot message send to the customer webhook endpoint URL and returned as response of a user messages can have different object structures depending on the message type. This section describes the different message type object structures.

### Text

A text message includes a simple bot text message.

**Request format**:

```javascript
{
  "senderId": "a7355930-fa92-11e7-8308-2f056e75d1ee",
  "message":  {
    "text": "Hi, I'm a chatbot"
  },
  "messageCounter": 1,
  "verifyToken": "8wMsLZkdDPT64nqh"
}
```

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| text | string | The user test message. |

### Button Template

A button template includes a simple bot text message and an array of button objects.

**Request format**:

```javascript
{
  "senderId": "a7355930-fa92-11e7-8308-2f056e75d1ee",
  "message":  {
    "attachment": {
      "type": "template",
      "payload": {
        "template_type": "button",
        "text": "Hello, in which language can I help you?",
        "buttons": [
          {
            "type": "postback",
            "title": "Nederlands",
            "payload": "{\"params\": [{\"key\": \"userLangSelected\", \"value\": 
                       \"nl-nl\"}], \"nextDialogstateId\": 3050, \"type\": \"button\", 
                       \"caption\": \"Nederlands\"}"
          },
          {
            "type": "postback",
            "title": "English",
            "payload": "{\"params\": [{\"key\": \"userLangSelected\", \"value\": 
                       \"en-us\"}], \"nextDialogstateId\": 3050, \"type\": \"button\", 
                       \"caption\": \"English\"}"
          },
        ]
      }
    }
  },
  "messageCounter": 1,
  "verifyToken": "8wMsLZkdDPT64nqh"
}
```

**Message object for button template**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| attachment | object | The attachment object. |

**Attachment object**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| type | string | The attachment type \(template\) |
| payload | object | The attachment payload object. The object structure depends of the attachment type |

**Attachment payload object**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| template\_type | string | The template type \(button\) |
| text | string \(optional\) | The text above the buttons \( only for a button template type\) |
| buttons | array | An array of button objects |

**Button object**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| type | string | The button type \(web\_url - postback - phone\_numberl - element\_share\) |
| title | string | The button caption |
| payload | object \(type postback\) or string \(type phone\_number\) - optional | The button payload. Only for postback type buttons. |
| url | string - optional | The button url. Only for url type buttons |

**Button payload object**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| params | array with key/value objects | The key - value configuration settings of the button. This data will be saved in to the user session state data when he clicks this button. |
| nextDialogstateId | string | The dialog state to which the user will be navigated after the button click |
| type | string | UI component type \(button\) |
| caption | string | The button caption |

### Quick replies

A quick reply message includes a simple bot text message and an array of quick reply objects.

**Request format**:

```javascript
{
  "senderId": "a7355930-fa92-11e7-8308-2f056e75d1ee",
  "message":  {
    "text": "Hello, in which language can I help you?",
    "quick_replies": [
      {
        "content_type": "text",
        "title": "Nederlands",
        "payload": "{\"params\": [{\"key\": \"userLangSelected\", \"value\": 
                   \"nl-nl\"}], \"nextDialogstateId\": 3050, \"type\": \"button\", 
                   \"caption\": \"Nederlands\"}",
        "image_url": "https://domain/logo.png"
      },
      {
        "content_type": "text",
        "title": "English",
        "payload": "{\"params\": [{\"key\": \"userLangSelected\", \"value\": 
                   \"en-us\"}], \"nextDialogstateId\": 3050, \"type\": \"button\", 
                   \"caption\": \"English\"}",
        "image_url": "https://domain/logo.png"
      },
    ]
  },
  "messageCounter": 1,
  "verifyToken": "8wMsLZkdDPT64nqh"
}
```

**Message object for quick replies**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| text | string | The text before the quick replies. |
| quick\_replies | array | An array of quick reply objects |

**Quick reply object**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| content\_type | string | The quick reply content type \(text\) |
| title | string | The button caption |
| payload | object | The quick reply payload |

**Quick reply payload object**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| params | array with key/value objects | The key - value configuration settings of the quick reply. This data will be saved in to the user session state data when the user clicks this quick reply. |
| nextDialogstateId | string | The dialog state to which the user will be navigated after the quick reply click |
| type | string | UI component type \( quickreply\) |
| caption | string | The button/quick reply caption |

### Generic template

A generic template \(carousel\) includes a list of generic template elements. The generic template element is a simple structured message that includes a title, subtitle, image, and up to three buttons

**Request format**:

```javascript
{
  "senderId": "a7355930-fa92-11e7-8308-2f056e75d1ee",
  "message":  {
    "attachment": {
      "type": "template",
      "payload": {
        "template_type": "generic",
        "elements": [
          {
             "title": "Language",
             "subtitle": "Please set your language",
             "image_url": "https://domain/lang.png",
             "item_url": "https://domain/lang",
             "buttons": [
               {
                 "type": "postback",
                 "title": "Nederlands",
                 "payload": "{\"params\": [{\"key\": \"userLangSelected\", \"value\": 
                            \"nl-nl\"}], \"nextDialogstateId\": 3050, \"type\": \"button\", 
                            \"caption\": \"Nederlands\"}"
               },
               {
                 "type": "postback",
                 "title": "English",
                 "payload": "{\"params\": [{\"key\": \"userLangSelected\", \"value\": 
                            \"en-us\"}], \"nextDialogstateId\": 3050, \"type\": \"button\", 
                            \"caption\": \"English\"}"
               },
            ]
          }
        ]
      }
    }
  },
  "messageCounter": 1,
  "verifyToken": "8wMsLZkdDPT64nqh"
}
```

**Message object for generic template**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| attachment | object | The attachment object. |

**Attachment object**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| type | string | The attachment type \(template\) |
| payload | object | The attachment payload object. The object structure depends of the attachment type |

**Attachment payload object**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| template\_type | string | The template type \(generic\) |
| elements | array | An array of generic template elements \(carousel cards\) |

**Generic template element object**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| title | string | The carousel card title |
| subtitle | string | The carousel card subtitle |
| image\_url | string | The carousel card image |
| item\_url | string | The carousel card url. When the user clicks the image the web page opens in a new browser tab. |
| buttons | array | An array of button objects |

**Button object**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| type | string | The button type \(web\_url - postback - phone\_numberl - element share\) |
| title | string | The button caption |
| payload | object \(type postback\) or string \(type phone\_number\) - optional | The button payload. Only for postback type buttons. |
| url | string - optional | The button url. Only for url type buttons |

**Button payload object**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| params | array with key/value objects | The key - value configuration settings of the button. This data will be saved in to the user session state data when he clicks this button or quick reply. |
| nextDialogstateId | string | The dialog state to which the user will be navigated after the button/quick reply click |
| type | string | UI component type \(button or quick reply\) |
| caption | string | The button/quick reply caption |

### List template

The list template is a list of 2-4 structured items with an optional global button rendered at the bottom. Each item may contain a thumbnail image, title, subtitle, and one button. You may also specify a default\_action object that sets a URL that will be opened when the item is tapped.

**Request format**:

```javascript
{
  "senderId": "a7355930-fa92-11e7-8308-2f056e75d1ee",
  "message":  {
    "attachment": {
      "type": "template",
      "payload": {
        "template_type": "list",
        "elements": [
          {
             "title": "Language",
             "subtitle": "Select your language",
             "image_url": "https://domain/lang.png",
             "default_action": {
                "type": "web_url",
                "url": "default_url"
              }
             "buttons": [
               {
                 "type": "postback",
                 "title": "Nederlands",
                 "payload": "{\"nextDialogstateId\": 3050, \"type\": \"button\", 
                            \"caption\": \"button\"}"
               }
            ]
          }
        ],
        "buttons": []
      }
    }
  },
  "messageCounter": 1,
  "verifyToken": "8wMsLZkdDPT64nqh"
}
```

**Message object for list template**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| attachment | object | The attachment object. |

**Attachment object**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| type | string | The attachment type \(template\) |
| payload | object | The attachment payload object. The object structure depends of the attachment type |

**Attachment payload object**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| template\_type | string | The template type \(list\) |
| elements | array | An array of list element |
| buttons | array | An array of general list button objects |

**List template element object**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| title | string | The carousel card title |
| subtitle | string | The carousel card subtitle |
| image\_url | string | The carousel card image |
| default\_action | object | The default action when the user taps the list item. |
| buttons | array | An array of list item button objects |

**Default action object**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| type | string | The action type \(web\_url\) |
| url | string | The action ur. When the user taps the list element this web page will open in a new browser tab. |

**Button object**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| type | string | The button type \(web\_url - postback - phone\_numberl - element share\) |
| title | string | The button caption |
| payload | object \(type postback\) or string \(type phone\_number\) - optional | The button payload. Only for postback type buttons. |
| url | string - optional | The button url. Only for url type buttons |

**Button payload object**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| params | array with key/value objects | The key - value configuration settings of the button. This data will be saved in to the user session state data when he clicks this button or quick reply. |
| nextDialogstateId | string | The dialog state to which the user will be navigated after the button/quick reply click |
| type | string | UI component type \(button or quick reply\) |
| caption | string | The button/quick reply caption |

### Attachment

An attachment represents a file such as images and video.

**Request format**:

```javascript
{
  "senderId": "a7355930-fa92-11e7-8308-2f056e75d1ee",
  "message":  {
    "attachment": {
      "type": "image"
      "payload": {
        "url": "image_url",
      }
    }
  },
  "messageCounter": 1,
  "verifyToken": "8wMsLZkdDPT64nqh"
}
```

**Message object for attachment**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| attachment | object | The attachment object. |

**Attachment object**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| type | string | The attachment type \(image-video\) |
| payload | object | The attachment payload object. The object structure depends of the attachment type |

**Attachment payload object**:

| **Property** | **Value** | **Description** |
| :--- | :--- | :--- |
| url | string | The attachment url |

#### Custom components

Chatlayer.ai provides custom component development for your channels. Please contact your project manager to discuss further integration.

### 

