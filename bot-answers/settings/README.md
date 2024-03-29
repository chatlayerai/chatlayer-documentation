# Settings

## Bot Details

In Bot Details you'll be able to see the name of your of bot as well as the primary and secondary languages you've added. Through Bot Details you can also change the amount of people who have access to the configuration of you bot through 'Bot Access'. To learn more about Bot Access click [here](https://docs.chatlayer.ai/organization-management/access-control).

## Bot Status

Click the status slider to temporarily disable the bot. The message configured under the `bot disabled` bot dialog will be shown. Read more about the `bot disabled` bot dialog [here](https://docs.chatlayer.ai/bot-answers/dialog-state#bot-disabled). 

## Maximum message length

Chatbots work best with short and concise messages. To avoid that messages that are too long are not understood, a maximum message length can be configured. Whenever a message is &gt; the characters stated in these settings, the bot will automatically go to a bot dialog of your choice. A bot message with text like: 'I am sorry, I work best with shorter messages. Could you please rephrase that?' is recommended for a good user experience. 

## Bot behaviour

The typing speed, or typing duration, is how fast the bot answers to the user. The higher the typing speed, the longer the user will see that the bot is 'typing' before they receive an answer. The right typing speed can create a positive, more humanlike experience for the user. The default typing speed is 1500ms, but try out different speeds to see what is best for your bot.

## Language detection

This setting allows you to enable the language detection flow when a user's locale isn't automatically detected or supported. Read more about this feature [here](../../understanding-users/multilanguage-bots/#language-detection-flow).

## API

{% page-ref page="../../integrations/custom-back-end-integrations/advanced-api-integrations.md" %}

## Bot import / export

{% hint style="info" %}
This feature is currently in beta. If you would like to have access to it, [get in touch](../../support/get-in-touch.md).
{% endhint %}

On this page you can export and import your bot. The export of your bot will include the bot’s NLP data and bot dialog configuration. It will not include analytics data, conversation history, error logs, older bot versions, channel or offloading configuration. 

Depending on the size of your bot, the export could take up to 30 minutes to finalize. As soon as the export is ready, you will be able to download it as a JSON file.

![](../../.gitbook/assets/image%20%28322%29.png)

Importing a bot can take up to 30 minutes. The uploaded file will be imported to the DRAFT version of the bot.

The export contains:

* NLP
  * Intents
  * Expressions
  * Entities
* Bot dialogs
  * Flows
  * Messages and translations
  * Variables

The export does not contain:

* Conversation history
* Analytics
* Channel settings
* Bot settings

{% hint style="warning" %}
Importing a bot will overwrite the current version of your bot. There is no way to recover a previous version of the bot
{% endhint %}



