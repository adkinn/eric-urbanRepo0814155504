---
title: "ProductScope Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aae522a9-51be-40e2-80b2-044144636a6c
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ProductScope Data Object
Defines a campaign level product scope with list of conditions that help determine whether a product from the [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)] store gets served as a product ad.

The *ProductScope* criterion can only be included within [BiddableCampaignCriterion](../campaign-api/biddablecampaigncriterion-data-object.md). Also note that ad group level [ProductPartition](../campaign-api/productpartition-data-object.md) can be added to [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) and [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md). Duplicate or conflicting product conditions attempted within an ad group's [ProductPartition](../campaign-api/productpartition-data-object.md) group will be rejected by the [ApplyProductPartitionActions](../campaign-api/applyproductpartitionactions-service-operation.md) operation; however, the operation will not validate whether duplicate or conflicting conditions already exist within the campaign level product scope.

[!INCLUDE[guide_bsc](../campaign-api/includes/guide-bsc.md)]

## Syntax

```xml
<xs:complexType name="ProductScope">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:Criterion">
      <xs:sequence>
        <xs:element minOccurs="0" name="Conditions" nillable="true" type="tns:ArrayOfProductCondition"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *ProductScope* object derives from the [Criterion](../campaign-api/criterion-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Conditions*|A list of up to 7 product conditions that helps determine whether a product from the [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)] store gets served as an ad.<br /><br />**Note:** Conditions may be returned by [!INCLUDE[brand](../campaign-api/includes/brand.md)] services in a different order from the order that you submitted.<br /><br />**Add:** Required<br/>**Update:** Required|[ProductCondition](../campaign-api/productcondition-data-object.md) array|

## <a name="InheritedElements"></a>Inherited Elements
The *ProductScope* object derives from the [Criterion](../campaign-api/criterion-data-object.md) object, and inherits the following elements. 

> [!NOTE]
> The descriptions below are specific to product scopes, and might not apply to other objects that inherit the same elements from the [Criterion](../campaign-api/criterion-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of the criterion. This value is *ProductScope* when you retrieve a product scope criterion. For more information about criterion types, see the [Criterion Data Object Remarks](../campaign-api/criterion-data-object.md#remarks).<br /><br />**Add:** Read-only<br/>**Update:** Read-only|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddCampaignCriterions](../campaign-api/addcampaigncriterions-service-operation.md)  
[DeleteCampaignCriterions](../campaign-api/deletecampaigncriterions-service-operation.md)  
[GetCampaignCriterionsByIds](../campaign-api/getcampaigncriterionsbyids-service-operation.md)  
[UpdateCampaignCriterions](../campaign-api/updatecampaigncriterions-service-operation.md)  
[Criterion](../campaign-api/criterion-data-object.md)  
[CampaignCriterion](../campaign-api/campaigncriterion-data-object.md)  

