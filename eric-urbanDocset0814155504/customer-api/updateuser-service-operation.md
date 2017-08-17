---
title: "UpdateUser Service Operation"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d2c9e8f4-4d66-449f-8f02-b2720dd927a7
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# UpdateUser Service Operation
Updates the details of the specified user.

||
|-|
|[!INCLUDE[cusman_navigation_noremarks](../customer-api/includes/cusman-navigation-noremarks.md)]|

## <a name="request"></a>UpdateUserRequest Message

### Request Body
The *UpdateUserRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*User*|The user object that contains the updated user information.<br /><br />This operation overwrites the existing user data with the contents of the user object that you pass. This operation performs a full update, not a partial update. The *User* object must contain the time stamp value from the last time that the *User* object was written to. To ensure that the time stamp contains the correct value, call the [GetUser](../customer-api/getuser-service-operation.md) operation. You can then update the user data as appropriate, and call *UpdateUser*.|[User](../customer-api/user-data-object.md)|

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
    <Action mustUnderstand="1">UpdateUser</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <UpdateUserRequest xmlns="https://bingads.microsoft.com/Customer/v11">
      <User xmlns:e35="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false">
        <e35:ContactInfo i:nil="false">
          <e35:Address i:nil="false">
            <e35:City i:nil="false"></e35:City>
            <e35:CountryCode i:nil="false"></e35:CountryCode>
            <e35:Id i:nil="false"></e35:Id>
            <e35:Line1 i:nil="false"></e35:Line1>
            <e35:Line2 i:nil="false"></e35:Line2>
            <e35:Line3 i:nil="false"></e35:Line3>
            <e35:Line4 i:nil="false"></e35:Line4>
            <e35:PostalCode i:nil="false"></e35:PostalCode>
            <e35:StateOrProvince i:nil="false"></e35:StateOrProvince>
            <e35:TimeStamp i:nil="false"></e35:TimeStamp>
          </e35:Address>
          <e35:ContactByPhone i:nil="false"></e35:ContactByPhone>
          <e35:ContactByPostalMail i:nil="false"></e35:ContactByPostalMail>
          <e35:Email i:nil="false"></e35:Email>
          <e35:EmailFormat i:nil="false"></e35:EmailFormat>
          <e35:Fax i:nil="false"></e35:Fax>
          <e35:HomePhone i:nil="false"></e35:HomePhone>
          <e35:Id i:nil="false"></e35:Id>
          <e35:Mobile i:nil="false"></e35:Mobile>
          <e35:Phone1 i:nil="false"></e35:Phone1>
          <e35:Phone2 i:nil="false"></e35:Phone2>
        </e35:ContactInfo>
        <e35:CustomerAppScope i:nil="false"></e35:CustomerAppScope>
        <e35:CustomerId i:nil="false"></e35:CustomerId>
        <e35:Id i:nil="false"></e35:Id>
        <e35:JobTitle i:nil="false"></e35:JobTitle>
        <e35:LastModifiedByUserId i:nil="false"></e35:LastModifiedByUserId>
        <e35:LastModifiedTime i:nil="false"></e35:LastModifiedTime>
        <e35:Lcid i:nil="false"></e35:Lcid>
        <e35:Name i:nil="false">
          <e35:FirstName i:nil="false"></e35:FirstName>
          <e35:LastName i:nil="false"></e35:LastName>
          <e35:MiddleInitial i:nil="false"></e35:MiddleInitial>
        </e35:Name>
        <e35:Password i:nil="false"></e35:Password>
        <e35:SecretAnswer i:nil="false"></e35:SecretAnswer>
        <e35:SecretQuestion></e35:SecretQuestion>
        <e35:UserLifeCycleStatus i:nil="false"></e35:UserLifeCycleStatus>
        <e35:TimeStamp i:nil="false"></e35:TimeStamp>
        <e35:UserName i:nil="false"></e35:UserName>
        <e35:IsMigratedToMicrosoftAccount></e35:IsMigratedToMicrosoftAccount>
      </User>
    </UpdateUserRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>UpdateUserResponse Message

### <a name="Body_Elements"></a>Response Body
The response does not contain additional body elements.

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
    <UpdateUserResponse xmlns="https://bingads.microsoft.com/Customer/v11">
      <LastModifiedTime></LastModifiedTime>
    </UpdateUserResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cusmanerror](../customer-api/includes/cusmanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
