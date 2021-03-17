# Bot dialogs

## Flows

You can think of flows as a folder in which you can put bot dialogs that are related to the same topic.

{% hint style="info" %}
Keep in mind that flows, just like the connections between dialog states, are simply a way of organizing your bot. They do not restrict the movement of users across your bot.

* Users can jump from one flow to another by using intents 
* Bot builders can set-up a next bot dialog to another flow
{% endhint %}

![](../../.gitbook/assets/image%20%286%29.png)

Some tips on choosing how to group flows:

* Group all flows that have a functional relation. In our Choo Choo example, you could group all bot dialogs that are meant to help book a ticket, all general questions about trains, and all support flows \(e.g. "I lost my bag on the train"\)
* Reserve one flow for general questions, such as your offloading settings and the dialog for when your bot doesn't understand

## Bot dialog flow builder

### Bot dialog types

There are 4 kinds of bot dialogs, each with its own color and functionalities:

![](../../.gitbook/assets/image%20%28152%29.png)

* \*\*\*\*[**Bot message**](message-components.md)
  * Any message a bot is sending to a user is what we call a bot message. This includes text messages, buttons, quick replies, etc.
* \*\*\*\*[**Go to**](plugins.md)
  * If you want to add rules to determine where a user is guided to, based on the value of a variable, you can do it with this bot dialog type.
* \*\*\*\*[**Action**](action-bot-dialog.md)\*\*\*\*
  * Actions allow you to configure the settings of a user session, such as the language that will be used to reply to your user, or the offloading of a user.
* \*\*\*\*[**Input validation**](user-input-bot-dialog.md)
  * Use this bot dialog type to gather input from your users.

Every bot dialog type has its own settings and NLP tab, which stays the same throughout the different types.

### Bot dialogs menu

Our platform offers two different views of your dialog states, where you can configure what the bot will answer to a user.

* **The flow view**: a visual representation of all your dialog states, where you can easily see which bot dialogs are related to each other.
* **The table view**: the same information about your dialog states as in the flow view, but shown in a table, making it easier to filter, search and sort the dialog states.

### Flow view

The flow view shows your flows like a tree. This view is helpful to see how your flows are constructed. The parent child relations between bot dialogs visually organises the bot dialog states. Changing the parent child relation will not change the way your conversation flows work: it is purely for organising the bot dialogs in a logical matter. The user is only redirected by intent recognition or clicks on UI components such as buttons and quick replies.

### Table view

View your bot dialog states as a table, which is helpful for searching, filtering and sorting dialog states.

## Bot Dialog Settings

### Bot Dialog ID

This is the ID associated with the dialog state. You can use this to debug your bot using the Emulator.

### Bot dialog Name

The name for a specific dialog state. This is also the label that is shown in the tree view, the list view or the translations module. You can enter any name you want and change it as often as you like.

###  Bot Dialog Label

You may use this field as a custom identifier for your bot dialog when integrating solutions through the Webhook Channel API .

For example: say you want to store the number of times some specific bot dialog \( eg. `Greeting Message` \) has been triggered. You have added a custom label to that bot dialog \( eg. `messages_greeting`\).

Now if you delete the `Greeting Message` and recreate it, its unique identifier on our side will change, but you could still add `messages_greeting` as the custom label again.

If you use this custom label in your system to check if the bot dialog has been triggered then nothing on your side needs to be changed, just make sure the label of the recreated bot dialog is the same as the label of the bot dialog you deleted.

### Flow

The bot dialog flow determines in which flow the bot dialog you are editing \(or creating\) will be stored.

### Parent bot dialog

The Parent Dialog State can be used to visually organise your dialog states. Changing the Parent Dialog State will not restrict the conversation flows: it is purely for organising the dialog states in a visual way on the canvas.

{% hint style="info" %}
You can only choose a parent that is present in the flow you have selected.
{% endhint %}

## Bot dialog NLP settings

### Intent

Every bot dialog can be linked to an Intent. When a user is entering free-form text, it is analysed by the NLP model. If the model recognises an intent with a high enough accuracy \(above the threshold\), the user will get the bot dialog coupled to that intent. Multiple bot dialogs can reuse the same intent by using different `Context` settings. A dialog state can only be linked to one Intent.

### Required context

Input contexts give more information about when exactly an intent can be used. If you specify an input context and the linked intent is recognised, the bot will check if the input context is active and act accordingly: combine multiple required contexts for sub flows in flows.

To set a required context for a certain bot dialog, type the name of your context in the `Search or create required context` field. If it doesn't exist, a new context will be created. An existing context will be reused. You can also click on the available contexts in order to select one.

* If the required context is not active, this dialog state will not be shown, even though the intent linked to it was recognised.
* If the required context is active, the dialog state will be shown.

To learn more about using context, see our [Context concepts documentation](../../understanding-users/using-context.md).

![](../../.gitbook/assets/image%20%28245%29.png)

### Output contexts

To set an output context for a certain bot dialog, type the name of your context in the `Search or create output context` field. If it doesn't exist, a new context will be created. An existing context will be reused. You can also click on the available contexts to select a specific one.  
  
The number on the left of the context name is the **lifetime** of that context. For example: if you specify a lifetime of 3, this context will remain active for 3 user messages in a row. After the user has entered three messages, this context will not be active anymore. Combine multiple input contexts for sub flows in flows.

![](../../.gitbook/assets/image%20%2829%29.png)

