# Intent recognition below threshold

Whenever an intent is recognized below the NLP threshold score, this will give the 'not understood' bot dialog:

![](../../.gitbook/assets/image%20%28484%29.png)

In the example above, we have a bot to check where ordered packages are. This is what the user would like to know, but a 'not understood' is returned because the Intent is recognized below 80% - the NLP threshold. This is not a great user experience, even though we are 60% sure of the question the user is asking.

This tutorial will show how to configure specific 'not understood' messages, whenever the expression is not above the NLP threshold. This will have the added value that the user feels more understood by the bot, and will find their answer more quickly.

## 1. Check your NLP Threshold score

In NLP &gt; NLP Threshold you can check what the current configuration is of your [threshold](https://docs.chatlayer.ai/understanding-users/natural-language-processing-nlp/settings). For this example, let's say we have a threshold for intents at 80%, and we would like to give a specific error message for all intent recognition between 60% and 80%.

## 2. Get intent variables

In the debugger, we need to get the variable for the intent recognition. Open de debugger after using an expression of choice, and find the `NLP` part:

![](../../.gitbook/assets/image%20%28483%29.png)

The variable we need for the score \(of 60,32% just like in the first image\) and for the name are:

`internal.nlp.intent.score`

`internal.nlp.intent.name`

## 3. Configure Not Understood

Now we need to change the 'not understood' bot message to a Go-To. 

![](../../.gitbook/assets/image%20%28486%29.png)

We need to create a condition for a specific intent. Let's configure that for the 'lost package' intent:

![](../../.gitbook/assets/image%20%28482%29.png)

Here, we will create two new bot messages: One specifically for lost packages expressions and a general one, for other intents.

## 4. Fill in bot messages

Fill in the bot messages, in this example, we will do the following:

* Do I understand correctly that you have a question about your lost package? \(specific not understood message\)
* Sorry I did not understand, can you rephrase? \(general not understood message\)

## 5. Try it out!

Let's try again the sentence we used in the beginning of this tutorial:

![](../../.gitbook/assets/image%20%28485%29.png)

Voila! As you can see, the intent is still not recognized above 80%, but the user feels more understood this way. They can immediately correctly start their 'lost package' flow, without having to rephrase their question. A better user experience than what we started with in the beginning of this tutorial! 

## Future use

This tutorial is a great alternative if you do not want to lower your overall NLP threshold score, or for bots that do not have a big range of expressions \(yet\). Be aware, that this needs to be implemented for separately for multiple intents in order to create specific 'not understood' messages. To check which intent is recognized and with the score, check out the NLP &gt; Train tab. There you can see which intents are most often used by users and give you an indication which intents need extra expressions or a specific 'not understood' message.



