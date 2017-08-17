---
title: "AdStatusReportFilter Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 301bcc45-3a29-4be7-9fc9-f14f070858e2
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdStatusReportFilter Value Set
Defines the ad status values that you can use to filter the report data. These values are also used as column values in reports that include ad status, such as the search query performance report.

## Syntax

```xml
\<xs:simpleType name="AdStatusReportFilter">
  \<xs:list>
    \<xs:simpleType>
      \<xs:restriction base="xs:string">
        \<xs:enumeration value="Rejected"/>
        \<xs:enumeration value="Deleted"/>
        \<xs:enumeration value="Pending"/>
        \<xs:enumeration value="Active"/>
        \<xs:enumeration value="Paused"/>
      \</xs:restriction>
    \</xs:simpleType>
  \</xs:list>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Active|The report will contain ads that are active.|
|Deleted|The report will contain ads that have been deleted.|
|Paused|The report will contain ads that are paused.|
|Pending|The report will contain ads that are pending editorial review.|
|Rejected|The report will contain ads that have been rejected by editorial review.|

## Remarks
This value set is used as a set of flags. You can combine the values when setting an element of this type. For example, in C#, use the following code example to filter the report data for paused and deleted ads in the report.

```csharp
objAdPerfReportRequest.Status = 
    AdStatusReportFilter.Paused | AdStatusReportFilter.Deleted;
```

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[SearchQueryPerformanceReportFilter](../reporting-api/searchqueryperformancereportfilter-data-object.md)  

