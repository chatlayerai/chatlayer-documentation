---
description: >-
  A good 'not understood' handling is key to a good bot experience. Learn how to
  set up a 'not understood' counter in this article.
---

# Not understood counter

Instead of displaying the same `not understood` message over and over to the user, you can create a counter to show different kinds of messages. For example, when the bot doesn't understand the user for the first time, it displays the following:

"Sorry, I didn't get that. Can you please rephrase?" 

When it still doesn't understand the second time, it shows this message:

"Sorry, I still didn't get it. Can you try one more time?"

Finally, if the bot can't understand again, it can provide the user with an alternative way to get help:

"Sorry, I can't understand. Perhaps you'd like to talk to my colleague instead?"

Or 

"Sorry, I can't understand. Perhaps you'd like to email us instead?"

You can create this message structure by introducing a counter. Learn how in this article.

## 1. Change the dialog type

Click on the 'not understood' bot dialog and change the type to 'Go To' 

![From bot message to Go To](../../.gitbook/assets/image%20%28469%29.png)

## 2. Set the conditions in the Go To-dialog

Now we are going to set the conditions for the Go To-dialog.

As the first condition, you want to check if the previous dialog bot dialog is not the 'not understood message' bot dialog. You can leave this empty for now and fill it in later. We can refer to the previous bot dialog using the variable `internal.previousDialogstate.id` 

Create a new `bot message` in the `Go To` section, and name it 'not understood message'

![](../../.gitbook/assets/image%20%28475%29.png)

Make sure you add the variable `not_understood_counter` here to make sure that the counter starts when the bot does not understand for the first time:

![](../../.gitbook/assets/image%20%28473%29.png)

For the second condition, you want to check if the `not understood` was already shown 2 times in a row. If so, you want to show a different bot dialog, named 'Not understood 3 times in a row' like below:

![](../../.gitbook/assets/image%20%28471%29.png)

The final condition \(Else\) is where you need to add an [increment ](https://docs.chatlayer.ai/bot-answers/settings/secure-variables-gdpr#incrementing-variable-counter)for the `not_understood_counter` variable. This way, the bot will automatically increase the counter with one.

Add the following text in the value field: `{not_understood_counter|increment}`

![](../../.gitbook/assets/image%20%28474%29.png)

## 4. Write the bot messages

This is what you'll see after you have saved the `Go To` dialog:

![](../../.gitbook/assets/image%20%28476%29.png)

Keep in mind: the dialog named `Not understood message` is the first message users will see when the bot doesn't understand. The dialog named `Not understood 3 times in a row` will be shown when the bot didn't understand for the 3rd time. 

Fill in text for both dialogs. Here's some inspiration:

`Not understood message`"Sorry, I didn't get that. Can you please rephrase?" 

`Not understood 3 times in a row` "Sorry, I can't understand. Perhaps you'd like to talk to my colleague instead?"





## 5. Fill in the bot id 

Let's go back to the `Not understood message` bot dialog. Open this dialog and then copy the bot ID in your browser's URL field:

![](../../.gitbook/assets/image%20%28468%29.png)

Now fill this in in your `Go To` dialog:

![](../../.gitbook/assets/image%20%28470%29.png)

And that's it! You now created a user-friendly way of offering human offloading when the bot didn't understand the user three times in a row.

