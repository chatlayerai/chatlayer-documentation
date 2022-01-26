---
description: The NLP threshold defines the level of which user information is understood
---

# NLP threshold

With every user message, our NLP model will check the [confidence score ](https://docs.chatlayer.ai/understanding-users/natural-language-processing-nlp)of that user message and how close it is to any existing expressions. If the confidence score is above the threshold, the corresponding intent and bot dialog is triggered. Below the threshold, the 'not understood' bot dialog is triggered.

Setting a threshold **too high** will result in very few user messages getting assigned the proper intent. Your customers will receive a lot of "I did not understand that" messages (which you can configure in the 'not understood' bot dialog). Do keep in mind that a high threshold will give more accurate bot answers to the user's input, if your expressions are plenty and varied.

Setting a threshold **too low** will make the bot act more confidently, but increases the chances of a wrong link being made between an expression and intent.

## Settings

The NLP threshold can be found in the NLP menu on the left hand side > NLP Settings.&#x20;



![](<../../.gitbook/assets/image (197).png>)

## Intent threshold

The intent threshold defines the level of which intents are recognized and their corresponding bot dialog is triggered.

Consider the following three expressions and scores:

* I want to book a train ticket (93% confidence for the intent 'Book train ticket')
* I need to be in Brussels tomorrow (79% confidence for 'Book train ticket')
* I lost something and still have my train ticket (66% confidence for 'Book train ticket')

In this example, the appropriate threshold would have been higher than 63%, but lower than 79%.

A threshold of 80% or higher wouldn't recognize the expression "I need to be in Brussels tomorrow" and miss it. The user would receive a reply "I am sorry, but I did not understand that," which is annoying.

A threshold of 65% or lower would result in the expression "I lost something (...)" to be incorrectly recognized as "Book train ticket". The user would receive a weird reply like "Where do you need to be?" which wouldn't fit the user's intent.



## Entity threshold

![An example where the entity 'London' is recognized with 74.55%](<../../.gitbook/assets/image (684) (2).png>)

The entity threshold defines at which level the entity will be correctly processed. In this example above, the 'book train intent' is recognized with 97.82%, and that's why the correct response _'So I have a request for a train ticket'_ is triggered. However, 'London' is recognized with 74.55%, which is below the entity threshold of 80%. Therefore London is not successfully saved and the bot asks again where the user would like to travel to.

## Recommendations

In most cases, we recommend an 80% threshold as a starting point for both intents and entities. However, for beginning bots with a small NLP model, a lower score could ensure that more sentences are successfully recognized. A 70% or 75% threshold for both entities and intents could work in the beginning stages until the NLP model grows.
