# How to NLP

Chatbots are automated computer programs that act like human support agents chatting on e.g. Facebook Messenger. They 'understand' what users say and react accordingly. The Natural Language Processing \(NLP\) engine of a chatbot is the underlying algorithm that takes care of this understanding.

Understanding language isn't easy: it takes us humans about 6 years and hundreds of examples to understand the most common 20,000 words. Computers are no different. To train an NLP engine, large amounts of example phrases are needed.

Intent recognition is the core of a smart chatbot. An intent can be understood as the speaker's 'intention': what does the user want to accomplish? In order to correctly recognise an intent, the chatbot has to learn the variety of ways of expressing a particular intent. For this to be possible, the bot is trained on a set of expressions: for each intent, it needs a sufficiently large number of expressions that convey the same message.

{% hint style="info" %}
**Example**

Intent: buy train ticket

Expressions:

* I need a train ticket
* I would like to buy a train ticket
* we need tickets to go to Brussels
* I have to go to Antwerp
{% endhint %}

The more expressions you add for an intent, and the more varied they are, the more accurately the chatbot will recognise the user’s input. The quality of the data you train your bot on is crucial for its accuracy. The interplay of several factors determines the quality of your training data: the intent structure, the expressions for each intent, and the entities.

## Intent structure <a id="Trainingdatagenerationforchatbots:bestpractices-Intentstructure"></a>

Coming up with a taxonomy of the intents that you need for your bot is no easy feat. Additionally, there is no correct way of doing it. Which intents you need depends largely on what you want your bot to do, on how you define the bot flow, and on how the users actually interact with the bot. 

There are some best practices:

1. **Think like a user**. Don't make the mistake of defining the structure of your intents based on your own needs. Think for instance of a support bot for a software company that should route user problems to the right specialised support agent. There is an agent for authentication issues, one for compatibility issues, one for feature requests, one for bug reports and one for functional issues. You define an intent structure with 5 intents, one for each type of issue. When one of these intents is recognised, the user is routed to the corresponding support agent.  When you put the bot into production, you notice that the users are rarely correctly routed or that the bot doesn't understand what they need most of the time. You check the user messages and notice that they write messages such as 'the program freezes' or 'I cannot do X or Y', instead of the 'I cannot do X because the update of your software is not backwards compatible with my operation system' you would like them to say for the routing to work well. Do not ask users to stick to a script that they are not aware of, because they won't.  
2. **Use all the information you have.**  If you already have user data, such as a database of questions that have been asked to your support desk, use it. Analyse the data to understand which questions are frequently asked and, more importantly, how they are asked. Calculate the volumes for each group of questions and prioritise. In case you have no idea how users will actually interact with the bot and what they might ask, you can start out with a simple click bot, which will allow you to gather a lot of useful information on your users' needs, permitting you to define an adequate intent structure.  
3. **Keep it simple.** Do not be afraid of starting with a bot that can only handle four of the questions that you eventually want it to handle, especially not if those four questions constitute 90% of incoming calls. You will only need four intents to build a bot that considerably improves the life of the support agents without affecting the quality of customer support, only the remaining 10% of questions will have to be handled manually. New intents can be added once you gather more user data. 
4. **Revise**. Start with a general flow and general intents, with follow-up questions to get to the details of what the user needs. This will allow you to gather the necessary data to revise your intent structure. For instance, for a telco support bot, you could start with 'problem with phone' and a 'problem with wifi' intent, with follow up questions concerning the model of the phone or the model of the modem. After a few weeks, you analyse the actual user messages, and notice that users often include the model of their phone \(eg. Samsung Galaxy S9\) in their messages before the bot explicitly asks for it, while they never use specific terms for anything related to wifi. In this case, it is a good idea to refine the 'problem with phone' intent, by splitting it up in several intents or by making use of entities to capture the phone model, avoiding that the bot asks a piece of information that the user already gave. The 'problem with wifi' general intent should be maintained, with follow-up questions to pin-point the exact problem. Keep in mind that defining a good intent structure is an iterative process.

## Expressions <a id="Trainingdatagenerationforchatbots:bestpractices-Expressions"></a>

Creating the set of expressions needed to train your bot is probably the part of the bot-creating process that takes up the most time. The accuracy of your bot stands or falls with the quality of your dataset. Spend enough time on this, and review regularly.

Make sure to take into account the following guidelines:

1. **Play Jeopardy.**  Jeopardy is a game in which an answer is provided, and the question has to be guessed. Write the expressions as if you were playing this game. If for instance you have an intent 'report problem', to which your bot will answer 'No worries, I will solve your problem in no time', think of all possible things a user could say to obtain this answer. Starting with the answer instead of with the question will help you to clearly separate the expressions for each intent. 
2. **Specific enough.**  Expressions have to be very specific to the topic. E.g. if the topic is ‘I want to change my address’, an expression like “I have a question” only confuses the model since it is not specific enough. For an intent “I forgot my password”, the expression “I forgot it” is not specific enough as it can apply to multiple contexts. Your bot will be wondering "you forgot what?". 
3. **No overlap allowed**.  Have intents that are close to each other is dramatic for the performance of model. Make sure your intents are properly aligned and do not overlap. 
4. **Avoid filler words**. Do not use intro’s and outro’s. Don’t add the expression “hello, I want to book a train ticket. Can I do that? Thanks”, just add “I want to book a train ticket” instead. Do this to ensure that the bot learns what is relevant. 
5. **Real language.** Use the language you would use when chatting with a human. Don’t write paragraphs, don’t use language that's too formal. Keep it light and natural. Make use of real user messages in case you have them. 
6. **Slang/dialect is allowed**.  Feel free to use slang words, common abbreviations \(e.g. asap instead of as soon as possible, or pq instead of parce-que \) or regional dialects. Don’t overdo it though: only stick to things the majority of people would actually use. 
7. **Like a user, not like an expert**.  Don’t assume a customer will ask for a SEPA code, they will ask for a bank account number. Write expressions that your users would actually use and avoid jargon only you understand. Crowdsourced expressions are a great way of accomplishing this. 
8. **Enough expressions**. From testing, we have found that you need at least 50 expressions to get reasonable performance. Some are easier, some are harder. If you have entities, be prepared to add 20 expressions per type of entity. Some of Chatlayer.ai's customers have 200-400 expressions per intent. Regularly look at the user data and add the expressions they provide you with to your model, which will make it more accurate over time.  
9. **Varied vocabulary**.  Capturing a wide variety of ways of saying something is from uttermost importance. Feel free to use a synonym lists \(e.g. [http://www.synonym.com/synonyms/](http://www.synonym.com/synonyms/)  or [https://www.thesaurus.com/](https://www.thesaurus.com/)\) to get ideas.  You can make use of the generator functionality in Chatlayer.ai to quickly create several expressions by simply substituting words by their synonyms. If you do, make sure to give special attention to creating a dataset with sufficient variation in the phrase structure. 
10. **Varied phrase structure**.  Some people will ask a question \(“What to do when I move?”\), other will use a declarative sentence \(“I am moving”\).  Do not create a dataset that contains the same sentence over and over with some different words in it. For instance, do not limit your dataset for intent "buy\_product" to a series of "I want to buy a book", " I want to buy a comic book", "I want to buy a dvd", I want to buy X", "I want to buy Y". If you do this, the model will overfit on the "I want to buy" portion of the expressions, with as a result that it will predict the intent "buy\_product" whenever a user inputs those words. Additionally, the bot will not be able to correctly predict this intent for sentences with a different phrase structure, such as "My son needs the most recent edition of Machine Learning for dummies". Creating a dataset with enough variation can be hard and drains you creativity. Make sure that more than one person participates in this process. More people, more ideas! 
11. **Correct spelling.**  During training, each word is mapped to a numeric representation summarising their meaning in a computer-readable format. The mappings only exist for a pre-existing vocabulary which contains the 200 000 most common words in a language. Misspelled words are not part of this vocabulary and hence cannot be mapped to an accurate numeric representation. Although the NLU engines do apply spell correction before mapping words to their representation, it is better to avoid typo's. Think for instance of the non-word _pone_: it could be corrected as _pony_ or as _phone_, which have two entirely different meanings, only one of them relevant for a telco support bot. Check the spelling of the training data to make sure that your bot learns the meanings that are relevant for your use case. 
12. **Lower case/UPPER CASE.** Users often do not use capitalisation when chatting with a bot. However, for intent classification, capitalisation is ignored, so you do not have to worry about it. Be careful: capitalisation is relevant for entity extraction \(see below\). 
13. **Punctuation.** Users often do not use punctuation when chatting with a bot. Make sure to include expressions both with and without punctuation. For instance, add questions with and without a question mark. 
14. **Accents**.  Users often do not use accents when chatting with a bot. In order for the bot to learn how to deal with this, accents are ignored in the models, so you do not have to worry about it. For instance, ‘élève’ is treated the same as ‘eleve’. 

## Entities <a id="Trainingdatagenerationforchatbots:bestpractices-Entities"></a>

Entities are words or small word groups that are particularly relevant for the bot flow. They can be names of people or organisations, cities, products, brands, companies, street names etc. 

Entities should only be used if their value is needed in the bot flow. For instance, if your bot allows for asking information about a certain product and you need to recover the name of the product to look up the necessary information in a database, you have to use entities. If your bot simply redirects to a webpage with an overview of all products, you do not need entities. 

When adding entities to your training data, take the following points into accounts:

1. **Punctuation**. Do not include any punctuation marks such as '.' or '?' in the entity. '-' is ok, as it is often part of the entity, as in 'Sint-Niklaas'. 
2. **Capitalisation.** The entity extraction models are not case sensitive. So there is no need to add both 'Brussels' and 'brussels'. 
3. **Words, not sentences**. Entities are words or small groups of words, usually noun phrases. Never mark full sentences or bigger phrases as an entity. If users often use paraphrases instead of a word, which frequently happens with technical terms, such as 'the little box that I use in order to have internet everywhere in my house' instead of 'wifi extender', consider not using entities but a separate intent. 

