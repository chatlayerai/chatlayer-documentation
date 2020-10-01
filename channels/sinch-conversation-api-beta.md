# Sinch Conversation API

The [Sinch Conversation API](https://www.sinch.com/products/apis/messaging/conversation-api/) allows you to connect Chatlayer.ai to multiple channels at the same time, without the need for any additional configuration. The Sinch Conversation API currently supports:

* SMS
* RCS
* Viber
* Facebook Messenger
* WhatsApp

You don't have to think about which type of message works with which channel - the Conversation API transcodes the messages automatically to match the target channel.

## Setting up the Conversation API integration

![](../.gitbook/assets/image%20%28316%29.png)

In the Channels page of Chatlayer.ai, add a new channel that is activated through the Sinch Conversation API. 

![](../.gitbook/assets/image%20%28306%29.png)

Chatlayer.ai will ask for a number of fields that are required to set up the connection. Let's go through them one by one.

#### Project ID

You can find the project id in the [conversation API overview](https://dashboard.sinch.com/convapi/overview).

![](../.gitbook/assets/image%20%28303%29.png)

#### App id

After creating an App, you can view the App id in the App table.

![](../.gitbook/assets/image%20%28304%29.png)

#### Client id & client secret

To get a client id and client secret, you need to create an access token. Navigate to [this page](https://dashboard.sinch.com/convapi/access-keys) to start the process.

Click on "New Key" and enter an access key display name

![](../.gitbook/assets/image%20%28305%29.png)

After confirming, you will be able to copy the client id and client secret to Chatlayer.ai

![](../.gitbook/assets/image%20%28308%29.png)

Once you have entered all the information in the Chatlayer.ai channel window, click Create and all the channels that are configured in the Sinch Conversation API app will be automatically added to Chatlayer.ai as well.

