---
title: "KeywordStatusReportFilter Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b116ef9-1fa7-48c3-9811-d405cbcc2184
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordStatusReportFilter Value Set
Defines the keyword status values that you can use to filter the report data. These values are also used as column values in reports that include keyword status, such as the keyword performance report.

## Syntax

```xml
<xs:simpleType name="KeywordStatusReportFilter">
  <xs:list>
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:enumeration value="Active"/>
        <xs:enumeration value="Paused"/>
        <xs:enumeration value="Deleted"/>
      </xs:restriction>
    </xs:simpleType>
  </xs:list>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Active|The report will contain keywords that are active.|
|Deleted|The report will contain keywords that have been deleted.|
|Paused|The report will contain keywords that are paused.|

## Remarks
This value set is used as a set of flags. You may combine the values when setting an element of this type. For example, in C#, use the following code example to filter the report data for paused and deleted keywords in the report.

```csharp
objKeywordPerfReportRequest.Status = 
    KeywordStatusReportFilter.Paused | 
    KeywordStatusReportFilter.Deleted;
```

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]

## See Also
[KeywordPerformanceReportFilter](../reporting-api/keywordperformancereportfilter-data-object.md)  

