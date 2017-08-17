---
title: "KeywordKPI Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 78beb008-ca91-4d19-801b-5be05cc76f64
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordKPI Data Object
Defines a key performance index object for a keyword. The object contains the historical performance statistics of the keyword for the corresponding match type, ad position, device, and network.

## Syntax

```xml
\<xs:complexType name="KeywordKPI">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="Device" nillable="true" type="xs:string"/>
    \<xs:element minOccurs="0" name="MatchType" type="tns:MatchType" />
    \<xs:element minOccurs="0" name="AdPosition" type="tns:AdPosition" />
    \<xs:element minOccurs="0" name="Clicks" type="xs:int" />
    \<xs:element minOccurs="0" name="Impressions" type="xs:long" />
    \<xs:element minOccurs="0" name="AverageCPC" type="xs:double" />
    \<xs:element minOccurs="0" name="CTR" type="xs:double" />
    \<xs:element minOccurs="0" name="TotalCost" type="xs:double" />
    \<xs:element minOccurs="0" name="AverageBid" type="xs:double" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdPosition*|The position in the search results in which the ad appeared.|[AdPosition](../adinsight-api/adposition-value-set.md)|
|*AverageBid*|The average bid of the keyword.|*double*|
|*AverageCPC*|The average cost per click (CPC). The average CPC is calculated by dividing the cost of all clicks by the number of clicks.|*double*|
|*Clicks*|The number of clicks that the keyword and match type generated during the specified time interval.|*int*|
|*CTR*|The click-through rate (CTR) as a percentage. The CTR is calculated by dividing the number of clicks by the number of impressions and multiplying the result by 100.|*double*|
|*Device*|The device where the ad appeared.|*string*|
|*Impressions*|The number of impressions that the keyword and match type generated during the specified time interval.|*long*|
|*MatchType*|The match type that you specified in the request.|[MatchType](../adinsight-api/matchtype-value-set.md)|
|*TotalCost*|The cost of using the specified keyword and match type during the specified time interval.<br /><br />[!INCLUDE[adint_default_currency](../adinsight-api/includes/adint-default-currency.md)]|*double*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[KeywordHistoricalPerformance](../adinsight-api/keywordhistoricalperformance-data-object.md)  
[GetHistoricalKeywordPerformance](../adinsight-api/gethistoricalkeywordperformance-service-operation.md)  

