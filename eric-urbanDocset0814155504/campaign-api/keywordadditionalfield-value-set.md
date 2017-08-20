---
title: "KeywordAdditionalField Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2873b82d-c463-4559-91d4-348c96c06173
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordAdditionalField Value Set
Defines a list of optional [Keyword](../campaign-api/keyword-data-object.md) properties that you can request when calling [GetKeywordsByAdGroupId](../campaign-api/getkeywordsbyadgroupid-service-operation.md), [GetKeywordsByEditorialStatus](../campaign-api/getkeywordsbyeditorialstatus-service-operation.md), and [GetKeywordsByIds](../campaign-api/getkeywordsbyids-service-operation.md). This set of flags enables you to get the latest features using the current version of Bing Ads Campaign Management API, and in the next version the corresponding propertys will be included in the [Keyword](../campaign-api/keyword-data-object.md) object by default.

## Syntax

```xml
\<xs:simpleType name="KeywordAdditionalField">
  \<xs:list>
    \<xs:simpleType>
      \<xs:restriction base="xs:string">
        \<xs:enumeration value="InheritedBidStrategyType" />
      \</xs:restriction>
    \</xs:simpleType>
  \</xs:list>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|InheritedBidStrategyType|Includes the *InheritedBidStrategyType* element that can be nested within the *BiddingScheme* element of an [Keyword](../campaign-api/keyword-data-object.md) object. The *InheritedBidStrategyType* will only be returned if the *BiddingScheme* element is an [InheritFromParentBiddingScheme](../campaign-api/inheritfromparentbiddingscheme-data-object.md) object.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[GetKeywordsByAdGroupId](../campaign-api/getkeywordsbyadgroupid-service-operation.md)  
[GetKeywordsByIds](../campaign-api/getkeywordsbyids-service-operation.md)  
[GetKeywordsByEditorialStatus](../campaign-api/getkeywordsbyeditorialstatus-service-operation.md)  
[Keyword](../campaign-api/keyword-data-object.md)  
[InheritFromParentBiddingScheme](../campaign-api/inheritfromparentbiddingscheme-data-object.md)