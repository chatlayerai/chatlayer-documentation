---
description: >-
  Airtable is a cloud collaboration service. It’s a spreadsheet-database hybrid:
  has the capabilities of a database applied to a spreadsheet.
---

# Airtable App integration

With this integration you can search, read, and update data in your Airtable database much easier  than having to create an API.

You can connect your Airtable App in 2 ways:

1\. [Via Action bot dialog](airtable-app-integration.md#a.-via-action-bot-dialog): when you are building your bot

2\. [From Chatlayer's homepage menu](airtable-app-integration.md#b.-from-chatlayers-homepage-menu): mainly before building your bot, when you know you’re going to create requests to one or more Airtable tables

## 1 – Via Action bot dialog

Configure your Airtable App directly in an Action bot dialog by clicking the option 'Add action' and then 'Integration':

![](<../../.gitbook/assets/0 (1)>)

If there is no Airtable app configured yet (as described in part 2 of this guide), a pop-up will appear:

![](../../.gitbook/assets/1)

You can find your API Key in you Airtable Account page. Find out more [d](https://support.airtable.com/hc/en-us/articles/219046777-How-do-I-get-my-API-key-).

![](<../../.gitbook/assets/2 (1)>)

Or you can also regenerate key:&#x20;

![](<../../.gitbook/assets/3 (1)>)

When clicking the API Key, you’ll be able to see it. So click, select, copy and paste it into the correspondent field of the pop-up:

![](../../.gitbook/assets/4)

You’ll see a new field to select integrations from. Choose 'Airtable'

![](../../.gitbook/assets/5)

In the Airtable Account field, you’ll see all Apps that you might have already created following the steps in the second part of this guide, or you can create a new one by clicking the 'Connect new account':

![](../../.gitbook/assets/6)

Once you pick the integrated App that you already have (or you created a new one), you’ll see the 'Select Action' field. There are three possible actions: Search, Create and Update records from your Airtable

![](../../.gitbook/assets/8)

Three new empty fields will appear in this screen. Here’s how you should fill them in:

![](../../.gitbook/assets/9)

You’ll get the information for the field “Base” from the Airtable URL. The URL syntax is:

https://airtable.com/**appXXXXXXX\[use this for “Base”]**/**tblYYYYYY\[use this for “Table”]**/…

![](<../../.gitbook/assets/10 (1)>)

![](<../../.gitbook/assets/11 (1)>)

This is what your Action dialog will look like once it’s filled in:

![](../../.gitbook/assets/12)

For the Search Action, fill in the 'Search Field' (use the name of your table's column) and Search Value (a [variable ](../../bot-answers/settings/secure-variables-gdpr.md)that user will input, that should match one of the Search Field's data point) **or** create your own Search Formula.\


More information on what to fill if you want to use the 'Search Formula' option [here](https://support.airtable.com/hc/en-us/articles/203255215-Formula-field-reference).

Now build your answer syntax:

![](<../../.gitbook/assets/image (678) (1) (1) (1) (1).png>)

You'll know it's right when your bot displays the correct data from your table:

![](<../../.gitbook/assets/image (672) (1) (1) (1).png>)

## 2. From Chatlayer's homepage menu

You can set up the Airtable integration directly from the left side menu on [app.chatlayer.ai](https://app.chatlayer.ai)

![](<../../.gitbook/assets/13 (1)>)

![](../../.gitbook/assets/14)

You can also create it by clicking '+ Add Account' button, after which you’ll see this pop-up:

![](../../.gitbook/assets/15)

You can find your API Key in your Airtable Account page. Find out more [here](https://support.airtable.com/hc/en-us/articles/219046777-How-do-I-get-my-API-key-)

![](../../.gitbook/assets/16)

Or you can regenerate a key:

![Graphical user interface, text, application, email

Description automatically generated](<../../.gitbook/assets/17 (1)>)

When clicking the API Key, you’ll be able to see it. Click, select, copy and paste it into the correspondent field of the pop-up:

![](<../../.gitbook/assets/18 (1)>)

This is what it will look like when you’ve successfully connected

![
](<../../.gitbook/assets/19 (1)>)

When clicking the three dots on the right, you can manage your app integration. There are four actions:

![](../../.gitbook/assets/20)

* Reconnect: it will open up a new pop-up allowing you to change the API Key
* Test Connection (soon)
* Change Account Name: will open up a pop-up so you can rename your integrated App
* Remove: **Attention!** When clicking this button, your App integration will **immediately** be removed

![Reconnect](<../../.gitbook/assets/image (674) (1) (1) (1).png>)

![Change Account Name](<../../.gitbook/assets/image (680) (1) (1) (1) (1).png>)

![Remove](<../../.gitbook/assets/image (673) (1) (1).png>)

## How to use each type of Action possible in the Airtable App Integration

Search, Create and Update Record are the possible actions:

![](<../../.gitbook/assets/image (676).png>)

### Create Record

To create a record, you must select the Airtable App and the Airtable account (either connecting to an existing one or connection to another), choose the Create Record action, inform Base and Table, as explained in A.8.1(link).

The following step is to fill out the Record fields. In the left-side blank, the name of the column in your Airtable should be informed, and in the right-side blank, the “hard-coded” value or variable (in curly brackets) should be informed.

In the example below, the column to be updated is called ‘Number’ and the variable is called `numberChosen`. The variable informed by the user was saved in a previous step through an [Input Validation bot dialog](https://docs.chatlayer.ai/bot-answers/dialog-state/user-input-bot-dialog).

![](<../../.gitbook/assets/image (698).png>)

### Update Record

To Update a record, you must select the Airtable App and the Airtable account (either connecting to an existing one or connection to another), choose the Update Record action, inform Base and Table, as explained in A.8.1(link).

Read about Record ID and Cell Values fields below the picture.

![](<../../.gitbook/assets/image (709).png>)

#### Airtable Record ID

The Record ID is the one highlighted in the URL from the screenshot below – you cannot use the value informed by the customer alone, to refer to the correct ID, you collect the ID informed by the customer in a variable (though an Input Validation bot dialog).

![](<../../.gitbook/assets/image (720).png>)

The correct syntax to retrieve the Record ID is `{apps.airtable.read_record._id}`

In Cell Values, the name of the column where the value will be updated is informed on the left-side blank, in this case ‘Number’, and the variable which has the new value saved under it in the right-side blank, in this example `{numberUpdate}`

The following screenshot shows an example of the flow that are explained in the table further down.

![](<../../.gitbook/assets/image (722).png>)



| **Bot Dialog**         | **Variable or action taken**                                                                                                                                                                                                                                                         |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Create update          | User passes the current data point thet they would like to update, which will be saved under variable `{ticketToUpdate}`                                                                                                                                                             |
| Get ticket id          | Action taken is the Search Record, with Search Value as the `{ticketToUpdate}` variable                                                                                                                                                                                              |
| Get value update       | The user informs the updated value that will be saved under variable `{numberUpdate}`                                                                                                                                                                                                |
| Read and update ticket | <p>Record Id is retrieved from Airtable using <code>{apps.airtable.read_record._id}</code></p><p>Cell values informed are the column name (in this case, Number) and variable saved in the previous step <code>{numberUpdate}</code> is passed as the new value for that ticket.</p> |

Now you're all set to create a personalized bot experience for your customers!
