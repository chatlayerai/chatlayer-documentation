---
description: >-
  Throughout our analytics, we use several key terms. Here are some important
  terms explained in more detail.
---

# Definitions

### Definition of a conversation

A conversation starts when a first message is sent. This message can be sent by the user, or by the bot.&#x20;

{% hint style="info" %}
For the counting of conversations shown in analytics or billing, 15 mins of silence or no interaction between a user and a bot closes the conversation and automatically starts a new one.
{% endhint %}

You can try out your bot in the "test your bot" window on the bottom right of the platform. These conversations are not counted in your analytics or towards your billing.

In the **analytics dashboard** you can toggle between viewing the results of your DRAFT or your LIVE conversations (learn more about DRAFT and LIVE [here](../publishing-your-bot/)). In **billing**, both DRAFT and LIVE conversations are counted and shown.

Every channel is a different conversation. If the same user talks to your bot on multiple channels, all of these conversations will be counted as separate conversations in both billing and analytics.

### Definition of a user

A user is anyone who sends at least one message to the bot.&#x20;

If you're on an asynchronous channel like Facebook or WhatsApp, a user will be identified as the same user throughout their entire conversation history with the bot. This means that every Facebook user talking to the bot will only be counted as one user in the analytics.

If your bot lives on a web widget or custom implementation, by default a user will be counted as a new user every time they refresh the web page and start talking to the bot again. However, some clients configure their web widgets in a way that recognizes a returning user through a Sender ID. This way, returning users are only counted as one user.

### Definition of a returning user

Users that have a conversation during and before the selected time range in the analytics dashboards are counted as a returning user.

If a user had multiple conversations during the selected time range, but no conversations before that range, they will not be counted as a returning user.

### Definition of a user Message

A user message is every interaction from the user with the bot. This can be a typed expression, but also a button click, a file upload, etc.

### Definition of a 'Not understood' message

A message is not understood if it's an expression that is not a match with one of the trained expressions, or the NLP confidence score of this expression is below the defined [NLP threshold](../../understanding-users/natural-language-processing-nlp/settings.md).

### Definition of a button click

Some messages will consist of the user clicking a button. This button can appear in a Button template, Quick Replies, Carousel, List, ...

### Definition of a channel

Analytics for every channel directly connected to Chatlayer can be viewed separately.

### Definition of language

Analytics for every bot language can be viewed separately.

### Definition of a call

A call is every time a user triggers a specific intent. The total number of calls per intent is the amount of times this specific intent was triggered during a given time range.

### Definition of a timestamp

The timestamp of the data you see in the analytics dashboards is based on the timezone of your browser.
