# WhatsApp Business API

WhatsApp is a messaging service owned by Facebook with over 1.5 billion monthly active users. Chatlayer.ai supports an integration with WhatsApp Business API through our official WhatsApp integration partner [CM.com](https://www.cm.com).

In order to activate your Chatlayer.ai bot on WhatsApp, you should follow these steps:

1. [x] Send an e-mail to [sales@chatlayer.ai](mailto:sales@chatlayer.ai), requesting an integration with WhatsApp for a specific bot.
2. [x] The Chatlayer.ai sales department will inform you about all WhatsApp-specific terms and conditions, and will bring you in contact with CM.com.
3. [x] After you have successfully signed up for CM.com, you should copy the URL of your WhatsApp webhook and share it with CM.com. You can find this URL under Settings &gt; Channels &gt; "+ WhatsApp"

![](../.gitbook/assets/image%20%28121%29.png)

1. [x] From CM.com you will receive a product token. Fill in this token as well as your WhatsApp Business API phone number in Chatlayer.ai

![](../.gitbook/assets/image%20%2825%29.png)

## Spreading awareness of your WhatsApp bot

One of the key challenges in creating a WhatsApp bot is making sure your customers know it exists and how to find it. Think carefully about where you want to position your WhatsApp conversational experience. We have some suggestions:

* Make noise on your social media channels that you're now also reachable on WhatsApp
* In the contact options on your page, make sure that WhatsApp is listed as an option next to your other channels.
* Use wa.me links: you can direct customers to your WhatsApp channel using this link: [http://wa.me/32472041640](http://wa.me/32472041640). Replace the number by your own WhatsApp Business API phone number. 
  * Users that navigate to this webpage will see the following message:

![](../.gitbook/assets/image%20%28170%29.png)

* After clicking "Message" the WhatsApp App will open on their smartphone - or the WhatsApp web interface will open on desktop, and customers can start messaging your business.
  * You can also include text messages in your wa.me links, by using the following template:  [https://wa.me/32472041640?text=Hello%20there](https://wa.me/32472041640?text=Hello%20there). This text will be filled in, ready to be sent by your customer with the click of a button. Make sure you use URL query encoding correctly.
  * This link can be easily included in website buttons, Facebook campaigns or inside a QR code.

## WhatsApp restrictions

Compared to the web widget or Facebook Messenger, WhatsApp is much more restrictive in what it can show as a bot. The following things are **not** supported in WhatsApp:

* Introduction message: users will always have to initiate the conversation themselves - you can use the wa.me link to send a default first message, as described [here](whatsapp.md#spreading-awareness-of-your-whatsapp-bot).
* Buttons, carousels, lists, quick replies: WhatsApp only support plain text messages, media, locations and contacts.
* Voice and video calling, speech messages
* Typing indicators and read receipts

