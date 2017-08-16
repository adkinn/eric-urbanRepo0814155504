---
title: "Getting Started With the Bing Ads API"
ms.custom: na
ms.date: "08/16/2017"
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: "article"
ms.assetid: d2f0876f-fe78-4ade-955a-059ae9ae12a9
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Getting Started With the Bing Ads API
Any [!INCLUDE[brand](../concepts/includes/brand.md)] user with a developer token can begin using the [!INCLUDE[brand](../concepts/includes/brand.md)] Application Programming Interface (API). For advertisers placing a large number of ads or developers building advertising tools, the [!INCLUDE[brand](../concepts/includes/brand.md)] API provides a programmatic interface to [!INCLUDE[brand](../concepts/includes/brand.md)]. You can write your [!INCLUDE[brand](../concepts/includes/brand.md)] application in any language that supports web services. Code examples are available in C# ([Getting Started](../concepts/getting-started-using-csharp-with-bing-ads-services.md) | [Examples](../concepts/csharp-examples-for-bing-ads.md)), Java ([Getting Started](../concepts/getting-started-using-java-with-bing-ads-services.md) | [Examples](../concepts/java-examples-for-bing-ads.md)), PHP ([Getting Started](../concepts/getting-started-using-php-with-bing-ads-services.md) | [Examples](../concepts/php-examples-for-bing-ads.md)), and Python ([Getting Started](../concepts/getting-started-using-python-with-bing-ads-services.md) | [Examples](../concepts/python-examples-for-bing-ads.md)). For more information about available services, see [Bing Ads API Overview](../concepts/bing-ads-api-overview.md).

## <a name="direct_signup"></a>Getting a Developer Token
To use [!INCLUDE[brand](../concepts/includes/brand.md)] APIs, you must have a developer token and valid user credentials. If you do not yet have a [!INCLUDE[brand](../concepts/includes/brand.md)] account, go to the [Bing Ads](https://bingads.microsoft.com/Default.aspx) web application, and click **Sign up**. To get a developer token for production, you must be logged into the [Bing Ads Developer Portal](https://developers.bingads.microsoft.com/Account) as a Microsoft Account user with the Super Admin role. The Super Admin may request API access for any user within their customer scope. For more information, see [User Roles and Available Service Operations](../concepts/customer-accounts.md#userroles).

The sandbox and production environments use separate credentials. For information about getting immediate access to the sandbox, see [Sandbox](../concepts/sandbox.md).

## <a name="where_to_use"></a>Where to Use the API Credentials
[!INCLUDE[brand](../concepts/includes/brand.md)] services use Simple Object Access Protocol (SOAP) to exchange the request and response messages with the service operation. For more information, see [Bing Ads Services Protocol](../concepts/bing-ads-services-protocol.md).

Each SOAP request must include the following SOAP headers, which contain the user’s credentials.

[!INCLUDE[headerelementdetails](../concepts/includes/headerelementdetails.md)]
## <a name="accountcustomerid"></a>Account and Customer Identifiers
Many [!INCLUDE[brand](../concepts/includes/brand.md)] service operations require an account ID and some require a customer ID. The following sections describe the account and customer identifiers, and provides information on retrieving the identifiers.

### <a name="accountid"></a>Account Identifier
The *account identifier* is a numeric identifier that identifies an account.

Many of the campaign management operations require that you specify the account identifier in the body of the request message. For example, the [GetCampaignsByAccountId](https://msdn.microsoft.com/library/bing-ads-campaign-management-getcampaignsbyaccountid.aspx) operation returns all of the campaigns for the account that you specify in the body of the request message.

Do not confuse the *account identifier* with the *account number*. The account number is the system generated account number that is used to identify the account in the [!INCLUDE[brand](../concepts/includes/brand.md)] web application. The account number has the form xxxxxxxx, where xxxxxxxx is a series of any eight alphanumeric characters.
The API uses only the account identifier, never the account number.

### <a name="customeraccountid"></a>Customer Account Identifier
The *customer account identifier* is the same as the account identifier. You specify the account identifier in the *CustomerAccountId* SOAP request header element.

As a best practice you should always specify the identifier of the account being accessed in the *CustomerAccountId* header element. Some of the campaign management operations require that you specify the account ID in the request message, and most of them require that you specify the account ID in the *CustomerAccountId* header element.

### <a name="customerid"></a>Customer Identifier
The *customer identifier* is the numeric identifier that identifies a customer. You specify the customer identifier in the *CustomerId* SOAP request header element.

As a best practice you should always specify the identifier of the customer that owns the account in the *CustomerId* header element. Only operations that store data in the customer library for example targets, require you to set the *CustomerId* header element. Operations that require you to specify the customer ID will state this in the corresponding service operation topic.

### Getting Your Account ID and Customer ID
To get a user’s customer ID and account ID, you can sign in to the [!INCLUDE[brand](../concepts/includes/brand.md)] web application and click on the **Campaigns** tab. The URL will contain a *cid* key/value pair in the query string that identifies your customer ID, and an *aid* key/value pair that identifies your account ID. For example, *https://ui.bingads.microsoft.com/campaign/Campaigns.m?cid=FindCustomerIdHere&aid=FindAccountIdHere#/customer/FindCustomerIdHere/account/FindAccountIdHere/campaign*.

## <a name="need_help"></a>Need Help?
For troubleshooting tips, see [Handling Service Errors and Exceptions](../concepts/handling-service-errors-and-exceptions.md).

To get help with issues that you cannot resolve, consider posting in the [API Developer Forum](http://go.microsoft.com/fwlink/?LinkId=269629) where an active [!INCLUDE[brand](../concepts/includes/brand.md)] product team or community member will try and help. If you do not find timely information via the developer forum, or if the investigation involves sensitive account or personal details, please contact [Bing Ads Support](http://go.microsoft.com/fwlink/?LinkId=269631).

## See Also
[Bing Ads Technical Guides](../concepts/bing-ads-technical-guides.md)  
[Bing Ads API Reference](../concepts/bing-ads-api-reference.md)  

