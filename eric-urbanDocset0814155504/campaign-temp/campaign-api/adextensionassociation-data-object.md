---
title: "AdExtensionAssociation Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 60233ced-a506-459f-aba2-a76d294697f2
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdExtensionAssociation Data Object
Defines the relationship and editorial status of an ad extension with an account, campaign, or ad group.

## Syntax

```xml
\<xs:complexType name="AdExtensionAssociation">
  \<xs:sequence>
    \<xs:element name="AdExtension" nillable="true" type="tns:AdExtension" />
    \<xs:element name="AssociationType" nillable="true" type="tns:AssociationType" />
    \<xs:element minOccurs="0" name="EditorialStatus" nillable="true" type="tns:AdExtensionEditorialStatus" />
    \<xs:element name="EntityId" type="xs:long" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdExtension*|The ad extension associated with a supported entity.<br/><br/>**Add:** Required<br/>**Update:** Required|[AdExtension](../campaign-api/adextension-data-object.md)|
|*AssociationType*|The type of entity associated with the ad extension.<br/><br/>**Add:** Required<br/>**Update:** Required|[AssociationType](../campaign-api/associationtype-value-set.md)|
|*EditorialStatus*|The editorial status of the ad extension.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[AdExtensionEditorialStatus](../campaign-api/adextensioneditorialstatus-value-set.md)|
|*EntityId*|The identifier of an entity associated with the ad extension.<br/><br/>**Add:** Required<br/>**Update:** Required|*long*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdExtensionAssociationCollection](../campaign-api/adextensionassociationcollection-data-object.md)  

