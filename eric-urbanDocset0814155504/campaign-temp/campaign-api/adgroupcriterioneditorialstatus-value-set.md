---
title: "AdGroupCriterionEditorialStatus Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: be2cd5d2-8817-4ca1-bd14-9e1ac6ca6b9c
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdGroupCriterionEditorialStatus Value Set
Defines the editorial review status values of an ad group criterion.

## Syntax

```xml
\<xs:simpleType name="AdGroupCriterionEditorialStatus">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Active" />
    \<xs:enumeration value="Disapproved" />
    \<xs:enumeration value="Inactive" />
    \<xs:enumeration value="ActiveLimited" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Active|The criterion passed editorial review.|
|ActiveLimited|The criterion passed editorial review in one or more markets, and one or more elements of the criterion is undergoing editorial review in another market. For example the criterion passed editorial review for Canada and is still pending review in the United States.|
|Disapproved|The criterion failed editorial review.|
|Inactive|The criterion is undergoing editorial review.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md)

