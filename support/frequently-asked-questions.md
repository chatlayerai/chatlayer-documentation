# Frequently Asked Questions \(FAQ\)

## Is it possible to connect two bots to each other?

In general, our advice is to try to centralize as much information within one bot, as long as the target audience & broad use case for that bot remains the same.

However, if for whichever reason, it is important of having two bots talking to the user within the same conversation, there are a few possibilities for achieving this.

* If you use the chatlayer web widget you could send an 'event' to the web application to indicate that the user should be connected to another bot. This is only possible with the Web & Webhook channel. 
* Option 2 is to use the Webhook channel, however this requires some custom implementation. In this case you could host a proxy service that feeds messages from the different channels to Chatlayer.ai. In this proxy service you can decide per incoming message at which bot you want to ask for an answer. Option 2 is a more advanced use case, and therefore not very common, but there are some bots within our platform that work this way. There is currently no out of the box solution that allows cross-channel switching between bots.

