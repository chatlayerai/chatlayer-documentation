# Sentiment analysis

The Chatlayer NLP engine allows you to analyse the sentiment in the message of a user. You can use this sentiment to customise the flow of your bot.

If you want to try out sentiment analysis, go the the "Test" menu under "NLP" and try out a few expressions.

![](<../../.gitbook/assets/image (678) (1).png>)

![](<../../.gitbook/assets/image (677) (1) (1).png>)

Chatlayer returns 3 different types of sentiments:

* Positive
* Neutral
* Negative

{% hint style="warning" %}
Sentiment analysis is currently in beta. If you'd like to try it out, [get in touch](../../support/get-in-touch.md) with us.
{% endhint %}

If you want to enable sentiment analysis for your bot, go to the "NLP settings" menu and active the "Sentiment Analysis" toggle

![Sentiment analysis settings in NLP settings](<../../.gitbook/assets/image (674) (1).png>)

As soon as you activate Sentiment analysis, all user messages will be analyzed for sentiment. You can find the result of that analysis in the `internal.nlp.sentiment` variable in the user session.

The `internal.nlp.sentiment` object consists of two key-value pairs:

* `internal.nlp.sentiment.name`: the type of sentiment - positive / neutral / negative
* `internal.nlp.sentiment.score`: the score of the sentiment type, ranging from 0 to 1

You can use these key-value pairs in [Go To's](../../bot-answers/dialog-state/plugins.md) to route your flows.
