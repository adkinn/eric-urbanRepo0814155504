---
title: "SearchClientLinks Service Operation"
ms.custom: ""
ms.date: "06/21/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a8bb8f82-d737-48fc-ba58-641d4d59a955
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SearchClientLinks Service Operation
[!INCLUDE[sandbox_clientlink](../customer-api/includes/sandbox-clientlink.md)]Searches for the client links for the customer of the current authenticated user, filtered by the search criteria. The operation returns the most recent link for each unique combination of agency customer and client account. For more information about the client link lifecycle, see [Link to Client Accounts](http://go.microsoft.com/fwlink/?LinkId=691023).

If your user is within a client customer that has one or more accounts managed by an agency, then you may search one at a time for individual accounts that were or are eligible to be linked. To search by individual account, set the predicate field to ClientAccountId and set the predicate value to the account identifier that you want to find.

The role of the user calling this operation must be Super Admin. For more information, see [User Roles and Available Service Operations](http://go.microsoft.com/fwlink/?LinkId=691022).

||
|-|
|[!INCLUDE[cusman_navigation_noremarks](../customer-api/includes/cusman-navigation-noremarks.md)]|

## <a name="request"></a>SearchClientLinksRequest Message

### Request Body
The *SearchClientLinksRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*Ordering*|Determines the order of results.<br /><br />**Note**: If specified, you should only include one *OrderBy* element in the list. Additional elements are not supported and will be ignored by the service.<br /><br />For this service operation, the following values are supported in the *Field* element of a *OrderBy* object.<br /><br />*Id* - The order is determined by the *ClientAccountId* element of the returned [ClientLink](../customer-api/clientlink-data-object.md).<br /><br />*Name* - The order is determined by the *Name* element of the returned [ClientLink](../customer-api/clientlink-data-object.md).<br /><br />*Number* - The order is determined by the *ManagingCustomerNumber* element of the returned [ClientLink](../customer-api/clientlink-data-object.md).|[OrderBy](../customer-api/orderby-data-object.md) array|No|
|*PageInfo*|Determines the index and size of  results per page.|[Paging](../customer-api/paging-data-object.md)|Yes|
|*Predicates*|Determines the request conditions. This operation's response will include client links that match all of the specified predicates.<br /><br />**Note**: You can specify either one or two predicates.<br /><br />For a list of supported *Field* and *Operator* elements of a *Predicate* object for this service operation, see [Predicate Field and Operator](#predicates).|[Predicate](../customer-api/predicate-data-object.md) array|Yes|

#### <a name="predicates"></a>Predicate Field and Operator
For this service operation, the following are supported *Field* element and *Operator* elements of a *Predicate* object.

|Field|Operator|Description|
|---------|------------|---------------|
|ClientAccountId|*Equals*<br /><br />*In*|Use this field to search the *ClientAccountId* element of the [ClientLink](../customer-api/clientlink-data-object.md).|
|ManagingCustomerId|*Equals*|Use this field to search the *ManagingCustomerId* element of the [ClientLink](../customer-api/clientlink-data-object.md).|

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
    <Action mustUnderstand="1">SearchClientLinks</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <SearchClientLinksRequest xmlns="https://bingads.microsoft.com/Customer/v11">
      <Predicates xmlns:e28="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false">
        <e28:Predicate>
          <e28:Field i:nil="false"></e28:Field>
          <e28:Operator></e28:Operator>
          <e28:Value i:nil="false"></e28:Value>
        </e28:Predicate>
      </Predicates>
      <Ordering xmlns:e29="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false">
        <e29:OrderBy>
          <e29:Field></e29:Field>
          <e29:Order></e29:Order>
        </e29:OrderBy>
      </Ordering>
      <PageInfo xmlns:e30="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false">
        <e30:Index></e30:Index>
        <e30:Size></e30:Size>
      </PageInfo>
    </SearchClientLinksRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>SearchClientLinksResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ClientLinks*|The list of client link invitations.|[ClientLink](../customer-api/clientlink-data-object.md) array|

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
    <SearchClientLinksResponse xmlns="https://bingads.microsoft.com/Customer/v11">
      <ClientLinks xmlns:e31="https://bingads.microsoft.com/Customer/v11/Entities" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e31:ClientLink>
          <e31:ClientAccountId p5:nil="false"></e31:ClientAccountId>
          <e31:ClientAccountNumber p5:nil="false"></e31:ClientAccountNumber>
          <e31:ManagingCustomerId p5:nil="false"></e31:ManagingCustomerId>
          <e31:ManagingCustomerNumber p5:nil="false"></e31:ManagingCustomerNumber>
          <e31:Note p5:nil="false"></e31:Note>
          <e31:Name p5:nil="false"></e31:Name>
          <e31:InviterEmail p5:nil="false"></e31:InviterEmail>
          <e31:InviterName p5:nil="false"></e31:InviterName>
          <e31:InviterPhone p5:nil="false"></e31:InviterPhone>
          <e31:IsBillToClient></e31:IsBillToClient>
          <e31:StartDate p5:nil="false"></e31:StartDate>
          <e31:Status p5:nil="false"></e31:Status>
          <e31:SuppressNotification></e31:SuppressNotification>
          <e31:LastModifiedDateTime></e31:LastModifiedDateTime>
          <e31:LastModifiedByUserId></e31:LastModifiedByUserId>
          <e31:Timestamp p5:nil="false"></e31:Timestamp>
          <ForwardCompatibilityMap xmlns:e32="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p5:nil="false">
            <e32:KeyValuePairOfstringstring>
              <e32:key p5:nil="false"></e32:key>
              <e32:value p5:nil="false"></e32:value>
            </e32:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
        </e31:ClientLink>
      </ClientLinks>
    </SearchClientLinksResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cusmanerror](../customer-api/includes/cusmanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AddClientLinks](../customer-api/addclientlinks-service-operation.md)  
[UpdateClientLinks](../customer-api/updateclientlinks-service-operation.md)  

