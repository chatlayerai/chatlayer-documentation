# Using time in your chatbot

The Get Time plugin on our platform guides your flow based on the current moment in time.

For example: one of our customers uses this plugin to determine if it's winter or summer, and will recommend tires based on the right season.

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

