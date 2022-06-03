# Bot-building best practices

Ready to build your own bot on Chatlayer? Great choice! Here are some best practices for creating a great user experience.

## Make it maintainable

1. Reuse bot dialogs as much as possible. Do not create similar bot dialogs, but just reuse the same one in multiple flows. For example, if you have a bot dialog explaining what the bot can do for its users, you will probably show this a couple of times, like when the user asks 'how can you help me?' but also at the start of the conversation. Simply use the same dialog:&#x20;

![An example how the same bot dialog is reused at the end of different flows with different variables](<../../.gitbook/assets/image (711) (1).png>)

* Next to reusing bot dialogs, try to reuse information and variables as well. If you already asked the name of the user in the beginning of the conversation, this will be remembered throughout the entire conversation. If your bot would keep asking for the same information, it makes the bot look 'dumb'. Ask once, remember always.
* Give clear titles to bot dialogs, intents, and variables. This helps other people working on the bot to make quick changes.

### Dynamic

Try to keep the bot as dynamic as possible, so it's resilient to change. For example, avoid hardcoding any information or variables in the bot but instead, pull needed information from an external database, to keep one source of truth. This way, whenever something changes in your organisation, you only need to change it in the database not in your bot dialogs as well.&#x20;

![An example of a non-dynamic bot with hardcoded values. Instead, create an intent or entity to cover all possible spellings.](<../../.gitbook/assets/image (685) (1).png>)

## Edge cases

Make sure your bot can handle [edge cases](https://docs.chatlayer.ai/tutorials/getting-started#06e9). If a user responds differently than expected, your bot should be able to handle this. Try to create a good ['not understood' message](https://docs.chatlayer.ai/tips-and-best-practices/not-understood-bot-dialog) and test the bot thoroughly before publishing it, to include all use cases and questions a user might ask.&#x20;

## Flows

* Avoid 'red' bot dialogs. Bot dialogs turn red when they are empty, which can lead to errors. When your bot dialog is red, either fill in a text message, delete it, or change the type.

![An example of a 'red' bot dialog](<../../.gitbook/assets/image (684) (1).png>)

* For action dialogs, try to limit API calls to less than 20 seconds to increase bot performance and prevent timeouts
* In an input validation dialog, always fill in the 'When user response is not valid the first 2 or 3 times, bot asks question' section. For example, if the input validation is expecting a date, but the user is not given a date as an answer, these error texts will be triggered. If they are empty, the bot will not give a response and the flow will simply stop.&#x20;

![](<../../.gitbook/assets/image (703) (1).png>)

If you have any other questions, do not hesitate to [contact us,](https://docs.chatlayer.ai/support/get-in-touch) we're happy to help!
