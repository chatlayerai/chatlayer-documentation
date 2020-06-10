# Chat message structure for API's

## Chat Messages

Chatlayer.ai supports different types of chat messages, each with his own object structure. Chat messages can be sent

* As a response from the API plugin
* From your webhook to Chatlayer.ai

Each message has two mandatory fields:

* **type**: the messages type \(carousel, buttons, list, media, text, …\)
* **config**: the message configuration

### Text Messages

A text message includes an array of text messages.

#### Request format

```javascript
const textMessage = {
  config: {
    textMessages: [{ text: '1st random text' }, { text: '2nd random text' }],
  },
  type: 'text',
};
```

#### Configuration object

| **Property** | **type** | **Description** |
| :--- | :--- | :--- |
| textMessages | Array | A list of text message objects |

#### Text message object

| **Property** | **type** | **Description** |
| :--- | :--- | :--- |
| text | String | A text message |

### Button template

A button template includes an array of buttons and an array of text messages. A button can have three types

* **postback**: redirects the user to a new dialog state. It is possible to save key values in the user session.
* **web\_url**: opens the website for this url.
* **phone\_number**: starts a telephone call.

#### Request format

```javascript
{
  config: {
    buttons: [
      {
        payload: {
          nextDialogstateId: 'eedeb3df-ebb1-46c0-836f-b85b784c42b1',
          params: [{ key: 'location', value: 'meulebeke' }],
        },
        title: 'gottotest',
        type: 'postback',
      },
      {
        title: 'URL button',
        type: 'web_url',
        url: 'https://www.google.com',
      },
      {
        payload: '193248u9',
        title: 'tel',
        type: 'phone_number',
      },
    ],
    textMessages: [{ text: '1st random text' }, { text: '2nd random text' }],
  },
  type: 'buttons',
}
```

#### Configuration object

| **Property** | **type** | **Description** |
| :--- | :--- | :--- |
| textMessages | Array | A list of text message objects |
| buttons | Array | A list of button objects |

#### Text message object

| **Property** | **type** | **Description** |
| :--- | :--- | :--- |
| text | String | A text message |

#### Button object

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Property</b>
      </th>
      <th style="text-align:left"><b>type</b>
      </th>
      <th style="text-align:left"><b>Description</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">title</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Title</td>
    </tr>
    <tr>
      <td style="text-align:left">type</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Button type: postback / web_url / call</td>
    </tr>
    <tr>
      <td style="text-align:left">payload (only for type postback and phone_number)</td>
      <td style="text-align:left">
        <p>String for type phone_number</p>
        <p>Object for type</p>
      </td>
      <td style="text-align:left">The button payload. An object with next dialog state and parameter key/value
        combinations for type postback. A telephone number for type phone_number.</td>
    </tr>
    <tr>
      <td style="text-align:left">url (only for type web_url)</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The website url to open</td>
    </tr>
    <tr>
      <td style="text-align:left">call (only for type phone_number)</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The phone number to call</td>
    </tr>
  </tbody>
</table>

#### Payload object for type postback

| **Property** | **type** | **Description** |
| :--- | :--- | :--- |
| nextDialogstateId | String | Redirect the user to this dialog state |
| params | Array | A list of parameter objects. A parameter object has a key and value property |

### Quick replies template

A quick replies template includes an list of quick replies and a list of text messages.

#### Request format

```javascript
const QR = {
  type: 'quickReplies',
  config: {
    textMessages: [{ text: '1st random text' }, {text: '2nd random text' }],
    quickReplies: [
      {
        imageUrl: 'https://www.faviconurl.jpg',
        payload: { nextDialogstateId: '1f51bo05-0510-11e03-0030-1f0d0040sd' },
        title: 'go to button',
        type: 'postback',
      },
    ],
  },
};
```

#### Configuration object

| **Property** | **type** | **Description** |
| :--- | :--- | :--- |
| textMessages | Array | A list of text message objects |
| quickReplies | Array | A list of quick reply objects |

#### Text message object

| **Property** | **type** | **Description** |
| :--- | :--- | :--- |
| text | String | A text message |

#### Quick reply object

| **Property** | **type** | **Description** |
| :--- | :--- | :--- |
| title | String | Title |
| type | String | Quick reply type: postback / location |
| payload | Object | The payload object with a next dialog state |
| imageUrl | String | The quick reply icon url |

#### Payload object

| **Property** | **type** | **Description** |
| :--- | :--- | :--- |
| nextDialogstateId | String | Redirect the user to this dialog state |
| params | Array | A list of parameter objects. A parameter object has a key and value property |

### Carousel

A carousel includes a list of carousel elements.

#### Request format

```javascript
const carousel = {
  config: {
    elements: [
      {
        imageUrl: 'https://www.chatlayer.ai/image.jpg',
        subTitle: 'subtitle',
        title: 'title',
        webUrl: 'https://www.chatlayer.ai',
        buttons: [
          {
            type: 'web_url',
            title: 'url button test',
            url: 'https://www.chatlayer.ai',
          },
        ],
      },
    ],
  },
  type: 'carousel',
};
```

#### Configuration object

| **Property** | **type** | **Description** |
| :--- | :--- | :--- |
| elements | Array | A list of carousel elements |

#### Carousel element object

| **Property** | **type** | **Description** |
| :--- | :--- | :--- |
| title | String | Title |
| subTitle | String | Subtitle |
| webUrl | String | The url to redirect the user to when a carousel element is tapped |
| imageUrl | String | The url of the carousel element image |
| buttons | Array | A list of buttons |

#### Button object

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Property</b>
      </th>
      <th style="text-align:left"><b>type</b>
      </th>
      <th style="text-align:left"><b>Description</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">title</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Title</td>
    </tr>
    <tr>
      <td style="text-align:left">type</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Button type: postback / web_url / call</td>
    </tr>
    <tr>
      <td style="text-align:left">payload (only for type postback and phone_number)</td>
      <td style="text-align:left">
        <p>String for type phone_number</p>
        <p>Object for type</p>
      </td>
      <td style="text-align:left">The button payload. An object with next dialog state and parameter key/value
        combinations for type postback. A telephone number for type phone_number.</td>
    </tr>
    <tr>
      <td style="text-align:left">url (only for type web_url)</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The website url to open</td>
    </tr>
    <tr>
      <td style="text-align:left">call (only for type phone_number)</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The phone number to call</td>
    </tr>
  </tbody>
</table>

#### Payload object for type postback

| **Property** | **type** | **Description** |
| :--- | :--- | :--- |
| nextDialogstateId | String | Redirect the user to this dialog state |
| params | Array | A list of parameter objects. A parameter object has a key and value property |

### Media

Media supports three types:

* image
* video
* audio

#### Request format

```javascript
const media = {
  config: {
    media: {
      type: 'image', //or video, attachment, audio
      url: 'https://www.chatlayer.ai/image.jpg',
    },
  },
  type: 'media',
};
```

#### Configuration object

| **Property** | **type** | **Description** |
| :--- | :--- | :--- |
| media | Media object | A media object |

#### Media object

| **Property** | **type** | **Description** |
| :--- | :--- | :--- |
| isCache | Boolean | A flag to indicate if the media should be cached for performance optimization. |
| type | String | The media type: video / audio / image |
| url | String | The media url |

