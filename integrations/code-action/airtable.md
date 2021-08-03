# Sending data to Airtable \(POST\)

Data gathered inside of bots is often sent to an external database. An easy way of doing this is by ingrating with [Airtable](https://airtable.com). Airtable is a tool that allows you to create a spreadsheet that you can talk to with an API.

In this tutorial we will set up an integration with Airtable. Because of all the code it looks quite technical, but in fact it's pretty easy.

{% hint style="info" %}
If you're new to using variables in Chatlayer.ai, follow [this](../../tutorials/tutorial-conditional-flow-navigation.md) tutorial first.
{% endhint %}

* Start by building a short flow that you use to gather some data about your user, for example:

![](../../.gitbook/assets/image%20%2874%29.png)

* This flow adds the variables "customerType" and "firstName" to the session of the user.

![](../../.gitbook/assets/image%20%282%29.png)

* Set up an Airtable that has a column for each variable you want to save. Rows will be added for each customer.

![](../../.gitbook/assets/image%20%28102%29.png)

{% hint style="info" %}
In this tutorial, we will be using [this Airtable](https://airtable.com/invite/l?inviteId=invSGcyaorwSSPjLi&inviteToken=a6d2dc90da0a95019886b059a10323d827520aa1b46dcf2c528756c3e120189c). Feel free to reuse it!
{% endhint %}

* At the point in the flow where you want to send the data to Airtable, add an Action containing a Code plugin.

{% hint style="info" %}
Want to learn more about the possibilities of the Code plug-in? You can find it [here](./).
{% endhint %}

* In our example, we want to send the customer's type and first name. Furthermore, we want to jump to another bot dialog as soon as the data has been sent. Start by adding these parameters at the top of your code editor.

![](../../.gitbook/assets/image%20%28173%29.png)

* Then add the code below to the plugin and save your Action dialog.

```javascript
const body = {
    "records": [{
        "fields": {
            "First Name": args.firstName,
            "Customer Type": args.customerType
        }
    }]
}
const airtableResult = await fetch('https://api.airtable.com/v0/(yourAppId)/(yourTableName)', {
    method: 'POST',
    body: JSON.stringify(body),
    headers: {
        'Authorization': 'Bearer (insert token here)',
        'Content-Type': 'application/json'
    }
}).then(r => r.json())

ChatlayerResponseBuilder()
    .setNextDialogState(args.nextDialogState)
    .send()
```

{% hint style="warning" %}
Remember to get the right app id, table name and bearer token for your Airtable. You can find it [here](https://airtable.com/api).
{% endhint %}

* Et voilà! Now, every time a user goes through your flow, their data will be sent to Airtable, and they will continue on to the Success bot dialog.
* If there are any errors with your connection to Airtable, you can find them in the Error logs tab in Chatlayer.ai.

![](../../.gitbook/assets/image%20%28127%29.png)

