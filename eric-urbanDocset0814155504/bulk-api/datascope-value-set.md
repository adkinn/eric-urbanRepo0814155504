---
title: "DataScope Value Set"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5bc7405b-f5e0-4882-a855-5335d7cd6a61
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DataScope Value Set
Defines the scope or types of data to download.

## Syntax

```xml
\<xs:simpleType name="DataScope">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="EntityData" />
    \<xs:enumeration value="EntityPerformanceData" />
    \<xs:enumeration value="QualityScoreData" />
    \<xs:enumeration value="BidSuggestionsData" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|BidSuggestionsData|Download the bid suggestions records.|
|EntityData|Download the entity attributes records.|
|EntityPerformanceData|Download the performance data fields for the corresponding entity records. The performance data is a summary aggregation per downloaded entity. If you want data aggregated by day, week, or month, you can use the Bing Ads Reporting API.|
|QualityScoreData|Download the quality score fields for the corresponding entity records.|

## Requirements
[!INCLUDE[reqbulk](../bulk-api/includes/reqbulk.md)]
## See Also
[DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md)  
[DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md)  

