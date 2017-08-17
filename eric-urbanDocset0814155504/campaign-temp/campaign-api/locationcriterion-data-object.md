---
title: "LocationCriterion Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c893e2d5-9cff-476a-800e-cc22a70923cb
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
---
# LocationCriterion Data Object
Defines a criterion that can be used to show ads to users in a specific location.

With location criterions, you can choose to show ads to potential customers in, searching for, or viewing pages about:
*  All available countries/regions
*  Selected cities, zip codes, metro areas, states/provinces, and countries/regions

Each location criterion defines a location code for the accompanying criterion bid adjustment. 

The maximum number of combined location and negative location criterions that you can specify per campaign or ad group is 10,000.  

> [!NOTE]
> You can only have one [LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md) per campaign or ad group to determine the location intent option that applies for all of the campaign or ad group's geographical criterions (location, negative location, and radius criterions). When you create the campaign or ad group's first criterion, a [LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md) will also be added automatically with the default *IntentOption* set to *PeopleInOrSearchingForOrViewingPages*. You can add or update a campaign or ad group's [LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md), whether or not the campaign or ad group has any other criterions. You cannot delete a [LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md), although it has no purpose without location or radius criterions. 

The *LocationCriterion* criterion can be included within [AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md), [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md), [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md), and [NegativeCampaignCriterion](../campaign-api/negativecampaigncriterion-data-object.md) objects. If ad group level location criterions are specified (positive or negative), the campaign level location criterions are ignored for that ad group. In other words the ad group location criterions override the campaign location criterions, and are not applied as a union.  

Also note that you must consider the location, negative location, and radius criterions as a set of *geo criterions*. If the ad group has any geo criterions, then none of the campaign's geo criterions are inherited. If the ad group doesn't have any geo criterions, then all of the campaign's geo criterions are inherited. The geo criterions can be inherited from the campaign even if the ad group has a location intent criterion. If the ad group's geo criterions are used, then the ad group's location intent criterion is used; if the campaign's geo criterions are inherited, then the campaign's location intent criterion is used and the ad group's location intent criterion is ignored. You cannot delete a campaign or ad group's location intent criterion, although it has no purpose without location or radius criterions. 

[!INCLUDE[guide_target_to_criterions](../campaign-api/includes/guide-target-to-criterions.md)]

## Syntax

```xml
\<xs:complexType name="LocationCriterion">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:Criterion">
      \<xs:sequence>
        \<xs:element name="DisplayName" type="xs:string"  minOccurs="0" nillable="true"/>
        \<xs:element xmlns:q74="http://schemas.microsoft.com/2003/10/Serialization/Arrays" minOccurs="0" name="EnclosedLocationIds" nillable="true" type="q74:ArrayOflong"/>
        \<xs:element name="LocationId" type="xs:long"  minOccurs="0" nillable="true"/>
        \<xs:element name="LocationType" type="xs:string"  minOccurs="0" nillable="true"/>
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
The *LocationCriterion* object derives from the [Criterion](../campaign-api/criterion-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*DisplayName*|The location display name.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|
|*EnclosedLocationIds*|Reserved for internal use.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*long* array|
|*LocationId*|The unique Bing Ads identifier for the location where you want to show your ads.<br /><br />For geographical location codes, see [Geographical Location Codes](http://msdn.microsoft.com/library/bing-ads-geographical-location-codes).<br/><br/>**Add:** Required<br/>**Update:** Not allowed. If you specify this element it must match the existing setting.|*long*|
|*LocationType*|The location type.<br/><br/>Possible values include, but are not limited to *City*, *Country*, *MetroArea*, *PostalCode*, and *State*.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only |*string*|

## <a name="InheritedElements"></a>Inherited Elements
The *LocationCriterion* object derives from the [Criterion](../campaign-api/criterion-data-object.md) object, and inherits the following element. 

> [!NOTE]
> The descriptions below are specific to location criterions, and might not apply to other objects that inherit the same elements from the [Criterion](../campaign-api/criterion-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of the criterion. This value is *Location* when you retrieve a location criterion. For more information about criterion types, see the [Criterion Data Object Remarks](../campaign-api/criterion-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[Criterion](../campaign-api/criterion-data-object.md)  
