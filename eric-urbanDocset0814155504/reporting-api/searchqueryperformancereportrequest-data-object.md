---
title: "SearchQueryPerformanceReportRequest Data Object"
ms.custom: ""
ms.date: "05/23/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df621c72-e678-4fe0-9e34-9c1d7867ecd3
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SearchQueryPerformanceReportRequest Data Object
Defines a search query performance report request. Use this report to see what your audience is searching for when your ads are shown. You can use this information to make informed additions, removals, or edits to both your keyword and negative keyword lists.

You can request impressions, clicks, click-through rate, and average position for search terms that have triggered your ads. For example, if you are a mortgage lender who is running a campaign with the following keywords: mortgage, home mortgage, and home equity loans; and the report shows that the search query “mortgage rates” results in many impressions of your ad, you would probably add “rates” to your keyword list. However, if you do not provide reverse mortgages and the report shows that the search query “reverse mortgage” results in many impressions, you would probably add “reverse mortgage” to your negative keywords list.

The report will include only search terms that resulted in a significant number of clicks in the last 30 days.

Since this data might change over time, please use the [KeywordPerformanceReportRequest](../reporting-api/keywordperformancereportrequest-data-object.md) to get the performance metrics for your keywords.

[!INCLUDE[reportrequest_header](../reporting-api/includes/reportrequest-header.md)]
## Syntax

```xml
<xs:complexType name="SearchQueryPerformanceReportRequest">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:ReportRequest">
      <xs:sequence>
        <xs:element name="Aggregation" type="tns:SearchQueryReportAggregation" />
        <xs:element name="Columns" nillable="true" type="tns:ArrayOfSearchQueryPerformanceReportColumn" />
        <xs:element minOccurs="0" name="Filter" nillable="true" type="tns:SearchQueryPerformanceReportFilter" />
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
|*Aggregation*|The type of aggregation to use to aggregate the report data. For example, you can aggregate the report data by day or week, or request a summary report.<br /><br />The default is Summary.<br /><br />The *Time* element specifies the time period to use for the aggregation.|[SearchQueryReportAggregation](../reporting-api/searchqueryreportaggregation-value-set.md)|Optional|
|*Columns*|The list of attributes and performance statistics to include in the report. The report will include the columns in the order that you specify them.|[SearchQueryPerformanceReportColumn](../reporting-api/searchqueryperformancereportcolumn-value-set.md) array|Required|
|*Filter*|The filter information to use to filter the report data.|[SearchQueryPerformanceReportFilter](../reporting-api/searchqueryperformancereportfilter-data-object.md)|Optional|
|*Scope*|The scope of the report. Use this element to limit the report to include data for a combination of accounts, ad groups, and campaigns.|[AccountThroughAdGroupReportScope](../reporting-api/accountthroughadgroupreportscope-data-object.md)|Required|
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

