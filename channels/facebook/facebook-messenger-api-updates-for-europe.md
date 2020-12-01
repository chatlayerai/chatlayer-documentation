# Facebook Messenger API Updates for Europe

Facebook unexpectedly [published a breaking change to the Messenger API](https://developers.facebook.com/docs/messenger-platform/europe-updates/) which will impact a large part of the over 300.000 chatbots that are currently live on their platform, especially for European users.

This article helps you understand what is changing and what you can do in Chatlayer.ai to ease the impact.

## Will this impact my bot?

We will guide you through a couple of questions to help you determine if your bot will be impacted by these changes from Facebook.

### Is your bot published on Facebook Messenger?

Only bots published on the Facebook Messenger channel are impacted. If your bot is not on this channel, there's no impact for you.

If you do have a bot published on Facebook Messenger, you might be impacted.

### Is the Facebook page connected to your bot the page of a European \(EEA\) company? Do you have European users?

This change only impacts businesses and users of bots in Europe.

For non-European Facebook bots talking to non-European customers, nothing changes.

### Are you using Carousels / Buttons / Quick Replies / Video Media in your bot?

Only the messages that contain a **carousel** \(also called generic template\), a **button** template, **quick replies** or a **video** will be impacted. All other messages \(normal text messages, webviews\) will remain the same.

### Are the users of your bot accessing it through [messenger.com](https://messenger.com)?

Only users that use Facebook Messenger through the website [messenger.com](https://messenger.com), or through the [chat plugin](https://developers.facebook.com/docs/messenger-platform/discovery/facebook-chat-plugin/), will be impacted. All conversations happening through the Facebook Messenger app on Android and iOS devices will not be impacted.

Facebook doesn't publish data on the percentage of users accessing Messenger through apps or through the website or chat plugin.

## What is changing?

Starting December 16th, if the page, user and device of the user fits the criteria outlined above, whenever a user triggers a message from the bot that contains a:

* Button
* Carousel \(also called generic template\)
* Quick reply
* Media containing a video

An error will be shown to the user of the bot, and the message will not be shown. We don't know what this error will look like yet.

## What is not changing?

The following features will not be impacted by the changes:

* m.me links
* Get Started button
* Webviews

## **What we don’t know**

**What will happen on December 16th?**

**What can you do to make your bot compliant with the new regulations?**

**Why are we only hearing about this now?**

As soon as Facebook released their official statement, we started preparing this 

**Are these changes temporary?**

Facebook writes on their official page “We are currently working to restore these features and will continue to update this document with the details as they are available.”

**Why is Facebook pushing these changes?**

