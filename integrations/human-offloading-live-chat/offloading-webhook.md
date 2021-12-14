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

{% hint style="warning" %}
Offloading Webhook is for offloading users from bot to human agent. The [Webhook channel](https://docs.chatlayer.ai/channels/webhook-api) is a custom integration channel, make sure  you don't mix up these two!
{% endhint %}

## Configuration

To configure your Chatlayer Offloading Webhook, head over to **Settings > Offloading** and create a **Webhook** integration.

![](<../../.gitbook/assets/image (312).png>)

Enter the API URL for your webservice and a Verify Token allowing you to validate incoming requests.

We will send a test request to your API URL when you press Save to validate whether your webservice is alive and ready to take requests, described in the Health Check method.

Congratulations! You are ready to start using your custom human handover integration.

## Webservice Implementation Reference

Your webservice will need to implement the following API methods for us to communicate with. All requests will arrive in JSON format at the API URL configured during the setup of the offloading webhook in Chatlayer. Every JSON POST request has a body with an **event** parameter that allows you to distinguish between the different types of data coming in. Different types are explained below.

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

**BotMessage** objects follow the same structure as that of the Webhook Channel API, documented [here](https://docs.chatlayer.ai/channels/webhook-api#message-objects).

```javascript
// Text Bot Message example
{
    "botId": "ko3123ze",
    "version": "DRAFT",
    "sessionId": "emulator-18878e66-03fb-4ee7-b2c4-eb9db1848291",
    "event": "messages",
    "messages": [
        {
            "actor": "bot",
            "message": {
                "text": "Hi Welcome"
            },
            "timestamp": "2021-11-15T07:38:31.387Z"
        }
    ],
    "timestamp": "2021-11-15T07:38:31.387Z"
}

// Quick reply Bot Message example
{
    "botId": "ko3123ze",
    "version": "DRAFT",
    "sessionId": "emulator-d3dac415-5263-482c-a30b-d1588c52d918",
    "event": "messages",
    "messages": [
        {
            "actor": "bot",
            "message": {
                "text": "Hi Welcome"
            },
            "timestamp": "2021-11-15T07:47:08.383Z"
        },
        {
            "actor": "bot",
            "message": {
                "text": "Choose what you want to do?",
                "quick_replies": [
                    {
                        "title": "Do API FROM CODE",
                        "payload": "{\"title\":\"Do API FROM CODE\",\"caption\":\"Do API FROM CODE\",\"type\":\"quickreply\",\"parameters\":[],\"nextDialogstateId\":\"19f87132-e23c-4335-877d-6a36f511c2cc\",\"originalTitle\":\"Do API FROM CODE\"}",
                        "content_type": "text"
                    },
                    {
                        "title": "Api Plugin",
                        "payload": "{\"title\":\"Api Plugin\",\"caption\":\"Api Plugin\",\"type\":\"quickreply\",\"parameters\":[],\"nextDialogstateId\":\"e0b327e0-bfa0-42a7-9685-c68491625b6e\",\"originalTitle\":\"Api Plugin\"}",
                        "content_type": "text"
                    },
                    {
                        "title": "SendMessageFromCode",
                        "payload": "{\"title\":\"SendMessageFromCode\",\"caption\":\"SendMessageFromCode\",\"type\":\"quickreply\",\"parameters\":[],\"nextDialogstateId\":\"c125a34e-7fec-4385-8333-6a91e25cdcff\",\"originalTitle\":\"SendMessageFromCode\"}",
                        "content_type": "text"
                    }
                ]
            },
            "timestamp": "2021-11-15T07:47:08.384Z"
        }
    ],
    "timestamp": "2021-11-15T07:47:08.383Z"
}

// carousel / Generic template message
{
    "botId": "ko3123ze",
    "version": "DRAFT",
    "sessionId": "emulator-39ac2f23-07ce-4878-bd7d-729e6b39efdf",
    "event": "messages",
    "messages": [
        {
            "actor": "bot",
            "message": {
                "attachment": {
                    "type": "template",
                    "payload": {
                        "template_type": "generic",
                        "elements": [
                            {
                                "title": "Item 1",
                                "image_url": "https://st.depositphotos.com/1708346/1858/i/600/depositphotos_18582903-stock-photo-carousel-at-night.jpg",
                                "buttons": [
                                    {
                                        "title": "Docs",
                                        "url": "https://docs.chatlayer.ai",
                                        "type": "web_url"
                                    }
                                ]
                            },
                            {
                                "title": "Item 2",
                                "image_url": "https://st.depositphotos.com/1708346/1858/i/600/depositphotos_18582903-stock-photo-carousel-at-night.jpg",
                                "subtitle": "Item 2 Subtitle",
                                "buttons": [
                                    {
                                        "title": "Docs",
                                        "url": "https://docs.chatlayer.ai",
                                        "type": "web_url"
                                    }
                                ],
                                "default_action": {
                                    "url": "https://docs.chatlayer.ai",
                                    "type": "web_url"
                                }
                            }
                        ]
                    }
                }
            },
            "timestamp": "2021-11-15T08:24:32.871Z"
        }
    ],
    "timestamp": "2021-11-15T08:24:32.871Z"
}
```

**UserMessage** objects may have the following structures:

```javascript
// UserMessage examples

// Intro
{
    "botId": "ko3123ze",
    "version": "DRAFT",
    "sessionId": "emulator-942c05c5-b9b7-4319-81e7-6d687afaa23f",
    "event": "messages",
    "messages": [
        {
            "actor": "user",
            "message": {
                "channelType": "web",
                "sender": {
                    "id": "emulator-942c05c5-b9b7-4319-81e7-6d687afaa23f",
                    "botId": "ko3123ze",
                    "botType": "web",
                    "preferredLanguage": "en",
                    "firstname": "Guest",
                    "isEmulator": "true"
                },
                "timestamp": "2021-11-15T08:28:05.872Z",
                "messageType": "intro",
                "id": "61921a15cdee7f37a16ee5fc"
            },
            "timestamp": "2021-11-15T08:28:05.872Z"
        }
    ],
    "timestamp": "2021-11-15T08:28:05.908Z"
}

// Text
{
    "botId": "ko3123ze",
    "version": "DRAFT",
    "sessionId": "emulator-8f5873aa-8fee-471a-9467-81e30dec693d",
    "event": "messages",
    "messages": [
        {
            "actor": "user",
            "message": {
                "channelType": "web",
                "sender": {
                    "id": "emulator-8f5873aa-8fee-471a-9467-81e30dec693d",
                    "botId": "ko3123ze",
                    "botType": "web",
                    "isEmulator": "true"
                },
                "timestamp": "2021-11-15T08:26:13.154Z",
                "messageType": "text",
                "text": "hi there",
                "id": "619219a5cdee7f9f1b6ee5f7"
            },
            "timestamp": "2021-11-15T08:26:13.154Z"
        }
    ],
    "timestamp": "2021-11-15T08:26:13.193Z"
}

// Upload
{
    "botId": "ko3123ze",
    "version": "DRAFT",
    "sessionId": "1636964964162",
    "event": "messages",
    "messages": [
        {
            "actor": "user",
            "message": {
                "channelType": "web",
                "sender": {
                    "id": "1636964964162",
                    "botId": "ko3123ze",
                    "botType": "web",
                    "firstname": "Guest"
                },
                "timestamp": "2021-11-15T08:29:38.900Z",
                "messageType": "fileUploadInputResult",
                "urls": [
                    "https://minio.dev.chatlayer.ai/chatlayer-dev-eu-storage/f42af93e42b350fd7b874300c775756b168cc9ea4475b0c8c80e947228a26404/1636964964162_full.png"
                ],
                "data": {
                    "uploadStatus": "SUCCEEDED",
                    "fileUrl": "https://minio.dev.chatlayer.ai/chatlayer-dev-eu-storage/f42af93e42b350fd7b874300c7asdasdcc9ea4475b0c8c80e947228a26404/1636964964162_full.png"
                },
                "id": "61921a72cdee7fd1c56ee614"
            },
            "timestamp": "2021-11-15T08:29:38.900Z"
        }
    ],
    "timestamp": "2021-11-15T08:29:38.934Z"
}}

// Location
{
    "botId": "ko3123ze",
    "version": "DRAFT",
    "sessionId": "emulator-8f5873aa-8fee-471a-9467-81e30dec693d",
    "event": "messages",
    "messages": [
        {
            "actor": "user",
            "message": {
                "channelType": "web",
                "sender": {
                    "id": "emulator-8f5873aa-8fee-471a-9467-81e30dec693d",
                    "botId": "ko3123ze",
                    "botType": "web",
                    "isEmulator": "true"
                },
                "timestamp": "2021-11-15T08:26:13.154Z",
                "messageType": "location", 
                "coordinates": { "lat": 0, "long": 0 } 
                "id": "619219a5cdee7f9f1b6ee5f7"
            },
            "timestamp": "2021-11-15T08:26:13.154Z"
        }
    ],
    "timestamp": "2021-11-15T08:26:13.193Z"
}

// Postback
{
    "botId": "ko3123ze",
    "version": "DRAFT",
    "sessionId": "emulator-6d09d652-a971-47ab-8484-223a86ff316e",
    "event": "messages",
    "messages": [
        {
            "actor": "user",
            "message": {
                "channelType": "web",
                "sender": {
                    "id": "emulator-6d09d652-a971-47ab-8484-223a86ff316e",
                    "botId": "ko3123ze",
                    "botType": "web",
                    "isEmulator": "true"
                },
                "timestamp": "2021-11-15T08:33:39.276Z",
                "messageType": "postback",
                "title": "Set Variables",
                "parameters": [],
                "nextDialogstateId": "071abbc7-1d6e-4689-adef-1ea825178a72",
                "id": "61921b63cdee7f21ab6ee621"
            },
            "timestamp": "2021-11-15T08:33:39.276Z"
        }
    ],
    "timestamp": "2021-11-15T08:33:39.309Z"
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

{% swagger-response status="200" description="For successful offloading, we expect following response" %}
```
{
    "offloadSuccess": true,
    "pauseBot": true
}
```
{% endswagger-response %}
{% endswagger %}

The items in the transcript array have the same format as in the **messages** method described above.

One example of the offload request can be as follows:

```
// Some code
{
    "botId": "ko3123ze",
    "version": "DRAFT",
    "sessionId": "emulator-714a7b79-d674-4a62-a9a9-49581d7451e5",
    "timestamp": "2021-11-15T08:36:21.527Z",
    "event": "offload",
    "transcript": [
        {
            "actor": "bot",
            "message": {
                "text": "Hi Welcome"
            },
            "timestamp": "2021-11-15T08:36:11.991Z"
        },
        {
            "actor": "bot",
            "message": {
                "text": "Choose what you want to do?",
                "quick_replies": [
                    {
                        "title": "Do API FROM CODE",
                        "payload": "{\"title\":\"Do API FROM CODE\",\"caption\":\"Do API FROM CODE\",\"type\":\"quickreply\",\"parameters\":[],\"nextDialogstateId\":\"19f87132-e23c-4335-877d-6a36f511c2cc\",\"originalTitle\":\"Do API FROM CODE\"}",
                        "content_type": "text"
                    },
                    {
                        "title": "Api Plugin",
                        "payload": "{\"title\":\"Api Plugin\",\"caption\":\"Api Plugin\",\"type\":\"quickreply\",\"parameters\":[],\"nextDialogstateId\":\"e0b327e0-bfa0-42a7-9685-c68491625b6e\",\"originalTitle\":\"Api Plugin\"}",
                        "content_type": "text"
                    },
                    {
                        "title": "carousel",
                        "payload": "{\"title\":\"carousel\",\"caption\":\"carousel\",\"type\":\"quickreply\",\"parameters\":[],\"nextDialogstateId\":\"0844670c-ee9f-43eb-9102-f50321cb4921\",\"originalTitle\":\"carousel\"}",
                        "content_type": "text"
                    },
                    {
                        "title": "first options",
                        "payload": "{\"title\":\"first options\",\"caption\":\"first options\",\"type\":\"quickreply\",\"parameters\":[],\"nextDialogstateId\":\"13fc7f3e-80e5-45b8-862b-d2ff436eae0e\",\"originalTitle\":\"first options\"}",
                        "content_type": "text"
                    }
                ]
            },
            "timestamp": "2021-11-15T08:36:11.992Z"
        },
        {
            "actor": "user",
            "message": {
                "parameters": [],
                "text": "first options",
                "messageType": "postback",
                "title": "first options",
                "nextDialogstateId": "13fc7f3e-80e5-45b8-862b-d2ff436eae0e",
                "channelType": "emulator",
                "sender": {
                    "id": "emulator-714a7b79-d674-4a62-a9a9-49581d7451e5",
                    "botId": "ko3123ze"
                }
            },
            "timestamp": "2021-11-15T08:36:15.009Z"
        },
        {
            "actor": "bot",
            "message": {
                "attachment": {
                    "type": "template",
                    "payload": {
                        "template_type": "button",
                        "text": "What do you want to do?",
                        "buttons": [
                            {
                                "title": "Set Variables",
                                "type": "postback",
                                "payload": "{\"title\":\"Set Variables\",\"caption\":\"Set Variables\",\"type\":\"button\",\"originalTitle\":\"Set Variables\",\"nextDialogstateId\":\"071abbc7-1d6e-4689-adef-1ea825178a72\",\"parameters\":[]}"
                            },
                            {
                                "title": "offload",
                                "type": "postback",
                                "payload": "{\"title\":\"offload\",\"caption\":\"offload\",\"type\":\"button\",\"originalTitle\":\"offload\",\"nextDialogstateId\":\"408c102e-7215-48f8-a76c-5a45d70dcd9d\",\"parameters\":[]}"
                            }
                        ]
                    }
                }
            },
            "timestamp": "2021-11-15T08:36:15.010Z"
        }
    ]
}
```

## Recipes

### User-requested human handover

Use a "Send to offload provider" bot action dialog to trigger an **offload** call to your API.

![](<../../.gitbook/assets/image (313).png>)

### Sending messages as an agent

Use the [conversation actions API ](https://api.chatlayer.ai/v1/docs/#operation/executeConversationAction)to send messages as an agent.&#x20;



### Webhook Offloading FAQs

Here you can find frequently asked questions regarding Webhook offloading

**Why do I get requests on the offloading endpoint even though the user is not yet offloaded?**

We send the details of all the conversations that are happening in between user and the bot to the offloading endpoint under the **event: "messages"** so you can takeover the conversation if need be. This would also allow customers to keep track of all the conversations if need be.
