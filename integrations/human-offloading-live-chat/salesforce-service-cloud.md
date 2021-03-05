# Salesforce Service Cloud

The Chatlayer.ai Salesforce Service Cloud integration allows you to easily transfer a user from the bot to an agent active in the Salesforce Service Cloud Console.

{% hint style="info" %}
The Salesforce Service Cloud integration is available as an add-on to our Enterprise pack.
{% endhint %}

## Installation & set-up

Install the Chatlayer.ai package in the Salesforce AppExchange, and ask an administrator to follow the Setup Instructions.

![](../../.gitbook/assets/image%20%28406%29.png)

In the final step, you will be requested to fill in the bot id, access token and version of the bot into the "Create New Configuration" window.

![](../../.gitbook/assets/image%20%28405%29.png)

### Bot id

To find the bot id, navigate to the bot you want to connect into Salesforce. You can find your bot id in the URL of your bot.

`https://cms.chatlayer.ai/bots/`**`thisIsYourBotId`**`/analytics/dashboard`

Copy paste your bot id into the Salesforce new configuration window.

### Access token

Create a new access token by navigating to the bot overview page, and selecting "Tokens" in the menu.

![](../../.gitbook/assets/image%20%28404%29.png)

Click "Generate token" to generate a new token. You can give it any name you like.

Copy paste your Access Token into the Salesforce new configuration window.

### Version

You can choose to connect the Draft or Live version of your bot to Salesforce. Typically, the Draft version is used for testing, and the Live version is used by your actual customers. Learn more about bot versions here:

{% page-ref page="../../bot-answers/publishing-your-bot.md" %}



