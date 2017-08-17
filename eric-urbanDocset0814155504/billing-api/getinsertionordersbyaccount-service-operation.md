---
title: "GetInsertionOrdersByAccount Service Operation"
ms.custom: ""
ms.date: "06/02/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5f44937-13b1-41d0-9293-d497f8bf567f
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetInsertionOrdersByAccount Service Operation
Gets a list of insertion orders for the specified account.

> [!NOTE]
> This operation is deprecated and will be removed in a future API version. To get insertion orders, you should use the [SearchInsertionOrders](../billing-api/searchinsertionorders-service-operation.md) operation.

||
|-|
|[!INCLUDE[bill_navigation_noremarks](../billing-api/includes/bill-navigation-noremarks.md)]|

## <a name="request"></a>GetInsertionOrdersByAccountRequest Message

### Request Body
The *GetInsertionOrdersByAccountRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountId*|The identifier of the account that contains the insertion orders to get.|*long*|
|*InsertionOrderIds*|A list of identifiers of the insertion orders to get. To get all insertion orders, including those that have expired, set to NULL.|*long* array|

### Request Headers
[!INCLUDE[header_intro](../billing-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[billing_header_oauth](../billing-api/includes/billing-header-oauth.md)]
#### Password Authentication
[!INCLUDE[billing_header_password](../billing-api/includes/billing-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Billing/v11">
    <Action mustUnderstand="1">GetInsertionOrdersByAccount</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetInsertionOrdersByAccountRequest xmlns="https://bingads.microsoft.com/Billing/v11">
      <AccountId></AccountId>
      <InsertionOrderIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </InsertionOrderIds>
    </GetInsertionOrdersByAccountRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetInsertionOrdersByAccountResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*InsertionOrders*|A list of insertion orders.|[InsertionOrder](../billing-api/insertionorder-data-object.md) array|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[bill_response_header_table](../billing-api/includes/bill-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Billing/v11">
    <TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  </s:Header>
  <s:Body>
    <GetInsertionOrdersByAccountResponse xmlns="https://bingads.microsoft.com/Billing/v11">
      <InsertionOrders xmlns:e5="https://bingads.microsoft.com/Customer/v11/Entities" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e5:InsertionOrder>
          <e5:AccountId></e5:AccountId>
          <e5:BalanceAmount p5:nil="false"></e5:BalanceAmount>
          <e5:BookingCountryCode p5:nil="false"></e5:BookingCountryCode>
          <e5:Comment p5:nil="false"></e5:Comment>
          <e5:EndDate></e5:EndDate>
          <e5:InsertionOrderId p5:nil="false"></e5:InsertionOrderId>
          <e5:LastModifiedByUserId p5:nil="false"></e5:LastModifiedByUserId>
          <e5:LastModifiedTime p5:nil="false"></e5:LastModifiedTime>
          <e5:NotificationThreshold p5:nil="false"></e5:NotificationThreshold>
          <e5:ReferenceId p5:nil="false"></e5:ReferenceId>
          <e5:SpendCapAmount></e5:SpendCapAmount>
          <e5:StartDate></e5:StartDate>
          <e5:Name p5:nil="false"></e5:Name>
          <e5:Status p5:nil="false"></e5:Status>
          <e5:PurchaseOrder p5:nil="false"></e5:PurchaseOrder>
          <e5:ChangePendingReview p5:nil="false"></e5:ChangePendingReview>
        </e5:InsertionOrder>
      </InsertionOrders>
    </GetInsertionOrdersByAccountResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[billingerror](../billing-api/includes/billingerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
