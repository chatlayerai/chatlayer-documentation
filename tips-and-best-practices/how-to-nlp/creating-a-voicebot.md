# Creating a voicebot

* Click on 'Settings' in the left menu and select 'voice'

![](../../.gitbook/assets/image%20%28380%29.png)

* Under 'Configure speech to text', select the language of your bot. You can also select the correct dialect if you'd like by clicking on the box 'Default dialect'
* Under 'Voices', select the voice you prefer 
* If you'd like to hear a sample of that voice, enter an example sentence in the box 'Text to try out' and click on the speaker that appears next to the voice to hear it read aloud

### Speech-To-Text

Google offers +/- 125 languages and variants. Check their page to see all languages supported by Cloud Speech-to-Text: [https://cloud.google.com/speech-to-text/docs/languages/](https://cloud.google.com/speech-to-text/docs/languages/).

Microsoft offers fewer languages, but some are higher quality than Google's. Find them all here: [https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/language-support](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/language-support)

{% hint style="success" %}
Did you know that Chatlayer's Flemish STT is considered the best according to independent companies? And yes, we're very proud of that.
{% endhint %}

### Text-To-Speech

Text-to-Speech \(TTS\) technology leverages neural network techniques to deliver a human‑like, engaging, and personalized user experience. [Readspeaker](https://www.readspeaker.com/languages-voices/​)​ is one of our partners that offers quality voices in Flemish and Belgian French​. They also do custom voices. 

Here's a list of [Google's Text-to-Speech voices](https://cloud.google.com/text-to-speech/docs/voices), as wel as [Microsoft's voices](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/language-support#text-to-speech).

## Testing your voicebot

* In the 'Bot Dialogs' menu, open the Emulator on the bottom right and click the 'debugger' button. 
* Change it to 'voice'
* Now you can speak to your bot and test it!

![](../../.gitbook/assets/image%20%28387%29.png)

## Customising your bot's voice with SSML

You can customise your bot's responses by using Speech Synthesis Markup Language \(SSML\). With SSML, you can:

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

![](../../.gitbook/assets/image%20%28388%29.png)

{% hint style="info" %}
The phone number should contain a country code but no leading zeros or '+' sign.  
For example: 0800 55 800 becomes 32800 55 80
{% endhint %}

* After setting up your phone number, make sure to add another action 'Close Call' to make sure your bot hangs up after forwarding the call

![](../../.gitbook/assets/image%20%28377%29.png)

## Silence detection event​

If the user doesn't reply to the bot, or it doesn't detect an answer, you can let it repeat the question by using a 'Silence detection event'

![](../../.gitbook/assets/image%20%28386%29.png)

Find more info [here](https://docs.chatlayer.ai/bot-answers/events​)

