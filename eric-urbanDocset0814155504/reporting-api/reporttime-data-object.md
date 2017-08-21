---
title: "ReportTime Data Object"
ms.custom: ""
ms.date: "05/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ab2a4cf8-7fe0-48e4-9691-022057e74b5f
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ReportTime Data Object
Defines the date range values of a report request.

## Syntax

```xml
<xs:complexType name="ReportTime">
  <xs:sequence>
    <xs:element minOccurs="0" name="CustomDateRangeEnd" nillable="true" type="tns:Date" />
    <xs:element minOccurs="0" name="CustomDateRangeStart" nillable="true" type="tns:Date" />
    <xs:element minOccurs="0" name="PredefinedTime" nillable="true" type="tns:ReportTimePeriod" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CustomDateRangeEnd*|The end date of the custom date range. The end date cannot be later than today’s date.|[Date](../reporting-api/date-data-object.md)|
|*CustomDateRangeStart*|The start date of the custom date range. The start date must be earlier than or the same as the end date.|[Date](../reporting-api/date-data-object.md)|
|*PredefinedTime*|A predefined date range value. Each report request type specifies the predefined time periods that you can specify for each aggregation type.|[ReportTimePeriod](../reporting-api/reporttimeperiod-value-set.md)|

## Remarks
The *PredefinedTime* element and the custom date range elements are mutually exclusive.

For information about how the time zone of the campaign affects the date range that you specify, see [Time Zones in Reporting](http://go.microsoft.com/fwlink/?LinkId=691015).

For information about how long reporting data is available, see [Reporting Data Retention Time Periods](~/concepts/reporting-data-retention-time-periods.md).

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
