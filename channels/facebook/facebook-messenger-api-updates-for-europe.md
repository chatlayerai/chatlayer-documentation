# Facebook Messenger API Updates for Europe

Facebook unexpectedly [published a breaking change to the Messenger API](https://developers.facebook.com/docs/messenger-platform/europe-updates/) which will impact a large part of the over 300.000 chatbots that are currently live on their platform.

This guide helps you understand what is changing and what you can do in Chatlayer.ai to ease the impact.

## Will this impact my bot?

We will guide you through a couple of questions to help you determine if your bot will be impacted by these changes from Facebook.

### Is your bot published on Facebook Messenger?

Only bots published on the Facebook Messenger channel are impacted. If your bot is not on this channel, there's no impact for you.

If you do have a bot published on Facebook Messenger, you might be impacted.

### Is the Facebook page connected to your bot the page of a European \(EEA\) company? Do you have European users?

This change only impacts businesses and users of bots in Europe.

For non-European Facebook bots talking to non-European customers, nothing changes.

If you want to know if your page will be impacted, go to developers.facebook.com, open your app, go to Messenger settings and find the following box:

![As you can see, our test page will be affected by the changes](../../.gitbook/assets/image%20%28352%29.png)

Enter your page ID here to check if it's affected by the changes.

### Are you using Carousels / Buttons / Quick Replies / Video Media in your bot?

Only the messages that contain a **carousel** \(also called generic template\), a **button** template, **quick replies** or media other than images \(video, files, audio\) will be impacted. 

All other messages \(normal text messages, webviews\) will remain the same.

### Are the users of your bot accessing it through [messenger.com](https://messenger.com)?

Only users that use Facebook Messenger through the website [messenger.com](https://messenger.com), or through the [chat plugin](https://developers.facebook.com/docs/messenger-platform/discovery/facebook-chat-plugin/), will be impacted. All conversations happening through the Facebook Messenger app on Android and iOS devices will not be impacted.

Facebook doesn't publish data on the percentage of users accessing Messenger through apps or through the website or chat plugin.

## What is changing?

Starting December 16th, if the page, user and device of the user fits the criteria outlined above, whenever a user triggers a message from the bot that contains a:

* Button
* Carousel \(also called generic template\)
* Quick reply
* Media other than images \(video, files, audio\)

That message will not be shown to the user.

Additionally:

* All typing indicators and read reports will not be shown to the user.
* m.me links with a referral with not work anymore
* The [persistent menu](./#persistent-menu) or hamburger menu will not be shown to the user.

## What is not changing?

The following Facebook Messenger features will not be impacted by the changes:

* Get Started button
* Webviews

## **How to convert your chatbot to avoid errors after December 16th?**

There are a few steps you can take to prepare your bot for the changes that are coming.

{% hint style="warning" %}
Facebook's policy doesn't seem to be set in stone, they are still adapting their policies and guidelines. Keep this in mind before starting a major rework of your bot.
{% endhint %}

* Remove all Buttons, Quick Replies and Carousels from your bot
  * You can filter on all bot dialogs containing buttons or quick replies using the [translations](../../bot-answers/dialog-state/translations.md) table
  * You can use a combination of [context](../../understanding-users/using-context.md) and intents to replace the buttons
* Facebook recommends URL buttons to be converted into a message containing a URL. Users can click that URL to get to the same place.

![](../../.gitbook/assets/image%20%28353%29.png)

* Remove all media except images
  * Video's, audio and files can be replaced with a direct link to the file itself
* Remove the [persistent menu](./#persistent-menu) of your bot

## **Why are we only hearing about this now?**

As soon as Facebook released their official statement, we published this guide. We aren't sure why Facebook is releasing this information so close to the deadline.

## **Are these changes permanent?**

Facebook writes on [their official post](https://developers.facebook.com/docs/messenger-platform/europe-updates/): 

`We are currently working to restore these features and will continue to update this document (...) with the details as they are available.`

Right now, we do not know what exactly will change in their policies before the December 16th deadline.

## **Why is Facebook making these changes?**

Most likely, these changes are caused by ongoing litigation between Facebook and the members of the European Economic Area.

## I need help

We have written all we know about the changes in the guide above, but if you have any questions specific to your bot, feel free to [get in touch](../../support/get-in-touch.md) with us.

