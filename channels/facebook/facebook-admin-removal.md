# Facebook Admin Removal

If the person that created the initial page access token is removed as an admin from the Facebook page the bot is linked to, the page access token is invalidated, causing the bot not being authorized to post messages to the page any longer.

Chatlayer advises to test any changes to the developer apps and pages within Facebook within a testing environment before changing anything in the production environment.

## Resolving the issue

If you are currently experiencing this issue, follow the steps below.

1. In the Facebook Application on [http://developers.facebook.com](http://developers.facebook.com), go to "Products &gt; Messenger &gt; Settings" and scroll down to "Token Generation".
2. Select the right Facebook page and copy the Page Access Token![](https://mail.google.com/mail/u/1?ui=2&ik=bc20346786&attid=0.1&permmsgid=msg-f:1610849996652561580&th=165ae3898cea44ac&view=fimg&sz=w1600-h1000&attbid=ANGjdJ9Q2WudzrM5lqpXvkKhmvm_c49tXuVAuCuUd0LUneZ3XktQPf5tZldFNByvltwTU6Y7AGC5c8a-cCDfwK68zFyb3KL3MWLK9evw5FV6SMFuSuSAOy1BWLks1gI&disp=emb&realattid=ii_jlqdfyhu2_165ae38425d7c01b)
3. Within the Chatlayer platform, go to Settings
4. Change the Page Access Token by the one you copied from Facebook and click on the "Push to bot" button.

If these steps do not resolve the problem, please contact us through our [support channels](../../support/get-in-touch.md).

