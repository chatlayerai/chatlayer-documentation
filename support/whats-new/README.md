---
description: New features and functionalities in the platform
---

# What's new

## January 2022

* [Integration with Freshdesk](../../integrations/app-integrations/freshdesk-app-integration.md) to create Freshdesk support tickets

## December 2021

* [Improved input validations](https://docs.chatlayer.ai/bot-answers/dialog-state/user-input-bot-dialog#entity-input-type), check whether the given user input is equal to one of your entities

## November 2021

* We now have the [bot builder](https://docs.chatlayer.ai/organization-management/access-control#team-roles) role in our Team roles
* [Native app integrations](https://docs.chatlayer.ai/integrations/app-integrations) without custom code, check out [the Airtable tutorial here](https://docs.chatlayer.ai/integrations/app-integrations/airtable-app-integration)
* We have a new channel: [LINE](../../channels/sinch-conversation-api-beta.md)

## October 2021

* You can now start a conversation initiated by the user, [skipping the introduction message](https://docs.chatlayer.ai/tutorials-1/skip-introduction-message)
* On the home page, you can now find the menu ['Billing and usage'](https://docs.chatlayer.ai/support/billing-and-subscription#billing-and-usage) to track your usage and plans.
* We now support offloading via [Sinch Contact & Contact Pro](https://docs.chatlayer.ai/integrations/human-offloading-live-chat/sinch-contact)

## August 2021

* A brand new color scheme that fits our new branding&#x20;
* [Data retention](https://docs.chatlayer.ai/bot-answers/settings/data-retention): enterprise customers can set a custom retention time for their conversations, sessions and training expressions.
* A configurable [typing indicator](https://docs.chatlayer.ai/bot-answers/settings#bot-behaviour)
* Another new channel: talk to your users on [Telegram](../../channels/sinch-conversation-api-beta.md)

## June 2021

* Support for managing team members through Single Sign On (SAML SSO). \
  Read more [here](../../organization-management/access-control/single-sign-on-sso-saml.md)
* We got ISO27001 certified

## May 2021

* The bot name can now be seen in the tab title in your browser. Helps if you're managing multiple bots!
* New analytics, see all about it [here](https://docs.chatlayer.ai/bot-answers/analytics)
* New way to access the platform & publish bots. Read more [here](../../bot-answers/publishing-your-bot/publishing-new.md)
* Integration with Sinch Contact to transfer a conversation from the bot to an agent

## April 2021

* Bot templates! You don't have to start from scratch anymore. Read more [here](../../tips-and-best-practices/bot-templates/). If you have ideas for new bot templates, [get in touch](../get-in-touch.md) with us
* Export/import of translations table: you can now edit the translations in an exported csv, and import them once you're done. Read more [here](../../understanding-users/multilanguage-bots/translations.md)
* Integration with Salesforce Service Cloud to transfer a conversation from the bot to an agent. Read more [here](../../integrations/human-offloading-live-chat/salesforce-service-cloud.md)

## March 2021

* New role: you can add a member to a RESTRICTED bot as NLP-only now. Read more [here](../../organization-management/access-control/#bot-access)
* Credit card payments: you can now pay for your Chatlayer subscription using a credit card
* Zoom controls in the Flows view

![](<../../.gitbook/assets/image (413).png>)

* We have reworked out Translations table to be a lot faster, and more convenient to use

## February 2021

### New bot dialog components

We introduced a new style for the bot dialog components. Looks good, right?

![](<../../.gitbook/assets/image (399).png>)

This update also makes it easier to see which type of button you're creating

![](../../.gitbook/assets/screenshot-2021-02-09-at-15.07.07.png)

### Better performance

In the background, we have switched from one database type to another, making the bots and the platform a lot faster. We will gradually move bots to this new database, so it might take a few weeks for your bot to enjoy the performance benefits.

### Team member roles & bot access

A lot of customers use bots in different parts of their organization. They have both a bot to help support their customers, as well as an internal HR bot. Often, these bots process sensitive information that should only be accessible by the team building that specific bot. That's why we have introduced team member roles & bot access.

Enterprise customers can now restrict bots to only be accessible by certain team members. Furthermore, you can set a team member as "read-only" so they can see how the bot is configured, but not change anything.

Read all about how to use team member roles & bot access:

{% content-ref url="../../organization-management/access-control/" %}
[access-control](../../organization-management/access-control/)
{% endcontent-ref %}

## December 2020

We released new types of entities. You can find all information about them here:

{% content-ref url="../../understanding-users/natural-language-processing-nlp/synonym-entities/" %}
[synonym-entities](../../understanding-users/natural-language-processing-nlp/synonym-entities/)
{% endcontent-ref %}

## October 2020

### Bot import/export (in beta)

Save a copy of your bot in an export. Exporting a bot will result in a JSON file that you can download to your computer.

This JSON file can be imported again to overwrite a bot with the data that is in the JSON file. Read more here:

{% content-ref url="../../bot-answers/settings/" %}
[settings](../../bot-answers/settings/)
{% endcontent-ref %}

### Sorting

You can now change the order of buttons, quick replies, carousel items and go to's using drag and drop.

![](../../.gitbook/assets/nov-24-2020-15-29-40.gif)

### Bot dialog language switching

Change the language of a bot dialog to immediately add or edit the translations for a message or button while you're creating or editing the flow.

![](../../.gitbook/assets/nov-24-2020-15-26-26.gif)

### Rich text messages

Customize text messages the way you want them to look, and add links to other pages and bot dialogs, using rich text messages. You can read all about them [here](../../bot-answers/dialog-state/message-components.md#rich-text).

![](<../../.gitbook/assets/image (325).png>)

