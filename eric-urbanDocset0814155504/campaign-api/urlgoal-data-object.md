---
title: "UrlGoal Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff66286d-4718-499b-b48d-97e051111f7b
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# UrlGoal Data Object
Defines a URL conversion goal. Use this type of goal to count every time someone visits a web page as a conversion. For example you can count a conversion if someone visits the purchase confirmation page.  

[!INCLUDE[guide_uet](../campaign-api/includes/guide-uet.md)]

## Syntax

```xml
<xs:complexType name="UrlGoal">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:ConversionGoal">
      <xs:sequence>
        <xs:element name="UrlExpression" type="xs:string" nillable="true" minOccurs="0"/>
        <xs:element name="UrlOperator" type="tns:ExpressionOperator" nillable="true" minOccurs="0"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *UrlGoal* object inherits elements from the [ConversionGoal](../campaign-api/conversiongoal-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*UrlExpression*|The expression used to determine the page or pages the user has to visit in order to count as a conversion. <br/><br/>**Add:** Required<br />**Update:** Optional|*string*|
|*UrlOperator*|The operator that can be applied to the value of the *Url* element.<br/><br/>**Add:** Optional; If not specified, the default operator is *Equals*.<br />**Update:** Optional; If not specified during update, the previous setting is retained.|[ExpressionOperator](../campaign-api/expressionoperator-value-set.md)|

## <a name="InheritedElements"></a>Inherited Elements
The *UrlGoal* object inherits the following elements from the [ConversionGoal](../campaign-api/conversiongoal-data-object.md) object. 

> [!NOTE]
> The descriptions below are specific to destination URL goals, and might not apply to other objects that inherit the same elements from the [ConversionGoal](../campaign-api/conversiongoal-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ConversionWindowInMinutes*|The conversion window is the length of time in minutes after a click that you want to track conversions. If you set this value to 43200 minutes (30 days), then conversions that happen within 30 days after a click are tracked. Past conversions aren't affected. The minimum value supported is 1 minute, although keep in mind that a shorter conversion window will reduce the number of conversions your account records. The maximum value supported is 129600 minutes (90 days).<br/><br/>**Add:** Optional<br />**Update:** Optional|*int*|
|*CountType*|This determines how your conversions are recorded within your chosen conversion window.<br/><br/>There are two choices, and if you do not set a value the default is *All*:<br/><br/>- *All*:  All conversions that happen after an ad click will be counted. This is a common choice for sales. <br/><br/>-  *Unique*:  Only one conversion that happens after an ad click will be counted. This is a common choice for leads.<br/><br/>For example:  You track two conversions: leads and sales. You pick *Unique* for leads and *All* for sales. When one ad click turns into two leads and two sales, it's counted as three conversions: one for the unique lead, and two for all the sales.<br/><br/>**Add:** Optional<br />**Update:** Optional|[ConversionGoalCountType](../campaign-api/conversiongoalcounttype-value-set.md)|
|*Id*|The unique Bing Ads identifier for the conversion goal.<br/><br/>**Add:** Read-only<br />**Update:** Required and Read-Only|*long*|
|*Name*|The conversion goal name.<br/><br/>The maximum length of the name is 100, and the name must be unique among all conversion goals belonging to the same customer.|*string*|
|*Revenue*|Determines how much each conversion is worth to your business.<br/><br/>When adding a conversion goal if you do not specify any revenue tracking preferences, then each [ConversionGoalRevenue](../campaign-api/conversiongoalrevenue-data-object.md) will be set to their respective default values.<br/><br/>When updating a conversion goal, if the *Revenue* element is nil or empty then none of the nested properties will be updated. However, if this element is not nil or empty then you are effectively replacing any existing revenue properties.<br/><br/>**Add:** Optional<br />**Update:** Optional|[ConversionGoalRevenue](../campaign-api/conversiongoalrevenue-data-object.md)|
|*Scope*|Determines if the goal applies to all accounts or only the account specified in the required *CustomerAccountId* header element. If you have multiple Bing Ads accounts, you can track conversions across all of those accounts. If you associate a goal with one account, conversions will be tracked for that account only.<br/><br/>Possible values are *Account* and *Customer*. If not specified, the scope will be set to *Customer* by default. <br/><br/>Once you set scope, you can't change it. If you want to change the scope, you need to create a new conversion goal and pause the old one.<br/><br/>**Add:** Optional<br />**Update:** Optional|[EntityScope](../campaign-api/entityscope-value-set.md)|
|*Status*|Defines the possible user-determined status values of a conversion goal. These are the status values that a user can decide to set, for example a goal can be set to *Paused* if you no longer wish to track conversions for that goal.<br/><br/>For status values that can be set by the system, for example whether or not the UET tag is verified, see the *TrackingStatus* element.<br/><br/>**Add:** Optional<br />**Update:** Optional|[ConversionGoalStatus](../campaign-api/conversiongoalstatus-value-set.md)|
|*TagId*|The unique Bing Ads identifier of the UET tag that you added to your website to allow Bing Ads to collect actions people take on your website.<br/><br/>**Add:** Required<br />**Update:** Optional|*long*|
|*TrackingStatus*|Defines the possible system-determined status values of a conversion goal. These are the status values that can be set by the system, for example the system sets the status to *TagUnverified* if the UET tag has not yet been verified.<br/><br/>For status values that a user can decide to set, for example setting the status to *Paused* if you no longer wish to track conversions for that goal, see the *Status* element.<br/><br/>**Add:** Read-only<br />**Update:** Read-only|[ConversionGoalTrackingStatus](../campaign-api/conversiongoaltrackingstatus-value-set.md)|
|*Type*|The type of the conversion goal. This value is *Url* when you retrieve a Url goal. For more information about conversion goal types, see the [ConversionGoal Data Object Remarks](../campaign-api/conversiongoal-data-object.md#remarks).<br/><br/>**Add:** Read-only<br />**Update:** Read-only|[ConversionGoalType](../campaign-api/conversiongoaltype-value-set.md)|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[ConversionGoal](../campaign-api/conversiongoal-data-object.md)  
[AddConversionGoals](../campaign-api/addconversiongoals-service-operation.md)  
[GetConversionGoalsByIds](../campaign-api/getconversiongoalsbyids-service-operation.md)  
[GetConversionGoalsByTagIds](../campaign-api/getconversiongoalsbytagids-service-operation.md)  
[UpdateConversionGoals](../campaign-api/updateconversiongoals-service-operation.md)  
