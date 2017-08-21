---
title: "SearchCampaignChangeHistoryReportRequest Data Object"
ms.custom: ""
ms.date: "05/23/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b576d086-5a48-407d-b766-a9e920dbc2da
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SearchCampaignChangeHistoryReportRequest Data Object
Defines a change history report request. Use this report to discover when changes to an account were made, as well as which user made the changes.

You can request a record of changes made by user and date. For example, you can request a record of changes to campaign name, location target association, and keyword bid. You can request both the old value and new value in the report.

> [!NOTE]
> It can take approximately one hour from the time an entity is added, updated, or deleted for the change history to be available for reporting.

[!INCLUDE[reportrequest_header](../reporting-api/includes/reportrequest-header.md)]
## Syntax

```xml
<xs:complexType name="SearchCampaignChangeHistoryReportRequest">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:ReportRequest">
      <xs:sequence>
        <xs:element name="Columns" nillable="true" type="tns:ArrayOfSearchCampaignChangeHistoryReportColumn" />
        <xs:element minOccurs="0" name="Filter" nillable="true" type="tns:SearchCampaignChangeHistoryReportFilter" />
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
|*Columns*|The list of attributes and performance statistics to include in the report. The report will include the columns in the order that you specify them.|[SearchCampaignChangeHistoryReportColumn](../reporting-api/searchcampaignchangehistoryreportcolumn-value-set.md) array|Required|
|*Filter*|The filter information to use to filter the report data.|[SearchCampaignChangeHistoryReportFilter](../reporting-api/searchcampaignchangehistoryreportfilter-data-object.md)|Optional|
|*Scope*|The scope of the report. Use this element to limit the report to include data for a combination of accounts, ad groups, and campaigns.<br /><br />**Note**: For this report you may only specify one account identifier in the *AccountIds* element of the  *AccountThroughAdGroupReportScope* object.|[AccountThroughAdGroupReportScope](../reporting-api/accountthroughadgroupreportscope-data-object.md)|Required|
|*Time*|The time period to use for the report. You can specify a custom date range or select one of the following predefined date ranges:<br /><br />LastSevenDays<br /><br />LastMonth<br /><br />LastThreeMonths|[ReportTime](../reporting-api/reporttime-data-object.md)|Required|

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

