---
title: "Server Side OAuth Authentication in PHP"
ms.custom: na
ms.date: "05/24/2017"
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: "article"
ms.assetid: c8fea347-f597-49ed-a3bf-b28e1c9ee328
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
robots: noindex,nofollow
---
# Server Side OAuth Authentication in PHP
This example demonstrates how to authenticate a [!INCLUDE[brand](../guides/includes/brand.md)] user in a PHP web application using OAuth. For more information about [!INCLUDE[brand](../guides/includes/brand.md)] and OAuth, see [Authentication with OAuth](../guides/authentication-with-oauth.md).

## Prerequisites
To implement and run this example, you'll need to have the following:
-   Your application's Client ID and Client Secret. When you registered your OAuth-enabled application as described in [Registering Your Application](../guides/authentication-with-oauth.md#registerapplication), you were issued these settings.  
-   Your application's redirect URI. When you register your OAuth-enabled application as described in [Registering Your Application](../guides/authentication-with-oauth.md#registerapplication), be sure to specify a redirect URL that includes the value in the *OAuth2Callback.php* file below e.g. */oauth2callback.php*. For example if your root domain is http://www.contoso.com, you must either register http://www.contoso.com/oauth2callback.php as a redirect URL or edit *$redirectUriPath* in the code example below to match your registered redirect URL.  
-   A developer token. If you're new to the [!INCLUDE[brand](../guides/includes/brand.md)] API and don't currently have a developer token, see [Getting Started With the Bing Ads API](../guides/getting-started-with-the-bing-ads-api.md) for instructions.  
-   A PHP-enabled web server that's connected to the internet and accessible with a registered domain name. For example you can publish using [Azure Websites](http://azure.microsoft.com/en-us/services/websites/).  

## Implementing an OAuth-Enabled Application with PHP
This example includes four source files which you  can save on your PHP-enabled web server. This server must be accessible via a valid, registered domain name and must be accessible from the public internet. For this example do not register an OAuth application with a localhost OAuth redirect URI. The actual location of these files on your server is up to you. The only requirements are that the $redirectUriPath and $getDataRedirectUriPath in ClientCredentials.php below are both set the actual location of these files and that the value of $redirectUriPath is the as the redirect URI you specified when you registered your application.

## ClientCredentials.php
This file contains the OAuth Client ID and Client Secret that you were issued when you registered your application. The $redirectUriPath must match the redirect URI that you specified when you registered your application and must obviously point to the oauth2callback.php source file, wherever you've put it on your web server. The $getDataRedirectUriPath is where the user will be redirected once you've obtained valid OAuth tokens; this is where you would implement code to begin accessing the user's [!INCLUDE[brand](../guides/includes/brand.md)] data.

This file is included from Index.php and OAuth2Callback.php below, so if you choose to have these files in different directories, be sure to edit the include statements accordingly.

```php
<?php
$clientId = '<the client ID for your application goes here>';
$clientSecret = '<the client secret for your application goes here>';

$DeveloperToken = "<DeveloperTokenGoesHere>";

$redirectUriPath = "/oauth2callback.php";    // This is the url that the client browser will be redirected to after authentication
$getDataRedirectUriPath = "get_data.php"; // this is the page in your application that will access client-owned data
```

## Index.php
This is the home page of this example application. This page contains a single button which kicks off the OAuth authorization grant flow sequence.

In a real-world application, this code would allow the user to login or create a new account. If the user already has an account in your user database, you would retrieve the OAuth refresh token that you had previous obtained (see the following code), exchange that for a temporary access token, and use that token to access the [!INCLUDE[brand](../guides/includes/brand.md)] API on behalf of the user. If the user is creating a new account on your system, you would execute the code as outlined in this example to obtain access and refresh tokens.

```php
<?php
include "ClientCredentials.php";

session_start();

// Generate random value for use as the 'state'.  Mitigates
// cross site request forgery attacks.
$_SESSION['state'] = rand(0,999999999);

// This is the Microsoft authentication service URL used to initiate the OAuth authentication flow
$authorizationUrlBase = 'https://login.live.com/oauth20_authorize.srf';

// URL parameters used to request an authorization token
$queryParams = array(
    'client_id' => $clientId,
    'redirect_uri' => (isset($_SERVER['HTTPS']) && ($_SERVER['HTTPS'] <> 'off')?'https://':'http://') .
        $_SERVER['HTTP_HOST'] . $redirectUriPath,
    'scope' => "bingads.manage",
    'response_type' => 'code',
    'state' => $_SESSION['state']
);

// Microsoft Authentication service url and params
$goToUrl = $authorizationUrlBase . '?' . http_build_query($queryParams);
?>

// Display a small form with a login button. In your application, you would implement code to allow
// the user to either log into your service or create a new account.
<h2>Bing Ads OAuth Demo</h2>

<p>This application would like to manage your Bing Ads data. Click below to login and authorize this application.</p>

<p>When you click OK below, you'll be redirected to the following URI:</p>
<p><?php echo $goToUrl ?></p>

// When the user presses this button, he'll be redirected to fully formed URL to request an
// authorization token. From here, the user will be redirected to the $redirectUriPath where the authorization
// token can be extracted.
<input type="button" onClick="return window.location='<?php echo $goToUrl;?>';" value="OK" />
```

## OAuth2Callback.php
The user will be redirected to this URL after he has logged in with Microsoft Live ID and authorized your application to access his data.

The purpose of this code is to extract the OAuth authorization token from the redirect URI and exchange it for access and refresh tokens. The access token can  be used to access the user's [!INCLUDE[brand](../guides/includes/brand.md)] data for a limited period of time, after which it must be refreshed using the refresh token. Your application should store the refresh token in its private user database. Refresh tokens do not normally expire, but a user can revoke his authorization for your application, so your code should allow for this possibility. Since this token can be used to gain full access to the user's [!INCLUDE[brand](../guides/includes/brand.md)] data, it should be stored with the same level of security that you would use to store username and password credentials.

```php
<?php
include "ClientCredentials.php";

// Initialize the session
session_start();

// A helper class used to construct an URL with parameters and execute
// HTTP POST operations.
class HttpClient {
     public function postData($url, $postData) {
        $ch = curl_init();

        $query = "";

        while(list($key, $val) = each($postData))
        {
            if(strlen($query) > 0)
            {
                $query = $query . '&';
            }

            $query = $query . $key . '=' . $val;
        }

        $options = array(
            CURLOPT_URL => $url,
            CURLOPT_SSL_VERIFYHOST => 0,
            CURLOPT_SSL_VERIFYPEER => 0,
            CURLOPT_FOLLOWLOCATION => 1,
            CURLOPT_RETURNTRANSFER => TRUE,
            CURLOPT_POST => TRUE,
            CURLOPT_POSTFIELDS => $query);

        curl_setopt_array($ch, $options);

        $response = curl_exec($ch);

        if(FALSE === $response)
        {
            $curlErr = curl_error($ch);
            $curlErrNum = curl_errno($ch);

            curl_close($ch);
            throw new Exception($curlErr, $curlErrNum);
        }

        curl_close($ch);

        return $response;
    }
}

// This is the URL used to exchange the authorization token for an
// access token and a refresh token.
$accessTokenExchangeUrl = "https://login.live.com/oauth20_token.srf";

// Get the authorization code from the URL as well as the cross site forgery mitigation value.
$code = $_GET['code'];
$state = $_GET['state'];

// Verify the 'state' value is the same random value we created
// when initiating the authorization request.
if ((! is_numeric($state)) || ($state != $_SESSION['state']))
{
    throw new Exception('Error validating state.  Possible cross-site request forgery.');
}

$redirectUri = (isset($_SERVER['HTTPS']) && ($_SERVER['HTTPS'] <> 'off')?'https://':'http://') .
    $_SERVER['HTTP_HOST'] . $redirectUriPath;

// These params will be added to the URL used in 
// HTTP POST below to request an access token
$accessTokenExchangeParams = array(
    'client_id' => $clientId,
    'client_secret' => $clientSecret,
    'grant_type' => 'authorization_code',
    'code' => $code,
    'redirect_uri' => $redirectUri
);

// Create an HTTP client and execute an HTTP POST request to
// exchange the authorization token for an access token and
// refresh token.
$httpClient = new HttpClient();
$responseJson = $httpClient->postData(
    $accessTokenExchangeUrl,
    $accessTokenExchangeParams);

// The response formatted in json
$responseArray = json_decode($responseJson, TRUE);

// If the response contains an access_token element, it was successful.
// If not, an error occurred and the description will be displayed below 
if(isset($responseArray['access_token']))
{
    $accessToken = $responseArray['access_token'];
    $expiresIn = $responseArray['expires_in'];
    $refreshToken = $responseArray['refresh_token'];

    $_SESSION['access_token'] = $accessToken;
    $_SESSION['refresh_token'] = $refreshToken;

    // Redirect to the URL that will finally access BingAds data.
    header('Location: ' . $getDataRedirectUriPath);
}
else
{
    $errorDesc = $responseArray['error_description'];
    $errorName = $responseArray['error'];
    printf("<p>OAuth failed Failed: %s - %s</p>", $errorName, $errorDesc);
}
```

## get_data.php
In this example, the user is redirected here from the OAuth redirect page, OAuth2Callback.php, after it has exchanged the temporary OAuth authorization token for the access and refresh tokens. At this point, you can use the access token to access the user's [!INCLUDE[brand](../guides/includes/brand.md)] data. Access tokens have a limited life span, but refresh tokens will persist unless the user revokes access to your application.

```php
<?php
session_start();

// The BingAds OAuth access token will be in session data. This is the token used
// to access BingAds data on behalf of the customer.
$accessToken = $_SESSION['access_token'];

printf("Implement code to retrieve data with access token: %s", $accessToken);
```

## See Also
[Getting Started Using PHP with Bing Ads Services](../guides/getting-started-using-php-with-bing-ads-services.md)  

