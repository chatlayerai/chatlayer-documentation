# Publishing your bot

Chatlayer.ai provides two environments, staging and production, to support working in parallel on a new version of your chatbot without interfering your production version which is talking to your real users. You have access to both environments.

* Staging \('Draft'\)
  * [https://cms-staging.chatlayer.ai](https://cms-staging.chatlayer.ai)
  * Used to build and test new bot versions and improve your NLP model.
* Production \('Live'\)
  * [https://cms.chatlayer.ai](https://cms.chatlayer.ai)
  * The production chatbot is communicating with your actual customers
* **We recommend to not change data and configuration \(flows, NLP, settings\) directly in your production environment**

Once your bot is ready and has been tested in the staging environment, it's time to publish your bot to the production environment.

If you have a bot that you want to run on Facebook Messenger, we advise to set-up a separate staging Facebook page and app for your staging version of the bot.

{% hint style="info" %}
Each day your production user messages are added in the staging environment so that you can  train your NLP models every day based on actual user data.
{% endhint %}

To publish your bot, go to the "Versioning" module in the Chatlayer.ai staging environment.

![](../.gitbook/assets/image%20%2894%29.png)

Enter a description for the new version of your bot, and publish it by clicking the button. 

You will then be prompted to choose between 'Publish Full Bot' and 'Publish NLP Only':

![](../.gitbook/assets/image%20%28178%29.png)

**'Publish Full Bot'** will publish both your latest NLP model and all your flows.

**'Publish NLP Only'** will only publish your NLP model, leaving the flows of the Live version unchanged. Take into account that:

* The NLP needs to be trained before publishing it
* You cannot publish NLP only if no NLP changes have been made since the last publish
* You cannot publish NLP only if Intents have been removed from your Draft version since the last publish. This is to avoid having flows Live that are linked to Intents that no longer exist. Removing Intents from the Live version is thus only possible with 'Publish Full Bot'. Adding new Intents to Live with 'Publish NLP Only' on the other hand, is possible.

{% hint style="info" %}
Different NLP models in different environments will never be 100% identical. There are random factors inherent to this kind of machine learning that create different results even on the same data. These differences are generally minimal, but in some cases where intents are very close, the differences can be more apparent and lead to significant differences in confidence or even other classifications entirely.
{% endhint %}

