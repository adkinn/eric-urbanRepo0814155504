---
title: "NegativeCampaignCriterion Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 497aaa20-f8aa-427b-acb7-e4e7da724bd9
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# NegativeCampaignCriterion Data Object
Defines a criterion that you want to exclude from the specified campaign.

## Syntax

```xml
\<xs:complexType name="NegativeCampaignCriterion">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:tns:CampaignCriterion">
      \<xs:sequence />
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
The *NegativeCampaignCriterion* object derives from the [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

## <a name="InheritedElements"></a>Inherited Elements
The *NegativeCampaignCriterion* object derives from the [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) object, and inherits the following elements. 

> [!NOTE]
> The descriptions below are specific to negative campaign criterion, and might not apply to other objects that inherit the same elements from the [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CampaignId*|The identifier of the campaign to apply the criterion to.<br/><br/>**Add:** Required<br/>**Update:** Required|*long*|
|*Criterion*|The criterion to apply to the campaign. The criterion helps determine whether ads in the campaign are served.<br/><br/>For a list of available criterion types, see [CampaignCriterionType](../campaign-api/campaigncriteriontype-value-set.md).<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|[Criterion](../campaign-api/criterion-data-object.md)|
|*Id*|The unique Bing Ads identifier for the campaign criterion.<br/><br/>**Add:** Read-only<br/>**Update:** Required|*long*|
|*Status*|A status value that determines whether the criterion applies for the campaign.<br/><br/>Currently the only supported status for negative campaign criterions is *Active*.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[CampaignCriterionStatus](../campaign-api/campaigncriterionstatus-value-set.md)|
|*Type*|The type of the campaign criterion. This value is *NegativeCampaignCriterion* when you retrieve a negative campaign criterion. For more information about campaign criterion types, see the [CampaignCriterion Data Object Remarks](../campaign-api/campaigncriterion-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddCampaignCriterions](../campaign-api/addcampaigncriterions-service-operation.md)  
[DeleteCampaignCriterions](../campaign-api/deletecampaigncriterions-service-operation.md)  
[GetCampaignCriterionsByIds](../campaign-api/getcampaigncriterionsbyids-service-operation.md)  
[UpdateCampaignCriterions](../campaign-api/updatecampaigncriterions-service-operation.md)  

