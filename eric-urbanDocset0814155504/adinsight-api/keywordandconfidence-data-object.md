---
title: "KeywordAndConfidence Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a4a98bac-b302-48bc-bcc3-399c47c14f9a
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordAndConfidence Data Object
Defines an object that contains a suggested keyword and a confidence score. The confidence score indicates the probability that the keyword would match a user’s search query.

## Syntax

```xml
<xs:complexType name="KeywordAndConfidence">
  <xs:sequence>
    <xs:element minOccurs="0" name="SuggestedKeyword" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="ConfidenceScore" type="xs:double" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*SuggestedKeyword*|The suggested keyword.|*string*|
|*ConfidenceScore*|A score from 0.0 to 1.0 that indicates the probability that the keyword would match a user’s search query.|*double*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[KeywordSuggestion](../adinsight-api/keywordsuggestion-data-object.md)  
[SuggestKeywordsForUrl](../adinsight-api/suggestkeywordsforurl-service-operation.md)  
[SuggestKeywordsFromExistingKeywords](../adinsight-api/suggestkeywordsfromexistingkeywords-service-operation.md)  

