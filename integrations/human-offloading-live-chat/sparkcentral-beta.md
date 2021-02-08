# Sparkcentral

Sparkcentral allows you to manage all your asynchronous messaging channels with human and virtual customer service agents.

{% hint style="warning" %}
The Sparkcentral integration doesn't support the use of buttons yet.
{% endhint %}

## Retrieving Sparkcentral API credentials

The first step to integrate Sparkcentral with Chatlayer.ai is to retrieve API Credentials from Sparkcentral. 

* Go to your Sparkcentral dashboard and open the Settings page. 
* Once you’re on the settings page, select the Integrations tab in the sidebar. 

![](../../.gitbook/assets/image%20%28282%29.png)

* To retrieve your Sparkcentral API credentials click the Generate API Keys button in the top right corner of the screen. 

![](../../.gitbook/assets/image%20%28286%29.png)

* Enter a name for your API credentials and click the Save button. A new entry will now be visible in the Integrations page containing your clientId and clientSecret. Keep these credentials open and go back to Chatlayer.ai to start the Sparkcentral configuration.
* Go to the channels page in Chatlayer. Click the plus icon next to Sparkcentral to start the channel configuration. 
* Enter your clientId and clientSecret in the form and press save.

![](../../.gitbook/assets/image%20%28283%29.png)

* After saving, the webhook URL for your newly created channel is visible. Copy this Webhook URL and go back to sparkcentral.
* Return to your Sparkcentral dashboard and open the Settings page. Open the Users tab from the sidebar on the settings page and click the Add Virtual Agent button in the top right corner. This will open a popup allowing you to configure some details for the Virtual Agent. 
* Enter the webhook URL for your virtual Chatlayer.ai agent under the section Virtual Agent Configuration. 

![](../../.gitbook/assets/image%20%28287%29.png)

* Once the configuration is complete, copy the Shared Secret under Virtual Agent Configuration and save the new Virtual Agent.
* Go back to Chatlayer.ai, enter the shared webhook secret and save the channel configuration.
* Edit the virtual agent configuration of Sparkcentral to enable the channels you want your bot to be active on.

![](../../.gitbook/assets/image%20%28281%29.png)

## Configure offloading

To transfer the conversation from the chatbot to a live agent in Sparkcentral, you can create an Action dialog containing a "send to offload provider" plugin. Configure the Sparkcentral offload provider.

![](../../.gitbook/assets/image%20%28288%29.png)

Once this Action is triggered the conversation will be added to the Sparkcentral agent queue.

