---
title: "CampaignEstimate Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 855a6530-a800-4921-a577-8080e3ef6db0
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CampaignEstimate Data Object
Contains a nested list of suggested keywords for the campaign's ad groups with minimum and maximum traffic estimates. Traffic estimates include average CPC, average position, clicks, CTR, impressions, and total cost.

> [!NOTE]
> The estimates are not a prediction or guarantee of future performance.

## Syntax

```xml
<xs:complexType name="CampaignEstimate">
  <xs:sequence>
    <xs:element minOccurs="0" name="AdGroupEstimates" nillable="true" type="tns:ArrayOfAdGroupEstimate"/>
    <xs:element minOccurs="0" name="CampaignId" nillable="true" type="xs:long"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CampaignId*|The ad group identifier.|*long*|
|*AdGroupEstimates*|The nested list of suggested keywords for the campaign's ad groups with minimum and maximum traffic estimates.<br/><br/>Traffic estimates include average CPC, average position, clicks, CTR, impressions, and total cost.|[AdGroupEstimate](../adinsight-api/adgroupestimate-data-object.md) array|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordTrafficEstimates](../adinsight-api/getkeywordtrafficestimates-service-operation.md)  
