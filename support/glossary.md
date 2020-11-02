# Glossary

#### **Chatbot** 

Chatbots – also known as “conversational agents” – are software applications that mimic written or spoken human speech for the purposes of simulating a conversation or interaction with a real person. 

#### **Voicebot** 

Voicebots are chatbots where the mode of interaction or channel is voice. They use voice technology to be able to interact with a chatbot. Voicebots are for example deployed in call centers to automatically route the customer to the right agent \(Smart IVR\) or to answer questions of customers calling, automatically. 

#### **Smart IVR**  

Smart IVR is software powered by artificial intelligence \(AI\) that allow a caller to use an interactive voice response \(IVR\) system with their voice, generally using natural language. Callers don't have to listen to menus and press corresponding numbers on their keypads. 

#### Voice technology 

Voice technology allows you to use a chatbot with your voice. For example, by talking to a digital assistant on your phone or in your home. It uses speech recognition \(STT\) to turn spoken language into text so that it can be understood by the computer. Next this text is used by a chatbot to return an answer. This answer is spoken using Text-to-Speech \(TTS\) 

#### NLP 

Natural language processing is a branch of artificial intelligence \(AI\) that helps computers understand, interpret and manipulate human language.  It is typically split in natural language understanding \(NLU\) and natural-language generation \(NLG\)            

#### NLG 

Natural-language generation \(NLG\) is a software process that transforms structured data into natural language. It can be used to produce long form content for organizations to automate custom reports, as well as produce custom content for a web or mobile application.  Practically, this means that text, for example a weather report, is automatically generated based on some input information, for example the temperature.        

#### CUX 

Conversational User Experiences are user experiences that combine chat, voice or any other natural language-based technology to mimic a human conversation. 

#### STT 

Speech-to-Text \(STT\) technology turns spoken text into written text. It typically uses machine learning to turn an audio signal into text. 

#### TTS 

Text-to-Speech \(TTS\) technology turns written text in naturally sounding spoken text. 

It leverages for example neural network techniques to deliver a human‑like, engaging, and personalized user experience    

#### Intent 

Intent refers to the motive of a chatbot user. It's the intention behind each message that the chatbot receives, what the user is ultimately trying to know or accomplish. 

#### Entity 

Entities can be fields, data, or text describing just about anything — a time, place, person, item, number, etc. Using NLP, chatbots can extract entities from entries that users type in in order to turn around accurate recommendations and answers. 

#### Expression 

A way of expressing a particular intent. The intent ‘book a ticket’ can be expressed as ‘I want to book a ticket’ or ‘Get me a ticket’ or ‘How do I book a ticket’ etc. 

#### Event 

Events are used to trigger a flow based on an event that happens in a certain conversation. Multiple types of events allow for widely varying use cases. 

#### Utterance 

An utterance is really anything the user will say. The utterance can be a sentence, some instances a few sentences, or just a word or a phrase.  

#### SDK or iFrame 

There are two ways of integrating the Chat Widget on your website: you can use either iframe or SDK. SDK stands for Software Development Kit.  

Our chat widget SDK is a layer on top of an iframe, which includes some other functionalities like a button that is shown before the chat window opens, with the option to close the chatbot. 

If you want to get the chat widget onto your website with minimal custom development, it's best to use an SDK. The only thing you need to do is include a HTML script tag as described below. 

If you want more control over other elements, such as the chat button, it's best to use iframe. An iframe is a custom element that can be used to show a different web page in the chat conversation. It can also be used to communicate with the parent window using the postMessage API. 

#### Bot dialogs 

There are four kinds of bot dialogs, each with its own functionalities: 

* Bot message: Any message a bot is sending to a user is what we call a bot message. This includes text messages, buttons, quick replies, etc. 
* Go to: If you want to add rules to determine where a user is guided to, based on the value of a variable, you can do it with this bot dialog type. 
* Action: Actions allow you to configure the settings of a user session, such as the language that will be used to reply to your user, or the offloading of a user. 
* Input validation: Use this bot dialog type to gather input from your users. 

Sometimes bot dialogs are sometimes also called dialog states. 

#### Flow 

You can think of flows as a folder in which you can put bot dialogs that are related to the same topic. 

#### Conversational flow 

How your dialogues are stringed together. Conversational flows show how your conversation will or can flow. 

#### API 

A computing interface which defines interactions between multiple software intermediaries. Simply put, an API sends information back and forth between a website or app and its user.  

APIs matter because your website, app or service isn’t doing anything without them. You need them to process an order and confirm payment if you are selling anything. You need them to collect data if that is the goal of your solution.  

#### Multi-lingual NLP 

A single NLP model that can handle multiple languages simultaneously. 

#### Parsing 

The process of analyzing a string of symbols, either in natural language, computer languages or data structures, conforming to the rules of a formal grammar. In practice, it comes down to extracting certain patterns from text. 

#### Web widget 

A web widget is a web application that is embedded as an element on a website and allows the user to chat with your chatbot. 

#### Variable 

Variables are used to store any information the bot knows about a user. This can be their preferred language, or the channel they're using, but also information coming from external data sources like, for example, an API. All variables are stored in what is called a user's session. 

#### JSON 

If your bot is published on the Webhook API channel, you can use the JSON Builder action to send messages to the conversation that don't need to result in an actual message to the user. Typically, it's used to send information about the user or bot conversation to the website the bot is published on. 

#### REST 

Chatlayer.ai provides a REST JSON API to retrieve, create and manipulate data from third party applications and a webhook configuration to notify you when a variety of interactions or events happen, including when a bot sends a message. Webhook events are sent by Chatlayer.ai as POST requests to your webhook. 

#### Webhook 

Our platform provides the following features: 

* a Webhook message API endpoint to send a user message to the bot 
* a Webhook configuration to be notified when bot messages are returned as response to a user messages sent to the webhook message API as described in this section. This API is almost real time and the purpose is to be able to trigger event-based behavior as soon as a bot message response occurs. This way you will be able to integrate the bot flow logic in your own application or message channel. 

The overall mechanism is loosely based on Pubsub protocol and relies on HTTP request containing the bot message response being sent to a consumer Endpoint URL. The customer webhook Endpoint URL can be configured on our platform as described in this section. 

#### Production & staging 

Our platform provides 2 environments: staging and production, to support working in parallel on a new version of your chatbot without interfering with your production version which is talking to your users in real-time. You have access to both environments. 

* Staging \('Draft'\) = Used to build and test new bot versions and improve your NLP model 
* Production \('Live'\) = The production chatbot that is already communicating with your users 
* We recommend not changing data and configuration \(flows, NLP, settings\) directly in your production environment as this can break your live bot. 

Once your bot is ready and tested in the staging environment, it's time to publish your bot to the production environment. 

#### Expression Generator 

An Expression Generator makes it easy for you to quickly generate a lot of expressions by swiftly adding synonyms for different parts of an already existing expression. 

#### Go to 

Go To enables your bot to redirect the user to a bot dialog state depending on the conditions of the session variables. 

#### Input validation 

An input validation dialog state can be used to get information from the bot's user. It first checks if the variable specified in the 'variable' field exists.  

If 'variable' has a value already, the bot will go automatically to the next bot dialog specified in the 'Next bot dialog' dropdown list. 

If 'variable' does not have a value, the bot will ask the question as defined in the Question section. 

#### Human handover/offloading 

Bots are great as a first line of support. However, they are not \(yet\) as smart as human support agents. Hybrid forms of chatbots in combination with live agents offer the best user experience. When a chatbot transfers the user to a human agent, we call this human handover or offloading. 

#### Live Chat 

Live chat allows the user to talk to a human agent. 

#### Live agent 

A human agent that can help the user when the chatbot is no longer able to. 

#### Token 

Each API request requires authentication to identify the user that is responsible for making the request. Authentication is provided by \(access\) tokens. 

#### CSS 

Cascading Style Sheets \(CSS\) is a style sheet language used for describing the styling of a document written in a markup language such as HTML. 

#### White listing \(Regex\)

The White List allows you to configure your Chat Widget to only display on website that you’ve allowed. To do so, you can write a Regex containing the allowed domains. This is an extra security measure to prevent third parties from including your Chatbot on their websites. 

#### Threshold 

You can decide how precisely your bot interprets what your user says by using a threshold that determines what the lowest matching score acceptable to trigger an interaction is. If the matching score falls below the confidence score, the bot will trigger fallback interaction, an interaction that asks the user to repeat the query. 

#### VUI 

Voice User Interface. VUI allows the user to interact with a system through voice or speech commands. Virtual assistants, such as Siri, Google Assistant, and Alexa, are examples of VUIs. 

