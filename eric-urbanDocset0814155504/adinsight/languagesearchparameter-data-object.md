---
title: "LanguageSearchParameter Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31261c36-bbee-43be-be8a-beb23b858108
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# LanguageSearchParameter Data Object
The language search parameter filter that you can include when requesting keyword ideas.

If you do not include the language search parameter when calling [GetKeywordIdeas](../Ad Insight Version 11/getkeywordideas-service-operation.md), then keyword ideas will be returned for all languages.

## Syntax

```xml
\<xs:complexType name="LanguageSearchParameter">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:SearchParameter">
      \<xs:sequence>
        \<xs:element xmlns:q7="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity.Criterions" minOccurs="0" name="Languages" nillable="true" type="q7:ArrayOfLanguageCriterion"/>
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Languages*|The language criterion list for the returned keyword ideas.|[LanguageCriterion](../Ad Insight Version 11/languagecriterion-data-object.md) array|

## Requirements
[!INCLUDE[reqadint](../Ad Insight Version 11/includes/reqadint.md)]
## See Also
[GetKeywordIdeas](../Ad Insight Version 11/getkeywordideas-service-operation.md)  
