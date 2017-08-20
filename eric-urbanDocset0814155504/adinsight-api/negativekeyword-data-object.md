---
title: "NegativeKeyword Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 203ea81a-01ab-44e0-a338-a73d1b3edd52
caps.latest.revision: 2
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# NegativeKeyword Data Object
Defines a negative keyword with match type.

## Syntax

```xml
\<xs:complexType name="NegativeKeyword">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="Id" nillable="true" type="xs:long"/>
    \<xs:element xmlns:q2="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" minOccurs="0" name="MatchType" type="q2:MatchType"/>
    \<xs:element minOccurs="0" name="Text" nillable="true" type="xs:string"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Id*|The Bing Ads identifier of the negative keyword.|*long*|
|*MatchTypes*|The match type of the negative keyword.|[MatchType](../adinsight-api/matchtype-value-set.md)|
|*Text*|The negative keyword text.|*string*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordTrafficEstimates](../adinsight-api/getkeywordtrafficestimates-service-operation.md)  

