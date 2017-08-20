---
title: "DistanceUnit Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b159463b-87d1-40a4-b902-f03bde3ca00f
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DistanceUnit Value Set
Defines the possible distance units of a geographical location.

## Syntax

```xml
<xs:simpleType name="DistanceUnit">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Kilometers" />
    <xs:enumeration value="Miles" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Kilometers|The distance of the specified geographical location is specified in kilometers.|
|Miles|The distance of the specified geographical location is specified in miles.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[RadiusCriterion](../campaign-api/radiuscriterion-data-object.md)  
[LocationCriterion](../campaign-api/locationcriterion-data-object.md)  

