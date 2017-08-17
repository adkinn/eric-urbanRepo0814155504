---
title: "KeywordDemographicResult Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8302bf12-d2df-4401-bfd1-513a6fbbc1c8
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordDemographicResult Data Object
Defines an object that contains the keyword and percentage of users by age and gender (if known) who searched for the specified keyword.

## Syntax

```xml
\<xs:complexType name="KeywordDemographicResult">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="Keyword" nillable="true" type="xs:string" />
    \<xs:element minOccurs="0" name="KeywordDemographics" nillable="true" type="tns:KeywordDemographic" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Keyword*|The keyword.|*string*|
|*KeywordDemographics*|An array of [KeywordDemographic](../Ad Insight Version 11/keyworddemographic-data-object.md) data objects that contains the percentage of users by age and gender (if known) that searched for the keyword on the device.|[KeywordDemographic](../Ad Insight Version 11/keyworddemographic-data-object.md) array|

## Requirements
[!INCLUDE[reqadint](../Ad Insight Version 11/includes/reqadint.md)]
## See Also
[GetKeywordDemographics](../Ad Insight Version 11/getkeyworddemographics-service-operation.md)

