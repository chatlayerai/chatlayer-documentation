# Sinch Conversation API

The [Sinch Conversation API](https://www.sinch.com/products/apis/messaging/conversation-api/) allows you to connect Chatlayer.ai to multiple channels at the same time, without any additional configuration. The Sinch Conversation API currently supports:

* SMS
* MMS
* RCS
* Viber
* Facebook Messenger
* WhatsApp
* Telegram
* Instagram
* LINE

You don't have to think about which type of message works with which channel – the Conversation API transcodes the messages automatically to match the target channel. Easy peasy!&#x20;

## Creating your channels

First, you need to create channels in the [Sinch dashboard](https://dashboard.sinch.com). Depending on the channel you want to set-up, the instructions will be different.

## Linking the channels to the Conversation API app

You can find detailed instructions on how to create a Conversation API app [here](https://developers.sinch.com/docs/conversation-getting-started).

{% hint style="warning" %}
Make sure that the region of your app is EU.

![](<../.gitbook/assets/image (351).png>)
{% endhint %}

## Setting up the Conversation API integration in Chatlayer

![](<../.gitbook/assets/image (316).png>)

In the Channels page on our platform, add a new channel that is activated through the Sinch Conversation API.&#x20;

![](<../.gitbook/assets/image (306).png>)

We'll then ask for a number of fields that are required to set up this connection. Let's go through each of them, one by one.

#### Project ID

You can find the project ID in the [conversation API overview](https://dashboard.sinch.com/convapi/overview).

![](<../.gitbook/assets/image (303).png>)

#### App ID

After creating an App, you can view the App ID in the App table.

![](<../.gitbook/assets/image (304).png>)

#### Client ID & client secret

To get a client ID and client secret, you need to create an access token. Navigate to [this page](https://dashboard.sinch.com/settings/access-keys) to start the process.

Click on 'New Key' and enter an access key display name:

![](<../.gitbook/assets/image (305).png>)

After confirming, you will be able to copy the client id and client secret to our platform:

![](<../.gitbook/assets/image (308).png>)

Once you've entered all the information in the Chatlayer.ai channel window, click 'Create' and all the channels that are configured in the Sinch Conversation API app will be automatically added to Chatlayer.ai as well.

## Variables

If multiple channels are connected to your Conversation API app, it can be useful to be able to send a specific flow depending on the channel the bot user is on. To do that, you can use the `internal.sinchConversationAPI.channelIdentifier` [variable](../bot-answers/settings/secure-variables-gdpr.md).&#x20;

The possible values for the channel are:

```
internal.sinchConversationAPI.channelIdentifier: 
"CHANNEL_UNSPECIFIED"
"WHATSAPP"
"RCS"
"SMS"
"MESSENGER"
"VIBER"
"VIBERBM"
"MMS"
"TELEGRAM"
"LINE"
"INSTAGRAM"
```

Furthermore, there are a few other variables that store data coming from the Sinch Conversation API that might be useful to guide your flow:

```
internal.sinchConversationAPI.channelIdentity: 'USER_PHONE_NUMBER_OR_ID',
internal.sinchConversationAPI.contactId: 'CONTACT_ID_CONV_API',
internal.sinchConversationAPI.appId: 'APP_ID_CONV_API',
internal.sinchConversationAPI.conversationId: 'CONVERSATION_ID_CONV_API',
```

You can learn more about how to use variables to guide your flow here:

{% content-ref url="../tutorials/tutorial-conditional-flow-navigation.md" %}
[tutorial-conditional-flow-navigation.md](../tutorials/tutorial-conditional-flow-navigation.md)
{% endcontent-ref %}

