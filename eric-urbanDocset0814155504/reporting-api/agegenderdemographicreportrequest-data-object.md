---
title: "AgeGenderDemographicReportRequest Data Object"
ms.custom: ""
ms.date: "05/23/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b22f5cf9-c7c3-439b-8026-01264308c61c
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AgeGenderDemographicReportRequest Data Object
Defines an age and gender demographic report request. Use this report to discover how your campaigns and ad groups are resonating with audiences of diverse age and gender.

You can request impression rate (%) and click-through-rate (%) for each campaign or ad group, organized by gender and age group.

[!INCLUDE[reportrequest_header](../reporting-api/includes/reportrequest-header.md)]
## Syntax

```xml
<xs:complexType name="AgeGenderDemographicReportRequest">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:ReportRequest">
      <xs:sequence>
        <xs:element name="Aggregation" type="tns:NonHourlyReportAggregation" />
        <xs:element name="Columns" nillable="true" type="tns:ArrayOfAgeGenderDemographicReportColumn" />
        <xs:element minOccurs="0" name="Filter" nillable="true" type="tns:AgeGenderDemographicReportFilter" />
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
|*Columns*|The list of attributes and performance statistics to include in the report. The report will include the columns in the order that you specify them.|[AgeGenderDemographicReportColumn](../reporting-api/agegenderdemographicreportcolumn-value-set.md) array|Required|
|*Filter*|The filter information to use to filter the report data.|[AgeGenderDemographicReportFilter](../reporting-api/agegenderdemographicreportfilter-data-object.md)|Optional|
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

