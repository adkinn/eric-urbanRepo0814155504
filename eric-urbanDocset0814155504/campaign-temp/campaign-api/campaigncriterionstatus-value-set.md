---
title: "CampaignCriterionStatus Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e7affac9-813d-499a-aaac-d7e128741ea1
caps.latest.revision: 2
author: "eric-urban"
ms.author: "eur"
---
# CampaignCriterionStatus Value Set
Defines the possible campaign criterion status values.

## Syntax

```xml
\<xs:simpleType name="CampaignCriterionStatus">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Active" />
    \<xs:enumeration value="Paused" />
    \<xs:enumeration value="Deleted" />
  \</xs:restriction>
\</xs:simpleType>
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
[CampaignCriterion](../campaign-api/campaigncriterion-data-object.md)

