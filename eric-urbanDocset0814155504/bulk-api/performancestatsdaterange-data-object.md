---
title: "PerformanceStatsDateRange Data Object"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e4e6340d-680e-458c-a5ce-b7bf95b74ef8
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# PerformanceStatsDateRange Data Object
Defines the date range values for the requested performance data in a bulk download.

## Syntax

```xml
<xs:complexType name="PerformanceStatsDateRange">
  <xs:sequence>
    <xs:element type="tns:Date" name="CustomDateRangeEnd" nillable="true" minOccurs="0"/>
    <xs:element type="tns:Date" name="CustomDateRangeStart" nillable="true" minOccurs="0"/>
    <xs:element minOccurs="0" name="PredefinedTime" nillable="true" type="tns:ReportTimePeriod" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|`CustomDateRangeEnd`|The end date of the custom date range. The end date cannot be later than today?s date.|[Date](../bulk-api/date-data-object.md)|
|`CustomDateRangeStart`|The start date of the custom date range. The start date must be earlier than or the same as the end date.|[Date](../bulk-api/date-data-object.md)|
|`PredefinedTime`|A predefined date range value.|[ReportTimePeriod](../bulk-api/reporttimeperiod-value-set.md)|

## Requirements
[!INCLUDE[reqbulk](../bulk-api/includes/reqbulk.md)]
## See Also
[DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md)  
[DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md)  

