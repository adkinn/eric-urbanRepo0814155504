---
title: "ConversionPerformanceReportColumn Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b82998c3-78a4-4baf-a2bb-a438ea9b90d4
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ConversionPerformanceReportColumn Value Set
Defines the attributes and performance statistics columns that you can include in the [ConversionPerformanceReportRequest](../reporting-api/conversionperformancereportrequest-data-object.md).

[!INCLUDE[reportcolumn_header](../reporting-api/includes/reportcolumn-header.md)]
## Syntax

```xml
<xs:simpleType name="ConversionPerformanceReportColumn">
  <xs:restriction base="xs:string">
    <xs:enumeration value="AccountName" />
    <xs:enumeration value="AccountNumber" />
    <xs:enumeration value="AccountId" />
    <xs:enumeration value="TimePeriod" />
    <xs:enumeration value="CampaignName" />
    <xs:enumeration value="CampaignId" />
    <xs:enumeration value="AdGroupName" />
    <xs:enumeration value="AdGroupId" />
    <xs:enumeration value="Keyword" />
    <xs:enumeration value="KeywordId" />
    <xs:enumeration value="Impressions" />
    <xs:enumeration value="Clicks" />
    <xs:enumeration value="Ctr" />
    <xs:enumeration value="Assists" />
    <xs:enumeration value="Conversions" />
    <xs:enumeration value="ConversionRate" />
    <xs:enumeration value="Spend" />
    <xs:enumeration value="Revenue" />
    <xs:enumeration value="ReturnOnAdSpend" />
    <xs:enumeration value="CostPerConversion" />
    <xs:enumeration value="CostPerAssist" />
    <xs:enumeration value="RevenuePerConversion" />
    <xs:enumeration value="RevenuePerAssist" />
    <xs:enumeration value="DeviceType" />
    <xs:enumeration value="AccountStatus"/>
    <xs:enumeration value="CampaignStatus"/>
    <xs:enumeration value="AdGroupStatus"/>
    <xs:enumeration value="KeywordStatus"/>
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|AccountId|[!INCLUDE[reportcolumn_accountid](../reporting-api/includes/reportcolumn-accountid.md)]|
|AccountName|[!INCLUDE[reportcolumn_accountname](../reporting-api/includes/reportcolumn-accountname.md)]|
|AccountNumber|[!INCLUDE[reportcolumn_accountnumber](../reporting-api/includes/reportcolumn-accountnumber.md)]|
|AccountStatus|[!INCLUDE[reportcolumn_accountstatus](../reporting-api/includes/reportcolumn-accountstatus.md)]|
|AdGroupId|[!INCLUDE[reportcolumn_adgroupid](../reporting-api/includes/reportcolumn-adgroupid.md)]|
|AdGroupName|[!INCLUDE[reportcolumn_adgroupname](../reporting-api/includes/reportcolumn-adgroupname.md)]|
|AdGroupStatus|[!INCLUDE[reportcolumn_adgroupstatus](../reporting-api/includes/reportcolumn-adgroupstatus.md)]|
|Assists|[!INCLUDE[reportcolumn_assists](../reporting-api/includes/reportcolumn-assists.md)]|
|CampaignId|[!INCLUDE[reportcolumn_campaignid](../reporting-api/includes/reportcolumn-campaignid.md)]|
|CampaignName|[!INCLUDE[reportcolumn_campaignname](../reporting-api/includes/reportcolumn-campaignname.md)]|
|CampaignStatus|[!INCLUDE[reportcolumn_campaignstatus](../reporting-api/includes/reportcolumn-campaignstatus.md)]|
|Clicks|[!INCLUDE[reportcolumn_clicks](../reporting-api/includes/reportcolumn-clicks.md)]|
|ConversionRate|[!INCLUDE[reportcolumn_conversionrate](../reporting-api/includes/reportcolumn-conversionrate.md)]|
|Conversions|[!INCLUDE[reportcolumn_conversions](../reporting-api/includes/reportcolumn-conversions.md)]|
|CostPerAssist|[!INCLUDE[reportcolumn_costperassist](../reporting-api/includes/reportcolumn-costperassist.md)]|
|CostPerConversion|[!INCLUDE[reportcolumn_costperconversion](../reporting-api/includes/reportcolumn-costperconversion.md)]|
|Ctr|[!INCLUDE[reportcolumn_ctr](../reporting-api/includes/reportcolumn-ctr.md)]|
|DeviceType|[!INCLUDE[reportcolumn_devicetype](../reporting-api/includes/reportcolumn-devicetype.md)]|
|Impressions|[!INCLUDE[reportcolumn_impressions](../reporting-api/includes/reportcolumn-impressions.md)]|
|Keyword|[!INCLUDE[reportcolumn_keyword](../reporting-api/includes/reportcolumn-keyword.md)]|
|KeywordId|[!INCLUDE[reportcolumn_keywordid](../reporting-api/includes/reportcolumn-keywordid.md)]|
|KeywordStatus|[!INCLUDE[reportcolumn_keywordstatus](../reporting-api/includes/reportcolumn-keywordstatus.md)]|
|ReturnOnAdSpend|[!INCLUDE[reportcolumn_returnonadspend](../reporting-api/includes/reportcolumn-returnonadspend.md)]|
|Revenue|[!INCLUDE[reportcolumn_revenue](../reporting-api/includes/reportcolumn-revenue.md)]|
|RevenuePerAssist|[!INCLUDE[reportcolumn_revenueperassist](../reporting-api/includes/reportcolumn-revenueperassist.md)]|
|RevenuePerConversion|[!INCLUDE[reportcolumn_revenueperconversion](../reporting-api/includes/reportcolumn-revenueperconversion.md)]|
|Spend|[!INCLUDE[reportcolumn_spend](../reporting-api/includes/reportcolumn-spend.md)]|
|TimePeriod|[!INCLUDE[reportcolumn_timeperiod](../reporting-api/includes/reportcolumn-timeperiod.md)]|

## <a name="requiredcolumns"></a>Required Columns
The report must include the following columns.

|Column|
|----------|
|TimePeriod<br /><br />**Note**: This column is required for all aggregation types except Summary.|
[!INCLUDE[reportcolumn_statsrequired](../reporting-api/includes/reportcolumn-statsrequired.md)]
## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[ConversionPerformanceReportRequest](../reporting-api/conversionperformancereportrequest-data-object.md)

