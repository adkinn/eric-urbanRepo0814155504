---
title: "GenderCriterion Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57db6856-c9c2-4927-9b9b-4f19068762ee
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
---
# GenderCriterion Data Object
Defines a criterion that can be used to show ads to users of a specific gender.

The *GenderCriterion* criterion can be included within [AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md) and [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) objects. If ad group level gender criterions are specified, the campaign level gender criterions are ignored for that ad group. In other words the ad group gender criterions override the campaign gender criterions, and are not applied as a union.   

[!INCLUDE[guide_target_to_criterions](../campaign-api/includes/guide-target-to-criterions.md)]

## Syntax

```xml
<xs:complexType name="GenderCriterion">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:Criterion">
      <xs:sequence>
        <xs:element name="GenderType" type="tns:GenderType" minOccurs="0" nillable="true"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *GenderCriterion* object derives from the [Criterion](../campaign-api/criterion-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*GenderType*|The gender of the people you want to see your ads.<br/><br/>**Add:** Required<br/>**Update:** Not allowed. If you specify this element it must match the existing setting. |[GenderType](../campaign-api/gendertype-value-set.md)|

## <a name="InheritedElements"></a>Inherited Elements
The *GenderCriterion* object derives from the [Criterion](../campaign-api/criterion-data-object.md) object, and inherits the following element. 

> [!NOTE]
> The descriptions below are specific to gender criterions, and might not apply to other objects that inherit the same elements from the [Criterion](../campaign-api/criterion-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of the criterion. This value is *Gender* when you retrieve a gender criterion. For more information about criterion types, see the [Criterion Data Object Remarks](../campaign-api/criterion-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[Criterion](../campaign-api/criterion-data-object.md)  
