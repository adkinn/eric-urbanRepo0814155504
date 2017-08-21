---
title: "AgeCriterion Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 598d3b4a-af77-4129-960c-ff6e0333c25f
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
---
# AgeCriterion Data Object
Defines a criterion that can be used to show ads to users in a specific age range.

The *AgeCriterion* criterion can be included within [AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md) and [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) objects. If ad group level age criterions are specified, the campaign level age criterions are ignored for that ad group. In other words the ad group age criterions override the campaign age criterions, and are not applied as a union.   

[!INCLUDE[guide_target_to_criterions](../campaign-api/includes/guide-target-to-criterions.md)]

## Syntax

```xml
<xs:complexType name="AgeCriterion">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:Criterion">
      <xs:sequence>
        <xs:element name="AgeRange" type="tns:AgeRange"  minOccurs="0" nillable="true"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *AgeCriterion* object derives from the [Criterion](../campaign-api/criterion-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AgeRange*|The age range of the people you want to see your ads.<br/><br/>**Add:** Required<br/>**Update:** Not allowed. If you specify this element it must match the existing setting. |[AgeRange](../campaign-api/agerange-value-set.md)|

## <a name="InheritedElements"></a>Inherited Elements
The *AgeCriterion* object derives from the [Criterion](../campaign-api/criterion-data-object.md) object, and inherits the following element. 

> [!NOTE]
> The descriptions below are specific to age criterions, and might not apply to other objects that inherit the same elements from the [Criterion](../campaign-api/criterion-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of the criterion. This value is *Age* when you retrieve an age criterion. For more information about criterion types, see the [Criterion Data Object Remarks](../campaign-api/criterion-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[Criterion](../campaign-api/criterion-data-object.md)  
