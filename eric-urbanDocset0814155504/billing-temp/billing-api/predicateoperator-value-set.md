---
title: "PredicateOperator Value Set"
ms.custom: ""
ms.date: "05/27/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec6918e9-17a8-467d-aa2d-e325ce86551b
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# PredicateOperator Value Set
Defines the condition of results for insertion orders returned using [SearchInsertionOrders](../billing-api/searchinsertionorders-service-operation.md).

## Syntax

```xml
\<xs:simpleType name="PredicateOperator">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Equals" />
    \<xs:enumeration value="NotEquals" />
    \<xs:enumeration value="Contains" />
    \<xs:enumeration value="In" />
    \<xs:enumeration value="GreaterThanEquals" />
    \<xs:enumeration value="LessThanEquals" />
    \<xs:enumeration value="NotContains" />
    \<xs:enumeration value="StartsWith" />
  \</xs:restriction>
\</xs:simpleType>
```

## Members

|Member|Description|
|----------|---------------|
|Contains|The field must contain the specified value.|
|Equals|The field must equal the specified value.|
|GreaterThanEquals|The field must be greater than or equal to the specified value.|
|In|The field must equal one of the specified comma separated values.<br /><br />**Note**: The maximum number of comma separated values that can be specified is 10.|
|LessThanEquals|The field must be less than or equal to the specified value.|
|NotContains|The field must not contain the specified value.<br /><br />**Note**: Not currently supported.|
|NotEquals|The field must not equal the specified value.<br /><br />**Note**: Not currently supported.|
|StartsWith|The field must start with the specified value.<br /><br />**Note**: Not currently supported.|

## Requirements
[!INCLUDE[reqbilling](../billing-api/includes/reqbilling.md)]
## See Also
[SearchInsertionOrders](../billing-api/searchinsertionorders-service-operation.md)

