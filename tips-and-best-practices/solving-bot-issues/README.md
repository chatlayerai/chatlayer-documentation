# Solving bot issues

Whenever your bot does not behave the way you expect it to, you will need to investigate to see exactly what the issue is. This is also called debugging. But where to start with debugging? How can you find what the cause of an issue is? This article will go through the basics of debugging in the  Chatlayer platform. Make sure to check the subpages on the left side, where some common issues in the Chatlayer platform are described and how to solve them.

## Emulator

Debugging can be done very easily in the emulator, this is the `Test your bot `window in the right bottom corner. The emulator consists of three parts:

### Test your bot

The main part of the emulator shows the bot response on the left side, and typed input from the user on the right side:

![](<../../.gitbook/assets/image (497).png>)

The following symbols are available for debugging:

![Open the specific bot dialog that gives that rep](<../../.gitbook/assets/image (492).png>)

![Repeat that particular bot dialog or user input](<../../.gitbook/assets/image (487).png>)

![Add that user input as an expression](<../../.gitbook/assets/image (493).png>)



Next to that, you can find the following options in this window:

![Open the Debugger tab](<../../.gitbook/assets/image (507).png>)

![Open the NLP Result tab](<../../.gitbook/assets/image (491).png>)

![Clear the entire conversation history and saved variables and start from scratch](<../../.gitbook/assets/image (504).png>)

![Choose the type of debugger window. Recommended is Debugger for the most information ](<../../.gitbook/assets/image (508).png>)

![Choose the language for this session in the emulator ](<../../.gitbook/assets/image (489).png>)

### Debugger tab

In the debugger you can find the following information:

![](<../../.gitbook/assets/image (502).png>)

`User says` the input the user has given

`Intent `the recognized intent

`Contexts `if any [contexts ](https://docs.chatlayer.ai/understanding-users/using-context)are active and what the lifespan is

`Bot dialog` with the id and name of the current dialog

`Read-Only Session data` This is all data that is retrieved up until this point in the session. If you need to use any of these variables, it is important that you add `internal.` before the variable. For example `internal.channel`

If there are any variables collected in the conversation along the way, they will be listed at the bottom. If you want to use these, `internal.` is not necessary

![](<../../.gitbook/assets/image (509).png>)

If you need to use any of the variables with a`  { }  `behind it, remember to use the correct variable name when you open the variable. For example` internal.currentDialogstate.name`

Below `Messages` (on the right side) you can see all the messages the bot has given up until that point.

### NLP Result tab

The NLP Result tab shows the result of the NLP engine. Any recognized intents or entities are shown here

![This expression gives a 93.86% positive score for the Book train ticket intent ](<../../.gitbook/assets/image (498).png>)

This information helps locating intent issues - if a wrong response is given in the bot, you can check here which intent was triggered.

![The word 'fries' gives a 100% match with the value 'fries' of the 'food' entity ](<../../.gitbook/assets/image (506).png>)
