---
title: "AdExtensionIdToEntityIdAssociation Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bcaca88d-880b-4f99-82cf-7437592a9522
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdExtensionIdToEntityIdAssociation Data Object
Defines an object that associates an ad extension to a supported entity, for example ad group or campaign.

## Syntax

```xml
<xs:complexType name="AdExtensionIdToEntityIdAssociation">
  <xs:sequence>
    <xs:element name="AdExtensionId" type="xs:long" />
    <xs:element name="EntityId" type="xs:long" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdExtensionId*|The system-generated identifier of the ad extension.|*long*|
|*EntityId*|The identifier of an entity associated with the ad extension.|*long*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[DeleteAdExtensionsAssociations](../campaign-api/deleteadextensionsassociations-service-operation.md)  
[GetAdExtensionsEditorialReasons](../campaign-api/getadextensionseditorialreasons-service-operation.md)  
[SetAdExtensionsAssociations](../campaign-api/setadextensionsassociations-service-operation.md)  

