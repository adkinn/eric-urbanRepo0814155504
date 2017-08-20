---
title: "DeliveredMatchTypeReportFilter Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6f2d63c7-ab50-4276-9bf6-330cd103f2af
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DeliveredMatchTypeReportFilter Value Set
Defines the delivered match type values that you can use to filter the report data. These values are also used as column values in reports that include match type, such as the keyword performance report.

## Syntax

```xml
\<xs:simpleType name="DeliveredMatchTypeReportFilter">
  \<xs:list>
    \<xs:simpleType>
      \<xs:restriction base="xs:string">
        \<xs:enumeration value="Exact"/>
        \<xs:enumeration value="Phrase"/>
        \<xs:enumeration value="Broad"/>
        \<xs:enumeration value="Content"/>
      \</xs:restriction>
    \</xs:simpleType>
  \</xs:list>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Broad|The report will contain ads that were delivered using a broad match comparison.|
|Content|The report will contain ads that were delivered by using a content match comparison.|
|Exact|The report will contain ads that were delivered by using an exact match comparison.|
|Phrase|The report will contain ads that were delivered by using a phrase match comparison.|

## Remarks
This value set is used as a set of flags. You can combine the values when setting an element of this type. For example, in C#, use the following code example to filter the report data for only ads that were delivered by using the broad and phrase match comparisons in the report.

```csharp
objKeywordPerfReportRequest.DeliveredMatchType = 
    DeliveredMatchTypeReportFilter.Broad | 
    DeliveredMatchTypeReportFilter.Phrase;
```

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[KeywordPerformanceReportFilter](../reporting-api/keywordperformancereportfilter-data-object.md)  
[SitePerformanceReportFilter](../Topic/SitePerformanceReportFilter%20Data%20Object.md)  

