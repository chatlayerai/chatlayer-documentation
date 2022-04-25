# Input Validation

An `input validation` dialog state can be used to get information from the user. When the user gives information, the bot will first check if the info corresponds to an already known variable. Variables can be known already for various reasons:

* The user has answered this question before
* A previous entity was detected with the same variable name
* The user is authenticated and the variable was automatically set

If the `variable` has a `value` already, the bot will automatically go to the next bot dialog specified in the `Next bot dialog` dropdown list.

If the `variable` does not have a `value` yet, the bot will ask the question written in the input validation dialog.

## Invalid input

When a user gives an answer that's invalid (for example, when the bot asks for an email address and the user replies with 'chicken') the bot needs to let the user know their answer was invalid. To do so, you can create a message to be displayed for when input validation fails once, and another message for when the input fails 3 times.&#x20;

For example: the first time an input fails, the error message could simply be "Sorry, I didn't get that. Can you try again?" or "Sorry, that doesn't seem to be a valid date. Can you try the DD-MM-YYYY format?". When the user fails to give valid input 3 times in a row, the error message could be "Sorry, I can't seem to understand. Please contact our support team at \[tel number]". Another option is for your bot to redirect the user to a live agent.

## Settings

### Disable NLP

Users are able to leave the input validation if an intent is recognized. For bots with a very small NLP model, this might trigger a false positive. The 'disable NLP' checkbox allows you to disable the NLP model while in the input validation, which makes sure that whatever the user says gets saved as input.

![](<../../.gitbook/assets/image (699).png>)

### Always past - always future

Our platform parses user's expressions to match a default date format. If the date you ask should always be in the present or future, you can use these options. A user saying “Thursday” for example will be either mapped to last or next Thursday.

## Input types

{% hint style="info" %}
Input validation have two types of input recognition, 'general' input types to check if the input follows a desired format, or 'entity' input types to check the user input with existing entities in the platform.
{% endhint %}

Input plugins automatically validate and extract different input types based on the type setting. The type parser is responsible for extracting the data from the user's input. For example: if the input-plugin has a type of **date** and the user's input-sentence was 'I need to be in Paris _in two days_' the input plugin parser will extract the date definition from this input which results in 'in two days'. The parser will convert this into a date representation, DD-MM-YYYY, and the result will be stored in the user session.

### General input type

#### Any

The 'Any' input type will accept all string values as an input. It is important to know that intents and entities are processed before parsers. This can be useful for automatically extracting certain pieces of a sentence as an answer to a question. We've got a great example of this in our tutorial [here](../../tutorials/tutorial-request-and-use-information-using-input-plugins.md).

#### Date

The Date input parser type will try to parse the response as a date. Sentences like 'next week Monday' are automatically converted to a DD-MM-YYYY date object. Supported formats (also in other supported NLP languages) are:

* 22-04-2018
* 22-04
* 22 apr
* 22 april 18
* twenty two April 2018
* yesterday
* today
* now
* last night
* tomorrow, tmr
* in two weeks
* in 3 days
* next Monday
* next week Friday
* last/past Monday
* last/past week
* within/in 5/five days
* Friday/Fri

#### Location

The location parser will send the user's input to a Google Geocoding API service. When a correct address or location is recognized, the Chatlayer platform will automatically create an object that contains all relevant geo-data.&#x20;

![](<../../.gitbook/assets/image (721).png>)

Look at the bot dialog above. When the user answers the question "Where do you work?" with a valid location, this information will be stored as a `userLocationInformed` variable (you can rename this variable if needed).&#x20;

Below is an example that shows how the `userLocationInformed` variable would be stored when the user responds with 'Chatlayer.ai':

```javascript
{
    fullAddress: "Oudeleeuwenrui 39, 2000 Antwerpen, Belgium",
    latitude: 51.227317,
    longitude: 4.409155999999999,
    streetNumber: "39",
    streetName: "Oudeleeuwenrui",
    city: "Antwerpen",
    country: "Belgium",
    zipcode: "2000",
}
```

{% hint style="info" %}
To show the address as a full address (street, street number, zip code and city) you need to add some extra information to the variable: `.fullAddress`

So in the example above, the bot can display the entire location by using the following variable:`{userLocationInformed.fullAddress}`
{% endhint %}

A bot message containing the following info:

`Thank you, shall I send your package to {userLocationInformed.fullAddress}?`

Will display the following message to the user:

`Thank you, shall I send your package to Oudeleeuwenrui 39, 2000 Antwerpen, Belgium?`

#### Hours

This input type will parse and validate timestamps.

#### **Image**

The image format type allows you to check if a user has uploaded an image or other file (such as pdf). Currently, this is only possible in the Facebook Messenger, WhatsApp, Instagram, RCS, MMS, Telegram and Instagram channels. If the bot user uploads a file, the URL to that file will be saved under the variable you save the response to.

#### Language

This input type will parse and validate NLP supported languages.

* English: (en-us): 'engels', 'English', 'en', 'anglais'
* Dutch (nl-nl): 'nederlands', 'Dutch', 'ned', 'nl', 'vlaams', 'hollands', 'be', 'ned', 'néerlandais', 'belgisch'
* French (fr-fr): 'French', 'français', 'frans', 'fr', 'francais'
* Chinese (zh-cn): 'Chinese', 'cn', 'zh', 'chinees'
* Spanish (es-es): 'Spanish', 'español', 'es', 'spaans'
* Italian (it-it): 'Italian', 'italiaans', 'italiano', 'it
* German (de-de): 'German', 'duits', 'de', 'deutsch
* Japanese (ja-jp): 'Japanese', 'japans', 'jp', '日本の
* Brazil Portugese (pt-br): 'Brazil Portugese', 'Portugese', 'portugees', 'braziliaans portugees', 'português'

#### **Voice message**

![](<../../.gitbook/assets/image (696).png>)

Use the Voice message input type to save whatever is said to the bot in a voice channel as text. You can configure the maximum duration of this voice message, and how long it takes for the bot to regard the message as "complete".

### System entities input type

The input validation parser can check if the given input is consistent with the format for one of the following system entities. Whenever a system entity is chosen in the 'Check if response matches' dropdown, you can give the variable a name that works for you:

![Example of saving an image URL to a variable in an input validation](<../../.gitbook/assets/image (658).png>)

The image will be saved as an array. If you chose {img} as variable, this means that you should use {img\[0]} to retrieve the URL for the first saved image.&#x20;

![Image URL array for WhatsApp channels](<../../.gitbook/assets/image (657).png>)

For the chat widget (web channel), we recommend using the [file upload](message-components.md#file-upload) template.

![](<../../.gitbook/assets/image (598).png>)

#### @sys.email

@sys.email checks if the given user input has the format of an email address. If the given input is not an email address, the bot will show the 'If user response is not valid.. ' messages, at the bottom of the input validation. If the response is a valid email address, you can see that the email address will be saved correctly under the given variable name in the debugger:

![](<../../.gitbook/assets/image (599).png>)

#### @sys.phone\_number

'@sys.phone\_number' will accept numbers with more than 6 and fewer than 17 numbers in them.&#x20;

#### @sys.number

Any number in the bot is immediately recognized as '@sys.number'. However, seeing you could ask for multiple number in different input validations, it is important to give them a unique name. So, when you choose '@sys.number' in 'Check if response matches', you will get the option to give this variable a unique name:

![](<../../.gitbook/assets/image (603).png>)

The input validation will check if the user input given was a number, and if not, the input validation will not continue:

![](<../../.gitbook/assets/image (604).png>)

#### @sys.url

'@sys.url' checks if the given input is a URL. Accepted formats can be with www (_www.chatlayer.ai_) or without (_chatlayer.ai_). Just the domain 'chatlayer' will not be accepted.

{% hint style="info" %}
To learn more about the input and output of the system entities, check out the examples in your own bot via NLP > Entities > System Entities.&#x20;
{% endhint %}

### Entity input type

You can also check if a given user input is identical to any of your created entities.  When you choose an entity type in the dropdown 'Check if response matches' , the entity name is already filled in for you in the 'Save response to variable' field. This is done because you can only [one value saved per entity](https://docs.chatlayer.ai/understanding-users/natural-language-processing-nlp/synonym-entities#the-difference-between-entities-variables-and-values). If you are unsure which entity type will suit your use case best, check out [this article.](https://docs.chatlayer.ai/understanding-users/natural-language-processing-nlp/synonym-entities#types-of-entities)

#### Match entities

Let's say, you have created this awesome bot for your fries shop:

![](<../../.gitbook/assets/image (602).png>)

By creating the entity 'food' with the values 'burger' and 'fries', you can immediately check in an input validation if the given input is a part of the entity. Set up your input validation to check if the response matches your match entity:

![](<../../.gitbook/assets/image (601).png>)

What happens whenever the user gives an input, is that the platform will check if the given input is one of the values of that entity. If the given input is not in one of the values (so 'fries' or 'burger'), the bot will go into the 'When user response is not valid' sections.

#### Contextual entities

For contextual entities, you can also check if there is a match between the input given by the user and the contextual entity values saved in your bot:

![](<../../.gitbook/assets/image (671) (1) (1) (1) (1).png>)

This will check if the answer is listed in the values  of the entity:

![](<../../.gitbook/assets/image (676) (1) (1) (1).png>)

Two important things to note for contextual entities in Input validations:

* If [fuzzy matching is enabled](https://docs.chatlayer.ai/understanding-users/natural-language-processing-nlp/synonym-entities#fuzzy-matching-for-contextual-entities), answers such as 'Brussel' or 'Antwerpp' will also pass in the Input validation as a correct answer.
* Answers like 'To Antwerp please' as input could work. This depends heavily on your NLP model and if the [NLP is not disabled](https://docs.chatlayer.ai/bot-answers/dialog-state/user-input-bot-dialog#disable-nlp) in this Input validation. If, in the Input validation, the NLP is enabled then 'To Antwerp please' could retrigger the intent and save the variable 'Antwerp'. However, it could be that this sentence is not recognized above the NLP threshold and this will mean the bot will go into the 'When user response is not valid' section. Make sure to test this in your own NLP model and create 'When user response is not valid' messages accordingly.

#### Composite entities&#x20;

When choosing a composite entity, the entity name is also prefilled for you:

![](<../../.gitbook/assets/image (605).png>)

Here, we have an '@order' composite entity, which consists of '@sys.number' and '@food'. So user input that will be accepted is '2 fries', 'three burgers' etc.

This will be saved under the variables  'order.sys.number' and 'order.food', as can be seen in the debugger:

![](<../../.gitbook/assets/image (606).png>)

These input types will enhance your flow, and make sure that the input given by the user will be checked with the entity values! If you have any questions do not hesitate to [contact Support](https://docs.chatlayer.ai/support/get-in-touch).&#x20;

&#x20;
