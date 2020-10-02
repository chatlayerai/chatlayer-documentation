# Context

{% hint style="info" %}
Context is used to reuse intents across several bot dialogs. Learn more about how to use context in [this tutorial](https://app.gitbook.com/@chatlayer/s/chatlayer-documentation/~/drafts/-MIZHNX0kLbXdbSP80Xb/understanding-users/using-context).
{% endhint %}

## Example

Consider the following dialog tree:

* Bot dialog `ask confirmation of pizza order`

  * Bot dialog `confirm order` - Intent: positive \(yes\)
  * Bot dialog `change order` - Intent: negative \(no\)

* Bot dialog `another joke?`
  * Bot dialog `second joke` - Intent: positive \(yes\)
  * Bot dialog `no more jokes` - Intent: negative \(no\)

We have two separate conversation in this tree. The first one orders a pizza and ends by asking the user to confirm the order. The second conversation tells our user a joke and asks if they would like to hear another one.

When in the `ask confirmation of pizza order` bot dialog, you want the user to be able to answer with something like _yes, confirm_ or _that looks good_. On the other hand when you are in the`another joke?` bot dialog, you also want the user to be able to answer with _yeah sure_ or _looks good_ or a similarly positive expression.

To make that happen, we need to reuse the '_Yes'_ intent for both bot dialogs. However, we need to give the bot a hand in understanding where the user wants to go by saying that intent at that point in the flow. For that, you can help the bot using **context**.

* Set the output context of the `ask confirmation of pizza order` bot dialog to **confirmingpizza.** The default value of the lifespan will be 1, you can leave that for now
* Next, in the bot dialog `confirm order`, specify that **confirmingpizza** needs to be the input context

![](../.gitbook/assets/image%20%2857%29.png)

Similarly, you can specify the output context of the `another joke?` bot dialog to **joking** and require **joking** as a required context for the bot dialog `second joke`.

Now, when the 'yes' intent is recognized, the bot will check which context is active. Depending on the context, a user will be directed to either the `confirm order` bot dialog \(when the **confirmingpizza** context is active\) or to the `second joke` bot dialog \(if the **joking** context was active\)

You can repeat this configuration for the 'no' intent as well. In the end, you would get a configuration like this:

* Bot dialog `ask confirmation of pizza orde`- Output context: **confirmingpizza**

  * Bot dialog `confirm order` - Required context: **confirmingpizza,** Intent: positive
  * Bot dialog `change order` - Required context: **confirmingpizza**, Intent: negative

* Bot dialog `another joke?` - Output context: **joking**
  * Bot dialog `second joke` - Required context: **joking**, Intent: positive
  * Bot dialog `no more jokes` - Required context: **joking**, Intent: negative

Of course, you don't want the user to be limited to this context for the rest of the conversation. After saying 'yes' to the initial question, every other expression similar to 'yes' can be an answer to a different question.

To configure this, you can define the **lifespan** of the output context. Each time the user enters a dialog state with an output configured, this context is added to his session with an initial lifespan value as defined in the bot dialog settings. For each user message, the lifespan of a context is decreased by one. When the value is 0, the context is removed from the session.

![](../.gitbook/assets/image%20%28190%29.png)

All of this means that a user is redirected to a bot dialog when:

1. The NLP model result has a top scoring intent with a value higher than the NLP intent recognition threshold value, and
2. This intent is linked to a bot dialog and the optional context linked to this bot dialog is available in the user session

{% hint style="info" %}
A user can have multiple contexts when navigating between different conversation flows. When multiple intent and input context combinations are found, the user's context with the highest lifespan value is taken.
{% endhint %}

