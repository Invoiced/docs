
# SAML 2.0 (Single Sign-On)

Single sign-on (SSO) allows users to use a single login for multiple enterprise applications. The SAML 2.0 integration allows your team to sign in using your existing identity provider instead of the user's Invoiced username and password.

<p class="alert alert-warning">SAML 2.0 is only available in the Enterprise edition.</p>

## Setup

Within your identity provider follow these instructions:

1. Create a new SAML 2.0 application in your identity provider for Invoiced.

2. Enter in the below for the service URL:

   ```
   https://invoiced/auth/sso/sp/acs
   ```

3. Set the Audience field to `invoiced`.

4. Set the NameID field to the email address.

Now go to the Invoiced application:

1. Go to **Settings** &rarr; **Team** &rarr; **SSO**. If you do not see the SSO tab then contact support to have it enabled.

2. Click on the **Enable SSO** toggle.

3. Copy the certificate from the identity provider and paste it into the X.509 Certificate field.

4. Copy over the Issuer URL into the **Identity Provider Identifier or Issuer URL** field.

5. Copy over the Single Sign-On URL into the **Identity Provider Single Sign-On URL** field.

## Usage

Once SSO is properly configured, users can click the **Login with SSO** button on the login screen or [go here](https://app.invoiced.com/login/sso). The user will be required to enter in their email address. Assuming there is a match the user will then be signed in through their identity provider.

[![SSO Login Screen](/docs/img/login-with-sso.png)](/docs/img/login-with-sso.png)

<p class="alert alert-info">Identity Provider-Initiated Sign In is not supported. SSO logins must be initiated through our login page.</p>