# NLP threshold

Both the intent recognition model as well as the entity extraction model are based on probabilistic approaches. That means the models are almost never 100% sure about an expression. Instead, they assign probabilities scores to the output. Depending on your application and available training data, you might want to decrease or increase this threshold.

Setting a threshold too high will result in very few user messages getting assigned the proper intent. Your customers will receive a lot if 'I did not understand that' messages \(configured in the 'not understood' bot dialog\). On the other hand, you will be more certain that the answer from the bot really belongs to the users input.

Setting a threshold too low will make the bot act more confident. This increases the chances of a wrong link between an expression and an intent.

### Example

Consider for example the following three expressions and scores

* I want to book a train ticket \(93% confidence for intent 'Book train ticket'\)
* I need to be in Brussels tomorrow \(79% confidence for 'Book train ticket'\)
* I lost something and still have my train ticket \(66% confidence for 'Book train ticket'\)

In this example, the appropriate threshold would have been higher than 63% but lower than 79%.

A threshold of 80% or higher would result in the 'I need to be in Brussels tomorrow' expression to be incorrectly missed. The user would receive a reply "I am sorry but I did not understand that". This is annoying for the user.

A threshold of 65% or lower would result in the expression 'I lost something \(...\)' to be incorrectly classified as 'Book train ticket'. The user would receive a weird reply like for example "where do you need to be?"

{% hint style="info" %}
In most cases Chatlayer.ai recommends a threshold for both intents and entities of 80% as a starting point.
{% endhint %}

![](../../.gitbook/assets/image%20%28197%29.png)

