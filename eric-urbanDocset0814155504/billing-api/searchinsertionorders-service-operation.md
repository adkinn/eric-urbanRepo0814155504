---
title: "SearchInsertionOrders Service Operation"
ms.custom: ""
ms.date: "06/21/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f180a0a1-8bcd-4dfb-9af4-011e2874c77d
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SearchInsertionOrders Service Operation
Searches for insertion orders that match a specified criteria.

||
|-|
|[!INCLUDE[bill_navigation_noremarks](../billing-api/includes/bill-navigation-noremarks.md)]|

## <a name="request"></a>SearchInsertionOrdersRequest Message
The *SearchInsertionOrdersRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

### Request Body

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*Ordering*|Determines the order of results by the specified property of an account.<br /><br />**Note**: You should only specify one *OrderBy* element in the array. Additional elements are not supported and will be ignored by the service.<br /><br />For this service operation, the following values are supported in the *Field* element of a *OrderBy* object.<br /><br />*Id* - The order is determined by the *InsertionOrderId*element of the returned [InsertionOrder](../billing-api/insertionorder-data-object.md).<br /><br />*Name* - The order is determined by the *Name* element of the returned [InsertionOrder](../billing-api/insertionorder-data-object.md).|[OrderBy](../billing-api/orderby-data-object.md) array|No|
|*PageInfo*|Determines the index and size of  results per page.|[Paging](../billing-api/paging-data-object.md)|Yes|
|*Predicates*|Determines the request conditions. This operation's response will include accounts that match all of the specified predicates.<br /><br />**Note**: You may specify up to 6 predicates, and one of the predicate fields must be AccountId. You may use the StartDate and EndDate predicate fields twice each to specify start and end date ranges, and otherwise may only use each predicate field once.<br /><br />For a list of supported *Field* and *Operator* elements of a *Predicate* object for this service operation, see [Predicate Field and Operator](#predicates).|[Predicate](../billing-api/predicate-data-object.md) array|Yes|

#### <a name="predicates"></a>Predicate Field and Operator
For this service operation, the following are supported *Field* element and *Operator* elements of a *Predicate* object.

|Field|Operator|Description|
|---------|------------|---------------|
|AccountId|*Equals*|Use this field to search by the insertion order's account identifier.<br /><br />**Note**: This predicate field is required.|
|EndDate|*GreaterThanEquals*<br /><br />*LessThanEquals*|Use this field to search by insertion order end date. **Note**: The date is stored in Coordinated Universal Time (UTC). Only the month, day, and year of the specified string are used for search. If you specify the hour, minutes, and seconds of a date they will be ignored.<br /><br />For information about the format of the date and time, see the **dateTime** entry in [Primitive XML Data Types](http://msdn.microsoft.com/library/ms256220.aspx).|
|InsertionOrderIds|*Equals*<br /><br />*In*|Use this field to search the *InsertionOrderId* element of the [InsertionOrder](../billing-api/insertionorder-data-object.md).|
|StartDate|*GreaterThanEquals*<br /><br />*LessThanEquals*|Use this field to search by insertion order start date.<br /><br />**Note**: The date is stored in Coordinated Universal Time (UTC). Only the month, day, and year of the specified string are used for search. If you specify the hour, minutes, and seconds of a date they will be ignored.<br /><br />For information about the format of the date and time, see the **dateTime** entry in [Primitive XML Data Types](http://msdn.microsoft.com/library/ms256220.aspx).|

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
    <Action mustUnderstand="1">SearchInsertionOrders</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <SearchInsertionOrdersRequest xmlns="https://bingads.microsoft.com/Billing/v11">
      <Predicates xmlns:e7="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false">
        <e7:Predicate>
          <e7:Field i:nil="false"></e7:Field>
          <e7:Operator></e7:Operator>
          <e7:Value i:nil="false"></e7:Value>
        </e7:Predicate>
      </Predicates>
      <Ordering xmlns:e8="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false">
        <e8:OrderBy>
          <e8:Field></e8:Field>
          <e8:Order></e8:Order>
        </e8:OrderBy>
      </Ordering>
      <PageInfo xmlns:e9="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false">
        <e9:Index></e9:Index>
        <e9:Size></e9:Size>
      </PageInfo>
    </SearchInsertionOrdersRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>SearchInsertionOrdersResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*InsertionOrders*|A  list of insertion orders that meet the specified criteria.|[InsertionOrder](../billing-api/insertionorder-data-object.md) array|

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
    <SearchInsertionOrdersResponse xmlns="https://bingads.microsoft.com/Billing/v11">
      <InsertionOrders xmlns:e10="https://bingads.microsoft.com/Customer/v11/Entities" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e10:InsertionOrder>
          <e10:AccountId></e10:AccountId>
          <e10:BalanceAmount p5:nil="false"></e10:BalanceAmount>
          <e10:BookingCountryCode p5:nil="false"></e10:BookingCountryCode>
          <e10:Comment p5:nil="false"></e10:Comment>
          <e10:EndDate></e10:EndDate>
          <e10:InsertionOrderId p5:nil="false"></e10:InsertionOrderId>
          <e10:LastModifiedByUserId p5:nil="false"></e10:LastModifiedByUserId>
          <e10:LastModifiedTime p5:nil="false"></e10:LastModifiedTime>
          <e10:NotificationThreshold p5:nil="false"></e10:NotificationThreshold>
          <e10:ReferenceId p5:nil="false"></e10:ReferenceId>
          <e10:SpendCapAmount></e10:SpendCapAmount>
          <e10:StartDate></e10:StartDate>
          <e10:Name p5:nil="false"></e10:Name>
          <e10:Status p5:nil="false"></e10:Status>
          <e10:PurchaseOrder p5:nil="false"></e10:PurchaseOrder>
          <e10:ChangePendingReview p5:nil="false"></e10:ChangePendingReview>
        </e10:InsertionOrder>
      </InsertionOrders>
    </SearchInsertionOrdersResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[billingerror](../billing-api/includes/billingerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AddInsertionOrder](../billing-api/addinsertionorder-service-operation.md)  
[UpdateInsertionOrder](../billing-api/updateinsertionorder-service-operation.md)  

