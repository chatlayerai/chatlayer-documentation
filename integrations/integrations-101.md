---
description: Integrations with Chatlayer, how does it work?
---

# Integrations 101

Would you like to start your integration journey with Chatlayer? Great choice!

This page will help you to get started and guide you in the right direction.

## Choose your integration

Chatlayer offers multiple ways of integration, all with their own possibilities.



### API plugin

The API integration is an integration that allows you to make API calls to your server and process the result as responded by your server. You can find this in an action dialog > API.

You can best use API when you want to make an API call to your server for the following use-cases:

* To easily create a GET or POST request with only filling in the headers and parameters
* When you want your server to respond to a particular message
* When you want to get details to be stored in the session from your server.
* Integrate with your own API where you can make changes if need be.

You should have your own service when you want to set this up. The service/API should respond in the same format as Chatlayer expects. The format that Chatlayer expects can be found [here](https://docs.chatlayer.ai/integrations/custom-back-end-integrations#sending-the-api-response). For more information about API integration visit [this page](https://docs.chatlayer.ai/integrations/custom-back-end-integrations)



### Chatlayer v1 REST API

Our own REST JSON API, as described in our [API documentation](https://api.chatlayer.ai/v1/docs/), can be used to make the API calls to Chatlayer and can be used as another way to integrate your service to Chatlayer.

One of the most common use cases of using the Chatlayer (REST JSON) API would be to integrate Webhook channel. We also provide a variety of service via our API some of which are:&#x20;

* Get all conversations
* Get all messages in a conversation
* Send messages
* Set session
* Pause/unpause the bot
* Trigger a specific dialog of the bot
* Extract the NLP for an expression
* Send user messages coming from your [Webhook channel](https://docs.chatlayer.ai/channels/webhook-api)

While making request to chatlayer API, Chatlayer expects a bearer token to be passed for the authorization. In case of unauthorized token, we respond with `401 Unauthorized` status code.

Some of the endpoints are rate limited and those can be figured out by checking the headers as defined below:

```http
HTTP/1.1 200 OK
x-ratelimit-limit: 1200
x-ratelimit-remaining: 1199
x-ratelimit-reset: 1609459200000
```

* `x-ratelimit-limit` - the rate limit ceiling that is applicable for the current request.
* `x-ratelimit-remaining` - the number of requests left for the current rate-limit window.
* `x-ratelimit-reset` - the time at which the rate limit resets, specified in UTC epoch time (in seconds) code editor

The example request samples can be seen on the right side of the page for each request. Some of the sample responses can also be seen on the bottom right of page.

You can expand all the request body schema to find all the schemas of the objects that can be sent in as the request to the Chatlayer API as shown in the image below and [on this page](https://api.chatlayer.ai/v1/docs/#section/Overview).

![](<../.gitbook/assets/Screenshot 2021-10-27 at 13.43.26.png>)

### Code Editor

In the code editor, you can easily add your custom code (in JavaScript) to the flow of the bot. You can use this plugin to make custom API calls to your or third party servers to manage and display the response that is sent back. This is a very versatile tool that we provide which helps you to add custom logic on the bot.

To start building with this integration, you need nothing more than (basic) Javascript knowledge.

You can best use Code editor if you want:

* Custom logic to be added into the bot, deciding where the flow should go next. This can also be done with Go Tos, but the code editor allows for more complex conditions than the Go To.
* To use the response sent by the server during an API call and want to first analyse the data sent by the server before further processing it.&#x20;
* To integrate with third-party API, for example [creating a ticket](https://docs.chatlayer.ai/integrations/human-offloading-live-chat/creating-a-zendesk-support-ticket) in an external ticketing system&#x20;

For some examples on how to use the code editor, check out this [POST ](https://docs.chatlayer.ai/integrations/code-action/airtable)or [GET ](https://docs.chatlayer.ai/integrations/code-action/retrieving-data-from-airtable-get)example.

### Webhook channel

The Webhook channel is best used when you want to use our amazing NLP engine and the bot flow that is provided by the Chatlayer along with your own custom page that handles the chat UI. Webhook integration can also be used if you want to integrate a bot in Chatlayer with another bot that you have running somewhere else.

The concept behind this integration is that Chatlayer will work behind the scenes to process your queries and then once the query is processed, Chatlayer will call your API with the result. This makes this integration more lightweight and can be easily integrated with other channels . For the processing intensive tasks, you do not have to keep waiting for the response from Chatlayer as we will call your own API URL when the processing is done.

You can activate Webhook channel in the 'Channels' page on the platform. All you have to do is provide the URL where we need to make the API call when the webhook request is processed.

For more information about Webhook channel visit [this page](https://docs.chatlayer.ai/channels/webhook-api).

## How to start

You now have chosen which integration type is best for your bot, great!

Now, you will need to start mapping out what your integration will look like.

For every integration, except the Webhook channel, it is important to visualise which information you first need to collect from the user before you send it to the external system. For example, when creating a ticket in an external ticketing system, first decide which variable you need, such as category, description, email address etc. Then, make sure all these variables are sent over correctly to the external ticketing system.

With response integrations, you would need to visualise what you would like to do with each response from the external system. Which responses can you receive from that system? Is there a certain logic, that response X leads to a different bot dialog in Chatlayer than response Y?&#x20;

Asking yourself these questions beforehand, and preparing your integration to cover all scenarios, will make it easier to build your integration on Chatlayer.

## Integration FAQ

Here you can find some frequently asked questions about our integration options:

#### What is the difference between the Webhook API and the Chatlayer API?

Chatlayer API works as request and response format, so a request is sent to the external system and a response is sent back.&#x20;

The Webhook API works as an event triggering system where, when the processing of certain request is complete, we do an API call to your system with the data that you expected from the previous call.

#### Which language do you support in Chatlayer?

Our API are built in Nodejs and in the Chatlayer platform we use JavaScript

#### Do you have a swagger file?

We do have a swagger file! The content of the swagger file is deployed [here](https://api.chatlayer.ai/v1/docs/#section/Overview).
