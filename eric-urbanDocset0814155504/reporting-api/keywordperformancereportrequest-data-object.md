---
title: "KeywordPerformanceReportRequest Data Object"
ms.custom: ""
ms.date: "05/31/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8a4a731b-bbd8-4a7b-b4d8-4d4cffd48ee0
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordPerformanceReportRequest Data Object
Defines a keyword performance report request. Use this report to find out which keywords are performing well and those that are not. 

You can request impressions, clicks, spend, and average cost per click for your landing pages. Once downloaded, this data can be sorted by keyword, account, campaign, and ad group.

[!INCLUDE[reportrequest_header](../reporting-api/includes/reportrequest-header.md)]

> [!NOTE]
> [!INCLUDE[report_not_applicable_to_bsc](../reporting-api/includes/report-not-applicable-to-bsc.md)]

## Syntax

```xml
<xs:complexType name="KeywordPerformanceReportRequest">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:ReportRequest">
      <xs:sequence>
        <xs:element name="Aggregation" type="tns:ReportAggregation" />
        <xs:element name="Columns" nillable="true" type="tns:ArrayOfKeywordPerformanceReportColumn" />
        <xs:element name="Filter" type="tns:KeywordPerformanceReportFilter" nillable="true" minOccurs="0"/>
        <xs:element name="MaxRows" type="xs:int" minOccurs="0"/>
        <xs:element name="Scope" nillable="true" type="tns:AccountThroughAdGroupReportScope" />
        <xs:element name="Sort" type="tns:ArrayOfKeywordPerformanceReportSort" nillable="true" minOccurs="0"/>
        <xs:element name="Time" nillable="true" type="tns:ReportTime" />
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
This object inherits elements from the [ReportRequest](../reporting-api/reportrequest-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*Aggregation*|The type of aggregation to use to aggregate the report data. For example, you can aggregate the report data by day or week, or request a summary report.<br /><br />The default is Summary.<br /><br />The *Time* element specifies the time period to use for the aggregation.|[ReportAggregation](../reporting-api/reportaggregation-value-set.md)|Optional|
|*Columns*|The list of attributes and performance statistics to include in the report. The report will include the columns in the order that you specify them.|[KeywordPerformanceReportColumn](../reporting-api/keywordperformancereportcolumn-value-set.md) array|Required|
|*Filter*|The filter information to use to filter the report data.|[KeywordPerformanceReportFilter](../reporting-api/keywordperformancereportfilter-data-object.md)|Optional|
|*MaxRows*|The top number of data rows to return in the report.|*int*|Optional|
|*Scope*|The scope of the report. Use this element to limit the report to include data for a combination of accounts, ad groups, and campaigns.|[AccountThroughAdGroupReportScope](../reporting-api/accountthroughadgroupreportscope-data-object.md)|Required|
|*Sort*|A list of the columns to sort, and the corresponding sort order.|[KeywordPerformanceReportSort](../reporting-api/keywordperformancereportsort-data-object.md) array|Optional|
|*Time*|The time period to use for the report. You can specify a custom date range or select a predefined date range, for example, Today or ThisWeek.<br /><br />For a list of the time periods that you can specify for each aggregation type, see [Aggregation and Time](http://go.microsoft.com/fwlink/?LinkId=691012).|[ReportTime](../reporting-api/reporttime-data-object.md)|Required|

## <a name="InheritedElements"></a>Inherited Elements
This object inherits the following elements from the [ReportRequest](../reporting-api/reportrequest-data-object.md) object.

|Element|Description|Data Type|Required/Optional|
|-----------|---------------|-------------|---------------------|
|*Format*|[!INCLUDE[reportrequest_format](../reporting-api/includes/reportrequest-format.md)]|[ReportFormat](../reporting-api/reportformat-value-set.md)|Optional|
|*Language*|[!INCLUDE[reportrequest_language](../reporting-api/includes/reportrequest-language.md)]|[ReportLanguage](../reporting-api/reportlanguage-value-set.md)|Optional|
|*ReportName*|[!INCLUDE[reportrequest_reportname](../reporting-api/includes/reportrequest-reportname.md)]|*string*|Optional|
|*ReturnOnlyCompleteData*|[!INCLUDE[reportrequest_returnonlycompletedata](../reporting-api/includes/reportrequest-returnonlycompletedata.md)]|*boolean*|Optional|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[ReportRequest](../reporting-api/reportrequest-data-object.md)  
[SubmitGenerateReport](../reporting-api/submitgeneratereport-service-operation.md)  

