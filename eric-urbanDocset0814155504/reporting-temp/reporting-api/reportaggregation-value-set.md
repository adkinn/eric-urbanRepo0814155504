---
title: "ReportAggregation Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0ecd379-51e6-42b1-ad9a-75103e1d7097
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ReportAggregation Value Set
Defines the aggregation values that you can use for a report.

## Syntax

```xml
\<xs:simpleType name="ReportAggregation">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Summary"/>
    \<xs:enumeration value="Hourly"/>
    \<xs:enumeration value="Daily"/>
    \<xs:enumeration value="Weekly"/>
    \<xs:enumeration value="Monthly"/>
    \<xs:enumeration value="Yearly"/>
    \<xs:enumeration value="HourOfDay"/>
    \<xs:enumeration value="DayOfWeek"/>
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Daily|Each row of the report identifies the month, day, and year when the transaction occurred. The report data will be aggregated by each day. Each row of the report identifies the month, day, and year when the transaction occurred. The report will include a column named *GregorianDate* that contains the day formatted as *yyyy-mm-dd*.|
|DayOfWeek|Each row of the report identifies the day of the week when the transaction occurred. The report data will be aggregated by each of the seven days in a week. The report will include a column named *DayOfWeek*, and the possible values are *1* - *7* where *1* represents Sunday and *7* represents Saturday. If the report time spans multiple weeks, then the performance data across all weeks for a given day of the week will be aggregated in one row. For example if *Campaign A* has 5 impressions every Monday (day *2*) throughout each of the 3 weeks included in the report time range, then the report will include one row with *DayOfWeek* set to *2* and impressions in that row totaling 15.<br/><br/>**Note:** The report will not include a column named *GregorianDate*. If you want data by date, you can use Daily or Hourly aggregation.|
|Hourly|Each row of the report identifies the hour when the transaction occurred. The report data will be aggregated by each hour of the day. The report will include a column named *Hour*, and the possible values are *0* - *23*. The report will also include a column named *GregorianDate* that contains the date formatted as *yyyy-mm-dd*. If the report time spans multiple days, then the performance data for a given hour will be provided separately across multiple rows i.e. the report will include one row for each unique day and hour. For example if *Campaign A* has 5 impressions during *Hour* 7 on each of the 3 days included in the report time range, then the report will include three rows each with 5 impressions for *Hour* 7.|
|HourOfDay|Each row of the report identifies the hour of the day when the transaction occurred. The report data will be aggregated by each of the 24 hours across all days.  The report will include a column named *HourOfDay*, and the possible values are *0* - *23*. If the report time spans multiple days, then the performance data across all days for a given hour will be aggregated in one row. For example if *Campaign A* has 5 impressions during hour *7* on each of the 3 days included in the report time range, then the report will include one row with impressions for *HourOfDay* totaling 15.|
|Monthly|Each row of the report identifies the month when the transaction occurred. The report data will be aggregated by each month. The report will include a column named *MonthStartDate* that contains the first day of the month formatted as *yyyy-mm-dd*.|
|Summary|The report data will be aggregated by the entire specified report time. The report will not include a time period column.|
|Weekly|Each row of the report identifies the week when the transaction occurred. The report data will be aggregated by each week. The report will include a column named *WeekStartDate* that contains the date of the Sunday for each week formatted as *yyyy-mm-dd*.|
|Yearly|Each row of the report identifies the year when the transaction occurred. The report data will be aggregated by each year. The report will include a column named *Year* that contains the year formatted as *yyyy*.|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[ReportRequest](../reporting-api/reportrequest-data-object.md)  

