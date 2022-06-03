# Sparkcentral by Hootsuite

[Sparkcentral by Hootsuite](https://sparkcentral.com/) allows you to manage all your asynchronous messaging channels with human and virtual customer service agents.

## Retrieving Sparkcentral API credentials

The first step to integrate Sparkcentral with Chatlayer.ai is to retrieve API Credentials from Sparkcentral.&#x20;

* Go to your Sparkcentral dashboard and open the Settings page.&#x20;
* Once you’re on the settings page, select the Integrations tab in the sidebar.&#x20;

![](<../../.gitbook/assets/image (282).png>)

* To retrieve your Sparkcentral API credentials click the Generate API Keys button in the top right corner of the screen.&#x20;

![](<../../.gitbook/assets/image (674) (1) (1) (1) (1).png>)

* Enter a name for your API credentials and click the Save button. A new entry will now be visible in the Integrations page containing your clientId and clientSecret. Keep these credentials open and go back to Chatlayer.ai to start the Sparkcentral configuration.
* Go to the channels page in Chatlayer. Click the plus icon next to Sparkcentral to start the channel configuration.&#x20;
* Choose your region: US or EU
* Enter your clientId and clientSecret in the form and press save.

![](<../../.gitbook/assets/image (676) (1) (1) (1) (1).png>)

* After saving, the webhook URL for your newly created channel is visible. Copy this Webhook URL and go back to sparkcentral.
* Return to your Sparkcentral dashboard and open the Settings page. Open the Virtual Agents tab from the sidebar on the settings page and click the Add Custom Virtual Agent button in the top right corner. This will open a popup allowing you to configure some details for the Custom Virtual Agent.&#x20;
* Enter the webhook URL for your virtual Chatlayer.ai agent under the section Custom Virtual Agents Configuration.&#x20;

![](<../../.gitbook/assets/image (677) (1) (1) (1) (1) (1) (1).png>)

![](<../../.gitbook/assets/image (675) (1) (1).png>)

* Once the configuration is complete, copy the Shared Secret under Custom Virtual Agent Configuration and save the new Custom Virtual Agent.
* Go back to Chatlayer.ai, enter the shared webhook secret and save the channel configuration.
* Edit the virtual agent configuration of Sparkcentral to enable the channels you want your bot to be active on.

![](<../../.gitbook/assets/image (672) (1) (1) (1) (1).png>)

## Configure offloading

To transfer the conversation from the chatbot to a live agent in Sparkcentral, you can create an Action dialog containing a "send to offload provider" plugin. Configure the Sparkcentral offload provider.

![](<../../.gitbook/assets/image (288).png>)

Once this Action is triggered the conversation will be added to the Sparkcentral agent queue.

## Retrieve user details from Sparkcentral

You can find more information from user sessions connected to Sparkcentral channel under the following: &#x20;

{% hint style="info" %}
internal.channelDetails
{% endhint %}

```
// export interface SparkcentralSessionDetails {
  channelId: string;
  medium?: string;
  contactProfile?: {
    id: string;
    mediumContactProfileId: string;
    primaryIdentifier: string;
    secondaryIdentifier: string;
    pictureUrl: string;
    vip: boolean;
  };
  contactAttributes?: { attribute: string; value: string; source: string }[];
}
```

An example for the internal.channelDetails can be as follows:

```
{
 channelId: "12345",
  medium: "twit".
  contactProfile: {
    id: "0-01f116a7f9c-000-b5d575cb,
    mediumContactProfileId: "cd067e88519ab323b15c9944"
    primaryIdentifier: "user_email@test.com"
    secondaryIdentifier: "user_email@test.com"
    pictureUrl: "https://avatar_url.com";
    vip: false;
  };
  "contactAttributes": [
    {
      "attribute": "fb-page-title",
      "value": "In-Web Messaging Demo",
      "source": "MEDIUM"
    },
    {
      "attribute": "fb-page-url",
      "value": "https://messenger-demoapp-dev/#JansDevSmoochChannel4",
      "source": "MEDIUM"
    },
    {
      "attribute": "fb-browser-language",
      "value": "en-US",
      "source": "MEDIUM"
    },
    {
      "attribute": "fb-domain",
      "value": "messenger-demoapp-dev",
      "source": "MEDIUM"
    },
    {
      "attribute": "fb-sdk-version",
      "value": "1.14.2",
      "source": "MEDIUM"
    }
  ]
}
```

If you want to retrieve the profile url of the user then you can retrieve it by `internal.channelDetails.contactProfile.profileUrl`

