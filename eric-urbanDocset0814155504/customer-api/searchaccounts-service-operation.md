---
title: "SearchAccounts Service Operation"
ms.custom: ""
ms.date: "08/01/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d105e7b5-448d-4d2e-ab9b-fdb28a17c439
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SearchAccounts Service Operation
Searches for accounts that match a specified criteria.

||
|-|
|[!INCLUDE[cusman_navigation_noremarks](../customer-api/includes/cusman-navigation-noremarks.md)]|

## <a name="request"></a>SearchAccountsRequest Message
The *SearchAccountsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

### Request Body

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*Ordering*|Determines the order of results by the specified property of an account<br/><br/>**Note:** You should only specify one *OrderBy* element in the array. Additional elements are not supported and will be ignored by the service.<br /><br />For this service operation, the following values are supported in the *Field* element of a *OrderBy* object.<br /><br />*Id* - The order is determined by the *Id*element of the returned [Account](../customer-api/account-data-object.md).<br /><br />*Name* - The order is determined by the *Name* element of the returned [Account](../customer-api/account-data-object.md).<br /><br />*Number* - The order is determined by the *Number* element of the returned [Account](../customer-api/account-data-object.md).|[OrderBy](../customer-api/orderby-data-object.md) array|No|
|*PageInfo*|Determines the index and size of  results per page.|[Paging](../customer-api/paging-data-object.md)|Yes|
|*Predicates*|Determines the request conditions. This operation's response will include accounts that match all of the specified predicates.<br/><br/>**Note:** With the exception of AccountLifeCycleStatus, you must specify exactly one predicate. When using the AccountLifeCycleStatus predicate field you must specify one additional predicate, for example with the *Field* set to UserId.<br /><br />For a list of supported *Field* and *Operator* elements of a *Predicate* object for this service operation, see [Predicate Field and Operator](#predicates).|[Predicate](../customer-api/predicate-data-object.md) array|Yes|

#### <a name="predicates"></a>Predicate Field and Operator
For this service operation, the following are supported *Field* element and *Operator* elements of a *Predicate* object.

|Field|Operator|Description|
|---------|------------|---------------|
|AccountId|*Equals*<br /><br />*In*|Use this field to search the *Id* element of the [Account](../customer-api/account-data-object.md).|
|AccountLifeCycleStatus|*Equals*|Use this field to search the *AccountLifeCycleStatus* element of the [Account](../customer-api/account-data-object.md).<br /><br />Possible values include any string representation of the [AccountLifeCycleStatus](../customer-api/accountlifecyclestatus-value-set.md), for example `Value = AccountLifeCycleStatus.Active.ToString()` or `Value="Active"` .|
|AccountName|*Contains*<br /><br />*Equals*|Use this field to search the *Name* element of the [Account](../customer-api/account-data-object.md).|
|AccountNumber|*Contains*<br /><br />*Equals*<br /><br />*In*|Use this field to search the *Number* element of the [Account](../customer-api/account-data-object.md).|
|CustomerId|*Equals*|Use this field to search the *Id* element of the [Customer](../customer-api/customer-data-object.md).|
|UserId|*Equals*|Use this field to search the *UserId* element of the  [User](../customer-api/user-data-object.md).|

### Request Headers
[!INCLUDE[header_intro](../customer-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[cusman_header_oauth](../customer-api/includes/cusman-header-oauth.md)]
#### Password Authentication
[!INCLUDE[cusman_header_password](../customer-api/includes/cusman-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
\<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="https://bingads.microsoft.com/Customer/v11">
    <Action mustUnderstand="1">SearchAccounts</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <SearchAccountsRequest xmlns="https://bingads.microsoft.com/Customer/v11">
      \<Predicates xmlns:e23="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false">
        \<e23:Predicate>
          \<e23:Field i:nil="false">\</e23:Field>
          \<e23:Operator>\</e23:Operator>
          \<e23:Value i:nil="false">\</e23:Value>
        \</e23:Predicate>
      </Predicates>
      \<Ordering xmlns:e24="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false">
        \<e24:OrderBy>
          \<e24:Field>\</e24:Field>
          \<e24:Order>\</e24:Order>
        \</e24:OrderBy>
      </Ordering>
      \<PageInfo xmlns:e25="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false">
        \<e25:Index>\</e25:Index>
        \<e25:Size>\</e25:Size>
      </PageInfo>
    </SearchAccountsRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>SearchAccountsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Accounts*|A  list of accounts that meet the specified criteria.|[Account](../customer-api/account-data-object.md) array|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[cusman_response_header_table](../customer-api/includes/cusman-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
\<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="https://bingads.microsoft.com/Customer/v11">
    \<TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  \</s:Header>
  \<s:Body>
    <SearchAccountsResponse xmlns="https://bingads.microsoft.com/Customer/v11">
      \<Accounts xmlns:e29="https://bingads.microsoft.com/Customer/v11/Entities" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        \<e29:Account p5:type="-- specify derived type here with the appropriate prefix --">
          \<e29:AccountType>\</e29:AccountType>
          \<e29:BillToCustomerId p5:nil="false">\</e29:BillToCustomerId>
          \<e29:CountryCode p5:nil="false">\</e29:CountryCode>
          \<e29:CurrencyType p5:nil="false">\</e29:CurrencyType>
          \<e29:AccountFinancialStatus p5:nil="false">\</e29:AccountFinancialStatus>
          \<e29:Id p5:nil="false">\</e29:Id>
          \<e29:Language p5:nil="false">\</e29:Language>
          \<ForwardCompatibilityMap xmlns:e30="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p5:nil="false">
            \<e30:KeyValuePairOfstringstring>
              \<e30:key p5:nil="false">\</e30:key>
              \<e30:value p5:nil="false">\</e30:value>
            \</e30:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          \<e29:LastModifiedByUserId p5:nil="false">\</e29:LastModifiedByUserId>
          \<e29:LastModifiedTime p5:nil="false">\</e29:LastModifiedTime>
          \<e29:Name p5:nil="false">\</e29:Name>
          \<e29:Number p5:nil="false">\</e29:Number>
          \<e29:ParentCustomerId>\</e29:ParentCustomerId>
          \<e29:PaymentMethodId p5:nil="false">\</e29:PaymentMethodId>
          \<e29:PaymentMethodType p5:nil="false">\</e29:PaymentMethodType>
          \<e29:PrimaryUserId p5:nil="false">\</e29:PrimaryUserId>
          \<e29:AccountLifeCycleStatus p5:nil="false">\</e29:AccountLifeCycleStatus>
          \<e29:TimeStamp p5:nil="false">\</e29:TimeStamp>
          \<e29:TimeZone p5:nil="false">\</e29:TimeZone>
          \<e29:PauseReason p5:nil="false">\</e29:PauseReason>
          \<!--Keep these fields if you set the i:type attribute to AdvertiserAccount-->
          \<e29:LinkedAgencies p5:nil="false">
            \<e29:CustomerInfo>
              \<e29:Id p5:nil="false">\</e29:Id>
              \<e29:Name p5:nil="false">\</e29:Name>
            \</e29:CustomerInfo>
          \</e29:LinkedAgencies>
          \<e29:SalesHouseCustomerId p5:nil="false">\</e29:SalesHouseCustomerId>
          \<TaxInformation xmlns:e31="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p5:nil="false">
            \<e31:KeyValuePairOfstringstring>
              \<e31:key p5:nil="false">\</e31:key>
              \<e31:value p5:nil="false">\</e31:value>
            \</e31:KeyValuePairOfstringstring>
          </TaxInformation>
          \<e29:BackUpPaymentInstrumentId p5:nil="false">\</e29:BackUpPaymentInstrumentId>
          \<e29:BillingThresholdAmount p5:nil="false">\</e29:BillingThresholdAmount>
          \<e29:BusinessAddress p5:nil="false">
            \<e29:City p5:nil="false">\</e29:City>
            \<e29:CountryCode p5:nil="false">\</e29:CountryCode>
            \<e29:Id p5:nil="false">\</e29:Id>
            \<e29:Line1 p5:nil="false">\</e29:Line1>
            \<e29:Line2 p5:nil="false">\</e29:Line2>
            \<e29:Line3 p5:nil="false">\</e29:Line3>
            \<e29:Line4 p5:nil="false">\</e29:Line4>
            \<e29:PostalCode p5:nil="false">\</e29:PostalCode>
            \<e29:StateOrProvince p5:nil="false">\</e29:StateOrProvince>
            \<e29:TimeStamp p5:nil="false">\</e29:TimeStamp>
          \</e29:BusinessAddress>
        \</e29:Account>
      </Accounts>
    </SearchAccountsResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cusmanerror](../customer-api/includes/cusmanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
