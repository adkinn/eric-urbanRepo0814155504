---
title: "ConversionGoal Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f1af04cd-af1b-4259-bbda-9c15a12be218
caps.latest.revision: 14
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ConversionGoal Data Object
Defines the base object of a conversion goal.

Do not try to instantiate a *ConversionGoal*. You can create one or more following objects that derive from it.
- [AppInstallGoal](../campaign-api/appinstallgoal-data-object.md)
- [DurationGoal](../campaign-api/durationgoal-data-object.md)
- [EventGoal](../campaign-api/eventgoal-data-object.md) 
- [InStoreTransactionGoal](../campaign-api/instoretransactiongoal-data-object.md) 
- [OfflineConversionGoal](../campaign-api/offlineconversiongoal-data-object.md) 
- [PagesViewedPerVisitGoal](../campaign-api/pagesviewedpervisitgoal-data-object.md)
- [UrlGoal](../campaign-api/urlgoal-data-object.md)

## Syntax

```xml
<xs:complexType name="ConversionGoal">
  <xs:sequence>
    <xs:element name="ConversionWindowInMinutes" type="xs:int" nillable="true" minOccurs="0"/>
    <xs:element name="CountType" type="tns:ConversionGoalCountType" nillable="true" minOccurs="0"/>
    <xs:element name="Id" type="xs:long" nillable="true" minOccurs="0"/>
    <xs:element name="Name" type="xs:string" nillable="true" minOccurs="0"/>
    <xs:element name="Revenue" type="tns:ConversionGoalRevenue" nillable="true" minOccurs="0"/>
    <xs:element name="Scope" type="tns:EntityScope" nillable="true" minOccurs="0"/>
    <xs:element name="Status" type="tns:ConversionGoalStatus" nillable="true" minOccurs="0"/>
    <xs:element name="TagId" type="xs:long" nillable="true" minOccurs="0"/>
    <xs:element name="TrackingStatus" type="tns:ConversionGoalTrackingStatus" nillable="true" minOccurs="0"/>
    <xs:element name="Type" type="tns:ConversionGoalType" nillable="true" minOccurs="0"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ConversionWindowInMinutes*|The conversion window is the length of time in minutes after a click that you want to track conversions. If you set this value to 43200 minutes (30 days), then conversions that happen within 30 days after a click are tracked. Past conversions aren't affected. The minimum value supported is 1 minute, although keep in mind that a shorter conversion window will reduce the number of conversions your account records. The maximum value supported is 129600 minutes (90 days).|*int*|
|*CountType*|This determines how your conversions are recorded within your chosen conversion window.<br/><br/>There are two choices, and if you do not set a value the default is *All*:<br/><br/>- *All*:  All conversions that happen after an ad click will be counted. This is a common choice for sales. <br/><br/>-  *Unique*:  Only one conversion that happens after an ad click will be counted. This is a common choice for leads.<br/><br/>For example:  You track two conversions: leads and sales. You pick *Unique* for leads and *All* for sales. When one ad click turns into two leads and two sales, it's counted as three conversions: one for the unique lead, and two for all the sales.<br/><br/>**Note:** This element is not applicable for the [AppInstallGoal](../campaign-api/appinstallgoal-data-object.md).|[ConversionGoalCountType](../campaign-api/conversiongoalcounttype-value-set.md)|
|*Id*|The unique Bing Ads identifier for the conversion goal.|*long*|
|*Name*|The conversion goal name.<br/><br/>The maximum length of the name is 100, and the name must be unique among all conversion goals belonging to the same customer.|*string*|
|*Revenue*|Determines how much each conversion is worth to your business.<br/><br/>When adding a conversion goal if you do not specify any revenue tracking preferences, then each [ConversionGoalRevenue](../campaign-api/conversiongoalrevenue-data-object.md) will be set to their respective default values.<br/><br/>When updating a conversion goal, if the *Revenue* element is nil or empty then none of the nested properties will be updated. However, if this element is not nil or empty then you are effectively replacing any existing revenue properties.<br/><br/>**Note:** The *VariableValue* option is not available for the [AppInstallGoal](../campaign-api/appinstallgoal-data-object.md), [DurationGoal](../campaign-api/durationgoal-data-object.md), or [PagesViewedPerVisitGoal](../campaign-api/pagesviewedpervisitgoal-data-object.md).|[ConversionGoalRevenue](../campaign-api/conversiongoalrevenue-data-object.md)|
|*Scope*|Determines if the goal applies to all accounts or only the account specified in the required *CustomerAccountId* header element. If you have multiple Bing Ads accounts, you can track conversions across all of those accounts. If you associate a goal with one account, conversions will be tracked for that account only.<br/><br/>Possible values are *Account* and *Customer*. If not specified, the scope will be set to *Customer* by default. <br/><br/>Once you set scope, you can't change it. If you want to change the scope, you need to create a new conversion goal and pause the old one.<br/><br/>**Note:** Only the *Customer* scope is supported for the [AppInstallGoal](../campaign-api/appinstallgoal-data-object.md).<br/><br/>**Note:** Only the *Account* scope is supported for the [OfflineConversionGoal](../campaign-api/offlineconversiongoal-data-object.md).|[EntityScope](../campaign-api/entityscope-value-set.md)|
|*Status*|Defines the possible user-determined status values of a conversion goal. These are the status values that a user can decide to set, for example a goal can be set to *Paused* if you no longer wish to track conversions for that goal.<br/><br/>For status values that can be set by the system, for example whether or not the UET tag is verified, see the *TrackingStatus* element.|[ConversionGoalStatus](../campaign-api/conversiongoalstatus-value-set.md)|
|*TagId*|The unique Bing Ads identifier of the UET tag that you added to your website to allow Bing Ads to collect actions people take on your website.<br/><br/>**Note:** This element is not applicable for the [AppInstallGoal](../campaign-api/appinstallgoal-data-object.md) and [OfflineConversionGoal](../campaign-api/offlineconversiongoal-data-object.md).|*long*|
|*TrackingStatus*|Defines the possible system-determined status values of a conversion goal. These are the status values that can be set by the system, for example the system sets the status to *TagUnverified* if the UET tag has not yet been verified.<br/><br/>For status values that a user can decide to set, for example setting the status to *Paused* if you no longer wish to track conversions for that goal, see the *Status* element.<br/><br/>**Note:** Only the *NoRecentConversions* and *RecordingConversions* statuses are applicable for the [AppInstallGoal](../campaign-api/appinstallgoal-data-object.md) and [OfflineConversionGoal](../campaign-api/offlineconversiongoal-data-object.md).|[ConversionGoalTrackingStatus](../campaign-api/conversiongoaltrackingstatus-value-set.md)|
|*Type*|The type of the conversion goal. For more information about conversion goal types, see the [Remarks](#remarks).|[ConversionGoalType](../campaign-api/conversiongoaltype-value-set.md)|

## <a name="remarks"></a>Remarks
For Java and the .NET languages, do not set the *Type* element because the value is determined by which type of conversion goal you instantiate.

If you generate the SOAP manually, use the *type* attribute of the `<ConversionGoal>` node as shown in the following example, to specify the type of the conversion goal.

```xml
<ConversionGoals i:nil="false">
  <ConversionGoal i:type="UrlGoal">
    <ConversionWindowInMinutes i:nil="false"></ConversionWindowInMinutes>
    <CountType i:nil="false">Unique</CountType>
    <Id i:nil="true" />
    <Name i:nil="false">My Url Conversion Goal</Name>
    <Revenue i:nil="false">
      <CurrencyCode i:nil="false">USDollar</CurrencyCode>
      <Type i:nil="false">FixedValue</Type>
      <Value i:nil="false">10.00</Value>
    </Revenue>
    <Scope i:nil="false">Customer</Scope>
    <Status i:nil="true" />
    <TagId i:nil="false"></TagId>
    <TrackingStatus i:nil="true" />
    <UrlExpression i:nil="false">contoso</UrlExpression>
    <UrlOperator i:nil="false">Contains</UrlOperator>
  </ConversionGoal>
</ConversionGoals>
```

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also

[AddConversionGoals](../campaign-api/addconversiongoals-service-operation.md)  
[GetConversionGoalsByIds](../campaign-api/getconversiongoalsbyids-service-operation.md)  
[GetConversionGoalsByTagIds](../campaign-api/getconversiongoalsbytagids-service-operation.md)  
[UpdateConversionGoals](../campaign-api/updateconversiongoals-service-operation.md)  
