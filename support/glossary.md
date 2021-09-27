# Platform Glossary

**Artificial intelligence \(AI\)**

Artificial intelligence is an extensive field, one I couldn’t dream of covering in this article. So I’ll keep it short and simple:

AI technology makes it possible for bots to “learn” by discovering certain patterns in user data. Bots can apply these patterns to similar but different problems without needing extra training from a human. This ability gives them the “intelligence” to perform tasks, solve problems, and manage information without human intervention.

**Session**

The session is an object that stores the state of the conversation. In it, we store some internal variables by default \(like the botId, version, detected intents and entities,...\) but you can also store your own variables for use in your bot's messages and actions.

It's often referred to as "context" in other Conversational AI platforms however context is a different feature in Chatlayer as you may read [here](../understanding-users/using-context.md). 

#### Bot dialogs

A bot dialog contains a bot response, which is usually connected to an intent. There are different types of bot dialogs, each with different functionalities:

* Bot Message: Any message a bot is sending to a user. It can include text messages, buttons, quick replies, video, etc
* Go To: If you want to add rules to determine which dialog is triggered when, you can do so with a Go To dialog
* Action: Actions allow you to configure the settings of a user session, call an API, add custom code, etc
* Input Validation \(or User Input\): Use this bot dialog type to gather input from your users so the bot can store and use it later in the conversation

**Channel**

The channel is where your chatbot will operate. These days, chatbots can live on almost any channel where a two-way conversation is possible, pick one where your target audience hangs out. The channel you choose for your bot depends on where its users will most likely look for help or hangs out already. The bot-building platform I use, [Chatlayer.ai](http://chatlayer.ai/), supports Facebook Messenger, WhatsApp, Google Assistant, web widget, phone & voice, SMS, and many others!

**Chatbot**

At the most basic level, a chatbot is a computer program that simulates a human conversation \(either written or spoken\), allowing users to interact with digital devices as if they were communicating with a real person.

**Chat widget**

A chat widget is a ready-to-use, fully customizable chat window that can be added to your website — you know, that little blob at the bottom of your screen — through which users can talk to your bot.

![](https://cdn-images-1.medium.com/max/1600/1*K1tk14Vfh23HPMWjJe64Ww.png)

  
**CSS** 

Cascading Style Sheets \(CSS\) is a style sheet language used for describing the styling of a document written in a markup language such as HTML. 

**Confidence Score**

The Confidence Score indicates how certain the NLP engine is that the intent has been assigned correctly. If the intent’s matching score falls below the confidence score, the bot will trigger a fallback dialog. 

**CUX**

Conversational User Experiences are user experiences that combine chat, voice, or any other natural language-based technology to mimic a human conversation.

**Dependency parsing**

Dependency parsing is the process of splitting user sentences into their essential parts, like nouns, verbs, objects, common phrases, and punctuations. This technique helps your bot to identify phrases so it can understand what the user wants to convey.

**Entities**

Entities are little blocks of information that can be found in a user dialog, like a phone number, location, email address, and even a person’s name. When trained, the bot can recognize this relevant information from a user's input and save it for later use.

For example: in the “introduction” dialog, the bot asks for the user’s name and email address. We predefined those two pieces of information as entities \(user name, email\) so the bot can detect and store them.

Then when the conversation goes to another topic, such as “Book a meeting”, your bot will need the user’s name and email address so it can confirm the meeting via email. But instead of asking for this information again, which wouldn’t feel so natural, the bot can simply ‘remember’ because of the entities stored earlier.

{% hint style="info" %}
Chatlayer.ai offers different kinds of entities, which helps bot builders extract the right kind of user information. Read more about entities [here](https://docs.chatlayer.ai/understanding-users/natural-language-processing-nlp/synonym-entities).
{% endhint %}

**Expressions**

One and the same intent can be expressed via all sorts of expressions. For example, the intent “book a ticket” can be expressed by the user as:

* “I want to book a ticket”
* “Get me a ticket”
* “How do I book a ticket?”
* “Can you help me book a ticket”
* “I’m traveling soon and I still need a ticket”



![A few expressions for one intent](https://cdn-images-1.medium.com/max/1600/1*OXj1rYFQF2xRENc98FYFqA.png)

{% hint style="info" %}
It’s important to feed your bot a decent amount of expressions so it can train to recognize the user’s intent more easily.
{% endhint %}

**Fallback message**

A default dialog which is triggered when the bot doesn’t recognize a user’s input, or when a user doesn’t give any input.

For example:

* “I didn’t get that. Can you please repeat?”

**Flow**

Flows are kinda like folders in which you put bot dialogs that are related to the same topic. I like to group my flows per use case/intent. For example, when building a banking bot, I would define the following flows:

* Lost/stolen card
* Check balance
* Find nearest branch
* Set card limit
* …

**Human handover/offloading**

When a chatbot transfers the user to a human agent, we call this human handover or offloading**.**

**Input validation** 

An input validation dialog state can be used to get information from the bot's user. It first checks if the variable specified in the 'variable' field exists. If 'variable' has a value already, the bot will go automatically to the next bot dialog specified in the 'Next bot dialog' dropdown list. If 'variable' does not have a value, the bot will ask the question as defined in the Question section. 

**Intent**

Users have a specific goal in mind when talking to a chatbot. This goal is called an intent because it refers to the user’s intention. When building a bot, you need to link intents to specific bot flows and dialogs, so that the bot knows what to do.

A few examples of intents:

* “Can I order a pizza?”  _The user’s intent is to place an order_
* “Where is my package?”  _The user’s intent is to find their package_
* “Show me the financial news”  _The user’s intent is to retrieve a list of financial headlines_

**Introduction**

The bot introduction is a short message that welcomes the user and gets the conversation going. [A good introduction](https://tesstettelin.medium.com/creating-the-best-most-effective-chatbot-welcome-message-to-engage-your-users-from-the-start-37a80aa17c76) greets the user, introduces the bot, and informs the user of the bot’s capabilities.

![Two different kinds of introductions. One shows options, the other one asks an open question.](https://cdn-images-1.medium.com/max/1600/1*9bIK1K0yNvt2vW7COXOyIQ.png)

**JSON** 

If your bot is published on the Webhook API channel, you can use the JSON Builder action to send messages to the conversation that don't need to result in an actual message to the user. Typically, it's used to send information about the user or bot conversation to the website the bot is published on. 

**Live agent** 

A human agent that can help the user when the chatbot is no longer able to. 

**Live Chat** 

Live chat allows the user to talk to a human agent. 

**Machine learning \(ML\)**

Machine learning is a branch of AI that refers to your bot’s ability to learn from the inputs it experiences. This means your bot is able to pull bits and pieces from previous user interactions and use them to come up with answers to future questions. These questions are part of sentence structures stated by the user that the bot was never explicitly programmed to answer.

**Multimodal experience**

Voice is great for getting quick answers to simple questions, whilst visuals are great for more complex tasks. Combine the two and you have a multimodal experience, like the Google Nest Hub.

![The Google Nest Hub combines both sonic and visual information](https://cdn-images-1.medium.com/max/1600/0*ndT8DmIz2zlS1IOR)

**Natural Language Generation \(NLG\)**

Natural-language generation \(NLG\) is a software process that transforms structured data into natural language. For example, a written weather report can automatically be generated based on some input information, like the temperature.

**Natural Language Processing \(NLP\)**

Natural Language Processing is a branch of AI that helps computers to interpret human language and understand what’s being said. It is typically split into Natural Language Understanding and Natural Language Generation.

**Natural Language Understanding \(NLU\)**

NLU is more specific in its purpose. It helps a computer to understand what a body of text really means because if it doesn’t understand the content, it cannot process it accordingly.

Some real-world examples of NLU are: issuing short commands based on comprehending text, like rerouting an email to the right person based on a basic syntax. Much more complex applications can fully comprehend news articles or shades of meaning within poetry or novels.

It’s best to view NLU as a first step towards achieving NLP: before a machine can process a language, it must understand what’s being said.

**Production & staging** 

Our platform provides 2 environments: staging and production, to support working in parallel on a new version of your chatbot without interfering with your production version which is talking to your users in real-time. You have access to both environments. 

* Staging \('Draft'\) = Used to build and test new bot versions and improve your NLP model
* Production \('Live'\) = The production chatbot that is already communicating with your users
* We recommend not changing data and configuration \(flows, NLP, settings\) directly in your production environment as this can break your live bot. 

Once your bot is ready and tested in the staging environment, it's time to publish your bot to the production environment. 

**REST** 

Chatlayer.ai provides a REST JSON API to retrieve, create and manipulate data from third**-**party applications and a webhook configuration to notify you when a variety of interactions or events happen, including when a bot sends a message. Webhook events are sent by Chatlayer.ai as POST requests to your webhook. 

**SDK / iFrame**

There are usually two ways of integrating a chat widget on your website: you can use either iframe or SDK. 

If you want to get the chat widget onto your website with minimal custom development, it’s best to use an SDK. If you want more control over certain elements, such as the chat button, it’s best you use an iFrame. 

**SSML**

[Speech Synthesis Markup Language](https://developers.google.com/assistant/conversational/df-asdk/ssml) \(SSML\) is part of TTS and allows you to change your bot’s voice responses to make them sound more natural. For example, you can add pauses, sound clips, and other nice speech effects.

**STT**

Speech to Text converts spoken words into text. This way, your voice bot can understand and process what a user is saying, and trigger the correct flow.

**Token** 

Each API request requires authentication to identify the user that is responsible for making the request. Authentication is provided by \(access\) tokens. 

**TTS**

Text to Speech is a technology that converts written text to spoken words. So once your voice bot has understood the user and found the corresponding flow, it can talk to the user. TTS is pretty cool because it can bring your bot to a whole new level: it gives it a voice, and more importantly, a personality.

![A basic overview of how a voice bot interprets the user and forms a reply](https://cdn-images-1.medium.com/max/1600/1*RlxpEWZfBcDL_40zZsafdw.png)

**Utterance**

Anything the user says to the bot. For example, when a user states “I’d like to order a pizza please”, the entire sentence is the utterance. Fun fact: [even a simple sigh can be understood as an utterance](https://tesstettelin.medium.com/is-a-sigh-just-a-sigh-the-ai-answer-is-no-cdb56f24597e?source=your_stories_page-------------------------------------).

**Value**

A value is a possible element of a variable. For example, the variable ‘destination’ can have the following values: Antwerp, London, Brussels, … Variables and values always appear together.

**Variables**

An entity that was successfully recognized by the NLP engine will be stored as a variable. For example, say you created the entity ‘Levels’ with values ‘Beginner’, ‘Intermediate’ and ‘Expert’. When a user says ‘I think I’m an expert’, the value ‘expert’ will be saved as a variable so it can be used later when, for example, the user wants to upgrade his account and the bot needs to know his current level.

**Voicebot**

These bots allow its users to interact with them simply by speaking. They’re also called voice assistants, you know, like Alexa, Siri, or Ok Google. Both their input and output is voice.

**Webhook** 

Our platform contains the following features: 

* A Webhook message API endpoint to send a user message to the bot
* A Webhook configuration to be notified when bot messages are returned as a response to user messages sent to the webhook message API as described in this section. This API is almost real-time and the purpose is to be able to trigger event-based behavior as soon as a bot message response occurs. This way you will be able to integrate the bot flow logic in your own application or message channel. 

The overall mechanism is loosely based on Pubsub protocol and relies on HTTP request containing the bot message response being sent to a consumer Endpoint URL. The customer webhook Endpoint URL can be configured on our platform as described in this section. 

**White listing \(Regex\)**

The White List allows you to configure your Chat Widget to only display on a website that you’ve allowed. To do so, you can write a Regex containing the allowed domains. This is an extra security measure to prevent third parties from including your Chatbot on their websites. 

