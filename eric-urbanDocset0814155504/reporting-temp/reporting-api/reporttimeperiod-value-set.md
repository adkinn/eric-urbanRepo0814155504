---
title: "ReportTimePeriod Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a0cdc07-5ec8-40ff-8ab9-4c646e6a141f
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ReportTimePeriod Value Set
Defines the predefined time and date range values for a report request.

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
|LastFourWeeks|A cumulative report for the four calendar weeks prior to today.<br /><br />**Note**: A calendar week runs from Sunday to Saturday.|
|LastMonth|A cumulative report for the previous calendar month.|
|LastSevenDays|A report for the previous seven days, one row for each day.|
|LastSixMonths|A cumulative report for the previous six calendar months.|
|LastThreeMonths|A cumulative report for the previous three calendar months.|
|LastWeek|A cumulative report for the previous calendar week.<br /><br />**Note**: A calendar week runs from Sunday to Saturday.|
|LastYear|A cumulative report for the previous calendar year.|
|ThisMonth|A cumulative report for the current calendar month.|
|ThisWeek|A cumulative report for the current calendar week.|
|ThisYear|A cumulative report for the current calendar year.|
|Today|A cumulative report for the current day.|
|Yesterday|A cumulative report for the previous day.|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[ReportTime](../reporting-api/reporttime-data-object.md)

