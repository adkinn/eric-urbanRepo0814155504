---
title: "OfflineConversion Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 372081e2-f09d-4d8d-9e9c-a3e32dcf4d91
caps.latest.revision: 14
author: "eric-urban"
ms.author: "eur"
---
# OfflineConversion Data Object
Defines an offline conversion that you send to Bing Ads. 

To set up offine conversion tracking, create an [OfflineConversionGoal](../campaign-api/offlineconversiongoal-data-object.md). If you set the *CountType* of the [OfflineConversionGoal](../campaign-api/offlineconversiongoal-data-object.md) to *All*, then all offline conversions for the same *MicrosoftClickId* with different conversion times will be added cumulatively. If you set the *CountType* of the [OfflineConversionGoal](../campaign-api/offlineconversiongoal-data-object.md) to *Unique*, then only the first conversion that happens after an ad click will be counted. Duplicate offline conversions with the same *MicrosoftClickId* and *ConversionTime* will be ignored. In other words only the first offline conversion for a given *MicrosoftClickId* and *ConversionTime* will be counted.

After the [OfflineConversionGoal](../campaign-api/offlineconversiongoal-data-object.md) is set up, wait two hours and then send Bing Ads the [OfflineConversion](../campaign-api/offlineconversion-data-object.md) data via the [ApplyOfflineConversions](../campaign-api/applyofflineconversions-service-operation.md) operation. It can take up to five hours to view conversion data in the Bing Ads reporting.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../campaign-api/includes/pilot-comingsoon.md)]

## Syntax

```xml
<xs:complexType name="OfflineConversion">
  <xs:sequence>
    <xs:element minOccurs="0" name="ConversionCurrencyCode" nillable="true" type="xs:string"/>
    <xs:element minOccurs="0" name="ConversionName" nillable="true" type="xs:string"/>
    <xs:element minOccurs="0" name="ConversionTime" nillable="true" type="xs:dateTime"/>
    <xs:element minOccurs="0" name="ConversionValue" nillable="true" type="xs:double"/>
    <xs:element minOccurs="0" name="MicrosoftClickId" nillable="true" type="xs:string"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ConversionCurrencyCode*|The currency code for the offline conversion.<br/><br/>For more information, see [Currencies](https://msdn.microsoft.com/library/bing-ads-currencies.aspx).<br/><br/>**Apply:** Optional. If you do not specify an offline conversion currency code, then the *CurrencyCode* element of the goal's [ConversionGoalRevenue](../campaign-api/conversiongoalrevenue-data-object.md) is used.|*string*|
|*ConversionName*|The conversion goal name.<br/><br/>This name must match an existing conversion goal name, otherwise the offline conversion goal data will not be applied.<br/><br/>**Apply:** Required|*string*|
|*ConversionTime*|The date and time when the offline conversion occurred.<br/><br/>The date and time must be within the last 90 days, otherwise the operation will fail when you attempt to send Bing Ads the offline conversion data.<br/><br/>To be counted by Bing Ads as an offline conversion after successful upload, the following additional requirements must be met:<br/>-  The date and time of the conversion must be set later than the date and time of the recorded click.<br/>-  The date and time must be within the conversion window. The *ConversionWindowInMinutes* property of the [OfflineConversionGoal](../campaign-api/offlineconversiongoal-data-object.md) determines the maximum length of time in minutes after a click that conversions will be tracked.<br/><br/>For example if three clicks were recorded on April 30th, if the *ConversionWindowInMinutes* of the [OfflineConversionGoal](../campaign-api/offlineconversiongoal-data-object.md) is equal to 30 days (43200 minutes), and if you send Bing Ads the following offline conversions on July 31st, then Bing Ads will only count the one with MicrosoftClickId=*2* as an offline conversion.<br/>-  MicrosoftClickId=*1*; ConversionTime=*2017-04-30T17:02:35.6853793Z*<br/>-  MicrosoftClickId=*2*; ConversionTime=*2017-05-15T17:02:35.6853793Z*<br/>-  MicrosoftClickId=*3*; ConversionTime=*2017-06-15T17:02:35.6853793Z*<br/><br/>The offline conversion data with MicrosoftClickId=*1* will not be uploaded since the conversion date and time is more than 90 days ago, and the offline conversion data with MicrosoftClickId=*3* will not be counted because it does not fall within the conversion window (April 30 through May 29).<br/><br/>**Important:** The value must be in Coordinated Universal Time (UTC). This differs from the time zone options when you upload offline conversions in the Bing Ads web application. For information about the format of the date and time, see the dateTime entry in [Primitive XML Data Types](https://msdn.microsoft.com/library/ms256220.aspx). <br/><br/>**Apply:** Required|*dateTime*|
|*ConversionValue*|The offline conversion value.<br/><br/>**Apply:** Optional. If you do not specify an offline conversion value, then the *Value* element of the goal's [ConversionGoalRevenue](../campaign-api/conversiongoalrevenue-data-object.md) is used.|*double*|
|*MicrosoftClickId*|The MSCLKID for the offline conversion.<br/><br/>To ensure that auto-tagging is enabled for Microsoft click ID tracking, use the [GetAccountProperties](../campaign-api/getaccountproperties-service-operation.md) and [SetAccountProperties](../campaign-api/setaccountproperties-service-operation.md) operations. <br/><br/>**Apply:** Required|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[OfflineConversionGoal](../campaign-api/offlineconversiongoal-data-object.md)  
[ApplyOfflineConversions](../campaign-api/applyofflineconversions-service-operation.md)  
