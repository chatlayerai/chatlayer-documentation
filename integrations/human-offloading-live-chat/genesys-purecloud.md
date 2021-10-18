---
description: >-
  Learn how to setup your Chatlayer chatbot with Genesys Cloud (formerly Genesys
  PureCloud) for human handover
---

# Genesys Cloud

In the Genesys Cloud platform, go to Admin > Integrations > OAuth

![](<../../.gitbook/assets/image (220).png>)

Add a new OAuth client for Chatlayer.ai to use

![](<../../.gitbook/assets/image (97).png>)

Pick an app name and description. Leave the token duration untouched and pick the Client Credentials grant type.

![](<../../.gitbook/assets/image (146).png>)

On the roles tab, assign all roles

![](<../../.gitbook/assets/image (36).png>)

Copy the newly created client id and client secret to your Genesys Cloud Offloading integration in Chatlayer

![](<../../.gitbook/assets/image (154).png>)

![](<../../.gitbook/assets/image (183).png>)

### Create the widget deployment

Create a new Widget by going to **Admin > Contact Center > Widgets > Create Widget**

****

![](<../../.gitbook/assets/image (12).png>)

Copy the deployment key to the offloading configuration screen in Chatlayer.

![](<../../.gitbook/assets/image (225).png>)

## Sending a user to Genesys Cloud

To have your user transferred to a live agent in Genesys Cloud, create an action at the point in the flow where you want your user to be handed over.

![](<../../.gitbook/assets/image (159).png>)

Add the action "Send to offload provider" to your bot dialog and configure it with the correct settings for Genesys Cloud.

Select the queue for your chatbot conversations to be offloaded into.

![](<../../.gitbook/assets/image (70).png>)

Once a user reaches this part of the conversation, the offload towards Genesys Cloud will be triggered. The bot will automatically be paused when a user reaches this action. When the agent closes the conversation, the bot will be resumed. 

### User Information and Custom Fields

When the conversations reaches a human handover dialog for Genesys Cloud, Chatlayer will fill in the following information about your user using variables if they are available in the chat session:

**First Name**: `genesysCloud.firstName` OR `internal.user.firstName`\
**Last Name**: `genesysCloud.lastName` OR `internal.user.lastName`\
**Phone** **Number**: `genesysCloud.phoneNumber`\
**Email**: `genesysCloud.email`

You may want to pass additional information about the user to Genesys, not covered in the above fields. To handle this, you can declare additional session variables under the `genesysCloud.customFields` namespace. These will be added as custom fields in Genesys Cloud. 

For example, to add the user's location as a custom field, you would adjust your bot's flow to ask the user's location, and store the answer as a variable under `genesysCloud.customFields.location`
