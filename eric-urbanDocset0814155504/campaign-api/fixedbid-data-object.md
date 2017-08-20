---
title: "FixedBid Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bf90a6ef-5be2-438f-a348-d8ba036529ff
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# FixedBid Data Object
Defines the fixed bid to use in the auction.

## Syntax

```xml
\<xs:complexType name="FixedBid">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:CriterionBid">
      \<xs:sequence>
        \<xs:element minOccurs="0" name="Amount" nillable="true" type="xs:double" />
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
The *FixedBid* object derives from the [CriterionBid](../campaign-api/criterionbid-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Amount*|The bid value. For details about the valid bid range for your market, see [Currencies](http://msdn.microsoft.com/library/bing-ads-currencies.aspx).<br/><br/>**Add:** Required<br/>**Update:** Optional|*double*|

## <a name="InheritedElements"></a>Inherited Elements
The *FixedBid* object derives from the [CriterionBid](../campaign-api/criterionbid-data-object.md) object, and inherits the following elements. 

> [!NOTE]
> The descriptions below are specific to fixed bids, and might not apply to other objects that inherit the same elements from the [CriterionBid](../campaign-api/criterionbid-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of the criterion bid. This value is *FixedBid* when you retrieve a fixed bid criterion. For more information about criterion types, see the [CriterionBid Data Object Remarks](../campaign-api/criterionbid-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md)

