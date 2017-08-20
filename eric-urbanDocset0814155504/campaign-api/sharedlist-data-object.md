---
title: "SharedList Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3685fcf4-3f49-4d48-abf1-7ad1638315b8
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SharedList Data Object
Defines the base class of a shared list.

Do not try to instantiate a *SharedList*. You can create the following object that derives from it.
-   [NegativeKeywordList](../campaign-api/negativekeywordlist-data-object.md)

## Syntax

```xml
\<xs:complexType name="SharedList">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:SharedEntity">
      \<xs:sequence>
        \<xs:element name="ItemCount" nillable="true" type="xs:int" />
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
The *SharedList* object derives from the *SharedEntity* object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ItemCount*|The number of [SharedListItem](../campaign-api/sharedlistitem-data-object.md) objects that are added to this shared list.<br /><br />**Add:** Read-only<br />**Update:** Read-only|*int*|

## <a name="InheritedElements"></a>Inherited Elements
The *SharedList* derives from the [SharedEntity](../campaign-api/sharedentity-data-object.md) object, and inherits the following elements. 

> [!NOTE]
> The description below is specific to shared lists, and might not apply to other objects that inherit the same elements from the [SharedEntity](../campaign-api/sharedentity-data-object.md)  object.

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
[DeleteListItemsFromSharedList](../campaign-api/deletelistitemsfromsharedlist-service-operation.md)  
[GetListItemsBySharedList](../campaign-api/getlistitemsbysharedlist-service-operation.md)  

