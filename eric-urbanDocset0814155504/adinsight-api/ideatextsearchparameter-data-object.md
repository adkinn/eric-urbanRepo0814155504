---
title: "IdeaTextSearchParameter Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 20f360c0-a9f4-45eb-983a-3981cd819b73
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# IdeaTextSearchParameter Data Object
The idea text search parameter filter that you can include when requesting keyword ideas.

Use these options to refine what keywords are returned when calling [GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md). You can limit the keyword ideas to include or exclude specific keywords. 

## Syntax

```xml
\<xs:complexType name="IdeaTextSearchParameter">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:SearchParameter">
      \<xs:sequence>
        \<xs:element name="Excluded" type="q2:ArrayOfKeyword" nillable="true" minOccurs="0" xmlns:q2="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity.Common"/>
        \<xs:element name="Included" type="q3:ArrayOfKeyword" nillable="true" minOccurs="0" xmlns:q3="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity.Common"/>
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Excluded*|The list of keywords that you explicitly want excluded from the list of returned keyword ideas.<br/><br/>The match type of each keyword must be set to Broad.|[Keyword](../adinsight-api/keyword-data-object.md) array|
|*Included*|The list of keywords that you explicitly want included in the list of returned keyword ideas.<br/><br/>The match type of each keyword must be set to Broad.|[Keyword](../adinsight-api/keyword-data-object.md) array|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordIdeaCategories](../adinsight-api/getkeywordideacategories-service-operation.md)  
[GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md)  
