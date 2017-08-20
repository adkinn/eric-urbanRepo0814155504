---
title: "AdGroupCriterionType Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b2c29bba-00e4-428f-8f1c-6ea9d9dd6e6d
caps.latest.revision: 15
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdGroupCriterionType Value Set
Defines the possible types of ad group criterions.

## Syntax

```xml
<xs:simpleType name="AdGroupCriterionType">
  <xs:list>
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:enumeration value="Age" />
        <xs:enumeration value="DayTime" />
        <xs:enumeration value="Device" />
        <xs:enumeration value="Gender" />
        <xs:enumeration value="Location" />
        <xs:enumeration value="LocationIntent" />
        <xs:enumeration value="Radius" />
        <xs:enumeration value="Targets" />
        <xs:enumeration value="ProductPartition" />
        <xs:enumeration value="Webpage" />
        <xs:enumeration value="Audience" />
        <xs:enumeration value="CustomAudience" />
        <xs:enumeration value="InMarketAudience" />
        <xs:enumeration value="RemarketingList" />
      </xs:restriction>
    </xs:simpleType>
  </xs:list>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|*Age*|The ad group criterion is an age criterion.<br/><br/>The *Criterion* element of a [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) can be an instance of [AgeCriterion](../campaign-api/agecriterion-data-object.md), but age criterion are not supported with [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md).<br/><br/>The *CriterionBid* element of a [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) must be an instance of [BidMultiplier](../campaign-api/bidmultiplier-data-object.md) when paired with this criterion type.|
|*Audience*|The ad group criterion is an audience criterion.<br/><br/>The *Criterion* element of either an [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) or [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md) can be an instance of [AudienceCriterion](../campaign-api/audiencecriterion-data-object.md). In other words you can include some audiences, and exclude other audiences.<br/><br/>The *CriterionBid* element of a [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) must be an instance of [BidMultiplier](../campaign-api/bidmultiplier-data-object.md) when paired with this criterion type.<br/><br/>To add, delete, or update audience criterions i.e., custom audiences, in-market audiences, and remarketing lists, you must specify the *Audience* value. To retrieve these audience criterions via [GetAdGroupCriterionsByIds](../campaign-api/getadgroupcriterionsbyids-service-operation.md) you must request the specific type i.e., *Custom*, *InMarket*, and *RemarketingList*.|
|*CustomAudience*|The ad group criterion is a custom audience association.<br/><br/>This criterion type value is only used by the [GetAdGroupCriterionsByIds](../campaign-api/getadgroupcriterionsbyids-service-operation.md) operation to request the custom audience associations represented by the [AudienceCriterion](../campaign-api/audiencecriterion-data-object.md) objects. To manage the custom audience, see [CustomAudience](../campaign-api/customaudience-data-object.md). |
|*DayTime*|The ad group criterion is a day and time criterion.<br/><br/>The *Criterion* element of a [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) can be an instance of [DayTimeCriterion](../campaign-api/daytimecriterion-data-object.md), but day and time criterion are not supported with [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md).<br/><br/>The *CriterionBid* element of a [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) must be an instance of [BidMultiplier](../campaign-api/bidmultiplier-data-object.md) when paired with this criterion type.|
|*Device*|The ad group criterion is a device criterion.<br/><br/>The *Criterion* element of a [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) can be an instance of [DeviceCriterion](../campaign-api/devicecriterion-data-object.md), but device criterion are not supported with [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md).<br/><br/>The *CriterionBid* element of a [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) must be an instance of [BidMultiplier](../campaign-api/bidmultiplier-data-object.md) when paired with this criterion type.|
|*Gender*|The ad group criterion is a gender criterion.<br/><br/>The *Criterion* element of a [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) can be an instance of [GenderCriterion](../campaign-api/gendercriterion-data-object.md), but gender criterion are not supported with [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md).<br/><br/>The *CriterionBid* element of a [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) must be an instance of [BidMultiplier](../campaign-api/bidmultiplier-data-object.md) when paired with this criterion type.|
|*InMarketAudience*|The ad group criterion is an in-market audience association.<br/><br/>This criterion type value is only used by the [GetAdGroupCriterionsByIds](../campaign-api/getadgroupcriterionsbyids-service-operation.md) operation to request the in-market audience associations represented by the [AudienceCriterion](../campaign-api/audiencecriterion-data-object.md) objects. To manage the in-market audience, see [InMarketAudience](../campaign-api/inmarketaudience-data-object.md). |
|*Location*|The ad group criterion is a location criterion.<br/><br/>The *Criterion* element of either an [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) or [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md) can be an instance of [LocationCriterion](../campaign-api/locationcriterion-data-object.md). In other words you can include some locations, and exclude other locations.<br/><br/>The *CriterionBid* element of a [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) must be an instance of [BidMultiplier](../campaign-api/bidmultiplier-data-object.md) when paired with this criterion type.|
|*LocationIntent*|The ad group criterion is a location intent criterion.<br/><br/>The *Criterion* element of a [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) can be an instance of [LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md), but location intent criterion are not supported with [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md).<br/><br/>The *CriterionBid* element of a [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) must be nil or empty when paired with this criterion type.|
|*ProductPartition*|The ad group criterion is a product partition criterion.<br/><br/>The *Criterion* element of either an [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) or [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md) can be an instance of [ProductPartition](../campaign-api/productpartition-data-object.md). In other words you can include some product partitions, and exclude other product partitions.<br/><br/>This criterion type is only used with Bing Shopping campaigns.<br/><br/>The *CriterionBid* element of a [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) must be an instance of [FixedBid](../campaign-api/fixedbid-data-object.md) when paired with this criterion type.|
|*Radius*|The ad group criterion is a radius criterion.<br/><br/>The *Criterion* element of a [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) can be an instance of [RadiusCriterion](../campaign-api/radiuscriterion-data-object.md), but radius criterion are not supported with [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md).<br/><br/>The *CriterionBid* element of a [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) must be an instance of [BidMultiplier](../campaign-api/bidmultiplier-data-object.md) when paired with this criterion type.|
|*RemarketingList*|The ad group criterion is a remarketing list association.<br/><br/>This criterion type value is only used by the [GetAdGroupCriterionsByIds](../campaign-api/getadgroupcriterionsbyids-service-operation.md) operation to request the remarketing list associations represented by the [AudienceCriterion](../campaign-api/audiencecriterion-data-object.md) objects. To manage the remarketing list, see [RemarketingList](../campaign-api/remarketinglist-data-object.md).|
|*Targets*|Represents one or more [AgeCriterion](../campaign-api/agecriterion-data-object.md), [DayTimeCriterion](../campaign-api/daytimecriterion-data-object.md), [DeviceCriterion](../campaign-api/devicecriterion-data-object.md), [GenderCriterion](../campaign-api/gendercriterion-data-object.md), [LocationCriterion](../campaign-api/locationcriterion-data-object.md), [LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md), and [RadiusCriterion](../campaign-api/radiuscriterion-data-object.md) objects that can be managed together to show ads based on your target criteria.<br/><br/>To add, delete, or update target criterions i.e., age, day and time, device, gender, location, location intent, and radius criterions, you must specify the *Targets* value. To retrieve these target criterions via [GetAdGroupCriterionsByIds](../campaign-api/getadgroupcriterionsbyids-service-operation.md) you must request the specific type i.e., *Age*, *DayTime*, *Device*, *Gender*, *Location*, *LocationIntent*, and *Radius*.|
|*Webpage*|The ad group criterion is a webpage criterion.<br/><br/>The *Criterion* element of either an [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) or [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md) can be an instance of [Webpage](../campaign-api/webpage-data-object.md), but webpage criterion are not supported with [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md). In other words you can include some webpages, and exclude other webpages.<br/><br/>This criterion type is only used with Dynamic Search Ads campaigns.<br/><br/>The *CriterionBid* element of a [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) must be an instance of [FixedBid](../campaign-api/fixedbid-data-object.md) when paired with this criterion type.|

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
[ProductPartition](../campaign-api/productpartition-data-object.md)  
[RadiusCriterion](../campaign-api/radiuscriterion-data-object.md)  
[Webpage](../campaign-api/webpage-data-object.md)  
