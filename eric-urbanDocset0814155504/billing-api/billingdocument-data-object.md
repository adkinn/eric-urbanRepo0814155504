---
title: "BillingDocument Data Object"
ms.custom: ""
ms.date: "05/27/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e9ffe72e-008d-4fdd-90cd-0f9cbce04544
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BillingDocument Data Object
Defines a billing document.

## Syntax

```xml
<xs:complexType name="BillingDocument">
  <xs:sequence>
    <xs:element minOccurs="0" name="Data" nillable="true" type="xsd:base64Binary" />
    <xs:element minOccurs="0" name="Id" type="xsd:long" />
    <xs:element minOccurs="0" name="Type" type="tns:DataType" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Data*|The billing document.|*base64Binary*|
|*Id*|The identifier of the billing document.|*long*|
|*Type*|The format of the billing document.|[DataType](../billing-api/datatype-value-set.md)|

## Remarks
The *BillingDocument* data object contains the actual billing document, whereas the [BillingDocumentInfo](../billing-api/billingdocumentinfo-data-object.md) contains information about the billing document.

## Requirements
[!INCLUDE[reqbilling](../billing-api/includes/reqbilling.md)]
## See Also
[GetBillingDocuments](../billing-api/getbillingdocuments-service-operation.md)

