# The Conversation Design process

Before you can start building your bot on the Chatlayer.ai platform, there are a few strategic steps to take. From defining the use cases to crafting a bot personality – here's how to build a bot just right for your business.

![](../../.gitbook/assets/emoji-figure.jpg)

## **1 — Define the goal** <a id="6f63"></a>

Before you can start building your chatbot, you need to know **why** **you are building it**. What is the goal here? If you want to automate an existing service, what is the current experience like, and how could a bot help you improve it? 

Make sure to look at your business/marketing goals: if one of your goals is to increase customer satisfaction, you may want to add a chatbot to your customer support team and let it handle the most common FAQs, so your team has more time to focus on the complex cases.

## 2 — Define the use cases <a id="9f38"></a>

After figuring out the why of your bot, it’s **time for the what**. What is your bot going to do exactly? How will it help the user? We cannot stress how important it is to figure this out **before** **you start building your bot**, you cannot build something that isn't clear yet.

Here are some use case examples:

* Book a restaurant
* Play a song
* Find specific products
* Recommend new products
* Get directions
* Book a flight
* Show local promotions
* Process returns

## 3 — Understand your tech <a id="d127"></a>

Know that you know the why and the what of your bot, it’s important to understand the where: **where will your bot live?** Will it be integrated with WhatsApp? Can customers engage with it via SMS, Facebook Messenger or on the company website? **What are the restrictions of each channel?** A bot that talks to your users via SMS won’t be able to use as many characters as a bot that only communicates via web. So make sure you understand your tech and its limitations.

> Our platform allows you to easily connect your bot to multiple channels and all your back-end databases. That's how you provide your users with a truly delightful experience.

## 4 — Know your user <a id="948d"></a>

In order to design an experience that feels personal, you need to make it personal. **Who is this user that will engage with your bot?** It’s important to know what they want and how they are feeling during the conversation. What’s their backstory? Their challenges? Their motivations? How familiar are they with your business and using bots in general? Our Conversation Designer likes to create a user ID that they keep close when writing the actual dialogues.

![An example of a user ID](../../.gitbook/assets/sarah.png)

## 5 — Craft your bot personality <a id="eb7b"></a>

A chatbot without personality is like a bad Tinder date: they looked great online, but as soon as you start talking to them, you want to end the date as soon as possible. There just wasn’t a connection…

So how can you make sure that your users connect with your chatbot and that the conversation is engaging and representative of real human interaction? By giving your chatbot a **clear** **personality**.

If you can, use your company branding as a starting point and build on it. You can read more about how to design your chatbot’s personality [**here**](https://chatbotslife.com/how-to-design-your-chatbots-personality-free-download-dd9eeccffbb9).

## 6 — Script your happy flow <a id="d5fb"></a>

Now that you have a clear picture of who’s communicating \(your bot persona and your user ID\) and what they’re talking about \(your use cases\), it’s time to write the **dialogues**.

**A ‘happy flow’ is** **a dialogue where everything everything runs the way it’s supposed to run**. The conversation is natural and smooth, and the user reaches their goal in as little steps as possible. Many conversation designers start with the happy flow because it’s the flow of least resistance. It takes the least amount of effort to script because it doesn’t include many of the inconvenient complexities that can occur.

But they will, and you need to be ready for when they do.

> **A great way to script a natural conversation is by having a sample dialog**. Have two people sit back-to-back and improvise a conversation around a use case, with one person playing the user and the other playing the chatbot. Record their conversation or take notes to see which parts of the dialog still need a bit more work.

## 7 — Script for edge cases <a id="06e9"></a>

While our AI technology is very, very good, it is not yet capable of understanding every user utterance well enough in order to reply in a correct way — no matter how well the script is written, in tricky situations, it will most likely fail. So after writing the happy flows, write out the most likely ways a user might go off track and how you’re going to deal with that. The sample dialog should help those pain points, as will user testing.

What if a user asks your bot how it’s doing? What if they tell the bot they don’t like it? What if they want another suggestion? What happens if the user wants to book a table for two, but one person is allergic to gluten and the other one doesn’t eat fish? 

{% hint style="info" %}
You can find these kind of questions as prebuilt intents in our platform's NLP section. These intens are predefined and come with their own expressions, which means you can use them straight away!
{% endhint %}

Always make to strategically guide the user back to an existing flow, like in the example below:

![A good answer to an out-of-scope question that puts the user back on track](../../.gitbook/assets/image%20%28343%29.png)

## 8 — Create the flowchart <a id="247b"></a>

Once you’ve written all possible flows, create a **visual flowchart** to see how a user would go from start to finish and where they might want to — or have to — dive into other flows. There are a ton of great tools out there to help you visualise these journeys, like [draw.io](https://draw.io/) & [Creately](https://app.creately.com/).

{% hint style="info" %}
_The_ [_**chatlayer.ai platform**_](https://chatlayer.ai/) _allows you to visualise your flows straight away whilst scripting your dialogues.👏_
{% endhint %}

![A visual overview of the different dialogues on the Chatlayer.ai platform](../../.gitbook/assets/flows.jpg)

## 9 — Testing your bot <a id="1b70"></a>

When you’ve completed your dialogues and created your flowchart, it’s time to take a deep breath. You’re now gonna send your bot to its first test! 

In order to get some first feedback, you can share your bot with a few friends and colleagues and ask them to complete some specific tasks. For example: “Play a song” or “Order some food” or “Return a pair of jeans”. Make sure to also ask them some detailed questions about the overal experience after:

* **Personality**: does the bot feel consistent? Does it fit the brand?
* **Onboarding**: was it clear what this bot can do for you? Did you miss anything?
* **Understanding**: did the bot understand your questions and answers? Where did you get stuck?
* **Answering**: did the bot give accurate, relevant and clear answers? Did it feel conversational?
* **Error management**: how did the bot handle errors? What went wrong? How did it make you feel?
* **Overal experience**: did you enjoy the conversation?

> On our platform you can see which intents and expressions were recognised \(in\)correctly, how long each user session was, and when the API plugins and code blocks returned an error.

{% hint style="info" %}
The Chatlayer.ai platform offers a lot of testing options: you can check which intents and expressions were recognised \(in\)correctly, how long each user session was, and when the API plugins and code blocks returned an error.
{% endhint %}

![An overview of the NLP testing area on our platform](../../.gitbook/assets/debug.png)

## 10 — Optimising <a id="ac29"></a>

Internal testing will already give you a lot of insight on how to improve your bot, but its your real users that you want to hear from. So after publishing your bot, make sure to **keep monitoring its performance**. Monitor the conversations, collect and analyse data, and keep improving the bot for an even better experience!

