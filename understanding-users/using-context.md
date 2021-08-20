---
description: Need to reuse the same intent twice or more? Context is your friend.
---

# Context

Context makes it possible to reuse the same intent in several bot dialogs, an important feature in bot building! Let's learn how to use context with this short example:

So, we've built a bot that can help users place a food order. At one point in the conversation, the bot will ask the user if they'd like a free dessert. The user can reply with 'yes' or 'no'. A bit later in the conversation, the bot will ask the user if they're ready to place their order. Again, the user can reply with 'yes' or 'no'. 

## Step 1: Helping the bot understand the user's reply

First, for the bot to understand the user's 'yes' or 'no', we need to create two bot dialogs and link each one to one of the following intents: 

* general.yes
* general.no

![Two bot dialogs, one for each possible user response](../.gitbook/assets/image%20%28593%29.png)

## Step 2: Linking intents through context

![](../.gitbook/assets/dessert%20%282%29.png)

In the screenshot above, we added the `general.yes` intent to a bot dialog. We also added the `general.no` intent to another bot dialog. Now all we have to do is connect these dialogs to the question above, so the bot knows which question is being answered. 

We can do this by creating `output context` for the bot dialog containing the question. Open the `Want free dessert` dialog and go to the `NLP` section. Create an `output context` that you will later link to the dialogs containing the `general.yes` and `general.no` intents:

![Adding output context to a bot dialog](../.gitbook/assets/image%20%28592%29.png)

{% hint style="info" %}
You can tell the bot how often this context can be repeated throughout the entire bot conversation. For example: If the bot offers free dessert twice in one conversation, we should put the `lifespan` at 2 because the user can say 'yes' or 'no' twice to this question. In this example, we'll only offer free dessert once, so we'll keep the `lifespan` at 1.
{% endhint %}

The last thing to do is make sure that the two bot dialogs containing the `general.yes` and `general.no` intents are linked correctly to the dialog containing the question. To do so, we have to open each dialog, go to the NLP section, and add the `output context` we defined earlier as `required context` :

![Adding required context to a bot dialog](../.gitbook/assets/image%20%28591%29.png)

Once you click 'save', the bot can understand a 'yes' or 'no' response to the question of free dessert. 

Step 1 completed ☑️

## Step 3: Reusing intents in the same conversation

Later in the conversation, the bot will again ask a 'yes' or 'no' question to its user: 

_"Would you like to place your order?"_

To make sure the user can reply 'yes' or 'no' to this question as well, we'll need to use `output context` again:

![Using a different output context so we can use the yes/no intents again](../.gitbook/assets/image%20%28594%29.png)

Now, when the `general.yes` intent is recognized, the bot will know which question this answer belongs to checking the `output context`. Depending on this context, a user will be directed to either the `Yes place order` bot dialog \(when the **place\_order** context is active\) or to the `Yes to free dessert` bot dialog \(if the **free\_dessert** context is active\).

{% hint style="info" %}
A user can have multiple contexts when navigating between different conversation flows. When multiple intents and input context combinations are found, the user's context with the highest lifespan value is taken.
{% endhint %}

