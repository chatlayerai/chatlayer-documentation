# Multilingual bots

Chatlayer.ai was built to support all the languages that your customers speak. From Dutch to English, Hindi and Afrikaans – you can find the complete list [here](../natural-language-processing-nlp/supported-languages.md).

## Primary language vs secondary languages

When you create a new bot, you need to choose a primary language. This is the language in which you will develop the bot. In other words, this language is the one that is shown in the 'Bot dialogs' module where you will configure all the messages, button labels, content, links and logic of the bot.

When creating a new bot, you can also choose \(multiple\) secondary languages. To configure the copy for these languages, you can use the [Translations](translations.md) tab. 

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

#### Language detection flow

Use the **Language detection** option to check if the user's language is supported by your bot. You can find this feature under 'Bot Settings'.

![](../../.gitbook/assets/image%20%28244%29.png)

* If the user's language is supported, they will be routed to the 'Introduction' bot dialog
* If the language is not supported by the bot, the user will be routed to a bot dialog of your choosing

{% hint style="warning" %}
Whenever the user types an expression in a language other than the preferredLanguage at that moment, the bot will not automatically switch to that language. If the expression is in a language that the bot knows, the expression will be processed and the bot will answer in the original preferredLanguage.
{% endhint %}

In the `Choose language` bot dialog, create an input validation that requests a language from the user and saves it as the `preferredLanguage` variable.

Our reference implementation looks like this:

![](../../.gitbook/assets/image%20%28221%29.png)

* Make sure you save the language as the `preferredLanguage` variable, with a two-letter language code \(en, nl, fr, de, ...\)
* Change the format type to `language` to make sure that, when the user types "English" instead of clicking the button, they still get English as the bot's language. Learn more about language parsing [here](../../bot-answers/dialog-state/user-input-bot-dialog.md#language).

{% hint style="info" %}
If you want to create an intent that allows a user to change their current language to another one, you can use a "clear session" action bot dialog to clear `preferredLanguage`, after which you can guide the user to the input validation detailed above.
{% endhint %}

#### Web widget

In the web widget you can trigger a specific bot language based on the language of the page the user is looking at. Learn more [here](../../channels/webwidget.md#default-locale).

#### Voice

When using a chatbot with voice capabilities, for example on the phone, the voice bot will greet the user in their default language. However, when the user starts talking for the first time, the language of the user will be detected based on this first expression. The bot will automatically switch to that language and continue the whole conversation in that same language.  Note that it will only be able to switch to a language supported by the bot. 

This feature is currently only available if Google Speech-To-Text \(STT\) is used for all languages supported by the bot. 

