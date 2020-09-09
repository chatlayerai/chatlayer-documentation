# Action

## Clear Session

Often, at the end of a flow, an API backend call will be configured to, for example, save a train ticket in the ticket ordering system. Afterwards users should be able to book a new ticket to a different location.

You can achieve this with the clear session action. This action removes the values of set session variables. This is useful when a user asks to correct a value, or to start over and delete all variables.

![](../../.gitbook/assets/image%20%28262%29.png)

## Send to offload provider

A user that reaches this action will be offloaded to a human customer support agent. For this to work you need to enable offloading.

Depending of your selected offloading provider additional configuration may be required.

## API

This action is used to integrate back-end services into your Chatlayer.ai bot. More details can be found in the tutorial [here](../../integrations/custom-back-end-integrations/).

## Code

Use the code editor to apply custom logic and functions to your flow, using Javascript. Click on the hamburger menu on the right to include some examples in your editor. You can find a tutorial about the use of the Code action [here](../../integrations/airtable.md).

## iframe

An iframe is a custom element that can be used to show a different webpage in the chat conversation. It can also be used to communicate with the parent window through the [postMessage API](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage).

A basic example would be the following :

```markup
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8">
		</head>
		<body>
			<button onClick="window.parent.postMessage(JSON.stringify({target:'CL_API',type:'SEND_MESSAGE', payload:{text: 'You clicked the button'} }),'*')">
         SEND_MESSAGE
        </button>
		</body>
</html>
```

If this code is hosted and embedded in the iframe plugin, when a user clicks the button, it will send a user message to the chat.

The postMessage API can also handle `UPDATE_SESSION` and `GO_TO_DIALOGSTATE` events.

## JSON Builder

If your bot is published on the [Webhook API](../../chatlayer-api/webhook-api.md) channel, you can use the JSON Builder action to send messages to the conversation that don't need to result in an actual message to the user. Typically, it's used to send information about the user or bot conversation to the website the bot is published at.

![](../../.gitbook/assets/image%20%28230%29.png)



