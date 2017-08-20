---
title: "KeywordIdEstimatedBid Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e9165126-27be-44cc-8610-c2a42cd3a0c9
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordIdEstimatedBid Data Object
Defines an object that contains the identifier of the keyword and the suggested bid value for the keyword and match type.

> [!NOTE]
> The estimates are not a prediction or guarantee of future performance.

## Syntax

```xml
<xs:complexType name="KeywordIdEstimatedBid">
  <xs:sequence>
    <xs:element minOccurs="0" name="KeywordId" type="xs:long" />
    <xs:element minOccurs="0" name="KeywordEstimatedBid" nillable="true" type="tns:KeywordEstimatedBid" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*KeywordEstimatedBid*|An object that contains the keyword string and the suggested bid value for each match type.|[KeywordEstimatedBid](../adinsight-api/keywordestimatedbid-data-object.md)|
|*KeywordId*|The identifier of the keyword to which the suggested bid applies.|*long*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetEstimatedBidByKeywordIds](../adinsight-api/getestimatedbidbykeywordids-service-operation.md)

