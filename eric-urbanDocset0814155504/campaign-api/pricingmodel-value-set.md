---
title: "PricingModel Value Set"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12f40e0d-b79a-4e9a-a0b8-fd8776a3a157
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# PricingModel Value Set
Defines the pricing model for an ad group.

## Syntax

```xml
<xs:simpleType name="PricingModel">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Cpc" />
    <xs:enumeration value="Cpm" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Cpc|The pricing model is cost-per-click (CPC).|
|Cpm|The pricing model is cost per thousand-impressions (CPM).<br /><br />[!INCLUDE[pilot_cpm](../campaign-api/includes/pilot-cpm.md)]|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdGroup](../campaign-api/adgroup-data-object.md)

