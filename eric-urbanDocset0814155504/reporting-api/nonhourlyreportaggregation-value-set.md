---
title: "NonHourlyReportAggregation Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec65c601-6d13-4ffc-b745-9bd5ba061a3d
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# NonHourlyReportAggregation Value Set
Defines the aggregation values for reports that cannot specify hourly aggregation.

## Syntax

```xml
<xs:simpleType name="NonHourlyReportAggregation">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Summary"/>
    <xs:enumeration value="Daily"/>
    <xs:enumeration value="Weekly"/>
    <xs:enumeration value="Monthly"/>
    <xs:enumeration value="Yearly"/>
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Daily|Each row of the report identifies the month, day, and year when the transaction occurred. The report data will be aggregated by each day. Each row of the report identifies the month, day, and year when the transaction occurred. The report will include a column named *GregorianDate* that contains the day formatted as *mm/dd/yyyy*.|
|Monthly|Each row of the report identifies the month when the transaction occurred. The report data will be aggregated by each month. The report will include a column named *MonthStartDate* that contains the first day of the month formatted as *mm/dd/yyyy*.|
|Summary|The report data will be aggregated by the entire specified report time. The report will not include a time period column.|
|Weekly|Each row of the report identifies the week when the transaction occurred. The report data will be aggregated by each week. The report will include a column named *WeekStartDate* that contains the date of the Sunday for each week formatted as *mm/dd/yyyy*.|
|Yearly|Each row of the report identifies the year when the transaction occurred. The report data will be aggregated by each year. The report will include a column named *Year* that contains the year formatted as *yyyy*.|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[AdDynamicTextPerformanceReportRequest](../reporting-api/addynamictextperformancereportrequest-data-object.md)  
[AdPerformanceReportRequest](../reporting-api/adperformancereportrequest-data-object.md)  
[AgeGenderDemographicReportRequest](../reporting-api/agegenderdemographicreportrequest-data-object.md)  
[DestinationUrlPerformanceReportRequest](../reporting-api/destinationurlperformancereportrequest-data-object.md)  
[GeoLocationPerformanceReportRequest](../Topic/GeoLocationPerformanceReportRequest%20Data%20Object.md)  
[PublisherUsagePerformanceReportRequest](../reporting-api/publisherusageperformancereportrequest-data-object.md)  

