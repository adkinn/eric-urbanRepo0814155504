---
title: "ReportTimePeriod Value Set"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1ae44fd7-fa78-4149-8698-210753ecb677
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ReportTimePeriod Value Set
Defines the date range values for the requested performance data in a bulk download.

## Syntax

```xml
\<xs:simpleType name="ReportTimePeriod">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Today"/>
    \<xs:enumeration value="Yesterday"/>
    \<xs:enumeration value="LastSevenDays"/>
    \<xs:enumeration value="ThisWeek"/>
    \<xs:enumeration value="LastWeek"/>
    \<xs:enumeration value="LastFourWeeks"/>
    \<xs:enumeration value="ThisMonth"/>
    \<xs:enumeration value="LastMonth"/>
    \<xs:enumeration value="LastThreeMonths"/>
    \<xs:enumeration value="LastSixMonths"/>
    \<xs:enumeration value="ThisYear"/>
    \<xs:enumeration value="LastYear"/>
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|LastFourWeeks|Performance data for the four calendar weeks prior to today.<br /><br />**Note:** A calendar week runs from Sunday to Saturday.|
|LastMonth|Performance data for the previous calendar month.|
|LastSevenDays|Performance data for the previous seven days, one row for each day.|
|LastSixMonths|Performance data for the previous six calendar months.|
|LastThreeMonths|Performance data for the previous three calendar months.|
|LastWeek|Performance data for the previous calendar week.<br /><br />**Note:** A calendar week runs from Sunday to Saturday.|
|LastYear|Performance data for the previous calendar year.|
|ThisMonth|Performance data for the current calendar month.|
|ThisWeek|Performance data for the current calendar week.|
|ThisYear|Performance data for the current calendar year.|
|Today|Performance data for the current day.|
|Yesterday|Performance data for the previous day.|

## Requirements
[!INCLUDE[reqbulk](../bulk-api/includes/reqbulk.md)]
## See Also
[PerformanceStatsDateRange](../bulk-api/performancestatsdaterange-data-object.md)

