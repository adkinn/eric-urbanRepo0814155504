---
title: "DSAAutoTargetPerformanceReportColumn Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e9ea903-2764-4a0b-a550-363f3bf8e9d0
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DSAAutoTargetPerformanceReportColumn Value Set
Defines the attributes and performance statistics columns that you can include in the [DSAAutoTargetPerformanceReportRequest](../reporting-api/dsaautotargetperformancereportrequest-data-object.md).

[!INCLUDE[reportcolumn_header](../reporting-api/includes/reportcolumn-header.md)]
## Syntax

```xml
<xs:simpleType name="DSAAutoTargetPerformanceReportColumn">
  <xs:restriction base="xs:string">
    <xs:enumeration value="TimePeriod"/>
    <xs:enumeration value="AccountName"/>
    <xs:enumeration value="AccountNumber"/>
    <xs:enumeration value="AccountId"/>
    <xs:enumeration value="AccountStatus"/>
    <xs:enumeration value="AdDistribution"/>
    <xs:enumeration value="CampaignName"/>
    <xs:enumeration value="CampaignId"/>
    <xs:enumeration value="CampaignStatus"/>
    <xs:enumeration value="AdGroupName"/>
    <xs:enumeration value="AdGroupId"/>
    <xs:enumeration value="AdGroupStatus"/>
    <xs:enumeration value="Language"/>
    <xs:enumeration value="Network"/>
    <xs:enumeration value="TopVsOther"/>
    <xs:enumeration value="DeviceType"/>
    <xs:enumeration value="DeviceOS"/>
    <xs:enumeration value="BidStrategyType"/>
    <xs:enumeration value="TrackingTemplate"/>
    <xs:enumeration value="CustomParameters"/>
    <xs:enumeration value="DynamicAdTarget"/>
    <xs:enumeration value="DynamicAdTargetId"/>
    <xs:enumeration value="WebsiteCoverage"/>
    <xs:enumeration value="Impressions"/>
    <xs:enumeration value="Clicks"/>
    <xs:enumeration value="Ctr"/>
    <xs:enumeration value="AverageCpc"/>
    <xs:enumeration value="Spend"/>
    <xs:enumeration value="AveragePosition"/>
    <xs:enumeration value="Conversions"/>
    <xs:enumeration value="ConversionRate"/>
    <xs:enumeration value="CostPerConversion"/>
    <xs:enumeration value="Assists"/>
    <xs:enumeration value="Revenue"/>
    <xs:enumeration value="ReturnOnAdSpend"/>
    <xs:enumeration value="CostPerAssist"/>
    <xs:enumeration value="RevenuePerConversion"/>
    <xs:enumeration value="RevenuePerAssist"/>
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
|AdDistribution|[!INCLUDE[reportcolumn_addistribution](../reporting-api/includes/reportcolumn-addistribution.md)]|
|AdGroupId|[!INCLUDE[reportcolumn_adgroupid](../reporting-api/includes/reportcolumn-adgroupid.md)]|
|AdGroupName|[!INCLUDE[reportcolumn_adgroupname](../reporting-api/includes/reportcolumn-adgroupname.md)]|
|AdGroupStatus|[!INCLUDE[reportcolumn_adgroupstatus](../reporting-api/includes/reportcolumn-adgroupstatus.md)]|
|Assists|[!INCLUDE[reportcolumn_assists](../reporting-api/includes/reportcolumn-assists.md)]|
|AverageCpc|[!INCLUDE[reportcolumn_averagecpc](../reporting-api/includes/reportcolumn-averagecpc.md)]|
|AveragePosition|[!INCLUDE[reportcolumn_averageposition](../reporting-api/includes/reportcolumn-averageposition.md)]|
|BidStrategyType|[!INCLUDE[reportcolumn_bidstrategytype](../reporting-api/includes/reportcolumn-bidstrategytype.md)]|
|CampaignId|[!INCLUDE[reportcolumn_campaignid](../reporting-api/includes/reportcolumn-campaignid.md)]|
|CampaignName|[!INCLUDE[reportcolumn_campaignname](../reporting-api/includes/reportcolumn-campaignname.md)]|
|CampaignStatus|[!INCLUDE[reportcolumn_campaignstatus](../reporting-api/includes/reportcolumn-campaignstatus.md)]|
|Clicks|[!INCLUDE[reportcolumn_clicks](../reporting-api/includes/reportcolumn-clicks.md)]|
|ConversionRate|[!INCLUDE[reportcolumn_conversionrate](../reporting-api/includes/reportcolumn-conversionrate.md)]|
|Conversions|[!INCLUDE[reportcolumn_conversions](../reporting-api/includes/reportcolumn-conversions.md)]|
|CostPerAssist|[!INCLUDE[reportcolumn_costperassist](../reporting-api/includes/reportcolumn-costperassist.md)]|
|CostPerConversion|[!INCLUDE[reportcolumn_costperconversion](../reporting-api/includes/reportcolumn-costperconversion.md)]|
|Ctr|[!INCLUDE[reportcolumn_ctr](../reporting-api/includes/reportcolumn-ctr.md)]|
|CustomParameters|The current custom parameters of the ad.|
|DeviceOS|[!INCLUDE[reportcolumn_deviceos](../reporting-api/includes/reportcolumn-deviceos.md)]|
|DeviceType|[!INCLUDE[reportcolumn_devicetype](../reporting-api/includes/reportcolumn-devicetype.md)]|
|DynamicAdTarget|[!INCLUDE[reportcolumn_dynamicadtarget](../reporting-api/includes/reportcolumn-dynamicadtarget.md)]|
|DynamicAdTargetId|[!INCLUDE[reportcolumn_dynamicadtargetid](../reporting-api/includes/reportcolumn-dynamicadtargetid.md)]|
|DynamicAdTargetStatus|[!INCLUDE[reportcolumn_dynamicadtargetstatus](../reporting-api/includes/reportcolumn-dynamicadtargetstatus.md)]|
|Impressions|[!INCLUDE[reportcolumn_impressions](../reporting-api/includes/reportcolumn-impressions.md)]|
|Language|[!INCLUDE[reportcolumn_language](../reporting-api/includes/reportcolumn-language.md)]|
|Network|[!INCLUDE[reportcolumn_network](../reporting-api/includes/reportcolumn-network.md)]|
|ReturnOnAdSpend|[!INCLUDE[reportcolumn_returnonadspend](../reporting-api/includes/reportcolumn-returnonadspend.md)]|
|Revenue|[!INCLUDE[reportcolumn_revenue](../reporting-api/includes/reportcolumn-revenue.md)]|
|RevenuePerAssist|[!INCLUDE[reportcolumn_revenueperassist](../reporting-api/includes/reportcolumn-revenueperassist.md)]|
|RevenuePerConversion|[!INCLUDE[reportcolumn_revenueperconversion](../reporting-api/includes/reportcolumn-revenueperconversion.md)]|
|Spend|[!INCLUDE[reportcolumn_spend](../reporting-api/includes/reportcolumn-spend.md)]|
|TimePeriod|[!INCLUDE[reportcolumn_timeperiod](../reporting-api/includes/reportcolumn-timeperiod.md)]|
|TopVsOther|[!INCLUDE[reportcolumn_topvsother](../reporting-api/includes/reportcolumn-topvsother.md)]|
|TrackingTemplate|The current tracking template of the ad. |
|WebsiteCoverage|[!INCLUDE[reportcolumn_websitecoverage](../reporting-api/includes/reportcolumn-websitecoverage.md)]|

## <a name="requiredcolumns"></a>Required Columns
The report must include the following columns.

|Column|
|----------|
|DynamicAdTargetId|
|TimePeriod<br/><br/>**Note**: This column is required for all aggregation types except Summary.|
[!INCLUDE[reportcolumn_statsrequired](../reporting-api/includes/reportcolumn-statsrequired.md)]

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]

## See Also
[DSAAutoTargetPerformanceReportRequest](../reporting-api/dsaautotargetperformancereportrequest-data-object.md)

