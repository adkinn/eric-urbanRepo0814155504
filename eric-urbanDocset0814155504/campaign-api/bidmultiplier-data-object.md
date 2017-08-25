---
title: "BidMultiplier Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6db465b4-80ab-4734-9ee0-78b04c72fe7a
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
---
# BidMultiplier Data Object
Defines the multiplier by which to adjust your base bid for the corresponding criterion.

## Syntax

```xml
<xs:complexType name="BidMultiplier">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:CriterionBid">
      <xs:sequence>
        <xs:element minOccurs="0" name="Multiplier" nillable="true" type="xs:double" />
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *BidMultiplier* object derives from the [CriterionBid](../campaign-api/criterionbid-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Multiplier*|The percentage amount that you want to adjust the bid for the corresponding criterion. <br/><br/>For most criterion types the valid bid multiplier range is -90.00 through 900.00. For exceptions, see [DeviceCriterion Usage](#devicecriterion) and [LocationIntentCriterion Usage](#locationintentcriterion) below.<br/><br/>**Add:** Required<br/>**Update:** Required|*double*|

## <a name="InheritedElements"></a>Inherited Elements
The *BidMultiplier* object derives from the [CriterionBid](../campaign-api/criterionbid-data-object.md) object, and inherits the following elements. 

> [!NOTE]
> The descriptions below are specific to bid multipliers, and might not apply to other objects that inherit the same elements from the [CriterionBid](../campaign-api/criterionbid-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of the criterion bid. This value is *BidMultiplier* when you retrieve a bid multiplier. For more information about criterion types, see the [CriterionBid Data Object Remarks](../campaign-api/criterionbid-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|

## <a name="devicecriterion"></a>DeviceCriterion Usage
If the *Criterion* property of the [BiddableCampaignCriterion](../campaign-api/biddablecampaigncriterion-data-object.md) or [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) object is a [DeviceCriterion](../campaign-api/devicecriterion-data-object.md), please note the following usage of *BidMultiplier* properties.

### <a name="devicecriterion_multiplier"></a>Multiplier
Supported values are -100 (negative one hundred) through positive 900 (nine hundred) percent. Setting the bid adjustment to -100 percent will result in the exclusion of the corresponding *DeviceName* for the [DeviceCriterion](../campaign-api/devicecriterion-data-object.md). 

## <a name="locationintentcriterion"></a>LocationIntentCriterion Usage
If the *Criterion* property of the [BiddableCampaignCriterion](../campaign-api/biddablecampaigncriterion-data-object.md) or [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) object is a [LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md), please note the following usage of *BidMultiplier* properties.

### <a name="locationintentcriterion_multiplier"></a>Multiplier
You cannot bid on a location intent criterion. The service will ignore the multiplier without returning any error.


## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md)  
[BiddableCampaignCriterion](../campaign-api/biddablecampaigncriterion-data-object.md)  

