# NPS template

## Template overview &#x20;

This chatbot template can be adapted for your own business to collect feedback from your users, following the NPS score system. Users will be asked if they are satisfied with your services, how likely they are to recommend you to others, and what they think can be improved about your services. Based on the ratings your users give, a Net Promoter Score (NPS) will be calculated. You can learn more about NPS [here](https://www.netpromoter.com/know/).

Keep reading to learn how you can customize this template for yourself!

## How to customize this template&#x20;

To save your users' ratings and feedback, this chatbot uses Airtable. If you also want to use Airtable, you'll need an Airtable account, a base with a table for collecting the feedback, and your own Airtable API key. Of course, you can connect any other database software, as long as it can make an API call to communicate with the Chatlayer platform.

Below is an overview of each flow within this template, and all the dialogs you need to change to customize this template for your own business.&#x20;

Let's get started!

### Flow: General

#### Dialog: Introduction

In the Introduction dialog, replace the gif with one that fits your brand, or remove it altogether if it does not fit your business' or bot's personality.

### Flow: NPS

#### Dialog: Check rating

This dialog checks the rating a user gives, after which it's stored as the variable `NPS_rating`. If they give a rating of 9 or higher, the user will be classified as a 'promoter' in the variable `respondent_type` and redirected to the 'Promoter response' dialog asking them why they like your services (response stored in `Reason_positive_rating`).&#x20;

If they gave a rating from 7 to 8, they will be classified as  'passive'. If the they gave a rating lower than 7, they are classified as 'detractor' and redirected to the Improvement Feedback dialog. There the bot asks them what can improved (response stored in `Improvement_feedback`).

#### Dialog: Send to Airtable

This Action dialog will store the NPS score, respondent type, and specific feedback in an external database. By default, this template bot will use Airtable to store this data, using the Create Record function of Chatlayer’s Airtable integration.&#x20;

{% hint style="info" %}
You can connect your own database or order management system to this bot, as long as this software can make an API call. Read more about these type of integrations [here](https://docs.chatlayer.ai/integrations/integrations-101).
{% endhint %}

You will need to customize this dialog by connecting it to your own Airtable account and your own Airtable base. However, when you just imported the NPS template, it will be linked to [this Airtable](https://airtable.com/invite/l?inviteId=invhLLUh0JbaO2y2f\&inviteToken=996adaa49de24b5973fee36732413e1dbee710403dd074512aa69a1dcb50a073). Feel free to use this template as an example of what the data in your own Airtable should look like, but make sure to replace it once you start using the bot for your own business! &#x20;

If you do not yet have an Airtable account set up yet, you can do so by clicking 'Connect new account' and following the steps in the pop-up window. You need your Airtable API key, which you can find on your [Airtable account page](https://airtable.com/account).&#x20;

Like the example Airtable, your own Airtable base should have a table with columns for NPS rating, Respondent type, the user's reason for giving a positive rating or their feedback for improvement (in case of a negative rating).

In the 'Base' field, replace the example ID with the ID of your own Airtable base. In the 'Table' field replace the example ID with the ID or name of the table in your own Airtable base where you the reservations data is stored. You can find your Airtable's base ID and table IDs [here](https://airtable.com/api).&#x20;

In the action dialog, in the left column under Record, we add the names of all fields we want to fill in the new Airtable record, i.e. NPS\_rating, Respondent\_type, Reason\_positive\_rating, Improvement\_feedback; in the right column we specify the variables we want to put as values in those fields.&#x20;

Once you have collected ratings from enough users you can use these to easily calculate your business' overall Net Promoter Score. You can learn more on how to calculate this score [here](https://customergauge.com/blog/how-to-calculate-the-net-promoter-score#:\~:text=program%20more%20reliable-,The%20NPS%20Calculation%20Formula,is%20a%20score%20of%2040.).
