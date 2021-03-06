# Table of contents

* [Welcome to Chatlayer 👋](README.md)

## Getting started <a id="tutorials"></a>

* [Planning your bot](tutorials/getting-started.md)
* [Creating a new bot](tutorials/tutorial-getting-started.md)
* [Adding content to your bot](tutorials/tutorial-adding-content.md)
* [Detecting information in expressions](tutorials/tutorial-getting-information-using-entities.md)
* [Asking user info through input validation](tutorials/tutorial-request-and-use-information-using-input-plugins.md)
* [Flow navigation with variables](tutorials/tutorial-conditional-flow-navigation.md)

## Understanding users

* [Context](understanding-users/using-context.md)
* [Expression generator](understanding-users/expression-generator.md)
* [Multilingual bots](understanding-users/multilanguage-bots/README.md)
  * [Translations](understanding-users/multilanguage-bots/translations.md)
* [Natural Language Processing \(NLP\)](understanding-users/natural-language-processing-nlp/README.md)
  * [NLP threshold](understanding-users/natural-language-processing-nlp/settings.md)
  * [NLP import & export](understanding-users/natural-language-processing-nlp/nlp-import-and-export.md)
  * [Training your bot with actual user input](understanding-users/natural-language-processing-nlp/tutorial-train-your-bot-based-on-actual-user-messages.md)
  * [NLP Dashboard & NLP Improve](understanding-users/natural-language-processing-nlp/nlp-dashboard-and-nlp-improve.md)
  * [Entities](understanding-users/natural-language-processing-nlp/synonym-entities/README.md)
    * [Detecting information with match entities](understanding-users/natural-language-processing-nlp/synonym-entities/how-to-use-match-entities.md)
  * [Supported languages](understanding-users/natural-language-processing-nlp/supported-languages.md)

## Bot management <a id="bot-answers"></a>

* [Analytics](bot-answers/analytics/README.md)
  * [Definitions](bot-answers/analytics/definitions.md)
  * [Users](bot-answers/analytics/users.md)
  * [Conversations](bot-answers/analytics/conversations.md)
  * [User flow](bot-answers/analytics/user-flow.md)
  * [Intents](bot-answers/analytics/intents.md)
* [Bot dialogs](bot-answers/dialog-state/README.md)
  * [Bot message](bot-answers/dialog-state/message-components.md)
  * [Go To](bot-answers/dialog-state/plugins.md)
  * [Input Validation](bot-answers/dialog-state/user-input-bot-dialog.md)
  * [Action](bot-answers/dialog-state/action-bot-dialog.md)
* [Conversation history](bot-answers/user-messages.md)
* [Events](bot-answers/events.md)
* [Publishing your bot](bot-answers/publishing-your-bot/README.md)
  * [Publishing & platform URLs FAQ](bot-answers/publishing-your-bot/publishing-new.md)
* [Settings](bot-answers/settings/README.md)
  * [Variables](bot-answers/settings/secure-variables-gdpr.md)

## Organization Management

* [Access Control](organization-management/access-control/README.md)
  * [Single Sign-On \(SAML SSO\)](organization-management/access-control/single-sign-on-sso-saml.md)

## Integrations

* [API integration](integrations/custom-back-end-integrations/README.md)
  * [Advanced API integrations](integrations/custom-back-end-integrations/advanced-api-integrations.md)
* [Code Editor](integrations/code-action.md)
* [Human handover & live chat](integrations/human-offloading-live-chat/README.md)
  * [\#Interact](integrations/human-offloading-live-chat/interact.md)
  * [Genesys Cloud](integrations/human-offloading-live-chat/genesys-purecloud.md)
  * [Help Scout](integrations/human-offloading-live-chat/helpscout.md)
  * [Intercom](integrations/human-offloading-live-chat/intercom-integration.md)
  * [Offloading Webhook](integrations/human-offloading-live-chat/offloading-webhook.md)
  * [RingCentral Engage Digital](integrations/human-offloading-live-chat/ringcentral-engage-digital.md)
  * [Salesforce Service Cloud](integrations/human-offloading-live-chat/salesforce-service-cloud.md)
  * [Sinch Contact & Contact Pro](integrations/human-offloading-live-chat/sinch-contact.md)
  * [Sparkcentral by Hootsuite](integrations/human-offloading-live-chat/sparkcentral-beta.md)
  * [Zendesk Chat](integrations/human-offloading-live-chat/zendesk-chat.md)
  * [Zendesk Support Ticket](integrations/human-offloading-live-chat/creating-a-zendesk-support-ticket.md)
* [Message objects for APIs](integrations/chat-message-structure-for-apis.md)
* [Retrieving data from Airtable \(GET\)](integrations/retrieving-data-from-airtable-get.md)
* [Sending data to Airtable \(POST\)](integrations/airtable.md)

## Channels

* [Channels](channels/multi-channel.md)
* [Facebook Messenger](channels/facebook/README.md)
  * [Facebook Admin Removal](channels/facebook/facebook-admin-removal.md)
  * [Facebook Webview Whitelisting](channels/facebook/facebook-webview-whitelisting.md)
  * [Facebook Messenger API updates for Europe](channels/facebook/facebook-messenger-api-updates-for-europe.md)
* [Google Assistant](channels/google-assistant.md)
* [Phone & voice](channels/phone-and-voice.md)
* [Sinch Conversation API](channels/sinch-conversation-api-beta.md)
* [Web chat widget](channels/webwidget/README.md)
  * [Customize web widget](channels/webwidget/customize-web-widget.md)
  * [Live example web widget](channels/webwidget/live-example-web-widget.md)
* [Webhook Channel](channels/webhook-api.md)
* [WhatsApp Business API](channels/whatsapp.md)
* [Workplace from Facebook](channels/workplace-from-facebook.md)

## Chatlayer API

* [V1 API Reference](https://api.chatlayer.ai/v1/docs)

## Tips & Best practices

* [Bot templates](tips-and-best-practices/bot-templates/README.md)
  * [Bot flows](tips-and-best-practices/bot-templates/bot-flows.md)
* [Bot-building checklist](tips-and-best-practices/chatbot-checklist.md)
* [Creating diverse expressions](tips-and-best-practices/creating-diverse-expressions.md)
* [Guidelines for building a good bot](tips-and-best-practices/what-makes-a-good-chatbot.md)
* [NLP best practices](tips-and-best-practices/how-to-nlp.md)
* [Not understood bot dialog](tips-and-best-practices/not-understood-bot-dialog/README.md)
  * [Not understood counter](tips-and-best-practices/not-understood-bot-dialog/not-understood-counter.md)
  * [Go to previous bot dialog](tips-and-best-practices/not-understood-bot-dialog/go-to-previous-bot-dialog.md)
  * [Create specific not understood messages](tips-and-best-practices/not-understood-bot-dialog/intent-recognition-below-threshold.md)
  * [Not understood Google search](tips-and-best-practices/not-understood-bot-dialog/not-understood-google-search.md)
* [Solving bot issues](tips-and-best-practices/solving-bot-issues/README.md)
  * [1. No correct response](tips-and-best-practices/solving-bot-issues/1.-no-correct-response.md)
  * [2. Input validation not working](tips-and-best-practices/solving-bot-issues/2.-input-validation-not-working.md)
  * [3. Video isn't working](tips-and-best-practices/solving-bot-issues/3.-media-upload-not-working.md)
* [Voice design](tips-and-best-practices/voice-design/README.md)
  * [From chat to voice](tips-and-best-practices/voice-design/from-chat-to-voice.md)

## Tutorials <a id="tutorials-1"></a>

* [Create a web widget demo page](tutorials-1/web-widget-demo-page.md)
* [Gathering user feedback](tutorials-1/gathering-user-feedback.md)
* [Recognizing a returning user](tutorials-1/how-to-recognize-a-returning-bot-user.md)
* [Reusing flows](tutorials-1/reuse-flows.md)
* [Using time in your chatbot](tutorials-1/using-time-in-your-chatbot.md)

## Support

* [Billing & subscription](support/billing-and-subscription.md)
* [Frequently Asked Questions \(FAQ\)](support/frequently-asked-questions.md)
* [Get in touch](support/get-in-touch.md)
* [Platform Glossary](support/glossary.md)
* [SaaS Regions & IP Ranges](support/saas-regions-and-ip-ranges.md)
* [Status](https://status.chatlayer.ai/)
* [What's new](support/whats-new/README.md)
  * [New documentation](support/whats-new/documentation.md)

