# Publishing your bot

Our platform provides 2 environments: staging and production, to support working in parallel on a new version of your chatbot without interfering with your live version that's being used by your users in real-time. 

You have access to both environments:

1. **Staging \('Draft'\)**

* [https://cms.staging.chatlayer.ai](https://cms.staging.chatlayer.ai)
* Used to build and test new bot versions and improve your NLP model

2. **Production \('Live'\)**

* [https://cms.chatlayer.ai](https://cms.chatlayer.ai)
* The production chatbot that is already communicating with your users
* **We recommend not changing data and configuration \(flows, NLP, settings\) directly in your production environment as this can break your live bot.**

Once your bot is ready and tested in the staging environment, it's time to publish your bot to the production environment.

If you want to run your bot within Facebook Messenger, we advise you to set up a separate Facebook page and app for your staging version of the bot.

{% hint style="info" %}
The user messages from your live bot are added to the [Train tab](../../understanding-users/natural-language-processing-nlp/tutorial-train-your-bot-based-on-actual-user-messages.md) of both the live and draft versions of your bot. You can use this real user data to optimize your NLP models.
{% endhint %}

To publish your bot, go to the 'Versioning' module in the staging environment.

![](../../.gitbook/assets/image%20%28370%29.png)

Enter a description for the new version of your bot and publish it by clicking the button.

![](../../.gitbook/assets/image%20%28369%29.png)

Take into account that:

* The NLP needs to be trained **before** publishing it
* You cannot publish just the NLP if no NLP changes have been made since the last publish
* You cannot publish just the NLP if Intents have been removed from your Draft version since the last publish. This is to avoid showing flows that are linked to Intents that no longer exist. That means that removing Intents from the Live version is only possible through 'Publish Full Bot'. Adding new Intents to Live with 'Publish NLP Only' on the other hand, is possible.

{% hint style="info" %}
Different NLP models in different environments will never be 100% identical. There are random factors inherent to this kind of machine learning that create different results, even with the same data. These differences are usually small, but in some cases where intents are very similar, the differences can be more apparent and lead to significant differences in confidence or entirely different classifications. 
{% endhint %}

