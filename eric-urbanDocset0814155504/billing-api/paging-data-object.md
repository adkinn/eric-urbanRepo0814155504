---
title: "Paging Data Object"
ms.custom: ""
ms.date: "06/21/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b18e216c-fd40-4672-a764-3cbdb6dc4f30
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Paging Data Object
Defines a paging object for the list of insertion orders returned using the [SearchInsertionOrders](../billing-api/searchinsertionorders-service-operation.md) operation.

## Syntax

```xml
<xs:complexType name="Paging">
  <xs:sequence>
    <xs:element name="Index" type="xs:int" minOccurs="0"/>
    <xs:element name="Size" type="xs:int" minOccurs="0"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Index*|The zero-based results page index. For example to request the first page of results, set this value to 0 (zero).|*int*|
|*Size*|The page size and the number of results to return in the specified page.<br /><br />The maximum size is 1,000.|*int*|

## Requirements
[!INCLUDE[reqbilling](../billing-api/includes/reqbilling.md)]
## See Also
[SearchInsertionOrders](../billing-api/searchinsertionorders-service-operation.md)

