# Translations

The 'Translations' module is used to manage translations for multilingual bots. 

This module automatically gathers all the strings that have to be translated or are language-dependent in other ways, like URLs. This includes all messages, random messages, button labels, carousel titles subtitles, URLs etc.

You can filter per column and combine filters too!

![](../../.gitbook/assets/image%20%28655%29.png)

### Translations import & export

By clicking the export button in the top right, you will receive an email containing a csv file of your translations. In this CSV, you will find:

* Flow id
* Dialog id
* Dialog name
* The component type, each separate component \(such as different buttons\) has a new row
* The translation for all of the languages of your bot

{% hint style="warning" %}
Two things to remember:

* Don't use this export to create new bot dialogs, just to change the translations of existing messages. 
* The translations of rich text messages will not be included in the export, use the interface to edit those.
{% endhint %}

It is recommend to use this export file as a basis for importing the translations. That way you have the correct format and all the ids needed for the import. The recommended steps for importing translations are:

* Click on 'Export' to export translations in the right upper corner
* Open de file received per email 
* Add the translations in the correct column, for example: for Dutch use 'value\_nl' column
* Leave the other columns as they are, those are needed for correct processing of the translations and save the file 
* Use the 'Import' button to import these translations, and choose the correct language in the pop-up
* Once imported, you will see a pending indicator whilst the import is still running
* When this indicator is gone, the import is complete. You can immediately see the translations in the translations tab and you do not need to update the NLP

You can choose to import one language at a time, and you do not need to do all translations at once. 

{% hint style="danger" %}
Importing / exporting translations will only work in the same bot. To get translations from bot A to bot B, look into importing and exporting [the entire bot](https://docs.chatlayer.ai/bot-answers/settings#bot-import-export).
{% endhint %}







