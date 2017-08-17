---
title: "KeywordAndMatchType Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 470e9f13-549e-473c-b009-40f2f72db0b0
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordAndMatchType Data Object
Defines an object that contains a keyword and corresponding match types.

## Syntax

```xml
\<xs:complexType name="KeywordAndMatchType">
  \<xs:sequence>
    \<xs:element type="xs:string" name="KeywordText" nillable="true" minOccurs="0"/>
    \<xs:element type="tns:ArrayOfMatchType" name="MatchTypes" nillable="true" minOccurs="0"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*KeywordText*|The keyword text.|*string*|
|*MatchTypes*|The corresponding match types for the keyword.|[MatchType](../Ad Insight Version 11/matchtype-value-set.md) array|

## Requirements
[!INCLUDE[reqadint](../Ad Insight Version 11/includes/reqadint.md)]
## See Also
[GetEstimatedBidByKeywords](../Ad Insight Version 11/getestimatedbidbykeywords-service-operation.md)

