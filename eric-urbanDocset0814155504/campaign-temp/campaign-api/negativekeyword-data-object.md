---
title: "NegativeKeyword Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e091c376-17b2-4196-b0ed-22feee167be0
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# NegativeKeyword Data Object
Defines a negative keyword with match type. A negative keyword can be added and deleted, but cannot be updated.

You may choose to assign negative keywords to an individual campaign or ad group. An assigned set of negative keywords cannot be shared with other campaigns or ad groups.

Negative keywords can also be added and deleted from a shared negative keyword list. The negative keyword list can be shared or associated with multiple campaigns.

> [!NOTE]
> The same negative keyword and match type can be added to all campaigns, ad groups, and negative keyword lists if you choose. Each instance must be added and associated individually and would be assigned a unique negative keyword identifier.

For more information about managing negative keywords and negative keyword lists, please see the technical guide about [Negative Keywords](http://go.microsoft.com/fwlink/?LinkID=691225).

## Syntax

```xml
\<xs:complexType name="NegativeKeyword">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:SharedListItem">
      \<xs:sequence>
        \<xs:element minOccurs="0" name="Id" nillable="true" type="xs:long" />
        \<xs:element name="MatchType" type="tns:MatchType" />
        \<xs:element name="Text" nillable="true" type="xs:string" />
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
The *NegativeKeyword* object derives from the [SharedListItem](../campaign-api/sharedlistitem-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Id*|The unique Bing Ads identifier of the negative keyword.<br/><br/>**Add:** Read-only|*long*|
|*MatchType*|The type of match to compare the negative keyword and the user's search term.<br /><br />The supported values for a negative keyword are Exact and Phrase.<br/><br/>**Add:** Required|[MatchType](../campaign-api/matchtype-value-set.md)|
|*Text*|The negative keyword text. The text can contain a maximum of 100 characters.<br/><br/>**Add:** Required|*string*|

## <a name="InheritedElements"></a>Inherited Elements
The *NegativeKeyword* object derives from the [SharedListItem](../campaign-api/sharedlistitem-data-object.md) object, and inherits the following elements. 

> [!NOTE]
> The descriptions below are specific to negative keywords, and might not apply to other objects that inherit the same elements from the [SharedListItem](../campaign-api/sharedlistitem-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />**Note:** Forward compatibility changes will be noted here in future releases. There are currently no forward compatibility changes for the *SharedListItem* object.|*KeyValuePairOfstringstring* array|
|*Type*|The type of the shared list item.  This value is *NegativeKeyword* when you retrieve a negative keyword. For more information about shared list item types, see [SharedListItem Data Object Remarks](../campaign-api/sharedlistitem-data-object.md#remarks).<br/><br/>**Add:** Read-only|*string*|

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

