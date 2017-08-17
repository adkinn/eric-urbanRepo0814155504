---
title: "SuggestedBidSearchParameter Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: acf4fc51-a329-467f-8321-461d600b0324
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SuggestedBidSearchParameter Data Object
The suggested bid search parameter filter that you can include when requesting keyword ideas.

If you do not include the suggested bid search parameter when calling [GetKeywordIdeas](../Ad Insight Version 11/getkeywordideas-service-operation.md), then keyword ideas will be returned regardless of suggested bid.

## Syntax

```xml
\<xs:complexType name="SuggestedBidSearchParameter">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:SearchParameter">
      \<xs:sequence>
        \<xs:element minOccurs="0" name="Maximum" nillable="true" type="xs:double"/>
        \<xs:element minOccurs="0" name="Maximum" nillable="true" type="xs:double"/>
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Maximum*|The maximum suggested bid that you want for keyword ideas.|*double*|
|*Maximum*|The minimum suggested bid that you want for keyword ideas.|*double*|

## Requirements
[!INCLUDE[reqadint](../Ad Insight Version 11/includes/reqadint.md)]
## See Also
[GetKeywordIdeas](../Ad Insight Version 11/getkeywordideas-service-operation.md)  
