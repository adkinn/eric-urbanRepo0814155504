---
title: "BillingDocumentInfo Data Object"
ms.custom: ""
ms.date: "05/27/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d2174fd-2565-4411-98f6-b6270360fb6a
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BillingDocumentInfo Data Object
Defines a billing document identification object that contains information about a billing document, such as the billing document identifier, billing document amount, and account identifier.

## Syntax

```xml
<xs:complexType name="BillingDocumentInfo">
  <xs:sequence>
    <xs:element minOccurs="0" name="AccountId" type="xsd:long" />
    <xs:element minOccurs="0" name="AccountName" nillable="true" type="xsd:string" />
    <xs:element minOccurs="0" name="AccountNumber" nillable="true" type="xsd:string" />
    <xs:element minOccurs="0" name="Amount" type="xsd:double" />
    <xs:element minOccurs="0" name="CurrencyCode" nillable="true" type="xsd:string" />
    <xs:element minOccurs="0" name="DocumentDate" nillable="true" type="xsd:dateTime" />
    <xs:element minOccurs="0" name="DocumentId" nillable="true" type="xsd:long" />
  </xs:sequence>
</xs:complexType>
```

## <a name="elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountId*|The identifier of the account for which the billing document was generated.|*long*|
|*AccountName*|The account name.|*string*|
|*AccountNumber*|The account number.|*string*|
|*Amount*|The amount of the billing document.|*double*|
|*CurrencyCode*|The currency of the billing document. For possible values, see [Currencies](http://msdn.microsoft.com/library/bing-ads-currencies.aspx).|*string*|
|*DocumentDate*|The date of the billing document.|*dateTime*|
|*DocumentId*|An identifier of the billing document.|*long*|

## Remarks
The *BillingDocumentInfo* data object contains information about the billing document, whereas the [BillingDocument](../billing-api/billingdocument-data-object.md) data object contains the actual billing document.

To get the billing document, pass the *DocumentId* within the *DocumentIds* array in the request to the [GetBillingDocuments](../billing-api/getbillingdocuments-service-operation.md) operation.

## Requirements
[!INCLUDE[reqbilling](../billing-api/includes/reqbilling.md)]
## See Also
[GetBillingDocumentsInfo](../billing-api/getbillingdocumentsinfo-service-operation.md)  

