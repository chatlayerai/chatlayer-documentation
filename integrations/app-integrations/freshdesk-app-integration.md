---
description: >-
  With the Freshdesk integration, users can submit a new ticket to your customer
  support service through a bot
---

# Freshdesk App integration

You can connect the Freshdesk app to Chatlayer by using the Action bot dialog. In this dialog, choose _Integration widget_, then under 'App', select _Freshdesk_ and click on 'Connect a new Freshdesk account'.

![](<../../.gitbook/assets/image (678) (1).png>)

After clicking on “Connect new account”, you’ll see this pop-up:

![](<../../.gitbook/assets/image (673).png>)

To find your Domain and API Key, please head to your profile page on Freshdesk:

![](<../../.gitbook/assets/image (674).png>)

The part of the URL inside the green rectangle is your account’s Domain. The green rectangle on the right highlights your API key.

After you've entered this info in the Chatlayer action dialog and the connection is set up, you’ll be able to pick the action you want to perform within this dialog:

· Create ticket

· Add notes to a ticket (update ticket)

· Add replies to a ticket (send an email to the user)

· Create contact (create new user)

![](<../../.gitbook/assets/image (677) (1) (1).png>)

### **Gathering information**

You'll need to ask the user for the information needed to create a new ticket, like for example, the user's name. You can do so with an 'Input Validation' dialog. By saving the user’s response as a variable, you'll be able to create a new ticket:

![Asking the user for their name](<../../.gitbook/assets/image (695) (1) (1).png>)

Next, your Actions could be as followed:

**1 – Create ticket**

![](<../../.gitbook/assets/image (690) (1).png>)

If your tickets have custom fields, you can also include them in the Action dialog state and request them thought the bot, as seen in "language" and "country" below:

![](<../../.gitbook/assets/image (706) (1).png>)

**2 – Add notes to a ticket**

![](<../../.gitbook/assets/image (687) (1) (1).png>)

**3 – Add replies to a ticket**&#x20;

![](<../../.gitbook/assets/image (679) (1).png>)

**4 – Create a contact**

![](<../../.gitbook/assets/image (681) (1).png>)

&#x20;And that's it, your Freshdesk connection is set up and ready to go!
