# Authentiq OpenID Connect Registration Handler for Salesforce

Registration handler for using Authentiq as a Salesforce OpenID provider.

Follow these steps to register [Authentiq](https://www.authentiq.com/developers/?utm_source=github&utm_medium=readme&utm_campaign=authentiq-salesforce-registration-handler) as an authentication provider for your Salesforce domain, so that your users can sign in to Salesforce using their Authentiq ID.

## Set up your Salesforce domain

![Domain management](https://github.com/AuthentiqID/authentiq-salesforce-registration-handler/blob/master/images/1-domain-management.png)

In your Salesforce dashboard, in the lefthand column, select **Domain Management** under **Administration Setup** and make sure you have a domain set up here. If not, follow [these directions](https://help.salesforce.com/articleView?err=1&id=domain_name_setup.htm&type=5) from Salesforce to set up a domain.


## Create registration handler

![Apex classes](https://github.com/AuthentiqID/authentiq-salesforce-registration-handler/blob/master/images/8-apex-classes.PNG)

To create a registration handler for Authentiq, go to the **Apex Classes** menu in the left column of your Salesforce dashboard.

Press **New** and you should be presented with a text editor.

![Apex editor](https://github.com/AuthentiqID/authentiq-salesforce-registration-handler/blob/master/images/9-apex-editor.PNG)

Copy and paste the raw code of the [latest Authentiq Registration Handler](https://github.com/AuthentiqID/authentiq-salesforce-registration-handler/blob/master/AuthentiqRegistrationHandler.apxc) in the editor and press **Save**.

## Create an new authentication provider

![Security controls](https://github.com/AuthentiqID/authentiq-salesforce-registration-handler/blob/master/images/2-security-controls.png)

Now select **Security Controls** under **Administration Setup** and click through to **Manage Authentication Providers**. 

![Manage Authentication Providers](https://github.com/AuthentiqID/authentiq-salesforce-registration-handler/blob/master/images/3-manage-authentication-providers.PNG)

If you don’t have an authentication provider set up then this list will be empty. 

![New provider](https://github.com/AuthentiqID/authentiq-salesforce-registration-handler/blob/master/images/5-new-auth-provider.png)

Press **New** and select **Open ID Connect** from the drop down, then use the following data to fill out the form.

|Field|Value|
|---|---|
|Name|`Authentiq`|
|URL Suffix|`authentiq`|
|Consumer Key|Your Client ID from the [Authentiq Dashboard](https://dashboard.authentiq.com/)|
|Consumer Secret|Your Client Secret from the [Authentiq Dashboard](https://dashboard.authentiq.com/)|
|Authorize Endpoint URL|`https://connect.authentiq.io/authorize`|
|Token Endpoint URL|`https://connect.authentiq.io/token`|
|User Info Endpoint URL|`https://connect.authentiq.io/userinfo`|
|Token Issuer|Leave this blank|
|Default Scopes|`openid aq:name~r email~rs phone~s address aq:push`|
|Send access token in header|`Checked`|
|Send client credentials in header|`Unchecked`|
|Custom Error URL|Leave this blank|
|Custom Logout URL|Leave this blank|
|Registration Handler|The Registration Handler you created above|
|Execute Registration As|The user you want to use to issue new registrations|
|Icon URL|`http://cdn.authentiq.io/logos/small/app-icon-hexagon.png`|

![Filled form without handler](https://github.com/AuthentiqID/authentiq-salesforce-registration-handler/blob/master/images/7-filled-form-without-handler.PNG)

Towards the bottom, press the magnifying lens next to the **Registration Handler** field. In the pop-up window, select the `AuthentiqRegistrationHandler` you created earlier. 

![Select handler](https://github.com/AuthentiqID/authentiq-salesforce-registration-handler/blob/master/images/11-select-registration-handler.PNG)

Now select the magnifying lens next to the **Execute Registration As** input field and select the account that you would like to use to perform the registrations as.

Save your new **Authentication Provider**.

![Providers list](https://github.com/AuthentiqID/authentiq-salesforce-registration-handler/blob/master/images/4-authentication-providers-list.PNG)

## Log in with Authentiq!

In a private browser window, navigate to your Salesforce domain/website. You should now have the option to sign in with Authentiq below the regular username & password form.

![Login with AuthentiqID](https://github.com/AuthentiqID/authentiq-salesforce-registration-handler/blob/master/images/12-login.PNG)

Press **Log in using Authentiq**, scan the QR code with your [Authentiq ID](https://www.authentiq.com/how-it-works/), and you're in!
