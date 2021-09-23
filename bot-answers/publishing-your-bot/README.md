---
description: >-
  Is your bot ready to go live and start talking to your users? Great, on this
  page we'll tell you how to push your bot live and make changes without
  breaking it.
---

# How to publish your bot

## Understanding the DRAFT version

When building your bot, you do so in the DRAFT environment. When you surf to [app.chatlayer.ai](http://app.chatlayer.ai/), you always start in the DRAFT environment too. 

The DRAFT environment is your building environment, it's where you can make changes to the bot, test out flows, and work on the NLP. Once you're happy with your bot and want to push it live, you need to publish it to the LIVE environment. 

### Why can't I make changes in the live bot?

You can, but we do not recommend it whatsoever. The LIVE bot is talking directly with your users, if you change something and break your bot, your bot will be broken for your users as well. Making changes in the draft environment is much safer since this version isn't talking to your users. 

{% hint style="info" %}
Always make changes in the DRAFT bot. Once you're happy with the new changes and tested everything, you can publish the bot to the LIVE environment so your users can enjoy the new update too.
{% endhint %}

### How to publish your bot

* When ready, click on the 'Publish' tab in the left side column. If you never published your bot before, you should see the following screen:

![](../../.gitbook/assets/image%20%28613%29.png)

* Now click 'Publish' to publish your bot:

![Publishing your bot](../../.gitbook/assets/image%20%28611%29.png)

You can add some notes to each new bot version keep track of the changes you made in that specific version. This is especially handy when multiple people are working on the same bot.

{% hint style="info" %}
Depending on the size of your bot, publishing could take a while. Relax, your bot is on its way!
{% endhint %}

## Understanding the LIVE version

Once you published your bot, you will see the following screen:

![](../../.gitbook/assets/image%20%28612%29.png)

When you click on 'Open live mode', it will take you to the LIVE environment of your bot. This version of your bot is the one users will interact with. Once you are in the LIVE environment, you will see a red banner on top to remind you that you are working in the LIVE environment:

![](../../.gitbook/assets/image%20%28585%29.png)

{% hint style="warning" %}
We recommend not changing any data or configurations directly in your LIVE environment as this can break the bot that your customers are actively using. 
{% endhint %}

## Publishing your NLP

Take into account that:

* The NLP needs to be trained **before** publishing it
* You cannot publish just the NLP if no NLP changes have been made since the last publish
* You cannot publish just the NLP if intents have been removed from your DRAFT version since the last publish. This is to avoid showing flows that are linked to intents that no longer exist. That means that removing intents from the LIVE version is only possible through 'Publish full bot'. Adding new intents to LIVE with 'Publish NLP Only' on the other hand, is possible.

{% hint style="info" %}
Different NLP models in different environments will never be 100% identical. There are random factors inherent to this kind of machine learning that create different results, even with the same data. These differences are usually small, but in some cases where intents are very similar, the differences can be more apparent and lead to significant differences in confidence or entirely different classifications. 
{% endhint %}

## Maintaining the bot

Once your bot is live and users are talking to it, you can keep making changes to your bot in the DRAFT environment. Once your changes are final, you can publish a new LIVE version of your bot. This will overwrite the existing version of your LIVE bot.

{% hint style="warning" %}
More questions about publishing your bot? Check out the[ FAQ page](https://docs.chatlayer.ai/bot-answers/publishing-your-bot/publishing-new) or [contact us](http://support.chatlayer.ai). 
{% endhint %}

