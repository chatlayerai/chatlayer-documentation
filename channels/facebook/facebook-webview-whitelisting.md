# Facebook Webview Whitelisting

Facebook allows webviews to be shown within the conversation between a bot and its user. These webviews are typically made of small applications that contain logic that is not possible to show within the default Facebook templates – like buttons and carousels.

{% hint style="success" %}
If you add a webview to a Facebook Messenger bot, the domain that hosts this webview has to be whitelisted. But only the domains that you enter as a webview on our platform have to be whitelisted.

Follow Facebook's instructions for whitelisting a domain [here](https://developers.facebook.com/docs/messenger-platform/reference/messenger-profile-api/domain-whitelisting/#page_settings).
{% endhint %}

You can add a webview by adding a button template, and adding a new button with the type `Webview`.

![](../../.gitbook/assets/image%20%28166%29.png)

Fill in this template with the right copy and URL and optional parameters that are passed on to the webview.

![](../../.gitbook/assets/image%20%28239%29.png)

