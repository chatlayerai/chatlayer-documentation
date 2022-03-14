# Variables

Variables are used to store any information the bot knows about a user. This can be their preferred language, or the channel they're using, but also information coming from external data sources like, for example, an API. All variables are stored in what is called a user's **session**.

## Sensitive variables - GDPR

Our platform allows you to make sure that some variables are processed differently. This is useful when the conversation between a bot and a user contains **sensitive information**, such as the user's bank account number.

To make sure variables are not stored in the conversation history, you can click on 'Variables' in the Settings tab. Here you can add a variable to the list of variables by clicking on `Create Variable`.&#x20;

![](<../../.gitbook/assets/image (589).png>)

If you put the Sensitive toggle to `true`, the content of your variable will never be stored in your database. Instead only a placeholder with the variable name is stored.

## Incrementing variable counter

If you want to incrementally increase the value of a variable, you can use the following steps:

* Define a variable, for example `variableName`, and give it a numeric value such as `0`
* At the point in the flow where you want to increment the value of `variableName`, enter variableName as the variable and `{variableName|increment}` as the value

This method will increase the value of counter by 1 each time, for example when a specific bot dialog is passed or a button is clicked. How to use this increment functionality in a bot dialog, see[ this tutorial](https://docs.chatlayer.ai/tips-and-best-practices/not-understood-bot-dialog/not-understood-counter).

## Upper case and lower case variables

Variables and values are case sensitive. For example:

`capitalVariable`

will be regarded as a separate variable from:

`CapitalVariable`

The same goes for values. If you check in a [Go To](../dialog-state/plugins.md) if a value for `variableX` is equal to `valueY` it will not be triggered if the value for `variableX` is equal to `valuey`

You can transform a value from upper case to lower case and vice versa by adding these modifiers to the value name:

```
{name|toUpperCase}
{name|toLowerCase}
{name|capitalize}
```

