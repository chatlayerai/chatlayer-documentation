# Adding content to your bot

In the previous tutorial, we created a new bot and added a greeting. Now it's time to add some actual content. We will start with some basic bot responses to users' frequently asked questions.

## The NLP engine

The Natural Language Processing \(NLP\) engine is the underlying algorithm that allows the bot to understand what the user is saying. Since each language has its own words and grammar, we have a separate NLP engine for each language.

> Understanding language isn't easy: it takes us humans about 6 years and hundreds of examples to understand the most common 20,000 words. And computers are not that different. To train an NLP engine, we need huge amounts of data. Luckily, we rely on pre-trained models that have a lot of smarts built in already.

## Adding an intent

An **intent** is a specific action your user can do, or a type of question your user can ask. Intents are single blocks of meaning that the NLP can recognise. For example: an intent can be a question, a statement, an answer to a question, or a greeting. Each intent can be expressed in many different ways, that all mean the same thing. We call these different ways of saying the same thing **expressions**.

Some examples of intents and expressions:

* Intent: book train ticket Expressions:
  * I want to book a train ticket
  * I need to go from Antwerp to Brussels
  * Can I order a ticket here?
* Intent: who are you? Expressions:
  * What is your name?
  * What can you do?
  * What should I call you?
* Intent: yes Expressions:
  * Looks good
  * Yes
  * Ok, confirm
* Intent: I want to speak to a human Expressions:
  * Can i speak to a real person?
  * human please
  * You are a dumb bot

For this tutorial, we want to give Choo Choo the ability to answer basic questions about itself. To get started, we will create an intent for the simple question `Who are you?`

* On the left side of the screen in the navigation menu, click on `NLP` to navigate to the NLP module. Click the `Intents` submenu.

![](../.gitbook/assets/image%20%28164%29.png)

* Click on `+ Add Intent` and name it `who are you`

![](../.gitbook/assets/screenshot-2019-04-02-at-13.25.38.png)

### Adding expressions

Now we have to train the NLP to recognise this Intent. We do this by adding Expressions. Expressions are different ways your users will express one Intent. 

{% hint style="info" %}
Expressions are another word for what is sometimes called 'Utterances'
{% endhint %}

The more Expressions you add to an Intent, the more accurately it will be recognised. It is crucial for an Intent to have a wide variety of expressions to give accurate results. The more expression you can think of, the better the result of the NLP will be and the 'smarter' your bot will appear.

* Select the `who are you` intent in the **Intents** pane
* Click on `+ Add Expression` in the **Expressions** pane
* Enter `Who are you?` in the open text field
* Click on `Create`

![](../.gitbook/assets/image%20%28337%29.png)

Your screen should look like this:

![](../.gitbook/assets/image%20%28333%29.png)

Add some more expressions:

* What is your name?
* Can I know your name?
* Tell me more about yourself
* Please, I'd like to know who I am talking to
* How should I call you?
* Who is Choo Choo?
* Tell me what your name is
* Who are ya?
* What do people call you?
* Are you a train?
* Do you have a name?

Again, the more expression you have, the more accurate your bot will be able to respond. Later on, we will see how we can make sure that our bot gets smarter over time, by looking at actual user input once the bot is made public.

{% hint style="info" %}
It’s important to have a roughly equal number of expressions for each intent. Even if it usually takes more examples to train your most important intent than your second-order ones, strive to keep their number of expressions around the same amount. This helps avoid a bias towards intents with a large expression count.
{% endhint %}

### Training the model

Add another intent, like `Greeting` and add some expressions:

* Hi
* Hello
* Hey
* Hi there
* Good morning

Tip: if two of your intents are very similar in terms of expressions’ syntax or content, you might want to merge them. For example, let's look at our bot responsible for booking train tickets. Imagine you'd also like to offer bus tickets. You could create an extra intent for booking bus tickets, but the expressions in each intent would be very similar, with only the transportation mode changing from time to time. It would be better to only have one intent handling reservations, and an **entity** to catch the requested vehicle type.   
We will look at entities in the next tutorial.

We have defined two intents now: who are you & greeting.

![](../.gitbook/assets/intents%20%281%29.png)

To update the bot, we now need to re-train the NLP.

{% hint style="info" %}
To successfully train the NLP, you need to have at least two intents with a minimum of 5 expressions each.
{% endhint %}

* Click the `Update NLP` button in the top right corner of the screen:

![](../.gitbook/assets/image%20%2884%29.png)

Select the language you used to add the expressions.  __You can view the status of the NLP update for each language by clicking on the Update NLP icon.

![](../.gitbook/assets/update-nlp.png)

Click on `Update` to start the training. This can take a couple of minutes to one hour depending on the size of your chatbot. The more complex, the longer it'll take.

![](../.gitbook/assets/updatenlp.png)

### Linking the intent and defining a response <a id="defineresponse"></a>

You have now taught the NLP to understand your query, congrats! The only thing left to do is teaching Choo Choo how to respond. You can do this by adding a new Bot dialog.

* Click on Bot dialogs menu item in the navigation pane
* Open the General flow
* Click on `+ Bot message`
* Enter `who are you` as the name
* Choose the `introduction` dialog state as the parent
* Link the intent to the bot dialog in the bot dialog NLP tab

![](../.gitbook/assets/image%20%2822%29.png)

* Go to `Bot Message` tab and add a text message that says:

> I am Choo Choo, your personal assistant for booking train tickets

Your screen should look like this:

![](../.gitbook/assets/image%20%28116%29.png)

{% hint style="info" %}
You can view the intents linked to a bot dialog, along with input and output context in the bot dialog box.

![](../.gitbook/assets/image%20%28231%29.png)
{% endhint %}

* Click on `Create`

![](../.gitbook/assets/image%20%28342%29.png)

We have defined the `introduction` bot dialog as the parent dialog state here. Parent bot dialogs do not limit or define the possible flow of the dialogue, they are a visual tool to structure the conversational flow and keep the overview. They make it easier to create complex conversational flows. Bot dialogs can be reached from any point in the conversation by linking a bot dialog to an intent, although you can restrict them too by using Contexts. This mimics the way humans talk, jumping from one subject to another.

### Adding multiple messages

As an exercise, you can now add multiple messages to the `who are you` bot message.  You can do this via Bot Dialogs &gt; Flow &gt; Edit 'Who are you' Bot Message.

Update the single message to show multiple messages:

* `I'am Choo Choo.`
* `Your train traveling assistant.`
* `You can book a train ticket or ask my support.`
* `After your booking I'll keep you updated about train details so you don't have to worry about your journey.`

This makes your bot more user-friendly and human.

### Testing your bot

Time to test your bot! Click on `Test your bot` at the bottom right to test your conversational flow. To get a feel of your bot's performance, ask the same question a couple times, including different ways of asking the question that are different to the expression you used to train. If a question is not recognized correctly when it should be, you'll have to go back to the `NLP` tab, add the questions as an expression, and retrain the NLP model. You can do this as many times as needed, the model will just keep on improving.

![](../.gitbook/assets/image%20%28184%29.png)

{% hint style="info" %}
This 'Test your bot' is also referred to as the emulator.
{% endhint %}

Open the Debugger and select a user message in the `Messages` list to retrieve detailed information about the bot's response message, the user funnel and context, Natural Language Processing results and user session data. 

### Using multiple languages

To configure the translations of the secondary language message and other text, go to the `Translations` module under the `Bot dialogs` tab. For more information, see the [Translations](../bot-answers/dialog-state/translations.md) module in this documentation.

When you have created a multilingual bot, you will notice that you can switch the active language in quite a few pages in the menu bar at the top, upper right. You can add expressions for all intents in the secondary language \(if you have one\) in the NLP tab.

![](../.gitbook/assets/image%20%28176%29.png)

For more information on how to retrieve the user's preferred language, head to [Multi-language bots](../understanding-users/multilanguage-bots.md).

{% hint style="info" %}
The [next tutorial](tutorial-getting-information-using-entities.md) is about getting user input.   
We will ask the user for input that is needed for booking a train ticket.
{% endhint %}

