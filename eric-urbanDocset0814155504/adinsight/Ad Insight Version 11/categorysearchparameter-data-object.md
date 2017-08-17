---
title: "CategorySearchParameter Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5fe67852-540f-48df-a316-86b9641d8b75
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CategorySearchParameter Data Object
The keyword category search parameter that you can use as a seed for new keyword ideas.

## Syntax

```xml
\<xs:complexType name="CategorySearchParameter">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:SearchParameter">
      \<xs:sequence>
        \<xs:element minOccurs="0" name="CategoryId" type="xs:long"/>
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CategoryId*|The Bing Ads identifier for the keyword category.<br/><br/>To get a list of keyword category identifiers, use the [GetKeywordIdeaCategories](../Ad Insight Version 11/getkeywordideacategories-service-operation.md) service operation.|*long*|

## Requirements
[!INCLUDE[reqadint](../Ad Insight Version 11/includes/reqadint.md)]
## See Also
[GetKeywordIdeaCategories](../Ad Insight Version 11/getkeywordideacategories-service-operation.md)  
[GetKeywordIdeas](../Ad Insight Version 11/getkeywordideas-service-operation.md)  
