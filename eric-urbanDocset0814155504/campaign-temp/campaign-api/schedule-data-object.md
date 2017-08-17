---
title: "Schedule Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 085ef17d-218b-4ebf-85d7-e6054b8b0d6f
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Schedule Data Object
Defines the start and end date ranges for ad extension scheduling. 

Use the *StartDate* and *EndDate* elements for calendar level scheduling, and then use *DayTimeRanges* to limit scheduling by day of the week, hour, and minute. 

## Syntax

```xml
\<xs:complexType name="Schedule">
  \<xs:sequence>
    \<xs:element name="DayTimeRanges" type="tns:ArrayOfDayTime" nillable="true" minOccurs="0"/>
    \<xs:element name="EndDate" type="tns:Date" nillable="true" minOccurs="0"/>
    \<xs:element name="StartDate" type="tns:Date" nillable="true" minOccurs="0"/>
    \<xs:element name="UseSearcherTimeZone" type="xs:boolean" nillable="true" minOccurs="0"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*DayTimeRanges*|The list of day and time ranges. Each day and time range includes the scheduled day of week, start/end hour, and start/end minute.<br/><br/>**Add:** Optional. If you set this element to null, then ad extensions will be eligible for scheduling anytime during the calendar start and end dates.<br/>**Update:** Optional. The individual [DayTime](../campaign-api/daytime-data-object.md) objects cannot be updated. You can effectively update the day and time ranges by sending a new list of all [DayTime](../campaign-api/daytime-data-object.md) settings that should replace the prior set. If you set this element to null, then you are effectively removing all existing day and time ranges.|[DayTime](../campaign-api/daytime-data-object.md) array|
|*EndDate*|The scheduled end date. <br /><br />The end date is inclusive. For example, if you set *EndDate* to 3/10/2017, the ad extensions will stop being shown at 11:59 PM on 3/10/2017.<br/><br/>**Add:** Optional. If you do not specify an end date, the ad extensions will continue to be delivered unless you pause the associated campaigns, ad groups, or ads.<br/>**Update:** Optional. The end date can be shortened or extended, as long as the start date is either null or occurs before the new end date. If you set the end date to null, then you are effectively removing the end date and the ad extensions will continue to be delivered unless you pause the associated campaigns, ad groups, or ads. |[Date](../campaign-api/date-data-object.md)|
|*StartDate*|The scheduled start date. <br /><br />The start date is inclusive. For example, if you set *StartDate* to 3/5/2017, the ad extensions will start being shown at 12:00 AM on 3/5/2017.<br/><br/>**Add:** Optional. If you do not specify a start date, the ad extensions are immediately eligible to be scheduled during the day and time ranges.<br/>**Update:** Optional. The start date can be shortened or extended, as long as the end date is either null or occurs after the new start date. If set the start date to null, then you are effectively removing the start date and the ad extensions are immediately eligible to be scheduled during the day and time ranges.|[Date](../campaign-api/date-data-object.md)|
|*UseSearcherTimeZone*|Determines whether to use the account time zone or the time zone of the search user where the ads could be delivered. Set this property to *true* if you want the ad extensions to be shown in the search user's time zone, and otherwise set it to *false*. <br/><br/>**Add:** Optional. If you do not specify this element or leave it null, the default value of *false* will be set and the account time zone will be used. <br/>**Update:** When you update a schedule the existing settings are replaced with the new setting. Thus if you update a schedule and leave this element null, then you are effectively resetting to the default value of *false*. |*boolean*|


## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdExtensionAssociation](../campaign-api/adextensionassociation-data-object.md)  
[AddAdExtensions](../campaign-api/addadextensions-service-operation.md)  
[GetAdExtensionsByIds](../campaign-api/getadextensionsbyids-service-operation.md)  
[UpdateAdExtensions](../campaign-api/updateadextensions-service-operation.md)  
