---
title: "Management Model for Tool Providers"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7cb56341-68a8-4a19-95a4-b91cf0c2c3f2
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Management Model for Tool Providers
A tool provider builds a [!INCLUDE[brand](../../concepts/includes/brand.md)] application for other companies to manage their advertising campaigns, and is not necessarily billed by [!INCLUDE[brand](../../concepts/includes/brand.md)]. The advertiser user owns the accounts, is billed directly by Microsoft for valid ad clicks, and may pay a fee to the tool provider. The following sections describe the entity model and credentials for tool providers.

## Tool Provider Entity Model
The following figure shows multiple customers using the same third-party tool.

![Management Model Tool Provider](../../concepts/guides/media/management-model-tool-provider.png "Management Model Tool Provider")

Third-party tools may be used to manage some or all aspects of an advertiser account. Your users may also manage their respective account through the [!INCLUDE[brand](../../concepts/includes/brand.md)] web application or another third-party tool. You should design your application to be flexible and robust considering that data may have changed state since the last time a client used your application.

## Credentials and Account Access
The following are the header elements and the corresponding identifiers that a tool provider would use.

> [!NOTE]
> If you use the *AuthenticationToken*, the *UserName* and *Password* elements are ignored. For more information, see [Authentication with OAuth](../../concepts/guides/authentication-with-oauth.md).

|Header Element|Owner|
|------------------|---------|
|AuthenticationToken|The OAuth access token corresponding to the tool user's linked Microsoft Account.|
|UserName|The sign-in user name.<br /><br />**Note:** The user of a tool may have any role. For more information see [Account Permissions and the Developer Token](../../concepts/guides/customer-accounts.md#accountpermissions) and [User Roles and Available Service Operations](../../concepts/guides/customer-accounts.md#userroles) within [Managing Customer Accounts](../../concepts/guides/customer-accounts.md).|
|Password|The sign-in password of the user specified in UserName.|
|DeveloperToken|The tool provider’s token.<br /><br />**Note:** A tool provider should use the multi-user developer token to authenticate with users of their application. A tool provider needs only one such token. You should not ask clients to provide their own single-user token. For more information about token types, see [Account Permissions and the Developer Token](../../concepts/guides/customer-accounts.md#accountpermissions).|
|CustomerId|The identifier of the customer that contains and owns the account. If you manage an account of another customer, you should use that customer ID instead of your own customer ID.<br /><br />**Note:** The customer ID may vary for each user of a given tool.|
|CustomerAccountId|A customer's account ID.|
For more information about customer and account identifiers, see [Getting Started With the Bing Ads API](../../concepts/getting-started-with-the-bing-ads-api.md).

## See Also
[Customer Accounts](../../concepts/guides/customer-accounts.md)  
[Getting Started With the Bing Ads API](../../concepts/getting-started-with-the-bing-ads-api.md)  

