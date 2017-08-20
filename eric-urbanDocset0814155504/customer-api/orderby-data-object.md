---
title: "OrderBy Data Object"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 49ee451c-dfb1-4910-befb-76484c440758
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# OrderBy Data Object
Defines an order for the list of entities returned using one of the search operations, for example [SearchAccounts](../customer-api/searchaccounts-service-operation.md), [SearchClientLinks](../customer-api/searchclientlinks-service-operation.md), or [SearchCustomers](../customer-api/searchcustomers-service-operation.md).

## Syntax

```xml
\<xs:complexType name="OrderBy">
  \<xs:sequence>
    \<xs:element name="Field" type="tns:OrderByField" minOccurs="0"	 />
    \<xs:element name="Order" type="tns:SortOrder" minOccurs="0" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Field*|Determines the field to order the results. For example order the results by *Id*.|[OrderByField](../customer-api/orderbyfield-value-set.md)|
|*Order*|Determines whether the results are ascending or descending.|[SortOrder](../customer-api/sortorder-value-set.md)|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[SearchAccounts](../customer-api/searchaccounts-service-operation.md)  
[SearchClientLinks](../customer-api/searchclientlinks-service-operation.md)  
[SearchCustomers](../customer-api/searchcustomers-service-operation.md)  

