# Bot dialogs

## Flows

You can think of flows as a folder in which you can put bot dialogs that are related to the same topic.

{% hint style="info" %}
Keep in mind that flows, just like the connections between dialog states, are simply a way of organizing your bot. They do not restrict the movement of users across your bot.

* Users can jump from one flow to another by using intents. 
* Bot builders can set-up a next bot dialog to another flow
{% endhint %}

![](../../.gitbook/assets/image%20%286%29.png)

Some tips in choosing how to split flows:

* Group all flows that have a functional relation. In our Choo Choo example, you could group all bot dialogs that are meant to help book a ticket, all general questions about trains, and all support flows \(e.g. I lost my bag on the train\).
* Reserve one flow for general questions, such as your offloading settings and your not understood bot dialog.

## Bot dialog flow builder

### Bot dialog types

There are four kinds of bot dialogs, each with its own color and functionalities.

![](../../.gitbook/assets/image%20%28152%29.png)

* \*\*\*\*[**Bot message**](message-components.md)
  * Every message that a bot will send to a user is a bot message. This includes text messages, buttons, quick replies, etc.
* \*\*\*\*[**Go to**](plugins.md)
  * If you want to add rules to determine how a user is routed based on the value of a variable, you can do it with this bot dialog type.
* \*\*\*\*[**Action**](action-bot-dialog.md)\*\*\*\*
  * Actions allow you to configure the settings of a user session, such as the language that will be used to reply to your user, or the offloading of a user.
* \*\*\*\*[**Input validation**](user-input-bot-dialog.md)
  * Use this bot dialog type to gather input from your users.

Every bot dialog type has a settings and NLP tab, which stay the same throughout the different types.

### Bot dialogs menu

In Chatlayer.ai you can have two views on your dialog states, where you configure what the bot will answer to a user.

* **The flow view**: a visual representation of all your dialog states, where you can easily see which bot dialogs are related to each other.
* **The table view**: the same information about your dialog states, but in a table, making it easier to filter, search and sort on dialog states.

### Bot dialog flow view

View your flows as a tree representation. This view is helpful to see how your flows are constructed. The parent child relations between bot dialogs is being used to visually organise the bot dialog states. Changing the parent child relation will not change the way your conversation flows work: it is purely for organising the bot dialogs in a logical matter on the canvas. The user is only redirected by intent recognition or click on UI components such as buttons and quick replies.

### Bot dialog table view

View your bot dialog states in a table which is helpful for searching, filtering and sorting dialog states.

## Bot Dialog Settings

### Bot Dialog ID

This is the ID associated with the dialog state. You can use this to debug the bot in the Emulator.

### Bot dialog Name

The name associated to this dialog state. This is also the label that is shown in the tree view, the list view or the translations module. You can enter any name you like and change it as often as you wish.

### Flow

The bot dialog flow determines in which flow the bot dialog you are editing or creating will live.

### Parent bot dialog

The Parent Dialog State can be used to visually organise the dialog states. Changing the Parent Dialog State will not restrict the conversation flows: it is purely for organising the dialog states in a logical matter on the canvas.

{% hint style="info" %}
You can only choose a parent that is present in the flow you have selected.
{% endhint %}

## Bot dialog NLP settings

### Intent

Every bot dialog can be linked to an Intent. When a user is entering free-form text, it is analysed by the NLP model. If the NLP model recognises an intent with a high enough accuracy \(above the threshold\), the user will reach the bot dialog coupled to the intent. Multiple bot dialogs can reuse the same intent by using different `Context` settings. A dialog state can only be linked to one Intent.

### Required context

To restrict the usage of an intent in a bot dialog to certain points in the dialog flow, you can use input contexts. If you specify an input context and the linked intent is recognised, the bot will check if the input context is active and act accordingly: combine multiple required contexts for sub flows in flows.

To set a required context for a certain bot dialog, type the name of your context in the `Search or create required context` field. If it doesn't exist a new context is created. An existing context is re-used. You can also click on the available contexts to select one.

* If the required context is not active, this dialog state will not be reached, even though the intent linked to it was recognised. 
* If the required context is active, the dialog state will be reached.

To learn more about using context, see the [Context concepts documentation](../../understanding-users/using-context.md)

![](../../.gitbook/assets/image%20%28245%29.png)

### Output contexts

To set an output context for a certain bot dialog, type the name of your context in the `Search or create output context` field. If it doesn't exist a new context is created. An existing context is re-used. You can also click on the available contexts to select one.  
  
The number on the left of the context name is the **lifetime** of the context. For example if you specify a lifetime of 3, this context will remain active for 3 user messages. After the user has entered three messages, this context will not be active anymore. Combine multiple input contexts for sub flows in flows.

![](../../.gitbook/assets/image%20%2829%29.png)

