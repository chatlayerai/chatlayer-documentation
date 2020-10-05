# Phone & voice

A voice bot is an extra layer on top of your chatbot. You can reuse your existing chatbot, and we will handle speech-to-text \(STT\) and text-to-speech \(TTS\). Configuring voice using our platform is a matter of minutes and we've created some custom components to make the configuration even easier.

Activate your phone channel by going to the Channels tab and clicking the '+' button next to 'Phone'.

![](../.gitbook/assets/image%20%28179%29.png)

## Architecture

### Testing

If you want to test a first version of your voice bot before going into production, you can use a test number. Before you can use a test number and call your bot, you have to give your number to the bot, so we know which bot you're trying to talk to.

Click the Create Configuration button to set this up. The Chatlayer.ai test number will be shown on top of the Phone configuration screen.

![](../.gitbook/assets/image%20%2860%29.png)

### Production

When you're ready to move your bot into production, please [get in touch](../support/get-in-touch.md). We will set up a specific phone number for your bot which can be used to call directly or forward calls to. A typical phone architecture looks like this:

![](../.gitbook/assets/nlp-high-level-architecture-2x-1.png)

## Voice-specific Chatlayer.ai components

### Silence detected event

If you want to trigger a certain flow when the user is silent for a set time, use the event which we describe [here](../bot-answers/events.md#silence-detected-event).

### Voice message format type for input validation

You can save anything the user is saying as a variable by using the voice message format type in an input validation. Read more [here](../bot-answers/dialog-state/user-input-bot-dialog.md#voice-message).

### Actions: forward call & close call

These actions are available when you configure the voice channel and will allow you to:

* Forward a call to a number of your choosing, often used to handover a customer from the bot to a live agent
* End the call by hanging up

