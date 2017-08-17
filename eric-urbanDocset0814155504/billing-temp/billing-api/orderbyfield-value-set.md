---
title: "OrderByField Value Set"
ms.custom: ""
ms.date: "05/27/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 53ead6b1-a60e-4412-ba58-8ba68e869d17
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# OrderByField Value Set
Defines the field order of insertion orders returned using [SearchInsertionOrders](../billing-api/searchinsertionorders-service-operation.md).

## Syntax

```xml
\<xs:simpleType name="OrderByField">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Id" />
    \<xs:enumeration value="Name" />
    \<xs:enumeration value="Number" />
    \<xs:enumeration value="LifeCycleStatus" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Id|The order is determined by a predicate identifier.|
|LifeCycleStatus|The order is determined by a predicate life cycle status.<br /><br />**Note**: This value is reserved for future use.|
|Name|The order is determined by a predicate name.|
|Number|The order is determined by a predicate number.<br /><br />**Note**: This value is reserved for future use.|

## Requirements
[!INCLUDE[reqbilling](../billing-api/includes/reqbilling.md)]
## See Also
[OrderBy](../billing-api/orderby-data-object.md)  
[Predicate](../billing-api/predicate-data-object.md)  
[SearchInsertionOrders](../billing-api/searchinsertionorders-service-operation.md)  

