---
title: "AdTypeReportFilter Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4e42bab5-92fe-4f0a-a555-a65955cc6d69
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdTypeReportFilter Value Set
Defines the ad type values that you can use to filter the report data. These values are also used as column values in reports that include the ad type, such as the ad performance report.

## Syntax

```xml
<xs:simpleType name="AdTypeReportFilter">
  <xs:list>
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:enumeration value="Text" />
        <xs:enumeration value="Local" /> 
        <xs:enumeration value="Product" /> 
        <xs:enumeration value="AppInstall" /> 
        <xs:enumeration value="DynamicSearchAd" /> 
        <xs:enumeration value="ExpandedText" /> 
      </xs:restriction>
    </xs:simpleType>
  </xs:list>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|AppInstall|The report will include app install ads.|
|DynamicSearchAd|The report will include dynamic search ads.|
|ExpandedText|The report will include expanded text ads.|
|Local|Not supported.|
|Product|The report will include product ads.|
|Text|The report will include text ads.|

## Remarks
This value set is used as a set of flags. You can combine the values when setting an element of this type. For example, in C#, use the following code example to filter the report data for expanded text and dynamic search ads in the report.

```csharp
objAdPerformanceReportFilter.AdType = 
    AdTypeReportFilter.ExpandedText | AdTypeReportFilter.DynamicSearchAd;
```

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[AdDynamicTextPerformanceReportFilter](../reporting-api/addynamictextperformancereportfilter-data-object.md)  
[AdPerformanceReportFilter](../reporting-api/adperformancereportfilter-data-object.md)  
[KeywordPerformanceReportFilter](../reporting-api/keywordperformancereportfilter-data-object.md)  
[SitePerformanceReportFilter](../Topic/SitePerformanceReportFilter%20Data%20Object.md)  

