---
description: >-
  Follow these step-by-step instructions on how to set up the phone and voice
  channel.
---

# Phone & voice

## Activating the phone channel

* Go to the 'Channels' tab on the left and click on the '+' button next to 'Phone'.

![Click the '+' button to add a phone connection](<../.gitbook/assets/image (179).png>)

* Click on 'create' if you see this pop-up:

![](<../.gitbook/assets/image (390).png>)

## Setting up a phone configuration

* Click on the blue button 'Create configuration' to set up a test caller

![](<../.gitbook/assets/image (389).png>)

* You will see the following pop-up:

![You can keep the Chatlayer test number for now](<../.gitbook/assets/image (391).png>)

* Under 'Caller' you can fill out the phone number of the **person who will test the bot**
* Under 'Languages' you can select the languages of your bot
* Under 'Description' you can fill out the name of the **person who will test the bot**

## Testing your voicebot

There are two ways to test your bot before publishing it:

**1 – Testing whilst building**

* In the 'Bot Dialogs' menu, open the Emulator on the bottom right and click the 'debugger' button.&#x20;
* Change it to 'voice'
* Now you can speak to your bot and test it!

![](<../.gitbook/assets/image (387).png>)

**2 – Testing the real experience**

You can also enact the real experience by calling the Chatlayer test number: +3238081698.&#x20;

{% hint style="info" %}
Only the people whose phone numbers were added in the phone configuration tab will be able to call the test number and test the bot.
{% endhint %}

## **Choosing a voice for your bot**

* Click on 'Settings' in the left menu and select 'voice'

![](<../.gitbook/assets/image (380).png>)

* Under 'Configure speech to text', select the language of your bot. You can also select the correct dialect if you'd like by clicking on the box 'Default dialect'
* Under 'Voices', select the voice you prefer&#x20;
* If you'd like to hear a sample of that voice, enter an example sentence in the box 'Text to try out' and click on the speaker that appears next to the voice to hear it read aloud

## Customizing your bot's voice with SSML

You can customize your bot's responses by using Speech Synthesis Markup Language (SSML) and enhance the conversational experience. A few examples of how you can tweak your bot's responses with SSML:

* Change certain pronunciation​s (especially handy when you have a brand name that needs to be pronounced a certain way)
* Change the speed​ of your bot's voice (for example, when giving a number that the user needs to write down, or spelling something)
* Play audio file​s
* Add pauses (natural breaks between blocks of information, just like a real human would do!)
* Pronounce words as characters
* Pronounce dates

There's much more cool stuff to do with SSML! See more here: [https://cloud.google.com/text-to-speech/docs/ssml](https://cloud.google.com/text-to-speech/docs/ssml)

{% hint style="info" %}
To enable SSML, you need to put \<speak> …  \</speak> around the entire bot text.&#x20;
{% endhint %}

{% hint style="info" %}
Using a Readspeaker (Nuance) voice? Then you need a different syntax. For example, when building a Flemish bot, this would be the SSML syntax: \<speak version="1.1" xml:lang="nl-BE">Goedemorgen\</speak>
{% endhint %}

Read more about Readspeaker's SSML guidelines here: [https://docs.readspeaker.com/assets/markup/ReadSpeaker\_SSML\_Documentation\_v1-3\_01.pdf](https://docs.readspeaker.com/assets/markup/ReadSpeaker\_SSML\_Documentation\_v1-3\_01.pdf)

## Forwarding and closing a call​

* Add an 'Action' dialog and select 'Forward Call'
* In the 'To' box, enter the phone number you'd wish to redirect the call to

![](<../.gitbook/assets/image (388).png>)

{% hint style="info" %}
The phone number should contain a country code but no leading zeros or '+' sign.\
For example: 0800 55 800 becomes 32800 55 80
{% endhint %}

* After setting up your phone number, make sure to add another action 'Close Call' to make sure your bot hangs up after forwarding the call

![](<../.gitbook/assets/image (377).png>)

## Silence detection event​

If the user doesn't reply to the bot, or it doesn't detect an answer, you can let it repeat the question by using a 'Silence detection event' – Described [here](../bot-answers/events.md#silence-detected-event).

![](<../.gitbook/assets/image (386).png>)

## Putting your voice bot into production

When you're ready to move your bot into production, please [get in touch](../support/get-in-touch.md). We will set up a specific phone number for your bot which can be used to call directly or forward calls to. A typical phone architecture looks like this:

![](<../.gitbook/assets/image (373).png>)

## Voice message format type for input validation

You can save anything the user is saying as a variable by using the voice message format type in an input validation. Read more [here](../bot-answers/dialog-state/user-input-bot-dialog.md#voice-message).

