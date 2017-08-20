---
title: "ImpressionShareSearchParameter Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f1fdf938-8059-49a4-93eb-f0e352d8e1b5
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ImpressionShareSearchParameter Data Object
The impression share search parameter filter that you can include when requesting keyword ideas.

If you do not include the impression share search parameter when calling [GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md), then keyword ideas will be returned regardless of impression share.

## Syntax

```xml
\<xs:complexType name="ImpressionShareSearchParameter">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:SearchParameter">
      \<xs:sequence>
        \<xs:element minOccurs="0" name="Maximum" nillable="true" type="xs:double"/>
        \<xs:element minOccurs="0" name="Minimum" nillable="true" type="xs:double"/>
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Maximum*|The maximum impression share that you want for keyword ideas.|*double*|
|*Maximum*|The minimum impression share that you want for keyword ideas.|*double*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md)  
