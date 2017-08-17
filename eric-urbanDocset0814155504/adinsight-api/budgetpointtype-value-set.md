---
title: "BudgetPointType Value Set"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 77f02cbe-fcb5-47de-a351-90402e055b88
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BudgetPointType Value Set
Defines the possible values of a campaign budget point.

## Syntax

```xml
\<xs:simpleType name="BudgetPointType">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Current">
    \<xs:enumeration value="Suggested">
    \<xs:enumeration value="Maximum">
    \<xs:enumeration value="Other">
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Current|The budget point includes the current budget.|
|Maximum|The budget point includes the proposed budget which is estimated to yield the maximum number of clicks.|
|Other|The budget point includes a proposed budget other than current, maximum, or suggested.|
|Suggested|The budget point includes the optimal suggested budget. The proposed budget is estimated to yield the optimal ratio of increased clicks to minimal budget increase.|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[BudgetPoint](../adinsight-api/budgetpoint-data-object.md)

