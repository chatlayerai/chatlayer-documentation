---
description: >-
  This page will walk you through the different components and sections of our
  Analytics page, which you can use to analyse and optimise your bot in the
  future.
---

# Analytics

## Dashboard

The dashboard is the main page in our Analytics. It shows a lot of important information about your bot in a quick and simple overview:

![](../../.gitbook/assets/image%20%28560%29.png)

Let's go through all the components one by one, and see what they exactly mean for your bot. Each section also includes detailed information about how that specific component can be interpreted and used to improve your bot.

### Filtering

![](../../.gitbook/assets/image%20%28555%29.png)

With these filters you can adjust the information shown on the dashboard, and create specific views for your bot. This provides valuable information to see how your bot progresses over time.

'All Channels' allows you to filter on specific channels, and 'All languages' shows information about your bot in different languages.

{% hint style="warning" %}
Not seeing any data in the overview? Then you might be looking at the 'DRAFT'  data, aka your unpublished bot, while your customers are communicating with your 'LIVE' \(= published\) bot. Switch to 'LIVE' with your filtering to see the actual customer data.  
{% endhint %}

The timestamp of the data you see in the analytics dashboard is based on the timezone of your browser.

### User Messages

![](../../.gitbook/assets/image%20%28559%29.png)

The 'User Messages' section shows an overview of how many messages are:

* Understood: the user expression is recognized correctly and the corresponding intent was triggered
* [Button clicks](https://docs.chatlayer.ai/bot-answers/analytics/intents): this shows how often users clicked on a button, carousel, quick reply etc.
* [Not understood](https://docs.chatlayer.ai/bot-answers/analytics/intents): the user expression is not understood, meaning it is below the NLP threshold, so the user saw the 'not understood message'

Clicking on 'Details' in the right upper corner will bring you to the [Conversations ](https://docs.chatlayer.ai/bot-answers/analytics/conversations)page. 

{% hint style="info" %}
Seeing a 'not understood' percentage of &gt; 15%? You should look into which intents are not understood correctly and improve your NLP by using the [Train tab](https://docs.chatlayer.ai/understanding-users/natural-language-processing-nlp/tutorial-train-your-bot-based-on-actual-user-messages). Creating better[ 'not understood' messages](https://docs.chatlayer.ai/tips-and-best-practices/not-understood-bot-dialog) will also create a better user experience.
{% endhint %}

### Users

![](../../.gitbook/assets/image%20%28557%29.png)

The 'Users' section gives information about how many users have interacted with your bot during that period. A [user ](https://docs.chatlayer.ai/bot-answers/analytics/definitions#user)is someone who sends at least one message to the bot, while a [returning user](https://docs.chatlayer.ai/bot-answers/analytics/definitions#returning-user) is someone who has had multiple conversations with the bot in this time period.

Clicking on 'Details' in the right upper corner will bring you to the [Users](https://docs.chatlayer.ai/bot-answers/analytics/users) page. 

{% hint style="info" %}
Seeing a lot of new users? That's not a bad thing! It could be that the user finds their answer quickly and doesn't have to return within the filtered time period. It's more telling to see if the usage of your bot does not decrease significantly over time, because that would mean users are not using the bot as much any more.
{% endhint %}

### Conversations

![](../../.gitbook/assets/image%20%28558%29.png)

The first 'Conversations' component shows the distribution of bot conversations in all available languages. 

Switching from 'Languages' to 'Channels' will show the use of the bot over different channels \(if these are used of course\).

{% hint style="warning" %}
Is the number of conversations in the Analytics overview different from the number of conversations in the conversation history? That's because in Analytics, we show all conversations, whereas in the history overview, we only include conversations where the user actually replied.
{% endhint %}

![](../../.gitbook/assets/image%20%28551%29.png)

The second 'Conversations' component shows the human offloading, average messages per conversation, and the average length of conversations:

* Human agent takes over: a conversation is marked as a human handover when it includes a triggered "Send to offload provider" action
* Messages per conversation: this category represents the most occurring length of a conversation in number of messages for interactions between your bot and its users.
* Conversation duration: this category represents the most occurring length of a conversation in number of minutes for interactions between your bot and its users

{% hint style="success" %}
Let's say, you made some significant changes to decrease human offloading on April 1st. The analytics can help to see what the offloading rate before and after April 1st was, so you can see the effect these changes had.   
  
Did the offloading rate indeed decrease? Compare these stats over the same amount of time for the best comparison, so the entire month of March and the entire month of May for example.
{% endhint %}

Clicking on 'Details' in the right upper corner will bring you to the [Conversations ](https://docs.chatlayer.ai/bot-answers/analytics/conversations)page. 

### Most triggered intents

![](../../.gitbook/assets/image%20%28561%29.png)

'Most triggered intents' shows the top 5 intents that were triggered most often, including the number of calls and their percentages.

{% hint style="success" %}
The example above shows that 50% of intents triggered were for an offload request. Some customers mention offloading immediately in their introduction, making it very easy for the user to ask for human assistance right away \(instead of using the bot to get their answer\). This defeats the purpose of a good chatbot.

If this happens for your bot too, try to decrease offloading by setting the[ correct expectations](https://docs.chatlayer.ai/tips-and-best-practices/what-makes-a-good-chatbot#2-set-the-right-expectations) and [guiding the user](https://docs.chatlayer.ai/tips-and-best-practices/what-makes-a-good-chatbot#3-guide-the-user) to their answer via the bot instead of asking for a human agent. 
{% endhint %}

Clicking on 'Details' in the right upper corner will bring you to the [Intents ](https://docs.chatlayer.ai/bot-answers/analytics/intents)page. 

### Active customers

![](../../.gitbook/assets/image%20%28552%29.png)

'Active customers' shows when your users are most active and interact with the bot.

Clicking on 'Details' in the right upper corner will bring you to the [Users - Activity](https://docs.chatlayer.ai/bot-answers/analytics/users) page where you can see the user activity per hour. 

{% hint style="info" %}
Use the knowledge of when your customers are most active to your advantage. Do you see an increase on a specific day? Make sure you have extra staff available that day to account for the extra offloading requests that could occur.
{% endhint %}

### Flows

![](../../.gitbook/assets/image%20%28556%29.png)

'Flow - Most popular bot dialogs' shows which route most users take in your bot. In the example above, 15.9% of users first go to the website router, and the same amount of users first go to the introduction or to the 'Intro Hello' intent. 3.5% immediately goes to offloading and 3.5% got a 'not understood' message.

Hover over one of the specific bot dialogs to show the option 'Open'. Now click again to see a detailed overview of the exact flow the user is following:

![](../../.gitbook/assets/image%20%28554%29.png)

{% hint style="success" %}
The example above shows that 63.6% of users immediately create an incident. If this doesn't fit the bot scope, make sure that creating an incident is more 'hidden' in the conversation and guide the user to search for their answer first.
{% endhint %}

![](../../.gitbook/assets/image%20%28553%29.png)

{% hint style="success" %}
This example shows that 73.7% of users immediately see a 'not understood' after the introduction. Use information like this to optimize your bot. Check in the [Train tab](https://docs.chatlayer.ai/understanding-users/natural-language-processing-nlp/tutorial-train-your-bot-based-on-actual-user-messages) which expressions are not understood, and improve your NLP model accordingly. Also, [manage expectations](https://docs.chatlayer.ai/tips-and-best-practices/what-makes-a-good-chatbot#2-set-the-right-expectations) in your introduction. If a user doesn't know what your bot can do for them, they'll ask anything, increasing the chance of getting a 'not understood' message because they're asking questions outside of the bot scope.
{% endhint %}

Clicking on 'Details' in the right upper corner will bring you to the [User Flow](https://docs.chatlayer.ai/bot-answers/analytics/user-flow) page. 

