# Publishing your bot

Publishing your bot is easier than you think! This article will guide you how to publish your bot so your users can enjoy the bot.

## Draft version

First, you need to create a draft version of your bot. You can do this by going to [app.chatlayer.ai](http://app.chatlayer.ai/) and start building your awesome bot!

Once you have your flow, a channel, and fully tested your bot, it is ready to go live so real users can use your bot.

* Go to  the 'Publish' menu on the left hand side. You should see the following if you have not published your bot before:

![](../../.gitbook/assets/image%20%28583%29.png)

* Click 'Publish' to start publishing your bot:

![](../../.gitbook/assets/image%20%28584%29.png)

* Add release notes to keep track of your changes in that specific version, and click 'Publish'

{% hint style="info" %}
Depending on the size of your bot, publishing could take a while.
{% endhint %}

## Live version

Once you have published your bot, you will see the following:

![](../../.gitbook/assets/image%20%28586%29.png)

Clicking on 'Open live mode' will take you to the live version of your bot. This is the version that users will interact with. Once you are in the live environment, you will see a red banner to visualize you are in the LIVE environment:

![](../../.gitbook/assets/image%20%28585%29.png)



{% hint style="warning" %}
We recommend not changing data and configuration \(flows, NLP, settings\) directly in your production environment as this can break your live bot which your customers are actively using. 
{% endhint %}

## Publishing your NLP

Take into account that:

* The NLP needs to be trained **before** publishing it
* You cannot publish just the NLP if no NLP changes have been made since the last publish
* You cannot publish just the NLP if Intents have been removed from your Draft version since the last publish. This is to avoid showing flows that are linked to Intents that no longer exist. That means that removing Intents from the Live version is only possible through 'Publish Full Bot'. Adding new Intents to Live with 'Publish NLP Only' on the other hand, is possible.

{% hint style="info" %}
Different NLP models in different environments will never be 100% identical. There are random factors inherent to this kind of machine learning that create different results, even with the same data. These differences are usually small, but in some cases where intents are very similar, the differences can be more apparent and lead to significant differences in confidence or entirely different classifications. 
{% endhint %}

## Maintaining the bot

Once your bot is live and customers are using it, you can keep making changes to your bot in the DRAFT environment of [app.chatlayer.ai](http://app.chatlayer.ai/) . Once your changes are finished, you can again publish your bot. This will overwrite the existing version of your LIVE bot with the state of your DRAFT bot.

{% hint style="warning" %}
More questions about publishing your bot? Check out the[ FAQ page](https://docs.chatlayer.ai/bot-answers/publishing-your-bot/publishing-new) or [contact us](http://support.chatlayer.ai). 
{% endhint %}

