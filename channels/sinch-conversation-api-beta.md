# Sinch Conversation API

The [Sinch Conversation API](https://www.sinch.com/products/apis/messaging/conversation-api/) allows you to connect Chatlayer.ai to multiple channels at the same time, without any additional configuration. The Sinch Conversation API currently supports:

* SMS
* RCS
* Viber
* Facebook Messenger
* WhatsApp

You don't have to think about which type of message works with which channel – the Conversation API transcodes the messages automatically to match the target channel. Easy peasy! 

## Creating your channels

First, you need to create channels in the [Sinch dashboard](https://dashboard.sinch.com/). Depending on the channel you want to set-up, the instructions will be different.

## Linking the channels to the Conversation API app

You can find detailed instructions on how to create a Conversation API app [here](https://developers.sinch.com/docs/conversation-getting-started).

{% hint style="warning" %}
Make sure that the region of your app is EU.

![](../.gitbook/assets/image%20%28351%29.png)
{% endhint %}

## Setting up the Conversation API integration in Chatlayer

![](../.gitbook/assets/image%20%28316%29.png)

In the Channels page on our platform, add a new channel that is activated through the Sinch Conversation API. 

![](../.gitbook/assets/image%20%28306%29.png)

We'll then ask for a number of fields that are required to set up this connection. Let's go through each of them, one by one.

#### Project ID

You can find the project ID in the [conversation API overview](https://dashboard.sinch.com/convapi/overview).

![](../.gitbook/assets/image%20%28303%29.png)

#### App ID

After creating an App, you can view the App ID in the App table.

![](../.gitbook/assets/image%20%28304%29.png)

#### Client ID & client secret

To get a client ID and client secret, you need to create an access token. Navigate to [this page](https://dashboard.sinch.com/settings/access-keys) to start the process.

Click on 'New Key' and enter an access key display name:

![](../.gitbook/assets/image%20%28305%29.png)

After confirming, you will be able to copy the client id and client secret to our platform:

![](../.gitbook/assets/image%20%28308%29.png)

Once you've entered all the information in the Chatlayer.ai channel window, click 'Create' and all the channels that are configured in the Sinch Conversation API app will be automatically added to Chatlayer.ai as well.

