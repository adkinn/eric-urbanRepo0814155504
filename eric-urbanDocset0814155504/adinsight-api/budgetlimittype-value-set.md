---
title: "BudgetLimitType Value Set"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80f6136f-038f-428d-8bd8-c21d0ff77371
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BudgetLimitType Value Set
Defines the possible types of campaign budgets.

## Syntax

```xml
\<xs:simpleType name="BudgetLimitType">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="DailyBudgetStandard"/>
    \<xs:enumeration value="DailyBudgetAccelerated"/>
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|DailyBudgetAccelerated|A daily budget that is spent until it is depleted. Depending on the activity, the complete budget could be spent within a couple of minutes, hours, or not at all.<br /><br />The daily spend will not exceed the daily budget limit and the accumulated daily spend will not exceed the calculated monthly budget limit.|
|DailyBudgetStandard|A daily budget that is spread throughout the day.<br /><br />The daily spend can exceed the daily budget limit by up to 20%; however, the accumulated daily spend will not exceed the calculated monthly budget limit.|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[BudgetOpportunity](../adinsight-api/budgetopportunity-data-object.md)  

