---
description: >-
  Starting to build your own bot on Chatlayer? Great choice! Here are some best
  practices to keep in mind while building your bot
---

# Bot-building best practices

When building your bot on Chatlayer, you would like to create it in such a way that the bot is well maintained and easy to work with as a bot-builder. This article gives you some best practice concepts to create the best bot possible!

## Future proof

Try to build a future proof bot. This means, that the bot should be build in such a way that it is easy to build on top of the current logic and the bot can easily be expanded in the coming years.

Try to think which use cases may be build in the future, or any added functionalities that may be added. If the current set-up of the bot supports this, it will save time in the future to add new features.&#x20;

![An example of future proof bot building, this makes it easy to add other languages in the future. ](<../../.gitbook/assets/image (718).png>)



## Maintainable

Ensure that the maintainability of the bot stays high. A few tips on how to do this:

* Reuse bot dialogs as much as possible. Do not create similar bot dialogs, but try to reuse them and use the same bot dialog in multiple flow. Let's say you have a bot dialog explaining the different use cases of the bot to the user. You would show this multiple times, for example if the user asks 'How can you help me?' but also after completing a flow. If in the future you would need to change a topic, you would only have to do this once instead of multiple times.

![An example how the same bot dialog is reused at the end of different flows with different variables](<../../.gitbook/assets/image (711).png>)

* Next to reusing bot dialogs, try to reuse information and variables as well. If you already asked the name of the user in the beginning of the conversation, this will be remembered through the entire conversation. If you would ask this again later, this makes the bot look 'dumb' to the user and adds more bot dialogs. Be critical in which information is needed to ask and which information can be reused.
* Give clear names to bot dialogs, intents and variables. That way it gives a very clear overview what exactly that item does, and makes it easy for a colleague to help with the bot too.
* Use as few bot dialogs as possible. When your bot grows to 300+ bot dialogs, it can make a big difference if you have saved some bot dialogs in the beginning stages of the bot. &#x20;

## Dynamic

Try to keep the bot as dynamic as possible. That means, the bot should be resilient to change. For example, avoid hardcoding any information or variables in the bot. Retrieve information as much as possible from the user or from an external system, to keep one source of truth. Whenever something then changes in your organisation, you would only have to change it in your external system and not in both that system and in Chatlayer, saving time.

![An example of a non-dynamic bot with hardcoded values. Instead, create an intent or entity to cover all possible spellings.](<../../.gitbook/assets/image (685).png>)

## Consistency

Aim for a consistent bot. Do this by building similar flows in the same way. This creates a better overview when the bot builder opens the flows page, and makes debugging a lot easier. Next to that, some bigger bots can have hundreds of bot dialogs and many variables. If you create a clear consistent naming from the start, this makes more the more consistent and maintainable in the future.&#x20;

## Edge cases

Account for non-happy flows and edge cases, as described [here](https://docs.chatlayer.ai/tutorials/getting-started#06e9). If a user responds differently than expected, your bot should be able to accommodate that.  Try to create good ['not understood' messages](https://docs.chatlayer.ai/tips-and-best-practices/not-understood-bot-dialog) and test the bot thoroughly to account for all use cases and questions the user might ask.&#x20;

## Flows

To create best practice flows, take a look at the tips below:

* Avoid 'red' bot dialogs. Bot dialogs turn red when they are empty, and this can lead to unexpected behaviour. When your bot dialog is  red, either fill in a text message, delete it or change the type.

![An example of a 'red' bot dialog](<../../.gitbook/assets/image (684).png>)

* For action dialogs, try to limit API calls to < 20 seconds to increase performance and prevent timeouts
* In input validations, always fill in the 'When user response is not valid the first 2 or 3 times, bot asks question' section. For example, if the input validation is expecting a date, but the user is not given a date as an answer, these texts will be triggered. If they are empty, the bot will not give a response and the flow will stop.&#x20;

![](<../../.gitbook/assets/image (703).png>)



If you have any other questions, do not hesitate to [contact us,](https://docs.chatlayer.ai/support/get-in-touch) we're happy to help!
