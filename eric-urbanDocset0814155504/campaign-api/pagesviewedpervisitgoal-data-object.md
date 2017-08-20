---
title: "PagesViewedPerVisitGoal Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2dece497-7984-4307-a701-add9238f8677
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# PagesViewedPerVisitGoal Data Object
Defines a pages viewed per visit conversion goal. Use this type of goal to count every time someone visits more than a specified number of pages on your website as a conversion. For example you can count a conversion if someone viewed more than 5 pages on a support site or product catalog.

[!INCLUDE[guide_uet](../campaign-api/includes/guide-uet.md)]

## Syntax

```xml
\<xs:complexType name="PagesViewedPerVisitGoal">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:ConversionGoal">
      \<xs:sequence>
        \<xs:element name="MinimumPagesViewed" type="xs:int" nillable="true" minOccurs="0"/>
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
The *PagesViewedPerVisitGoal* object inherits elements from the [ConversionGoal](../campaign-api/conversiongoal-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*MinimumPagesViewed*|The minimum number of pages the user must visit, in order to count as a conversion.<br/><br/>**Add:** Required<br/>**Update:** Optional|*int*|

## <a name="InheritedElements"></a>Inherited Elements
The *PagesViewedPerVisitGoal* object inherits the following elements from the [ConversionGoal](../campaign-api/conversiongoal-data-object.md) object. 

> [!NOTE]
> The descriptions below are specific to pages viewed per visit goals, and might not apply to other objects that inherit the same elements from the [ConversionGoal](../campaign-api/conversiongoal-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ConversionWindowInMinutes*|The conversion window is the length of time in minutes after a click that you want to track conversions. If you set this value to 43200 minutes (30 days), then conversions that happen within 30 days after a click are tracked. Past conversions aren't affected. The minimum value supported is 1 minute, although keep in mind that a shorter conversion window will reduce the number of conversions your account records. The maximum value supported is 129600 minutes (90 days).<br/><br/>**Add:** Optional<br/>**Update:** Optional|*int*|
|*CountType*|This determines how your conversions are recorded within your chosen conversion window.<br/><br/>There are two choices, and if you do not set a value the default is *All*:<br/><br/>- *All*:  All conversions that happen after an ad click will be counted. This is a common choice for sales. <br/><br/>-  *Unique*:  Only one conversion that happens after an ad click will be counted. This is a common choice for leads.<br/><br/>For example:  You track two conversions: leads and sales. You pick *Unique* for leads and *All* for sales. When one ad click turns into two leads and two sales, it's counted as three conversions: one for the unique lead, and two for all the sales.<br/><br/>**Add:** Optional<br/>**Update:** Optional|[ConversionGoalCountType](../campaign-api/conversiongoalcounttype-value-set.md)|
|*Id*|The unique Bing Ads identifier for the conversion goal.<br/><br/>**Add:** Read-only<br/>**Update:** Required and Read-Only|*long*|
|*Name*|The conversion goal name.<br/><br/>The maximum length of the name is 100, and the name must be unique among all conversion goals belonging to the same customer.|*string*|
|*Revenue*|Determines how much each conversion is worth to your business.<br/><br/>When adding a conversion goal if you do not specify any revenue tracking preferences, then each [ConversionGoalRevenue](../campaign-api/conversiongoalrevenue-data-object.md) will be set to their respective default values.<br/><br/>When updating a conversion goal, if the *Revenue* element is nil or empty then none of the nested properties will be updated. However, if this element is not nil or empty then you are effectively replacing any existing revenue properties. <br/><br/>**Note:** The *VariableValue* option is not available for pages viewed per visit conversion goals.<br/><br/>**Add:** Optional<br/>**Update:** Optional|[ConversionGoalRevenue](../campaign-api/conversiongoalrevenue-data-object.md)|
|*Scope*|Determines if the goal applies to all accounts or only the account specified in the required *CustomerAccountId* header element. If you have multiple Bing Ads accounts, you can track conversions across all of those accounts. If you associate a goal with one account, conversions will be tracked for that account only.<br/><br/>Possible values are *Account* and *Customer*. If not specified, the scope will be set to *Customer* by default. <br/><br/>Once you set scope, you can't change it. If you want to change the scope, you need to create a new conversion goal and pause the old one.<br/><br/>**Add:** Optional<br/>**Update:** Optional|[EntityScope](../campaign-api/entityscope-value-set.md)|
|*Status*|Defines the possible user-determined status values of a conversion goal. These are the status values that a user can decide to set, for example a goal can be set to *Paused* if you no longer wish to track conversions for that goal.<br/><br/>For status values that can be set by the system, for example whether or not the UET tag is verified, see the *TrackingStatus* element.<br/><br/>**Add:** Optional<br/>**Update:** Optional|[ConversionGoalStatus](../campaign-api/conversiongoalstatus-value-set.md)|
|*TagId*|The unique Bing Ads identifier of the UET tag that you added to your website to allow Bing Ads to collect actions people take on your website.<br/><br/>**Add:** Required<br/>**Update:** Optional|*long*|
|*TrackingStatus*|Defines the possible system-determined status values of a conversion goal. These are the status values that can be set by the system, for example the system sets the status to *TagUnverified* if the UET tag has not yet been verified.<br/><br/>For status values that a user can decide to set, for example setting the status to *Paused* if you no longer wish to track conversions for that goal, see the *Status* element.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[ConversionGoalTrackingStatus](../campaign-api/conversiongoaltrackingstatus-value-set.md)|
|*Type*|The type of the conversion goal. This value is *PagesViewedPerVisit* when you retrieve a pages viewed per visit goal. For more information about conversion goal types, see the [ConversionGoal Data Object Remarks](../campaign-api/conversiongoal-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[ConversionGoalType](../campaign-api/conversiongoaltype-value-set.md)|


## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[ConversionGoal](../campaign-api/conversiongoal-data-object.md)  
[AddConversionGoals](../campaign-api/addconversiongoals-service-operation.md)  
[GetConversionGoalsByIds](../campaign-api/getconversiongoalsbyids-service-operation.md)  
[GetConversionGoalsByTagIds](../campaign-api/getconversiongoalsbytagids-service-operation.md)  
[UpdateConversionGoals](../campaign-api/updateconversiongoals-service-operation.md)  