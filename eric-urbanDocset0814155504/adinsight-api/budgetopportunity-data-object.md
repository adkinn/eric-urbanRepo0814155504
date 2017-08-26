---
title: "BudgetOpportunity Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 71378754-9fe7-4baa-be66-7a2c2005ec62
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BudgetOpportunity Data Object
Defines an object that contains the suggested budget with estimated clicks and impressions opportunities. Additionally, the object contains a list of budget points with weekly impressions, clicks and cost estimates for the given budget amount.

> [!NOTE]
> The budget opportunity is an estimate based on the last 15 days of performance data, and not a prediction or guarantee of future performance.

## Syntax

```xml
<xs:complexType name="BudgetOpportunity">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:Opportunity">
      <xs:sequence>
        <xs:element minOccurs="0" name="BudgetPoints" nillable="true" type="tns:ArrayOfBudgetPoint"/>
        <xs:element minOccurs="0" name="BudgetType" type="tns:BudgetLimitType"/>
        <xs:element minOccurs="0" name="CampaignId" type="xs:long" />
        <xs:element minOccurs="0" name="CurrentBudget" type="xs:double" />
        <xs:element minOccurs="0" name="IncreaseInClicks" type="xs:double" />
        <xs:element minOccurs="0" name="IncreaseInImpressions" type="xs:long" />
        <xs:element minOccurs="0" name="PercentageIncreaseInClicks" type="xs:int" />
        <xs:element minOccurs="0" name="PercentageIncreaseInImpressions" type="xs:int" />
        <xs:element minOccurs="0" name="RecommendedBudget" type="xs:double" />
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *BudgetOpportunity* object inherits elements from the [Opportunity](../adinsight-api/opportunity-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*BudgetPoints*|The list of budget points with weekly impressions, clicks and cost estimates for the given budget amount.|[BudgetPoint](../adinsight-api/budgetpoint-data-object.md) array|
|*BudgetType*|The type of budget that the campaign uses.|[BudgetLimitType](../adinsight-api/budgetlimittype-value-set.md)|
|*CampaignId*|The identifier of the campaign to which the suggested budget applies.|*long*|
|*CurrentBudget*|The campaign's current budget.|*double*|
|*IncreaseInClicks*|The estimated clicks opportunities corresponding to the suggested budget.|*double*|
|*IncreaseInImpressions*|The estimated impressions opportunities corresponding to the suggested budget.|*long*|
|*PercentageIncreaseInClicks*|The estimated percentage increase in clicks corresponding to the suggested budget.|*int*|
|*PercentageIncreaseInImpressions*|The estimated percentage increase in impressions corresponding to the suggested budget.|*int*|
|*RecommendedBudget*|The suggested budget based on the last 15 days of performance history for the corresponding campaign.|*double*|

## <a name="InheritedElements"></a>Inherited Elements
The *BudgetOpportunity* object inherits the following element from the [Opportunity](../adinsight-api/opportunity-data-object.md) object. 

> [!NOTE]
> The description below is specific to budget opportunities, and might not apply to other objects that inherit the same element from the [Opportunity](../adinsight-api/opportunity-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*OpportunityKey*|An identifier that uniquely identifies the opportunity.|*string*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetBudgetOpportunities](../adinsight-api/getbudgetopportunities-service-operation.md)

