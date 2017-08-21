---
title: "KeywordCategory Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4615e2d0-0f02-4315-895d-7e08e9baf6c7
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordCategory Data Object
Defines an object that contains a keyword category and a confidence score. The confidence score indicates the likelihood that the keyword belongs to the keyword category.

## Syntax

```xml
<xs:complexType name="KeywordCategory">
  <xs:sequence>
    <xs:element minOccurs="0" name="Category" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="ConfidenceScore" type="xs:double" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Category*|The keyword category that the keyword might belong to.<br /><br />If the category is undetermined, this element is set to Unknown Category and the ConfidenceScore element is set to 0.0.|*string*|
|*ConfidenceScore*|A score from 0.0 to 1.0 that indicates the likelihood that the keyword belongs to the category.|*double*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[KeywordCategoryResult](../adinsight-api/keywordcategoryresult-data-object.md)
[GetKeywordCategories](../adinsight-api/getkeywordcategories-service-operation.md)

