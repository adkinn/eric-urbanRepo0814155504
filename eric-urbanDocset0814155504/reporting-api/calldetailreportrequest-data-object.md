---
title: "CallDetailReportRequest Data Object"
ms.custom: ""
ms.date: "05/23/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 70de2e55-24a4-491f-ae1d-9cbad6780643
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CallDetailReportRequest Data Object
Defines a call detail report request. Use this report to discover which accounts, campaigns, or ad groups are driving the most completed phone calls.

You can request duration and phone spend for each forwarded call that originated from a call ad extension.

There is one row or record in the report for each call made to the tracked number.

[!INCLUDE[reportrequest_header](../reporting-api/includes/reportrequest-header.md)]

> [!NOTE]
> [!INCLUDE[report_not_applicable_to_bsc](../reporting-api/includes/report-not-applicable-to-bsc.md)]

## Syntax

```xml
<xs:complexType name="CallDetailReportRequest">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:ReportRequest">
      <xs:sequence>
        <xs:element name="Aggregation" type="tns:ReportAggregation" />
        <xs:element name="Columns" type="tns:ArrayOfCallDetailReportColumn" nillable="true"/>
        <xs:element name="Filter" type="tns:CallDetailReportFilter" nillable="true" minOccurs="0"/>
        <xs:element name="Scope" type="tns:AccountThroughAdGroupReportScope" nillable="true"/>
        <xs:element name="Time" type="tns:ReportTime" nillable="true"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
This object inherits elements from the [ReportRequest](../reporting-api/reportrequest-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*Aggregation*|The type of aggregation to use to aggregate the report data.<br /><br />The default is Summary.<br /><br />**Note**: For this report, *Aggregation* must always be set to Summary.<br /><br />The *Time* element specifies the time period to use for the aggregation.|[ReportAggregation](../reporting-api/reportaggregation-value-set.md)|Optional|
|*Columns*|The list of attributes and performance statistics to include in the report. The report will include the columns in the order that you specify them.|[CallDetailReportColumn](../reporting-api/calldetailreportcolumn-value-set.md) array|Required|
|*Filter*|The filter information to use to filter the report data.|[CallDetailReportFilter](../reporting-api/calldetailreportfilter-data-object.md)|Optional|
|*Scope*|The scope of the report. Use this element to limit the report to include data for specified accounts, campaigns, or ad groups.<br /><br />**Note**: For this report you may only specify one account identifier in the *AccountIds* element of the  *AccountThroughAdGroupReportScope* object.|[AccountThroughAdGroupReportScope](../reporting-api/accountthroughadgroupreportscope-data-object.md)|Required|
|*Time*|The time period to use for the report. You can specify a custom date range or select a predefined date range, for example, Today or LastSevenDays.<br /><br />For a list of the time periods that you can specify for the Summary aggregation type, see [Aggregation and Time](http://go.microsoft.com/fwlink/?LinkId=691012).|[ReportTime](../reporting-api/reporttime-data-object.md)|Required|

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

