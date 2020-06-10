# Capture information with input validation

So far, our content was limited to a simple conversation. In a lot of use cases, the bot needs input from the user to fully fulfil their flow. That input can then be used later in the flow, or you can send it to the database with the API plugin.

### Adding an Input Validation

In our Choo Choo example, the user has shown an interest in booking a train ticket. Before we can do that, we need some information from the user like:

* Destination
* Origin
* First class or second class

## Text input

Let's start by asking for the departure location.

* Open the `book train ticket` bot dialog.
* In the Bot Message tab, click the green + icon at the bottom to add a Go to
* Type `destination` in the Go to field, and click `Create Input Validation 'destination'`

![](../.gitbook/assets/image%20%2862%29.png)

* Save the `book train ticket` bot dialog
* Open the newly created `destination` input validation
* On the `Input Validation` tab, under Question, add a new text message "Where do you want to go?".
* In the Validation pane, select `Any` as the format type

{% hint style="info" %}
Input validation can automatically parse certain types of data like dates, addresses, numbers, hours, currency, ... This will convert the users response into a more structured format. In this example, we just want to have a city, which can take on any format. Hence, we use input type 'Any' which will accept all values as valid input. You can find more info about plugin parser types [here](../bot-answers/dialog-state/user-input-bot-dialog.md#input-types).
{% endhint %}

* Type `destination` as the variable. The input from each user will be saved under this variable.
* Type `Confirm booking` in the Go to field. Because the `Confirm booking` bot dialog doesn't exist you get the option to create a new one. Pick `Create Bot Message 'Confirm booking'`

![](../.gitbook/assets/image%20%2872%29.png)

The end result should look like this.

![](../.gitbook/assets/add-input-validation.png)

Once created you will see the following flow.

![](../.gitbook/assets/flow-confirm-booking%20%281%29.png)

{% hint style="warning" %}
The parent - child relation between dialog state nodes has no functional conversation meaning. It is only a visual representation. Always link your bot dialogs using Go to's.
{% endhint %}

#### Using input in text messages

All the session variables are stored in the user session. To access a variable in any displayed text, you can put the variable name between curly brackets.

* Open the `Confirm booking` bot dialog
* Enter a new text message `Okay you want to go to {destination}. We can do that.`

#### NLP & input plugin

You want to make sure your users don't get stuck in a loop asking them for some input. Because of this, by default, Chatlayer.ai makes sure that if an intent is detected in the answer to the input plugin, users leave the input plugin and go to the relevant part of the conversation.

Our Choo Choo bot doesn't have a mature NLP model yet, which increases the likelihood of false intent matches. So for now, it's best to select the "Disable NLP" checkmark in the input plugin.

![](../.gitbook/assets/image%20%2837%29.png)

Time for a test!

![](../.gitbook/assets/bot-dialog-destination.png)

{% hint style="info" %}
If you forget to define the 'Go to' and you test your conversation flow, the flow will just stop. The conversation flow will only continue if you correctly set the 'Go to' on each dialog state.
{% endhint %}

### Add remaining input validations

Repeat the previous steps for the the other pieces of information we need to get from our users:

* Origin: Where are you leaving from?
* Departure time: At what time do you want to leave?
* Departure date: Which day do you want to take the train?

Make sure all of these input validations follow a consecutive flow, and end up in the `Confirm booking` bot dialog:

1. `Book train ticket`
2. `Destination`
3. `Origin`
4. `Departure time`
5. `Departure date`
6. `Confirm booking`

### Combining input plugins with buttons

In the previous example we requested user input by sending a text message. However, in an input validation, we can also ask for the user's input by click but it is also possible to use buttons, lists, carousels and other UI components to support user input as text or clicks.

Let's use a carousel component to request the user his preferred train class.

* In the `Departure date` input validation, type `Class` in the Go to field and create a new input validation.
* Onder Question, add Buttons
* Enter the text message: "Which class do you want to travel in?"
* Add two buttons, "First class" and "Second class" both going to the `Confirm booking` bot dialog.
* In both buttons add a variable `class` and value `first` and `second`

![](../.gitbook/assets/image%20%28156%29.png)

* Select format type `Any`, enter `class` as variable, and Go to `Confirm booking`

{% hint style="info" %}
It's important to use an identical variable name for the input variable, the NLP entity and the button variable.
{% endhint %}

Depending on the user input different actions are executed:

1. If a user types an expression that contains an entity which matches with the variable in an input validation, this input validation is skipped over. This way we can avoid asking things to the user that they have already said. 
   1. For example: when the user says `I need a first class train ticket` which belongs to intent `book train ticket` and includes an entity `class`, the 'class' variable is stored in the user session with a value 'first' and the input validation 'class' is skipped because the value for the input variable is already available in the user session.
2. When the user is asked to input his preferred train class and he inputs 'first', this value will be added in the input variable 'class' in the user session.
3. When the user clicks the button 'First class', the value 'first' will be added to the variable 'class' in the user session.

### Finishing it up

Now that we have all these extra inputs, it's time to show all of the data we've gathered in the input validations to the user of the bot.

* Open the `Confirm booking` bot dialog
* Replace the existing text message with "I have a train ticket for you from {origin} to {destination} on {departure date} at {departure time}h, in {class} class."

Test your newly created rail bot!



In the [next tutorial](tutorial-using-context-for-intent-reuse.md) we will learn how we can use context for reusing intents. A good example are **yes** and **no**, which can be used in association with more than one specific bot dialog.

