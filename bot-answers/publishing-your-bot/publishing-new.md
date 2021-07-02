# Publishing & platform URLs FAQ

In one of our previous platform updates, we have released a new version of Chatlayer that makes handling the live and draft versions of your bot much easier. Older customers may still know [cms.staging.chatlayer.ai](http://cms.staging.chatlayer.ai/) instead of [app.chatlayer.ai](http://app.chatlayer.ai/).

We’re introducing the [app.chatlayer.ai](http://app.chatlayer.ai/) URL that unifies everything that’s used to be on the [cms.staging.chatlayer.ai](http://cms.staging.chatlayer.ai/) and the [cms.chatlayer.ai](http://cms.chatlayer.ai/) URLs.

## Why are we changing this? 

We’ve received a few support tickets by customers accidentally making changes to their live bots when they wanted to do so in the staging environment. And we get it, it’s too easy to make mistakes in a URL! We also think it’s quite a hassle to remember which URL hosts which environment, especially if you’re a new Chatlayer user.

## So, what has changed?

### Chatlayer URL

Instead of having a separate URL for Staging & Production, we now have 1 URL for everything: [app.chatlayer.ai](http://app.chatlayer.ai/). You can manage both the live & draft versions of your bot through this URL.

{% hint style="info" %}
Now when you open a bot on [app.chatlayer.ai](http://app.chatlayer.ai/), it will open the DRAFT version of that bot. Go to the 'publish' tab to, well, publish your bot.
{% endhint %}

### Publishing a bot

We’ve renamed the “Versioning” tab to “Publish”. When you’re ready to publish a newer version of the bot, just click the “Publish” button and follow the steps in the platform.

### Editing your LIVE bot

We recommend against changing the LIVE version of the bot directly. However, in some cases, if you need to make some quick changes without publishing an entirely new version, it can be useful. To change the LIVE version of the bot, go to the “Publish” page. On this page, look for the LIVE version of the bot on the right and click the “Open live mode” button.

![](../../.gitbook/assets/image%20%28517%29.png)

### Channels

Your bot can still connect to draft and live channels separately, exactly like you’re doing now in the Staging and Production environments. However, we want to give a better overview, so we’re consolidating all your channels into one single table.

![](../../.gitbook/assets/image%20%28516%29.png)

### Conversations

Only one small change on the conversations page: both LIVE and DRAFT conversations are now visible within the same table. You can filter in this table to show either one.

### Bot export

When you export a bot, you can now choose between exporting the LIVE or DRAFT version of that bot.

## What is not changing?

Your workflow will remain the same: you can publish a new version of the bot from draft to live whenever it’s ready.

The Chatlayer API URLs will not change.

## FAQ

* Am I losing my staging environment?

No, the databases and infrastructure between the staging and production environments have been the same for over a year already. We are just merging the URLs. Your workflow remains the same: you can publish a new version from draft to live whenever it’s ready.

* Will the old URLs \(using ‘cms’\) still work?

The ‘cms’ URLs will continue to work for now. At some point in the future we will redirect them to [app.chatlayer.ai](http://app.chatlayer.ai/) URLs. There will be no change to the URLs that you use in your APIs.

* What do I have to change to my account or bot?

Nothing! Your workflow will remain the same: you can publish a new version of the bot from draft to live whenever it’s ready. The Chatlayer API URLs will not change.

* Will there be any downtime of the bots during or after the release?

We have been secretly preparing for this release for a long time, so in the background, everything has been merged already. This means that this change isn’t actually a really big one. Hence, we do not expect any downtime during or after the release of your bot.

* What will happen to the analytics dashboard?

If you have a live version of your bot, we will show you the stats from that live version. If you don’t, we will show some sample data in the analytics dashboard.

* What should I do if I still have questions?

If you have any questions about your bot specifically, feel free to [reach out to us](http://support.chatlayer.ai/).

