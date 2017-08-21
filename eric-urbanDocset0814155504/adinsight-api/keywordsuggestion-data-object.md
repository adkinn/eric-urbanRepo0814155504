---
title: "KeywordSuggestion Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e552193b-2c6b-41e2-9e7c-60c3367ba531
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordSuggestion Data Object
Defines an object that contains a list of suggested keywords that may perform better than the specified keyword.

## Syntax

```xml
<xs:complexType name="KeywordSuggestion">
  <xs:sequence>
    <xs:element minOccurs="0" name="Keyword" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="SuggestionsAndConfidence" nillable="true" type="tns:ArrayOfKeywordAndConfidence" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Keyword*|The keyword to which the suggested keywords apply.|*string*|
|*SuggestionsAndConfidence*|A [KeywordAndConfidence](../adinsight-api/keywordandconfidence-data-object.md) array that contains a list of suggested keywords and, for each keyword, a score that indicates the probability that using the keyword would result in an ad being included in the results of a search query.<br /><br />The suggested keywords are sorted in order from keywords with the highest confidence score to those with the lowest confidence score.|[KeywordAndConfidence](../adinsight-api/keywordandconfidence-data-object.md) array|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[SuggestKeywordsFromExistingKeywords](../adinsight-api/suggestkeywordsfromexistingkeywords-service-operation.md)

