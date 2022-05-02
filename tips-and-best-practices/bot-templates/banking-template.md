# Banking template

## Template overview

This chatbot can help users check their account balance, report a card as lost or stolen, check their card limit, and find the office closest to them.&#x20;

Let's dive into how you can change this template for your business!

## How to customize this template

This template only uses dialogs to display data (which means that addresses, account numbers etc will be pre-defined in the dialog). In order to use real data, you can use the [Airtable App integration](https://docs.chatlayer.ai/integrations/app-integrations/airtable-app-integration).&#x20;

### Flow: General

#### Dialog: Introduction

In the introduction message, you can change the Botbank image to an image that fits your branding and bot's personality. There, you can also change the Quick Reply buttons to the main flows you want to be covered by your bot, i.e. the main issues that can be taken care of by the bot.

### Flow: Card limit

In this flow, users ask to check their card limit, and they get a different response depending on what card type they choose. Card types are defined under the `accounttype` contextual entity in the NLP section.

### Flow: Transfer money

In this flow, users can make a one-time money transfer, or create a standing order.

#### Dialog: One-time transfer

Here, the bot first asks the amount to transfer, from which account, and finally the bank account number of the recipient. These values are stored as `transfer_once_amount`, `Type_Account`, and `IBAN` entities.&#x20;

To check that the bank account corresponds to a correct IBAN format, we use a Go-To component that verifies if the `IBAN` exists. To do so, the bot checks that the IBAN that is entered by the user matches the IBAN Regex pattern. In short, it checks whether this is a valid IBAN. To see this pattern and adapt it to your needs, you can go in Entities > Match Entities > `@IBAN.`

#### Dialog: Standing order

To set up a standing order, the bot first asks the user how often the payment should occur. This is stored as the variable `transfer_occurence`variable. After that, it asks for the the start and end date. To check if the user's input is a valid date, we check if the value matches "date" before saving it as the variables `start_date_standing_order` and `end_date_standing_order.`

### Flow: Card information

This flow allows a user to report their card as lost or stolen. The user is immediately redirected to external links to help block the card, after which they're asked if they want to order a new card.

#### Dialog: Card lost or stolen

You can customize the external links to redirect your users to your website and/or phone number.&#x20;

{% hint style="info" %}
In the Action dialog 'clear address', we tell the bot to forget the variable 'user\_address' because the user wants to correct their address by entering a new one. We need to clear the old variable in order to save the new one.
{% endhint %}

### Flow: Office locations

This flow is triggered when we want to show the user the office that is the closest to them. For the sake of this template, addresses are predefined within the dialog, but you customize yours following the [Find Nearest Location Template](https://docs.chatlayer.ai/tips-and-best-practices/bot-templates/use-case-templates/template-find-nearest-location) with Google Maps.





