---
title: "SortOrder Value Set"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ef07faaf-08c2-442f-9c57-80cf232c6c6a
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SortOrder Value Set
Defines the ascending or descending sort order of results for one of the search operations, for example [SearchAccounts](../customer-api/searchaccounts-service-operation.md), [SearchClientLinks](../customer-api/searchclientlinks-service-operation.md), or [SearchCustomers](../customer-api/searchcustomers-service-operation.md).

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
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[SearchAccounts](../customer-api/searchaccounts-service-operation.md)  
[SearchClientLinks](../customer-api/searchclientlinks-service-operation.md)  
[SearchCustomers](../customer-api/searchcustomers-service-operation.md)  

