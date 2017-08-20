---
title: "AppInstallGoal Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6f9ee697-c893-4c8f-9168-eda1aa9c2b95
caps.latest.revision: 18
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AppInstallGoal Data Object
Defines an app install conversion goal. Use this type of goal to track every time someone installs your app as a conversion.

For other conversion goal types you create a Universal Event Tracking (UET) tag, add it to your website, and then create a conversion goal. But for app install conversion goals, all you have to do is use the app-specific URL that is provided by the Bing Ads-certified partner. For more information, please see [How to track mobile app installs as conversions](http://help.bingads.microsoft.com/#apex/3/en/56690/2). 

[!INCLUDE[guide_uet](../campaign-api/includes/guide-uet.md)]


## Syntax

```xml
\<xs:complexType name="AppInstallGoal">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:ConversionGoal">
      \<xs:sequence>
        \<xs:element minOccurs="0" name="AppPlatform" nillable="true" type="xs:string"/>
        \<xs:element minOccurs="0" name="AppStoreId" nillable="true" type="xs:string"/>
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
The *AppInstallGoal* object inherits elements from the [ConversionGoal](../campaign-api/conversiongoal-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AppPlatform*|The application platform.<br /><br />Possible values include *Android*, *iOS*, *Windows* and *WindowsPhone*.<br/><br/>**Add:** Required<br/>**Update:** Optional|*string*|
|*AppStoreId*|The application identifier provided by the app store.<br/><br/>**Add:** Required<br/>**Update:** Optional|*string*|

## <a name="InheritedElements"></a>Inherited Elements
The *AppInstallGoal* object inherits the following elements from the [ConversionGoal](../campaign-api/conversiongoal-data-object.md) object. 

> [!NOTE]
> The descriptions below are specific to app install goals, and might not apply to other objects that inherit the same elements from the [ConversionGoal](../campaign-api/conversiongoal-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ConversionWindowInMinutes*|The conversion window is the length of time in minutes after a click that you want to track conversions. If you set this value to 43200 minutes (30 days), then conversions that happen within 30 days after a click are tracked. Past conversions aren't affected. The minimum value supported is 1 minute, although keep in mind that a shorter conversion window will reduce the number of conversions your account records. The maximum value supported is 129600 minutes (90 days).<br/><br/>**Add:** Optional<br/>**Update:** Optional|*int*|
|*CountType*|Not applicable for app install goals.|[ConversionGoalCountType](../campaign-api/conversiongoalcounttype-value-set.md)|
|*Id*|The unique Bing Ads identifier for the conversion goal.<br/><br/>**Add:** Read-only<br/>**Update:** Required and Read-Only|*long*|
|*Name*|The conversion goal name.<br/><br/>The maximum length of the name is 100, and the name must be unique among all conversion goals belonging to the same customer.|*string*|
|*Revenue*|Determines how much each conversion is worth to your business.<br/><br/>When adding a conversion goal if you do not specify any revenue tracking preferences, then each [ConversionGoalRevenue](../campaign-api/conversiongoalrevenue-data-object.md) will be set to their respective default values.<br/><br/>When updating a conversion goal, if the *Revenue* element is nil or empty then none of the nested properties will be updated. However, if this element is not nil or empty then you are effectively replacing any existing revenue properties.<br/><br/>**Note:** The *VariableValue* option is not available for app install conversion goals.<br/><br/>**Add:** Optional<br/>**Update:** Optional|[ConversionGoalRevenue](../campaign-api/conversiongoalrevenue-data-object.md)|
|*Scope*|Determines if the goal applies to all accounts or only the account specified in the required *CustomerAccountId* header element. If you have multiple Bing Ads accounts, you can track conversions across all of those accounts. If you associate a goal with one account, conversions will be tracked for that account only.<br/><br/>For app install goals the Account level scope is not supported. You can set this element to Customer or leave it nil. If not specified, the scope will be set to Customer by default.<br/><br/>**Add:** Optional<br/>**Update:** Optional|[EntityScope](../campaign-api/entityscope-value-set.md)|
|*Status*|Defines the possible user-determined status values of a conversion goal. These are the status values that a user can decide to set, for example a goal can be set to *Paused* if you no longer wish to track conversions for that goal.<br/><br/>For status values that can be set by the system, see the *TrackingStatus* element.<br/><br/>**Add:** Optional<br/>**Update:** Optional|[ConversionGoalStatus](../campaign-api/conversiongoalstatus-value-set.md)|
|*TagId*|Not applicable for app install goals.|*long*|
|*TrackingStatus*|Defines the possible system-determined status values of a conversion goal. These are the status values that can be set by the system, for example the system sets the status to *RecordingConversions* if we have recorded conversions within the last 7 days.<br/><br/>Only the *NoRecentConversions* and *RecordingConversions* statuses are applicable for app install conversion goals.<br/><br/>For status values that a user can decide to set, for example setting the status to *Paused* if you no longer wish to track conversions for that goal, see the *Status* element.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[ConversionGoalTrackingStatus](../campaign-api/conversiongoaltrackingstatus-value-set.md)|
|*Type*|The type of the conversion goal. This value is *AppInstall* when you retrieve an app install goal. For more information about conversion goal types, see the [ConversionGoal Data Object Remarks](../campaign-api/conversiongoal-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[ConversionGoalType](../campaign-api/conversiongoaltype-value-set.md)|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[ConversionGoal](../campaign-api/conversiongoal-data-object.md)  
[AddConversionGoals](../campaign-api/addconversiongoals-service-operation.md)  
[GetConversionGoalsByIds](../campaign-api/getconversiongoalsbyids-service-operation.md)  
[GetConversionGoalsByTagIds](../campaign-api/getconversiongoalsbytagids-service-operation.md)  
[UpdateConversionGoals](../campaign-api/updateconversiongoals-service-operation.md)  