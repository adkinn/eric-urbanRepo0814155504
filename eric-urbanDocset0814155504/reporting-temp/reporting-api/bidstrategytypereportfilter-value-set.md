---
title: "BidStrategyTypeReportFilter Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1ab1f177-f5c4-447b-ab28-e5cdc493f146
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BidStrategyTypeReportFilter Value Set
Defines the possible values that you can use to use to filter the report data by bid strategy type.

## Syntax

```xml
\<xs:complexType name="BidStrategyTypeReportFilter">
  \<xs:sequence>
    \<xs:enumeration value="ManualCpc"/>
    \<xs:enumeration value="EnhancedCpc"/>
  \</xs:sequence>
\</xs:complexType>
```

|Value|Description|
|---------|---------------|
|EnhancedCpc|The report will contain data related to keywords, ad groups, or campaigns that use the enhanced CPC bid strategy.|
|ManualCpc|The report will contain data related to keywords, ad groups, or campaigns that use the manual CPC bid strategy.|


## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[KeywordPerformanceReportFilter](../reporting-api/keywordperformancereportfilter-data-object.md)  
[ShareOfVoiceReportFilter](../reporting-api/shareofvoicereportfilter-data-object.md)  
[SitePerformanceReportFilter](../Topic/SitePerformanceReportFilter%20Data%20Object.md)  