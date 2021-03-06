# NLP best practices

Chatbots are automated computer programs that act like human support agents, chatting on, for example, Facebook Messenger. They 'understand' what the user is saying and react accordingly. The Natural Language Processing \(NLP\) engine of a chatbot is the underlying algorithm that enables the bot to 'understand' what's being said.

Understanding language isn't easy: it takes us humans about 6 years and hundreds of examples to understand the most common 20,000 words. And computers are not that different. To train an NLP engine, you need large amounts of example phrases.

Intent recognition is the core of a clever chatbot. An intent can be understood as the speaker's 'intention' or need: what does the user wish to accomplish? In order to correctly recognise an intent, the chatbot has to learn a variety of ways of expressing a particular intent. For this to be possible, the bot needs to be trained for a set of expressions: for each intent, it needs a sufficiently large number of expressions that convey the same message \(= intent\).

{% hint style="info" %}
**An example**

Intent: buy a train ticket

Expressions:

* I need a train ticket
* I would like to buy a train ticket
* We need tickets to go to Brussels
* I have to go to Antwerp
* I want a ticket to Ghent
{% endhint %}

The more expressions you add for one intent and the more varied they are, the more accurate the chatbot will recognise the user’s input. The quality of the data you train your bot with is crucial for this accuracy. Several factors determine the quality of your training data: the intent structure, the expressions for each intent, and the entities.

## Intent structure <a id="Trainingdatagenerationforchatbots:bestpractices-Intentstructure"></a>

Thinking of the intents that you need for your bot is not always so easy. Additionally, there is no correct way of doing it, it depends on what you want your bot to do, how you define the bot flow, and on how the user actually interacts with the bot. 

Here are some tips & tricks to create great intents:

1. **Think like a user** Don't make the mistake of defining the structure of your intents based on your own needs. Think for instance of a support bot for a software company. The goal is for the bot to route specific user problems to the correct specialised support agent. There is an agent for authentication issues, one for compatibility issues, one for feature requests, one for bug reports and one for functional issues. So you define an intent structure of 5 intents, one for each type of issue. When one of these intents is recognised, the user is routed to the corresponding support agent.   But when you put your bot into production, you notice that users are almost never routed to the right agent, or that the bot doesn't understand what the user needs. So you check your user's messages and notice that they write things like "the program freezes" or "I cannot do X or Y", instead of "I cannot do X because the update of your software is not backwards compatible with my operation system," which is what you planned for them to say for the routing to be correct. Learning: do not ask your users to stick to a strict script that they are not aware of, because they won't. It doesn't come natural to them.  So think like your user. Use their words, listen to how they phrase their problems, and use that to create your bot's messages and flow.  
2. **Use all the data you have**  If you already have some user data, like a list of questions that users have asked your support desk – use it! Analyse that data to understand which questions are frequently asked and, more importantly, how they are asked specifically. Calculate the volumes for each group of questions and prioritise them accordingly. In case you have no idea how users will actually interact with your bot and what they might ask, you can start with a simple click bot, which will allow you to gather a lot of useful information on your users' needs, allowing you to define an good intent structure afterward.  
3. **Keep it simple, Sherlock** Do not be afraid of starting with a bot that can only handle four of the 10+ questions that you eventually want it to handle, especially if those four questions make up 90% of all incoming questions. You'll only need four intents to build a bot that considerably improves the life of your support agents, without affecting the quality of customer support, which means that only the remaining 10% of questions will have to be handled manually. New intents can be added once you gather more user data, let it grow organically. 
4. **Revise** Start with a general flow and some general intents, then add follow-up questions to get a detailed understanding of what your user needs. This will allow you to gather the necessary data to revise your intent structure.   For instance, if you're building a telco support bot, you could start with two simple intents: – Problem with phone – Problem with wifi  And then add a follow-up question about the model of the phone, or the model of the modem. After a few weeks, when you analyse the actual user messages, you notice that users often already include the model of their phone \(eg. Samsung Galaxy S9\) in their messages before the bot explicitly asks for it, while they never use specific terms for anything related to wifi. In this case, it makes sense to refine the 'problem with phone' intent by splitting it up into several other intents, or by making use of entities to capture the phone model, whilst avoiding your bot asking for a piece of information that the user already gave. The 'problem with wifi' intent can stay as it is, with follow-up questions to pin-point the exact problem. Keep in mind that defining a good intent structure is an iterative process, it takes time and effort.

## Expressions <a id="Trainingdatagenerationforchatbots:bestpractices-Expressions"></a>

Creating a set of expressions needed to train your bot is probably the most time-intensive part of creating your bot. The accuracy of your bot stands or falls with the quality of your expressions. So make sure to spend some time on this, and review them regularly.

Here are some tips & tricks for creating good expressions:

1. **Play Jeopardy** Jeopardy is a game in which an answer is provided, and the question has to be guessed. So write the expressions as if you were playing this game. If for instance you have an intent 'report problem', to which your bot should answer 'No worries, I will solve your problem in no time', think of all the possible things a user could say to get this specific answer. Starting with the answer instead of the question can help you clearly separate the expressions for each intent. 
2. **Be specific enough** Expressions have to specifically match a certain intent. For example, if the intent is "I want to change my address," an expression like “I have a question” only confuses the model since it is not specific enough. For the intent “I forgot my password”, the expression “I forgot it” is not specific enough as it can apply to multiple contexts. Your bot will keep wondering "you forgot what?". 
3. **Don't allow overlap** Creating intents that are too similar to each other is dramatic for the performance of the NLP model. Make sure your intents are properly aligned and do not overlap. 
4. **Avoid filler words** Do not use intro’s and outro’s. Don’t add the expression “hello, I want to book a train ticket. Can I do that? Thanks,” Simply say “I want to book a train ticket” instead, which is short and simple. Do this to ensure that the bot learns what is relevant. 
5. **Use real language** Use words and sentences you would use when talking to a real person. Don’t use paragraphs or language that's overly formal. Keep it light and natural. Make use of real user messages in case you have them, data is knowledge. 
6. **Allow for slang and dialect** Feel free to use slang words, common abbreviations \('asap' instead of 'as soon as possible', or 'pq' instead of 'parce-que'\) and regional dialects. Don’t overdo it though: only stick to things the majority of people would actually use. 
7. **Think like a user, not like an expert** Don’t assume a customer will ask for a SEPA code, they will most likely ask for a bank account number. Create expressions that your users would actually use and avoid jargon that only you would understand. Crowdsourced expressions are a great way of accomplishing this. 
8. **Use enough expressions** We learned from lots of previous testing that you need at least 50 expressions to get a reasonable bot performance. Some are easier, some are harder. If you have entities, be prepared to add 20 expressions per type of entity. Some of our customers have between 200 and 400 expressions per intent, which results in great bot behavior. Regularly look at your user data \(if you have it\) and add the expressions your users provide you with to your model, which will make it more and more accurate over time.  
9. **Have a varied vocabulary** Capturing a wide variety of ways to say the same thing is super important. Feel free to use a list of synonyms \([http://www.synonym.com/synonyms/](http://www.synonym.com/synonyms/)  or [https://www.thesaurus.com/](https://www.thesaurus.com/)\) to get inspired.   You can also make use of the generator functionality on our platform to quickly create several expressions by simply substituting words for their synonyms. If you do, make sure to give special attention to creating a dataset with sufficient variation in the phrase structure. You don't want to repeat the same phrase over and over again, with only one word difference. 
10. **Choose a varied phrase structure** Some people will state their intent by asking a question \(“What to do when I move?”\) while others might use a declarative sentence \(“I am moving.”\)  Avoid creating a data set that contains the same sentence over and over, only with a few different words in it. For example: do not limit your dataset for the intent "buy\_product" to a series of "I want to buy a book", " I want to buy a comic book", "I want to buy a dvd", I want to buy X", "I want to buy Y". If you do this, the model will latch on to the "I want to buy" portion of the expressions and wrongly predict the intent "buy\_product" whenever a user uses those words. Additionally, the bot will not be able to correctly predict this intent for sentences with a different phrase structure, such as "My son needs the most recent edition of Yoga for dummies". Creating a data set with enough variation can be hard as it drains your creativity, so we advice to have more than one person participating in the creation process. Also account for diverse people giving input, a man might not think of the things a woman will think of because they might experience the same thing quite differently. In short: the more \(diverse\) people, the more \(creative and accurate\) phrases you'll get. 
11. **Use correct spelling** During training, each word is mapped to a numeric representation summarising their meaning in a computer-readable format. The mappings only exist for a pre-existing vocabulary which contains the 200 000 most common words in a language. Misspelled words are not part of this vocabulary and hence cannot be mapped to an accurate numeric representation. Although the NLU engines do apply spell correction before mapping words to their representation, it is better to avoid typo's. Think for instance of the non-word _pone_: it could be corrected as _pony_ or as _phone_, which have two entirely different meanings, only one of them relevant for a telco support bot. Check the spelling of the training data to make sure that your bot learns the meanings that are relevant for your case. 
12. **Lower case vs UPPER CASE** Users often do not use capitalisation when chatting with a bot. However, for intent classification, capitalisation is ignored, so you do not have to worry about it. But be careful: capitalisation is relevant for entity extraction \(see below\). 
13. **Punctuation** Users often do not use punctuation when chatting with a bot, so make sure to include expressions both with and without punctuation. For instance, add questions with and without a question mark. 
14. **Accents** Users often do not use accents when chatting with a bot. In order for the bot to learn how to deal with this, accents are ignored in our models, so don't worry about it. For instance, ‘élève’ is treated the same as ‘eleve’. 

## Entities <a id="Trainingdatagenerationforchatbots:bestpractices-Entities"></a>

Entities are words or small groups of words that are particularly relevant for your bot flow. They can be names of people or organisations, cities, products, brands, companies, street names and so on. 

{% hint style="info" %}
We recommends adding at least 30 expressions per entity, to guarantee the quality of the entity detection.
{% endhint %}

Entities should only be used if their value is needed in the bot flow. For instance, if your bot allows for asking information about a certain product and you need to recover the name of that product to look up the necessary information in a database, you can use entities. If your bot simply redirects to a web page with an overview of all products, you do not need entities. 

When adding entities to your training data, take the following things into account:

1. **Punctuation** Do not include any punctuation like '.' or '?' in your entity. '-' is ok, as it is often part of the entity, as in 'Sint-Niklaas'. 
2. **Capitalisation** The entity extraction models are not case sensitive. So there is no need to add both 'Brussels' and 'brussels'. 
3. **Words, not sentences** Entities are words or small groups of words, usually noun phrases. Never mark full sentences or bigger phrases as an entity. If users often use paraphrases instead of a word, which frequently happens with technical terms, such as 'the little box that I use in order to have internet everywhere in my house' instead of 'wifi extender', consider not using entities but a separate intent. 

