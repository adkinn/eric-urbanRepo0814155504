---
title: "AdExtensionAssociationCollection Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76f97c73-df17-4cde-b1d8-976af98efcc2
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdExtensionAssociationCollection Data Object
Defines an array of objects that associate an ad extension and its editorial status to an account, campaign, or ad group.

## Syntax

```xml
\<xs:complexType name="AdExtensionAssociationCollection">
  \<xs:sequence>
    \<xs:element name="AdExtensionAssociations" nillable="true" type="tns:ArrayOfAdExtensionAssociation" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdExtensionAssociations*|An array of objects that associate an ad extension and its editorial status to an account, campaign, or ad group.<br/><br/>**Add:** Required<br/>**Update:** Required|[AdExtensionAssociation](../campaign-api/adextensionassociation-data-object.md) array|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[GetAdExtensionsAssociations](../campaign-api/getadextensionsassociations-service-operation.md)

