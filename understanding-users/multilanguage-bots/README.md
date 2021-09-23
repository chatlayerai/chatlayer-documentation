# Multilingual bots

Chatlayer supports many languages. From Dutch to English, Hindi and Afrikaans – find the complete list [here](../natural-language-processing-nlp/supported-languages.md).

## Primary language vs. secondary languages

When you create a new bot, you need to choose a **primary language**. This is the language in which you will develop the bot. In other words, this language is the one that is shown in the 'Bot dialogs' module where you will configure all the messages, button labels, content, links and logic of the bot.

When creating a new bot, you can also choose \(multiple\) **secondary languages**. To configure the copy for these languages, you can use the [Translations](translations.md) tool. 

The structure and logic of the bot is defined once and will then be reused for all languages. That means that you only have to build the bot once, and then simply can translate it. If you add functionalities or conversational flows, they will automatically be added to the secondary languages as well. This makes sure your bot remains in sync and offers a consistent experience in all languages.

## Managing a multi-lingual NLP

When you have created a multi-lingual bot, you will notice that in the NLP module, you can switch the active language in the menu bar at the top, upper right. When you switch languages, the color of the interface will change.

Things to remember when managing NLP models in more than one language:

* If you add an intent, the intent will automatically be added to all other languages as well. You can add intents in the primary as well as in the secondary languages.
* If you add an expression, the expression is language-dependent and will only be added to the active language model.
* As language models are independent from each other, so you'll have to train and publish them separately. That means that if you make changes in two languages, you will have to train and publish both. 
* The number of expressions that is displayed under 'Intents' is the number of expression for the active language.

![](../../.gitbook/assets/image%20%28242%29.png)

## Talking to the user in the right language

If you have built your bot to support multiple languages, you want it to talk to the user in their own language. A bot that doesn't have any information about the user's language will automatically use the primary language.

{% hint style="info" %}
Language detection can't be applied to text, so a chatbot cannot figure out what language the user is speaking based on what they're saying to the bot. Instead, it will use channel information. On Facebook, for example, the bot will use the value it receives from the FB user API. For the web widget, it'll use the SDK language.
{% endhint %}

#### Language detection flow

You can use the `Language detection` ****option to check if the user's language is supported by your bot. You can find this feature under `Bot Settings.`

* If the user's language is supported, the user will be routed to the `Introduction` dialog
* If the language is not supported by the bot, the user will be routed to a bot dialog of your choosing

![](../../.gitbook/assets/image%20%28654%29.png)

{% hint style="warning" %}
Whenever the user types an expression in a language other than the `preferredLanguage` activated, the bot will not automatically switch to that language. If the expression is in a language that the bot knows, the expression will be processed and the bot will answer in the original `preferredLanguage`.
{% endhint %}

* Let's create an input validation dialog that allows the user to select their preferred language. You can name it 'Choose language'
* In the `Choose language` dialog, ask the user in what language they want to continue
* Make sure to save this input as a variable with the name `preferredLanguage` 
* If you use buttons that the user can click to select a language, please make sure they also contain the `preferredLanguage` variable and a two-letter language code \(en, nl, fr, de, ...\) for the value

Our dialog now looks like this:

![Click on the image to enlarge it](../../.gitbook/assets/image%20%28652%29.png)

#### Web widget

In the web widget you can trigger a specific bot language based on the language of the page the user is looking at. Learn more [here](../../channels/webwidget/#default-locale).

#### Voice

When using a voicebot that talks to user, for example, on the phone, the bot will greet the user in their default language. However, when the user starts talking for the first time, the user's preferred language is detected based on their first expression. The bot will automatically switch to that language and continue the entire conversation in the detected language.

{% hint style="info" %}
Language recognition is currently only available if the Google Speech-To-Text \(STT\) voice is used for all languages supported by the bot. When you mix voices, the language recognition does not work.
{% endhint %}

{% hint style="info" %}
Language recognition only works for voice. When it comes to chatbots \(aka text\), the bot will detect the user's language based on the channel's parameters. For the web widget, the bot will use the language that was set in the SDK. For FB messenger, the bot uses the language value it received from the FB user API.
{% endhint %}

