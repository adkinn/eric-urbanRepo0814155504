---
title: "BroadMatchSearchQueryKPI Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f330d946-efac-4729-bbab-d57917a939ab
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BroadMatchSearchQueryKPI Data Object
Defines an object that contains search query statistics of including broad match type keyword bids.

## Syntax

```xml
\<xs:complexType name="BroadMatchSearchQueryKPI">
  \<xs:sequence>
    \<xs:element name="AverageCTR" type="xs:double" minOccurs="0"/>
    \<xs:element name="Clicks" type="xs:double" minOccurs="0"/>
    \<xs:element name="Impressions" type="xs:long" minOccurs="0"/>
    \<xs:element name="SRPV" type="xs:long" minOccurs="0"/>
    \<xs:element name="SearchQuery" type="xs:string" minOccurs="0" nillable="true"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AverageCTR*|The average CTR for the search query.|*double*|
|*Clicks*|The clicks for the search query.|*double*|
|*Impressions*|The impressions for the search query.|*long*|
|*SRPV*|The SRPV for the search query.|*long*|
|*SearchQuery*|The search query corresponding to the keyword.|*string*|

## Requirements
[!INCLUDE[reqadint](../Ad Insight Version 11/includes/reqadint.md)]
## See Also
[GetKeywordOpportunities](../Ad Insight Version 11/getkeywordopportunities-service-operation.md)  
[BroadMatchKeywordOpportunity](../Ad Insight Version 11/broadmatchkeywordopportunity-data-object.md)  

