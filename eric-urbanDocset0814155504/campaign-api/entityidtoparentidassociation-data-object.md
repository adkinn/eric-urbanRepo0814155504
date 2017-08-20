---
title: "EntityIdToParentIdAssociation Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5355f77f-08f1-4f28-a7db-55ba8f28e4bb
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# EntityIdToParentIdAssociation Data Object
Defines an object that contains the unique system identifier of an entity such as ad or keyword, and the identifier of its parent. An ad group is the parent of an ad or keyword.

## Syntax

```xml
\<xs:complexType name="EntityIdToParentIdAssociation">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="EntityId" type="xs:long"/>
    \<xs:element minOccurs="0" name="ParentId" type="xs:long"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*EntityId*|The system-generated unique identifier of an entity such as ad or keyword.|*long*|
|*ParentId*|The identifier of the entity's parent. An ad group is the parent of an ad or keyword.|*long*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[GetEditorialReasonsByIds](../campaign-api/geteditorialreasonsbyids-service-operation.md)

