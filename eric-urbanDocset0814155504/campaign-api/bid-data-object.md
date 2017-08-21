---
title: "Bid Data Object"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b6e3a40d-083c-4bfe-a800-48999cbae977
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Bid Data Object
Defines a bid.

## Syntax

```xml
<xs:complexType name="Bid">
  <xs:sequence>
    <xs:element minOccurs="0" name="Amount" nillable="true" type="xs:double" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Amount*|The bid value. For details about the valid bid range for your market, see [Currencies](http://msdn.microsoft.com/library/bing-ads-currencies.aspx).|*double*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdGroup](../campaign-api/adgroup-data-object.md)  
[Keyword](../campaign-api/keyword-data-object.md)  

