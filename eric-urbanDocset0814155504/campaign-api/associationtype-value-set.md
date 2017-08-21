---
title: "AssociationType Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 242f5172-0f17-46ed-a3b9-3bcc2a9d8a27
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AssociationType Value Set
Defines the entity types that can be associated with an ad extension.

## Syntax

```xml
<xs:simpleType name="AssociationType">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Campaign" />
    <xs:enumeration value="AdGroup" />
    <xs:enumeration value="Account" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Account|Refers to ad extension associations with accounts.<br /><br />**Note:** Call ad extensions cannot be associated with an account.|
|AdGroup|Refers to ad extension associations with ad groups.<br /><br />**Note:** Call and Location ad extensions cannot be associated with an ad group.|
|Campaign|Refers to ad extension associations with campaigns.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdExtensionAssociation](../campaign-api/adextensionassociation-data-object.md)  
[DeleteAdExtensionsAssociations](../campaign-api/deleteadextensionsassociations-service-operation.md)  
[GetAdExtensionIdsByAccountId](../campaign-api/getadextensionidsbyaccountid-service-operation.md)  
[GetAdExtensionsAssociations](../campaign-api/getadextensionsassociations-service-operation.md)  
[GetAdExtensionsEditorialReasons](../campaign-api/getadextensionseditorialreasons-service-operation.md)  
[SetAdExtensionsAssociations](../campaign-api/setadextensionsassociations-service-operation.md)  

