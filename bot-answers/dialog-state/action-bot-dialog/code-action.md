---
description: >-
  Learn how to steer the conversation by writing JavaScript code with the Code
  Action.
---

# Code Action

The code action allows developers to quickly build custom logic on top of their bot by writing their own Javascript code blocks. Typically, the code editor is used to perform requests to external systems, or to do operations with variables.

### Getting Started

To get started with the Code Action, create a new 'Action Dialogstate' and select the **Code** plugin as an action.

![](../../../.gitbook/assets/image%20%28318%29.png)

### Arguments

You can pass arguments to your Code actions by assigning them keys. Your keys will be made available to the `args` variable inside the Code Editor.

![](../../../.gitbook/assets/image%20%28319%29.png)

### ChatlayerResponseBuilder

The `ChatlayerResponseBuilder` function is a helper function that allows you to steer your conversation by sending messages as a bot, navigating to dialogstates, or even creating session data.

To start using the ChatlayerResponseBuilder, simply call it in your Code action:

![Initializing the ChatlayerResponseBuilder](../../../.gitbook/assets/image%20%28320%29.png)

This Chatlayer constant will now make it possible for you to call specific functionality within the bot's flow. When you're ready to publish your changes, use the `send()` function to send them to your user's conversation. 

#### setSessionVariable\(namespace: string, data: any\)

Insert a variable on a certain namespace within the session. 

```javascript
const chatlayer = ChatlayerResponseBuilder()
chatlayer.setSessionVariable('userName', 'Joachim')
chatlayer.send()
```

#### addMessage\(message: string\)

Adds a text message to be sent by the bot.

```javascript
const chatlayer = ChatlayerResponseBuilder()
chatlayer.addMessage('Hello!')
chatlayer.send()
```

#### setNextDialogState\(dialogstateId: string\)

Route the conversation to the given dialogstate ID.

```javascript
const { introductionDialogstate } = args

const chatlayer = ChatlayerResponseBuilder()
chatlayer.setNextDialogState(introductionDialogstate)
chatlayer.send()
```

### Available functionality

The the following functionality exists inside the Code action's scope:

#### lodash \(\_\)

Lodash is a JavaScript utility library. You can find more info [here](https://lodash.com/docs/4.17.15). 

```javascript
const introductionDialogstate = _.get(args, 'introductionDialogstate')

const chatlayer = ChatlayerResponseBuilder()
chatlayer.setNextDialogState(introductionDialogstate)
chatlayer.send()
```

#### fetch

Fetch allows you to perform API calls. You can find more info [here](https://github.com/node-fetch/node-fetch).

```javascript
const response = await fetch('https://randomuser.me/api/');
const json = await response.json();

const person = _.get(json, 'results[0]')  

const chatlayer = ChatlayerResponseBuilder()
chatlayer.setSessionVariable('profile', userProfile)
chatlayer.send()
```



