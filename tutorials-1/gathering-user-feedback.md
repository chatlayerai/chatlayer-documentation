# Gathering user feedback

This tutorial will show you how to gather feedback from your users about the quality of the bot and send that feedback to an external database for further analysis. In this example, we will send the feedback data to Airtable – a tool that allows you to create a spreadsheet that you can talk to using an API.

* Start by creating a flow in your Chatlayer.ai bot that contains rating options, for example:

![](../.gitbook/assets/image%20%28300%29.png)

* Make sure you save the rating of the user as a variable "star\_rating" with a number value
* As a Go To, create a new input validation called "long text feedback"

![](../.gitbook/assets/image%20%28292%29.png)

* Save the additional comments under the "comment" variable, and Go To a newly created Action "send feedback to Airtable"
* In the newly created Action, add a "Code" plugin that contains the following header:

![](../.gitbook/assets/image%20%28301%29.png)

* The "nextDialogState" is where your bot will go after saving the feedback to Airtable
* Create a new Airtable with these columns:

![](../.gitbook/assets/image%20%28298%29.png)

{% hint style="info" %}
In this tutorial, we will be using [this Airtable](https://airtable.com/shrip6vQuFSy5z7Tz). Feel free to reuse it!
{% endhint %}

* Add the following code to your Code plugin in Chatlayer.ai

```javascript
const body = {
    "records": [{
        "fields": {
            "star_rating": args.star_rating,
            "comment": args.comment,
            "sessionId": args.sessionId
        }
    }]
}
const airtableResult = await fetch('https://api.airtable.com/v0/(insert app name here)/(insert table name here)', {
    method: 'POST',
    body: JSON.stringify(body),
    headers: {
        'Authorization': 'Bearer (insert your bearer token here)',
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

* Add a small confirmation to the "feedback recorded" bot dialog
* Ready to test

![](../.gitbook/assets/image%20%28296%29.png)

* The feedback data from the user shows up in the Airtable, ready for analysis!

![](../.gitbook/assets/image%20%28293%29.png)



