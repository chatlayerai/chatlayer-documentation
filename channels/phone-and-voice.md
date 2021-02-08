---
description: >-
  Follow these step-by-step instructions on how to set up the phone and voice
  channel.
---

# Phone & voice

## Activating the phone channel

* Go to the 'Channels' tab on the left and click on the '+' button next to 'Phone'.

![Click the &apos;+&apos; button to add a phone connection](../.gitbook/assets/image%20%28179%29.png)

* Click on 'create' if you see this pop-up:

![](../.gitbook/assets/image%20%28390%29.png)

## Setting up a phone configuration

* Click on the blue button 'Create configuration' to set up a test caller

![](../.gitbook/assets/image%20%28389%29.png)

* You will see the following pop-up:

![You can keep the Chatlayer test number for now](../.gitbook/assets/image%20%28391%29.png)

* Under 'Caller' you can fill out the phone number of the **person who will test the bot**
* Under 'Languages' you can select the languages of your bot
* Under 'Description' you can fill out the name of the **person who will test the bot**

## Testing your voicebot

There are two ways to test your bot before publishing it:

**1 – Testing whilst building**

* In the 'Bot Dialogs' menu, open the Emulator on the bottom right and click the 'debugger' button. 
* Change it to 'voice'
* Now you can speak to your bot and test it!

![](../.gitbook/assets/image%20%28387%29.png)

**2 – Testing the real experience**

You can also enact the real experience by calling the Chatlayer test number: +3238081698. 

{% hint style="info" %}
Only the people whose phone numbers were added in the phone configuration tab will be able to call the test number and test the bot.
{% endhint %}

## **Choosing a voice for your bot**

* Click on 'Settings' in the left menu and select 'voice'

![](../.gitbook/assets/image%20%28380%29.png)

* Under 'Configure speech to text', select the language of your bot. You can also select the correct dialect if you'd like by clicking on the box 'Default dialect'
* Under 'Voices', select the voice you prefer 
* If you'd like to hear a sample of that voice, enter an example sentence in the box 'Text to try out' and click on the speaker that appears next to the voice to hear it read aloud

## Customizing your bot's voice with SSML

You can customize your bot's responses by using Speech Synthesis Markup Language \(SSML\). With SSML, you can:

* Change certain pronunciation​s
* Change the speed​ of your bot's voice
* Play audio file​s
* Add pauses
* Pronounce words as characters
* Pronounce dates

And much more! See all options here: [https://cloud.google.com/text-to-speech/docs/ssml](https://cloud.google.com/text-to-speech/docs/ssml)

{% hint style="info" %}
To enable SSML, you have to put &lt;speak&gt; …  &lt;/speak&gt; around the entire bot response. 
{% endhint %}

{% hint style="info" %}
Building a Flemish bot? Then you should put &lt;speak version="1.1" xml:lang="nl-BE"&gt; ... &lt;/speak&gt; around your messages
{% endhint %}

## Forwarding and closing a call​

* Add an 'Action' dialog and select 'Forward Call'
* In the 'To' box, enter the phone number you'd wish to redirect the call to

![](../.gitbook/assets/image%20%28388%29.png)

{% hint style="info" %}
The phone number should contain a country code but no leading zeros or '+' sign.  
For example: 0800 55 800 becomes 32800 55 80
{% endhint %}

* After setting up your phone number, make sure to add another action 'Close Call' to make sure your bot hangs up after forwarding the call

![](../.gitbook/assets/image%20%28377%29.png)

## Silence detection event​

If the user doesn't reply to the bot, or it doesn't detect an answer, you can let it repeat the question by using a 'Silence detection event' – Described [here](../bot-answers/events.md#silence-detected-event).

![](../.gitbook/assets/image%20%28386%29.png)

## Putting your voice bot into production

When you're ready to move your bot into production, please [get in touch](../support/get-in-touch.md). We will set up a specific phone number for your bot which can be used to call directly or forward calls to. A typical phone architecture looks like this:

![](../.gitbook/assets/image%20%28373%29.png)

## Voice message format type for input validation

You can save anything the user is saying as a variable by using the voice message format type in an input validation. Read more [here](../bot-answers/dialog-state/user-input-bot-dialog.md#voice-message).



