---
title: "BudgetPoint Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: acc6ba96-72db-4727-9c22-0c6099dd5590
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BudgetPoint Data Object
Defines an object that contains a budget amount and an estimate of weekly impressions, clicks, and cost for this budget amount.

> [!NOTE]
> The budget point is an estimate based on the last 15 days of performance data, and not a prediction or guarantee of future performance.

## Syntax

```xml
\<xs:complexType name="BudgetPoint">
  \<xs:sequence>
    \<xs:element name="BudgetAmount" type="xs:double" minOccurs="0"/>
    \<xs:element name="BudgetPointType" type="tns:BudgetPointType" minOccurs="0"/>
    \<xs:element name="EstimatedWeeklyClicks" type="xs:double" minOccurs="0"/>
    \<xs:element name="EstimatedWeeklyCost" type="xs:double" minOccurs="0"/>
    \<xs:element name="EstimatedWeeklyImpressions" type="xs:double" minOccurs="0"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*BudgetAmount*|A potential new budget.<br /><br />**Note:** This budget amount is your current campaign budget if the *BudgetPointType* value is *Current*.|*double*|
|*BudgetPointType*|The type of budget relative to a list of budget points. For example, if the budget point type is *Current* then this object's *BudgetAmount* element would be equal to the corresponding campaign's daily budget.|[BudgetPointType](../adinsight-api/budgetpointtype-value-set.md)|
|*EstimatedWeeklyClicks*|The estimated weekly  clicks for the given budget amount.|*double*|
|*EstimatedWeeklyCost*|The estimated weekly cost for the given budget amount.|*double*|
|*EstimatedWeeklyImpressions*|The estimated weekly impressions for the given budget amount.|*double*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetBudgetOpportunities](../adinsight-api/getbudgetopportunities-service-operation.md)

