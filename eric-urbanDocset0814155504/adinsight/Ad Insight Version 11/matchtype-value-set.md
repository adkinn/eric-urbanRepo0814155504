---
title: "MatchType Value Set"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1ab49f55-5644-4ea9-b154-eef92501ae95
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# MatchType Value Set
Defines the possible keyword match type values.

## Syntax

```xml
\<xs:simpleType name="MatchType">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Exact" />
    \<xs:enumeration value="Phrase" />
    \<xs:enumeration value="Broad" />
    \<xs:enumeration value="Content" />
    \<xs:enumeration value="Aggregate" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Aggregate|Aggregates the data across all match types.|
|Broad|A broad match results when words in the keyword are present in the user's search query; however, the word order can vary.|
|Content|A content match results when the keywords extracted from the content webpage match the keywords in the user’s search query by using an exact match comparison. An exact match results when all of the words in the keyword exactly match the user's query.|
|Exact|An exact match results when all of the words in the keyword exactly match the user's search query.|
|Phrase|A phrase match results when all of the words in the keyword are present in the user's search query and are in the same order.|

## Requirements
[!INCLUDE[reqadint](../Ad Insight Version 11/includes/reqadint.md)]
## See Also
[EstimatedBidAndTraffic](../Ad Insight Version 11/estimatedbidandtraffic-data-object.md)  
[EstimatedPositionAndTraffic](../Ad Insight Version 11/estimatedpositionandtraffic-data-object.md)  
[KeywordAndMatchType](../Ad Insight Version 11/keywordandmatchtype-data-object.md)  
[KeywordKPI](../Ad Insight Version 11/keywordkpi-data-object.md)  
[GetEstimatedPositionByKeywords](../Ad Insight Version 11/getestimatedpositionbykeywords-service-operation.md)  
[GetHistoricalKeywordPerformance](../Ad Insight Version 11/gethistoricalkeywordperformance-service-operation.md)  

