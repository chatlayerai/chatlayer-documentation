# Training your bot with actual user input

Once you have configured your bot, you want to train your NLP models with actual user input. By doing so, your bot becomes smarter and smarter over time and can support different kinds of expressions. To do so, you can use the NLP Train section.

* To get started, you should create some actual training data by talking to your bot on Facebook Messenger. If you haven't activated your bot on Facebook Messenger yet, follow the steps in the Channel wizard in the platform

![](../../.gitbook/assets/screen-shot-2018-03-04-at-11.28.16.png)

{% hint style="info" %}
All conversations from your channels will be loaded into the Train module. Conversations from the emulator \(tests\) are ignored.
{% endhint %}

* Look at the train NLP section. As you can see, the user messages have been labeled by the NLP model so that you can evaluate these messages. It seems that your model has detected the correct intent and entity values

![](../../.gitbook/assets/image%20%2893%29.png)

* Click on '+' to add this candidate expression as a validated expression

{% hint style="warning" %}
In your DRAFT environment you can see expressions from both the DRAFT and LIVE environment. Make sure you will add the expression to your DRAFT environment, and with the next published version your new expression will be in the LIVE environment as well. 
{% endhint %}

* Let's do a second test by sending a new user message on Facebook Messenger

![](../../.gitbook/assets/screen-shot-2018-03-04-at-11.34.20.png)

* Hmm, it seems that the entities are not recognised correctly
* Adjust the expression by adding these entities, then train and publish your model and test it in the NLP test section. If needed, add similar expressions to the intent

To summarise, we recommend using the following flow to analyse expressions coming directly from users in the Train tab:

![](../../.gitbook/assets/nlp-high-level-architecture-2x.png)

There are a couple of things you should keep in mind when using the Train tab:

1. Expressions from the "Test your bot" window will not be included in the Train tab
2. If two users use the exact same expression, it will only show up once in the Train tab
3. If an expression from a user is an exact match with an expression already included in your model, it will not be included in the Train tab
4. In the 'Score' column you will see the score of the NLP model at the time the expression was said. This might differ from the score that the current NLP model gives this expression

