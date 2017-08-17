---
title: "ProductSearchQueryPerformanceReportColumn Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1fed4d50-2d97-498f-ad99-fda5bab7049e
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
---
# ProductSearchQueryPerformanceReportColumn Value Set
Defines the attributes and performance statistics columns that you can include in the [ProductSearchQueryPerformanceReportRequest](../reporting-api/productsearchqueryperformancereportrequest-data-object.md).

The report will include data only for search terms that resulted in a significant number of clicks in the last 30 days.

[!INCLUDE[reportcolumn_header](../reporting-api/includes/reportcolumn-header.md)]
## Syntax

```xml
\<xs:simpleType name="ProductSearchQueryPerformanceReportColumn">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="TimePeriod" />
    \<xs:enumeration value="AccountName" />
    \<xs:enumeration value="AccountNumber" />
    \<xs:enumeration value="AccountId" />
    \<xs:enumeration value="AccountStatus"/>
    \<xs:enumeration value="CampaignName" />
    \<xs:enumeration value="CampaignId" />
    \<xs:enumeration value="CampaignStatus" />
    \<xs:enumeration value="AdGroupName" />
    \<xs:enumeration value="AdGroupId" />
    \<xs:enumeration value="AdGroupStatus"/>
    \<xs:enumeration value="AdId" />
    \<xs:enumeration value="Language"/>
    \<xs:enumeration value="Network"/>
    \<xs:enumeration value="DeviceType" />
    \<xs:enumeration value="DeviceOS"/>
    \<xs:enumeration value="SearchQuery" />
    \<xs:enumeration value="MerchantProductId"/>
    \<xs:enumeration value="AdGroupCriterionId"/>
    \<xs:enumeration value="Title"/>
    \<xs:enumeration value="DestinationUrl" />
    \<xs:enumeration value="PartitionType"/>
    \<xs:enumeration value="ProductGroup"/>
    \<xs:enumeration value="ClickTypeId" />
    \<xs:enumeration value="ClickType" />
    \<xs:enumeration value="Impressions" />
    \<xs:enumeration value="Clicks" />
    \<xs:enumeration value="Ctr" />
    \<xs:enumeration value="AverageCpc" />
    \<xs:enumeration value="Spend" />
    \<xs:enumeration value="AveragePosition" />
    \<xs:enumeration value="Conversions" />
    \<xs:enumeration value="ConversionRate" />
    \<xs:enumeration value="CostPerConversion" />
    \<xs:enumeration value="Assists" />
    \<xs:enumeration value="Revenue" />
    \<xs:enumeration value="ReturnOnAdSpend" />
    \<xs:enumeration value="CostPerAssist"/>
    \<xs:enumeration value="RevenuePerConversion" />
    \<xs:enumeration value="RevenuePerAssist" />
    \<xs:enumeration value="TotalClicksOnAdElements" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|AccountId|[!INCLUDE[reportcolumn_accountid](../reporting-api/includes/reportcolumn-accountid.md)]|
|AccountName|[!INCLUDE[reportcolumn_accountname](../reporting-api/includes/reportcolumn-accountname.md)]|
|AccountNumber|[!INCLUDE[reportcolumn_accountnumber](../reporting-api/includes/reportcolumn-accountnumber.md)]|
|AccountStatus|[!INCLUDE[reportcolumn_accountstatus](../reporting-api/includes/reportcolumn-accountstatus.md)]|
|AdGroupCriterionId|[!INCLUDE[reportcolumn_adgroupcriterionid](../reporting-api/includes/reportcolumn-adgroupcriterionid.md)]|
|AdGroupId|[!INCLUDE[reportcolumn_adgroupid](../reporting-api/includes/reportcolumn-adgroupid.md)]|
|AdGroupName|[!INCLUDE[reportcolumn_adgroupname](../reporting-api/includes/reportcolumn-adgroupname.md)]|
|AdGroupStatus|[!INCLUDE[reportcolumn_adgroupstatus](../reporting-api/includes/reportcolumn-adgroupstatus.md)]|
|AdId|[!INCLUDE[reportcolumn_adid](../reporting-api/includes/reportcolumn-adid.md)]|
|Assists|[!INCLUDE[reportcolumn_assists](../reporting-api/includes/reportcolumn-assists.md)]|
|AverageCpc|[!INCLUDE[reportcolumn_averagecpc](../reporting-api/includes/reportcolumn-averagecpc.md)]|
|AveragePosition|[!INCLUDE[reportcolumn_averageposition](../reporting-api/includes/reportcolumn-averageposition.md)]|
|CampaignId|[!INCLUDE[reportcolumn_campaignid](../reporting-api/includes/reportcolumn-campaignid.md)]|
|CampaignName|[!INCLUDE[reportcolumn_campaignname](../reporting-api/includes/reportcolumn-campaignname.md)]|
|CampaignStatus|[!INCLUDE[reportcolumn_campaignstatus](../reporting-api/includes/reportcolumn-campaignstatus.md)]|
|Clicks|[!INCLUDE[reportcolumn_clicks](../reporting-api/includes/reportcolumn-clicks.md)]|
|ClickType|[!INCLUDE[reportcolumn_clicktype](../reporting-api/includes/reportcolumn-clicktype.md)]|
|ClickTypeId|[!INCLUDE[reportcolumn_clicktypeid](../reporting-api/includes/reportcolumn-clicktypeid.md)]|
|ConversionRate|[!INCLUDE[reportcolumn_conversionrate](../reporting-api/includes/reportcolumn-conversionrate.md)]|
|Conversions|[!INCLUDE[reportcolumn_conversions](../reporting-api/includes/reportcolumn-conversions.md)]|
|CostPerAssist|[!INCLUDE[reportcolumn_costperassist](../reporting-api/includes/reportcolumn-costperassist.md)]|
|CostPerConversion|[!INCLUDE[reportcolumn_costperconversion](../reporting-api/includes/reportcolumn-costperconversion.md)]|
|Ctr|[!INCLUDE[reportcolumn_ctr](../reporting-api/includes/reportcolumn-ctr.md)]|
|DestinationUrl|[!INCLUDE[reportcolumn_destinationurl](../reporting-api/includes/reportcolumn-destinationurl.md)]|
|DeviceOS|[!INCLUDE[reportcolumn_deviceos](../reporting-api/includes/reportcolumn-deviceos.md)]|
|DeviceType|[!INCLUDE[reportcolumn_devicetype](../reporting-api/includes/reportcolumn-devicetype.md)]|
|Impressions|[!INCLUDE[reportcolumn_impressions](../reporting-api/includes/reportcolumn-impressions.md)]|
|Language|[!INCLUDE[reportcolumn_language](../reporting-api/includes/reportcolumn-language.md)]|
|MerchantProductId|[!INCLUDE[reportcolumn_merchantproductid](../reporting-api/includes/reportcolumn-merchantproductid.md)]|
|Network|[!INCLUDE[reportcolumn_network](../reporting-api/includes/reportcolumn-network.md)]|
|PartitionType|[!INCLUDE[reportcolumn_partitiontype](../reporting-api/includes/reportcolumn-partitiontype.md)]|
|ProductGroup|[!INCLUDE[reportcolumn_productgroup](../reporting-api/includes/reportcolumn-productgroup.md)]|
|ReturnOnAdSpend|[!INCLUDE[reportcolumn_returnonadspend](../reporting-api/includes/reportcolumn-returnonadspend.md)]|
|Revenue|[!INCLUDE[reportcolumn_revenue](../reporting-api/includes/reportcolumn-revenue.md)]|
|RevenuePerAssist|[!INCLUDE[reportcolumn_revenueperassist](../reporting-api/includes/reportcolumn-revenueperassist.md)]|
|RevenuePerConversion|[!INCLUDE[reportcolumn_revenueperconversion](../reporting-api/includes/reportcolumn-revenueperconversion.md)]|
|SearchQuery|[!INCLUDE[reportcolumn_searchquery](../reporting-api/includes/reportcolumn-searchquery.md)]|
|Spend|[!INCLUDE[reportcolumn_spend](../reporting-api/includes/reportcolumn-spend.md)]|
|TimePeriod|[!INCLUDE[reportcolumn_timeperiod](../reporting-api/includes/reportcolumn-timeperiod.md)]|
|Title|[!INCLUDE[reportcolumn_title](../reporting-api/includes/reportcolumn-title.md)]|
|TotalClicksOnAdElements|[!INCLUDE[reportcolumn_totalclicksonadelements](../reporting-api/includes/reportcolumn-totalclicksonadelements.md)]|

## <a name="requiredcolumns"></a>Required Columns
The report must include the following columns.

|Column|
|----------|
|CampaignId|
|MerchantProductId|
|SearchQuery|
|TimePeriod<br /><br />**Note**: This column is required for all aggregation types except Summary.|
[!INCLUDE[reportcolumn_statsrequired](../reporting-api/includes/reportcolumn-statsrequired.md)]

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]

## See Also
[ProductSearchQueryPerformanceReportRequest](../reporting-api/productsearchqueryperformancereportrequest-data-object.md)

