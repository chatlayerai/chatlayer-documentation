# Message components

To design your conversational flow, you can use multiple components like text messages, buttons and carousels. Depending on the channel you publish the bot to \(Facebook Messenger, web, Slack, Telegram, ...\), these will be rendered slightly differently.

{% hint style="info" %}
**Character limits**

When you're building your flows, Chatlayer.ai gives you advice on how many characters to use in buttons, text messages, etc.

![](../../.gitbook/assets/image%20%2817%29.png)

For the Facebook Messenger channel, these are hard limits, which means that if you're adding a button label that's longer than 20 characters it will be cut off with "...".

For all other channels, the character limit is just an advice, we recommend staying below the limit, but it's not mandatory.
{% endhint %}

## Text Messages <a id="text"></a>

Text messages are the simplest components. Most channels will show them as 'text bubbles'.

## Buttons

Buttons are a useful way to guide the conversation by giving the user a limited set of options. You can add a maximum of three buttons to a message.

### Button types

#### Next bot dialog

For each button, you need to define a next dialog state. Optionally, you can add key-value combinations to a button. These will set variables depending on which button the user has clicked. These variables can then later be used to route dialog states, do an API call or render specific text.

#### URL

You can link a button to an external URL.

#### Call

This button will initiate a call if the user is working on a mobile device.

## Media

Using the Media template you can make the bot send files to your users.

#### Images

All typical image file types, such as jpg, png and gif are supported.

#### Video

Videos are available in the emulator, web widget and Facebook channel. The following video formats are supported:

* mp4
* ogv
* webm

A nice addition to the Facebook Messenger channel is that people can share the video with friends by clicking the button on the right side of the video:

![](../../.gitbook/assets/video-messenger.png)

#### Audio

The audio widget is available in the emulator, the web widget and Facebook Messenger. The only supported audio format is MP3.

### ![](../../.gitbook/assets/messenger-audio.png)

#### Files

File attachments are available in the emulator, web widget and Facebook Messenger. Currently, only pdf files are allowed.

![](../../.gitbook/assets/attachment.png)

## Quick replies

Quick replies behave similarly to buttons. They are rendered horizontally next to each other in a scrollable container. This means you add as many quick replies as you see necessary.

#### Payloads

For each quick reply, you need to define a next dialog state. Optionally, you can add key-value combinations. These will set variables depending on which button the user has clicked. These variables can then later be used to route dialog states, do an API call or render specific text.

#### URL

Quick replies only support next dialog states, no links to external websites. You can use a button for that.

#### Icon

Optionally, you can add an icon to a quick reply by specifying its URL.

![](../../.gitbook/assets/quickrelies.png)

#### Location

This button will save your location to a defined variable. Define the language for all location related data.

## Carousel

Carousels are a way to visualize options with images. Each option can have up to three buttons with separate actions, but that is not required. These buttons are the same buttons as in a button template with the same properties like payloads an URL, with the addition of an extra share button.

{% hint style="info" %}
Facebook has renamed Carousel to Generic Template. You can read about their guidelines for Generic Templates [here](https://developers.facebook.com/docs/messenger-platform/send-messages/template/generic).
{% endhint %}

#### Share button

The share button opens a share dialog in Facebook Messenger enabling people to share message bubbles with friends. A message bubble is a carousel card.

When a new user receives the bubble he can share it again with other friends by tapping the same share button. When tapping a postback button the user is send to the start page of the bot.

You can only use share button in generic templates \(carousels\) items and only items with maximum one url will be shared by Facebook. It is not possible to change the button title: Facebook Messenger will translate the button to the user his preferred language profile setting.

![](../../.gitbook/assets/carousel.png)

## List

The List Template is a template that allows you to present a set of items vertically.

Each item may render a button which can be used as a call-to-action \(postback\). You can also provide a URL to be opened when an item is tapped.

Each list template message can also have up to 1 global button which will be rendered below the item list.

### List rendering styles

Lists can be rendered in two different ways: Large and Compact.

#### Large

The first way renders the first item with a cover image with text overlaid. This is good to making the first item appear prominently above the other items.

![](../../.gitbook/assets/list-template.png)

#### Compact

The second way renders each item identically and is useful for presenting a list of items where no item is shown prominently.

![](../../.gitbook/assets/list-template-compact.png)

## File upload

Use the file upload template to let users upload a file directly from their device to the bot.

![](../../.gitbook/assets/image%20%287%29.png)

Configuring the File Upload as shown above will result in an Upload button in the conversation:

![](../../.gitbook/assets/image%20%2890%29.png)

If the upload failed because there was a problem with the connection, or the file the user chose was above 10 MB, the bot will go to the "failed upload" bot dialog.

The URL where the uploaded file is stored can be found under the `{uploadedFileUrl}` variable in the session of the user. You can reuse this variable to show the file the user uploaded, by using the [Media](message-components.md#attachments) template. Alternatively, you can retrieve the URL with an [API plugin](../../integrations/custom-back-end-integrations/) to store the files on your servers.

![](../../.gitbook/assets/image%20%28106%29.png)

