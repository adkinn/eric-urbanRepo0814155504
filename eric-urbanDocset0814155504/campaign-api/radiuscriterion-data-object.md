---
title: "RadiusCriterion Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f1ac98de-b672-4c4b-969e-cb3b2e8f5b36
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
---
# RadiusCriterion Data Object
Defines a criterion that can be used to show ads to users within the radius of a specific geographical location.

With radius criterions, you can choose to show ads to potential customers in, searching for, or viewing pages about a specified radius around a zip code, coordinates, landmark, or area.

Each radius criterion defines a radius, latitude, and longitude for the accompanying criterion bid adjustment. 

The maximum number of radius criterions that you can specify per campaign or ad group is 2,000.

> [!NOTE]
> You can only have one [LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md) per campaign or ad group to determine the location intent option that applies for all of the campaign or ad group's geographical criterions (location, negative location, and radius criterions). When you create the campaign or ad group's first criterion, a [LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md) will also be added automatically with the default *IntentOption* set to *PeopleInOrSearchingForOrViewingPages*. You can add or update a campaign or ad group's [LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md), whether or not the campaign or ad group has any other criterions. You cannot delete a [LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md), although it has no purpose without location or radius criterions. 

The *RadiusCriterion* criterion can be included within [AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md) and [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) objects. If ad group level radius criterions are specified, the campaign level radius criterions are ignored for that ad group. In other words the ad group radius criterions override the campaign radius criterions, and are not applied as a union.  

Also note that you must consider the location, negative location, and radius criterions as a set of *geo criterions*. If the ad group has any geo criterions, then none of the campaign's geo criterions are inherited. If the ad group doesn't have any geo criterions, then all of the campaign's geo criterions are inherited. The geo criterions can be inherited from the campaign even if the ad group has a location intent criterion. If the ad group's geo criterions are used, then the ad group's location intent criterion is used; if the campaign's geo criterions are inherited, then the campaign's location intent criterion is used and the ad group's location intent criterion is ignored. You cannot delete a campaign or ad group's location intent criterion, although it has no purpose without location or radius criterions. 

[!INCLUDE[guide_target_to_criterions](../campaign-api/includes/guide-target-to-criterions.md)]

## Syntax

```xml
<xs:complexType name="RadiusCriterion">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:Criterion">
      <xs:sequence>
        <xs:element name="LatitudeDegrees" type="xs:double" minOccurs="0" nillable="true"/>
        <xs:element name="LongitudeDegrees" type="xs:double" minOccurs="0" nillable="true"/>
        <xs:element name="Name" nillable="true" type="xs:string" minOccurs="0" nillable="true"/>
        <xs:element name="Radius" type="xs:double" minOccurs="0" nillable="true"/>
        <xs:element name="RadiusUnit" type="tns:DistanceUnit" minOccurs="0" nillable="true"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *RadiusCriterion* object derives from the [Criterion](../campaign-api/criterion-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*LatitudeDegrees*|The latitude, in degrees, of the target location.<br /><br />The latitude must be greater than or equal to -85.0 and less than or equal to +85.0.<br/><br/>**Add:** Required<br/>**Update:** Not allowed. If you specify this element it must match the existing setting.|*double*|
|*LongitudeDegrees*|The longitude, in degrees, of the target location.<br /><br />The longitude must be greater than or equal to -180.0 and less than or equal to +180.0.<br/><br/>**Add:** Required<br/>**Update:** Not allowed. If you specify this element it must match the existing setting.|*double*|
|*Name*|The name of the geographical location being targeted. The name can contain a maximum of 50 characters.<br/><br/>**Add:** Optional<br/>**Update:** Read-only|*string*|
|*Radius*|The radius that specifies the area surrounding the geographical location to target.<br /><br />If the *RadiusUnit* is set to Miles, then positive integer values from 1 to 500 are accepted.<br /><br />If the *RadiusUnit* is set to Kilometers, then positive integer values from 1 to 800 are accepted.<br /><br />**Note:** The data type is double and may be supported in a future release. Currently the service only accepts and returns integer values.<br/><br/>**Add:** Required<br/>**Update:** Not allowed. If you specify this element it must match the existing setting.|*double*|
|*RadiusUnit*|The unit of measurement for the specified radius, for example kilometers or miles.<br/><br/>**Add:** Required<br/>**Update:** Not allowed. If you specify this element it must match the existing setting.|[DistanceUnit](../campaign-api/distanceunit-value-set.md)|

## <a name="InheritedElements"></a>Inherited Elements
The *RadiusCriterion* object derives from the [Criterion](../campaign-api/criterion-data-object.md) object, and inherits the following element. 

> [!NOTE]
> The descriptions below are specific to radius criterions, and might not apply to other objects that inherit the same elements from the [Criterion](../campaign-api/criterion-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of the criterion. This value is *Radius* when you retrieve a radius criterion. For more information about criterion types, see the [Criterion Data Object Remarks](../campaign-api/criterion-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[Criterion](../campaign-api/criterion-data-object.md)  
