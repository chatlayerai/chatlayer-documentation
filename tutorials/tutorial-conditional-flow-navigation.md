---
description: >-
  In this final tutorial we will look at how to use user information and base
  different conversational flows on that.
---

# Flow navigation with variables

## Step 19: Go to bot dialog

The `Go To` bot dialog enables the bot to redirect the user to a bot dialog, depending on conditions of the session variables. You can define conditions with operators like `equals`, `greater than`, `smaller than`, etc. You can also combine multiple conditions with `AND` and `OR`.

Consider the following scenario where the user asks the bot the following:

> I want to book a train from Paris to London in first class please.

We already have a lot of information in this expression. Let's say we now want to show a different message for first class tickets, seeing there are more facilities in first than in second class.

* Create a `Go To` bot dialog with the name `class redirect`
* Add a condition with the '+' sign next to 'If'
* Choose a Go To condition saying 'if class equals first' &gt; go to `selected first class` bot message

![](../.gitbook/assets/image%20%28444%29.png)

* Open another condition with the '+' sign, next to 'Else if' and do the same for second class.

![](../.gitbook/assets/image%20%28422%29.png)

* If the user has selected no class at all, we want to redirect the user to the bot dialog `class,` which we already created. Here, the traveler will be asked explicitly in which class they want to travel. 
* Make sure the parent of this Go To is the `departure date`Input Validation.
* Configure the Go To like this:

![](../.gitbook/assets/image%20%28434%29.png)

## Step 20: First class options

* Open `selected first class` bot dialog. We are going to create buttons and save that information in a variable. Click on 'buttons' and create similar buttons as in the `class` Input Validation, to ask the user if they want a window seat. Make sure to save this to a variable. Add a Go To that redirects the user to `confirm booking.` 

![](../.gitbook/assets/image%20%28426%29.png)

## Step 21: Final touches

* Open `selected second class` bot dialog. Add a text message saying 'Second class confirmed' and go to `confirm booking`
* In the `departure date` Input Validation, change the Go To to `class redirect`
* Open the `class`  Input Validation. Change buttons so that both choices are redirected to the Go To `class redirect`. Change the parent to `class redirect` 

![](../.gitbook/assets/image%20%28425%29.png)

What we have now done, is that in `class redirect` we check if the class has already been given in the expression by the user. If that is the case, we confirm second class or give extra options for first class. If class has not been given yet, the user can choose this in the `class` Input Validation. If the user chooses their class in the Input Validation, then they are redirected to the class options.

Let's test this new functionality in the emulator:

![](../.gitbook/assets/image%20%28458%29.png)



That looks great! If something is not working correctly, double check the Go Tos in the bot dialogs. Sometimes the parent is changed, but the Go Tos not and that can cause issues. 

## Lesson recap

That was it! You have completed Choo Choo, great job! 

You should now be comfortable with the basics of bot building on the Chatlayer platform:

* Creating Bot Messages
* Asking for user input in Input Validations
* Creating intents and expressions 
* Using contextual entities 
* Using a Go To to steer the conversation 

Make sure to check out the rest of the documentation as well. 

Good luck with building your own bot! If you have any questions, please do not hesitate to contact us at [support@chatlayer.ai](mailto:support@chatlayer.ai). 



