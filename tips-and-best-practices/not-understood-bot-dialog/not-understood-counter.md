# Not understood counter

You can create a counter for the 'not understood' bot dialog. For example, you can initiate a human offloading whenever the bot has returned 'not understood' three times in a row. This article will explain on how to configure such a counter.

## 1. Change bot dialog type

Go to your 'not understood' bot dialog and change the type to 'Go To' 

![](../../.gitbook/assets/image%20%28469%29.png)

## 2. Create the conditions in the Go To

Now we are going to create the conditions in the Go To.

The first condition is to check if the previous dialog bot dialog is not the 'not understood message' bot dialog, leave this empty for now and we will fill it in later. We can refer to the previous bot dialog with the variable `internal.previousDialogstate.id` 

Create a new bot message in the Go To section, named 'not understood message'

![](../../.gitbook/assets/image%20%28475%29.png)

Make sure you add the following variable here, this ensures that the counter starts when the bot does not understand the first time.

![](../../.gitbook/assets/image%20%28473%29.png)

The second condition is to check if there is already 2 times in a row a 'Not understood'. This will give another bot dialog than before

![](../../.gitbook/assets/image%20%28471%29.png)

The final condition is to add an [increment ](https://docs.chatlayer.ai/bot-answers/settings/secure-variables-gdpr#incrementing-variable-counter)for the variable. This means that automatically the bot will add one to the variable of `not_understood_counter`

Add the following in the value field: `{not_understood_counter|increment}`

![](../../.gitbook/assets/image%20%28474%29.png)

## 4. Fill in bot messages

This is now the result when the Go To is saved:

![](../../.gitbook/assets/image%20%28476%29.png)

The 'Not understood message' is the message users will now see when there is one or two times in a row a 'Not understood'. Add a message such as 'I did not understand that, can you please repeat?'

The 'Not understood 3 times in a row' bot message will be shown when there is 3 times in a row a not understood. Add, for example, buttons asking is the user would like an offloading to a human agent.

## 5. Fill in the bot id 

Let's go back to the 'Not understood message' bot message. Open this and copy the bot id in the URL bar:

![](../../.gitbook/assets/image%20%28468%29.png)

Fill this in in your Go To:

![](../../.gitbook/assets/image%20%28470%29.png)



And that's it! Now you have a very use friendly way of offering offloading when the bot does not understand the user three times!

