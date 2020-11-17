# Capturing information with entities

We can define a new intent that tells us the user wants to book a train ticket by training it with expressions like:

* I want a train ticket
* I need a ticket
* Can I book a train ticket here?

But what happens when a user says something like:

* I want a train ticket to Amsterdam
* I need to go to Antwerp tomorrow
* Can I book a train ticket to Brussels please?

Those expressions contain valuable information. We want to make sure we capture the destination and save it as a variable. In this tutorial, you will learn how to store data that was mentioned in intents, using entities. In the next tutorial, you will learn how you can ask explicitly for missing variables.

## Creating entities

Not all users will immediately mention their destination, so let's make sure we train our intent without those specific entities as well:

* Go to `NLP` &gt; `Intents`
* Add a new intent called `book train ticket`
* Add some simple expressions, like:
  * I want a train ticket
  * I need a ticket
  * Can I book a train ticket, please?

{% hint style="info" %}
If you have trouble doing this, please read the [previous tutorial](tutorial-adding-content.md).
{% endhint %}

Next, it's time to add an entity.

* Click on `+ Add expression`
* Select the `book train ticket` intent
* Enter an expression that contains an entity, for example:

> I want to book a ticket from Brussels to Paris

* Select `Brussels` in this sentence. 

![](../.gitbook/assets/image%20%2815%29.png)

* Click on the ![](../.gitbook/assets/entity-add-.png)  '+ entity' icon in the bottom right of the expression box to create a new entity for 'Brussels'  
* Brussels is the location the user wants to depart from, so we will name this entity `origin` 
* Type `origin` in the `Create new entity` field and click on 'Create new entity' to confirm

![](../.gitbook/assets/image%20%28250%29.png)

* Brussels will be added to the list of possible values for the @origin variable
* Do the same thing for `Paris` as a 'destination' entity

![](../.gitbook/assets/image%20%2886%29.png)

* Add some other values to the 'origin' and 'destination' entities in the expression field. These will be saved for all future expressions.
* Add more expressions that contain the entities **origin** and **destination**

{% hint style="info" %}
We recommends adding at least 30 expressions per entity, to guarantee the quality of the entity detection.
{% endhint %}

* Some ideas for expressions:

  * Can I book a train from Cologne to Brussels?
  * I need to be in Rotterdam
  * I need a train to London
  * I want to travel to Lyon
  * I want to buy a ticket from Moscow to Vladivostok
  * I need a ticket from New York to Baltimore

* Tip: when typing a new expression, use the '@' to choose from an existing entity to add it to the sentence.
* Make sure you retrain the NLP model by clicking the `Update NLP` button.

We have built a way to create a lot of expressions really fast: the **expression generator**. Follow the instructions on [this page](../understanding-users/expression-generator.md) to get started.

## Testing entities

After we have retrained our model, let's see if its good enough to recognise the destination entity.

* Go to `NLP` &gt;`Test` to open the testing console 
* Write 'I would like to go to Brussels from Amsterdam' as the expression to be tested
* Click on `Test`

You'll see that the entity gets recognized with a 89.72% confidence. The results will be different based on your training set. If the entity is not recognized correctly, you can add it here as a training expression immediately. 

{% hint style="warning" %}
Make sure you retrain the model before testing newly added expressions.
{% endhint %}

![](../.gitbook/assets/image%20%2827%29.png)

## Using variables in messages

When a user says something containing an entity, and the entity is successfully detected, our tool will automatically store the entity as a **variable** for that specific user.

To reuse the variable later on in the conversation, you can put it in between curly brackets like this: `{variable_name}`. When writing this message to the users, we will automatically substitute `{variable_name}` ****with the value of the variable. If the variable is empty, an empty string will be shown.

* In Bot dialogs, create a bot dialog of the type 'Bot message' `book train ticket` and link the `book train ticket` intent to it in the NLP tab.
* Add a new text message with the text "So you want to go to `{destination}`, I can help you with that!"

Variables can be used everywhere throughout the platform, for example in API calls, list templates and button labels.

{% hint style="info" %}
Not only entities can be variables. Later on you will learn how to use variables to build flows.
{% endhint %}

![](../.gitbook/assets/image%20%2856%29.png)

## Testing entities in the emulator

Now that we have linked everything, we are ready to test if everything is configured correctly by using the emulator.

* Open the emulator \(aka `Test your bot`\)
* Enter "I want to go to Amsterdam" and click on submit
* Open the debugger

![](../.gitbook/assets/image%20%28193%29.png)

In the tab 'NLP Result'  you can now see if the entity was extracted correctly.

All entities are automatically stored in the variables list. In the 'Debugger' tab, you can find a list of all known variables under 'User Session'. Since the entity was recognized in the previous message, this contains the variable 'destination'.

![](../.gitbook/assets/image%20%28253%29.png)

{% hint style="info" %}
If your entity is recognised by the NLP but doesn't show up in the User Session, it did not pass the threshold. By default the threshold is set to 80%. You can lower it in the NLP tab, but better still is to add more expressions to your bot so that the model becomes more robust and will work better in the future.
{% endhint %}

## Multiple entities

You can add as many entities as you want to one expression. Sometimes it makes sense to prepare for a lot of entities and add an expression like

* I want to go from **Antwerp** to **Brussels** **tomorrow** at **9am** in **first** class

with the following entities:

* origin: Antwerp
* destination: Brussels
* departure-date: tomorrow
* departure-time: 9am
* class: first

Keep in mind that NLP techniques are probabilistic in nature. When you try to capture five expressions in one sentence, it might not be able to recognise all of them correctly. As a general rule of thumb, you can start to expect reasonable results for one entity when the NLP was given at least 30 expression to learn from. 

![](../.gitbook/assets/expression-withentities.png)

#### Additional suggestions for expressions

* I need to be in Paris next Thursday
* I need to be in New York on Friday
* I want to go to Brussels on Monday
* Friday I want to go from Antwerp to Amsterdam
* I want to travel in second class from Ghent to Brussel on Friday
* I want to travel in first class from Antwerp to Aalst on Thursday
* I like to book a first class ticket from Aalst to Brussels at nine o'clock
* Tomorrow I want to go from Antwerp to Brussels on the train from 9:00 in first class

## Missing entities

### Testing your entities

Update the `book train ticket` message to display the entities:

`So I have a request for a train ticket; {origin} to {destination} on {departure-date}, {departure-time}, {class} class.`

Now retrain your NLP model and test your bot

![](../.gitbook/assets/incomplete-conversation%20%281%29.png)

Uh oh, this isn't really what we expected. As you can see, the departure date and time is not set \(your result may be different depending on the expressions you used\).  
  
So, what's the problem? Lets have a look at the NLP Results:

![](../.gitbook/assets/nlp-result%20%281%29.png)

`origin`, `destination` and `departure-date` were found correctly, but only `origin` and `destination` have a confidence score above 80%. So `departure-date` was not processed and put into a variable.  
  
More expressions can help you fix this problem!

Not every user will input all the entities you need. In the [next tutorial](tutorial-request-and-use-information-using-input-plugins.md), you will learn how to check if a user has already provided certain information, and ask for what's missing.

