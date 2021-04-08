# NLP import & export

## Importing and exporting expressions

In the tab 'Expressions' you can import and export your NLP model easily.

![](../../.gitbook/assets/image%20%2896%29.png)

When you click on the **Export** button, a dialog will open that allows you to choose which languages and intents you wish to export:

![](../../.gitbook/assets/image%20%28254%29.png)

When you click on the **Import** button, a model opens that guides you through the steps of importing an NLP model. In the first step, you can download a template for your NLP import, and upload your filled-in version.

The second step lets you choose between **adding** to or **replacing** your existing NLP model. Be very careful with replacing your model, this cannot be undone!

![](../../.gitbook/assets/image%20%28252%29.png)

Chatlayer's NLP engine will recognize each expression and will not accept duplicate expressions, so be careful while adding expressions when importing a large number of expressions at a time. When you add expressions manually, there is a check if that expression already exists. This also happens when adding a new import file, but it can be difficult to find which expression is a duplicate. Try these steps to see which expression is a duplicate: 

{% hint style="danger" %}
Please make sure to **backup your data** before you do these steps because these steps cannot be reversed.
{% endhint %}

1. Make sure you export your current expressions. 
2. Now add your new expressions with the one that you just exported. \(Make sure you don't replace your backup that you just downloaded\).
3. Make sure that you have only unique expressions \(Using tools like Excel helps here\)
4. Delete all expressions from Chatlayer platform.
5. Import the new CSV you just created.
6. Update the NLP

With these steps, you should have all the expressions imported without any duplicates.

## Importing and exporting entities

Our platform also allows you to import and export **entities**. If you go to the 'Entities' module under NLP, you can import and export the entity values and the synonyms for these values.

All entity types will be included in the export.

![](../../.gitbook/assets/image%20%28302%29.png)

