# NLP threshold

Both the intent recognition model, as well as the entity extraction model, are based on probabilistic approaches. That means the models are almost never 100% sure of an expression. Instead, they assign probability scores to each output. Depending on your application and the available training data, you might want to decrease or increase this threshold.

Setting a threshold **too high** will result in very few user messages getting assigned the proper intent. Your customers will receive a lot of "I did not understand that" messages \(which you can configure in the 'not understood' bot dialog\). Do keep in mind that a high threshold will give more accurate bot answers to the user's input, if your expressions are plenty and varied.

Setting a threshold **too low** will make the bot act more confident, but potentially more wrong too. A low threshold increases the chances of a wrong link between an expression and an intent.

### An example

Consider the following three expressions and scores:

* I want to book a train ticket \(93% confidence for the intent 'Book train ticket'\)
* I need to be in Brussels tomorrow \(79% confidence for 'Book train ticket'\)
* I lost something and still have my train ticket \(66% confidence for 'Book train ticket'\)

In this example, the appropriate threshold would have been higher than 63%, but lower than 79%.

A threshold of 80% or higher wouldn't recognize the expression "I need to be in Brussels tomorrow" and miss it. The user would receive a reply "I am sorry, but I did not understand that," which is annoying for them.

A threshold of 65% or lower would result in the expression "I lost something \(...\)" to be incorrectly recognized as "Book train ticket". The user would receive a weird reply like "Where do you need to be?" which doesn't fit the user's intent.

{% hint style="info" %}
In most cases, we recommend an 80% threshold as a starting point for both intents and entities.
{% endhint %}

![](../../.gitbook/assets/image%20%28197%29.png)

