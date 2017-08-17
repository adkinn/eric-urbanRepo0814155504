---
title: "ProductPartition Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 460a370f-dd94-4630-bccc-148b39b5a2e6
caps.latest.revision: 12
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ProductPartition Data Object
Defines an ad group level product partition with one condition that helps determine whether a product from the [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)] store gets served as a product ad.

The *ProductPartition* criterion can be included within [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) and [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md). Also note that campaign level [ProductScope](../campaign-api/productscope-data-object.md) can be added to [BiddableCampaignCriterion](../campaign-api/biddablecampaigncriterion-data-object.md). Duplicate or conflicting product conditions attempted within an ad group's product partition group will be rejected by the [ApplyProductPartitionActions](../campaign-api/applyproductpartitionactions-service-operation.md) operation; however, the operation will not validate whether duplicate or conflicting conditions already exist within the campaign level [ProductScope](../campaign-api/productscope-data-object.md).

[!INCLUDE[guide_bsc](../campaign-api/includes/guide-bsc.md)]

## Syntax

```xml
\<xs:complexType name="ProductPartition">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:Criterion">
      \<xs:sequence>
        \<xs:element name="Condition" nillable="true" type="tns:ProductCondition"/>
        \<xs:element name="ParentCriterionId" nillable="true" type="xs:long"/>
        \<xs:element name="PartitionType" type="tns:ProductPartitionType"/>
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
The *ProductPartition* object derives from the [Criterion](../campaign-api/criterion-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Condition*|A condition that helps determine whether a product from the [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)] store gets served as an ad.<br /><br />Multiple product conditions can be specified by creating a tree of *ProductPartition* objects using [ApplyProductPartitionActions](../campaign-api/applyproductpartitionactions-service-operation.md). For a catalog item to be served as an ad, it must meet all conditions. To get a list of all conditions for an ad group, call [GetAdGroupCriterionsByIds](../campaign-api/getadgroupcriterionsbyids-service-operation.md) with the *AdGroupCriterionIds* element set to null and the *CriterionType* element set to ProductPartition.<br/><br/>**Add:** Required<br/>**Update:** Update is not supported for this object|[ProductCondition](../campaign-api/productcondition-data-object.md)|
|*ParentCriterionId*|The identifier of the parent [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) or [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md).<br /><br />**Note:** This element must be set to null if the product partition represents the root node of a product partition tree.<br/><br/>**Add:** Required<br/>**Update:** Update is not supported for this object<br/>**Delete:** Required|*long*|
|*PartitionType*|The type of product partition, for example *Subdivision* or *Unit*.<br/><br/>**Add:** Required<br/>**Update:** Update is not supported for this object|[ProductPartitionType](../campaign-api/productpartitiontype-value-set.md)|

## <a name="InheritedElements"></a>Inherited Elements
The *ProductPartition* object derives from the [Criterion](../campaign-api/criterion-data-object.md) object, and inherits the following elements. 

> [!NOTE]
> The descriptions below are specific to product partitions, and might not apply to other objects that inherit the same elements from the [Criterion](../campaign-api/criterion-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of the criterion. This value is *ProductPartition* when you retrieve a product partition criterion. For more information about criterion types, see the [Criterion Data Object Remarks](../campaign-api/criterion-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[ApplyProductPartitionActions](../campaign-api/applyproductpartitionactions-service-operation.md)  
[GetAdGroupCriterionsByIds](../campaign-api/getadgroupcriterionsbyids-service-operation.md)  
[Criterion](../campaign-api/criterion-data-object.md)  
[BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md)  
[NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md)  

