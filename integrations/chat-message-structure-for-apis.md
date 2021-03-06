# Message objects for APIs

Chatlayer.ai supports different types of chat messages, each with his own object structure. Chat messages can be sent:

* As a response from the API plugin
* From your [webhook](../channels/webhook-api.md) to Chatlayer.ai

Each message has two mandatory fields:

* **type**: the messages type \(carousel, buttons, list, media, text, …\)
* **config**: the message configuration

## Text

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

## Button Template

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

## Quick replies

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

## Generic template

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

## List template

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

## Attachment

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

