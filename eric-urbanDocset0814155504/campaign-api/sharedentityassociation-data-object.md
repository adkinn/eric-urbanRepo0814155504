---
title: "SharedEntityAssociation Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 23b87d59-5ceb-477b-a231-4d6261dd9b95
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SharedEntityAssociation Data Object
Defines an object that contains association information for a campaign and shared entity such as a negative keyword list.

## Syntax

```xml
<xs:complexType name="SharedEntityAssociation">
  <xs:sequence>
    <xs:element name="EntityId" type="xs:long" />
    <xs:element name="EntityType" type="xs:string" nillable="true"/>
    <xs:element name="SharedEntityId" type="xs:long" />
    <xs:element name="SharedEntityType" type="xs:string" nillable="true"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*EntityId*|The system-generated identifier of the campaign that is associated with the shared entity.|*long*|
|*EntityType*|The type of entity.<br /><br />Currently the only supported value is Campaign.|*string*|
|*SharedEntityId*|The system-generated identifier of the shared entity.|*long*|
|*SharedEntityType*|The type of the shared entity.<br /><br />Currently the only supported value is NegativeKeywordList.|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[DeleteSharedEntityAssociations](../campaign-api/deletesharedentityassociations-service-operation.md)  
[GetSharedEntityAssociationsByEntityIds](../campaign-api/getsharedentityassociationsbyentityids-service-operation.md)  
[GetSharedEntityAssociationsBySharedEntityIds](../campaign-api/getsharedentityassociationsbysharedentityids-service-operation.md)  
[SetSharedEntityAssociations](../campaign-api/setsharedentityassociations-service-operation.md)  

