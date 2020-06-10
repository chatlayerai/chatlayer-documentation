# Variables

Variables are used in Chatlayer.ai to store any information the bot knows about a customer. This can be the language or channel they're using, but also information coming from external data sources through for example an API. All variables are stored on what is called the _session_ of a user.

## Sensitive variables - GDPR

In Chatlayer.ai you can make sure that variables are not stored. This is typically useful when the conversation between a bot and user contains sensitive information, such as a bank account number. Sensitive data often should not or can not be stored with an external provider like Chatlayer.ai, in order to comply with GDPR or other data & security policies.

To make sure variables are not stored in the database you can click on Variables in the Settings tab. Here you can add a variable to the list of variables by clicking on + Variable. 

![](../../.gitbook/assets/screenshot-2019-05-13-at-14.48.10.png)

If you put the Sensitive toggle to `true`, the content of your variable will never be stored in the database. Instead only a placeholder with the variable name is stored.

## Incrementing variable counter

If you want to incrementally increase the value of a variable, you can use the following steps:

* Define a variable, for example `variableName`, and give it a numeric value such as `0`
* At the point in the flow where you want to increment the value of `variableName`, enter variableName as the variable and `{variableName|increment}` as the value.

This method will increase the value of counter by 1 each time for example a specific bot dialog is passed or button is clicked.



