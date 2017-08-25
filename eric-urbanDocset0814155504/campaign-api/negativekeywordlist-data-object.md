---
title: "NegativeKeywordList Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dd89feac-5dfe-43ed-b6a3-970e3bfc31c7
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# NegativeKeywordList Data Object
Defines a negative keyword list. You can add negative keywords to a negative keyword list and associate the list with one or more campaigns.

## Syntax

```xml
<xs:complexType name="NegativeKeywordList">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:SharedList">
      <xs:sequence />
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *NegativeKeywordList* object inherits elements from the [SharedList](../campaign-api/sharedlist-data-object.md) and [SharedEntity](../campaign-api/sharedentity-data-object.md) objects. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

## <a name="InheritedElements"></a>Inherited Elements
### <a name="InheritedElementsSharedList"></a>Inherited Elements from SharedList
The *NegativeKeywordList* inherits the following element from the [SharedList](../campaign-api/sharedlist-data-object.md) object. 

> [!NOTE]
> The description below is specific to negative keywords, and might not apply to other objects that inherit the same element from the [SharedList](../campaign-api/sharedlist-data-object.md)  object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ItemCount*|The number of [SharedListItem](../campaign-api/sharedlistitem-data-object.md) objects that are added to this shared list.<br /><br />**Add:** Read-only<br />**Update:** Read-only|*int*|

### <a name="InheritedElementsSharedEntity"></a>Inherited Elements from SharedEntity
The *NegativeKeywordList* inherits the following elements from the [SharedEntity](../campaign-api/sharedentity-data-object.md) object. 

> [!NOTE]
> The description below is specific to negative keywords, and might not apply to other objects that inherit the same elements from the [SharedEntity](../campaign-api/sharedentity-data-object.md)  object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AssociationCount*|The number of active associations between this object and an entity such as a campaign.<br /><br />For a [NegativeKeywordList](../campaign-api/negativekeywordlist-data-object.md), the maximum association count is 20.<br /><br />**Add:** Read-only<br />**Update:** Read-only|*int*|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />**Note:** Forward compatibility changes will be noted here in future releases. There are currently no forward compatibility changes for the *SharedEntity* object.|*KeyValuePairOfstringstring* array|
|*Id*|The unique Bing Ads identifier of the shared entity.<br /><br />**Add:** Read-only<br />**Update:** Required|*long*|
|*Name*|The name of the shared entity.<br /><br />For a [NegativeKeywordList](../campaign-api/negativekeywordlist-data-object.md), the maximum length is 255.<br /><br />**Add:** Optional<br />**Update:** Optional|*string*|
|*Type*|The type of the shared entity. For more information about shared entity types, see [SharedEntity Data Object Remarks](../campaign-api/sharedentity-data-object.md#remarks).<br /><br />**Add:** Read-only<br />**Update:** Read-only|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddListItemsToSharedList](../campaign-api/addlistitemstosharedlist-service-operation.md)  
[AddNegativeKeywordsToEntities](../campaign-api/addnegativekeywordstoentities-service-operation.md)  
[AddSharedEntity](../campaign-api/addsharedentity-service-operation.md)  
[DeleteListItemsFromSharedList](../campaign-api/deletelistitemsfromsharedlist-service-operation.md)  
[DeleteNegativeKeywordsFromEntities](../campaign-api/deletenegativekeywordsfromentities-service-operation.md)  
[DeleteSharedEntities](../campaign-api/deletesharedentities-service-operation.md)  
[DeleteSharedEntityAssociations](../campaign-api/deletesharedentityassociations-service-operation.md)  
[GetListItemsBySharedList](../campaign-api/getlistitemsbysharedlist-service-operation.md)  
[GetNegativeKeywordsByEntityIds](../campaign-api/getnegativekeywordsbyentityids-service-operation.md)  
[GetSharedEntitiesByAccountId](../campaign-api/getsharedentitiesbyaccountid-service-operation.md)  
[GetSharedEntityAssociationsByEntityIds](../campaign-api/getsharedentityassociationsbyentityids-service-operation.md)  
[GetSharedEntityAssociationsBySharedEntityIds](../campaign-api/getsharedentityassociationsbysharedentityids-service-operation.md)  
[SetSharedEntityAssociations](../campaign-api/setsharedentityassociations-service-operation.md)  
[UpdateSharedEntities](../campaign-api/updatesharedentities-service-operation.md)  
[NegativeKeyword](../campaign-api/negativekeyword-data-object.md)  

