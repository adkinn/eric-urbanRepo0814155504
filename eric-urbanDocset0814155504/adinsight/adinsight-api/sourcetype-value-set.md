---
title: "SourceType Value Set"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6fee8ce6-9b19-420a-87ac-80b94dd292f2
caps.latest.revision: 2
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SourceType Value Set
Defines the source or seed for the keyword idea. 

You can request that the source be returned in the [KeywordIdea](../adinsight-api/keywordidea-data-object.md) object when calling the [GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md) operation.

## Syntax

```xml
\<xs:simpleType name="SourceType">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Unknown">
    \<xs:enumeration value="Seed">
    \<xs:enumeration value="SuggestionFromKeyword">
    \<xs:enumeration value="SuggestionFromUrl">
    \<xs:enumeration value="SuggestionFromCategory">
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Seed|The keyword idea source is a seed that you provided such as the query search parameter.|
|SuggestionFromCategory|The keyword idea is sourced from a provided category.|
|SuggestionFromKeyword|The keyword idea is sourced from a provided keyword.|
|SuggestionFromCategory|The keyword idea is sourced from a provided URL.|
|Unknown|The keyword idea source is unknown.|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md)  

