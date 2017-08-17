---
title: "KeywordCategoryResult Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98b906b7-25e0-42dc-9ada-d3bf6c7db4e6
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordCategoryResult Data Object
Defines an object that contains the keyword and a list of keyword categories that the keyword might belong to.

## Syntax

```xml
\<xs:complexType name="KeywordCategoryResult">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="Keyword" nillable="true" type="xs:string" />
    \<xs:element minOccurs="0" name="KeywordCategories" nillable="true" type="tns:ArrayOfKeywordCategory" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Keyword*|The keyword being categorized.|*string*|
|*KeywordCategories*|An array of [KeywordCategory](../Ad Insight Version 11/keywordcategory-data-object.md) objects that contains a keyword category and a score that indicates the confidence that the keyword belongs to that keyword category.|[KeywordCategory](../Ad Insight Version 11/keywordcategory-data-object.md) array|

## Requirements
[!INCLUDE[reqadint](../Ad Insight Version 11/includes/reqadint.md)]
## See Also
[GetKeywordCategories](../Ad Insight Version 11/getkeywordcategories-service-operation.md)

