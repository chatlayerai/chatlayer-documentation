# NLP best practices

Voice and chatbots are virtual programs that can understand and reply to what a user is saying, thanks to their Natural Language Processing (NLP) engine.

Understanding language isn't easy: it takes us humans about 6 years and hundreds of examples to understand the most common 20,000 words. Computers are not that different; to train an NLP engine, you need huge amounts of data and example phrases.

Accurate intent recognition lies at the core of any clever bot. FYI, an intent reflects the user's goal or 'intention': what is the user trying to accomplish through this bot? For the bot to be able to correctly recognise an intent, it needs to learn all the ways a user could express their particular intent. How does the bot learn? By getting fed user expressions which it then uses to train on. For every intent, the bot needs a large number of expressions that convey the same intent

{% hint style="info" %}
**An example**

Intent: Buy a train ticket

Expressions:

* I need a train ticket
* I would like to buy a train ticket
* We need tickets to go to Brussels
* I have to go to Antwerp
* Can I get a ticket to Ghent?
* Help me book some train tickets
* ...
{% endhint %}

The more expressions you add to the bot and the more diverse they are, the more accurate your bot will recognise the user’s input. The quality of the expressions you train your bot on is crucial for its accuracy. Several factors determine the quality of this training data: the intent structure, the quality of expressions for each intent, and possible entities.

## Creating intents <a href="#trainingdatagenerationforchatbots-bestpractices-intentstructure" id="trainingdatagenerationforchatbots-bestpractices-intentstructure"></a>

Finding the right intents to add to your bot isn't always so easy. So let us help you get started! Here are some tips & tricks to create great intents:

1. **Use the data you already have** \
   If you already have some customer data available, like a list of frequently asked questions that your support desk handles daily – use it! Analyse this data to understand which questions are most important and asked most, so your bot can handle these. You can calculate the volume for each question and prioritise them accordingly. \
   \
   No idea what your users want to get out of your bot? Start with a simple click-bot, so you can gather useful information on your users' needs. Use that info to define good intents afterward. \

2. **Keep it simple, Sherlock**\
   Don't be afraid of starting small. If the first version of your bot can only handle 5 of the 15 questions you eventually want it to handle, that's totally fine, especially if those 5 questions make up 80% of all incoming questions. You can already improve your customer support service significantly using a small bot with 5 intents, handling 70% to 80% of all requests, so your team of human agents can focus on the remaining 30% to 20% of requests. New intents can always be added later, when you've gathered more user data, so let your bot grow organically.\
   \
   Keep in mind: it's better to start small and do it right, then trying to do everything at once and do it wrong.\

3. **Revise, revise, optimise**\
   Start with a general intent which triggers a general flow, then add some follow-up questions to get a detailed understanding of what your user needs exactly. This approach will allow you to gather the necessary data to revise your intents afterward. \
   \
   For example, if you're building a telco support bot, you could start with two simple intents: \
   1\. Problem with phone\
   2\. Problem with wifi\
   \
   The first intent catches all issues related to phones, which of course, can be very diverse. Is it a problem with the battery? The screen? The software? A lost order? The same goes for the second intent. To figure out what the actual problem is, you can add a few follow-up questions about the model of the phone, or the model of the modem. After a few weeks, when you analyse the real user messages, you notice that users often already include the model of their phone (eg. Samsung Galaxy S9) in their messages before the bot explicitly asks for it, while they never use specific terms for anything related to wifi. \
   \
   In this case, it makes sense to split up the intent 'problem with phone' by creating several other intents, or by using entities to capture the phone model straight away. The intent 'problem with wifi' can stay as it is, with follow-up questions to pin-point the exact problem. Keep in mind that creating intents is an ongoing process, which takes time and effort. \


When two (or more) intents are very similar in meaning and/or use case, you should merge them to avoid confusing the NLP engine. For example, you've built a bot that can help a user book train tickets. after a while, you would also like to offer bus tickets. You could create an extra intent for booking bus tickets, but the expressions would be too similar to the one for booking train tickets. Only the mode of transportation is different. In this case, it's better to create only one intent, 'booking tickets', and use an [entity](https://docs.chatlayer.ai/understanding-users/natural-language-processing-nlp/synonym-entities) to recognise the transportation mode.

{% hint style="info" %}
It’s important to have about the same number of expressions per intent to make sure that the bot doesn't train more on intens with a large expression count, ignoring the ones with a less expressions.
{% endhint %}

## Creating expressions <a href="#trainingdatagenerationforchatbots-bestpractices-expressions" id="trainingdatagenerationforchatbots-bestpractices-expressions"></a>

Creating a good set of expressions is key to create a smart bot. The accuracy of your bot stands or falls with the quality of your expressions, so make sure to spend enough time on this, as well as reviewing them regularly.

Here are some tips & tricks for creating good expressions:

1.  **Use real live data**

    Chances are there are already a lot of user expressions which you can feed to your bot. Think customer support logs, social media posts, comments on your company's forum etc.
2. **Use pre-built intents**\
   ****No need to reinvent the wheel when you can download the wheel directly on the Chatlayer platform! We have a lot of pre-built intents ready for you to use. Simply download them, train the NLP, and you're good to go!
3. **Be specific**\
   Expressions have to match a specific intent, so your expressions have to specific too. For example, if the intent is "change address," an expression like “I have a question” will only confuse the bot since it is not specific enough. A question about what? For the intent “Forgot password”, the expression “I forgot it” is not specific enough as it can apply to multiple things a user could forget. So be specific.
4. **Avoid filler words**\
   Avoid adding the expression “hello, I want to book a train ticket. Can you help me with that? Thanks” because this sentence contains too many irrelevant words. Simply use “I want to book a train ticket” which is shorter and more relevant.
5. **Use real language**\
   Add words and sentences to your bot which a real person would use in this conversation. Don’t use entire paragraphs or language which is overly formal. Keep it light and natural instead. Make use of real user messages in case you have them; data is knowledge.
6. **Allow for slang and dialect**\
   Feel free to use slang words, common abbreviations ('asap' instead of 'as soon as possible', or 'pq' instead of 'parce-que') and regional dialects. Don’t overdo it though: only stick to things the majority of people would actually use.
7. **Create enough expressions**\
   We learned from lots of previous testing that you need at least 40 to 50 expressions to get a reasonable bot performance. Some of our customers added 200 to 400 expressions per intent, which results in excellent bot behaviour. Regularly check your user data (if you have it) and add the expressions your users provided you with to your model, which will make the model more and more accurate over time.&#x20;
8. **Have a varied vocabulary**\
   Capturing a wide variety of ways of saying the same thing is super important. Feel free to use a list of synonyms ([http://www.synonym.com/synonyms/](http://www.synonym.com/synonyms/)  or [https://www.thesaurus.com/](https://www.thesaurus.com)) to get inspired. \
   \
   You can also make use of the generator functionality on our platform to quickly create several expressions by simply substituting words for their synonyms. If you do so, make sure to pay special attention to creating a dataset with sufficient variation in the phrase structure. You don't want to repeat the same phrase over and over again, with only one word difference.
9. **Choose a varied phrase structure**\
   Some people will state their intent by asking a question (“What to do when I move?”) while others might use a declarative sentence (“I am moving.”)  Avoid creating a data set that contains the same sentence over and over with only a few different words in it. For example: do not limit your dataset for the intent "buy\_product" to a series of "I want to buy a book", " I want to buy a comic book", "I want to buy a dvd", I want to buy X", "I want to buy Y". If you do this, the model will latch on to the "I want to buy" portion of the expressions and wrongly predict the intent "buy\_product" whenever a user uses those words. Additionally, the bot will not be able to correctly predict this intent for sentences with a different phrase structure, such as "My son needs the most recent edition of Yoga for dummies". Creating a data set with enough variation can be hard as it drains your creativity, so we advice to have more than one person participating in the creation process. Also account for a diverse array of people giving input; a man might not think of things a woman will think of because they might experience something differently. In short: the more (diverse) people, the more (creative and accurate) phrases you'll get.
10. **Use correct spelling**\
    During training, each word is mapped to a numeric representation summarising their meaning in a computer-readable format. The mappings only exist for a pre-existing vocabulary which contains the 200 000 most common words in a language. Misspelled words are not part of this vocabulary and hence cannot be mapped to an accurate numeric representation. Although the NLU engines do apply spell correction before mapping words to their representation, it is better to avoid typo's. Think for instance of the non-word, _pone_: it could be corrected as _pony_ or as _phone_, which are two entirely different meanings, only one of them is relevant for a telco support bot. Check the spelling of the training data to make sure that your bot learns the meaning of words relevant for your use-case.
11. **Lower case vs UPPER CASE**\
    ****Users often do not use capitalisation when chatting with a bot. However, for intent classification, capitalisation is ignored, so you do not have to worry about it. But be careful: capitalisation is relevant for entity extraction (see below).
12. **No need for punctuation (or accents)**

    Punctuation and accents are ignored by our NLP, so don't worry about adding them. For instance, ‘élève’ is treated the same as ‘eleve’. &#x20;

## Entities <a href="#trainingdatagenerationforchatbots-bestpractices-entities" id="trainingdatagenerationforchatbots-bestpractices-entities"></a>

Entities are a word or small number of words that are particularly relevant for your bot flow. They can be names of people or organisations, cities, products, brands, companies, street names and so on.&#x20;

{% hint style="info" %}
We recommends adding at least 30 expressions per entity, to guarantee the quality of the entity detection.
{% endhint %}

Entities should only be used if their value is needed in the bot flow. For instance, if your bot allows for asking information about a certain product and you need to recover the name of that product to look up the necessary information in a database, you can use entities. If your bot simply redirects to a web page with an overview of all products, you do not need entities.&#x20;

When adding entities to your training data, take the following things into account:

1. **Punctuation**\
   Do not include any punctuation like '.' or '?' in your entity. '-' is ok, as it is often part of the entity, as in 'Sint-Niklaas'.\

2. **Capitalisation**\
   ****The entity extraction models are not case sensitive. So there is no need to add both 'Brussels' and 'brussels'.\

3. **Words, not sentences**\
   Entities are a word or small number of words, usually noun phrases. Never mark full sentences or bigger phrases as an entity. In case users often use paraphrases instead of a word, which frequently happens with more technical terms, such as 'the little box that I use in order to have internet everywhere in my house' instead of 'wifi extender', consider not using entities but a separate intent.&#x20;
