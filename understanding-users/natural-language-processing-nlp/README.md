# Natural Language Processing \(NLP\)

The Natural Language Processing \(NLP\) engine is the underlying code that enables your bot to understand the natural language used by the user.

Understanding natural language isn't easy: it takes us humans about 12 years and hundreds of examples to understand the 20,000 most common words and computers are not so different. To train the NLP engine, we need huge amounts of data. Luckily, we rely on pre-trained models that have a lot of smarts built in. Our NLP engine will take care of spelling mistakes, synonyms, slang, varying word order, etc ...

## Intent

An intent is a joint name for a specific action a user can take. They're single blocks of meaning that the NLP can recognise. For example, an intent can be a question, a statement, an answer to a question or a greeting.

Some examples of intents:

* Can you book me a train ticket from Brussels to Amsterdam?
* Who are you?
* I want to leave at 9 pm
* Yes
* Thank you
* I want to speak to a human

{% hint style="info" %}
It’s important to roughly have an equal number of expressions for each intent. Even if it usually takes more examples to train your most important intent compared to the others, do strive to keep the number of expressions consistent over intents. This will help avoid creating a bias towards intents with a large expression count
{% endhint %}

### Intent scoping

If two of your intents are very similar in terms of meaning and/or use case, you should merge them to avoid confusing the NLP engine.

For example, let's look at our bot responsible for booking train tickets. Imagine that, besides train tickets, you'd also like to offer bus tickets. You could create an extra intent for booking bus tickets, but the expressions would be very similar to the intent for booking train tickets, with only the transportation mode changing from time to time. In this case, it would be better to only have one intent for booking tickets, and an [**entity**](https://docs.chatlayer.ai/understanding-users/natural-language-processing-nlp/synonym-entities) to catch the requested vehicle type.

## Expressions

{% hint style="info" %}
Please note that our NLP engine has a limit of 1000 characters. That means, messages with more than 1000 characters will always go to 'not understood'. You can configure a customized 'not understood' message for long user input in the settings, as described [here](https://docs.chatlayer.ai/bot-answers/settings#maximum-message-length). 
{% endhint %}

Expressions are example sentences for a specific intent: all the different ways for a user to express the intent. In industry literature, they are sometimes also called 'utterances'. It is crucial for an intent to have a wide variety of expressions so that the NLP can give more accurate results and your bot will appear smarter.

Here are some examples of expressions for the intent 'who are you'

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
* Are you a robot?
* Do you have a name?

## Entities

Entities are important pieces of information which can be found in an expression. Often, you'll want to save them as a variable so you can re-use them later. 

Find out more about entities by clicking the link below:

{% page-ref page="synonym-entities/" %}

## Updating the NLP

On every screen in our platform, you will find an 'update NLP' button at the top right of the screen. When you see a spinner icon instead of a brain symbol, your NLP model is \(still\) training.

![](../../.gitbook/assets/image%20%28162%29.png)

{% hint style="info" %}
Do you want to learn how you can improve your NLP model? You can find tips and tricks in the article below.

{% page-ref page="../../tips-and-best-practices/how-to-nlp.md" %}
{% endhint %}

## Intent pack

We've created a small intent pack in the most frequently used languages allowing you to quickly get started with your NLP model. This pack contains intents such as "yes", "no", "thank you", "who are you", and chit chat intents such as "tell me a joke". 

You can add these pre-built intents directly in the platform, or by downloading them below:

{% file src="../../.gitbook/assets/default-intents-chit-chat-en.csv" caption="Basic intent pack EN" %}

{% file src="../../.gitbook/assets/default-intents-chit-chat-fr.csv" caption="Basic intent pack FR" %}

{% file src="../../.gitbook/assets/default-intents-chit-chat-nl.csv" caption="Basic intent pack NL" %}

