# Banking template

## Template overview

This chatbot can help users check their account balance, card limit, report a card as lost or stolen,  and find the office closest to them.&#x20;

Let's dive into how you can change this template for your business!

## How to customize this template

This template only uses dialogs [Airtable App integration](https://docs.chatlayer.ai/integrations/app-integrations/airtable-app-integration) to search and read data. Make sure to make your own and connect it to this template to connect your own data to your bot.

### Flow: General

#### Dialog: Introduction

In the introduction message, you can change the Botbank image to an image that fits your branding and bot's personality. There, you can also change the Quick Reply buttons to the main flows you want to be covered by your bot, i.e. the main issues that can be taken care of by the bot.

#### Dialog: Not Understood

For this message, we have used a [Not Understood Counter](https://docs.chatlayer.ai/tips-and-best-practices/not-understood-bot-dialog/not-understood-counter?q=not+under) to create a better user experience and make the bot feel more natural. Feel free to adapt those dialogs to your bot's persona.

#### Dialog: Anything Else

This dialog is where the conversation goes to when a flow is over. For instance, when the user is done checking their account, they will be asked if there is anything else that can be done to help them. Make sure to make this dialog fit to your own use cases as well.

### Flow: Check account

This flow groups everything related to checking the user's account. Two use cases fall under it: checking an account balance, and checking a card limit. A spreadsheet for Accounts and another for Cards were created in an Airtable base that was made by using the  [Airtable App integration](https://docs.chatlayer.ai/integrations/app-integrations/airtable-app-integration).

On the one hand, if users ask to check their card limit, and they get a different response depending on what card type they choose. Card types are defined under the `cardtype` contextual entity in the NLP section. This flow is triggered either by a Quick Reply button or by the `Card.Limit` intent.

On the other hand, if users ask to check their account balance, they can choose to check their current account or savings account. Those are defined under the `accounttype` contextual entity. This flow is triggered either by a Quick Reply button or by the `Check.Balance` intent. Once the balance is checked, the user is asked if they want to make a money transfer from that account. This redirects us to the `Transfer money` flow where a `Is account known?` Go-To dialog checks that the `accounttype` variable is already filled before proceeding to the money transfer.

### Flow: Transfer money

In this flow, users can make a one-time money transfer, or create a standing order.

#### Dialog: One-time transfer

Here, the bot first asks the amount to transfer, from which account, and finally the bank account number of the recipient. These values are stored as:

`amount` : the amount to be transferred

`accounttype` : the account from which the money is transferred

`IBAN` : the recipient's account number

To check that the bank account corresponds to a correct IBAN format, we use a Go-To component that verifies if the `IBAN` exists. To do so, the bot checks that the IBAN that is entered by the user matches the IBAN Regex pattern. In short, it checks whether this is a valid IBAN. To see this pattern and adapt it to your needs, you can go in the Entities tab > Match Entities > `@IBAN.`

#### Dialog: Standing order

To set up a standing order, the bot first asks the user how often the payment should occur. This is stored as the`frequency`variable. After that, it asks for the the start and end date. To check if the user's input is a valid date, we check if the value matches "date" before saving it as the variables `startDate` and `endDate`. Here users can also add a reference in their transfer, stored under the `reference` variable.

### Flow: Report lost card

This flow allows a user to report their card as lost or stolen. The user is immediately redirected to external links to help block the card, after which they're asked if they want to order a new card. This flow is triggered by either a Quick Reply button or the `Lost.Or.Stolen.Card` intent.

To find the nearest office locations, the conversation is steered to the `Office locations` flow.

#### Dialog: Report lost card

You can customize the external links to redirect your users to your website and/or phone number.&#x20;

{% hint style="info" %}
In the Action dialog 'clear address', we tell the bot to forget the variable 'user\_address' because the user wants to correct their address by entering a new one. We need to clear the old variable in order to save the new one.
{% endhint %}

### Flow: Office locations

This flow is triggered when we want to show the user the office that is the closest to them. For the sake of this template, addresses are predefined within the dialog, but you customize yours following the [Find Nearest Location Template](https://docs.chatlayer.ai/tips-and-best-practices/bot-templates/use-case-templates/template-find-nearest-location) that uses Google Maps.

### Flow: Random questions

In this flow are grouped all dialogs meant to answer random questions like: _Which cards do you offer?, How are you?, Who built this?, ..._ All those dialogs are triggered by intents so that the bot can answer to those random questions at any time in the conversation. Make sure that you foresee many of those while building your bot so that the conversation continues to flow.





