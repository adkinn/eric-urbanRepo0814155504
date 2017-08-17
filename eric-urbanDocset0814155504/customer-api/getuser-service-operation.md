---
title: "GetUser Service Operation"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 843fa7ef-7901-45cb-905c-9e7c6fa5e5e2
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetUser Service Operation
Gets the details of a user.

||
|-|
|[!INCLUDE[cusman_navigation_noremarks](../customer-api/includes/cusman-navigation-noremarks.md)]|

## <a name="request"></a>GetUserRequest Message

### Request Body
The *GetUserRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*UserId*|The identifier of the user to get.<br /><br />**Note**: If this element is null or not provided, the response will include details for the authenticated user specified in the request header.|*long*|No|

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
    <Action mustUnderstand="1">GetUser</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetUserRequest xmlns="https://bingads.microsoft.com/Customer/v11">
      <UserId i:nil="false"></UserId>
    </GetUserRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetUserResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Accounts*|An array of identifiers of the accounts to which the user has access permissions. If the *Roles* element contains an account role and the *Accounts* element contains a 0 (zero)-length array, it indicates that the user has access permissions to all of the customer’s accounts.|*long* array|
|*Customers*|An array of identifiers of the customers to which the user has access permissions. If the *Roles* element contains a customer role and the *Customers* element contains a 0 (zero)-length array, it indicates that the user has access permissions to all customers.|*long* array|
|*Roles*|An array of roles that determines the permissions that the user has to manage the customer or account data.<br /><br />Possible values include the following:<br />16 - The user has the **Advertiser Campaign Manager** role.<br />33 - The user has the **Aggregator** role.<br />41 - The user has the **Super Admin** role.<br />100 - The user has the **ClientViewer** role.<br />203 - The user has the **Standard** role.<br /><br />For more information, see [User Roles and Available Service Operations](https://msdn.microsoft.com/library/bing-ads-managing-customer-accounts-guide.aspx#userroles).<br /><br />**Important**: The list above provides examples of possible return values. Other  values might be returned. Deprecated or internal roles can be included in the response.|*int* array|
|*User*|A user object that contains information about the user.|[User](../customer-api/user-data-object.md)|

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
    <GetUserResponse xmlns="https://bingads.microsoft.com/Customer/v11">
      <User xmlns:e17="https://bingads.microsoft.com/Customer/v11/Entities" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e17:ContactInfo p5:nil="false">
          <e17:Address p5:nil="false">
            <e17:City p5:nil="false"></e17:City>
            <e17:CountryCode p5:nil="false"></e17:CountryCode>
            <e17:Id p5:nil="false"></e17:Id>
            <e17:Line1 p5:nil="false"></e17:Line1>
            <e17:Line2 p5:nil="false"></e17:Line2>
            <e17:Line3 p5:nil="false"></e17:Line3>
            <e17:Line4 p5:nil="false"></e17:Line4>
            <e17:PostalCode p5:nil="false"></e17:PostalCode>
            <e17:StateOrProvince p5:nil="false"></e17:StateOrProvince>
            <e17:TimeStamp p5:nil="false"></e17:TimeStamp>
          </e17:Address>
          <e17:ContactByPhone p5:nil="false"></e17:ContactByPhone>
          <e17:ContactByPostalMail p5:nil="false"></e17:ContactByPostalMail>
          <e17:Email p5:nil="false"></e17:Email>
          <e17:EmailFormat p5:nil="false"></e17:EmailFormat>
          <e17:Fax p5:nil="false"></e17:Fax>
          <e17:HomePhone p5:nil="false"></e17:HomePhone>
          <e17:Id p5:nil="false"></e17:Id>
          <e17:Mobile p5:nil="false"></e17:Mobile>
          <e17:Phone1 p5:nil="false"></e17:Phone1>
          <e17:Phone2 p5:nil="false"></e17:Phone2>
        </e17:ContactInfo>
        <e17:CustomerAppScope p5:nil="false"></e17:CustomerAppScope>
        <e17:CustomerId p5:nil="false"></e17:CustomerId>
        <e17:Id p5:nil="false"></e17:Id>
        <e17:JobTitle p5:nil="false"></e17:JobTitle>
        <e17:LastModifiedByUserId p5:nil="false"></e17:LastModifiedByUserId>
        <e17:LastModifiedTime p5:nil="false"></e17:LastModifiedTime>
        <e17:Lcid p5:nil="false"></e17:Lcid>
        <e17:Name p5:nil="false">
          <e17:FirstName p5:nil="false"></e17:FirstName>
          <e17:LastName p5:nil="false"></e17:LastName>
          <e17:MiddleInitial p5:nil="false"></e17:MiddleInitial>
        </e17:Name>
        <e17:Password p5:nil="false"></e17:Password>
        <e17:SecretAnswer p5:nil="false"></e17:SecretAnswer>
        <e17:SecretQuestion></e17:SecretQuestion>
        <e17:UserLifeCycleStatus p5:nil="false"></e17:UserLifeCycleStatus>
        <e17:TimeStamp p5:nil="false"></e17:TimeStamp>
        <e17:UserName p5:nil="false"></e17:UserName>
        <e17:IsMigratedToMicrosoftAccount></e17:IsMigratedToMicrosoftAccount>
      </User>
      <Roles p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <a1:int></a1:int>
      </Roles>
      <Accounts p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <a1:long></a1:long>
      </Accounts>
      <Customers p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <a1:long></a1:long>
      </Customers>
    </GetUserResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cusmanerror](../customer-api/includes/cusmanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
