---
title: "MatchType Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 50a771ae-2751-4925-ba62-8709c0677903
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# MatchType Value Set
Defines the possible match types for a keyword or negative keyword.

## Syntax

```xml
\<xs:simpleType name="MatchType">
  \<xs:annotation>
    \<xs:appinfo>
      <ActualType Name="unsignedByte" Namespace="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/2003/10/Serialization/" />
    \</xs:appinfo>
  \</xs:annotation>
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Exact" />
    \<xs:enumeration value="Phrase" />
    \<xs:enumeration value="Broad" />
    \<xs:enumeration value="Content" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Broad|The match type is Broad.|
|Content|The match type is Content.|
|Exact|The match type is Exact.|
|Phrase|The match type is Phrase.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[Keyword](../campaign-api/keyword-data-object.md)  
[NegativeKeyword](../campaign-api/negativekeyword-data-object.md)  

