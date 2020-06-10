# Analytics

## Definitions

Throughout our analytics we use several key concepts. In order to fully understand these analytics, it's important to know the exact definitions of these concepts.

### User

A user is anybody who sends at least one message to the bot. 

If you're on an asynchronous channel like Facebook or WhatsApp, the user will be persisted throughout their entire lifecycle with the bot. This means that every Facebook user talking to the bot only counts as one user in the analytics.

If you're exposing the bot through a web widget or custom implementation, by default every time somebody refreshes their web page and starts talking to the bot again they are counted as a new user. However, some clients configure their web widgets in a way that recognizes a returning user with a Sender ID. These returning users only count once.

### Message

A message is every interaction from the user towards the bot. This can be a typed expression, but also a button click, a file upload, etc.

#### Not understood message

A message counts as not understood if it's an expression that is not an exact match for one of the trained expressions and the NLP confidence of this expression falls below the defined [NLP threshold](../../understanding-users/natural-language-processing-nlp/settings.md).

### Session

Every time a user says something for the first time or after an interval of at least 15 minutes of silence, it counts as a new session.

#### Session duration

The duration between the first message of a session and the last message before a period of at least 15 minutes of inactivity.



