---
title: "Predicate Data Object"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ffe7c463-7fbb-4611-926e-f126a1dc8bfd
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Predicate Data Object
Defines a predicate for the list of entities requested using one of the search operations, for example [SearchAccounts](../customer-api/searchaccounts-service-operation.md), [SearchClientLinks](../customer-api/searchclientlinks-service-operation.md), or [SearchCustomers](../customer-api/searchcustomers-service-operation.md).

## Syntax

```xml
\<xs:complexType name="Predicate">
  \<xs:sequence>
    \<xs:element name="Field" type="xs:string" nillable="true" minOccurs="0" />
    \<xs:element name="Operator" type="tns:PredicateOperator" minOccurs="0"/>
    \<xs:element name="Value" type="xs:string" nillable="true" minOccurs="0"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Field*|The name of the element for  the object you are searching.<br /><br />For possible values, see the Predicates element of one of the search operations, for example [SearchAccounts](../customer-api/searchaccounts-service-operation.md), [SearchClientLinks](../customer-api/searchclientlinks-service-operation.md), or [SearchCustomers](../customer-api/searchcustomers-service-operation.md).|*string*|
|*Operator*|Defines the relationship between the field and the value.|[PredicateOperator](../customer-api/predicateoperator-value-set.md)|
|*Value*|The string to search in the specified field.<br /><br />**Note:** The length of this string must be four or greater, unless the field is set to MarketCountry or MarketLanguage.|*string*|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[SearchAccounts](../customer-api/searchaccounts-service-operation.md)
[SearchClientLinks](../customer-api/searchclientlinks-service-operation.md)
[SearchCustomers](../customer-api/searchcustomers-service-operation.md)

