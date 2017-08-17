---
title: "DynamicAdTargetStatusReportFilter Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 824cc44d-014d-47b6-aa4a-ec809b09a7d8
caps.latest.revision: 2
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DynamicAdTargetStatusReportFilter Value Set
Defines the dynamic ad target status values that you can use to filter the report data. These values are also used as column values in reports that include dynamic ad targets status, such as the DSA auto target performance report.

## Syntax

```xml
\<xs:simpleType name="DynamicAdTargetStatusReportFilter">
  \<xs:list>
    \<xs:simpleType>
      \<xs:restriction base="xs:string">
        \<xs:enumeration value="Active"/>
        \<xs:enumeration value="Paused"/>
        \<xs:enumeration value="Deleted"/>
      \</xs:restriction>
    \</xs:simpleType>
  \</xs:list>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Active|The report will contain dynamic ad targets that are active.|
|Deleted|The report will contain dynamic ad targets that have been deleted.|
|Paused|The report will contain dynamic ad targets that are paused.|

## Remarks
This value set is used as a set of flags. You can combine the values when setting an element of this type. For example, in C#, use the following code example to filter the report data for paused and deleted dynamic ad targets in the report.

```csharp
objAdPerfReportRequest.Status = 
    DynamicAdTargetStatusReportFilter.Paused | DynamicAdTargetStatusReportFilter.Deleted;
```

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[DSAAutoTargetPerformanceReportFilter](../reporting-api/dsaautotargetperformancereportfilter-data-object.md)  

