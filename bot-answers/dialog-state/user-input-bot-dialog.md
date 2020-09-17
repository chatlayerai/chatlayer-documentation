# Input Validation

An input validation dialog state can be used to get information from the bot users. 

The input validation dialog state first checks if the variable specified under the 'variable' field exists.

If 'variable' has a value, the plugin automatically goes to the next bot dialog specified in the 'Next bot dialog' dropdown list.

If 'variable' does not have a value, the plugin will ask the question as defined under the Question section.

Session variables can be already known for various reasons:

* the user has answered this question before
* an entity was extracted with the same variable name
* the user is authenticated and the variable was automatically set

## Invalid input

You can specify the message to be displayed when input validation fails, or fails 3x. For example the first time a message might simply be "Can you try again?" or "Can you try DD/MM/YYY format?" and after 3 fails the message might be "Please contact our support at \[tel number\]" or to redirect the user to a live agent.

## Settings

### Disable NLP

Users are able to leave the input validation if an intent is recognized. For bots with a very small NLP model, this might trigger a false positive. The disable NLP checkmark allows you to to disable the NLP model while in the input validation, which makes sure that whatever the user says gets saved as input.

![](../../.gitbook/assets/image%20%28109%29.png)

### Always past - always future

Chatlayer parses the expressions from users to match a default date format. If the date you ask should always be present or future, you can use these options. A user saying “Thursday” for example will be either mapped to last or next Thursday.

### Input types

Input plugins automatically validate and extract different input types based on the type setting. The type parser is responsible for extracting the data out from the user input. For example if the input plugin has a type of _date_ and the user his input sentence was 'I need to be in Paris _in two days_' the input plugin parser will extract the date definition out of this user input which results in 'in two days'. The parser will convert this into a date representation, DD/MM/YYY and the result will be stored in the user session.

#### Any

The 'Any' input type will accept all string values as an input. It is important to know that intents and entities are processed before parsers. This can be useful for automatically extracting certain pieces of a sentence as an answer to a question. We've got a great example of this in our tutorial [here](../../tutorials/tutorial-request-and-use-information-using-input-plugins.md).

#### Date

The Date input parser type will try to parse the response as a date. Sentences like 'next week monday' are automatically converted to a DD/MM/YYYY date object. Supported formats \(also in other supported NLP languages\)

* 22/04/2018
* 22/04
* 22 apr
* 22 april 18
* twenty two april 2018
* yesterday
* today
* now
* last night
* tomorrow, tmr
* in two weeks
* in 3 days
* next monday
* next week friday
* last/past monday
* last/past week
* within/in 5/five days
* friday/fri
* ... \(Contact the [Support](https://github.com/chatlayer/chatlayer-documentation/tree/583d39b48ac82ffccf142520f337ede136bb68e2/reference/support.md) team for extra supported formats\)

#### Location

The location parser will send the user input sentence to the Google Geocoding API service. When a correct address or location is recognized, Chatlayer will automatically create a variable with all relevant geodata.

![An example for a location input validation](../../.gitbook/assets/screenshot-2020-09-17-at-12.25.45.png)

For the bot dialog that we configured as shown in the screenshot, a message 'Where do you work?' would be prompted to the user. When the user of the bot answers that question, an object containing information about the location will be stored in the `user_work_location` variable. Below is an example that shows how the `user_work_location` variable will look when the user responds with 'Chatlayer.ai':

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

A bot message configured as:

`Thank you, shall I send your package to {user_work_location.fullAddress} then?`

Will result in the following message to the user in this specific example:

`Thank you, shall I send your package to Oudeleeuwenrui 39, 2000 Antwerpen, Belgium then?`

#### Number

Number will parse any number the user has given.

#### Hours

This input type will parse and validate timestamps.

#### Currency

This input type will parse and validate currencies.

#### E-mail

This input type will parse and validate e-mail addresses.

#### Postal code

This input type will parse and validate postal codes. Note: as of now, only Belgian postal codes are supported.

**Image**

The image format type allows you to check if a user has uploaded an image. Currently, this is only possible in Facebook Messenger.

#### Language

This input type will parse and validate NLP supported languages.

* English: \(en-us\): 'engels', 'english', 'en', 'anglais'
* Dutch \(nl-nl\): 'nederlands', 'dutch', 'ned', 'nl', 'vlaams', 'hollands', 'be', 'ned', 'néerlandais', 'belgisch'
* French \(fr-fr\): 'french', 'français', 'frans', 'fr', 'francais'
* Chinese \(zh-cn\): 'chinese', 'cn', 'zh', 'chinees'
* Spanish \(es-es\): 'Spanish', 'español', 'es', 'spaans'
* Italian \(it-it\): 'italian', 'italiaans', 'italiano', 'it
* German \(de-de\): 'german', 'duits', 'de', 'deutsch
* Japanese \(ja-jp\): 'japanese', 'japans', 'jp', '日本の
* Brazil Portugese \(pt-br\): 'brazil portugese', 'portugese', 'portugees', 'braziliaans portugees', 'português'

#### **Voice message**

![](../../.gitbook/assets/image%20%2821%29.png)

Use the Voice message input type to save whatever is said to the bot in a voice channel as text. You can configure the maximum duration of this voice message, and how long it takes for the bot to regard the message as "complete".

