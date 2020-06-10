# Context

{% hint style="info" %}
Context is used to reuse intents across several bot dialogs. To learn more about how to use context in Chatlayer.ai, follow [this tutorial](../tutorials/tutorial-using-context-for-intent-reuse.md).
{% endhint %}

## Usage example

Consider the following dialog tree

* Bot dialog `ask confirmation of pizza order`
  * Bot dialog `confirm order` - Intent: positive \(yes\)
  * Bot dialog `change order` - Intent: negative \(no\)
* Bot dialog `another joke?`
  * Bot dialog `second joke` - Intent: positive \(yes\)
  * Bot dialog `no more jokes` - Intent: negative \(no\)

We have two separate conversation in this tree. The first one orders a pizza and ends in asking the user to confirm the order. The second conversation tells a user jokes and asks if he or she would like to hear another one.

When in the `ask confirmation of pizza order` bot dialog, you want the user to be able to answer with something like _yes, confirm_ or _that looks good_. On the other hand when you are in the`another joke?` bot dialog, you also want the user to be able to answer with _yeah sure_ or _looks good_ or a similarly positive expression.

To achieve that behaviour, we need to reuse the _Yes_ intent for both bot dialogs. However, we need to give the bot a hand in determining where the user wants to go by saying that intent at that point in the flow. In Chatlayer.ai, you can guide the bot using **context**.

* Set the output context of the `ask confirmation of pizza order` bot dialog to **confirmingpizza.** The default value of the lifespan will be 1, you can leave that for now. ****
* Next, in the bot dialog `confirm order`, specify that **confirmingpizza** needs to be the input context.

![](../.gitbook/assets/image%20%2857%29.png)

Similarly, you can specify the output context of the `another joke?` bot dialog to **joking** and require **joking** as a required context for the bot dialog `second joke`

Now, when the 'yes' intent is recognized, the bot will check which context is active. Depending on the context, a user will be routed to either the `confirm order` bot dialog \(**confirmingpizza** context was active\) or to the `second joke` bot dialog \(**joking** context was active\)

We can repeat this configuration for the 'no' intent. In the end, we would get a configuration like this

* Bot dialog `ask confirmation of pizza orde`- Output context: **confirmingpizza**
  * Bot dialog `confirm order` - Required context: **confirmingpizza,** Intent: positive
  * Bot dialog `change order` - Required context: **confirmingpizza**, Intent: negative
* Bot dialog `another joke?` - Output context: **joking**
  * Bot dialog `second joke` - Required context: **joking**, Intent: positive
  * Bot dialog `no more jokes` - Required context: **joking**, Intent: negative

Of course, we don't want the user to be limited to this context for the rest of the conversation. After saying yes to the initial question, every other yes expression can be an answer to a different question.

To configure this you can define the **lifespan** of the output context. Each time the user enters a dialog state with an output configured this context is added to his session with an initial lifespan value as defined in the bot dialog settings. For each user message the lifespan of a context is decreased by one. When the value is 0 the context is removed from the session.

![](../.gitbook/assets/image%20%28190%29.png)

All of this means that: a user is redirected to a dialog state when

1. The NLP model result has a top scoring intent with a value higher than the NLP intent recognition threshold value, and
2. This intent is linked to a bot dialog and the optional context linked to this bot dialog is available in the user session

{% hint style="info" %}
A user can have multiple contexts when navigating between different conversation flows. When multiple intent and input context combinations are found, the user's context with the highest lifespan value is taken.
{% endhint %}

