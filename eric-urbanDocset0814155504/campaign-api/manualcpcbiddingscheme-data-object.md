---
title: "ManualCpcBiddingScheme Data Object"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5c5abaf-12dd-40c1-b60d-a1abee3157fd
caps.latest.revision: 14
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ManualCpcBiddingScheme Data Object
Defines an object that represents the manual CPC bid strategy type. 

This is the default bid strategy type for your campaigns. Use the manual CPC bid strategy type if you will set your ad group and keyword bids, and Bing Ads will use these bids every time. 

> [!TIP]
> You can set your campaign?s bid strategy to [EnhancedCpcBiddingScheme](../campaign-api/enhancedcpcbiddingscheme-data-object.md), [MaxClicksBiddingScheme](../campaign-api/maxclicksbiddingscheme-data-object.md), [MaxConversionsBiddingScheme](../campaign-api/maxconversionsbiddingscheme-data-object.md), or [TargetCpaBiddingScheme](../campaign-api/targetcpabiddingscheme-data-object.md) and then, at any time, set an individual ad group?s or keyword?s bid strategy to Manual CPC.

## Syntax

```xml
<xs:complexType name="ManualCpcBiddingScheme">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:BiddingScheme">
      <xs:sequence/>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *ManualCpcBiddingScheme* object inherits elements from the [BiddingScheme](../campaign-api/biddingscheme-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

## <a name="InheritedElements"></a>Inherited Elements
The *ManualCpcBiddingScheme* object inherits the following element from the [BiddingScheme](../campaign-api/biddingscheme-data-object.md) object. 

> [!NOTE]
> The description below is specific to the manual CPC bidding scheme, and might not apply to other objects that inherit the same element from the [BiddingScheme](../campaign-api/biddingscheme-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of the bidding scheme. This value is *ManualCpcBiddingScheme* when you retrieve a manual CPC bidding scheme. For more information about bidding scheme types, see the [BiddingScheme Data Object Remarks](../campaign-api/biddingscheme-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdGroup](../campaign-api/adgroup-data-object.md)  
[Campaign](../campaign-api/campaign-data-object.md)  
[Keyword](../campaign-api/keyword-data-object.md)  
