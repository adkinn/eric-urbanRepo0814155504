---
title: "LocationIntentCriterion Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d32b775c-94c2-40ad-88e1-bad701a717af
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
---
# LocationIntentCriterion Data Object
Defines a criterion that determines the intent option for all location and radius criterions of the campaign or ad group. There isn't any accompanying criterion bid adjustment. 

The maximum number of location intent criterions that you can specify per campaign or ad group is one.

> [!NOTE]
> You can only have one [LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md) per campaign or ad group to determine the location intent option that applies for all of the campaign or ad group's geographical criterions (location, negative location, and location intent criterions). When you create the campaign or ad group's first criterion, a [LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md) will also be added automatically with the default *IntentOption* set to *PeopleInOrSearchingForOrViewingPages*. You can add or update a campaign or ad group's [LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md), whether or not the campaign or ad group has any other criterions. You cannot delete a [LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md), although it has no purpose without location or location intent criterions. 

The *LocationIntentCriterion* criterion can be included within [AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md) and [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) objects. 

Also note that you must consider the location, negative location, and radius criterions as a set of *geo criterions*. If the ad group has any geo criterions, then none of the campaign's geo criterions are inherited. If the ad group doesn't have any geo criterions, then all of the campaign's geo criterions are inherited. The geo criterions can be inherited from the campaign even if the ad group has a location intent criterion. If the ad group's geo criterions are used, then the ad group's location intent criterion is used; if the campaign's geo criterions are inherited, then the campaign's location intent criterion is used and the ad group's location intent criterion is ignored. You cannot delete a campaign or ad group's location intent criterion, although it has no purpose without location or radius criterions. 

[!INCLUDE[guide_target_to_criterions](../campaign-api/includes/guide-target-to-criterions.md)]

## Syntax

```xml
\<xs:complexType name="LocationIntentCriterion">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:Criterion">
      \<xs:sequence>
        \<xs:element name="IntentOption" type="tns:IntentOption" minOccurs="0" nillable="true"/>
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
The *LocationIntentCriterion* object derives from the [Criterion](../campaign-api/criterion-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*IntentOption*|Determines whether a person must be physically located in the targeted location in order for the ad to display.<br/><br/>The following values are supported. The default value is *PeopleInOrSearchingForOrViewingPages*.<br/>- Use *PeopleInOrSearchingForOrViewingPages* if you want to show ads to people in, searching for, or viewing pages about your targeted location.<br/>- Use *PeopleSearchingForOrViewingPages* if you want to show ads to people searching for or viewing pages about your targeted location.<br/>- Use *PeopleIn* if you want to show ads to people in your targeted location.<br/><br/>**Add:** Optional. If no value is specified the default value is *PeopleInOrSearchingForOrViewingPages*.<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|[IntentOption](../campaign-api/intentoption-value-set.md)|

## <a name="InheritedElements"></a>Inherited Elements
The *LocationIntentCriterion* object derives from the [Criterion](../campaign-api/criterion-data-object.md) object, and inherits the following element. 

> [!NOTE]
> The descriptions below are specific to location intent criterions, and might not apply to other objects that inherit the same elements from the [Criterion](../campaign-api/criterion-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of the criterion. This value is *LocationIntent* when you retrieve a location intent criterion. For more information about criterion types, see the [Criterion Data Object Remarks](../campaign-api/criterion-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[Criterion](../campaign-api/criterion-data-object.md)  
