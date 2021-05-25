# Intent recognition below threshold

Whenever an expression is recognised, but falls below the NLP confidence score, the bot will display a 'not understood' bot dialog. 

See the example below: the expression "Can you check where my ordered parcel is?" could be linked to the 'lost package' intent, or the 'general.no' intent. Since neither of them meet the 80% confidence score, it results in a 'not understood' dialog.

![The confidence score is too low for the bot to recognise this expression correctly](../../.gitbook/assets/image%20%28484%29.png)

In the tutorial below, we will show you how to configure a specific 'not understood' message for whenever an expression doesn't meet the NLP threshold. This message will try and figure out what the user meant, making the bot look smarter and helping the user find their answer faster.

## Step 1: Check your NLP Threshold score

In the left column, under `NLP`, click on `NLP Threshold`. There you can check what the current confidence score is of your NLP [threshold](https://docs.chatlayer.ai/understanding-users/natural-language-processing-nlp/settings). In this example, let's say we have a threshold for intents at 80%, and we would like to give a specific error message for all intent recognition between 60% and 80%.

## Step 2: Get intent variables

In the bot's debugger, we need to get the variable so we can do intent recognition. Open the debugger after using an expression of your choice, and go the `NLP` part:

![](../../.gitbook/assets/image%20%28483%29.png)

The variable we need for a confidence score &gt; 60% and for the name are:

`internal.nlp.intent.score`

`internal.nlp.intent.name`

## Step 3: Configure the 'Not Understood' dialog

Now we need to change the 'not understood' bot dialog into a go-to dialog:

![Click on Go To to convert this dialog into a go-to dialog](../../.gitbook/assets/image%20%28486%29.png)

Then we need to create a rule for the specific intent. Let's create a rule for the 'lost package' intent:

![](../../.gitbook/assets/image%20%28482%29.png)

Here, we will create two new bot messages: One specifically for expressions related to lost packages, and a general one, for all other intents that were not understood correctly.

## Step 4: Fill in the bot messages

Write some text in the bot messages, such as:

* Specific not understood message: "Do I understand correctly that you have a question about your lost package?"
* General not understood message: "Sorry, I did not understand. Can you please rephrase?"

## Step 5: Test your bot

Let's try again the sentence we used at the beginning of this tutorial:

![](../../.gitbook/assets/image%20%28485%29.png)

It works! As you can see, the intent is still not recognised correctly \(above 80% confidence score\) but the user feels better understood this way. When they reply 'yes' to this message \(use context!\) they can immediately start the 'lost package' flow, without having to rephrase their question. 

This creates a much better user experience than before you applied the steps in this tutorial! 

## Scaling this set-up

This tutorial is a great alternative for when you don't want to lower your overall NLP confidence score, or for when bots do not have a big range of expressions \(yet\). But be aware that these steps need to be implemented separately for each intent in order to create specific 'not understood' dialogs. 

To check which intent is recognized under what score, check out the `Train tab` under the `NLP` section. There you can see which intents are used most by users, which gives you an indication which intents need extra expressions, or a specific 'not understood' message.



