# Reuse flows

For a lot of bots built on Chatlayer.ai the answer to a question a user has depends on some information you know about that customer. This information, such as which type of customer you are, which sort of subscription you have, etc, can be gathered through an API, but also directly in the flow itself.

For example:

![](../.gitbook/assets/image%20%2880%29.png)

In this flow the answer a customer gets depends on the type of customer they are. However, the customer type is important for the answer to a lot of different questions a user might have. We don't want to build the same "customer type question" logic every time the user asks a question like this. Instead we want to create that in one place.

In this tutorial you will be learning how to create a reusable flow, how to trigger it, and how to return to the original point in the flow.

* Create a bot dialog that links to the intent that needs a specific answer. Link this bot dialog with a Go To to the flow you want to reuse. Add a variable of type "bot dialog", give it a name such as "reuseFlow", and a bot dialog to return to once the flow is finished.

{% hint style="info" %}
You can create two types of variables in Chatlayer.ai: text variables, that allow you to store data on the session of the user, and bot dialog variables, that allow you to store a variable. Read more about variables [here](../tutorials/tutorial-conditional-flow-navigation.md).
{% endhint %}

![](../.gitbook/assets/image%20%28189%29.png)

* Create the flow you want to reuse, and gather the variables you need from the customer
* Add the end of your flow, add a new Action bot dialog, and add a "Go to variable bot dialog" plugin. Fill in the bot dialog variable to return to in this flow

![](../.gitbook/assets/screen-recording-2020-02-06-at-14.53.00.gif)

* When a user reaches this part of the flow, they will return to the original bot dialog that was defined in the reuseFlow variable.

The flow used in the example above looks like this:

![](../.gitbook/assets/image%20%285%29.png)

