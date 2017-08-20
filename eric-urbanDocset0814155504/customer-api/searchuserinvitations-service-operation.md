---
title: "SearchUserInvitations Service Operation"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 653e56be-137b-4007-8d64-b1bbd745c388
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SearchUserInvitations Service Operation
Searches for user invitations that match a specified criteria.

This operation returns all pending invitations, whether or not they have expired. Accepted invitations are not included in the response.  

[!INCLUDE[customer_service_namespace](../customer-api/includes/customer-service-namespace.md)]

## <a name="request"></a>SearchUserInvitationsRequest Message
The *SearchUserInvitationsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

### Request Body

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*Predicates*|Determines the request conditions. This operation's response will include user invitations that match all of the specified predicates.<br /><br />**Note**: You may specify only one predicate.<br /><br />For a list of supported *Field* and *Operator* elements of a *Predicate* object for this service operation, see [Predicate Field and Operator](#predicates).|[Predicate](../customer-api/predicate-data-object.md) array|Yes|

#### <a name="predicates"></a>Predicate Field and Operator
For this service operation, the following are supported *Field* element and *Operator* elements of a *Predicate* object.

|Field|Operator|Description|
|---------|------------|---------------|
|CustomerId|*Equals*|Use this field to search the *CustomerId* element of the [UserInvitation](../customer-api/userinvitation-data-object.md).|

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
    <Action mustUnderstand="1">SearchUserInvitations</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <SearchUserInvitationsRequest xmlns="https://bingads.microsoft.com/Customer/v11">
      <Predicates xmlns:e39="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false">
        <e39:Predicate>
          <e39:Field i:nil="false"></e39:Field>
          <e39:Operator></e39:Operator>
          <e39:Value i:nil="false"></e39:Value>
        </e39:Predicate>
      </Predicates>
    </SearchUserInvitationsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>SearchUserInvitationsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*UserInvitations*|A  list of user invitations that meet the specified criteria.|[UserInvitation](../customer-api/userinvitation-data-object.md) array|

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
    <SearchUserInvitationsResponse xmlns="https://bingads.microsoft.com/Customer/v11">
      <UserInvitations xmlns:e40="https://bingads.microsoft.com/Customer/v11/Entities" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e40:UserInvitation>
          <e40:Id></e40:Id>
          <e40:FirstName p5:nil="false"></e40:FirstName>
          <e40:LastName p5:nil="false"></e40:LastName>
          <e40:Email p5:nil="false"></e40:Email>
          <e40:CustomerId></e40:CustomerId>
          <e40:Role></e40:Role>
          <e40:AccountIds p5:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </e40:AccountIds>
          <e40:ExpirationDate></e40:ExpirationDate>
          <e40:Lcid></e40:Lcid>
        </e40:UserInvitation>
      </UserInvitations>
    </SearchUserInvitationsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cusmanerror](../customer-api/includes/cusmanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
