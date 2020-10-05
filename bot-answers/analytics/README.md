# Analytics

## Definitions

Throughout our analytics we use several key terms. In order to fully understand our analytics, it's important to know the exact definition of these term.

### User

A user is anyone who sends at least one message to the bot. 

If you're on an asynchronous channel like Facebook or WhatsApp, the user will be the same throughout their entire lifecycle with the bot. This means that every Facebook user talking to the bot will only count as one user in the analytics.

If you're exposing the bot through a web widget or custom implementation, by default every time somebody refreshes their web page and starts talking to the bot again, they are counted as a new user. However, some clients configure their web widgets in a way that recognizes a returning user with a Sender ID. This way, returning users are only counted once.

### Message

A message is every interaction by the user with the bot. This can be a typed expression, but also a button click, a file upload, etc.

#### 'Not understood' message

A message is not understood if it's an expression that is not an exact match for one of the trained expressions and the NLP confidence of this expression is under the defined [NLP threshold](../../understanding-users/natural-language-processing-nlp/settings.md).

### Session

Every time a user says something for the first time, or after an interval of at least 15 minutes of silence, it will count as a new session.

#### Session duration

The session duration is the time between the first message of a session and the last message before a period of at least 15 minutes of inactivity.



