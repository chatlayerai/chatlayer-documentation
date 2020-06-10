# Multi-language bots

Chatlayer.ai was built to support all the languages that your customers speak.

## Primary language vs secondary languages

When a bot is created, a user has to choose a primary language. This is the language in which the bot will be developed. In other words, this language is the language that is shown in the 'Bot dialogs' module where you configure all the messages, button labels, content, links and logic of the bot.

When a bot is created, the user also has the option to choose \(multiple\) secondary languages. To configure the copy-writing for these languages, you can use the [Translations](../bot-answers/dialog-state/translations.md) tab. 

The structure and logic of the bot is defined once and then reused for all languages. That means that you build the bot once, and then just translate it. If you add functionality or conversational flows, they will automatically be added to the secondary languages as well. This makes sure your bot remains in sync and offers a consistent experience for all languages.

## Managing a multi-lingual NLP

When you have created a multi-lingual bot, you will notice that in the NLP module, you can switch the active language in menu bar at the top, upper right. When you switch language, the color of the interface will change.

Things to note when managing NLP models in more than one language

* If you add an intent, the intent will automatically be added to all other languages as well. You can add intents in the primary as well as in the secondary languages. 
* If you add an expression, the expression is language dependent and will only be added to the active language model.
* As language models are independent of each other, you have to train and publish them separately. That means that if you make changes to two languages, you will have to train and publish them both. 
* The number of expressions that is displayed under the 'Intents' block is the number of expression for the active language.

![](../.gitbook/assets/image%20%28242%29.png)

## Talking to the user in the right language

If you have built your bot to support multiple languages, you want it to talk to the user in the language they prefer. A bot that doesn't have any information about the user's language will use the primary language.

#### Language detection flow

Use the **Language detection** option to check if the user's language is supported by the bot. You can find it under Bot Settings.

![](../.gitbook/assets/image%20%28244%29.png)

* If the user's language is supported, they will be routed to the Get Started bot dialog.
* If the language is not supported by the bot, the user will be routed to the bot dialog of your choice.

In the `Choose language` bot dialog, create an input validation that requests a language from the user and saves it as the `preferredLanguage` variable.

Our reference implementation looks like this:

![](../.gitbook/assets/image%20%28221%29.png)

* Make sure you save the language as the `preferredLanguage` variable, with a two-letter language code such as en, nl, fr, de, ...
* Change the format type to `language`, which will make sure that if the user types "English" instead of clicking the button, they will still get English as the bot language. Learn more about language parsing [here](../bot-answers/dialog-state/user-input-bot-dialog.md#language).

{% hint style="info" %}
If you want to create an intent that allows a user to clear their current language and use another bot in another language, you can use a "clear session" action bot dialog to clear `preferredLanguage`, and then you can route the user to the input validation detailed above.
{% endhint %}

#### Web widget

In the web widget you can trigger a specific bot language based on the language of the page the user is looking at. You can find more information [here](../channels/webwidget.md#default-locale).



