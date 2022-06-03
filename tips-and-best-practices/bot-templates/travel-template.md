# Travel template

## Template overview

The travel template is a flight booking assistant that uses the Skyscanner API to retrieve ticketing options from the web. This bot makes use of a lot of API calls, which makes it highly customizable.

## How to customize this template



This template can be integrated to your own chatbot as a flow that finds the best flight ticket option for the user. Changes can be made at two levels:

* the dialogs
* the API calls

### Flow: General

In this flow you can modify the introduction message, for instance by changing the gif in the Introduction bot dialog. You can also change the Not Understood dialog to better fit your bot.

### Flow: Booking Flight Ticket

Everything happens in this flow: the bot asks the city of departure, then the specific airport, and same goes for the destination. Then dates are asked. Finally, a recapitulation of the user's request is formulated, and they can validate it before going further.

You can customize this bot by giving more options to your user. In our template, we sticked to a  simple use-case: looking at the best tickets to come and go from a city to another. But what if the user wants a single-way ticket? Or maybe if they would like to compare multiple dates? All these options are customizable depending on how you use the Skycanner API.

The action dialogs 'Clear dates' and 'Clear cities' are here to delete the dates and cites of destination and departure from the bot's memory, so that another request can be made right after that.

