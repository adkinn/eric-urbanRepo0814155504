---
title: "SearchCustomers Service Operation"
ms.custom: ""
ms.date: "08/01/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2aa11c81-d5f5-42c0-8874-4b1458ac1a19
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SearchCustomers Service Operation
Searches for customers that match a specified criteria.

||
|-|
|[!INCLUDE[cusman_navigation_noremarks](../customer-api/includes/cusman-navigation-noremarks.md)]|

## <a name="request"></a>SearchCustomersRequest Message
The *SearchCustomersRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

### Request Body

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*ApplicationScope*|A value that determines whether to return results for advertising customers or publishing customers. If you do not specify the scope, the list may include both types of customers.|[ApplicationType](../customer-api/applicationtype-value-set.md)|No|
|*DateRange*|Determines the minimum and maximum customer creation date range.|[DateRange](../customer-api/daterange-data-object.md)|No|
|*Ordering*|Determines the order of results by the specified property of a customer.<br /><br />**Note**: You should only specify one *OrderBy* element in the array. Additional elements are not supported and will be ignored by the service.<br /><br />For this service operation, the following values are supported in the *Field* element of a *OrderBy* object:<br /><br />*Id* - The order is determined by the *Id*element of the returned [Customer](../customer-api/customer-data-object.md).<br /><br />*Name* - The order is determined by the *Name* element of the returned [Customer](../customer-api/customer-data-object.md).<br /><br />*Number* - The order is determined by the *Number* element of the returned [Customer](../customer-api/customer-data-object.md).|[OrderBy](../customer-api/orderby-data-object.md) array|No|
|*PageInfo*|Determines the index and size of  results per page.|[Paging](../customer-api/paging-data-object.md)|Yes|
|*Predicates*|Determines the request conditions. This operation's response will include customers that match all of the specified predicates.<br /><br />**Note**: You may specify up to 10 predicates. You may use the CreatedDate predicate field twice to specify a created date range, and otherwise may only use each predicate field once.<br /><br />For a list of supported *Field* and *Operator* elements of a *Predicate* object for this service operation, see [Predicate Field and Operator](#predicates).|[Predicate](../customer-api/predicate-data-object.md) array|Yes|

#### <a name="predicates"></a>Predicate Field and Operator
For this service operation, the following are supported *Field* element and *Operator* elements of a *Predicate* object.

|Field|Operator|Description|
|---------|------------|---------------|
|AccountId|*Equals*|Use this field to search the *Id* element of the [Account](../customer-api/account-data-object.md).|
|AccountName|*Contains*<br /><br />*Equals*|Use this field to search the *Name* element of the [Account](../customer-api/account-data-object.md).|
|AccountNumber|*Contains*<br /><br />*Equals*|Use this field to search the *Number* element of the [Account](../customer-api/account-data-object.md).|
|ApplicationScope|*Equals*|For internal use only.|
|CreatedDate|*GreaterThanEquals*<br /><br />*LessThanEquals*|Use this field to search the date when the customer was created or signed up.<br /><br />**Note**: The date is stored in Coordinated Universal Time (UTC). Only the month, day, and year of the specified string are used for search. If you specify the hour, minutes, and seconds of a date they will be ignored.<br /><br />For information about the format of the date and time, see the **dateTime** entry in [Primitive XML Data Types](http://msdn.microsoft.com/library/ms256220.aspx).|
|CustomerId|*Equals*<br /><br />*In*|Use this field to search the *Id* element of the [Customer](../customer-api/customer-data-object.md).|
|CustomerName|*Contains*<br /><br />*Equals*|Use this field to search the *Name* element of the [Customer](../customer-api/customer-data-object.md).|
|CustomerNumber|*Contains*<br /><br />*Equals*|Use this field to search the *Number* element of the [Customer](../customer-api/customer-data-object.md).|
|Email|*Contains*<br /><br />*Equals*|Use this field to search the *Email* element of the [ContactInfo](../customer-api/contactinfo-data-object.md) within a [User](../customer-api/user-data-object.md).|
|MarketCountry|*Equals*|Use this field to search the *MarketCountry* element of the [Customer](../customer-api/customer-data-object.md).<br /><br />**Note**: The *MarketCountry* and *MarketLanguage* predicate fields are not required; however, if either is specified then both are required.|
|MarketLanguage|*Equals*|Use this field to search the *MarketLanguage* element of the [Customer](../customer-api/customer-data-object.md).<br /><br />**Note**: The *MarketCountry* and *MarketLanguage* predicate fields are not required; however, if either is specified then both are required.|
|PersonName|*Contains*<br /><br />*Equals*|Use this field to search the combined *FirstName*, *MiddleInitial*,   and *LastName* elements of the [PersonName](../customer-api/personname-data-object.md) within a [User](../customer-api/user-data-object.md).<br /><br />The string value corresponding to elements within *PersonName* should be separated by spaces in the order of *FirstName*, *MiddleInitial*,   and *LastName*.|
|UserName|*Contains*<br /><br />*Equals*|Use this field to search the *UserName* element of the  [User](../customer-api/user-data-object.md).|
|TaxId|*Contains*<br /><br />*Equals*|For internal use only.|

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
    <Action mustUnderstand="1">SearchCustomers</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <SearchCustomersRequest xmlns="https://bingads.microsoft.com/Customer/v11">
      <ApplicationScope></ApplicationScope>
      <Predicates xmlns:e19="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false">
        <e19:Predicate>
          <e19:Field i:nil="false"></e19:Field>
          <e19:Operator></e19:Operator>
          <e19:Value i:nil="false"></e19:Value>
        </e19:Predicate>
      </Predicates>
      <DateRange xmlns:e20="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false">
        <e20:MinDate i:nil="false"></e20:MinDate>
        <e20:MaxDate i:nil="false"></e20:MaxDate>
      </DateRange>
      <Ordering xmlns:e21="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false">
        <e21:OrderBy>
          <e21:Field></e21:Field>
          <e21:Order></e21:Order>
        </e21:OrderBy>
      </Ordering>
      <PageInfo xmlns:e22="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false">
        <e22:Index></e22:Index>
        <e22:Size></e22:Size>
      </PageInfo>
    </SearchCustomersRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>SearchCustomersResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Customers*|A  list of customers that meet the specified criteria.|[Customer](../customer-api/customer-data-object.md) array|

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
    <SearchCustomersResponse xmlns="https://bingads.microsoft.com/Customer/v11">
      <Customers xmlns:e23="https://bingads.microsoft.com/Customer/v11/Entities" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e23:Customer>
          <e23:CustomerAddress p5:nil="false">
            <e23:City p5:nil="false"></e23:City>
            <e23:CountryCode p5:nil="false"></e23:CountryCode>
            <e23:Id p5:nil="false"></e23:Id>
            <e23:Line1 p5:nil="false"></e23:Line1>
            <e23:Line2 p5:nil="false"></e23:Line2>
            <e23:Line3 p5:nil="false"></e23:Line3>
            <e23:Line4 p5:nil="false"></e23:Line4>
            <e23:PostalCode p5:nil="false"></e23:PostalCode>
            <e23:StateOrProvince p5:nil="false"></e23:StateOrProvince>
            <e23:TimeStamp p5:nil="false"></e23:TimeStamp>
          </e23:CustomerAddress>
          <e23:CustomerFinancialStatus p5:nil="false"></e23:CustomerFinancialStatus>
          <e23:Id p5:nil="false"></e23:Id>
          <e23:Industry p5:nil="false"></e23:Industry>
          <e23:LastModifiedByUserId p5:nil="false"></e23:LastModifiedByUserId>
          <e23:LastModifiedTime p5:nil="false"></e23:LastModifiedTime>
          <e23:MarketCountry p5:nil="false"></e23:MarketCountry>
          <ForwardCompatibilityMap xmlns:e24="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p5:nil="false">
            <e24:KeyValuePairOfstringstring>
              <e24:key p5:nil="false"></e24:key>
              <e24:value p5:nil="false"></e24:value>
            </e24:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <e23:MarketLanguage p5:nil="false"></e23:MarketLanguage>
          <e23:Name p5:nil="false"></e23:Name>
          <e23:ServiceLevel p5:nil="false"></e23:ServiceLevel>
          <e23:CustomerLifeCycleStatus p5:nil="false"></e23:CustomerLifeCycleStatus>
          <e23:TimeStamp p5:nil="false"></e23:TimeStamp>
          <e23:Number p5:nil="false"></e23:Number>
        </e23:Customer>
      </Customers>
    </SearchCustomersResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cusmanerror](../customer-api/includes/cusmanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
