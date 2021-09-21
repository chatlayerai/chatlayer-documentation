# Data retention

Some of our customers may need to review their cloud data retention policy to adhere to company policies or certification standards. To accommodate that need, our platform offers custom data retention settings in every bot.

This article will explain the ins and outs of the data retention settings, and what happens with your data once this feature is enabled.

{% hint style="warning" %}
Is Data retention not visible in your settings? Our Enterprise and Corporate customers can have it enabled by contacting [Support](mailto:support@chatlayer.ai).
{% endhint %}

## Enable Retention

In Settings &gt; Bot Settings, you can now find the 'Data retention' settings:

![](../../.gitbook/assets/image%20%28596%29.png)

Toggle 'Customise retention' to make use of the Data retention feature. Once enabled, you can specify what the specific retention period \(in days\) should be for each section in the platform:

### Conversations

Conversations are the conversations users have had with the bot. These conversations can be found in the History &gt; Conversations menu.

### Sessions

Per default, sessions are expired after 30 days. That means that session information and variables are deleted after 30 days. This can be changed with the customised data retention so that the session expires after a configurable amount of days after the last session activity.

It is also possible to delete the session at any point in the conversation, for example after a couple of hours and you want the user to re-identify themselves in the bot. This can be done using this [API endpoint](https://api.chatlayer.ai/v1/docs/#operation/deleteSessionDataByConversationId).

### Error history

If an API integration is used, and this throws an error, this error will end up in History &gt; Error logs. With the customised data retention settings you can choose when these logs are deleted.

### Training expressions

In the menu NLP &gt; Train, expressions are stored used to train the NLP. These are expressions from actual user conversations. Read more about the training expressions [here](https://docs.chatlayer.ai/understanding-users/natural-language-processing-nlp/tutorial-train-your-bot-based-on-actual-user-messages).

{% hint style="info" %}
Note that changing the data retention settings take about a day to be visible in the platform.
{% endhint %}

## Draft / Live

The draft and live version of a bot can have different data retention settings. This means that it is possible to retain testing data in your draft bot longer than actual user data in your live bot.

Simply change to your live environment \(by going to Publish &gt; Open live mode\) and change the settings while in the live mode of the bot.

## No custom data retention?

If you wish to not make use of this feature, but still protect some of your user's data, you can use '[Sensitive variables](https://docs.chatlayer.ai/bot-answers/settings/secure-variables-gdpr#sensitive-variables-gdpr)'. With this functionality, variables are never stored in your database, for example to protect private user information.

It is also important to note that sessions are deleted automatically after 30 days. The other components; conversations, error history and training expressions, are deleted after a year \(365 days\) if custom data retention is not enabled.


