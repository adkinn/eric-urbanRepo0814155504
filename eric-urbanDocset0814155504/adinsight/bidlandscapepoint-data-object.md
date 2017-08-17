---
title: "BidLandscapePoint Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e31ff6b5-6470-4999-9156-5a7a92edd28c
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BidLandscapePoint Data Object
Defines an object that contains estimates of clicks, cost, and impressions  given the suggested bid.

> [!NOTE]
> The estimates are not a prediction or guarantee of future performance. Estimates are for search traffic only, and not based on performance for ads on the content network.

## Syntax

```xml
\<xs:complexType name="BidLandscapePoint">
  \<xs:sequence>
    \<xs:element type="xs:double" name="Bid" minOccurs="0"/>
    \<xs:element type="xs:double" name="Clicks" nillable="true" minOccurs="0"/>
    \<xs:element type="xs:long" name="Impressions" minOccurs="0"/>
    \<xs:element type="xs:long" name="TopImpressions" nillable="true" minOccurs="0"/>
    \<xs:element type="tns:Currency" name="Currency" minOccurs="0"/>
    \<xs:element type="xs:double" name="Cost"  nillable="true" minOccurs="0"/>
    \<xs:element type="xs:double" name="MarginalCPC"  nillable="true" minOccurs="0"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Bid*|The suggested bid value.|*double*|
|*Clicks*|The estimated number of clicks.<br /><br />**Note:** This element will be nil if there is no estimate available.|*double*|
|*Cost*|The estimated cost.<br /><br />**Note:** This element will be nil if there is no estimate available.|*double*|
|*Currency*|The monetary unit of the suggested bid value and estimated performance statistics.|[Currency](../Ad Insight Version 11/currency-value-set.md)|
|*Impressions*|The estimated number of impressions.|*long*|
|*MarginalCPC*|Reserved for future use.|*double*|
|*TopImpressions*|The estimated number of impressions in the top or mainline ad results.<br /><br />**Note:** This element will be nil if there is no estimate available.|*long*|

## Requirements
[!INCLUDE[reqadint](../Ad Insight Version 11/includes/reqadint.md)]
## See Also
[KeywordBidLandscape](../Ad Insight Version 11/keywordbidlandscape-data-object.md)  
[GetBidLandscapeByKeywordIds](../Ad Insight Version 11/getbidlandscapebykeywordids-service-operation.md)  

