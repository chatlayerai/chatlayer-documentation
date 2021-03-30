# Go to previous bot dialog

Usually, when a user asks a question, and this is not understood, they see a message like 'I did not understand'. To refresh the user's memory, you can repeat the last bot dialog again to the user, as shown below:

![](../../.gitbook/assets/image%20%28480%29.png)

What we see here is that the introduction has been created, and then the bot does not understand the user input 'test'. Then, after the 'not understood' message, the same message from before is shown again. This creates a full user experience and conversation flow. How to set this up is explained below:

## 1. Add variable to 'not understood'

In the 'not understood' bot message, create a new variable as shown below:

![](../../.gitbook/assets/image%20%28481%29.png)

Also make sure that the 'Go to' section of this bot dialog goes to a new action dialog, called 'Go to previous dialog' in this case.

## 2. Create action dialog

In the 'Go to previous dialog' action, create the following:

![](../../.gitbook/assets/image%20%28479%29.png)

This makes sure that the bot goes to the previous bot dialog, using the variable that is set in the 'not understood' bot message. The code can be copied from below:

```javascript
const { prevDialog } = args;

ChatlayerResponseBuilder()
.setNextDialogState(args.prevDialog)
.send() 
```

Make sure to test out your new configuration in the emulator.

And that's it! With just two simple steps you have created a better 'not understood experience'. Make sure to also check out the other [articles ](https://docs.chatlayer.ai/tips-and-best-practices/not-understood-bot-dialog)written about the 'not understood' bot dialog.

