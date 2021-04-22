# Translations

The 'Translations' module is used to manage translations for multilingual bots. Find more information on how to configure your multilingual bot here:

{% page-ref page="../../understanding-users/multilanguage-bots.md" %}

This module automatically gathers all the strings that have to be translated or are language-dependent in other ways, like URLs. This includes all messages, random messages, button labels, carousel titles subtitles, URLs ...

You can filter on each column and combine filters.

![](../../.gitbook/assets/image%20%28513%29.png)

### Translations import & export

By clicking the export button in the top right, you will receive an email containing a csv file of your translations. In this csv, you will find:

* Flow id
* Dialog id
* Dialog name
* The translation for each of the languages of your bot

{% hint style="warning" %}
Two things to take into account:

* Don't use this export to create new messages, just to change the translations of existing messages. 
* The translations of rich text messages will not be included in the export, use the interface to edit those.
{% endhint %}

