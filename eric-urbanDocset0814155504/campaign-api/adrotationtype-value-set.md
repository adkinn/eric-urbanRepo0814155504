---
title: "AdRotationType Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6f60a759-c0d5-43c9-aff2-8fcf0bcc65ea
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdRotationType Value Set
Defines the possible ad rotation types that you can apply to an ad group. For ad groups with more than one ad, these options determine how the ads are rotated into the auction.

## Syntax

```xml
\<xs:simpleType name="AdRotationType">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="OptimizeForClicks" />
    \<xs:enumeration value="RotateAdsEvenly" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|OptimizeForClicks|Favor the best performing ads.<br /><br />This is the default.|
|RotateAdsEvenly|Rotate ads evenly into the auction.|

## Remarks
Because the OptimizeForClicks favors the best performing ads, the likelihood that new ads will be rotated into the auction in the near future is reduced. If you add seasonal ads or if you want to experiment with the ad copy of underperforming ads, you should select the RotateAdsEvenly option to get the ads in front of customers.

Note that rotating ads evenly into the auction does not mean that they will get an equal number of impressions.

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdRotation](../campaign-api/adrotation-data-object.md)

