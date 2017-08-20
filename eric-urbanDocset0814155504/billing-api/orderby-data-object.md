---
title: "OrderBy Data Object"
ms.custom: ""
ms.date: "05/27/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f3457889-88c4-42ab-a0bb-20cd56274ba6
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# OrderBy Data Object
Defines an order for the list of insertion orders returned using the [SearchInsertionOrders](../billing-api/searchinsertionorders-service-operation.md) operation.

## Syntax

```xml
<xs:complexType name="OrderBy">
  <xs:sequence>
    <xs:element name="Field" type="tns:OrderByField" minOccurs="0"	 />
    <xs:element name="Order" type="tns:SortOrder" minOccurs="0" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Field*|Determines the field to order the results. For example order the results by *Id*.|[OrderByField](../billing-api/orderbyfield-value-set.md)|
|*Order*|Determines whether the results are ascending or descending.|[SortOrder](../billing-api/sortorder-value-set.md)|

## Requirements
[!INCLUDE[reqbilling](../billing-api/includes/reqbilling.md)]
## See Also
[SearchInsertionOrders](../billing-api/searchinsertionorders-service-operation.md)

