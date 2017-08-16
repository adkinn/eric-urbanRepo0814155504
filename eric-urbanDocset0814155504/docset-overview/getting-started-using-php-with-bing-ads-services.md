---
title: "Getting Started Using PHP with Bing Ads Services"
ms.custom: na
ms.date: "07/31/2017"
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: "article"
ms.assetid: 0176d1b0-5dbd-420e-967e-fd7dcb8af6b4
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Getting Started Using PHP with Bing Ads Services
To get started developing Bing Ads applications with PHP, [install the SDK](#installation) and either start with the provided examples at [GitHub](https://github.com/BingAds/BingAds-PHP-SDK/) or follow one of the application walkthroughs for a [Web](Walkthrough:%20Bing%20Ads%20Web%20Application%20in%20PHP.md) or [Desktop](Walkthrough:%20Bing%20Ads%20Desktop%20Application%20in%20PHP.md) application. You can also browse the [PHP Examples for Bing Ads](../docset-overview/php-examples-for-bing-ads.md) on MSDN. The examples have been developed with the Bing Ads PHP SDK in the environment described below. Your custom configuration may vary.

> [!NOTE]
> Please note the deprecated [PHP Classes for Bing Ads API examples](http://go.microsoft.com/fwlink/?LinkId=329042) will be removed from MSDN at the end of October, so when you [migrate to API version 11](../docset-overview/migrating-to-bing-ads-api-version-11.md) you should [upgrade](#upgrade) to the new SDK.
> 
> Unlike other Bing Ads SDKs, the PHP SDK does not suppport *BulkServiceManager* or *ReportingServiceManager*. 

-   [Setting Up the Development Environment](#requirements)  
-   [Installing the SDK](#installation)  
-   [Walkthroughs](#walkthrough)  
-   [Using AuthorizationData](#authorizationdata)  
-   [Using OAuth](#oauth)  
-   [Using ServiceClient](#serviceclient)  
-   [Exception Handling](#exceptionhandling)  
-   [Configuring Sandbox](#sandbox)  
-   [Upgrade from Deprecated Examples](#upgrade)  

## <a name="requirements"></a>Setting Up the Development Environment
You need user credentials with access to [!INCLUDE[brand](../docset-overview/includes/brand.md)] either in production or sandbox. You also need a developer token. For more information, please see [Getting Started With the Bing Ads API](../docset-overview/getting-started-with-the-bing-ads-api.md) and [Sandbox](../docset-overview/sandbox.md).

To authenticate with a [Microsoft Account](https://account.microsoft.com/account) in production, the Microsoft account user must [sign up](https://secure.azure.bingads.microsoft.com/Auth) or [manage](../docset-overview/customer-accounts.md#managingusers) an existing [!INCLUDE[brand](../docset-overview/includes/brand.md)] account. You also must [register](../docset-overview/authentication-with-oauth.md#registerapplication) an application and get the corresponding client identifier. You also need to take note of the client secret and redirect URI if you are developing a web application. For authentication details, see [Using OAuth](#oauth) below.

The examples provided at [GitHub](https://github.com/BingAds/BingAds-PHP-SDK/) and the examples within [PHP Examples for Bing Ads](../docset-overview/php-examples-for-bing-ads.md) have been developed and run in a similar environment as described below. Your custom configuration may vary.

-   PHP 5.6.30 has been installed from [PHP](http://go.microsoft.com/fwlink/?LinkID=103371&clcid=0x409).

    You should be able to use other versions of PHP, packages, and operating systems. However, certain parts of the code and configuration might have to be changed. For information about how to set up a PHP development environment to use web services, see the documentation for your tools.

-   The SOAP and OpenSSL extensions are included in the PHP.ini file. The curl extension is also enabled to run the bulk upload samples.

    ```
    extension=php_soap.dll
    extension=php_openssl.dll
    extension=php_curl.dll
    ```

## <a name="installation"></a>Installing the SDK
You can install the Bing Ads PHP SDK using the [Composer](https://getcomposer.org/doc/00-intro.md#introduction) package manager to fetch from [Packagist](https://packagist.org/packages/microsoft/bingads), or you can clone the source from [GitHub](https://github.com/BingAds/BingAds-PHP-SDK/). This guide describes how you can use Composer to get the latest version of the Bing Ads PHP SDK. 

1.  Download and install [Composer](https://getcomposer.org/doc/00-intro.md#introduction). Microsoft Windows users should also add composer.phar to your *PATH* variable.

2.  Open a command prompt and type `composer require microsoft/bingads`. 

    > [!NOTE]
    > Windows users who did not add *composer.phar* to the *PATH* will need to type `php composer.phar require microsoft/bingads` instead.

3.  To get updates going forward, type `composer update`. If any updates are available at packagist, composer will install the latest version.

## <a name="walkthrough"></a>Walkthroughs
Once you have the Bing Ads PHP SDK installed you can either browse the [PHP Examples for Bing Ads](../docset-overview/php-examples-for-bing-ads.md), download the examples at [GitHub](https://github.com/BingAds/BingAds-PHP-SDK/), or follow one of the application walkthroughs for a [Web](Walkthrough:%20Bing%20Ads%20Web%20Application%20in%20PHP.md) or [Desktop](Walkthrough:%20Bing%20Ads%20Desktop%20Application%20in%20PHP.md) application.

## <a name="authorizationdata"></a>Using AuthorizationData
You must initialize a new instance of [ServiceClient](#serviceclient) with *AuthorizationData*. The *AuthorizationData* class contains properties that [!INCLUDE[brand](../docset-overview/includes/brand.md)] uses to authorize a user. 

The following code block shows how to create an instance of *AuthorizationData* and set its *Authentication*, *CustomerId*, *AccountId*, and *DeveloperToken* properties.

```php
$authorizationData = (new AuthorizationData())
    ->withAuthentication($AuthenticationGoesHere)
    ->withCustomerId($CustomerIdGoesHere)
    ->withAccountId($AccountIdGoesHere)
    ->withDeveloperToken($DeveloperTokenGoesHere);
```
The *Authentication* property must be set to an Authentication-derived class such as *OAuthWebAuthCodeGrant*, *OAuthDesktopMobileAuthCodeGrant*, *OAuthDesktopMobileImplicitGrant*, or *PasswordAuthentication*.

> [!NOTE]
> Some services such as Customer Management do not accept *CustomerId* and *CustomerAccountId* headers, so they will be ignored if you specified them in the *AuthorizationData* object.

## <a name="oauth"></a>Using OAuth
The OAuth classes in the SDK abstract the low level user authorization details, so you can focus at a high level on your security requirements. The SDK objects take care of low level details such as formatting the authorization and redirect URIs, setting the request headers, and parsing the redirect traffic and response stream.

To use OAuth with the Bing Ads PHP SDK, the *Authentication* property of your *AuthorizationData* object must be set to an Authentication-derived class such as *OAuthWebAuthCodeGrant*, *OAuthDesktopMobileAuthCodeGrant* or *OAuthDesktopMobileImplicitGrant*. For repeat or long term authentication, you should follow the authorization code grant flow for obtaining an access token. This is a standard OAuth 2.0 flow and is defined in detail in the [Authorization Code Grant section of the OAuth 2.0 spec](http://tools.ietf.org/html/draft-ietf-oauth-v2-15#section-4.1). The steps below describe the procedural workflow, and references code blocks from the [Walkthrough: Bing Ads Web Application in PHP](Walkthrough:%20Bing%20Ads%20Web%20Application%20in%20PHP.md). For more information both about authorization code and implicit grant flows, see [Authentication with OAuth](../docset-overview/authentication-with-oauth.md).

1.  Create an instance of *OAuthWebAuthCodeGrant*, that will be used to manage Microsoft Account user authorization. Replace *ClientId*, *ClientSecret*, and *RedirectUri* with the values configured in [Registering Your Application](../docset-overview/authentication-with-oauth.md#registerapplication).

    ```php
    // Prepare the OAuth object for use with the authorization code grant flow. 
    // It is recommended that you specify a non guessable 'state' request parameter to help prevent
    // cross site request forgery (CSRF). 
    $authentication = (new OAuthWebAuthCodeGrant())
        ->withClientId(ClientId)
        ->withClientSecret(ClientSecret)
        ->withRedirectUri('https://' . $_SERVER['HTTP_HOST'] . RedirectUri)
        ->withState(rand(0,999999999)); 
    
    // Assign this authentication instance to the global authorization_data. 

    $_SESSION['AuthorizationData'] = (new AuthorizationData())
        ->withAuthentication($authentication)
        ->withDeveloperToken(AuthHelper::DeveloperToken);
    
    $_SESSION['state'] = $_SESSION['AuthorizationData']->Authentication->State;
    ```

2.  Request user consent by connecting to the Microsoft Account authorization endpoint through a web browser. Call the *GetAuthorizationEndpoint* method of the *OAuthWebAuthCodeGrant* instance that you created in the earlier step.

    ```php
    // The user needs to provide consent for the application to access their Bing Ads accounts.
    header('Location: '. $_SESSION['AuthorizationData']->Authentication->GetAuthorizationEndpoint());
    ```
    
    The user will be prompted through the Microsoft Account authorization web browser control to grant permissions for your application to manage their [!INCLUDE[brand](../docset-overview/includes/brand.md)] accounts.
    
    The authorization service calls back to your application with the redirection URI, which includes an authorization code if the user authorized your application to manage their [!INCLUDE[brand](../docset-overview/includes/brand.md)] accounts. For example the callback Url includes an authorization code as follows if the user granted permissions for your application to manage their [!INCLUDE[brand](../docset-overview/includes/brand.md)] accounts: *https://contoso.com/redirect/?code=CODE&state=ClientStateGoesHere*. If the user granted your application permissions to manage their [!INCLUDE[brand](../docset-overview/includes/brand.md)] accounts, you should use the code right away in the next step. The short duration of the authorization code, for example 5 minutes, is subject to change.
    
    If the user denied your application permissions to manage their [!INCLUDE[brand](../docset-overview/includes/brand.md)] accounts, the callback URI includes an error and error description field as follows: *REDIRECTURI?error=access_denied&error_description=ERROR_DESCRIPTION&state=ClientStateGoesHere*.

3.  Use the authorization code to request the access token and refresh token. Pass the full callback Url to the *RequestOAuthTokensByResponseUri* method of your *OAuthWebAuthCodeGrant* instance. This method uses the authorization code fragment to request the access token and refresh token.

    ```php
    if($_GET['code'] != null)
    {   
        // Verify whether the 'state' value is the same random value we created
        // when the authorization request was initiated.
        if ($_GET['state'] != $_SESSION['state'])
        {
            throw new Exception(sprintf(
                "The OAuth response state (%s) does not match the client request state (%s)", 
                $_GET['state'], 
                $_SESSION['state']));
        }   
        
        $_SESSION['AuthorizationData']->Authentication->RequestOAuthTokensByResponseUri($_SERVER['HTTP_HOST'] . $_SERVER['REQUEST_URI']);
                
        header('Location: '. '/CallBingAdsServices.php');
    }
    ```
    
    If this step succeeded, your application has permissions to manage the user's [!INCLUDE[brand](../docset-overview/includes/brand.md)] accounts. To call [!INCLUDE[brand](../docset-overview/includes/brand.md)] services, you should initialize the ServiceClient with *AuthorizationData* that contains your *OAuthWebAuthCodeGrant* instance.
    
    For more information, see [Using AuthorizationData](#authorizationdata) and [Using ServiceClient](#serviceclient).

4.  You will need to get a new refresh token on a regular basis, e.g. once per hour. You can refresh the *AccessToken*, *RefreshToken*, and *ExpiresIn* values from the *OAuthTokens* property of your *OAuthWebAuthCodeGrant* instance by calling *RequestAccessAndRefreshTokens*. It is important to save the most recent refresh token whenever new OAuth tokens are received.
    
    ```php
    $_SESSION['AuthorizationData']->Authentication->RequestOAuthTokensByRefreshToken($refreshToken);
    ```
  
    > [!NOTE] 
    > Whereas the refresh token parameter does not have a defined expiration period, you should expect it to last several months. 
    
    You may need to start again from Step 1 and request user consent if, for example the Microsoft Account user changed their password, removed a device from their list of trusted devices, or removed permissions for your application to authenticate on their behalf.

## <a name="serviceclient"></a>Using ServiceClient
You can use a single instance of the *ServiceClient* class to call any methods in the service, for example you can set the *CustomerManagementVersion11* service client type as follows.

```php
$customerProxy = new ServiceClient(ServiceClientType::CustomerManagementVersion11, $authorizationData, ApiEnvironment::Production);
)
```

Depending on the *Authentication* type specified in [AuthorizationData](#authorizationdata), the corresponding [Service Request Header](../docset-overview/authentication-with-oauth.md#serviceheaders) fields are set when you create a new *ServiceClient*. For example if you use the *OAuthWebAuthCodeGrant* authentication type, the *AuthenticationToken* service request header will be set. If you use *PasswordAuthentication*, the *UserName* and *Password* headers will be set instead of *AuthenticationToken*.


## <a name="exceptionhandling"></a>Exception Handling
In addition to handling PHP framework exceptions, your application should be prepared to handle Bing Ads API service level exceptions and Bing Ads PHP SDK wrapper exceptions. 

Bing Ads API service level exceptions include AdApiFaultDetail, ApiBatchFault, ApiFault, ApiFaultDetail, and EditorialApiFaultDetail. For more information, see [Handling Service Errors and Exceptions](../docset-overview/handling-service-errors-and-exceptions.md). 

You should also handle the *OAuthTokenRequestException*, which is thrown if an error was returned from the Microsft Account authorization server. To resolve this exception you can first check the stack trace to see the error details, in case there is some action you can take to resolve the issue. For example you might have specified an invalid client ID. 



## <a name="sandbox"></a>Configuring Sandbox
The sandbox endpoint is used by [ServiceClient](#serviceclient) by default. In the snippet below it is explicitly set to sandbox. To use the production environment instead, set it to production i.e. *ApiEnvironment::Production*.

```php
$customerProxy = new ServiceClient(ServiceClientType::CustomerManagementVersion11, $authorizationData, ApiEnvironment::Sandbox);
```

## <a name="upgrade"></a>Upgrade from Deprecated Examples
Please note the deprecated [PHP Classes for Bing Ads API examples](http://go.microsoft.com/fwlink/?LinkId=329042) will be removed from MSDN at the end of October, so when you [migrate to API version 11](../docset-overview/migrating-to-bing-ads-api-version-11.md) you should use the new SDK.

### <a name="autoload"></a>Use Autoloading
The deprecated samples explicity included each proxy file.

```php
include 'bingads\v11\CampaignManagementClasses.php'; 
include 'bingads\ClientProxy.php'; 
```

With the new SDK it is recommended and expected that you use autoloading i.e. require *autoload.php*. 

```php
require_once "/../vendor/autoload.php";
```


### <a name="namespace"></a>Update the Namespace
The deprecated samples did not prefix the namespace with *Microsoft*.

```php 
use BingAds\v11\CampaignManagement\AddCampaignsRequest; 
```

With the new SDK you must use the *Microsoft*. 

```php
use \Microsoft\BingAds\v11\CampaignManagement\AddCampaignsRequest;
```

### <a name="namespace"></a>Upgrade from ClientProxy to ServiceClient
The deprecated samples shipped with a *ClientProxy* class that you could use to construct SOAP messages and call the web services.

```php 
$GLOBALS['CampaignProxy'] = ClientProxy::ConstructWithAccountAndCustomerId( 
        $GLOBALS['CampaignWsdl'],  
        $GLOBALS['UserName'],  
        $GLOBALS['Password'],  
        $GLOBALS['DeveloperToken'],  
        $GLOBALS['AccountId'],  
        $GLOBALS['CustomerId'], 
        null); 
```

The new SDK you should use the *ServiceClient* class instead. For more details see [Using ServiceClient](#serviceclient) and [Using AuthorizationData](#authorizationdata).

```php
$campaignProxy = new ServiceClient(ServiceClientType::CampaignManagementVersion11, $authorizationData, ApiEnvironment::Production);
```

## See Also
[Sandbox](../docset-overview/sandbox.md)  
[PHP Examples for Bing Ads](../docset-overview/php-examples-for-bing-ads.md)  
[Bing Ads Web Service Addresses](../docset-overview/bing-ads-web-service-addresses.md)  
