---
title: "CampaignStatusReportFilter Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d78867ac-a4a3-4b9a-8a78-36d8eee570d4
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CampaignStatusReportFilter Value Set
Defines the campaign status values that you can use to filter the report data. These values are also used as column values in reports that include campaign status, such as the campaign performance report.

## Syntax

```xml
<xs:simpleType name="CampaignStatusReportFilter">
  <xs:list>
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:enumeration value="Cancelled"/>
        <xs:enumeration value="Deleted"/>
        <xs:enumeration value="Paused"/>
        <xs:enumeration value="BudgetPaused"/>
        <xs:enumeration value="Active"/>
        <xs:enumeration value="Suspended"/>
      </xs:restriction>
    </xs:simpleType>
  </xs:list>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Active|The report will contain campaigns that are active.|
|BudgetPaused|The report will contain campaigns that are paused due to budget restrictions.|
|Cancelled|The report will contain campaigns that have been canceled.|
|Deleted|The report will contain campaigns that have been deleted.|
|Paused|The report will contain campaigns that are paused.|
|Suspended|The report will contain campaigns that have been suspended.|

## Remarks
This value set is used as a set of flags. You may combine the values when setting an element of this type. For example, in C#, use the following code example to filter the report data for paused and deleted campaigns in the report.

```csharp
objCampaignPerfReportRequest.Status = 
    CampaignStatusReportFilter.Paused | 
    CampaignStatusReportFilter.Deleted;
```

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[CampaignPerformanceReportFilter](../reporting-api/campaignperformancereportfilter-data-object.md)  
