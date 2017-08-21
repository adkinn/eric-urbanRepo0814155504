---
title: "ApplicationType Value Set"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 66b4196e-e439-45bf-a1c4-31ca477768bd
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ApplicationType Value Set
Defines the possible application types.

## Syntax

```xml
<xs:simpleType name="ApplicationType">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Advertiser" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Advertiser|An advertiser application.|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
