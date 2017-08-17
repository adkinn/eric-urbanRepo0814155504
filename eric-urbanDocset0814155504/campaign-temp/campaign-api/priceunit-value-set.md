---
title: "PriceUnit Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: be3487f0-8ddf-4251-a80f-55c66a2fb6c6
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
---
# PriceUnit Value Set
Defines price units for price ad extensions.

## Syntax

```xml
\<xs:simpleType name="PriceUnit">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Unknown"/>
    \<xs:enumeration value="PerDay"/>
    \<xs:enumeration value="PerHour"/>
    \<xs:enumeration value="PerMonth"/>
    \<xs:enumeration value="PerWeek"/>
    \<xs:enumeration value="PerYear"/>
    \<xs:enumeration value="PerNight"/>
    \<xs:enumeration value="None"/>
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|None|The price of the [PriceAdExtension](../campaign-api/priceadextension-data-object.md) will not be appended with price unit text.|
|PerDay|The *Per Day* price unit text will be appended to the price of the [PriceAdExtension](../campaign-api/priceadextension-data-object.md), for example *$9.99 Per Day*.|
|PerHour|The *Per Hour* price unit text will be appended to the price of the [PriceAdExtension](../campaign-api/priceadextension-data-object.md), for example *$9.99 Per Hour*.|
|PerMonth|The *Per Month* price unit text will be appended to the price of the [PriceAdExtension](../campaign-api/priceadextension-data-object.md), for example *$9.99 Per Month*.|
|PerNight|The *Per Night* price unit text will be appended to the price of the [PriceAdExtension](../campaign-api/priceadextension-data-object.md), for example *$9.99 Per Night*.|
|PerrWeek|The *Per Week* price unit text will be appended to the price of the [PriceAdExtension](../campaign-api/priceadextension-data-object.md), for example *$9.99 Per rWeek*.|
|PerYear|The *Per Year* price unit text will be appended to the price of the [PriceAdExtension](../campaign-api/priceadextension-data-object.md), for example *$9.99 Per Year*.|
|Unknown|Reserved for forward compatibility.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[PriceAdExtension](../campaign-api/priceadextension-data-object.md)  

