---
description: >-
  By creating specific not understood messages, the bot seems smarter and gives
  users a much better experience.
---

# How to create better not understood messages

There are a few ways to make your bot respond in a smarter way when it is unable to understand the user. What if the bot could name the topic the user was asking about, so the user at least knows the bot kinda understood, but is unable to reply? This type of bot reply can be built by tweaking the NLP Threshold score and using specific variables.&#x20;

## Option 1: using the NLP Threshold

In the tutorial below, you will learn how to configure a specific 'not understood' message for whenever an expression doesn't meet the NLP threshold. In this dialog, the bot will try and figure out what the user meant, making the bot look smarter and helping the user find their answer faster.

See the example below: the expression "Can you check where my ordered parcel is?" both triggers a recognition rate for the intent 'lost package' and the intent 'general.no'. Since neither of those meet the 80% NLP confidence score, the bot shows a 'not understood' dialog.

![The confidence score is too low for the bot to recognise this expression correctly](<../../.gitbook/assets/image (484).png>)

### Step 1: Check your NLP Threshold score

In the left column, under `NLP`, click on `NLP Threshold`. There you can check what the current confidence score is of your NLP [threshold](https://docs.chatlayer.ai/understanding-users/natural-language-processing-nlp/settings). In this example, let's say we have a threshold for intents at 80%, and we would like to give a specific error message for all intent recognition between 60% and 80%.

### Step 2: Get intent variables

In the bot's debugger, we need to get the right variable so we can use it for intent recognition. To do so, open the debugger after using an expression of your choice. Underneath the title _READ-ONLY SESSION DATE_, click on `nlp` . You should see something like this:

![](<../../.gitbook/assets/image (483).png>)

The variables we need for a confidence score over 60% and for the name are:

`internal.nlp.intent.score`

`internal.nlp.intent.name`

### Step 3: Configure the 'Not Understood' dialog

Now we need to change the 'not understood' bot dialog into a go-to dialog:

![Click on Go To to convert this dialog into a go-to dialog](<../../.gitbook/assets/image (486).png>)

Then we need to create a rule for the specific intent. Let's create a rule for the 'lost package' intent:

![](<../../.gitbook/assets/image (482).png>)

Here, we will create two new bot messages: One specifically for expressions related to lost packages, and a general one, for all other intents that were not understood correctly.

### Step 4: Fill in the bot messages

Write some text in the bot messages, such as:

* Specific not understood message: \
  "Do I understand correctly that you have a question about your lost package?"
* General not understood message: \
  "Sorry, I did not understand. Can you please rephrase?"

### Step 5: Test your bot

Let's try again the sentence we used at the beginning of this tutorial:

![](<../../.gitbook/assets/image (485).png>)

It works! As you can see, the intent is still not recognised correctly (above 80% confidence score) but the user feels better understood this way. When they reply 'yes' to this message (use context!) they can immediately start the 'lost package' flow, without having to rephrase their question.&#x20;

This creates a much better user experience than before you applied the steps in this tutorial!&#x20;

### How to scale this set-up

This tutorial is a great alternative for when you don't want to lower your overall NLP confidence score, or for when bots don't have a lot of expressions (yet). Be aware that these steps need to be implemented separately for each intent in order to create specific 'not understood' dialogs.&#x20;

To check which intent is recognized under what score, check out the `Train tab` under the `NLP` section. There you can see which intents are used most by users, which gives you an indication which intents need extra expressions, or a specific 'not understood' message.



## Option 2: Using variables

Another option to create specific 'not understood' messages is to use variables. Many bots have a set-up like below, where you can add variables to buttons or Go-Tos to save the route users have taken in the bot:

![In the example above, the variable 'topic' saves the route the user has taken in the bot](<../../.gitbook/assets/image (686) (1) (1) (1).png>)



Then, change your 'not understood' in a 'Go To' (see step 3 in the tutorial above) and create a logic as such:

![](<../../.gitbook/assets/image (670) (1).png>)

Make sure to fill in your specific not understood bot messages, just like in Step 4 of the previous tutorial. After that, you are all set to give users a smarter 'not understood'  experience!
