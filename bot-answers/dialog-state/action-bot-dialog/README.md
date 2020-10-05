# Action

## Clear Session

Often, at the end of a flow, an API backend call will be configured to, for example, save a train ticket in the ticket ordering system. Afterwards users should be able to book a new ticket to a different location.

You can achieve this with the 'clear session' action. This action removes the values of set session variables. This is useful when a user asks to correct a value, or to start over and delete all variables.

![](../../../.gitbook/assets/image%20%28262%29.png)

## Send to offload provider

A user that reaches this action will be offloaded to a human customer support agent. For this to work, you need to enable offloading.

Depending on your selected offloading provider, additional configuration may be required.

## API

This action can be used to integrate back-end services into your bot.   
More details can be found in [our tutorial](https://app.gitbook.com/@chatlayer/s/chatlayer-documentation/~/drafts/-MIrr7mtVp_aqyzM-udL/integrations/custom-back-end-integrations).

## Code

The code editor allows developers to quickly build custom logic on top of the bot by writing their own Javascript code blocks. Typically, the code editor is used to perform requests to external systems, or to do operations with variables.

Click on the hamburger menu on the right to include some examples in your editor. There are two tutorials on how to use the Code editor:

{% page-ref page="../../../integrations/retrieving-data-from-airtable-get.md" %}

{% page-ref page="../../../integrations/airtable.md" %}

## iframe

An iframe is a custom element that can be used to show a different web page in the chat conversation. It can also be used to communicate with the parent window using the [postMessage API](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage).

Have a look at this basic example:

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

If this block of code is hosted and embedded within our iframe plugin, it will send the user a chat message when they click the button.

The postMessage API can also handle `UPDATE_SESSION` and `GO_TO_DIALOGSTATE` events.

## JSON Builder

If your bot is published on the [Webhook API](../../../channels/webhook-api.md) channel, you can use the JSON Builder action to send messages to the conversation that don't need to result in an actual message to the user. Typically, it's used to send information about the user or bot conversation to the website the bot is published on.

![](../../../.gitbook/assets/image%20%28230%29.png)



