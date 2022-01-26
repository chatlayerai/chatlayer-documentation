---
description: The NLP threshold defines the level of which user information is understood
---

# NLP threshold

For each user message, our NLP model will check the [confidence score ](https://docs.chatlayer.ai/understanding-users/natural-language-processing-nlp)of that message and how close it's related to an existing expression. If the confidence score is above the threshold, the corresponding bot dialog will be triggered. If it's below the threshold, the 'not understood' bot dialog will be triggered.

If you set the NLP threshold **rather high (> 80%),** very few user messages will be recognised correctly, so your users will often get a 'not understood' message. So when can you put the NLP threshold higher to make sure more accurate bot answers are given? When the bot's expressions are plenty and varied.

Setting a threshold **too low (<70%)** will make the bot act more confidently at the start, but also increases the chances of a wrong intent recognition. Keep the threshold low when your bot is still small to avoid too many 'not understood' messages.

## Threshold recommendations

In most cases, we recommend an NLP threshold of around 80%  as a good starting point for both intents and entities. However, for beginning bots with a small(er) NLP model, lowering the threshold could help more expressions being successfully recognised. A threshold of 70% to 75% for both entities and intents could work at the early stages of a chatbot, until its NLP model develops more.

## Changing the threshold settings

The NLP threshold can be accessed in the NLP menu on the left hand side, under 'NLP Settings'

![](<../../.gitbook/assets/image (197).png>)

## Intent threshold

The intent threshold defines the accuracy level with which intents are recognised.

Have a look at the following three expressions and their confidence scores:

* I want to book a train ticket (93% confidence for the intent 'Book train ticket')
* I need to be in Brussels tomorrow (79% confidence for 'Book train ticket')
* I lost something but still have my train ticket (66% confidence for 'Book train ticket')

In this example, the correct threshold should be higher than 63%, but lower than 79%.

A threshold of 80% (or higher) wouldn't allow the bot to recognise the expression "I need to be in Brussels tomorrow" correctly. The user would receive a 'not understood' message, which we want to avoid of course.&#x20;

A threshold of 65% (or lower) would result in the expression "I lost something (...)" to be incorrectly linked to the intent "Book train ticket" so the matching bot dialog would be triggered. So when the user says, "I lost something but still have my train ticket" the bot would reply "Where do you need to be?" which wouldn't fit the user's goal (= intent).



## Entity threshold

![An example where the entity 'London' is recognised with 74.55%](<../../.gitbook/assets/image (684) (2).png>)

The entity threshold defines with what level the entity will be processed correctly. In the example above, the intent 'Book train ticket' gets a confidence score of 97.82%, which is why the correct response "_So I have a request for a train ticket"_ is shown. However, 'London' is recognised with 74.55% confidence, so below the entity threshold of 80%, which is why 'London' is not successfully saved and the bot asks again where the user would like to travel to.
