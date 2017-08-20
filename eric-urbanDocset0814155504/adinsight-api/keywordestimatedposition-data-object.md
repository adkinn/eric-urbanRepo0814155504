---
title: "KeywordEstimatedPosition Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: daebf210-bf80-4011-936c-1f2a046fe41c
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordEstimatedPosition Data Object
Defines an object that contains the keyword and the estimated position in the search results for each match type.

> [!NOTE]
> The estimates are not a prediction or guarantee of future performance.

## Syntax

```xml
<xs:complexType name="KeywordEstimatedPosition">
  <xs:sequence>
    <xs:element minOccurs="0" name="Keyword" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="EstimatedPositions" nillable="true" type="tns:ArrayOfEstimatedPositionAndTraffic" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*EstimatedPositions*|An array of [EstimatedPositionAndTraffic](../adinsight-api/estimatedpositionandtraffic-data-object.md) data objects that contains the position in the search results corresponding to the specified maximum bid.<br /><br />Each object also contains estimates of clicks, average cost per click (CPC), impressions, click-through rate (CTR), and total cost given the specified bid.<br /><br />If there is no data available for a match type, the array will not include estimates for the match type.|[EstimatedPositionAndTraffic](../adinsight-api/estimatedpositionandtraffic-data-object.md) array|
|*Keyword*|The keyword to which the estimates apply.|*string*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[KeywordIdEstimatedPosition](../adinsight-api/keywordidestimatedposition-data-object.md)  
[GetEstimatedPositionByKeywordIds](../adinsight-api/getestimatedpositionbykeywordids-service-operation.md)  
[GetEstimatedPositionByKeywords](../adinsight-api/getestimatedpositionbykeywords-service-operation.md)  

