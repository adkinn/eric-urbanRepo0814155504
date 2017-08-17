---
title: "BidMatchTypeReportFilter Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 82439b42-60a6-43e6-9af2-dde93c0641b5
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BidMatchTypeReportFilter Value Set
Defines the bid match type values that you can use to filter the report data. These values are also used as column values in reports that include bid match type, such as the keyword performance report.

## Syntax

```xml
\<xs:simpleType name="BidMatchTypeReportFilter">
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
|Broad|The report will contain keywords that set a bid value for the broad match type.|
|Content|The report will contain keywords that set a bid value for the content match type.|
|Exact|The report will contain keywords that set a bid value for the exact match type.|
|Phrase|The report will contain keywords that set a bid value for the phrase match type.|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[KeywordPerformanceReportFilter](../reporting-api/keywordperformancereportfilter-data-object.md)  

