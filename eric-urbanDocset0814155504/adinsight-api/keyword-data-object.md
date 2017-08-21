---
title: "Keyword Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7d4b2d27-a343-4e06-b9e3-6cd282e338ca
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Keyword Data Object
Defines a keyword with match type.

## Syntax

```xml
<xs:complexType name="Keyword">
  <xs:sequence>
    <xs:element minOccurs="0" name="Id" nillable="true" type="xs:long"/>
    <xs:element xmlns:q1="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" minOccurs="0" name="MatchType" type="q1:MatchType"/>
    <xs:element minOccurs="0" name="Text" nillable="true" type="xs:string"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Id*|The Bing Ads identifier of the keyword.|*long*|
|*MatchType*|The match type of the keyword.|[MatchType](../adinsight-api/matchtype-value-set.md)|
|*Text*|The keyword text.|*string*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordTrafficEstimates](../adinsight-api/getkeywordtrafficestimates-service-operation.md)  

