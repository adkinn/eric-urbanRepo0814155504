---
title: "BudgetSummaryReportTime Data Object"
ms.custom: ""
ms.date: "05/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b704a7b3-54bd-4c3a-bf8e-d30f434704f0
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BudgetSummaryReportTime Data Object
Defines the date range values of a budget summary report request.

> [!NOTE]
> The *CustomDateRangeStart* and *CustomDateRangeEnd* elements versus the *PredefinedTime* element are mutually exclusive. For information about how the time zone of the campaign affects the date range that you specify, see [Time Zones in Reporting](https://msdn.microsoft.com/library/bing-ads-time-zones.aspx).

## Syntax

```xml
\<xs:complexType name="BudgetSummaryReportTime">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="CustomDateRangeEnd" nillable="true" type="tns:Date" />
    \<xs:element minOccurs="0" name="CustomDateRangeStart" nillable="true" type="tns:Date" />
    \<xs:element minOccurs="0" name="PredefinedTime" nillable="true" type="tns:BudgetSummaryReportTimePeriod" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CustomDateRangeEnd*|The end date of a date range.<br/><br/>The end date must be greater than or equal to the start date.<br/><br/>|[Date](../reporting-api/date-data-object.md)|
|*CustomDateRangeStart*|The start date of a date range.<br/><br/>|[Date](../reporting-api/date-data-object.md)|
|*PredefinedTime*|A predefined date range.<br/><br/>The *PredefinedTime* element and the other date elements are mutually exclusive.|[BudgetSummaryReportTimePeriod](../reporting-api/budgetsummaryreporttimeperiod-value-set.md)|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[BudgetSummaryReportRequest](../reporting-api/budgetsummaryreportrequest-data-object.md)  

