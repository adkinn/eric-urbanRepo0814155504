---
title: "KeywordIdEstimatedPosition Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b2f32006-c0e5-4082-9fac-ce0502da37aa
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordIdEstimatedPosition Data Object
Defines an object that contains the identifier of a keyword and the estimated search results position for the keyword and match type.

> [!NOTE]
> The estimates are not a prediction or guarantee of future performance.

## Syntax

```xml
\<xs:complexType name="KeywordIdEstimatedPosition">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="KeywordId" type="xs:long" />
    \<xs:element minOccurs="0" name="KeywordEstimatedPosition" nillable="true" type="tns:KeywordEstimatedPosition" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*KeywordEstimatedPosition*|An object that contains the keyword string and estimated position in the search results given the specified maximum bid.|[KeywordEstimatedPosition](../Ad Insight Version 11/keywordestimatedposition-data-object.md)|
|*KeywordId*|The identifier of the keyword to which the estimated position applies.|*long*|

## Requirements
[!INCLUDE[reqadint](../Ad Insight Version 11/includes/reqadint.md)]
## See Also
[GetEstimatedPositionByKeywordIds](../Ad Insight Version 11/getestimatedpositionbykeywordids-service-operation.md)

