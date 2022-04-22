---
description: >-
  A good 'not understood' handling is key to a good bot experience. Learn how to
  set up this counter in the article below.
---

# Not understood counter

Instead of always showing the same `not understood` message, you can create a counter to show different messages, depending on how often the not understood dialog is triggered. For example, when the bot doesn't understand the user for the first time, it will display the first not understood message:

"Sorry, I didn't get that. Can you please rephrase?"&#x20;

After the user has sent another message and the bot didn't understand a second time, it will display the second not understood message, offering an external way out:

"Sorry, I still don't understand. Perhaps you'd like to talk to my colleague instead?"

Or "Sorry, I still don't understand. Perhaps you'd like to email us instead?"

This counter set-up creates a better user experience and makes the bot appear much smarter. Ready to get started? Let's go! 👏

## 1. Change the dialog type

Step 1: Click on the 'not understood' Bot Message dialog and in the list under 'Type', select 'Go To'&#x20;

![](<../../.gitbook/assets/image (668).png>)

## 2. Set the first condition in the Go To dialog

For the next step, we are going to set the counter conditions so the bot knows how often this dialog was triggered already.

For the first condition, we want to check if the 'not understood message' dialog was triggered already once. To do so, copy and paste the variable _**not\_understood\_counter**_ in the left field. Click on 'create' to create the variable.&#x20;

Then in the middle field, select `equals` in the drop down menu.&#x20;

In the field on the right, we'll put **1** – This tells the bot that the first not understood dialog was displayed already and that it's time to display the second not understood dialog.

![](<../../.gitbook/assets/image (674) (1) (1).png>)

## 3. Set the final condition in the Go To dialog

For the second and final condition, we're creating the actual counter.

Under Else, type _**Not understood x 1**_** ** and click 'create' to create the variable.&#x20;

Next, click `+ Add Variable` to add a variable and value. In the middle field, add the variable _**not\_understood\_counter**_. In the field on the right, add the [increment value](https://docs.chatlayer.ai/bot-answers/settings/secure-variables-gdpr#incrementing-variable-counter)  _**{not\_understood\_counter|increment}**_

![](<../../.gitbook/assets/image (673) (1).png>)

Save your set-up by clicking the `Save` button on the bottom right.

The entire Go To dialog should look like this:

![](<../../.gitbook/assets/image (675) (1).png>)

## 4. Write the bot messages

After saving your `Go To` dialog and closing it, the flow should look like this:

<img src="../../.gitbook/assets/image (677) (1) (1) (1) (1).png" alt="" data-size="original">

Now it's time to write the copy for both dialogs. Here's some inspiration for the first message that will be displayed – the 'Not understood x 1' dialog:

* Sorry, I didn't get that. Can you please rephrase?
* Hmm, I can't understand. Can you use different words? Perhaps I'll get it then!
* I didn't understand, please try once more

For the second and final message, the 'Not understood x 2' dialog, you can write something like this:

* Sorry, I still can't understand. Perhaps you'd like to talk to my human colleague instead?
* Sorry, I can't seem to understand. Would you like to call us instead?&#x20;
* Sorry, I can't seem to understand. Perhaps it's better if you email us your question

That's it, all done! You just created a user-friendly way of telling the user the bot didn't understand 👏
