---
title: "EstimatedPositionAndTraffic Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e124049a-4be4-4421-8ee2-c0089f5c3687
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# EstimatedPositionAndTraffic Data Object
Defines an object that contains the estimated search results position and estimated keyword statistics such as clicks, average cost per click (CPC), impressions, click-through rate (CTR), and total cost for the specified keyword given the specified bid.

> [!NOTE]
> The estimates are not a prediction or guarantee of future performance.

## Syntax

```xml
\<xs:complexType name="EstimatedPositionAndTraffic">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="MatchType" type="tns:MatchType" />
    \<xs:element minOccurs="0" name="MinClicksPerWeek" type="xs:double" />
    \<xs:element minOccurs="0" name="MaxClicksPerWeek" type="xs:double" />
    \<xs:element minOccurs="0" name="AverageCPC" type="xs:double" />
    \<xs:element minOccurs="0" name="MinImpressionsPerWeek" type="xs:long" />
    \<xs:element minOccurs="0" name="MaxImpressionsPerWeek" type="xs:long" />
    \<xs:element minOccurs="0" name="CTR" type="xs:double" />
    \<xs:element minOccurs="0" name="MinTotalCostPerWeek" type="xs:double" />
    \<xs:element minOccurs="0" name="MaxTotalCostPerWeek" type="xs:double" />
    \<xs:element minOccurs="0" name="Currency" type="tns:Currency" />
    \<xs:element minOccurs="0" name="EstimatedAdPosition" type="xs:double" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AverageCPC*|The estimated average CPC.<br /><br />The formula used to calculate the average CPC is (maximum total cost / maximum number of clicks).|*double*|
|*CTR*|The estimated CTR.<br /><br />The formula used to calculate the CTR is (maximum number of clicks / maximum number of impressions) &#42; 100.|*double*|
|*Currency*|The monetary unit of the cost values, such as *AverageCPC*.|[Currency](../Ad Insight Version 11/currency-value-set.md)|
|*EstimatedAdPosition*|The position in the search results given the specified bid.|*double*|
|*MatchType*|The keyword match type used to determine the estimates.|[MatchType](../Ad Insight Version 11/matchtype-value-set.md)|
|*MaxClicksPerWeek*|The estimated maximum number of clicks per week.|*double*|
|*MaxImpressionsPerWeek*|The estimated maximum number of impressions per week.|*long*|
|*MaxTotalCostPerWeek*|The estimated maximum cost per week.|*double*|
|*MinClicksPerWeek*|The estimated minimum number of clicks per week.|*double*|
|*MinImpressionsPerWeek*|The estimated minimum number of impressions per week.|*long*|
|*MinTotalCostPerWeek*|The estimated minimum cost per week.|*double*|

## Requirements
[!INCLUDE[reqadint](../Ad Insight Version 11/includes/reqadint.md)]
## See Also
[KeywordEstimatedPosition](../Ad Insight Version 11/keywordestimatedposition-data-object.md)  
[KeywordIdEstimatedPosition](../Ad Insight Version 11/keywordidestimatedposition-data-object.md)  
[GetEstimatedPositionByKeywordIds](../Ad Insight Version 11/getestimatedpositionbykeywordids-service-operation.md)  
[GetEstimatedPositionByKeywords](../Ad Insight Version 11/getestimatedpositionbykeywords-service-operation.md)  

