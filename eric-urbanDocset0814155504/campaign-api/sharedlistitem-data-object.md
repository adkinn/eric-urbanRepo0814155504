---
title: "SharedListItem Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd186566-d05b-4e17-a522-5d9b55cb355b
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SharedListItem Data Object
Defines the base class of a shared list item.

Do not try to instantiate a *SharedListItem*. You can create the following object that derives from it.
-   [NegativeKeyword](../campaign-api/negativekeyword-data-object.md)

## Syntax

```xml
<xs:complexType name="SharedListItem">
  <xs:sequence>
    <xs:element minOccurs="0" name="ForwardCompatibilityMap" nillable="true" type="q52:ArrayOfKeyValuePairOfstringstring" xmlns:q52="http://schemas.datacontract.org/2004/07/System.Collections.Generic" />
    <xs:element name="Type" nillable="true" type="xs:string" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />**Note:** Forward compatibility changes will be noted here in future releases. There are currently no forward compatibility changes for the *SharedListItem* object.|*KeyValuePairOfstringstring* array|
|*Type*|The type of the shared list item. For more information about shared list item types, see [Remarks](#remarks).<br /><br />**Add:** Read-only<br />**Update:** Read-only|*string*|

## <a name="remarks"></a>Remarks
For Java and the .NET languages, do not set the *Type* element because the value is determined by the object instance.

If you generate the SOAP manually, use the *Type* attribute of the `<SharedListItem>` node as shown in the following example, to specify whether the shared list item is a negative keyword.

```xml
<SharedListItem i:type="-- specify derived type here with the appropriate prefix --">
  <ForwardCompatibilityMap xmlns:e6="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
    <e6:KeyValuePairOfstringstring>
      <e6:key i:nil="false"></e6:key>
      <e6:value i:nil="false"></e6:value>
    </e6:KeyValuePairOfstringstring>
  </ForwardCompatibilityMap>
  <Type i:nil="false"></Type>
  <!--Keep these fields if you set the i:type attribute to NegativeKeyword-->
  <Id i:nil="false"></Id>
  <MatchType></MatchType>
  <Text i:nil="false"></Text>
</SharedListItem>
```

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddListItemsToSharedList](../campaign-api/addlistitemstosharedlist-service-operation.md)  
[DeleteListItemsFromSharedList](../campaign-api/deletelistitemsfromsharedlist-service-operation.md)  
[GetListItemsBySharedList](../campaign-api/getlistitemsbysharedlist-service-operation.md)  

