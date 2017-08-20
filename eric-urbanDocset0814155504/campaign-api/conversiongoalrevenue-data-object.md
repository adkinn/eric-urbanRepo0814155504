---
title: "ConversionGoalRevenue Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 691ba84f-a8fd-4aa7-8882-10071f38efb1
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ConversionGoalRevenue Data Object
Defines properties for revenue that can be tracked by a conversion goal.

## Syntax

```xml
\<xs:complexType name="ConversionGoalRevenue">
  \<xs:sequence>
    \<xs:element name="CurrencyCode" type="xs:string" nillable="true" minOccurs="0"/>
    \<xs:element name="Type" type="tns:ConversionGoalRevenueType" nillable="true" minOccurs="0"/>
    \<xs:element name="Value" type="xs:decimal" nillable="true" minOccurs="0"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CurrencyCode*|The currency type that you want the conversion goal revenue to be reported.<br/><br/>For a list of possible string values see [Bing Ads Currencies](https://msdn.microsoft.com/library/bing-ads-currencies.aspx).<br/><br/>**IMPORTANT:** If the *Scope* element of the parent [ConversionGoal](../campaign-api/conversiongoal-data-object.md) is set to *Customer*, this property will be ignored and by default the account level billing currency will be used to report conversion goal revenue. If the *Scope* element of the parent [ConversionGoal](../campaign-api/conversiongoal-data-object.md) is set to *Account* and you do not specify any *CurrencyCode*, then by default the account level billing currency will be used to report conversion goal revenue.<br/><br/>**Note:** Revenue currency is not available for the [AppInstallGoal](../campaign-api/appinstallgoal-data-object.md), [DurationGoal](../campaign-api/durationgoal-data-object.md), or [PagesViewedPerVisitGoal](../campaign-api/pagesviewedpervisitgoal-data-object.md). You cannot set this property for those goal types.<br/><br/>**Note:** For the [OfflineConversionGoal](../campaign-api/offlineconversiongoal-data-object.md), the *ConversionCurrencyCode* element of the applied [OfflineConversion](../campaign-api/offlineconversion-data-object.md) data takes precedence over this currency code.<br/><br/>**Add:** Required. If the *Type* is *NoValue* (the default type), then the currency code is ignored.<br/>**Update:**  Required. If the *Type* is *NoValue* (the default type), then the currency code is ignored.|*string*|
|*Type*|Determines how revenue is tracked. The possible types are *FixedValue*, *NoValue* (the default type), and *VariableValue*. <br/><br/>If the type is *FixedValue* then you must specify the *Value* element.<br/><br/>If the type is *NoValue* then you must not specify the *Value* element.<br/><br/>If the type is *VariableValue* then you can optionally specify a default value with the *Value* element.|[ConversionGoalRevenueType](../campaign-api/conversiongoalrevenuetype-value-set.md)|
|*Value*|The revenue value or amount.  If you assign values to your conversions, you'll be able to see the total value driven by your advertising across different conversions, rather than simply the number of conversions that have happened.<br/><br/>The default value is effectively 0, and possible values range from 0 to 999,9999. Accepted values depend on the revenue type, so please see the *Type* element for details.<br/><br/>**Note:** For the [OfflineConversionGoal](../campaign-api/offlineconversiongoal-data-object.md), the *ConversionValue* element of the applied [OfflineConversion](../campaign-api/offlineconversion-data-object.md) data takes precedence over this currency value.|*decimal*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[ConversionGoal](../campaign-api/conversiongoal-data-object.md)  

