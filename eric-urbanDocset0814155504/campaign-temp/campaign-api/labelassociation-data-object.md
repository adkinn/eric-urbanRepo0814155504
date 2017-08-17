---
title: "LabelAssociation Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ca41d3cf-7181-47fe-ae2c-d981c0944ff7
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
---
# LabelAssociation Data Object
Defines the relationship between a label and campaign, ad group, ad, or keyword entity.

## Syntax

```xml
\<xs:complexType name="LabelAssociation">
  \<xs:sequence>
    \<xs:element name="EntityId" type="xs:long" />
    \<xs:element name="LabelId" type="xs:long" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*EntityId*|The identifier of an entity associated with the label.<br/><br/>Supported entity types for labels are campaign, ad group, ad, and keyword. The entity type is specified in the request message of each [DeleteLabelAssociations](../campaign-api/deletelabelassociations-service-operation.md), [GetLabelAssociationsByEntityIds](../campaign-api/getlabelassociationsbyentityids-service-operation.md), [GetLabelAssociationsByLabelIds](../campaign-api/getlabelassociationsbylabelids-service-operation.md), and [SetLabelAssociations](../campaign-api/setlabelassociations-service-operation.md) operation.<br/><br/>Each entity can be associated with a maximum of 50 labels. For example *Campaign A* can be associated with up to 50 labels.<br/><br/>**Set:** Required<br/>**Delete:** Required|*long*|
|*LabelId*|The identifier of the label.<br/><br/>**Set:** Required<br/>**Delete:** Required|*long*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[Label](../campaign-api/label-data-object.md)  
[DeleteLabelAssociations](../campaign-api/deletelabelassociations-service-operation.md)  
[GetLabelAssociationsByEntityIds](../campaign-api/getlabelassociationsbyentityids-service-operation.md)  
[GetLabelAssociationsByLabelIds](../campaign-api/getlabelassociationsbylabelids-service-operation.md)  
[SetLabelAssociations](../campaign-api/setlabelassociations-service-operation.md)  