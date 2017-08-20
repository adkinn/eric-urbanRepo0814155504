---
title: "Paging Data Object"
ms.custom: ""
ms.date: "06/21/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 16f85a50-168e-457f-a5cf-99a7eefb49de
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Paging Data Object
Defines a paging object for the list of entities returned using one of the search operations, for example [SearchAccounts](../customer-api/searchaccounts-service-operation.md), [SearchClientLinks](../customer-api/searchclientlinks-service-operation.md), or [SearchCustomers](../customer-api/searchcustomers-service-operation.md).

## Syntax

```xml
\<xs:complexType name="Paging">
  \<xs:sequence>
    \<xs:element name="Index" type="xs:int" minOccurs="0"/>
    \<xs:element name="Size" type="xs:int" minOccurs="0"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Index*|The zero-based results page index. For example to request the first page of results, set this value to 0 (zero).|*int*|
|*Size*|The page size and the number of results to return in the specified page. The maximum size is 1,000.|*int*|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[SearchAccounts](../customer-api/searchaccounts-service-operation.md)  
[SearchClientLinks](../customer-api/searchclientlinks-service-operation.md)  
[SearchCustomers](../customer-api/searchcustomers-service-operation.md)  

