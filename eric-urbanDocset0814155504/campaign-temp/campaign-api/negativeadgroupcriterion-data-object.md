---
title: "NegativeAdGroupCriterion Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f7606549-b6ba-4f3f-b5ea-795ffcd365dc
caps.latest.revision: 13
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# NegativeAdGroupCriterion Data Object
Defines a criterion that you want to exclude from the specified ad group.

## Syntax

```xml
\<xs:complexType name="NegativeAdGroupCriterion">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:tns:AdGroupCriterion">
      \<xs:sequence />
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
The *NegativeAdGroupCriterion* object derives from the [AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

## <a name="InheritedElements"></a>Inherited Elements
The *NegativeAdGroupCriterion* object derives from the [AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md) object, and inherits the following elements. 

> [!NOTE]
> The descriptions below are specific to negative ad group criterion, and might not apply to other objects that inherit the same elements from the [AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdGroupId*|The identifier of the ad group to apply the criterion to.<br/><br/>**Add:** Required<br/>**Update:** Required|*long*|
|*Criterion*|The criterion to apply to the ad group. The criterion helps determine whether ads in the ad group are served.<br/><br/>For a list of available criterion types, see [AdGroupCriterionType](../campaign-api/adgroupcriteriontype-value-set.md).<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|[Criterion](../campaign-api/criterion-data-object.md)|
|*Id*|The unique Bing Ads identifier for the ad group criterion.<br/><br/>**Add:** Read-only<br/>**Update:** Required|*long*|
|*Status*|A status value that determines whether the criterion applies for the ad group.<br/><br/>Currently the only supported status for negative ad group criterions is *Active*.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[AdGroupCriterionStatus](../campaign-api/adgroupcriterionstatus-value-set.md)|
|*Type*|The type of the ad group criterion. This value is *NegativeAdGroupCriterion* when you retrieve a negative ad group criterion. For more information about ad group criterion types, see the [AdGroupCriterion Data Object Remarks](../campaign-api/adgroupcriterion-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|


## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddAdGroupCriterions](../campaign-api/addadgroupcriterions-service-operation.md)  
[GetAdGroupCriterionsByIds](../campaign-api/getadgroupcriterionsbyids-service-operation.md)  
[UpdateAdGroupCriterions](../campaign-api/updateadgroupcriterions-service-operation.md)  

