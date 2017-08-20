---
title: "CustomerLifeCycleStatus Value Set"
ms.custom: ""
ms.date: "08/01/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99a43a87-b401-437d-a7a0-0e819e16f859
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CustomerLifeCycleStatus Value Set
Defines the possible status values of a customer.

## Syntax

```xml
\<xs:simpleType name="CustomerLifeCycleStatus">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Active" />
    \<xs:enumeration value="Inactive" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Active|The customer is active.|
|Inactive|The customer is inactive, which means that the customer was deleted.|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[Customer](../customer-api/customer-data-object.md)

