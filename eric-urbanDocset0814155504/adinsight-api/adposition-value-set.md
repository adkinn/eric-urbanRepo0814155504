---
title: "AdPosition Value Set"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b26b4b60-01aa-43a2-bedd-1c0180f5b43c
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdPosition Value Set
Defines the possible positions of an ad in the search results or on a content-based webpage.

## Syntax

```xml
\<xs:simpleType name="AdPosition">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="All" />
    \<xs:enumeration value="MainLine1" />
    \<xs:enumeration value="MainLine2" />
    \<xs:enumeration value="MainLine3" />
    \<xs:enumeration value="MainLine4" />
    \<xs:enumeration value="SideBar1" />
    \<xs:enumeration value="SideBar2" />
    \<xs:enumeration value="SideBar3" />
    \<xs:enumeration value="SideBar4" />
    \<xs:enumeration value="SideBar5" />
    \<xs:enumeration value="SideBar6" />
    \<xs:enumeration value="SideBar7" />
    \<xs:enumeration value="SideBar8" />
    \<xs:enumeration value="SideBar9" />
    \<xs:enumeration value="SideBar10" />
    \<xs:enumeration value="Aggregate" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Aggregate|Aggregates the data for all supported positions.<br /><br />The following are examples of how the data is aggregated: Average bid would be the average bid of all the keywords in all the ad positions; Impressions is the sum of the number of impressions in all the ad positions; Clicks is the sum of the number of clicks in all the ad positions; Total cost is the sum of the cost of using the keywords in all the ad positions; AverageCTR is calculated by dividing the number of clicks by the number of impressions and multiplying the result by 100; AverageCPC is calculated by dividing the cost of all clicks by the number of clicks.|
|All|Indicates all search result positions.|
|MainLine1|The first ad to appear at the top of the search results page.|
|MainLine2|The second ad to appear at the top of the search results page.|
|MainLine3|The third ad to appear at the top of the search results page.|
|MainLine4|The fourth ad to appear at the top of the search results page.|
|SideBar1|The first ad to appear on the right side of the first search results page.|
|SideBar2|The second ad to appear on the right side of the first search results page.|
|SideBar3|The third ad to appear on the right side of the first search results page.|
|SideBar4|The fourth ad to appear on the right side of the first search results page.|
|SideBar5|The fifth ad to appear on the right side of the first search results page.|
|SideBar6|The sixth ad to appear on the right side of the first search results page.|
|SideBar7|The seventh ad to appear on the right side of the first search results page.|
|SideBar8|The eighth ad to appear on the right side of the first search results page.|
|SideBar9|The ninth ad to appear on the right side of the first search results page.|
|SideBar10|The tenth ad to appear on the right side of the first search results page.|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[EstimatedPositionAndTraffic](../adinsight-api/estimatedpositionandtraffic-data-object.md)  
[KeywordKPI](../adinsight-api/keywordkpi-data-object.md)  
[GetHistoricalKeywordPerformance](../adinsight-api/gethistoricalkeywordperformance-service-operation.md)  

