---
title: "BudgetSummaryReportTimePeriod Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 386864b8-2d5c-4e4f-a61b-dfd4078376c1
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BudgetSummaryReportTimePeriod Value Set
Defines the predefined time and date range values for a budget summary report request.

## Syntax

```xml
<xs:simpleType name="BudgetSummaryReportTimePeriod">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Today"/>
    <xs:enumeration value="Yesterday"/>
    <xs:enumeration value="LastSevenDays"/>
    <xs:enumeration value="ThisMonth"/>
    <xs:enumeration value="LastMonth"/>
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|LastMonth|A cumulative report for the previous calendar month.|
|LastSevenDays|A cumulative report for the previous seven days, having one row for each day.|
|ThisMonth|A cumulative report for the current calendar month.|
|Today|A cumulative report for the current day.|
|Yesterday|A cumulative report for the previous day.|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[BudgetSummaryReportTime](../reporting-api/budgetsummaryreporttime-data-object.md)

