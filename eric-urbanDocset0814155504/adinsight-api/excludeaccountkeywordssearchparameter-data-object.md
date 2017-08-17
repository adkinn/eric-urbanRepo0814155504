---
title: "ExcludeAccountKeywordsSearchParameter Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 466f1ea8-e1dc-45a0-a039-291d3484e1f4
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ExcludeAccountKeywordsSearchParameter Data Object
The exclude account keywords search parameter filter that you can include when requesting keyword ideas.

If you do not include the exclude account keywords search parameter when calling [GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md), then keyword ideas will be returned whether or not they already exist in your account.

## Syntax

```xml
\<xs:complexType name="ExcludeAccountKeywordsSearchParameter">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:SearchParameter">
      \<xs:sequence>
        \<xs:element minOccurs="0" name="ExcludeAccountKeywords" type="xs:boolean"/>
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ExcludeAccountKeywords*|Determines whether or not to exclude existing account keywords from the returned keyword ideas.<br/><br/>By default your existing account keywords will be included with the keyword idea data e.g., suggested bid. If you set the element *True* then the keyword ideas will not include any keywords for the same match type that already exist in your account.|*boolean*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md)  
