# Single Sign-On (SAML SSO)

{% hint style="info" %}
Single Sign-On (SAML SSO) is only available in the Enterprise pack or higher. Want to upgrade? \
[Get in touch](../../support/get-in-touch.md).
{% endhint %}

By configuring Single Sign-On (SSO), your users can access Chatlayer through your organization's identity and access management (IAM) system. This is a secure and user-friendly way of accessing our platform.

Our SSO solution is compliant with SAML 2.0. This allows you to configure a wide range of IAM systems like:

* Azure Active Directory
* Okta
* OneLogin
* Ping Identity

## Azure AD

We'll guide you through the entire process of setting up SAML SSO through Azure Active Directory in a few steps. You can also find out more about the setup process on the [Azure AD documentation pages](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/add-application-portal-setup-sso).

### Creating an application

On the Azure portal ([https://portal.azure.com](https://portal.azure.com/#home)), go to the Azure Active Directory service.

![](<../../.gitbook/assets/image (537).png>)

Follow the "Enterprise applications" menu entry and create a new application

![](<../../.gitbook/assets/image (548).png>)

Press the "Create your own application" button. A form will appear. Give the new application a fitting name and select the Non-gallery option.

![](<../../.gitbook/assets/image (536).png>)

### Assigning users

[https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/add-application-portal-assign-users](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/add-application-portal-assign-users)

### Configuration in AD and Chatlayer

Next we'll set up Single sign-on. Select the Single sign-on menu entry and select SAML.

![](<../../.gitbook/assets/image (532).png>)

**1. Basic SAML Configuration** \
Edit the configuration and fill in the following fields:

* **Identifier (Entity ID):** `https://auth.chatlayer.ai/auth/realms/Chatlayer`
* **Reply URL (Assertion Consumer Service URL):** \
  Copy this value from the SAML SSO configuration screen in our platform.

![](<../../.gitbook/assets/image (550).png>)

**2. User Attributes & Claims** - Default values

**3. SAML Signing Certificate** - Download the Base64 certificate, open it with a text editor and copy the value into the "Public Certificate" field in the SAML SSO configuration screen in our platform.

**4. Set up Chatlayer**&#x20;

* **Login URL:** Copy this value into the "Sign on URL" field in our platform.
* **Azure AD Identifie**r: Copy this value into the "Issuer" field in our platform.\


![](<../../.gitbook/assets/image (540).png>)

![](<../../.gitbook/assets/image (534).png>)

You may now save the changes in both Azure AD and Chatlayer.&#x20;

It is now possible for members of your AD organization to login to the Chatlayer application.

&#x20;We do not currently offer role-mapping of Azure AD roles to Chatlayer roles. You can find out more about roles and access control on our [user management page](https://docs.chatlayer.ai/bot-answers/user-management).

## Okta

To set up SAML SSO through Okta, you can follow the steps below.

Step 1: Create a new app integration in Okta, select SAML 2.0

![](<../../.gitbook/assets/image (717).png>)

Step 2: give the newly created SAML 2.0 app a name

![](<../../.gitbook/assets/image (713).png>)

Step 3: fill in the Single sign on URL as retrieved from Chatlayer (Assertion consumer service URL) and the Audience URI (`https://auth.chatlayer.ai/auth/realms/Chatlayer`)

![](<../../.gitbook/assets/image (705).png>)

Step 4: Select the following settings in the 'Feedback' step of the Okta configuration

![](<../../.gitbook/assets/image (724).png>)
