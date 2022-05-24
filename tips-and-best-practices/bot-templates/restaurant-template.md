# Restaurant template

## Template overview &#x20;

This chatbot template can be adapted for your own restaurant. With this bot, your users can see the latest menu, order food online for delivery or pick-up, and book a table.

Keep reading to learn how you can customize this template for yourself!

## How to customize this template&#x20;

To register the orders and reservations, this chatbot uses Airtable. If you also want to use Airtable, you'll need an Airtable account, a base with a table for both orders and reservations, and your own Airtable API key. Of course, you can connect any other order management software, as long as it can make an API call to communicate with the Chatlayer platform.

Below is an overview of each flow within this template, and all the dialogs you need to edit to customize this template for your own restaurant.&#x20;

Let's get started!

### Flow: General

#### Dialog: Introduction

In the Introduction dialog, replace the image with that of your own restaurant. You can also delete it if you prefer. In the text, make sure to change 'The Taco Shop' and 'Sal' with your own restaurant and bot name.&#x20;

### Flow: See the menu&#x20;

**Dialog: Show menu**

Change the image of the taco menu in this dialog to an image of your own restaurant’s menu. \
Tip: you can use [www.canva.com](https://www.canva.com/) to create a free menu and any other visuals needed.

### Flow: Book a table&#x20;

This flow allows users to make a reservation at your restaurant. The bot will first ask the user on what date they want to make a reservation, and for how many people, and then look up the availabilities for that day in an external database. It then shows these options to the user. &#x20;

#### Dialog: Search availability in Airtable&#x20;

This Action dialog will look up available reservation times in an external database. By default, this template bot will use Airtable to look up times, using the Search Record function of Chatlayer’s Airtable integration.&#x20;

{% hint style="info" %}
You can connect your own database or order management system to this bot, as long as this software can make an API call. Read more about these type of integrations [here](https://docs.chatlayer.ai/integrations/integrations-101).
{% endhint %}

You will need to customize this dialog by connecting it to your own Airtable account and your own Airtable base. However, when you just imported the Restaurant template, it will be linked to [this Airtable](https://airtable.com/invite/l?inviteId=inv4z7FlKMiMCJZC0\&inviteToken=c391841a94cbae63af44e7d8ae26c5700909a42e4adf95007f313badadfb8cfb\&utm\_source=email). Feel free to use this template for testing, or as an example of what the data in your own Airtable should look like, but make sure to replace it once you start using the bot for your own restaurant! &#x20;

If you do not yet have an Airtable account set up yet, you can do so by clicking 'Connect new account' and following the steps in the pop-up window. You need your Airtable API key, which you can find on your [Airtable account page](https://airtable.com/account).&#x20;

Like the template Airtable, your own Airtable base should have a table with columns for reservation date, reservation time name, user email, special menu and number of people.&#x20;

In the 'Base' field, replace the example ID with the ID of your own Airtable base. In the 'Table' field replace the example ID with the ID or name of the table in your own Airtable base where you the reservations data is stored. You can find your Airtable's base ID and table IDs [here](https://airtable.com/api).&#x20;

The 'Search' field is the name of the field (= column) in Airtable that we want to search in. In this case, the column with possible reservation dates, and 'Search' value is the value that will be searched for in that column, in this case the date the user wants a reservation. &#x20;

#### Dialog: Send reservation to Airtable&#x20;

This Action dialog updates the Airtable record of the reservation slot your customer has chosen with their reservation details (name, email, number of people and choice of special menu). &#x20;

Just like the search availability in Airtable dialog, you will need to customize this dialog by connecting it to your own Airtable account and your own Airtable base. In the 'Base' field, replace the example ID with the ID of your own Airtable base. In the 'Table' field, replace the example ID with the ID or name of the table in your own Airtable base where the reservations data is stored. &#x20;

In the 'Record' ID, we use the ID of the record we retrieved from Airtable in the Search record action, which is stored in the variable `apps.airtable.read_record._id`. Under 'Cell values', in the left column, we have filled in the the name of the fields in Airtable we want to update, and in the right column are the names of the chatbot variables we want to use as values in those fields.&#x20;

#### Dialog: Send reservation email&#x20;

This Action dialog sends your customer an email with the confirmation of their reservation. Replace 'the Taco Shop' by your own restaurant’s name and customize the email’s text to your own preference. &#x20;

### Flow: Order online&#x20;

This flow allows your customers to place an online order. The user will order several options, step-by-step, choosing between main dishes (in this case, tacos), extras, and desserts. After choosing, they will be given an overview of their complete order and the opportunity to make changes if they want. When the order is complete, the user is asked to choose between delivery or pickup, and at what time they want to receive their order. Finally, the user needs to choose a payment method, after which they will receive a confirmation by email.&#x20;

#### Dialog: Order tacos &#x20;

This dialog lets the customer choose main dishes, displayed in a carousel. This enhances the user experience because people like to see what the dish looks like, before deciding if they want it.

Replace all images, titles, and subtitles for each carousel item with the options available at your restaurant. If your restaurant offers more than three menu items, you can add an additional carousel item for every extra menu option needed.&#x20;

In the button of each carousel item, replace the `name_of_taco` variable name with a name for your own restaurant. If your restaurant does not specialise in one food item, you can give this variable a generic name, like for example, `main_course`.&#x20;

Replace the template values with the values corresponding to the menu items at your restaurant. These variables and their values should correspond to the match entities you define in your bot’s NLP.&#x20;

#### Dialog: Already ordered same taco?&#x20;

This Go-to dialog will check if the user already has the same taco in their order.&#x20;

In the conditions, replace `name_of_taco` with the name of the variable you gave to your main courses in the Order tacos dialog. Replace `taco_order_nr_1`-`3` by the name of the variables you define in Save taco order. Add an additional Go to condition for each main course item you added to the carousel in Order tacos and ad a Go to to a corresponding bot dialog.&#x20;

#### Dialog: Number of tacos&#x20;

Replace `name_of_taco` in the text with the menu items variable you defined above, and replace `number_of_tacos` with a variable name appropriate to your restaurant.&#x20;

#### Dialog: Save taco order&#x20;

This Go-to dialog saves the menu item chosen by the customer to the correct variable. If the customer has not selected any items yet, their choice will be assigned to the first variable. If they already chose one previous item, the item will be stored in a second variable, etc.&#x20;

You should add an extra Go-to condition for any additional menu items you added to the carousel in the 'Order tacos' dialog. Also replace the names of the variables `taco_order_nr_1-3` and `taco_order_nr_1-3_quantity` by variable names for your restaurant. &#x20;

#### Dialog: Extras & Dialog: Dessert&#x20;

Ordering Extras and Dessert works the same way as ordering tacos. You can customize these dialogs by applying the same steps as described above for taco ordering:

* Order extras
* Order dessert
* Already ordered same extras/dessert?&#x20;
* Number of extras
* Number of dessert
* Save extras
* Save dessert&#x20;

#### Dialog: Show final order&#x20;

This dialog gives the customer an overview of their final order. Replace the order and order quantity variable names with the ones you defined for your own menu items above.&#x20;

#### Dialog: Yes checkout&#x20;

This dialog gives the customer the option to choose between pick up or delivery for their order. &#x20;

In case your restaurant does not offer these options, you can change the text of this dialog to a general acknowledgement message and set either the Delivery or Pick-up time dialog as the Go to.&#x20;

#### Dialog: Send order to Airtable&#x20;

This Action dialog will store the customer’s order in an external database. By default, this template is set up to store this information in an Airtable using the 'Create Record' function of Chatlayer’s Airtable integration.&#x20;

{% hint style="info" %}
You can connect your own database or order management system to this bot, as long as this software can make an API call. Read more about these type of integrations [here](https://docs.chatlayer.ai/integrations/integrations-101).
{% endhint %}

Just like with the other Airtable integration dialogs, you will need to customize this dialog by connecting it to your own Airtable account and your own Airtable base. The example Airtable the template is linked to by default also contains an orders table.&#x20;

Your own orders table should contain a field for each menu item and the quantity of each item, as well as fields that specify delivery or pickup, delivery time, pick-up time, and the customer’s phone number and email address.&#x20;

In the action dialog, in the left column under Record, we add the names of all fields we want to fill in the new Airtable record, i.e. all menu item options and their quantities, pick-up or delivery details and the customer’s details; in the right column we specify the variables we want to put as values in those fields.&#x20;

That's it, you've just customized your own Restaurant chatbot! 👏
