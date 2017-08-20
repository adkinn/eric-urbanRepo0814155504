---
title: "GoalsAndFunnelsReportRequest Data Object"
ms.custom: ""
ms.date: "07/31/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 015f22a0-48c9-42b6-b8b7-0e1002168190
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GoalsAndFunnelsReportRequest Data Object
Defines a goals and funnels report request. Use this report to discover whether your audience completes each step through the land, browse, prospect, and conversion pages of your website. For example, you can use this report to determine the step that users leave the conversion funnel, so that you can improve or remove that step to increase the chance that the user will continue to the next step.

You can request spend, revenue, assists, conversions, and conversion steps of your websites. Once downloaded, this data can be sorted by account, ad group, campaign, keyword, and goal.

[!INCLUDE[reportrequest_header](../reporting-api/includes/reportrequest-header.md)]

> [!NOTE]
> [!INCLUDE[report_not_applicable_to_bsc](../reporting-api/includes/report-not-applicable-to-bsc.md)]

## Syntax

```xml
<xs:complexType name="GoalsAndFunnelsReportRequest">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:ReportRequest">
      <xs:sequence>
        <xs:element name="Aggregation" type="tns:NonHourlyReportAggregation" />
        <xs:element name="Columns" nillable="true" type="tns:ArrayOfGoalsAndFunnelsReportColumn" />
        <xs:element minOccurs="0" name="Filter" nillable="true" type="tns:GoalsAndFunnelsReportFilter" />
        <xs:element name="Scope" nillable="true" type="tns:AccountThroughAdGroupReportScope" />
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
|*Aggregation*|The type of aggregation to use to aggregate the report data. For example, you can aggregate the report data by day or week, or request a summary report.<br /><br />The default is Summary.<br /><br />The *Time* element specifies the time period to use for the aggregation.|[NonHourlyReportAggregation](../reporting-api/nonhourlyreportaggregation-value-set.md)|Optional|
|*Columns*|The list of attributes and performance statistics to include in the report. The report will include the columns in the order that you specify them.|[GoalsAndFunnelsReportColumn](../reporting-api/goalsandfunnelsreportcolumn-value-set.md) array|Required|
|*Filter*|The filter information to use to filter the report data.<br /><br />**Note**: The *Filter* element is not supported at this time.|[GoalsAndFunnelsReportFilter](../reporting-api/goalsandfunnelsreportfilter-data-object.md)|Optional|
|*Scope*|The scope of the report. For example, you can limit the report to include data for a combination of accounts, ad groups, and campaigns.|[AccountThroughAdGroupReportScope](../reporting-api/accountthroughadgroupreportscope-data-object.md)|Required|
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

