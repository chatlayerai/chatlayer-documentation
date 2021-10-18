# WhatsApp Business API

WhatsApp is a messaging service owned by Facebook with over 1.5 billion monthly active users. Our platform supports an integration with WhatsApp Business API through the [Sinch Conversation API](sinch-conversation-api-beta.md).

## Inform users of your WhatsApp bot

One of the key challenges in creating a WhatsApp bot is making sure your customers know it exists and where they can find it. So think carefully about where you want to position your WhatsApp conversational experience. 

We have some suggestions to help you get started:

* Communicate via your social media channels that users can now reach you on WhatsApp.
* List WhatsApp as an option in your list of contact options on your contact webpage.
* Use wa.me links to guide customers to your WhatsApp channel using this link: [http://wa.me/32472041640](http://wa.me/32472041640). Make sure to replace that last string of numbers with your own WhatsApp Business API phone number. Users that navigate to this webpage will see the following message:

![](<../.gitbook/assets/image (170).png>)

* After clicking "Message," the WhatsApp App will open on the user's smartphone, or the WhatsApp web interface will open on desktop, and users can start messaging your business straight away.
  * You can also include text messages in your wa.me links, by using the following template: [https://wa.me/32472041640?text=Hello%20there](https://wa.me/32472041640?text=Hello%20there). This text will be filled in, ready to be sent by your user with the click of a button. Make sure you use URL query encoding correctly.
  * This link can be easily included in website buttons, Facebook campaigns or as a QR code.

## WhatsApp restrictions

Compared to the web widget or Facebook Messenger, WhatsApp is much more restrictive in what you can do with your bot. The following things are **not **supported by WhatsApp:

* Introduction message: users will always have to initiate the conversation themselves. You can use a wa.me link to send a default first message – learn more [here](whatsapp.md#spreading-awareness-of-your-whatsapp-bot)
* Buttons, carousels, lists, quick replies. WhatsApp only supports plain text messages, media, locations and contacts
* Voice and video calling are not supported
* Typing indicators and read receipts are not supported
