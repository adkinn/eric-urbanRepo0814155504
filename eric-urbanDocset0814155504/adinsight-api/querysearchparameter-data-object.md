---
title: "QuerySearchParameter Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb52e1ea-f79c-4c46-bbb1-6e2375553a63
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# QuerySearchParameter Data Object
The query search parameter that you can use as a seed for new keyword ideas.

## Syntax

```xml
\<xs:complexType name="QuerySearchParameter">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:SearchParameter">
      \<xs:sequence>
        \<xs:element xmlns:q1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" minOccurs="0" name="Queries" nillable="true" type="q1:ArrayOfstring"/>
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Queries*|Up to 200 words or phrases that describe what you're advertising.|*string* array|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md)  
