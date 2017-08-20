---
title: "ProductPartitionType Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5c25a3e5-61c5-4fd7-8836-b268ee07aedc
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ProductPartitionType Value Set
Defines the possible types of product partitions.

## Syntax

```xml
<xs:simpleType name="ProductPartitionType">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Subdivision" />
    <xs:enumeration value="Unit" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Subdivision|The [ProductPartition](../campaign-api/productpartition-data-object.md) is a product group subdivision. A subdivision is also referred to as a branch node in a tree.|
|Unit|The [ProductPartition](../campaign-api/productpartition-data-object.md) is a product group unit. A unit is also referred to as a leaf node in a tree.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[ApplyProductPartitionActions](../campaign-api/applyproductpartitionactions-service-operation.md)  
[ProductPartition](../campaign-api/productpartition-data-object.md)  
[AdGroupCriterionAction](../campaign-api/adgroupcriterionaction-data-object.md)  
[BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md)  

