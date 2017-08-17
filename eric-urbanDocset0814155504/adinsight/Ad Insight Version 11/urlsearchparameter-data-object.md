---
title: "UrlSearchParameter Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d52f1dd0-cffb-4e0f-9fd6-4bd7a665a215
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# UrlSearchParameter Data Object
The URL search parameter that you can use as a seed for new keyword ideas.

## Syntax

```xml
\<xs:complexType name="UrlSearchParameter">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:SearchParameter">
      \<xs:sequence>
        \<xs:element minOccurs="0" name="Url" nillable="true" type="xs:string"/>
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Url*|The URL of your website or a page on your website.<br/><br/>**Note:** Bing Ads extracts keywords from the HTML code on your website or landing page. If your HTML code contains Javascript, which generates content at runtime, Bing Ads will not extract keywords rendered from the Javascript and you'll see fewer or no keywords.|*string*|

## Requirements
[!INCLUDE[reqadint](../Ad Insight Version 11/includes/reqadint.md)]
## See Also
[GetKeywordIdeas](../Ad Insight Version 11/getkeywordideas-service-operation.md)  
