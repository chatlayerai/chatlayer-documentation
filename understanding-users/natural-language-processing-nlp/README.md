# Natural Language Processing (NLP)

The Natural Language Processing (NLP) engine is the underlying code that enables your bot to understand the natural language used by us humans.&#x20;

Understanding natural language isn't easy: it takes us more than 12 years and hundreds of examples to understand the 20,000 most common words. Imagine how hard it must be for computers! To train the NLP engine, we need huge amounts of data. Luckily, we rely on pre-trained models that have a lot of smarts built in. Our NLP engine will take care of spelling mistakes, synonyms, slang, varying word order, etc ...

## The basics

![](<../../.gitbook/assets/image (697) (1).png>)

Whenever a user sends a message to the bot, the bot will check if that message is related to any of the expressions that are part of the NLP engine. For example, when a user types _'Get me a flight ticket,'_ the __ NLP will check if this sentence matches any of its expressions and check if this message contains similar words as the expressions. In the example above, the NLP gives a 93% confidence score that _'Get me a flight ticket'_ belongs to the intent _'Book flight'_. Because this sentence is recognised above the [NLP threshold](https://docs.chatlayer.ai/understanding-users/natural-language-processing-nlp/settings), the response that is linked to this intent will be shown to the user.

## Intent

An intent refers to **the goal** that a customer has in mind when talking to a bot, it's all about what the user wants to get out of the interaction.&#x20;

Some examples of intents:

* Book train ticket
* Talk to a human
* Create support ticket
* Greeting
* Yes

It is important to scope your intents well so the bot can recognise them more easily. Learn how to create good intents [here](https://docs.chatlayer.ai/tips-and-best-practices/how-to-nlp).

## Expressions

Expressions are example sentences of a specific intent: they're all the different ways a user can express their intent. It's crucial for an intent to contain diverse expressions so that the NLP can give more accurate results.

Here are a few expressions for the intent 'who are you'

* Who are you?
* What is your name?
* Do you have a name?
* Tell me more about yourself
* Please, I'd like to know who I am talking to
* How should I call you?
* who is choo choo?
* Tell me what your name is
* Who are ya?
* What do people call you?

Here are a few expressions for the intent 'order pizza'

* I'd like to order some pizza please
* Can I get a pizza to go?
* I want a pizza margherita
* I'd like to order some food
* Can you help me order pizza?
* I'm in the mood for some pizza tonight!

{% hint style="info" %}
Please note that our NLP engine has a limit of 1000 characters. Messages with more than 1000 characters will always trigger the 'not understood' dialog. To guide the user, you can create a customized 'not understood' message for these long messages, as described [here](https://docs.chatlayer.ai/bot-answers/settings#maximum-message-length).&#x20;
{% endhint %}

## Entities

Entities are important pieces of information that can be found in expressions. In some cases, you'll want to save these as variables so you can re-use them later in the conversation.&#x20;

Find out more about entities by clicking the link below:

{% content-ref url="synonym-entities/" %}
[synonym-entities](synonym-entities/)
{% endcontent-ref %}

## Updating the NLP

On every section in our platform, you'll find an 'update NLP' button at the top right of the screen. When you see a spinner icon instead of the brain symbol, the NLP model is (still) training.

![](<../../.gitbook/assets/image (162).png>)

New changes made to the NLP model (such as adding a new intent or changing certain entities) won't go through until the NLP was updated. We recommend to update the NLP after any major NLP changes, such as many new expressions or intents. That way, you can easily test what effect these changes will have on your bot.

{% hint style="info" %}
Do you want to learn how you can improve your NLP model? You can find tips and tricks in [this article](https://docs.chatlayer.ai/tips-and-best-practices/how-to-nlp).
{% endhint %}

## Intent pack

We've created a few intent packs so you can quickly get started and train your NLP model. You can add these pre-built intents directly in the platform by clicking on 'intents' in the NLP section and then on the top right, 'Add Prebuilt Intent'

&#x20;![](<../../.gitbook/assets/image (683) (1).png>)

Then you'll get a pop-up screen showing you all the pre-built intents you can add:

![](<../../.gitbook/assets/image (677) (1) (1).png>)
