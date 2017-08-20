---
title: "BudgetSummaryReportRequest Data Object"
ms.custom: ""
ms.date: "05/23/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e109ed80-f6b1-41f1-812c-85338b1f60d1
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BudgetSummaryReportRequest Data Object
Defines a budget summary report request. Use this report to discover how your campaign’s budget is performing for the month. For example, the report shows your monthly budget, how much you have spent to date, and whether you are on target to spend your monthly budget.

You can request your monthly budget, how much you have spent to date, and whether you are on target to spend your monthly budget.

[!INCLUDE[reportrequest_header](../reporting-api/includes/reportrequest-header.md)]
## Syntax

```xml
\<xs:complexType name="BudgetSummaryReportRequest">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:ReportRequest">
      \<xs:sequence>
        \<xs:element name="Columns" nillable="true" type="tns:ArrayOfBudgetSummaryReportColumn" />
        \<xs:element name="Scope" nillable="true" type="tns:AccountThroughCampaignReportScope" />
        \<xs:element name="Time" nillable="true" type="tns:BudgetSummaryReportTime" />
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
This object inherits elements from the [ReportRequest](../reporting-api/reportrequest-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*Columns*|The list of attributes and performance statistics to include in the report. The report will include the columns in the order that you specify them.|[BudgetSummaryReportColumn](../reporting-api/budgetsummaryreportcolumn-value-set.md) array|Required|
|*Scope*|The scope of the report. Use this element to limit the report to include data for a combination of accounts and campaigns.|[AccountThroughCampaignReportScope](../reporting-api/accountthroughcampaignreportscope-data-object.md)|Required|
|*Time*|The time period to use for the report. You can specify a custom date range or select a predefined date range, for example, Today or ThisMonth.|[BudgetSummaryReportTime](../reporting-api/budgetsummaryreporttime-data-object.md)|Required|

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

