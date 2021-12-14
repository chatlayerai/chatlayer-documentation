---
description: >-
  Learn how to steer the conversation by writing JavaScript code with the Code
  Action.
---

# Code Editor

The code action allows developers to quickly build custom logic on top of their bot by writing their own Javascript code blocks. Typically, the code editor is used to perform requests to external systems, or to do operations with variables.

### Getting Started

To get started with the Code Action, create a new 'Action Dialogstate' and select the **Code** plugin as an action.

![](<../../.gitbook/assets/image (318).png>)

### Arguments in the Code Editor

You can pass arguments to your Code actions by assigning them keys. Your keys will be made available to the `args` variable inside the Code Editor.

![](<../../.gitbook/assets/image (319).png>)

### ChatlayerResponseBuilder function

The `ChatlayerResponseBuilder` function returns a helper instance that allows you to steer your conversation by sending messages as a bot, navigating to bot dialogs, or even creating session data.

To start manipulating conversation data in your code action, simply call the function `ChatlayerResponseBuilder()` which will return a `ChatlayerResponseBuilder` instance.&#x20;

The `ChatlayerResponseBuilder` has a fluent interface, this means that every function you call will return the same instance. This makes it easy to chain multiple function calls when, for example, you want to show a message and manipulate session data at the same time.&#x20;

Whenever you want to publish your changes to the conversation, you must call the `send()` function.&#x20;

{% hint style="warning" %}
If you don't call the `send()` function anywhere in your Code Action, users will not see any of your results after the code has executed.
{% endhint %}

```javascript
ChatlayerResponseBuilder()
    .addSessionVariable("user", { address: { ... } })
    .addMessage("Thank you for sharing your address!")
    .send();
```

Another way to accomplish the same result:

```javascript
const builder = ChatlayerResponseBuilder();
builder.addSessionVariable("user", { address: { ... } });
builder.addMessage("Thank you for sharing your address!");
builder.send();
```



#### Set variables or send messages

The `ChatlayerResponseBuilder` has the ability to set variables or adding messages to the chatbot. Both are shown in the example below:

_`addSessionVariable(namespace: string, data: any)`:_  Insert a variable on a certain namespace within the session.&#x20;

_`addMessage(message: string)`:_ Adds a text message to be sent by the bot.

```javascript
ChatlayerResponseBuilder()
    .addSessionVariable("user", 'Joachim')
    .addMessage("addSessionVariable done.")
    .send();
```

To enhance your variables even more, you can store multiple variables about the user in an object.&#x20;

```javascript
ChatlayerResponseBuilder()
    .addSessionVariable("user", { firstName: "Joachim", lastName: "Chatbot" })
    .send();
```

If you would like to use this information in a bot message, simply type `{user.lastName}` and the information is visible in the chatbot!

### Next or previous dialogs

Based on code, variables or other input, you can steer the conversation to other dialogstates. With the code below you can go to a next dialogstate.&#x20;

#### setNextDialogState(dialogstateId: string)

Route the conversation to the given dialogstate ID.&#x20;

```javascript
const { introductionDialogstate } = args;

const chatlayer = ChatlayerResponseBuilder();
chatlayer.setNextDialogState(introductionDialogstate);
chatlayer.send();
```

### Bot Message functionalities

In the code editor, some 'bot message' functionalities are also available, such as quick replies or buttons. For more in depth functionality, these same options can be created using code.&#x20;

#### addCarousel

In the Code Editor it is also possible to add a carousel, just like in Bot messages. This can be of added value when dynamic content needs to be shown or to combine a Bot message and Action dialog in one.

```javascript
ChatlayerResponseBuilder().addCarousel([
    {
        title: 'Item 1',
        imageUrl: 'https://st.depositphotos.com/1708346/1858/i/600/depositphotos_18582903-stock-photo-carousel-at-night.jpg',
        buttons: [
            { type: 'web_url', url: 'https://docs.chatlayer.ai', title: 'Docs' }
        ]
    },
    {
        title: 'Item 2',
        // This is optional
        subTitle: 'Item 2 Subtitle',
        // This is also optional, it will redirect a user to a certain website when they click the carousel image
        webUrl: 'https://docs.chatlayer.ai',
        imageUrl: 'https://st.depositphotos.com/1708346/1858/i/600/depositphotos_18582903-stock-photo-carousel-at-night.jpg',
        buttons: [
            { type: 'web_url', url: 'https://docs.chatlayer.ai', title: 'Docs' }
        ]
    }
]).send();
```

#### addQuickReplies

Just like the example above, Quick Replies can also be created in the code editor. By copying the code below you can add as many Quick reply buttons as needed.

```javascript
const quickReplies = [
[
  {
    title: "Option 1",
    payload: {
      nextDialogstateId: args.setNextDialogstateDs,
      params: [
        // This will be set on the session.0
        { key: "choice", value: "option1" },
      ],
    },
  },
  {
    title: "Option 2",
    payload: {
      nextDialogstateId: args.addHtmlDs,
      params: [
        // This will be set on the session.
        { key: "choice", value: "option1" },
      ],
    },
  },
];

ChatlayerResponseBuilder()
    .addQuickReplies({
        title: 'How can we help you?', // this is the title of the Quick Replies
        quickReplies,
    })
    .send();
```

#### addButtonGroup

With bot messages we can also add buttons, but with code there is more variety than the bot message.

![These buttons are created with the code below](<../../.gitbook/assets/image (371).png>)

```javascript
const invoices = [
 "123",
 "456",
 "789"
]

const buttons = invoices.map((invoiceNumber, index) => ({
    type: 'postback',
    title: 'Choose ' + invoiceNumber,
    payload: {
        nextDialogstateId: args.nextDialogstate,
        params: [
            { key: 'chosenNumber', value: invoiceNumber },
        ],
    },
}));

ChatlayerResponseBuilder()
    .addButtonGroup({
        title: "These 'postback' buttons can be used to navigate to a certain bot dialog and set a variable when a users clicks on them.",
        buttons,
    })
    .addButtonGroup({
        title: 'You can also add URL buttons.',
        buttons: [
            { type: 'web_url', title: 'docs', url: 'https://docs.chatlayer.ai' },
            { type: 'phone_number', title: 'Call 1207', payload: '1207'}
        ]
    })
    .send();
```

Here, the 'invoices' are the different button options displayed. With the `.addButtonGroup` you can add these buttons or create URL buttons.&#x20;

### Add HTML or Iframe

HTML can de added in the chatbot to show more diverse output to the user.

```javascript
ChatlayerResponseBuilder()
    .addHtml(`
        <h1>This is a header</h1>
        <p>Unfortunately, html messages will only work on the web widget.</p>
    `, { withBalloon: true })
    .send();
```

Iframes can be used to embed other pages in the chatbot. A perfect example of why you would need an iframe is embedding Youtube videos.

```javascript
ChatlayerResponseBuilder()
    .addIframe("https://www.youtube.com/watch?v=yaYzSQn9rL4", {
        withBalloon: false,
        height: "200px"
    })
    .send();
```

### Add media

The `addMediaMessage` method supports sending images, audio & video files through code actions.

```javascript
// Send an image
ChatlayerResponseBuilder()
    .addMediaMessage({
        type: "image",
        url: "<IMAGE_URL>"
    })
    .send();

// Send an audio file
ChatlayerResponseBuilder()
    .addMediaMessage({
        type: "audio",
        url: "<AUDIO_URL>"
    })
    .send();

// Send a video
ChatlayerResponseBuilder()
    .addMediaMessage({
        type: "video",
        url: "<VIDEO_URL>"
    })
    .send();
```

### Utility library and API calls

The following functionality exists inside the Code action's scope:

#### lodash (\_)

Lodash is a JavaScript utility library. You can find more info [here](https://lodash.com/docs/4.17.15).&#x20;

```javascript
const introductionDialogstate = _.get(args, 'introductionDialogstate');

const chatlayer = ChatlayerResponseBuilder();
chatlayer.setNextDialogState(introductionDialogstate);
chatlayer.send();
```

#### fetch

Fetch allows you to perform API calls. We use [**node-fetch**](https://github.com/node-fetch/node-fetch) **** as the default fetch library.

```javascript
const url = 'https://gorest.co.in/public/v1/users';
const response = await fetch(url).then((res) => {
    // res.status >= 200 && res.status < 300
    if (res.ok) {
        return res;
    } else {
        throw new Error(res.statusText);
    }
});

const json = await response.json();

const person = _.get(json, 'results[0]');

const chatlayer = ChatlayerResponseBuilder();
chatlayer.addSessionVariable('profile', userProfile);
chatlayer.send();
```

### Creating a slight delay between bot messages

Sometimes you want to create a slight delay between bot messages, either to create a natural pauze between them or because you need a few seconds to make an API call and don't want the bot to just be silent. Either way, slight pauzes can improve the user experience a lot.&#x20;

To create a short delay of two seconds, add an 'Action' dialog and paste the following code:

```javascript
const builder = ChatlayerResponseBuilder();

await new Promise((resolve)=>{_.delay(resolve,2000)});
builder.send();
```

_You can adjust the length of the delay by replacing the 2000 with 3000 (3 seconds) etc._
