# Single Sign-On \(SAML SSO\)

{% hint style="info" %}
Single Sign-On \(SAML SSO\) is only available in the Enterprise pack or higher. Want to upgrade?   
[Get in touch](../support/get-in-touch.md).
{% endhint %}

By configuring Single Sign-On \(SSO\), your users can access Chatlayer through your organization's identity and access management \(IAM\) system. This is a secure and user-friendly way of accessing Chatlayer.

Chatlayer's SSO solution is compliant with SAML 2.0. This allows you to configure a wide range of IAM systems like:

* Azure Active Directory
* Okta
* OneLogin
* Ping Identity

## Azure AD

We'll guide you through the entire process of setting up SAML SSO through Azure Active Directory in a few steps. You can also find out more about the setup process on the [Azure AD documentation pages](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/add-application-portal-setup-sso).

### Creating an application

On the Azure portal \([https://portal.azure.com](https://portal.azure.com/#home)\), go to the Azure Active Directory service.

![](../.gitbook/assets/image%20%28537%29.png)

Follow the "Enterprise applications" menu entry and create a new application

![](../.gitbook/assets/image%20%28548%29.png)

Press the "Create your own application" button. A form will appear. Give the new application a fitting name and select the Non-gallery option.

![](../.gitbook/assets/image%20%28536%29.png)

### Assigning users

[https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/add-application-portal-assign-users](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/add-application-portal-assign-users)

### Configuration in AD and Chatlayer

Next we'll set up Single sign-on. Select the Single sign-on menu entry and select SAML.

![](../.gitbook/assets/image%20%28532%29.png)

**1. Basic SAML Configuration**   
Edit the configuration and fill in the following fields:

* **Identifier \(Entity ID\):** `https://auth.chatlayer.ai/auth/realms/Chatlayer`
* **Reply URL \(Assertion Consumer Service URL\):**  Copy this value from the SAML SSO configuration screen in Chatlayer.

![](../.gitbook/assets/image%20%28539%29.png)

**2. User Attributes & Claims** - Default values

**3. SAML Signing Certificate** - Download the Base64 certificate, open it with a text editor and copy the value into the "Public Certificate" field in the SAML SSO configuration screen in Chatlayer.

**4. Set up Chatlayer** 

* **Login URL:** Copy this value into the "Sign on URL" field in Chatlayer.
* **Azure AD Identifie**r: Copy this value into the "Issuer" field in Chatlayer 

![](../.gitbook/assets/image%20%28540%29.png)

![](../.gitbook/assets/image%20%28534%29.png)

You may now save the changes in both Azure AD and Chatlayer. 

It is now possible for members of your AD organization to login to the Chatlayer application.

 



