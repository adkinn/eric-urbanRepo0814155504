---
title: "SortOrder Value Set"
ms.custom: ""
ms.date: "05/27/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5542d5f-ac25-450f-9c19-0b383204a024
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SortOrder Value Set
Defines the ascending or descending sort order of results for [SearchInsertionOrders](../billing-api/searchinsertionorders-service-operation.md).

## Syntax

```xml
\<xs:simpleType name="SortOrder">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Ascending" />
    \<xs:enumeration value="Descending" />
  \</xs:restriction>
\</xs:simpleType>
```

## Members

|Member|Description|
|----------|---------------|
|Ascending|The results will be sorted ascending.|
|Descending|The results will be sorted descending.|

## Requirements
[!INCLUDE[reqbilling](../billing-api/includes/reqbilling.md)]
## See Also
[SearchInsertionOrders](../billing-api/searchinsertionorders-service-operation.md)

