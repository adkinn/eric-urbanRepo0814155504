---
title: "GenderType Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 16252b04-472b-4bee-9e21-8431f25e382c
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GenderType Value Set
Defines the genders that are available for gender criterion.

## Syntax

```xml
<xs:simpleType name="GenderType">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Male" />
    <xs:enumeration value="Female" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|
|---------|
|Female|
|Male|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[GenderCriterion](../campaign-api/gendercriterion-data-object.md)

