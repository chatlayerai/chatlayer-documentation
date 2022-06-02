---
description: >-
  In the previous tutorial, you learned about intents and expressions. In this
  section, we'll cover another important part of bot building: entities.
---

# Detecting information in expressions

You will learn how to detect valuable information, mentioned by a user in an intent, using **contextual entities**. Entities are important pieces of information that are extracted from an expression. There are four types of entities. You can find more information about them here:

{% content-ref url="../understanding-users/natural-language-processing-nlp/synonym-entities/" %}
[synonym-entities](../understanding-users/natural-language-processing-nlp/synonym-entities/)
{% endcontent-ref %}

In this tutorial we will focus on one entity type: contextual entities. Contextual entities use machine learning to identify entities in sentences by learning what type of word your entity is, where it's placed in the sentence, and what the specific context is.

You want to store these contextual entities in a separate variable so you can re-use them later on. Read more about the difference between entities and variables [here](https://docs.chatlayer.ai/understanding-users/natural-language-processing-nlp/synonym-entities#the-difference-between-entities-variables-and-values). In the next tutorial, you will learn how you can ask explicitly for missing information.

Let's say we have an intent that tells us the user wants to book a train ticket. A few different expressions could be:&#x20;

* I want a train ticket
* I need a ticket
* Can I book a train ticket here?

This assures the bot dialog, linked to the corresponding intent, to be triggered when the user says one of these expressions.

But what would happen if the user says:

* I want a train ticket to **Amsterdam**
* I need to go to **Antwerp tomorrow**
* Can I book a train ticket to **Brussels** please?

These expressions contain valuable information. We want to make sure we capture that information, in this case the destination and time, and save it as **entities**. We then have expressions with an entity in them.

We are now going to create a new intent with some expressions for booking a train ticket. Some of these expressions will contain a contextual entity, but some will not.

## Step 9: Creating contextual entities

Not all users will immediately mention their destination, so let's make sure we train our intent without those specific entities as well:

* Go to `NLP` > `Intents`
* Click on `Add Intent`
* Add a new intent called `book train ticket`
* Add some simple expressions, like:
  * I want a train ticket
  * I need a ticket
  * Can I book a train ticket, please?

{% hint style="info" %}
If you have trouble doing this, please read the [previous tutorial](tutorial-adding-content.md).
{% endhint %}

Next, it's time to add a contextual entity.

* Go to `Intents` and select your `book train ticket` intent
* Click on `+ Add expression` to create a new expression
* Enter an expression that contains an entity, for example:

> I want to book a ticket from Brussels to Paris

* Select `Brussels` in this sentence

![](<../.gitbook/assets/image (619).png>)

* Click on the '+ entity' icon in the bottom right of the expression box to create a new contextual entity for 'Brussels' &#x20;

![The '+ entity' icon](<../.gitbook/assets/image (651).png>)

* Brussels is the location the user wants to depart from, so we will name this entity `origin`&#x20;
* Type `origin` in the `Create new entity` field and click on 'Create new entity' to confirm

![Creating a new entity called 'origin'](<../.gitbook/assets/image (634).png>)

* Brussels will be added to the list of possible values for the @origin variable
* Do the same thing for `Paris` as a 'destination' entity

You will then have the following set-up for this expression:

![Creating multiple entities in an expression](<../.gitbook/assets/image (635).png>)

We now save added the expression 'I want to book a ticket from @origin to @destination', where 'Brussels' is a value for @origin and 'Paris' is a value for the entity @destination.&#x20;

* Add some other values to the 'origin' and 'destination' entities in the expression field. These will be saved for all future expressions. You can add these in the 'Create new value' box and pressing enter.
* Add more expressions that contain the entities **origin** and **destination**

Once you have added more Entity values, these will also show up in the menu \
`Entities` > `Contextual Entities`

![](<../.gitbook/assets/image (432).png>)

*   Now, let's add some more expressions to our `Book train ticket` intent. Some ideas for expressions:

    * Can I book a train from Cologne to Brussels?
    * I need to be in Rotterdam
    * I need a train to London
    * I want to travel to Lyon
    * I want to buy a ticket from Moscow to Vladivostok
    * I need a ticket from New York to Baltimore



{% hint style="info" %}
When typing a new expression, you can add entities and entity values in two ways:

1. Typing @ and then the name of the entity, for example @origin. You can add a new value in the box below with 'Create new value'
2. Selecting an entity value and clicking the +entity value button. For example, select 'Cologne', click the +button. This will result in 'Cologne' being changed into @origin and 'Cologne' will be a value of @origin
{% endhint %}

* Make sure you retrain the NLP model by clicking the `Update NLP` button in the right upper corner.

This will now result some expressions for the `Book train ticket` intent, and entity values, like so:

![Adding expressions to an intent](<../.gitbook/assets/image (650).png>)

## Step 10: Testing contextual entities

After we have retrained our model, let's see if its good enough to recognise the destination entity.

* Go to `NLP` >`Test` to open the testing console&#x20;
* Write 'I would like to go to Brussels from Amsterdam' as the expression to be tested
* Click on `Test`

You'll see that the entity gets recognized with a 99.93% confidence. The results will be different based on your training set. If the entity is not recognized correctly, you can add it here as a training expression immediately by clicking `+Add expression`.&#x20;

{% hint style="warning" %}
Make sure you retrain the NLP model before testing newly added expressions
{% endhint %}

![Testing an expression](<../.gitbook/assets/image (646).png>)

Now we know how to add intents, create expressions and entities, however we still need to create a conversation so the user can talk to Choo Choo and our bot replies accordingly. Let's add some bot messages in the next step.

## Step 11: Using variables in messages

When a user says something containing an entity, and the entity is successfully detected, our tool will automatically store the entity as a **variable** for that specific user. &#x20;

At the moment, when you test your bot, the user is stuck after giving the information about the ticket:

![The bot does not understand yet](<../.gitbook/assets/image (620).png>)

However, we do see some positive items, namely that the 'origin' and 'destination' are stored correctly as variables. You can see this by opening the debugger by clicking  'Debugger' (with the magnifying glass icon) in the emulator. In the 'Debugger' tab, you can scroll down and you see this:

![](<../.gitbook/assets/image (439).png>)

So even though the sentence did give an error message, these entities are correctly recognized in the user input. This means the variable 'origin' is now saved with a variable value 'Brussels' and the variable 'destination' with the value 'Paris'. Also, in the ''NLP Result' tab we see that the intent was recognised correctly, that's great! Let's now work on removing that error message first.

The error message is caused by the fact that the intent `Book train ticket` does not have a bot dialog linked to it. So even though it is correctly recognised, we are not telling the bot what to do when that intent is recognised.&#x20;

We can change that by adding a new Bot message:&#x20;

* In the menu Bot dialogs, open the 'General' flow,  create a bot dialog of the type 'Bot message' `book train ticket`. Open the 'NLP' tab, and choose the `Book train ticket` intent in the 'Intent' dropdown.&#x20;
* In the 'Settings' tab, name the bot message `Book train ticket`
* Add a new text message with the text "So you want to go to `{destination}`, I can help you with that!"
* Click `Create` to save this bot message.

{% hint style="info" %}
To reuse the variable later on in the conversation, you can put it in between curly brackets like this: `{variable_name}`&#x20;

When writing this message to the users, Chatlayer will automatically substitute `{variable_name}` **** with the value of the variable. If the variable is empty, an empty space will be shown.
{% endhint %}

![Creating a bot reply](<../.gitbook/assets/image (631).png>)

We have now linked the `Book train ticket` to this bot message, great job! This means that, when a user says something that triggers the `Book train ticket` intent, this bot message will show.&#x20;

## Step 12: Testing entities in the emulator

Now that we have linked everything, we are ready to test if everything is configured correctly by using the emulator.

* Open the emulator (the `Test your bot` tool on the bottom right)
* If needed, clear the last conversation by clicking 'Clear conversation' on the top right. This starts a new conversation
* Enter "I want to go to Amsterdam" and click on submit
* Open the debugger

In the tab 'NLP Result'  you can now see if the entity was recognized correctly:

![The entity 'destination' was correctly recognized](<../.gitbook/assets/image (615).png>)

{% hint style="info" %}
When creating new bot dialogs, you don't need to re-train the NLP
{% endhint %}

If you do not get the result as stated above, please check the following items in your bot:

* If your entity is recognised by the NLP but doesn't show up in with `{destination}` it did not pass the threshold of 80%. Try adding that value to your entity and re-train your model, or choose another destination
* If you get 'Sorry I didn't understand that', double check if your intent is linked to the Bot message and this is saved correctly.
* If your intent or expression is not recognised, try re-training your NLP again. &#x20;

Now we already have a great start with linking the intent and giving a response to the expression the user says. However, we want more information from the user. Let's add more expressions and entities.&#x20;

## Step 13: Multiple entities in one expression

You can add as many entities as you want to one expression. For Choo Choo, we want to more information from the user than just the destination and origin, to give a complete train-booking experience. Let's add more contextual entities!

* Go to the `Expressions` menu
* Click 'Add Expression'
* Select the `Book train ticket` intent

Create the following expression:

* I want to go from **Antwerp** to **Brussels** **tomorrow** at **9am** in **first** **class**

And create the following entities:

* origin: Antwerp
* destination: Brussels
* departure-date: tomorrow
* departure-time: 9am
* class: first class

_If you are having trouble adding these, scroll back to step 9 in this tutorial to read all about it._

![](<../.gitbook/assets/image (617).png>)

#### Additional suggestions for expressions

* I need to be in Paris next Thursday
* I need to be in New York on Friday
* I want to go to Brussels on Monday
* Friday I want to go from Antwerp to Amsterdam
* I want to travel in second class from Ghent to Brussel on Friday
* I want to travel in first class from Antwerp to Aalst on Thursday
* I like to book a first class ticket from Aalst to Brussels at nine o'clock
* Tomorrow I want to go from Antwerp to Brussels on the train from 9:00 in first class

{% hint style="info" %}
Keep in mind that NLP techniques are probabilistic in nature. When you try to capture five expressions in one sentence, it might not be able to recognise all of them correctly. As a general rule of thumb, you can start to expect reasonable results for one entity when the NLP was given at least 30 expression to learn from.&#x20;
{% endhint %}

Add more expressions with the new contextual entities to the intent. Ensure you have around 20 expressions for `Book train ticket` in total.

## Step 14: Missing entities

Let's test out your newly created expressions:

Update the wording in the `book train ticket` dialog to correctly display the entities:

_I need a ticket from Antwerp to Brussels tomorrow at 9am in first class_

![Updating the bot dialog](<../.gitbook/assets/image (618).png>)

{% hint style="warning" %}
If you try to update your NLP and you get an error message about 5 example entities, it means you need to add more entity values to some of your newly created entities. To do so, go to NLP > Entities > Contextual entities and make sure that that entity has at least 5 values.
{% endhint %}

![Testing the expression in the emulator](<../.gitbook/assets/image (637).png>)

Uh oh, this isn't really what we expected. As you can see, not all variables were recognized correctly. So, what's the issue? Lets have a look at the NLP results in the debugger:

![](<../.gitbook/assets/image (639).png>)

`origin`, `destination`, `time_departure` and `class` were found correctly, but only `time_departure` and `class` have a confidence score higher than 80%. `Origin` and `destination` score much lower, so they weren't processed as variables.

{% hint style="info" %}
In the [NLP treshold settings](https://docs.chatlayer.ai/understanding-users/natural-language-processing-nlp/settings) of our bot, we put a threshold of 80%, so anything underneath that won't be recognized correctly. &#x20;
{% endhint %}

How can you fix this issue? By adding more expressions! Try adding more expressions and retrain your NLP model to see if the variables now show up correctly in the bot. You can also choose to lower the NLP score, but be careful as this can impact the overal accuracy of your bot in the long run.

## Lesson recap

Your bot now has the following configuration:

* 3 intents with around 35 expressions in total&#x20;
* 5 contextual entities
* A bot message, linked to the `Book train ticket` intent, confirming the user input in the message

You now know how to:

* Create contextual entities and entity values
* Use variables in a bot message&#x20;
* Use multiple contextual entities in an expression
* Test your input in the debugger

Not every user will give all the entities you need. In the [next tutorial](tutorial-request-and-use-information-using-input-plugins.md), you will learn how to check if a user has already provided certain information, and ask for what's missing.
