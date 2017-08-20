---
title: "ReportRequest Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 88633df7-23a6-45d4-b219-5de6644313a2
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ReportRequest Data Object
Defines the base object for all report requests.

Do not instantiate this object. Instead, you may instantiate one of the report request objects which derives from this object, for example the [CampaignPerformanceReportRequest](../reporting-api/campaignperformancereportrequest-data-object.md). For a list of reports, see the [Report Types](https://msdn.microsoft.com/library/bing-ads-reporting-report-types.aspx) guide.

## Syntax

```xml
<xs:complexType name="ReportRequest">
  <xs:sequence>
    <xs:element minOccurs="0" name="ExcludeColumnHeaders" nillable="true" type="xs:boolean" />
    <xs:element minOccurs="0" name="ExcludeReportFooter" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="ExcludeReportHeader" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="Format" nillable="true" type="tns:ReportFormat" />
    <xs:element minOccurs="0" name="Language" nillable="true" type="tns:ReportLanguage" />
    <xs:element minOccurs="0" name="ReportName" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="ReturnOnlyCompleteData" nillable="true" type="xs:boolean" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|Required/Optional|
|-----------|---------------|-------------|---------------------|
|*ExcludeColumnHeaders*|Determines whether or not the downloaded report should contain header descriptions for each column. The report column header matches the requested column name e.g. *Impressions* and *Clicks*.<br/><br/>Set this property *true* if you want the report column headers excluded from the downloaded report. The default value is *false*.|*boolean*|Optional|
|*ExcludeReportFooter*|Determines whether or not the downloaded report should contain footer metadata such as Microsoft copyright (*©2017 Microsoft Corporation. All rights reserved.*). <br/><br/>Set this property *true* if you want the report footer metadata excluded from the downloaded report. The default value is *false*.|*boolean*|Optional|
|*ExcludeReportHeader*|Determines whether or not the downloaded report should contain header metadata such as report name, date range, and aggregation.<br/><br/>Set this property *true* if you want the report header metadata excluded from the downloaded report. The default value is *false*.|*boolean*|Optional|
|*Format*|[!INCLUDE[reportrequest_format](../reporting-api/includes/reportrequest-format.md)]|[ReportFormat](../reporting-api/reportformat-value-set.md)|Optional|
|*Language*|[!INCLUDE[reportrequest_language](../reporting-api/includes/reportrequest-language.md)]|[ReportLanguage](../reporting-api/reportlanguage-value-set.md)|Optional|
|*ReportName*|[!INCLUDE[reportrequest_reportname](../reporting-api/includes/reportrequest-reportname.md)]|*string*|Optional|
|*ReturnOnlyCompleteData*|[!INCLUDE[reportrequest_returnonlycompletedata](../reporting-api/includes/reportrequest-returnonlycompletedata.md)]|*boolean*|Optional|


## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
