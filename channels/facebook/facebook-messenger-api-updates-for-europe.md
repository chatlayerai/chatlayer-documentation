# Facebook Messenger API updates for Europe

On December 2nd, Facebook announced they'll be [updating their Messenger API](https://developers.facebook.com/docs/messenger-platform/europe-updates/) which will impact many of the 300.000+ chatbots that are currently live on this platform.

Beginning December 16th, several parts of the Messenger API, including those showing **Buttons**, **Carousels** and **Persistent Menus**, will be unavailable for developers and businesses in Europe, and for people in Europe who connect with businesses globally.

We created this guide to help you understand what is changing exactly and what you can do on the Chatlayer.ai platform to minimise the impact on your bot.

## Will this impact my bot?

We will guide you through a couple of questions to help you determine if your bot will be impacted by the new changes from Facebook.

### 1 – Is your bot published on Facebook Messenger?

Only bots that are published on Facebook Messenger will be impacted. If your bot is not on this channel, there will be no impact for you.

If you do have a bot published on Facebook Messenger, it might be impacted. Keep reading to find out more.

### 2 – Is your bot connected to a Facebook page that belongs to a European \(EEA\) company? Are your users European?

Facebook's API updates only impact businesses and bot users located **in Europe**. 

Bots that are live on non-European Facebook pages and talk to non-European customers will not be affected by these updates.

If you want to know if your page will be impacted, go to [developers.facebook.com](https://developers.facebook.com/), open your app, go to Messenger settings and find the following box:

![As you can see, our test page will be affected by the changes](../../.gitbook/assets/image%20%28352%29.png)

Enter your page ID to check if your page is affected by the new updates.

### 3 – Are the users of your bot accessing it through [messenger.com](https://messenger.com)?

Only users that access Facebook Messenger through the website [messenger.com](https://messenger.com), or through the [chat plugin](https://developers.facebook.com/docs/messenger-platform/discovery/facebook-chat-plugin/), will be impacted. Conversations happening on the Facebook Messenger app on Android and iOS devices **will not be impacted**.

### 4 – Does your bot use Carousels/Buttons/Video Media?

Only the messages that contain a **carousel** \(also called generic template\), a **button** template, or **media** other than images \(video, files, audio\) will be impacted. 

All other messages \(normal text messages, webviews\) will remain the same.

## What is changing exactly?

Starting December 16th, if the page, user location and device of the user fits the criteria above, users will no longer be able to see messages that contain one or more of the items below:

* Button
* Carousel \(also called generic template\)
* Media other than images \(video, files, audio\)

Additionally:

* All typing indicators and read reports will not be shown to the user
* m.me links with a referral will not work anymore
* The [persistent menu](./#persistent-menu) or hamburger menu will not be shown to the user
* The locale parameter, which is used to determine the user's language, as well as the first and last name of the user, cannot be retrieved any longer, even if those permission has been granted for your app.

## What is not changing?

The following Facebook Messenger features will not be impacted by the updates:

* Text messages
* Get Started button
* Webviews
* Quick replies

## **How to update your chatbot to avoid any errors from December 16th onwards?**

There are a few steps you can take to prepare your bot for the changes that are coming.

{% hint style="warning" %}
Facebook's policy doesn't seem to be set in stone, they are still adapting their policies and guidelines. Keep this in mind before starting a major rework of your bot.
{% endhint %}

* Remove all Buttons and Carousels from your bot
  * You can filter on bot dialogs containing buttons or quick replies using the [translations](../../bot-answers/dialog-state/translations.md) table
  * You can use a combination of [context](../../understanding-users/using-context.md) and intents to replace any buttons
  * You can use quick replies to replace some of the functionalities of buttons
* Facebook recommends URL buttons to be converted into a message containing a URL. Users can click that URL to get to the same place.

![](../../.gitbook/assets/image%20%28353%29.png)

* Remove all media except for images
  * Video's, audio and files can be replaced with a direct link to the file itself
* Remove the [persistent menu](./#persistent-menu) of your bot

If you want detailed advice on how to keep a good conversation design with a buttonless bot, we have written a guide ["How to create a buttonless bot"](https://tesstettelin.medium.com/dd68772f8560) to help you out.

## **Why are we only hearing about this now?**

As soon as Facebook released their official statement, we created this guide. We aren't sure why Facebook is releasing this information so close to the deadline, but we are doing our best to prepare and help you.

## **Are these changes permanent?**

Facebook said this in their [official release](https://developers.facebook.com/docs/messenger-platform/europe-updates/): 

`We are currently working to restore these features and will continue to update this document (...) with the details as they are available.`

That means that right now, we don't really know what exactly will change in their policies before December 16th...

## **Why is Facebook making these changes?**

Most likely, these changes are caused by ongoing litigation between Facebook and the members of the European Economic Area. Facebook is updating their Messenger API as part of their efforts to comply with new privacy rules in Europe.

## I need more help!

This guide contains all information we have so far, and is being updated every time we receive more information. But if you still have questions specific to your bot, feel free to [get in touch](../../support/get-in-touch.md) with us.

