---
title: "Budget Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 210a32d9-be12-483b-82de-6709e0ef1b1b
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Budget Data Object
Represents a budget that can be shared by any campaigns in an account.

You can set a single daily budget that can be used by any campaign within the same account. This will enable you to efficiently distribute a single daily budget across all campaigns or across a defined group of campaigns within your Bing Ads account. 

Say you have a budget of $20 to be used uniformly between two campaigns every day. On a given day Campaign A spends only $8 (of its $10 budget) because it got a smaller amount of impressions and clicks than usual. Using a Shared Budget, if Campaign B is performing well then Bing Ads will automatically take the remaining $2 and allocate it to Campaign B. This will increase the chances that the remaining budget will be used to send you more traffic. 

## Syntax

```xml
<xs:complexType name="Budget">
  <xs:sequence>
    <xs:element name="Amount" type="xs:decimal" nillable="true" minOccurs="0"/>
    <xs:element name="AssociationCount" type="xs:int" nillable="true" minOccurs="0"/>
    <xs:element name="BudgetType" type="tns:BudgetLimitType" nillable="true" minOccurs="0"/>
    <xs:element name="Id" type="xs:long" nillable="true" minOccurs="0"/>
    <xs:element name="Name" type="xs:string" nillable="true" minOccurs="0"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements 

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Amount*|The amount to spend daily across all campaigns that share the budget.<br/><br/>**Add:** Required<br/>**Update:** Optional|*decimal*|
|*AssociationCount*|The number of [Campaign](../campaign-api/campaign-data-object.md) objects that currently share this budget.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*int*|
|*BudgetType*|The budget type determines the pace at which the budget is spent throughout the day.<br /><br />Possible values are *DailyBudgetAccelerated* and *DailyBudgetStandard*.<br/><br/>**Add:** Required<br/>**Update:** Optional|[BudgetLimitType](../campaign-api/budgetlimittype-value-set.md)|
|*Id*|The unique [!INCLUDE[brand](../campaign-api/includes/brand.md)] identifier of the budget.<br/><br/>**Add:** Read-only<br/>**Update:** Required|*long*|
|*Name*|The name of the budget. The name must be unique among all budgets within the account. The name can contain a maximum of 255 characters.<br /><br />The service performs a case-insensitive comparison when it compares the name to existing budget names.<br/><br/>**Add:** Required<br/>**Update:** Optional|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddBudgets](../campaign-api/addbudgets-service-operation.md)  
[DeleteBudgets](../campaign-api/deletebudgets-service-operation.md)  
[GetBudgetsByIds](../campaign-api/getbudgetsbyids-service-operation.md)  
[GetCampaignIdsByBudgetIds](../campaign-api/getcampaignidsbybudgetids-service-operation.md)  
[UpdateBudgets](../campaign-api/updatebudgets-service-operation.md)  
