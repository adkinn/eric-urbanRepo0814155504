---
title: "EntityScope Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59c34441-b7a5-41d4-b250-410077c2be7a
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# EntityScope Value Set
Defines values that you can use to determine whether the remarketing list can only be associated with ad groups within one specified account, or can be associated with any ad groups across all of the customer's accounts.

## Syntax

```xml
<xs:simpleType name="EntityScope">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Account" />
    <xs:enumeration value="Customer" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Account|The remarketing list can only be associated with ad groups within one specified account.|
|Customer|The remarketing list can be associated with any ad groups across all of the customer's accounts.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[RemarketingList](../campaign-api/remarketinglist-data-object.md)  
