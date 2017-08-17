---
title: "AdGroupCriterionAction Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c691376-7aea-49fc-988a-6ba4ee8b3c93
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdGroupCriterionAction Data Object
Defines the action to apply to a [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) or [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md), specifically one that contains a [ProductPartition](../campaign-api/productpartition-data-object.md). You can send a group of [AdGroupCriterionAction](../campaign-api/adgroupcriterionaction-data-object.md) objects, also known as a product group, to the [ApplyProductPartitionActions](../campaign-api/applyproductpartitionactions-service-operation.md) service operation.

## Syntax

```xml
<xs:complexType name="AdGroupCriterionAction">
  <xs:sequence>
    <xs:element name="Action" type="tns:ItemAction"/>
    <xs:element name="AdGroupCriterion" nillable="true" type="tns:AdGroupCriterion"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Action*|The action to be applied for the *AdGroupCriterion*.|[ItemAction](../campaign-api/itemaction-value-set.md)|
|*AdGroupCriterion*|The [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) or [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md), either of which must contain a [ProductPartition](../campaign-api/productpartition-data-object.md) criterion.<br/><br/>For the Update action, only the *CriterionBid* and *DestinationUrl* elements of the *AdGroupCriterion* are mutable. To update the order or structure of the product group, you cannot use the update action. You must delete ad group criterions and then add new product partitions instead.|[AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md)|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[ApplyProductPartitionActions](../campaign-api/applyproductpartitionactions-service-operation.md)  
[ProductPartition](../campaign-api/productpartition-data-object.md)  
[AdGroupCriterionAction](../campaign-api/adgroupcriterionaction-data-object.md)  
[BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md)  
[NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md)  

