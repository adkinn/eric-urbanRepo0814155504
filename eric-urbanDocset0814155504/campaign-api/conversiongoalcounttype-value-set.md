---
title: "ConversionGoalCountType Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 097cc670-1404-460c-89e2-83197ad08442
caps.latest.revision: 2
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ConversionGoalCountType Value Set
Defines how your conversions are recorded within your chosen conversion window.

For example, you track two conversions: leads and sales. You pick *Unique* for leads and *All* for sales. When one ad click turns into two leads and two sales, it's counted as three conversions: one for the unique lead, and two for all the sales. 

## Syntax

```xml
<xs:simpleType name="ConversionGoalCountType">
  <xs:list>
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:enumeration value="All" />
        <xs:enumeration value="Unique" />
      </xs:restriction>
    </xs:simpleType>
  </xs:list>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|All|All conversions that happen after an ad click will be counted. This is a common choice for sales.|
|Unique|Only one conversion that happens after an ad click will be counted. This is a common choice for leads.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[ConversionGoal](../campaign-api/conversiongoal-data-object.md)

