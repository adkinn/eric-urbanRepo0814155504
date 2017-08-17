---
title: "AddInsertionOrder Service Operation"
ms.custom: ""
ms.date: "06/02/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 866066a3-1bd1-49e7-80f6-a304cbec5b25
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AddInsertionOrder Service Operation
Adds an insertion order to the specified account.

||
|-|
|[!INCLUDE[bill_navigation_noremarks](../billing-api/includes/bill-navigation-noremarks.md)]|

## <a name="request"></a>AddInsertionOrderRequest Message

### Request Body
The *AddInsertionOrderRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*InsertionOrder*|An insertion order to add to the account specified in the *InsertionOrder* object.|[InsertionOrder](../billing-api/insertionorder-data-object.md)|

### Request Headers
[!INCLUDE[header_intro](../billing-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[billing_header_oauth](../billing-api/includes/billing-header-oauth.md)]
#### Password Authentication
[!INCLUDE[billing_header_password](../billing-api/includes/billing-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
\<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="https://bingads.microsoft.com/Billing/v11">
    <Action mustUnderstand="1">AddInsertionOrder</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <AddInsertionOrderRequest xmlns="https://bingads.microsoft.com/Billing/v11">
      \<InsertionOrder xmlns:e1="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false">
        \<e1:AccountId>\</e1:AccountId>
        \<e1:BalanceAmount i:nil="false">\</e1:BalanceAmount>
        \<e1:BookingCountryCode i:nil="false">\</e1:BookingCountryCode>
        \<e1:Comment i:nil="false">\</e1:Comment>
        \<e1:EndDate>\</e1:EndDate>
        \<e1:InsertionOrderId i:nil="false">\</e1:InsertionOrderId>
        \<e1:LastModifiedByUserId i:nil="false">\</e1:LastModifiedByUserId>
        \<e1:LastModifiedTime i:nil="false">\</e1:LastModifiedTime>
        \<e1:NotificationThreshold i:nil="false">\</e1:NotificationThreshold>
        \<e1:ReferenceId i:nil="false">\</e1:ReferenceId>
        \<e1:SpendCapAmount>\</e1:SpendCapAmount>
        \<e1:StartDate>\</e1:StartDate>
        \<e1:Name i:nil="false">\</e1:Name>
        \<e1:Status i:nil="false">\</e1:Status>
        \<e1:PurchaseOrder i:nil="false">\</e1:PurchaseOrder>
        \<e1:ChangePendingReview i:nil="false">\</e1:ChangePendingReview>
      </InsertionOrder>
    </AddInsertionOrderRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>AddInsertionOrderResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CreateTime*|Identifies the server time in UTC when the insertion order was added.|*dateTime*|
|*InsertionOrderId*|A *long* value that represents the identifier for the insertion order that was added.|*long*|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[bill_response_header_table](../billing-api/includes/bill-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
\<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="https://bingads.microsoft.com/Billing/v11">
    \<TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  \</s:Header>
  \<s:Body>
    <AddInsertionOrderResponse xmlns="https://bingads.microsoft.com/Billing/v11">
      <InsertionOrderId></InsertionOrderId>
      <CreateTime></CreateTime>
    </AddInsertionOrderResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[billingerror](../billing-api/includes/billingerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[SearchInsertionOrders](../billing-api/searchinsertionorders-service-operation.md)  
[UpdateInsertionOrder](../billing-api/updateinsertionorder-service-operation.md)  

