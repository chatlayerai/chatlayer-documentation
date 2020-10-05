# Publishing your bot

Our platform provides 2 environments: staging and production, to support working in parallel on a new version of your chatbot without interfering with your production version which is talking to your users in real-time. You have access to both environments.

* Staging \('Draft'\)
  * [https://cms-staging.chatlayer.ai](https://cms-staging.chatlayer.ai)
  * Used to build and test new bot versions and improve your NLP model
* Production \('Live'\)
  * [https://cms.chatlayer.ai](https://cms.chatlayer.ai)
  * The production chatbot that is already communicating with your users
* **We recommend not changing data and configuration \(flows, NLP, settings\) directly in your production environment as this can break your live bot.**

Once your bot is ready and tested in the staging environment, it's time to publish your bot to the production environment.

If you want to run your bot within Facebook Messenger, we advise you to set up a separate Facebook page and app for your staging version of the bot.

{% hint style="info" %}
Each day your production user messages are added to the staging environment so that you can train your NLP models every day, based on real user data.
{% endhint %}

To publish your bot, go to the 'Versioning' module in the staging environment.

![](../.gitbook/assets/image%20%2894%29.png)

Enter a description for the new version of your bot and publish it by clicking the button. You will then be prompted to choose between 'Publish Full Bot' and 'Publish NLP Only':

![](../.gitbook/assets/image%20%28178%29.png)

**'Publish Full Bot'** will publish both the latest NLP model and all of your flows.

**'Publish NLP Only'** will only publish your NLP model, leaving the flows of the Live version unchanged.   
Take into account that:

* The NLP needs to be trained **before** publishing it
* You cannot publish just the NLP if no NLP changes have been made since the last publish
* You cannot publish just the NLP if Intents have been removed from your Draft version since the last publish. This is to avoid showing flows that are linked to Intents that no longer exist. That means that removing Intents from the Live version is only possible through 'Publish Full Bot'. Adding new Intents to Live with 'Publish NLP Only' on the other hand, is possible.

{% hint style="info" %}
Different NLP models in different environments will never be 100% identical. There are random factors inherent to this kind of machine learning that create different results, even with the same data. These differences are usually small, but in some cases where intents are very similar, the differences can be more apparent and lead to significant differences in confidence or entirely different classifications. 
{% endhint %}

