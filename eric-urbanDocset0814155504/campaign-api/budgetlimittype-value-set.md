---
title: "BudgetLimitType Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e2762121-a371-4a8e-9850-bdf302dcc28d
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BudgetLimitType Value Set
Defines the possible budget types that you can specify for a campaign.

## Syntax

```xml
\<xs:simpleType name="BudgetLimitType">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="DailyBudgetAccelerated" />
    \<xs:enumeration value="DailyBudgetStandard" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|DailyBudgetAccelerated|A daily budget that is spent until it is depleted. Depending on the activity, the complete budget could be spent within a couple of minutes, hours, or not at all.<br /><br />The daily spend will not exceed the daily budget limit and the accumulated daily spend will not exceed the calculated monthly budget limit.<br /><br />To specify an accelerated daily budget, set the *BudgetType* element of the [Campaign](../campaign-api/campaign-data-object.md) object to DailyBudgetAccelerated and set the *DailyBudget* element to the amount that you want to spend daily on the campaign.|
|DailyBudgetStandard|A daily budget that is spread throughout the day.<br /><br />The daily spend can exceed the daily budget limit by up to 20%; however, the accumulated daily spend will not exceed the calculated monthly budget limit.<br /><br />To specify a standard daily budget, set the *BudgetType* element of the [Campaign](../campaign-api/campaign-data-object.md) object to DailyBudgetStandard and set the *DailyBudget* element to the amount that you want to spend daily on the campaign.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[Campaign](../campaign-api/campaign-data-object.md)  

