---
title: "SearchQueryReportAggregation Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a348768f-7081-47f7-85cd-1054816c7fed
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SearchQueryReportAggregation Value Set
Defines the aggregation values that you can use in a search query performance report.

## Syntax

```xml
<xs:simpleType name="SearchQueryReportAggregation">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Summary" />
    <xs:enumeration value="Hourly" />
    <xs:enumeration value="Daily" />
    <xs:enumeration value="Weekly" />
    <xs:enumeration value="Monthly" />
    <xs:enumeration value="Yearly" />
    <xs:enumeration value="HourOfDay" />
    <xs:enumeration value="DayOfWeek" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Daily|The report data will be aggregated for each day.|
|DayOfWeek|The report data will be aggregated by each of the seven days in a week.|
|Hourly|The report data will be aggregated for each hour.|
|HourOfDay|The report data will be aggregated by each of the 24 hours in a day.|
|Monthly|The report data will be aggregated for each month.|
|Summary|The report data will be aggregated for the entire specified report time.|
|Weekly|The report data will be aggregated for each week.|
|Yearly|The report data will be aggregated for each year.|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[SearchQueryPerformanceReportRequest](../reporting-api/searchqueryperformancereportrequest-data-object.md)

