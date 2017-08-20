---
title: "BudgetSummaryReportColumn Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b6074296-2422-4671-bec0-6ef8aefeb0b9
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BudgetSummaryReportColumn Value Set
Defines the attributes and performance statistics columns that you can include in the [BudgetSummaryReportRequest](../reporting-api/budgetsummaryreportrequest-data-object.md).

[!INCLUDE[reportcolumn_header](../reporting-api/includes/reportcolumn-header.md)]
## Syntax

```xml
\<xs:simpleType name="BudgetSummaryReportColumn">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="AccountName"/>
    \<xs:enumeration value="AccountNumber"/>
    \<xs:enumeration value="AccountId"/>
    \<xs:enumeration value="CampaignName"/>
    \<xs:enumeration value="CampaignId"/>
    \<xs:enumeration value="Date"/>
    \<xs:enumeration value="CurrencyCode"/>
    \<xs:enumeration value="MonthlyBudget"/>
    \<xs:enumeration value="DailySpend"/>
    \<xs:enumeration value="MonthToDateSpend"/>
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|AccountId|[!INCLUDE[reportcolumn_accountid](../reporting-api/includes/reportcolumn-accountid.md)]|
|AccountName|[!INCLUDE[reportcolumn_accountname](../reporting-api/includes/reportcolumn-accountname.md)]|
|AccountNumber|[!INCLUDE[reportcolumn_accountnumber](../reporting-api/includes/reportcolumn-accountnumber.md)]|
|CampaignId|[!INCLUDE[reportcolumn_campaignid](../reporting-api/includes/reportcolumn-campaignid.md)]|
|CampaignName|[!INCLUDE[reportcolumn_campaignname](../reporting-api/includes/reportcolumn-campaignname.md)]|
|CurrencyCode|[!INCLUDE[reportcolumn_currencycode](../reporting-api/includes/reportcolumn-currencycode.md)]|
|DailySpend|[!INCLUDE[reportcolumn_dailyspend](../reporting-api/includes/reportcolumn-dailyspend.md)]|
|Date|[!INCLUDE[reportcolumn_date](../reporting-api/includes/reportcolumn-date.md)]|
|MonthlyBudget|[!INCLUDE[reportcolumn_monthlybudget](../reporting-api/includes/reportcolumn-monthlybudget.md)]|
|MonthToDateSpend|[!INCLUDE[reportcolumn_monthtodatespend](../reporting-api/includes/reportcolumn-monthtodatespend.md)]|

## <a name="requiredcolumns"></a>Required Columns
The report must include the following columns.

|Column|
|----------|
|AccountName|
|AccountNumber|
|CampaignName|
|CurrencyCode|
|Date|
[!INCLUDE[reportcolumn_statsrequired](../reporting-api/includes/reportcolumn-statsrequired.md)]
## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[BudgetSummaryReportRequest](../reporting-api/budgetsummaryreportrequest-data-object.md)

