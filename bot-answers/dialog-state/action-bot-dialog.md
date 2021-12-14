# Action

## Clear Session

Often, at the end of a flow, an API backend call will be configured to, for example, save a train ticket in the ticket ordering system. Afterwards users should be able to book a new ticket to a different location.

You can achieve this with the 'clear session' action. This action removes the values of set session variables. This is useful when a user asks to correct a value, or to start over and delete all variables.

![](<../../.gitbook/assets/image (262).png>)

## Send to offload provider

A user that reaches this action will be offloaded to a human customer support agent. For this to work, you need to enable offloading.

Depending on your selected offloading provider, additional configuration may be required.

## API

This action can be used to integrate back-end services into your bot. \
More details can be found in [our tutorial](https://docs.chatlayer.ai/integrations/custom-back-end-integrations).

## Code

The code editor allows developers to quickly build custom logic on top of the bot by writing their own Javascript code blocks. Typically, the code editor is used to perform requests to external systems, or to do operations with variables.

You can find more information about the code editor here:

{% content-ref url="../../integrations/code-action/" %}
[code-action](../../integrations/code-action/)
{% endcontent-ref %}

There are also two tutorials in which we show you how the code editor can be used:

{% content-ref url="../../integrations/code-action/retrieving-data-from-airtable-get.md" %}
[retrieving-data-from-airtable-get.md](../../integrations/code-action/retrieving-data-from-airtable-get.md)
{% endcontent-ref %}

{% content-ref url="../../integrations/code-action/airtable.md" %}
[airtable.md](../../integrations/code-action/airtable.md)
{% endcontent-ref %}

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

If your bot is published on the [Webhook API](../../channels/webhook-api.md) channel, you can use the JSON Builder action to send messages to the conversation that don't need to result in an actual message to the user. Typically, it's used to send information about the user or bot conversation to the website the bot is published on.

![](<../../.gitbook/assets/image (230).png>)

### Website window events&#x20;

**You can use the JSON builder action** **in combination with the webwidget channel** to receive window events on your webpage. These events will contain the data as configured in your JSON builder action.&#x20;

Here's an example: \
Configure your JSON builder action to send a **language** key, with a variable retrieved from the session, and the "Send config to parent window" toggled on.

![JSON builder action with a language field](<../../.gitbook/assets/image (324).png>)

Your widget will trigger an event for that configuration to its parent window as a MessageEvent. The MessageEvent will contain a \`data\` field which contains the stringified result of the JSON builder configuration. Here's an example on how to listen to these events:

```javascript
// Chatlayer JSON Builder Event Handler
window.addEventListener('message', (event) => {
    const data = event && event.data && JSON.parse(event.data) || {}
    const { type, payload } = data
    if (type !== 'CL_DISPATCH_EVENT') return;
    console.log('Chatlayer language received: ' + payload.language)
})
```
