# What's new

## March 2021 Release

* New role: you can add a member to a RESTRICTED bot as NLP-only now. Read more [here](../bot-answers/user-management.md#bot-access).
* Credit card payments: you can now pay for your Chatlayer subscription using a credit card.
* Zoom controls in the Flows view

![](../.gitbook/assets/image%20%28413%29.png)

## February 2021 Release

### New bot dialog components

We introduced a new style for the bot dialog components. Looks good, right?

![](../.gitbook/assets/image%20%28399%29.png)

This update also makes it easier to see which type of button you're creating.

![](../.gitbook/assets/screenshot-2021-02-09-at-15.07.07.png)

### Better performance

In the background, we have switched from one database type to another, making the bots and the platform a lot faster. We will gradually move bots to this new database, so it might take a few weeks for your bot to enjoy the performance benefits.

### Team member roles & bot access

A lot of customers use bots in different parts of their organization. They have both a bot to help support their customers, as well as an internal HR bot. Often, these bots process sensitive information that should only be accessible by the team building that specific bot. That's why we have introduced team member roles & bot access.

Enterprise customers can now restrict bots to only be accessible by certain team members. Furthermore, you can set a team member as "read-only" so they can see how the bot is configured, but not change anything.

Read all about how to use team member roles & bot access:

{% page-ref page="../bot-answers/user-management.md" %}

## December 2020 Release

We released new types of entities. You can find all information about them here:

{% page-ref page="../understanding-users/natural-language-processing-nlp/synonym-entities.md" %}

## October 2020 Release

### Bot import/export \(in beta\)

Save a copy of your bot in an export. The export contains:

* NLP
  * Intents
  * Expressions
  * Entities
* Bot dialogs
  * Flows
  * Messages and translations
  * Variables

The export does not contain:

* Conversation history
* Analytics
* Channel settings
* Bot settings

Exporting a bot will result in a JSON file that you can download to your computer.

This JSON file can be imported again to overwrite a bot with the data that is in the JSON file.

### Sorting

You can now change the order of buttons, quick replies, carousel items and go to's using drag and drop.

![](../.gitbook/assets/nov-24-2020-15-29-40.gif)

### Bot dialog language switching

Change the language of a bot dialog to immediately add or edit the translations for a message or button while you're creating or editing the flow.

![](../.gitbook/assets/nov-24-2020-15-26-26.gif)

### Rich text messages

Customize text messages the way you want them to look, and add links to other pages and bot dialogs, using rich text messages. You can read all about them [here](../bot-answers/dialog-state/message-components.md#rich-text).

![](../.gitbook/assets/image%20%28325%29.png)



