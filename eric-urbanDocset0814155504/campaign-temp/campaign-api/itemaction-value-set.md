---
title: "ItemAction Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 96e0bdf5-02c0-49bd-aeae-0d7a7cc3fc44
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ItemAction Value Set
Defines the possible types of item actions, for example to add, delete, or update the product partition criterion.

## Syntax

```xml
\<xs:simpleType name="ItemAction">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Add" />
    \<xs:enumeration value="Delete" />
    \<xs:enumeration value="Update" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Add|The requested action is to add the item, for example add the [ProductPartition](../campaign-api/productpartition-data-object.md).|
|Delete|The requested action is to delete the item, for example delete the [ProductPartition](../campaign-api/productpartition-data-object.md).|
|Update|The requested action is to update the item, for example update the [ProductPartition](../campaign-api/productpartition-data-object.md).|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[ApplyProductPartitionActions](../campaign-api/applyproductpartitionactions-service-operation.md)  
[ProductPartition](../campaign-api/productpartition-data-object.md)  
[AdGroupCriterionAction](../campaign-api/adgroupcriterionaction-data-object.md)  

