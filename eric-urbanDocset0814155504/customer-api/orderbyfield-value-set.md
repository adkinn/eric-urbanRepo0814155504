---
title: "OrderByField Value Set"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 869926ee-e09a-4312-9127-228ec58ca16f
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# OrderByField Value Set
Defines the field order of entities returned using one of the search operations, for example [SearchAccounts](../customer-api/searchaccounts-service-operation.md), [SearchClientLinks](../customer-api/searchclientlinks-service-operation.md), or [SearchCustomers](../customer-api/searchcustomers-service-operation.md).

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
|LifeCycleStatus|The order is determined by a predicate life cycle status.|
|Name|The order is determined by a predicate name.|
|Number|The order is determined by a predicate number.|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[OrderBy](../customer-api/orderby-data-object.md)  
[Predicate](../customer-api/predicate-data-object.md)  
[SearchAccounts](../customer-api/searchaccounts-service-operation.md)  
[SearchClientLinks](../customer-api/searchclientlinks-service-operation.md)  
[SearchCustomers](../customer-api/searchcustomers-service-operation.md)  

