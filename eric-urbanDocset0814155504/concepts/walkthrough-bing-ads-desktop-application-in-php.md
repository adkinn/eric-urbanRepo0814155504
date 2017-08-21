---
title: "Walkthrough: Bing Ads Desktop Application in PHP"
ms.custom: ""
ms.date: "08/01/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5c2bbbd-42e7-49c9-9b04-1356e9adceda
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Walkthrough: Bing Ads Desktop Application in PHP
This guide describes how you can download samples from the [GitHub source](https://go.microsoft.com/fwlink/?linkid=838593), edit with your credentials, and run in a local console. 

> [!IMPORTANT] 
> Be sure to test in sandbox before running samples in production. Also note that some samples might require additional information e.g. within *ManageClient.php* you'll need to supply a valid $ClientAccountId.

For more information about getting started with PHP, please see [Setting Up the Development Environment](../concepts/getting-started-using-php-with-bing-ads-services.md#requirements). 


## <a name="desktopapp"></a>Desktop Application Example Walk-Through

1.  Download the Bing Ads examples or copy snippets as needed from the [GitHub source](https://go.microsoft.com/fwlink/?linkid=838593). For example open a command prompt and type `git clone https://github.com/BingAds/BingAds-PHP-SDK.git`. 
2.  Navigate to your local project directory e.g. *c:\dev\BingAdsPHP* and [install](getting-started-using-php-with-bing-ads-services#installation.md) the Bing Ads PHP SDK. You should now see the vendor directory which contains both the SDK source and samples. 
3.  Copy both *AuthHelper.php* and the *V11* directory (with included samples) to your local project directory e.g. copy from *c:\dev\BingAdsPHP\vendor\microsoft\bingads\samples* to *c:\dev\BingAdsPHP*.

    ![Sample PHP Project Directory](../concepts/media/sample-php-project-directory.PNG)  
    > [!NOTE]
    > You have alternative options for example, changing the path of *autoload.php* within *AuthHelper.php* and within each sample that you want to run. You could also write your application from scratch in the *c:\dev\BingAdsPHP* directory. 
    
4. Within the *AuthHelper.php* sample helper file, edit the *UserName*, *Password*, and *DeveloperToken* values to your own credentials. 
   > [!NOTE] 
   > To authenticate with OAuth you'll need a refresh token to get started. For details see [OAuth Refresh Token](#oauth).
5. Edit one of the samples e.g. *\V11\SearchUserAccounts.php*. Choose the authentication helper function that you will use, and comment out the other. 
   ```php
   // You should authenticate for Bing Ads production services with a Microsoft Account, 
   // instead of providing the Bing Ads username and password set. 
   
   //AuthHelper::AuthenticateWithOAuth();
   
   // However, authentication with a Microsoft Account is currently not supported in Sandbox,
   // so it is recommended that you set the UserName and Password in sandbox for testing.
   
   AuthHelper::AuthenticateWithUserName();
   ```
6. At the console command prompt run the sample e.g. at *c:\dev\BingAdsPHP* type `php .\V11\SearchUserAccounts.php`. 
   
## <a name="oauth"></a>OAuth Refresh Token
To authenticate with OAuth you'll need a refresh token to get started.
1. Within *AuthHelper.php*, edit the *ClientId* and *DeveloperToken* values to your own credentials. The *RedirectUri* should be set to *https://login.live.com/oauth20_desktop.srf*.
2. Edit one of the samples e.g. *\V11\SearchUserAccounts.php*. Choose the *AuthenticateWithOAuth* helper function that you will use, and comment out *AuthenticateWithUserName*. 
   ```php
   AuthHelper::AuthenticateWithOAuth();
   //AuthHelper::AuthenticateWithUserName();
   ```
3. At the console command prompt run the sample e.g. type `php .\V11\SearchUserAccounts.php`. 
4. You should be prompted to copy and paste the authorization URL into a web browser. The one time user consent is required, and thereafter you will be able to use the refresh token to request new access and refresh tokens.
5. After authorizing your application to manage your Bing Ads accounts, copy the resulting URL (with *code* parameter) and paste it into the console window. Then press the *Enter* (return) key to continue execution.
6. The refresh token will be written to *refresh.txt*. You can change the location by editing the *OAuthRefreshTokenPath* setting within *AuthHelper.php*.
   > [!IMPORTANT] 
   > This quick start example is not recommended in production. You should only store a Bing Ads user's refresh token in a secure location.
7. Subsequent calls to the *AuthenticateWithOAuth* helper function will attempt to read the refresh token from the same location. 
   

## See Also
[PHP Examples for Bing Ads](../concepts/php-examples-for-bing-ads.md)  
[Bing Ads Web Service Addresses](../concepts/bing-ads-web-service-addresses.md)  

