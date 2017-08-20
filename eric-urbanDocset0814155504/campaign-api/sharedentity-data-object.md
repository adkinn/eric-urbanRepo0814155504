---
title: "SharedEntity Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2020e797-6051-4580-9788-c88a54400abf
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SharedEntity Data Object
Defines the base class of a shared entity.

Do not try to instantiate a *SharedEntity*. You can create the following object that derives from it.
-   [NegativeKeywordList](../campaign-api/negativekeywordlist-data-object.md)  

A [NegativeKeywordList](../campaign-api/negativekeywordlist-data-object.md) is derived from the [SharedList](../campaign-api/sharedlist-data-object.md), which derives from the [SharedEntity](../campaign-api/sharedentity-data-object.md) object.

## Syntax

```xml
\<xs:complexType name="SharedEntity">
  \<xs:sequence>
    \<xs:element name="AssociationCount" nillable="true" type="xs:int" />
    \<xs:element minOccurs="0" name="ForwardCompatibilityMap" nillable="true" type="q55:ArrayOfKeyValuePairOfstringstring" xmlns:q55="http://schemas.datacontract.org/2004/07/System.Collections.Generic" />
    \<xs:element minOccurs="0" name="Id" nillable="true" type="xs:long" />
    \<xs:element name="Name" nillable="true" type="xs:string" />
    \<xs:element name="Type" nillable="true" type="xs:string" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AssociationCount*|The number of active associations between this object and an entity such as a campaign.|*int*|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />**Note:** Forward compatibility changes will be noted here in future releases. There are currently no forward compatibility changes for the *SharedEntity* object.|*KeyValuePairOfstringstring* array|
|*Id*|The unique Bing Ads identifier of the shared entity.|*long*|
|*Name*|The name of the shared entity.|*string*|
|*Type*|The type of the shared entity. For more information about shared entity types, see [SharedEntity Data Object Remarks](../campaign-api/sharedentity-data-object.md#remarks).|*string*|

## <a name="remarks"></a>Remarks
For Java and the .NET languages, do not set the *Type* element because the value is determined by the object instance.

If you generate the SOAP manually, use the *type* attribute of the `<SharedEntity>` node as shown in the following example, to specify whether the shared entity is a negative keyword list.

```xml
\<SharedEntity i:type="NegativeKeywordList" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  \<AssociationCount i:nil="true" />
  \<ForwardCompatibilityMap i:nil="true" xmlns:a="http://schemas.datacontract.org/2004/07/System.Collections.Generic" />
  \<Id i:nil="true" />
  <Name>My Negative Keyword List</Name>
  \<ItemCount i:nil="true" />
</SharedEntity>
```

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddSharedEntity](../campaign-api/addsharedentity-service-operation.md)  
[DeleteSharedEntities](../campaign-api/deletesharedentities-service-operation.md)  
[DeleteSharedEntityAssociations](../campaign-api/deletesharedentityassociations-service-operation.md)  
[GetSharedEntitiesByAccountId](../campaign-api/getsharedentitiesbyaccountid-service-operation.md)  
[GetSharedEntityAssociationsByEntityIds](../campaign-api/getsharedentityassociationsbyentityids-service-operation.md)  
[GetSharedEntityAssociationsBySharedEntityIds](../campaign-api/getsharedentityassociationsbysharedentityids-service-operation.md)  
[SetSharedEntityAssociations](../campaign-api/setsharedentityassociations-service-operation.md)  
[UpdateSharedEntities](../campaign-api/updatesharedentities-service-operation.md)  

