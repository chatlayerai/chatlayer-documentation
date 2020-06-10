# Facebook Webview Whitelisting

Facebook allows webviews to be shown within the conversation between a bot and a user. These webviews typically contain small applications that contain some logic that is not possible to show with the default Facebook templates - such as buttons and carousels.

If you add a webview for a Facebook Messenger bot, the domain that hosts this webview has to be whitelisted.

{% hint style="success" %}
Follow Facebook's instructions for whitelisting a domain [here](https://developers.facebook.com/docs/messenger-platform/reference/messenger-profile-api/domain-whitelisting/#page_settings).
{% endhint %}

Only the domains that you enter as a webview in Chatlayer.ai have to be whitelisted. You can add a webview by adding a button template, and adding a new button with the type `Webview`.

![](../../.gitbook/assets/image%20%28166%29.png)

Fill in this template with the right copy and URL, and optional parameters that are passed on to the webview.

![](../../.gitbook/assets/image%20%28239%29.png)

