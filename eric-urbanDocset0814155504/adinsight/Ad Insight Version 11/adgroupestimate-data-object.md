---
title: "AdGroupEstimate Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 88896178-d1bd-4bf5-b6ae-cc3e81acadbc
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdGroupEstimate Data Object
Contains a list of suggested keywords for the ad group with minimum and maximum traffic estimates. Traffic estimates include average CPC, average position, clicks, CTR, impressions, and total cost.

> [!NOTE]
> The estimates are not a prediction or guarantee of future performance.

## Syntax

```xml
\<xs:complexType name="AdGroupEstimate">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="AdGroupId" nillable="true" type="xs:long"/>
    \<xs:element minOccurs="0" name="KeywordEstimates" nillable="true" type="tns:ArrayOfKeywordEstimate"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdGroupId*|The ad group identifier.|*long*|
|*KeywordEstimates*|The list of suggested keywords with minimum and maximum traffic estimates.<br/><br/>Traffic estimates include average CPC, average position, clicks, CTR, impressions, and total cost.|[KeywordEstimate](../Ad Insight Version 11/keywordestimate-data-object.md) array|

## Requirements
[!INCLUDE[reqadint](../Ad Insight Version 11/includes/reqadint.md)]
## See Also
[GetKeywordTrafficEstimates](../Ad Insight Version 11/getkeywordtrafficestimates-service-operation.md)  
