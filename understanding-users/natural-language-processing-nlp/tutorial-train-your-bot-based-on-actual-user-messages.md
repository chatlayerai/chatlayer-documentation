# Training your bot with real user input

After you published your bot, you want to keep training the NLP model with real user input. By doing so, your bot becomes smarter over time and can support more diverse expressions too. To do so, you can use the NLP `Train` tab.

### Getting started

Before you can use the `train` tab, you should already have some real training data – either from users or by talking to the bot yourself on Facebook Messenger. If you haven't published your bot on Facebook Messenger yet, please follow the steps in the `Channels` tab on the platform.

![A user is talking to the bot, providing it with real data to train](../../.gitbook/assets/screen-shot-2018-03-04-at-11.28.16.png)

{% hint style="info" %}
All conversations happening on channels will be displayed in the `Train` tab on the platform. Conversations that occur in the debugger \(the testing environment on the platform\) will be ignored.
{% endhint %}

Let's have a look at the NLP `train` tab. As you can see in the image below, all user messages are labeled by the NLP model. Each message get's a proposed intent and a confidence score so that you can evaluate these messages. The NLP also identifies possible entities and values.

![A quick glance at the NLP train tab](../../.gitbook/assets/image%20%2893%29.png)

### Checking your data before training

Before you add an expression, you need to make sure that it's a relevant one. Not all things said by a user are qualitative enough for the bot to train on. **Never add all suggested expressions without checking them** as this can confuse your bot and mess up its training.

For example, consider the following expression, said by a user to your bot:

![](../../.gitbook/assets/image%20%28601%29.png)

Even though our NLP is really smart, it doesn't always suggest the correct intent. In this case, the bot did not contain an intent referring to the date or time, which is why the NLP classified the expression under a wrong intent. This is why **you should always check an expression** before adding it to the NLP.

We also recommend scoping expressions in case they contain unnecessary information. Let's look at the following example:

![](../../.gitbook/assets/image%20%28598%29.png)

In this case, the NLP did find the correct intent, but the confidence score is rather low because the expression contains a lot of unnecessary information. It's best practice to **delete this information from the expression before adding it to the intent**, so that the bot trains on relevant info only.

![Click on the image to enlarge it](../../.gitbook/assets/image%20%28599%29.png)

{% hint style="info" %}
**Let's recap:**

* Always check an expression before adding it to the bot
* Make sure the expression is linked to the right intent with a high confidence score
* Clean up the expression if necessary to remove irrelevant data
{% endhint %}

Now back to our bot example:

![](../../.gitbook/assets/image%20%28600%29.png)

* Click on '+' to add the expression to the suggested intent

{% hint style="warning" %}
In the draft environment, you can see expressions from both the DRAFT and LIVE environment. Make sure you add the expressions to your DRAFT environment so that the next published version on the LIVE environment contains these new expressions as well. 
{% endhint %}

* Let's do a second test by sending a new user message on Facebook Messenger

![](../../.gitbook/assets/screen-shot-2018-03-04-at-11.34.20.png)

* Hmm, it seems that the entities are not recognised correctly
* Adjust the expression by adding these entities, then train and publish your model and test it in the NLP test section. If needed, add similar expressions to the intent

### Tips & things to keep in mind

1. Expressions from the "Test your bot" window will not be included in the Train tab
2. If two users use the exact same expression, it will only show up once in the Train tab
3. If an expression from a user is an exact match with an expression already included in your model, it will not be included in the Train tab
4. In the 'Score' column you will see the score of the NLP model at the time the expression was said. This might differ from the score that the current NLP model gives this expression

