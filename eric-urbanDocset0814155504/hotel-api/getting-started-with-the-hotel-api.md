---
title: "Getting Started with the Hotel API"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a371f495-df5b-40f9-a5ac-10390bb51ea2
caps.latest.revision: 17
author: "eric-urban"
ms.author: "scottwhi"
---
# Getting Started with the Hotel API
<a name="doyouhavecredentials"/> 
## Do you have your Bing Ads credentials?
To use the Hotel API, you must have a Bing Ads account and a Microsoft account. To get a Bing Ads account, go to [http://bingads.microsoft.com](http://bingads.microsoft.com). If you're not signed in to your Microsoft account, you'll be redirected to sign in to your Microsoft account or sign up for a Microsoft account. After signing in, you'll have the option to **Sign up for a new Bing Ads account**. Select the sign up option and continue with the sign up process.

Unlike the other Bing Ads APIs, the Hotel API does not use a developer token. The API ignores it if you include it.

<a name="authenticatingcredentials"/> 
## Authenticating your credentials

The Hotel API uses the OAuth authentication scheme. For details about authenticating Microsoft account credentials using OAuth, see [Managing User Authentication with OAuth](https://msdn.microsoft.com/library/bing-ads-user-authentication-oauth-guide.aspx). 

You *can* use the [Bing Ads SDK](https://msdn.microsoft.com/library/bing-ads-client-libraries.aspx) for .NET, Java, or Python to authenticate Microsoft account credentials. For details about using the SDK to get the access token, see [C#](https://msdn.microsoft.com/library/bing-ads-overview-getting-started-csharp-visual-basic-with-web-services(v=msads.100).aspx#oauth) | [Java](https://msdn.microsoft.com/library/bing-ads-overview-getting-started-java-with-web-services(v=msads.100).aspx#oauth) | [Python](https://msdn.microsoft.com/library/bing-ads-overview-getting-started-python-with-web-services(v=msads.100).aspx#oauth). (You should only use the SDK to get the access token if you're using the SDK for Bing ad campaigns, too. Otherwise, it may not be worth the overhead of installing the SDK.)

If you choose not to use the Bing Ads SDK to get the tokens, see [OAuth C# Example](../hotel-api/oauth-csharp-example.md) for an example OAuth implementation.

> [!NOTE]
> You cannot use the Bing Ads SDK in the SI environment to get the access token. For SI, you can either clone the SDK Git repository and update the endpoints accordingly, or write your own AOuth implementation.
>
>For the SI environment, the following are the endpoints you must use to get Microsoft accounts and your application's client ID. Wherever you see endpoints mentioned in [Managing User Authentication with OAuth](https://msdn.microsoft.com/library/bing-ads-user-authentication-oauth-guide.aspx), substitute them with the following SI endpoints.
>
> - si.bingads.microsoft.com&mdash;Endpoint for Bing Ads
> - account.microsoft-int.com&mdash;Endpoint for getting an SI Microsoft account 
> - outlook-int.com&mdash;Endpoint for SI email used when getting an SI Microsoft account
> - apps.dev.microsoft-int.com/#/appList&mdash;Endpoint for getting an SI client ID
> - login.live-int.com&mdash;Endpoint for OAuth requests

<a name="wheretousecredentials"/> 
## Where do you use your credentials?

After getting the user's OAuth access token, set the Authorization header to it.

```csharp
var headers = new WebHeaderCollection();
headers.Add(HttpRequestHeader.Authorization, "Bearer " + tokens.AccessToken);
```

For information about the Authorization header and other headers that the request and response may contain, see [headers](../hotel-api/hotel-api-reference.md#headers). 

> [!NOTE]
> The Hotel API uses the standard Authorization header; however, Bing Ads uses the AuthenticationToken header. If you use the Bing Ads SDK to get the OAuth tokens, you'll use the SDK to get the tokens and then set the Authorization header.

<a name="feeds"/>
## Do you have your hotel feed set up?

Before using the Hotel API, you should have your hotel feeds set up. For details, see:

- [Hotel Feed](../hotel-feed/hotel-feed.md)
- [Points of Sale Feed](../pos-feed/points-of-sale-feed.md) 
- [Transaction Message](../transaction-message/transaction-message.md) 




