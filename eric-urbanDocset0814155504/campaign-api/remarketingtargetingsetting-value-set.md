---
title: "RemarketingTargetingSetting Value Set"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 696225f5-af9c-487f-920f-e05c36cc6866
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# RemarketingTargetingSetting Value Set
The targeting setting that is applicable for all audiences e.g., custom audiences and remarketing lists that are associated with this ad group. Each audience can be associated with multiple ad groups, and each ad group's remarketing targeting setting is applied independently for delivery. 

## Syntax

```xml
\<xs:simpleType name="RemarketingTargetingSetting">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="BidOnly" />
    \<xs:enumeration value="TargetAndBid" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|BidOnly|Show ads to people searching for your ad, with the option to change the bid amount for people included in the audience. Ads in this ad group can show to everyone but the bid adjustment will apply to people included in the audience.<br/><br/>**Note:** Bing Ads won't apply any bid boosts until the associated audience has at least 1000 users.|
|TargetAndBid|Show ads only to people included in the audience, with the option to change the bid amount. Ads in this ad group will only show to people included in the audience.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdGroup](../campaign-api/adgroup-data-object.md)  
[GetAdGroupsByCampaignId](../campaign-api/getadgroupsbycampaignid-service-operation.md)  
[GetAdGroupsByIds](../campaign-api/getadgroupsbyids-service-operation.md)  