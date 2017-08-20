---
title: "KeywordIdeaCategory Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1ec205da-1e3c-41e7-a11f-c9665fb6b445
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordIdeaCategory Data Object
Defines an object that contains a keyword idea category.

You can use the category identifier in the [CategorySearchParameter](../adinsight-api/categorysearchparameter-data-object.md) when calling [GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md).

## Syntax

```xml
\<xs:complexType name="KeywordIdeaCategory">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="CategoryId" type="xs:long"/>
    \<xs:element minOccurs="0" name="CategoryName" nillable="true" type="xs:string"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CategoryId*|The Bing Ads identifier of the keyword idea category.|*long*|
|*CategoryName*|The name of the keyword idea category.|*string*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordIdeaCategories](../adinsight-api/getkeywordideacategories-service-operation.md)  
[GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md)  
