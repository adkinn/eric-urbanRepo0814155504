---
title: "PriceQualifier Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b77400c9-89f1-405c-b411-11f7fac20a98
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
---
# PriceQualifier Value Set
Defines price qualifiers for price ad extensions.

## Syntax

```xml
<xs:simpleType name="PriceQualifier">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Unknown" />
    <xs:enumeration value="From" />
    <xs:enumeration value="UpTo" />
    <xs:enumeration value="None" />
    <xs:enumeration value="Average" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Average|The price of the [PriceAdExtension](../campaign-api/priceadextension-data-object.md) is prefixed with price qualifier text *Average*, for example *Average $9.99*.|
|From|The price of the [PriceAdExtension](../campaign-api/priceadextension-data-object.md) is prefixed with price qualifier text *From*, for example *From $9.99*.|
|None|The price of the [PriceAdExtension](../campaign-api/priceadextension-data-object.md) is not prefixed with price qualifier text.|
|UpTo|The price of the [PriceAdExtension](../campaign-api/priceadextension-data-object.md) is prefixed with the price qualifier text *Up to*, for example *Up to $9.99*.|
|Unknown|Reserved for forward compatibility.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[PriceAdExtension](../campaign-api/priceadextension-data-object.md)  

