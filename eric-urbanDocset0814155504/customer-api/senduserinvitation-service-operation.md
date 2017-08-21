---
title: "SendUserInvitation Service Operation"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7604ae84-192f-4e27-b4c9-98063046784a
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SendUserInvitation Service Operation
Sends an invitation for  a Microsoft account user to manage one or more [!INCLUDE[brand](../customer-api/includes/brand.md)] customer accounts. When the invitation is accepted, the user's Microsoft account is linked to the specified [!INCLUDE[brand](../customer-api/includes/brand.md)] customer accounts.  

It is possible to have multiple pending invitations sent to the same email address, which have not yet expired. It is also possible for those invitations to have specified different user roles, for example if you sent an invitation with an incorrect user role and then sent a second invitation with the correct user role. The recipient can accept any of the invitations. The Bing Ads API does not support any operations to delete pending user invitations. After you invite a user, the only way to cancel the invitation is through the Bing Ads web application. You can find both pending and accepted invitations in the Users section of Accounts & Billing.

Since a recipient can accept the invitation and sign into Bing Ads with a Microsoft account different than the invitation email address, you cannot determine with certainty the mapping from [UserInvitation](../customer-api/userinvitation-data-object.md) to accepted [User](../customer-api/user-data-object.md). You can search by the invitation ID (returned by *SendUserInvitations*), only to the extent of finding out whether or not the invitation has been accepted or has expired. The [SearchUserInvitations](../customer-api/searchuserinvitations-service-operation.md) operation returns all pending invitations, whether or not they have expired. Accepted invitations are not included in the [SearchUserInvitations](../customer-api/searchuserinvitations-service-operation.md) response.  

After the invitation has been accepted, you can call [GetUsersInfo](../customer-api/getusersinfo-service-operation.md) and [GetUser](../customer-api/getuser-service-operation.md) to access the Bing Ads user details. Once again though, since a recipient can accept the invitation and sign into Bing Ads with a Microsoft account different than the invitation email address, you cannot determine with certainty the mapping from [UserInvitation](../customer-api/userinvitation-data-object.md) to accepted [User](../customer-api/user-data-object.md). With the user ID returned by [GetUsersInfo](../customer-api/getusersinfo-service-operation.md) or [GetUser](../customer-api/getuser-service-operation.md), you can call [DeleteUser](../customer-api/deleteuser-service-operation.md) to remove the user.

For more information about user authentication, see [Authentication with OAuth](~/concepts/authentication-with-oauth.md).

[!INCLUDE[customer_service_namespace](../customer-api/includes/customer-service-namespace.md)]

## <a name="request"></a>SendUserInvitationRequest Message
The *SendUserInvitationRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

### Request Body

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*UserInvitation*|The user invitation to send.|[UserInvitation](../customer-api/userinvitation-data-object.md)|Yes|

### Request Headers
[!INCLUDE[header_intro](../customer-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[cusman_header_oauth](../customer-api/includes/cusman-header-oauth.md)]
#### Password Authentication
[!INCLUDE[cusman_header_password](../customer-api/includes/cusman-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Customer/v11">
    <Action mustUnderstand="1">SendUserInvitation</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <SendUserInvitationRequest xmlns="https://bingads.microsoft.com/Customer/v11">
      <UserInvitation xmlns:e41="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false">
        <e41:Id></e41:Id>
        <e41:FirstName i:nil="false"></e41:FirstName>
        <e41:LastName i:nil="false"></e41:LastName>
        <e41:Email i:nil="false"></e41:Email>
        <e41:CustomerId></e41:CustomerId>
        <e41:Role></e41:Role>
        <e41:AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
          <a1:long></a1:long>
        </e41:AccountIds>
        <e41:ExpirationDate></e41:ExpirationDate>
        <e41:Lcid></e41:Lcid>
      </UserInvitation>
    </SendUserInvitationRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>SendUserInvitationResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*UserInvitationId*|A system-generated identifier for the user invitation that was sent.|long|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[cusman_response_header_table](../customer-api/includes/cusman-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Customer/v11">
    <TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  </s:Header>
  <s:Body>
    <SendUserInvitationResponse xmlns="https://bingads.microsoft.com/Customer/v11">
      <UserInvitationId></UserInvitationId>
    </SendUserInvitationResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cusmanerror](../customer-api/includes/cusmanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
