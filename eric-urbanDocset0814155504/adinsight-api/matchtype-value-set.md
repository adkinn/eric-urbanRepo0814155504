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
<xs:simpleType name="MatchType">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Exact" />
    <xs:enumeration value="Phrase" />
    <xs:enumeration value="Broad" />
    <xs:enumeration value="Content" />
    <xs:enumeration value="Aggregate" />
  </xs:restriction>
</xs:simpleType>
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
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[EstimatedBidAndTraffic](../adinsight-api/estimatedbidandtraffic-data-object.md)  
[EstimatedPositionAndTraffic](../adinsight-api/estimatedpositionandtraffic-data-object.md)  
[KeywordAndMatchType](../adinsight-api/keywordandmatchtype-data-object.md)  
[KeywordKPI](../adinsight-api/keywordkpi-data-object.md)  
[GetEstimatedPositionByKeywords](../adinsight-api/getestimatedpositionbykeywords-service-operation.md)  
[GetHistoricalKeywordPerformance](../adinsight-api/gethistoricalkeywordperformance-service-operation.md)  

