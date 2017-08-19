---
title: "GetUsersInfo Service Operation"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aacc8a3a-f320-491d-941f-058ee8a6b948
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetUsersInfo Service Operation
Gets a list of objects that contains user identification information, for example the user name and identifier of the user.

[!INCLUDE[customer_service_namespace](../customer-api/includes/customer-service-namespace.md)]

## <a name="request"></a>GetUsersInfoRequest Message

### Request Body
The *GetUsersInfoRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CustomerId*|The identifier of the customer to which the users belong.|*long*|
|*StatusFilter*|The status value that the operation uses to filter the list of users that it returns. The operation returns only those users with the specified status.|[UserLifeCycleStatus](../customer-api/userlifecyclestatus-value-set.md)|

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
    <Action mustUnderstand="1">GetUsersInfo</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetUsersInfoRequest xmlns="https://bingads.microsoft.com/Customer/v11">
      <CustomerId></CustomerId>
      <StatusFilter i:nil="false"></StatusFilter>
    </GetUsersInfoRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetUsersInfoResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*UsersInfo*|A list of *UserInfo* objects that identifies the list of users who meet the filter criteria.<br /><br />To get the user data for a user in the list, access the *Id* element of the *UserInfo* object and use it to call [GetUser](../customer-api/getuser-service-operation.md).|[UserInfo](../customer-api/userinfo-data-object.md) array|

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
    <GetUsersInfoResponse xmlns="https://bingads.microsoft.com/Customer/v11">
      <UsersInfo xmlns:e18="https://bingads.microsoft.com/Customer/v11/Entities" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e18:UserInfo>
          <e18:Id></e18:Id>
          <e18:UserName p5:nil="false"></e18:UserName>
        </e18:UserInfo>
      </UsersInfo>
    </GetUsersInfoResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cusmanerror](../customer-api/includes/cusmanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
