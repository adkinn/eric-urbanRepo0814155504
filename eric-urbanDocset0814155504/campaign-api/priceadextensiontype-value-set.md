---
title: "PriceAdExtensionType Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc77e723-9071-4532-8a3b-b3bdd398d2c4
caps.latest.revision: 2
author: "eric-urban"
ms.author: "eur"
---
# PriceAdExtensionType Value Set
Defines the possible types of price ad extensions.

## Syntax

```xml
<xs:simpleType name="PriceAdExtensionType">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Unknown" />
    <xs:enumeration value="Brands" />
    <xs:enumeration value="Events" />
    <xs:enumeration value="Locations" />
    <xs:enumeration value="Neighborhoods" />
    <xs:enumeration value="ProductCategories" />
    <xs:enumeration value="ProductTiers" />
    <xs:enumeration value="ServiceCategories" />
    <xs:enumeration value="Services" />
    <xs:enumeration value="ServiceTiers" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Brands|The header and description of the [PriceAdExtension](../campaign-api/priceadextension-data-object.md) describe brands.|
|Events|The header and description of the [PriceAdExtension](../campaign-api/priceadextension-data-object.md) describe events.|
|Locations|The header and description of the [PriceAdExtension](../campaign-api/priceadextension-data-object.md) describe locations.|
|Neighborhoods|The header and description of the [PriceAdExtension](../campaign-api/priceadextension-data-object.md) describe neighborhoods.|
|ProductCategories|The header and description of the [PriceAdExtension](../campaign-api/priceadextension-data-object.md) describe product categories.|
|ProductTiers|The header and description of the [PriceAdExtension](../campaign-api/priceadextension-data-object.md) describe product tiers.|
|ServiceCategories|The header and description of the [PriceAdExtension](../campaign-api/priceadextension-data-object.md) describe service categories.|
|Services|The header and description of the [PriceAdExtension](../campaign-api/priceadextension-data-object.md) describe services.|
|ServiceTiers|The header and description of the [PriceAdExtension](../campaign-api/priceadextension-data-object.md) describe service tiers.|
|Unknown|Reserved for forward compatibility.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[PriceAdExtension](../campaign-api/priceadextension-data-object.md)  

