---
title: "OfflineConversionGoal Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f6e76c8f-cba7-486b-8e55-703545088af0
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
---
# OfflineConversionGoal Data Object
Defines an offline conversion goal. Use this type of goal if you have lead generation as an objective. Lead generation is when potential customers fill out a form or quote of interest, and then the sale is completed offline in person or over the phone (for example, car purchases, insurance quotes, mortgages, etc.).  

To set up offine conversion tracking, create an [OfflineConversionGoal](../campaign-api/offlineconversiongoal-data-object.md), wait two hours, and then send Bing Ads the [OfflineConversion](../campaign-api/offlineconversion-data-object.md) data via the [ApplyOfflineConversions](../campaign-api/applyofflineconversions-service-operation.md) operation.

> [!IMPORTANT]
> [!INCLUDE[MSCLKID_auto_enabled](../campaign-api/includes/msclkid-auto-enabled.md)]

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../campaign-api/includes/pilot-comingsoon.md)]

## Syntax

```xml
\<xs:complexType name="OfflineConversionGoal">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:ConversionGoal">
      \<xs:sequence/>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
The *OfflineConversionGoal* object inherits elements from the [ConversionGoal](../campaign-api/conversiongoal-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

## <a name="InheritedElements"></a>Inherited Elements
The *OfflineConversionGoal* object inherits the following elements from the [ConversionGoal](../campaign-api/conversiongoal-data-object.md) object. 

> [!NOTE]
> The descriptions below are specific to offline conversion goals, and might not apply to other objects that inherit the same elements from the [ConversionGoal](../campaign-api/conversiongoal-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ConversionWindowInMinutes*|The conversion window is the length of time in minutes after a click that you want to track conversions. If you set this value to 43200 minutes (30 days), then conversions that happen within 30 days after a click are tracked. Past conversions aren't affected. The minimum value supported is 1 minute, although keep in mind that a shorter conversion window will reduce the number of conversions your account records. The maximum value supported is 129600 minutes (90 days).<br/><br/>**Add:** Optional<br/>**Update:** Optional|*int*|
|*CountType*|This determines how your conversions are recorded within your chosen conversion window.<br/><br/>There are two choices, and if you do not set a value the default is *All*:<br/><br/>- *All*:  All conversions with different offline conversion times that happen after an ad click will be counted. This is a common choice for sales. <br/><br/>-  *Unique*:  Only the first conversion that happens after an ad click will be counted. This is a common choice for leads.<br/><br/>For example:  You track two conversions: leads and sales. You pick *Unique* for leads and *All* for sales. When one ad click turns into two leads and two sales, it's counted as three conversions: one for the unique lead, and two for all the sales.<br/><br/>**Note:** Duplicate offline conversions with the same *MicrosoftClickId* and *ConversionTime* will be ignored. In other words only the first offline conversion for a given *MicrosoftClickId* and *ConversionTime* will be counted.<br/><br/>**Add:** Optional<br/>**Update:** Optional|[ConversionGoalCountType](../campaign-api/conversiongoalcounttype-value-set.md)|
|*Id*|The unique Bing Ads identifier for the conversion goal.<br/><br/>**Add:** Read-only<br/>**Update:** Required and Read-Only|*long*|
|*Name*|The conversion goal name.<br/><br/>The maximum length of the name is 100, and the name must be unique among all conversion goals belonging to the same customer.|*string*|
|*Revenue*|Determines how much each conversion is worth to your business.<br/><br/>When adding a conversion goal if you do not specify any revenue tracking preferences, then each [ConversionGoalRevenue](../campaign-api/conversiongoalrevenue-data-object.md) will be set to their respective default values.<br/><br/>When updating a conversion goal, if the *Revenue* element is nil or empty then none of the nested properties will be updated. However, if this element is not nil or empty then you are effectively replacing any existing revenue properties.<br/><br/>**Note:** If the revenue type is *FixedValue* or *VariableValue*, then the *ConversionCurrencyCode* and *ConversionValue* elements of the applied [OfflineConversion](../campaign-api/offlineconversion-data-object.md) data takes precedence over the [ConversionGoalRevenue](../campaign-api/conversiongoalrevenue-data-object.md) currency code and value.<br/><br/>**Add:** Optional<br/>**Update:** Optional|[ConversionGoalRevenue](../campaign-api/conversiongoalrevenue-data-object.md)|
|*Scope*|Determines if the goal applies to all accounts or only the account specified in the required *CustomerAccountId* header element.<br/><br/>For offline conversion goals the *Customer* level scope is not supported. You can set this element to *Account* or leave it nil. If not specified, the scope will be set to *Account* by default.<br/><br/>**Add:** Optional<br/>**Update:** Optional|[EntityScope](../campaign-api/entityscope-value-set.md)|
|*Status*|Defines the possible user-determined status values of a conversion goal. These are the status values that a user can decide to set, for example a goal can be set to *Paused* if you no longer wish to track conversions for that goal.<br/><br/>For status values that can be set by the system, see the *TrackingStatus* element.<br/><br/>**Add:** Optional<br/>**Update:** Optional|[ConversionGoalStatus](../campaign-api/conversiongoalstatus-value-set.md)|
|*TagId*|Not applicable for offline conversion goals.|*long*|
|*TrackingStatus*|Not applicable for offline conversion goals.|[ConversionGoalTrackingStatus](../campaign-api/conversiongoaltrackingstatus-value-set.md)|
|*Type*|The type of the conversion goal. This value is *OfflineConversion* when you retrieve an offline conversion goal. For more information about conversion goal types, see the [ConversionGoal Data Object Remarks](../campaign-api/conversiongoal-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[ConversionGoalType](../campaign-api/conversiongoaltype-value-set.md)|


## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also

[ConversionGoal](../campaign-api/conversiongoal-data-object.md)  
[AddConversionGoals](../campaign-api/addconversiongoals-service-operation.md)  
[GetConversionGoalsByIds](../campaign-api/getconversiongoalsbyids-service-operation.md)  
[GetConversionGoalsByTagIds](../campaign-api/getconversiongoalsbytagids-service-operation.md)  
[UpdateConversionGoals](../campaign-api/updateconversiongoals-service-operation.md)  