# Retrieving data from Airtable \(GET\)

Bots are often used to show data from external sources to your user. An easy way to manage this data is by using [Airtable](https://airtable.com). Airtable is a tool that allows you to create a spreadsheet that you can talk to with an API.

In this tutorial we will set up an integration with Airtable. Because of all the code it looks quite technical, but in fact it's pretty easy.

{% hint style="info" %}
If you're new to using variables in Chatlayer.ai, follow [this](../tutorials/tutorial-conditional-flow-navigation.md) tutorial first.
{% endhint %}

As an example we're going to be building a bot that shows information about chatbot meetups.

* The first thing we have to do is create some meetup data. In this example, we will be using [this Airtable](https://airtable.com/shrJGHyo1RZuJf72Z). Feel free to reuse it!

![](../.gitbook/assets/image%20%28132%29.png)

* Start by building a short flow that states the purpose of the bot and that asks about which month the user wants to know meetup info.

![](../.gitbook/assets/image%20%28165%29.png)

* For the month question, make sure you're using an [input validation](../bot-answers/dialog-state/user-input-bot-dialog.md) that saves the response as the`month` variable and that continues to the next step: an action bot dialog.

![](../.gitbook/assets/image%20%28138%29.png)

* Configure the action bot dialog that is triggered after the input validation with a code plug-in. Add the "month" variable as an argument, as shown in the screenshot:

![](../.gitbook/assets/image%20%28122%29.png)

* Next, add this code snippet:

```javascript
const { month } = args;

const { records = [] } = await fetch(
  "https://api.airtable.com/v0/(yourAppId)/(yourTableName)",
  {
    method: "GET",
    headers: {
      Authorization: "Bearer (insert token here)",
    },
  }
).then((res) => res.json());

const found = records.filter((rec) => rec.fields.Month === month.toLowerCase());

const builder = ChatlayerResponseBuilder();

if (found.length) {
  builder.setSessionVariable("meetups", found);
} else {
  builder.setSessionVariable("nomeetups", found);
}

builder.send();
```

{% hint style="warning" %}
Remember to get the right app id, table name and bearer token for your Airtable. You can find it [here](https://airtable.com/api).
{% endhint %}

* This code block searches the table for a meetup in the month that the user said, and if it finds one, returns that information to Chatlayer.ai. If there is no meetup found, the `nomeetups` variable is saved to the session of the user.
* If you follow the flow to this point, it will look something like this:

![](../.gitbook/assets/image%20%28199%29.png)

* And the following data is saved on the session:

![](../.gitbook/assets/image%20%28134%29.png)

* Now all we need to do is show that data! Add a Go To at the end of the Action bot dialog where you have added the code block.
* Configure this Go To as following:

![](../.gitbook/assets/image%20%2841%29.png)

* This way, the user will get a different response if there are no meetups in the month that they've asked about.
* Finally, configure the messages in "show meetup info" to show the retrieved info from the Airtable sheet.

![](../.gitbook/assets/image%20%28101%29.png)

* All done! You can now test the full flow.

![](../.gitbook/assets/image%20%2848%29.png)

