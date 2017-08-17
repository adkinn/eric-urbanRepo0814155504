---
title: "KeywordEstimatedBid Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2bb56b91-cb7a-471b-a39a-deae9e8f5ada
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordEstimatedBid Data Object
Defines an object that contains the keyword and the estimated bid value for each match type.

> [!NOTE]
> The estimates are not a prediction or guarantee of future performance.

## Syntax

```xml
\<xs:complexType name="KeywordEstimatedBid">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="Keyword" nillable="true" type="xs:string" />
    \<xs:element minOccurs="0" name="EstimatedBids" nillable="true" type="tns:ArrayOfEstimatedBidAndTraffic" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*EstimatedBids*|A list of [EstimatedBidAndTraffic](../adinsight-api/estimatedbidandtraffic-data-object.md) data objects that contains the suggested bid value for the keyword and match type. If there is data available for the keyword, the [EstimatedBidAndTraffic](../adinsight-api/estimatedbidandtraffic-data-object.md) object will provide an estimated bid value. Otherwise, if no data is available the *EstimatedBids* element will be null.<br /><br />Each object also contains estimates of clicks, average cost per click (CPC), impressions, click-through rate (CTR), and total cost given the suggested bid.<br /><br />If there is no data available for a match type, the array will not include estimates for the match type.<br /><br />**Note:** Some returned elements of the [EstimatedBidAndTraffic](../adinsight-api/estimatedbidandtraffic-data-object.md) may be NULL.|[EstimatedBidAndTraffic](../adinsight-api/estimatedbidandtraffic-data-object.md) array|
|*Keyword*|The keyword to which the estimates apply.|*string*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[KeywordIdEstimatedBid](../adinsight-api/keywordidestimatedbid-data-object.md)  
[GetEstimatedBidByKeywordIds](../adinsight-api/getestimatedbidbykeywordids-service-operation.md)  
[GetEstimatedBidByKeywords](../adinsight-api/getestimatedbidbykeywords-service-operation.md)  

