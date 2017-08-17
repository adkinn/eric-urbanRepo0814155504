---
title: "CampaignCriterionType Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: da1ee387-d062-4030-86e6-4ccc635eac0c
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CampaignCriterionType Value Set
Defines the possible types of campaign criterions.

## Syntax

```xml
\<xs:simpleType name="CampaignCriterionType">
  \<xs:list>
    \<xs:simpleType>
      \<xs:restriction base="xs:string">
        \<xs:enumeration value="Age" />
        \<xs:enumeration value="Audience" />
        \<xs:enumeration value="DayTime" />
        \<xs:enumeration value="Device" />
        \<xs:enumeration value="Gender" />
        \<xs:enumeration value="Location" />
        \<xs:enumeration value="LocationIntent" />
        \<xs:enumeration value="ProductScope" />
        \<xs:enumeration value="Radius" />
        \<xs:enumeration value="Targets" />
        \<xs:enumeration value="Webpage" />
      \</xs:restriction>
    \</xs:simpleType>
  \</xs:list>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|*Age*|The campaign criterion is an age criterion.<br/><br/>The *Criterion* element of a [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) can be an instance of [AgeCriterion](../campaign-api/agecriterion-data-object.md), but age criterion are not supported with [NegativeCampaignCriterion](../campaign-api/negativecampaigncriterion-data-object.md).<br/><br/>The *CriterionBid* element of a [BiddableCampaignCriterion](../campaign-api/biddablecampaigncriterion-data-object.md) must be an instance of [BidMultiplier](../campaign-api/bidmultiplier-data-object.md) when paired with this criterion type.|
|*Audience*|Reserved for future use. You cannot set audience criterion for campaigns.|
|*DayTime*|The campaign criterion is a day and time criterion.<br/><br/>The *Criterion* element of a [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) can be an instance of [DayTimeCriterion](../campaign-api/daytimecriterion-data-object.md), but day and time criterion are not supported with [NegativeCampaignCriterion](../campaign-api/negativecampaigncriterion-data-object.md).<br/><br/>The *CriterionBid* element of a [BiddableCampaignCriterion](../campaign-api/biddablecampaigncriterion-data-object.md) must be an instance of [BidMultiplier](../campaign-api/bidmultiplier-data-object.md) when paired with this criterion type.|
|*Device*|The campaign criterion is a device criterion.<br/><br/>The *Criterion* element of a [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) can be an instance of [DeviceCriterion](../campaign-api/devicecriterion-data-object.md), but device criterion are not supported with [NegativeCampaignCriterion](../campaign-api/negativecampaigncriterion-data-object.md).<br/><br/>The *CriterionBid* element of a [BiddableCampaignCriterion](../campaign-api/biddablecampaigncriterion-data-object.md) must be an instance of [BidMultiplier](../campaign-api/bidmultiplier-data-object.md) when paired with this criterion type.|
|*Gender*|The campaign criterion is a gender criterion.<br/><br/>The *Criterion* element of a [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) can be an instance of [GenderCriterion](../campaign-api/gendercriterion-data-object.md), but gender criterion are not supported with [NegativeCampaignCriterion](../campaign-api/negativecampaigncriterion-data-object.md).<br/><br/>The *CriterionBid* element of a [BiddableCampaignCriterion](../campaign-api/biddablecampaigncriterion-data-object.md) must be an instance of [BidMultiplier](../campaign-api/bidmultiplier-data-object.md) when paired with this criterion type.|
|*Location*|The campaign criterion is a location criterion.<br/><br/>The *Criterion* element of either a [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) or [NegativeCampaignCriterion](../campaign-api/negativecampaigncriterion-data-object.md) can be an instance of [LocationCriterion](../campaign-api/locationcriterion-data-object.md). In other words you can include some locations, and exclude other locations.<br/><br/>The *CriterionBid* element of a [BiddableCampaignCriterion](../campaign-api/biddablecampaigncriterion-data-object.md) must be an instance of [BidMultiplier](../campaign-api/bidmultiplier-data-object.md) when paired with this criterion type.|
|*LocationIntent*|The campaign criterion is a location intent criterion.<br/><br/>The *Criterion* element of a [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) can be an instance of [LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md), but location intent criterion are not supported with [NegativeCampaignCriterion](../campaign-api/negativecampaigncriterion-data-object.md).<br/><br/>The *CriterionBid* element of a [BiddableCampaignCriterion](../campaign-api/biddablecampaigncriterion-data-object.md) must be nil or empty when paired with this criterion type.|
|*ProductScope*|The campaign criterion is a product scope criterion.<br/><br/>The *Criterion* element of a [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) can be an instance of [ProductScope](../campaign-api/productscope-data-object.md), but product scope criterion are not supported with [NegativeCampaignCriterion](../campaign-api/negativecampaigncriterion-data-object.md).<br/><br/>This criterion type is only used with Bing Shopping campaigns.<br/><br/>The *CriterionBid* element of a [BiddableCampaignCriterion](../campaign-api/biddablecampaigncriterion-data-object.md) must be an instance of [FixedBid](../campaign-api/fixedbid-data-object.md) when paired with this criterion type.|
|*Radius*|The campaign criterion is a radius criterion.<br/><br/>The *Criterion* element of a [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) can be an instance of [RadiusCriterion](../campaign-api/radiuscriterion-data-object.md), but radius criterion are not supported with [NegativeCampaignCriterion](../campaign-api/negativecampaigncriterion-data-object.md).<br/><br/>The *CriterionBid* element of a [BiddableCampaignCriterion](../campaign-api/biddablecampaigncriterion-data-object.md) must be an instance of [BidMultiplier](../campaign-api/bidmultiplier-data-object.md) when paired with this criterion type.|
|*Targets*|Represents one or more [AgeCriterion](../campaign-api/agecriterion-data-object.md), [DayTimeCriterion](../campaign-api/daytimecriterion-data-object.md), [DeviceCriterion](../campaign-api/devicecriterion-data-object.md), [GenderCriterion](../campaign-api/gendercriterion-data-object.md), [LocationCriterion](../campaign-api/locationcriterion-data-object.md), [LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md), and [RadiusCriterion](../campaign-api/radiuscriterion-data-object.md) objects that can be managed together to show ads based on your target criteria.<br/><br/>To add, delete, or update target criterions i.e., age, day and time, device, gender, location, location intent, and radius criterions, you must specify the *Targets* value. To retrieve these target criterions via [GetCampaignCriterionsByIds](../campaign-api/getcampaigncriterionsbyids-service-operation.md) you must request the specific type i.e., *Age*, *DayTime*, *Device*, *Gender*, *Location*, *LocationIntent*, and *Radius*.|
|*Webpage*|The campaign criterion is a webpage criterion.<br/><br/>The *Criterion* element of a [NegativeCampaignCriterion](../campaign-api/negativecampaigncriterion-data-object.md) can be an instance of [Webpage](../campaign-api/webpage-data-object.md), but webpage criterion are not supported with [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md).<br/><br/>This criterion type is only used with Dynamic Search Ads campaigns.<br/><br/>The *CriterionBid* element of a [BiddableCampaignCriterion](../campaign-api/biddablecampaigncriterion-data-object.md) must be an instance of [FixedBid](../campaign-api/fixedbid-data-object.md) when paired with this criterion type.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AgeCriterion](../campaign-api/agecriterion-data-object.md)  
[AudienceCriterion](../campaign-api/audiencecriterion-data-object.md)  
[DayTimeCriterion](../campaign-api/daytimecriterion-data-object.md)  
[DeviceCriterion](../campaign-api/devicecriterion-data-object.md)  
[GenderCriterion](../campaign-api/gendercriterion-data-object.md)  
[LocationCriterion](../campaign-api/locationcriterion-data-object.md)  
[LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md)  
[ProductScope](../campaign-api/productscope-data-object.md)  
[RadiusCriterion](../campaign-api/radiuscriterion-data-object.md)  
[Webpage](../campaign-api/webpage-data-object.md)  
