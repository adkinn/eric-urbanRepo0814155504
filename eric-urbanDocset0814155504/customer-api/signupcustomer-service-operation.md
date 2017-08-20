---
title: "SignupCustomer Service Operation"
ms.custom: ""
ms.date: "08/01/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 83a6d769-df9a-4295-9f0e-c3fe74e00b18
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SignupCustomer Service Operation
Signs up a customer with [!INCLUDE[brand](../customer-api/includes/brand.md)].

||
|-|
|[!INCLUDE[cusman_navigation_noremarks](../customer-api/includes/cusman-navigation-noremarks.md)]|

## <a name="request"></a>SignupCustomerRequest Message

### Request Body
The *SignupCustomerRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*Account*|An [Account](../customer-api/account-data-object.md) that specifies the details of the customer’s primary account.<br /><br />**Note**: Do not instantiate the *Account* data object. Instead, instantiate the [AdvertiserAccount](../customer-api/advertiseraccount-data-object.md) that derives from the *Account* data object.|[Account](../customer-api/account-data-object.md)|Yes|
|*ApplicationScope*|Determines  the type of customer application. The default is Advertiser.<br /><br />The scope of this customer and the scope of the parent customer must be the same; for example, they must both be set to Advertiser.|[ApplicationType](../customer-api/applicationtype-value-set.md)|No|
|*Customer*|A [Customer](../customer-api/customer-data-object.md) that specifies the details of the customer that you are adding.|[Customer](../customer-api/customer-data-object.md)|Yes|
|*ParentCustomerId*|The customer identifier of the reseller that will manage this customer.|*long*|Yes|

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
    <Action mustUnderstand="1">SignupCustomer</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <SignupCustomerRequest xmlns="https://bingads.microsoft.com/Customer/v11">
      \<Customer xmlns:e46="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false">
        \<e46:CustomerAddress i:nil="false">
          \<e46:City i:nil="false">\</e46:City>
          \<e46:CountryCode i:nil="false">\</e46:CountryCode>
          \<e46:Id i:nil="false">\</e46:Id>
          \<e46:Line1 i:nil="false">\</e46:Line1>
          \<e46:Line2 i:nil="false">\</e46:Line2>
          \<e46:Line3 i:nil="false">\</e46:Line3>
          \<e46:Line4 i:nil="false">\</e46:Line4>
          \<e46:PostalCode i:nil="false">\</e46:PostalCode>
          \<e46:StateOrProvince i:nil="false">\</e46:StateOrProvince>
          \<e46:TimeStamp i:nil="false">\</e46:TimeStamp>
        \</e46:CustomerAddress>
        \<e46:CustomerFinancialStatus i:nil="false">\</e46:CustomerFinancialStatus>
        \<e46:Id i:nil="false">\</e46:Id>
        \<e46:Industry i:nil="false">\</e46:Industry>
        \<e46:LastModifiedByUserId i:nil="false">\</e46:LastModifiedByUserId>
        \<e46:LastModifiedTime i:nil="false">\</e46:LastModifiedTime>
        \<e46:MarketCountry i:nil="false">\</e46:MarketCountry>
        \<ForwardCompatibilityMap xmlns:e47="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
          \<e47:KeyValuePairOfstringstring>
            \<e47:key i:nil="false">\</e47:key>
            \<e47:value i:nil="false">\</e47:value>
          \</e47:KeyValuePairOfstringstring>
        </ForwardCompatibilityMap>
        \<e46:MarketLanguage i:nil="false">\</e46:MarketLanguage>
        \<e46:Name i:nil="false">\</e46:Name>
        \<e46:ServiceLevel i:nil="false">\</e46:ServiceLevel>
        \<e46:CustomerLifeCycleStatus i:nil="false">\</e46:CustomerLifeCycleStatus>
        \<e46:TimeStamp i:nil="false">\</e46:TimeStamp>
        \<e46:Number i:nil="false">\</e46:Number>
      </Customer>
      \<Account xmlns:e48="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false" i:type="-- specify derived type here with the appropriate prefix --">
        \<e48:AccountType>\</e48:AccountType>
        \<e48:BillToCustomerId i:nil="false">\</e48:BillToCustomerId>
        \<e48:CountryCode i:nil="false">\</e48:CountryCode>
        \<e48:CurrencyType i:nil="false">\</e48:CurrencyType>
        \<e48:AccountFinancialStatus i:nil="false">\</e48:AccountFinancialStatus>
        \<e48:Id i:nil="false">\</e48:Id>
        \<e48:Language i:nil="false">\</e48:Language>
        \<ForwardCompatibilityMap xmlns:e49="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
          \<e49:KeyValuePairOfstringstring>
            \<e49:key i:nil="false">\</e49:key>
            \<e49:value i:nil="false">\</e49:value>
          \</e49:KeyValuePairOfstringstring>
        </ForwardCompatibilityMap>
        \<e48:LastModifiedByUserId i:nil="false">\</e48:LastModifiedByUserId>
        \<e48:LastModifiedTime i:nil="false">\</e48:LastModifiedTime>
        \<e48:Name i:nil="false">\</e48:Name>
        \<e48:Number i:nil="false">\</e48:Number>
        \<e48:ParentCustomerId>\</e48:ParentCustomerId>
        \<e48:PaymentMethodId i:nil="false">\</e48:PaymentMethodId>
        \<e48:PaymentMethodType i:nil="false">\</e48:PaymentMethodType>
        \<e48:PrimaryUserId i:nil="false">\</e48:PrimaryUserId>
        \<e48:AccountLifeCycleStatus i:nil="false">\</e48:AccountLifeCycleStatus>
        \<e48:TimeStamp i:nil="false">\</e48:TimeStamp>
        \<e48:TimeZone i:nil="false">\</e48:TimeZone>
        \<e48:PauseReason i:nil="false">\</e48:PauseReason>
        \<!--Keep these fields if you set the i:type attribute to AdvertiserAccount-->
        \<e48:LinkedAgencies i:nil="false">
          \<e48:CustomerInfo>
            \<e48:Id i:nil="false">\</e48:Id>
            \<e48:Name i:nil="false">\</e48:Name>
          \</e48:CustomerInfo>
        \</e48:LinkedAgencies>
        \<e48:SalesHouseCustomerId i:nil="false">\</e48:SalesHouseCustomerId>
        \<TaxInformation xmlns:e50="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
          \<e50:KeyValuePairOfstringstring>
            \<e50:key i:nil="false">\</e50:key>
            \<e50:value i:nil="false">\</e50:value>
          \</e50:KeyValuePairOfstringstring>
        </TaxInformation>
        \<e48:BackUpPaymentInstrumentId i:nil="false">\</e48:BackUpPaymentInstrumentId>
        \<e48:BillingThresholdAmount i:nil="false">\</e48:BillingThresholdAmount>
        \<e48:BusinessAddress i:nil="false">
          \<e48:City i:nil="false">\</e48:City>
          \<e48:CountryCode i:nil="false">\</e48:CountryCode>
          \<e48:Id i:nil="false">\</e48:Id>
          \<e48:Line1 i:nil="false">\</e48:Line1>
          \<e48:Line2 i:nil="false">\</e48:Line2>
          \<e48:Line3 i:nil="false">\</e48:Line3>
          \<e48:Line4 i:nil="false">\</e48:Line4>
          \<e48:PostalCode i:nil="false">\</e48:PostalCode>
          \<e48:StateOrProvince i:nil="false">\</e48:StateOrProvince>
          \<e48:TimeStamp i:nil="false">\</e48:TimeStamp>
        \</e48:BusinessAddress>
      </Account>
      \<ParentCustomerId i:nil="false"></ParentCustomerId>
      <ApplicationScope></ApplicationScope>
    </SignupCustomerRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>SignupCustomerResponse Message

### <a name="Body_Elements"></a>Response Body
> [!NOTE]
> Identifiers returned in the response may not be immediately available . As a best practice, you should not use customer and account identifiers in subsequent service calls until 10-30 seconds after receiving the response from *SignupCustomer*.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountId*|A system-generated account identifier corresponding to the new account specified in the request.<br /><br />Use this identifier with operation requests that require an *AccountId* element and a *CustomerAccountId* SOAP header element.|*long*|
|*AccountNumber*|A system-generated account number that is used to identify the account in the [!INCLUDE[brand](../customer-api/includes/brand.md)] web application. The account number has the form, X*nnnnnnn*, where *nnnnnnn* is a series of digits.|*string*|
|*CreateTime*|The date and time that the account was added. The date and time value reflects the date and time at the server, not the client. For information about the format of the date and time, see the dateTime entry in [Primitive XML Data Types](http://msdn.microsoft.com/library/ms256220.aspx).|*dateTime*|
|*CustomerId*|A system-generated customer identifier corresponding to the new customer specified in the request.<br /><br />Use this identifier with operation requests that require a *CustomerId* SOAP header element.|*long*|
|*CustomerNumber*|A system-generated customer number that is used in the [!INCLUDE[brand](../customer-api/includes/brand.md)] web application. The customer number is of the form, C*nnnnnnn*, where *nnnnnnn* is a series of digits.|*string*|

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
    <SignupCustomerResponse xmlns="https://bingads.microsoft.com/Customer/v11">
      <CustomerId></CustomerId>
      \<CustomerNumber p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></CustomerNumber>
      \<AccountId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></AccountId>
      \<AccountNumber p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></AccountNumber>
      <CreateTime></CreateTime>
    </SignupCustomerResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cusmanerror](../customer-api/includes/cusmanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Code|
|--------|
|105|
|310|
