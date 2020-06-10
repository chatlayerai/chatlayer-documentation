# Using time in your chatbot

With Chatlayer.ai, you can use the Get Time plugin to guide your flow based on the current moment in time.

One of our customers, for example, uses this to determine if it is winter or summer, and will recommend tires based on the current season.

To implement this, first create an `Action` bot dialog that contains a Get Time plugin.

![](../.gitbook/assets/image%20%28211%29.png)

This plugin saves the current time variables to a variable of your choosing. Determine the name of this variable in the Target field. You can use it in your Go To's and Bot Messages with the following variables:

* \(target\).year
* \(target\).month
* \(target\).days
* \(target\).hours
* \(target\).minutes
* \(target\).seconds

All variables will return a number. You can use them in your flow like this:

![](../.gitbook/assets/image%20%28223%29.png)

