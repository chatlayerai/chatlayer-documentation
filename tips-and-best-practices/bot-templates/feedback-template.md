# Feedback template

## Template overview

This template allows you to collect feedback from your users. By default, the template asks the user to rate their experience in three areas (products, delivery and customer service) and asks them to give more detailed feedback if they did not give a perfect rating. These ratings and feedbacks are stored as variables and are then sent to an external database (in this case Airtable). If the user gives their email address, they will also be offered a discount code

## &#x20;How to customize this template

To customise this flow, you will need an Airtable account, an Airtable base with a feedback and discount code tables, and your Airtable API key.

### Contact info

This dialog offers the user a discount code if they give their email address. If the user doesn’t want to give their email, they will immediately be sent to the end of the flow.

### Search discount code

If the user does give their email address, this dialog will look up an available discount code in an external database. By default, this template is set up to look up this code in an Airtable using the Search Record function of Chatlayer’s Airtable integration.

{% hint style="info" %}
You can link any sort of database to this bot, as long as it has an API. Read more about integrations [here](https://docs.chatlayer.ai/integrations/integrations-101).
{% endhint %}

You will need to customize this dialog by connecting it to your own Airtable account and your own Airtable base. However, when you have newly imported the Feedback template, it will be linked to [this Airtable](https://airtable.com/invite/l?inviteId=inv4OOmgw4Z9LECqW\&inviteToken=a76823d9162c8ffc11225de76fa27ced854aaaeaf90c1013bc5f65ffebf4a8ae\&utm\_source=email). Feel free to use it as an example of what the data in your own Airtable should look like, but make sure to replace it once you start using the bot for your own organisation. &#x20;

If you do not yet have an Airtable account set up in Chatlayer, you can do so by clicking Connect new account and following the steps in the pop-up window (you will need your Airtable API key). You can find your API key on your [Airtable account page](https://airtable.com/account).&#x20;

Like the example Airtable, your own Airtable base should have a table with one Code\_status column and one Discount\_code column.&#x20;

In the Base field replace the exampleID with the ID of your own Airtable base. In the Table field replace the example ID with the ID or name of the table in your own Airtable base where you want to store the feedback. You can find your Airtable's base ID and table IDs [here](https://airtable.com/api).&#x20;

### Set discount code used

This action dialog changes the status of the discount code that was looked up in the previous dialog from Available to Used with the Update Record function. We use the record ID of the discount code As in the previous dialog, you will need to connect to your own Airtable account and replace the example base and table IDs by your own.

### Send to Airtable

This Action dialog sends the feedback the bot has gathered to an external database, in this template again an Airtable using the Create Record function. As in the previous Airtable integration dialogs you will need to connect your own Airtable account and base and table IDs. In your Airtable base you will need a table with columns for each of the feedback variables, as well as the user’s email address.

![](<../../.gitbook/assets/Screenshot 2022-03-23 at 10.37.51 (1).png>)

If your own Airtable uses different field (column) names you will also need to replace the names in the left hand column in the Record field by the field (column) names in your own Airtable.

Once you've connected the bot to your own Airtable, use the emulator to test your bot and verify if the feedback is written correctly to your Airtable.
