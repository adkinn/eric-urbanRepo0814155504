---
title: "AdGroupCriterionStatus Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e1c764f0-349b-4fb0-9b7b-6ce371f56e0b
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdGroupCriterionStatus Value Set
Defines the possible ad group criterion status values.

## Syntax

```xml
<xs:simpleType name="AdGroupCriterionStatus">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Active" />
    <xs:enumeration value="Paused" />
    <xs:enumeration value="Deleted" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Active|The criterion is active.|
|Deleted|The criterion was deleted. Note that the *Get* operations will not return deleted objects.|
|Paused|The criterion is paused.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md)

