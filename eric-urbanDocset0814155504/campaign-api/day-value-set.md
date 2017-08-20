---
title: "Day Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e71b65e-7148-4413-941d-b6cdc602df66
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Day Value Set
Defines the day values that you can specify for day and time criterion.

## Syntax

```xml
<xs:simpleType name="Day">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Sunday" />
    <xs:enumeration value="Monday" />
    <xs:enumeration value="Tuesday" />
    <xs:enumeration value="Wednesday" />
    <xs:enumeration value="Thursday" />
    <xs:enumeration value="Friday" />
    <xs:enumeration value="Saturday" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|
|---------|
|Sunday|
|Monday|
|Tuesday|
|Wednesday|
|Thursday|
|Friday|
|Saturday|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[DayTimeCriterion](../campaign-api/daytimecriterion-data-object.md)

