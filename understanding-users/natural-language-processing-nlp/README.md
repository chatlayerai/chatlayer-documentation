# Natural Language Processing \(NLP\)

The Natural Language Processing \(NLP\) engine is the underlying code that's used to understand the natural language that is used by the user.

Understanding language isn't easy: it takes us humans about 12 years and hundreds of examples to understand the most common 20,000 words. And computers are not so different. To train an NLP engine, we need huge amounts of data. Luckily, we rely on pre-trained models that have a lot of smarts built in. Our NLP engine will take care of spelling mistakes, synonyms, slang, varying word order, etc ...

## Intent

An intent is a joint name for a specific action your user can take. Intents are single blocks of meaning that the NLP can recognise. For example, an intent can be a question, a statement, an answer to a question or a greeting.

Some examples of intents:

* Can you book me a train ticket from Brussels to Amsterdam?
* Who are you?
* I want to leave at 9 pm
* Yes
* Thank you
* I want to speak to a human

Tip: if two of your intents are very similar in terms of expressions’ syntax or content, you might want to merge them. For example, let's look at our bot responsible for booking train tickets. Imagine you'd also like to offer bus tickets. You could create an extra intent for booking bus tickets, but the expressions in each intent would be very similar, with only the transportation mode changing from time to time. It would be better to only have one intent handling reservations, and an **entity** to catch the requested vehicle type. 

{% hint style="info" %}
It’s important to have a roughly equal number of expressions for each intent. Even if it usually takes more examples to train your most important intent than your second-order ones, strive to keep their number of expressions around the same amount. This helps avoid a bias towards intents with a large expression count.
{% endhint %}

## Expressions

Expressions are example sentences for a specific Intent. In industry literature, they are sometimes called 'utterances'. The more Expression you add to an Intent, the more accurately it will be recognized. It is crucial for an Intent to have a wide variety of expressions to give accurate results. The more expression you can think of, the better the result of the NLP and the 'smarter' your bot will appear.

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

The more expression you have, and the more varied, the more accurate your bot will respond.

## Entities

Entities are important pieces of information that are extracted from an expression. Often, you want to store these in a separate variable so you can re-use them later. 

Find out more about entities here:

{% page-ref page="synonym-entities.md" %}

## Updating the NLP

On every page in our tool, you will find an 'update NLP' button at the top right of the screen. When you see a spinner instead of a brain symbol, your NLP model is still training.

![](../../.gitbook/assets/image%20%28162%29.png)

{% hint style="info" %}
Do you want to learn how you can improve your NLP model? You can find tips and tricks in the article below.

{% page-ref page="../../tips-and-best-practices/how-to-nlp.md" %}
{% endhint %}

## Intent pack

We've created a small intent pack in the most frequently used languages to allow you to quickly get started with your NLP model. This pack contains intents such as "yes", "no", "thank you", "who are you", and chit chat intents such as "tell me a joke". Download them here:

{% file src="../../.gitbook/assets/default-intents-chit-chat-en.csv" caption="Basic intent pack EN" %}

{% file src="../../.gitbook/assets/default-intents-chit-chat-fr.csv" caption="Basic intent pack FR" %}

{% file src="../../.gitbook/assets/default-intents-chit-chat-nl.csv" caption="Basic intent pack NL" %}

