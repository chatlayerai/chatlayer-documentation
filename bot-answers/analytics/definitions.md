---
description: >-
  Throughout our analytics, we use several key terms. In order to fully
  understand these analytics, it's important for you to know the definition of
  these terms.
---

# Definitions

### Conversation

A conversation starts with a first message being sent, either by the bot or by the user. ​

{% hint style="info" %}
We start counting a new conversation when there is no interaction between your bot and a user for at least 15 minutes.​
{% endhint %}

You can try out your bot in the "test your bot" window within the platform. These conversations are not counted in your analytics or your billing.

In the **analytics dashboard** you can choose if you want to see the metrics for your DRAFT or LIVE conversations \(learn more about DRAFT and LIVE [here](../publishing-your-bot/)\). In your **billing**, both DRAFT and LIVE conversations will be counted.

One conversation happens in at most one channel. If the same user uses multiple channels to talk to the bot, all of these conversations will be counted separately in billing and analytics.

### User

A user is anyone who sends at least one message to the bot. 

If you're on an asynchronous channel like Facebook or WhatsApp, the user will stay the same throughout their entire lifecycle with the bot. This means that every Facebook user talking to the bot will only count as one user in the analytics.

If you're showing the bot through a web widget or custom implementation, by default every time somebody refreshes the web page and starts talking to the bot again, they'll be counted as a new user. However, some clients configure their web widgets in a way that recognizes a returning user via a Sender ID. This way, returning users are only counted once.

### Returning user

Users that have a conversation during and before the selected time range in the analytics dashboards are counted as a returning user.

If a user had multiple conversations during the selected time range, but no conversations before that range, they will not be counted as a returning user.

### User Message

A user message is every interaction by the user with the bot. This can be a typed expression, but also a button click, a file upload, etc.

### 'Not understood' message

A message is not understood if it's an expression that is not an exact match for one of the trained expressions and the NLP confidence of this expression is under the defined [NLP threshold](../../understanding-users/natural-language-processing-nlp/settings.md).

### Button clicks

Some messages will consist of the user clicking a button. This button can appear in a Button template, Quick Replies, Carousel, List, ...

### Channel

Analytics for every channel directly connected to Chatlayer can be shown separately

### Language

Analytics for every bot language can be shown separately.

### Call

A call is every time a user triggers a certain intent. The total number of calls per intent is the amount of times a specific intent was triggered during a given time range.

### Timestamp

The timestamp of the data you see in the analytics dashboards is based on the timezone of your browser.

