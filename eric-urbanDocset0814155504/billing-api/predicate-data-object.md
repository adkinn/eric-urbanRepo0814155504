---
title: "Predicate Data Object"
ms.custom: ""
ms.date: "05/27/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 92dae445-1f1d-458b-8772-cb9bd9e6613a
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Predicate Data Object
Defines a predicate for the list of insertion orders returned using the [SearchInsertionOrders](../billing-api/searchinsertionorders-service-operation.md) operation.

## Syntax

```xml
<xs:complexType name="Predicate">
  <xs:sequence>
    <xs:element name="Field" type="xs:string" nillable="true" minOccurs="0" />
    <xs:element name="Operator" type="tns:PredicateOperator" minOccurs="0"/>
    <xs:element name="Value" type="xs:string" nillable="true" minOccurs="0"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Field*|The name of the element for  the object you are searching.<br /><br />For possible values, see the [SearchInsertionOrders](../billing-api/searchinsertionorders-service-operation.md) operation.|*string*|
|*Operator*|Defines the relationship between the field and the value.|[PredicateOperator](../billing-api/predicateoperator-value-set.md)|
|*Value*|The string to search in the specified field.<br /><br />**Note**: The length of this string must be four or greater, unless the field is set to MarketCountry or MarketLanguage.|*string*|

## Requirements
[!INCLUDE[reqbilling](../billing-api/includes/reqbilling.md)]
## See Also
[SearchInsertionOrders](../billing-api/searchinsertionorders-service-operation.md)

