# Solving bot issues

There are a couple of problems you might encounter as a starting bot developer. In this article you will learn how to find and fix the most common bot problems.

## 1 – Your user asks a question, your bot doesn't give the correct response

* Open the `Test your bot`  window and type the expression that returns the unexpected result
* Go to the `NLP result` tab
* Check to see if an intent was detected with a confidence above the [threshold](../understanding-users/natural-language-processing-nlp/settings.md) \(the default threshold is 80%\)

### If an intent was detected with &gt; 80% confidence

* Go to the bot dialogs table view
* Filter on the intent that was detected
* If there is no result for that intent, it means that your intent doesn't have an answer linked to it, which will mean the bot defaults to `not understood`
  * **Solution:** configure an answer to  the intent by adding a new bot message, and linking the intent to it
* If there is a bot dialog that has that intent linked to it, click it 
  * **Solution:** configure the bot message linked to the intent and make sure it's aligned with how you want the bot to reply. Alternatively, if the intent should not be linked to that bot message, remove the link between bot dialog and intent and create a new bot dialog for that intent

### If no intent was detected with &gt; 80% confidence

* Check your NLP model. Does an intent already exist where this expression might belong to?
* If yes, add the expression to the model, click `Update NLP` and test your bot again
* If no, create a new intent, add the expression and a few others like it to the new intent and update your NLP model

{% hint style="info" %}
Make sure you follow our [NLP training best practices](how-to-nlp.md) when creating new intents and expressions.
{% endhint %}

* Create a new bot dialog, link the intent to that bot dialog, and define an answer the bot should give as a reply to your new intent



