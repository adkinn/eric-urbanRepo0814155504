---
title: "DeleteAccount Service Operation"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0dad5a3-b37a-4c0c-bd8a-b9b9ce2c0ee1
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DeleteAccount Service Operation
Deletes an account.

> [!NOTE]
> After deleting the account it will be searchable and show as inactive in the [!INCLUDE[brand](../customer-api/includes/brand.md)] web application. You may or may not choose to surface inactive accounts in your application.

||
|-|
|[!INCLUDE[cusman_navigation_noremarks](../customer-api/includes/cusman-navigation-noremarks.md)]|

## <a name="request"></a>DeleteAccountRequest Message

### Request Body
The *DeleteAccountRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountId*|The identifier of the account to delete.|*long*|
|*TimeStamp*|The time-stamp value that the operation uses to reconcile the update. You must call  [GetAccount](../customer-api/getaccount-service-operation.md) to get the time-stamp value. The delete operation fails if the account object has a time-stamp value that differs from the one that you pass.|*base64Binary*|

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
    <Action mustUnderstand="1">DeleteAccount</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <DeleteAccountRequest xmlns="https://bingads.microsoft.com/Customer/v11">
      <AccountId></AccountId>
      <TimeStamp i:nil="false"></TimeStamp>
    </DeleteAccountRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>DeleteAccountResponse Message

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
    <DeleteAccountResponse xmlns="https://bingads.microsoft.com/Customer/v11" />
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cusmanerror](../customer-api/includes/cusmanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
