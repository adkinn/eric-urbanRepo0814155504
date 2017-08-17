---
title: "AdGroupAdditionalField Value Set"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 574b74f1-d458-40a0-b974-aeeb53b57169
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdGroupAdditionalField Value Set
Defines a list of optional [AdGroup](../campaign-api/adgroup-data-object.md) properties that you can request when calling [GetAdGroupsByCampaignId](../campaign-api/getadgroupsbycampaignid-service-operation.md) and [GetAdGroupsByIds](../campaign-api/getadgroupsbyids-service-operation.md). This set of flags enables you to get the latest features using the current version of Bing Ads Campaign Management API, and in the next version the corresponding properties will be included in the [AdGroup](../campaign-api/adgroup-data-object.md) object by default.

## Syntax

```xml
\<xs:simpleType name="AdGroupAdditionalField">
  \<xs:list>
    \<xs:simpleType>
      \<xs:restriction base="xs:string">
        \<xs:enumeration value="InheritedBidStrategyType" />
      \</xs:restriction>
    \</xs:simpleType>
  \</xs:list>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|InheritedBidStrategyType|Includes the *InheritedBidStrategyType* element that can be nested within the *BiddingScheme* element of an [AdGroup](../campaign-api/adgroup-data-object.md) object. The *InheritedBidStrategyType* will only be returned if the *BiddingScheme* element is an [InheritFromParentBiddingScheme](../campaign-api/inheritfromparentbiddingscheme-data-object.md) object.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[GetAdGroupsByCampaignId](../campaign-api/getadgroupsbycampaignid-service-operation.md)  
[GetAdGroupsByIds](../campaign-api/getadgroupsbyids-service-operation.md)  
[AdGroup](../campaign-api/adgroup-data-object.md)  
[InheritFromParentBiddingScheme](../campaign-api/inheritfromparentbiddingscheme-data-object.md)