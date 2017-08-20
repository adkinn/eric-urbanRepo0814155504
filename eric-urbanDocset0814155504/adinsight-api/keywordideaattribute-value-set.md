---
title: "KeywordIdeaAttribute Value Set"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4058f1a7-a063-464e-986e-0bda08d2c1d3
caps.latest.revision: 2
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordIdeaAttribute Value Set
Determines which properties of the [KeywordIdea](../adinsight-api/keywordidea-data-object.md) object you want returned when calling the [GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md) operation.

## Syntax

```xml
\<xs:simpleType name="KeywordIdeaAttribute">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="AdGroupId">
    \<xs:enumeration value="AdGroupName">
    \<xs:enumeration value="Keyword">
    \<xs:enumeration value="Source">
    \<xs:enumeration value="MonthlySearchCounts">
    \<xs:enumeration value="SuggestedBid">
    \<xs:enumeration value="Competition">
    \<xs:enumeration value="Relevance">
    \<xs:enumeration value="AdImpressionShare">
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|AdGroupId|Include the ad group identifier.|
|AdGroupName|Include the ad group name.|
|AdImpressionShare|Include the ad impression share.|
|Competition|Include the competition.|
|Keyword|Include the keyword.|
|MonthlySearchCounts|Include the monthly search counts.|
|Relevance|Include the relevance.|
|Source|Include the source.|
|SuggestedBid|Include the suggested bid.|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md)  

