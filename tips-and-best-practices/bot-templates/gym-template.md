# Gym template

This booking assistant helps your customers to schedule their gym sessions. It offers a free trial for new joiners, books and reschedules trainings and classes, and answers some practical questions about prices, rules, and opening hours. A valuable tool to make your customers more free!

This bot uses [Airtable](https://docs.chatlayer.ai/integrations/app-integrations/airtable-app-integration) to store data on gym sessions locations.&#x20;

To find the nearest gym location, this bot uses the [Find Nearest Location](https://docs.chatlayer.ai/tips-and-best-practices/bot-templates/use-case-templates/template-find-nearest-location) use case template.

## Flow: Choose language

This is the flow triggered when the user opens the chatbot. It will ask them to choose between continuing the conversation either in German or in English, which will be set as value for the `preferredLanguage` variable. Read more about multilingual bots [here](https://docs.chatlayer.ai/understanding-users/multilanguage-bots).

## Flow: General

The Introduction message here sets up the 3 main use cases, into 3 Quick Reply buttons:&#x20;

* `I'm new` leads to the Lead Generation flow,&#x20;
* `Bookings` leads to to Manage classes and Manage trainings, &#x20;
* `FAQ` leads to the FAQ flow

On top of the regular dialogs that are found in many bots (e.g. Introduction, Goodbye, Anything else, etc), you will find some routers here to keep the conversation flowing:

#### Dialog: User details exist?

At the end of a use case flow, the conversation loops back at the 3 use cases cited above through the Anything Else dialog. If the user would like to keep in touch, the User details exist go-to dialog will be triggered to check if the bot already knows the user details. If so, it will just summarise what is already known. If not, it will ask for the user details.

#### Dialog: Start again

This action dialog clears all the variables of the conversation so that the conversation can start again. This is useful for testing but also if the conversation is left and the user wants to start again. It is triggered whenever users greet the bot, by using the `chitchat.greeting` intent.

## Flow: Lead generation

This is the flow triggered by clicking on the "I'm new" button in the Introduction message. The bot offers a free trial to the user, then their details are asked before they get suggested to book a class right away.&#x20;

## Flow: manage classes

This is where conversations on booking or cancelling a class happen. Each of them is triggered by either the `book_class` __ or __ `cancel_class` intent.

#### Dialogs: Which language?

These go-to dialogs are routers to decide which Airtable data needs to be retrieved. This data will depend on the `preferredLanguage` variable that is defined in the Choose Language flow, at the very start of the conversation. This step is necessary since dates, times and locations are not said the same in German or in English.&#x20;

{% hint style="info" %}
You will need one Airtable table per language. For instance, we have used 4 tables for English (Group classes, Trainings with Enrique, Trainings with Jenny, and Locations), and 4 more for German (same data but translated to German).
{% endhint %}

Those dialogs happen both in the Book class part of the flow and in the Cancel class part of the flow.

#### Dialogs: Clear class and Clear cancel class

Those action dialogs clear out the variables that define the class to book or to cancel. By doing so, we avoid the bot taking for granted that the same class is meant if users repeat the same flow. Instead, the bot will ask which class is meant by the user again.

#### Dialog: Which advice?

Depending on the booked class, the bot advices users on what to bring for this class through this go-to dialog. Do not hesitate to personalise this as much as you would like: make your users feel acknowledged! This part of the flow can also happen earlier: you could decide to advise them before they decide on a class.

## Flow: manage trainings

This flow is very similar to the Manage classes flow: here, you can book, cancel or reschedule a training.

#### Dialogs: Cancel training > Find trainings booked

Those action dialogs fetch data from the Airtable depending on which teacher is requested to find an already-booked training. We use `user` as a search value since this is the value noted down in our Airtable if the training is considered as "booked".

#### Dialogs: Book training > Find available trainings

Those action dialogs fetch data from the Airtable depending on which teacher is requested to find an available training. We use `none` as search value since this is the value noted down in our Airtable when the training is considered "available".

#### Dialog: Training > Cancel or change?

This go-to dialog is called after the Find booked trainings dialogs. It routes the conversation to a different message if the user chooses to reschedule a training or to change one. To know that, we fill a `cancelOrChange` variable with the appropriate `cancel` or `change` value.

#### Dialogs: Which teacher and language?

These go-to dialogs steers the conversation depending on the `preferredLanguage` and the `classTeacher` variables, so that the correct Airtable data can be fetched.

#### Dialog: Book training > Is name known?

This go-to dialog checks if the bot already knows the `userName` variable. If not, it will ask the user name here.

#### Dialog: Clear training session

This action dialog clears out all variables that define the training requested, so that the user can keep speaking to the bot without the bot taking for granted what training they are talking about.

## Flow: FAQ

In this flow are grouped some of the frequently asked questions and their answers. We focused on 3 topics: covid rules, prices, and opening hours.

To find the opening hours of the nearest office, we have implemented the [Find Nearest Location](https://docs.chatlayer.ai/tips-and-best-practices/bot-templates/use-case-templates/template-find-nearest-location) flow.

## Flow: Frank Search when Not Understood

Frank Search is a playful and useful way to continue the conversation even if the bot did not understand what the user said. Whenever the user will say something out of scope, or unclear, Frank is triggered and will do a web search to try to find an answer.&#x20;

