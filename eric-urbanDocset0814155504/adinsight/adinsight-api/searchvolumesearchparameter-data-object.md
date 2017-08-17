---
title: "SearchVolumeSearchParameter Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 20f9babb-cc6b-4742-8591-5c79e3fb402a
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SearchVolumeSearchParameter Data Object
The search volume search parameter filter that you can include when requesting keyword ideas.

If you do not include the search volume search parameter when calling [GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md), then keyword ideas will be returned regardless of search volume.

## Syntax

```xml
\<xs:complexType name="SearchVolumeSearchParameter">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:SearchParameter">
      \<xs:sequence>
        \<xs:element minOccurs="0" name="Maximum" nillable="true" type="xs:long"/>
        \<xs:element minOccurs="0" name="Minimum" nillable="true" type="xs:long"/>
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Maximum*|The maximum search volume that you want for keyword ideas.|*long*|
|*Maximum*|The minimum search volume that you want for keyword ideas.|*long*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md)  
