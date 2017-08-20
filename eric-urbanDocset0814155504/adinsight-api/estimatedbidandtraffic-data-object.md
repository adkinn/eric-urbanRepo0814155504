---
title: "EstimatedBidAndTraffic Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 35d32ae9-4d74-4484-81ff-97590ddfe986
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# EstimatedBidAndTraffic Data Object
Defines an object that contains estimates of clicks, average cost per click (CPC), impressions, click-through rate (CTR), and total cost for the corresponding keyword or ad group given the suggested bid.

> [!NOTE]
> The estimates are not a prediction or guarantee of future performance.

## Syntax

```xml
\<xs:complexType name="EstimatedBidAndTraffic">
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
    \<xs:element minOccurs="0" name="EstimatedMinBid" type="xs:double" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AverageCPC*|The estimated average CPC.<br /><br />The formula used to calculate the average CPC is (maximum total cost / maximum number of clicks).|*double*|
|*CTR*|The estimated CTR.<br /><br />The formula used to calculate the CTR is (maximum number of clicks / maximum number of impressions) &#42; 100.|*double*|
|*Currency*|The monetary unit of the cost estimates and suggested bid value.|[Currency](../adinsight-api/currency-value-set.md)|
|*EstimatedMinBid*|The suggested bid value.|*double*|
|*MatchType*|The match type used to determine the estimates.|[MatchType](../adinsight-api/matchtype-value-set.md)|
|*MaxClicksPerWeek*|The estimated maximum number of clicks per week.|*double*|
|*MaxImpressionsPerWeek*|The estimated maximum number of impressions per week.|*long*|
|*MaxTotalCostPerWeek*|The estimated maximum cost per week.|*double*|
|*MinClicksPerWeek*|The estimated minimum number of clicks per week.|*double*|
|*MinImpressionsPerWeek*|The estimated minimum number of impressions per week.|*long*|
|*MinTotalCostPerWeek*|The estimated minimum cost per week.|*double*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[KeywordEstimatedBid](../adinsight-api/keywordestimatedbid-data-object.md)  
[KeywordIdEstimatedBid](../adinsight-api/keywordidestimatedbid-data-object.md)  
[GetEstimatedBidByKeywordIds](../adinsight-api/getestimatedbidbykeywordids-service-operation.md)  
[GetEstimatedBidByKeywords](../adinsight-api/getestimatedbidbykeywords-service-operation.md)  

