---
title: "Customer Data Object"
ms.custom: ""
ms.date: "08/01/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a4c8e03e-e494-4fb7-9dbb-3bea2f095249
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Customer Data Object
Defines a customer.

## Syntax

```xml
<xs:complexType name="Customer">
  <xs:sequence>
    <xs:element minOccurs="0" name="CustomerAddress" nillable="true" type="tns:Address" />
    <xs:element minOccurs="0" name="CustomerFinancialStatus" nillable="true" type="tns:CustomerFinancialStatus" />
    <xs:element minOccurs="0" name="Id" nillable="true" type="xsd:long" />
    <xs:element minOccurs="0" name="Industry" nillable="true" type="tns:Industry" />
    <xs:element minOccurs="0" name="LastModifiedByUserId" nillable="true" type="xsd:long" />
    <xs:element minOccurs="0" name="LastModifiedTime" nillable="true" type="xsd:dateTime" />
    <xs:element minOccurs="0" name="MarketCountry" nillable="true" type="tns:String" />
    <xs:element minOccurs="0" name="ForwardCompatibilityMap" xmlns:q2="http://schemas.datacontract.org/2004/07/System.Collections.Generic" nillable="true" type="q2:ArrayOfKeyValuePairOfstringstring" />
    <xs:element minOccurs="0" name="MarketLanguage" nillable="true" type="tns:LanguageType" />
    <xs:element minOccurs="0" name="Name" nillable="true" type="xsd:string" />
    <xs:element minOccurs="0" name="ServiceLevel" nillable="true" type="tns:ServiceLevel" />
    <xs:element minOccurs="0" name="CustomerLifeCycleStatus" nillable="true" type="tns:CustomerLifeCycleStatus" />
    <xs:element minOccurs="0" name="TimeStamp" nillable="true" type="xs:base64Binary" />
    <xs:element minOccurs="0" name="Number" nillable="true" type="xs:string" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CustomerAddress*|The customer's business address.<br/><br/>**Add:** Required<br/>**Update:** Required|[Address](../customer-api/address-data-object.md)|
|*CustomerFinancialStatus*|The financial status of the customer. For example, the status indicates whether the customer is in good standing or one or more of the accounts are past due.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[CustomerFinancialStatus](../customer-api/customerfinancialstatus-value-set.md)|
|*CustomerLifeCycleStatus*|The status of the customer. When you create the customer, the status is set to *Active*. You cannot change the status.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[CustomerLifeCycleStatus](../customer-api/customerlifecyclestatus-value-set.md)|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />**Note:** Forward compatibility changes will be noted here in future releases. There are currently no forward compatibility changes for the *Customer* object.|*KeyValuePairOfstringstring* array|
|*Id*|The system generated customer identifier.<br /><br />Use this identifier with operation requests that require a *CustomerId* SOAP header element.<br/><br/>**Add:** Read-only<br/>**Update:** Required|*long*|
|*Industry*|The primary business segment of the customer, for example, automotive, food, or entertainment.<br/><br/>**Add:** Required<br/>**Update:** Required|[Industry](../customer-api/industry-value-set.md)|
|*LastModifiedByUserId*|The identifier of the last user to update the customer’s information.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*long*|
|*LastModifiedTime*|The date and time that the customer information was last updated. The value is in Coordinated Universal Time (UTC).<br /><br />The date and time value reflects the date and time at the server, not the client. For information about the format of the date and time, see the **dateTime** entry in [Primitive XML Data Types](https://msdn.microsoft.com/library/ms256220.aspx).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*dateTime*|
|*MarketCountry*|The primary country where the customer operates. For a list of customer market country code values, see [Product Language](https://msdn.microsoft.com/library/bing-ads-ad-languages.aspx#productlanguage).<br/><br/>**Add:** Required<br/>**Update:** Read-only|*string*|
|*MarketLanguage*|The primary language that the customer uses. Your customer market language determines the language of the Bing Ads interface. For a list of customer market language code values, see [Product Language](https://msdn.microsoft.com/library/bing-ads-ad-languages.aspx#productlanguage).<br/><br/>**Add:** Required<br/>**Update:** Read-only|[LanguageType](../customer-api/languagetype-value-set.md)|
|*Name*|The name of the customer. The name can contain a maximum of 100 characters.<br/><br/>**Add:** Required<br/>**Update:** Required|*string*|
|*Number*|A system-generated customer number that is used in the [!INCLUDE[brand](../customer-api/includes/brand.md)] web application. The customer number is of the form, C*nnnnnnn*, where *nnnnnnn* is a series of digits.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|
|*ServiceLevel*|For internal use only. If this element is set when calling [SignupCustomer](../customer-api/signupcustomer-service-operation.md) an error will be returned. If this element is set when calling [UpdateCustomer](../customer-api/updatecustomer-service-operation.md) the element will be ignored.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[ServiceLevel](../customer-api/servicelevel-value-set.md)|
|*TimeStamp*|A time-stamp value that the system uses internally to reconcile updates when you call the [UpdateCustomer](../customer-api/updatecustomer-service-operation.md) and [DeleteCustomer](../customer-api/deletecustomer-service-operation.md) operations.<br/><br/>**Add:** Read-only<br/>**Update:** Required|*base64Binary*|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[GetCustomer](../customer-api/getcustomer-service-operation.md)  
[SignupCustomer](../customer-api/signupcustomer-service-operation.md)  
[UpdateCustomer](../customer-api/updatecustomer-service-operation.md)  

