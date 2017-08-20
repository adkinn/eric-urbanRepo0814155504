---
title: "BMCStore Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9ef4e4b3-330f-48c7-9a60-7bf1027d04b5
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BMCStore Data Object
Defines a [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)] store.

Elements of this object are defined in the [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)] store, and read-only in [!INCLUDE[brand](../campaign-api/includes/brand.md)].  Values of elements do not restrict [!INCLUDE[brand](../campaign-api/includes/brand.md)] features. For example, a Bing Shopping campaign and product ad may be added whether the *IsActive* element is set to true or false.

## Syntax

```xml
<xs:complexType name="BMCStore">
  <xs:sequence>
    <xs:element minOccurs="0" name="HasCatalog" type="xs:boolean" />
    <xs:element minOccurs="0" name="Id" type="xs:long" />
    <xs:element minOccurs="0" name="IsActive" type="xs:boolean" />
    <xs:element minOccurs="0" name="IsProductAdsEnabled" type="xs:boolean" />
    <xs:element minOccurs="0" name="Name" nillable="true" type="xs:string" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*HasCatalog*|Value will be true if the store has a catalog of items, and otherwise the value is false.|*boolean*|
|*Id*|The unique identifier for the  [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)] store.|*long*|
|*IsActive*|Value will be true if the store is active, and otherwise the value is false.|*boolean*|
|*IsProductAdsEnabled*|Value will be true if the store is enabled for product ads in [!INCLUDE[brand](../campaign-api/includes/brand.md)], and otherwise the value is false.|*boolean*|
|*Name*|Defines the name of the store as defined in the [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)].|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[GetBMCStoresByCustomerId](../campaign-api/getbmcstoresbycustomerid-service-operation.md)

