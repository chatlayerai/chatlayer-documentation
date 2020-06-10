# Natural Language Processing \(NLP\)

The Natural Language Processing \(NLP\) engine is the underlying code that's used to understand the natural language that is entered by the user.

Understanding language isn't easy: it takes us humans about 12 years and hundreds of examples to understand the most common 20,000 words. Computers are no different. To train an NLP engine, huge amounts of data are needed. Luckily, we rely on pre-trained models that have a lot of smarts built in. The NLP engine will take care of spelling mistakes, synonyms, slang, varying word order, etc...

## Intent

An intent is a joint name for a specific action your user can do. Intents are single blocks of meaning that the NLP can recognise. For example an intent can be a question, a statement, an answer to a question or a greeting.

Some examples of intents:

* Can you book me a train ticket from Brussels to Amsterdam?
* Who are you?
* I want to leave at 9pm
* Yes
* Thank you
* I want to speak to a human

## Expressions

Expressions are example sentences for a specific Intent. In the literature, this will sometimes be called 'utterances' as well. The more Expression you add to an Intent, the more accurately it will be recognized. It is crucial for an Intent to have a wide variety of expressions to give accurate results. The more expression you can think of, the better the result of the NLP will be and the 'smarter' your bot will be

Some examples of expressions for an intent 'who are you'

* Who are you?
* What is your name?
* Can I know your name?
* Tell me more about yourself
* Please, I'd like to know who I am talking to
* How should I call you
* who is choo choo
* tell me what your name is
* Who are ya
* What do people call you?
* Are you a robot?
* Do you have a name?

The richer the variety of expression you have, the more accurate your bot will respond.

## Entities

Entities are important pieces of information that are extracted from an expression. Often, you want to store these in a separate variable for re-using them later. See the tutorial 'Getting information using entities' for learning how to use them.

## Updating the NLP

On every page there is an update NLP button on the top right of the screen, visible on all pages. When you see a spinner instead of a brain icon, your NLP model is still training.

![](../../.gitbook/assets/image%20%28162%29.png)

{% hint style="info" %}
Do you want to learn how to improve your NLP model? Learn about the best practices our article:

{% page-ref page="../../tips-and-best-practices/how-to-nlp.md" %}
{% endhint %}

## Intent pack

We've created a small intent pack in the most frequently used languages to allow you to quickly get started with your NLP model. This pack contains intents such as "yes", "no", "thank you", "who are you", and Chit Chat intents such as "tell me a joke".

{% file src="../../.gitbook/assets/default-intents-chit-chat-en.csv" caption="Basic intent pack EN" %}

{% file src="../../.gitbook/assets/default-intents-chit-chat-fr.csv" caption="Basic intent pack FR" %}

{% file src="../../.gitbook/assets/default-intents-chit-chat-nl.csv" caption="Basic intent pack NL" %}

