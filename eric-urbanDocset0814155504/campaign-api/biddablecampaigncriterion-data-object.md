---
title: "BiddableCampaignCriterion Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 722b9cf1-8bae-4ce9-8170-66ba085c4c3e
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
---
# BiddableCampaignCriterion Data Object
Defines a biddable criterion that you want applied to the specified campaign.

## Syntax

```xml
<xs:complexType name="BiddableCampaignCriterion">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:CampaignCriterion">
      <xs:sequence>
        <xs:element minOccurs="0" name="CriterionBid" nillable="true" type="tns:CriterionBid" />
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *BiddableCampaignCriterion* object derives from the [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CriterionBid*|The bid to use in the auction.<br/><br/>**Add:** Requirements vary depending on the type of *Criterion* that is [inherited](#InheritedElements) from the [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) object. The bid is optional and will be set to the default of *0* if not included for [AgeCriterion](../campaign-api/agecriterion-data-object.md), [DayTimeCriterion](../campaign-api/daytimecriterion-data-object.md), [DeviceCriterion](../campaign-api/devicecriterion-data-object.md), [GenderCriterion](../campaign-api/gendercriterion-data-object.md), [LocationCriterion](../campaign-api/locationcriterion-data-object.md), and [RadiusCriterion](../campaign-api/radiuscriterion-data-object.md). The bid is not applicable for [LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md) and [ProductScope](../campaign-api/productscope-data-object.md) (The service will not return any error and the bid will be ignored even if you include it).<br/>**Update:** Requirements vary depending on the type of *Criterion* that is [inherited](#InheritedElements) from the [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) object. The bid is required for [AgeCriterion](../campaign-api/agecriterion-data-object.md), [DayTimeCriterion](../campaign-api/daytimecriterion-data-object.md), [DeviceCriterion](../campaign-api/devicecriterion-data-object.md), [GenderCriterion](../campaign-api/gendercriterion-data-object.md), [LocationCriterion](../campaign-api/locationcriterion-data-object.md), and [RadiusCriterion](../campaign-api/radiuscriterion-data-object.md). The bid is not applicable for [LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md) and [ProductScope](../campaign-api/productscope-data-object.md) (The service will not return any error and the bid will be ignored even if you include it).|[CriterionBid](../campaign-api/criterionbid-data-object.md)|

## <a name="InheritedElements"></a>Inherited Elements
The *BiddableCampaignCriterion* object derives from the [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) object, and inherits the following elements. 

> [!NOTE]
> The descriptions below are specific to biddable campaign criterion, and might not apply to other objects that inherit the same elements from the [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CampaignId*|The identifier of the campaign to apply the criterion to.<br/><br/>**Add:** Required<br/>**Update:** Required|*long*|
|*Criterion*|The criterion to apply to the campaign. The criterion helps determine whether ads in the campaign are served.<br/><br/>For a list of available criterion types, see [CampaignCriterionType](../campaign-api/campaigncriteriontype-value-set.md).<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|[Criterion](../campaign-api/criterion-data-object.md)|
|*Id*|The unique Bing Ads identifier for the campaign criterion.<br/><br/>**Add:** Read-only<br/>**Update:** Required|*long*|
|*Status*|A status value that determines whether the criterion applies for the campaign.<br/><br/>Currently the only supported status for biddable campaign criterions is *Active*.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[CampaignCriterionStatus](../campaign-api/campaigncriterionstatus-value-set.md)|
|*Type*|The type of the campaign criterion. This value is *BiddableCampaignCriterion* when you retrieve a biddable campaign criterion. For more information about campaign criterion types, see the [CampaignCriterion Data Object Remarks](../campaign-api/campaigncriterion-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|
 

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddCampaignCriterions](../campaign-api/addcampaigncriterions-service-operation.md)   
[GetCampaignCriterionsByIds](../campaign-api/getcampaigncriterionsbyids-service-operation.md)  
[UpdateCampaignCriterions](../campaign-api/updatecampaigncriterions-service-operation.md)  

