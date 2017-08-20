---
title: "AudiencePerformanceReportColumn Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 65f83b99-da31-455e-a85b-da1b47fc9ca0
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AudiencePerformanceReportColumn Value Set
Defines the attributes and performance statistics columns that you can include in the [AudiencePerformanceReportRequest](../reporting-api/audienceperformancereportrequest-data-object.md).

[!INCLUDE[reportcolumn_header](../reporting-api/includes/reportcolumn-header.md)]
## Syntax

```xml
\<xs:simpleType name="AudiencePerformanceReportColumn">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="AccountName"/>
    \<xs:enumeration value="AccountNumber"/>
    \<xs:enumeration value="AccountId"/>
    \<xs:enumeration value="TimePeriod"/>
    \<xs:enumeration value="CampaignName"/>
    \<xs:enumeration value="CampaignId"/>
    \<xs:enumeration value="AdGroupName"/>
    \<xs:enumeration value="AdGroupId"/>
    \<xs:enumeration value="AudienceId"/>
    \<xs:enumeration value="AudienceName"/>
    \<xs:enumeration value="AssociationStatus" />
    \<xs:enumeration value="BidAdjustment"/>
    \<xs:enumeration value="TargetingSetting" /> 
    \<xs:enumeration value="Impressions"/>
    \<xs:enumeration value="Clicks"/>
    \<xs:enumeration value="Ctr"/>
    \<xs:enumeration value="AverageCpc"/>
    \<xs:enumeration value="Spend"/>
    \<xs:enumeration value="AveragePosition"/>
    \<xs:enumeration value="Conversions"/>
    \<xs:enumeration value="ConversionRate"/>
    \<xs:enumeration value="CostPerConversion"/>
    \<xs:enumeration value="Revenue"/>
    \<xs:enumeration value="ReturnOnAdSpend" /> 
    \<xs:enumeration value="RevenuePerConversion" />
    \<xs:enumeration value="AccountStatus"/>
    \<xs:enumeration value="CampaignStatus"/>
    \<xs:enumeration value="AdGroupStatus"/> 
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
|AdGroupId|[!INCLUDE[reportcolumn_adgroupid](../reporting-api/includes/reportcolumn-adgroupid.md)]|
|AdGroupName|[!INCLUDE[reportcolumn_adgroupname](../reporting-api/includes/reportcolumn-adgroupname.md)]|
|AdGroupStatus|[!INCLUDE[reportcolumn_adgroupstatus](../reporting-api/includes/reportcolumn-adgroupstatus.md)]|
|AssociationStatus|[!INCLUDE[reportcolumn_associationstatus](../reporting-api/includes/reportcolumn-associationstatus.md)]|
|AudienceId|[!INCLUDE[reportcolumn_AudienceId](../reporting-api/includes/reportcolumn-audienceid.md)]|
|AudienceName|[!INCLUDE[reportcolumn_AudienceName](../reporting-api/includes/reportcolumn-audiencename.md)]|
|Assists|[!INCLUDE[reportcolumn_assists](../reporting-api/includes/reportcolumn-assists.md)]|
|AverageCpc|[!INCLUDE[reportcolumn_averagecpc](../reporting-api/includes/reportcolumn-averagecpc.md)]|
|AveragePosition|[!INCLUDE[reportcolumn_averageposition](../reporting-api/includes/reportcolumn-averageposition.md)]|
|BidAdjustment|[!INCLUDE[reportcolumn_bidadjustment](../reporting-api/includes/reportcolumn-bidadjustment.md)]|
|CampaignId|[!INCLUDE[reportcolumn_campaignid](../reporting-api/includes/reportcolumn-campaignid.md)]|
|CampaignName|[!INCLUDE[reportcolumn_campaignname](../reporting-api/includes/reportcolumn-campaignname.md)]|
|CampaignStatus|[!INCLUDE[reportcolumn_campaignstatus](../reporting-api/includes/reportcolumn-campaignstatus.md)]|
|Clicks|[!INCLUDE[reportcolumn_clicks](../reporting-api/includes/reportcolumn-clicks.md)]|
|ConversionRate|[!INCLUDE[reportcolumn_conversionrate](../reporting-api/includes/reportcolumn-conversionrate.md)]|
|Conversions|[!INCLUDE[reportcolumn_conversions](../reporting-api/includes/reportcolumn-conversions.md)]|
|CostPerConversion|[!INCLUDE[reportcolumn_costperconversion](../reporting-api/includes/reportcolumn-costperconversion.md)]|
|Ctr|[!INCLUDE[reportcolumn_ctr](../reporting-api/includes/reportcolumn-ctr.md)]|
|Impressions|[!INCLUDE[reportcolumn_impressions](../reporting-api/includes/reportcolumn-impressions.md)]|
|ReturnOnAdSpend|[!INCLUDE[reportcolumn_returnonadspend](../reporting-api/includes/reportcolumn-returnonadspend.md)]|
|Revenue|[!INCLUDE[reportcolumn_revenue](../reporting-api/includes/reportcolumn-revenue.md)]|
|RevenuePerConversion|[!INCLUDE[reportcolumn_revenueperconversion](../reporting-api/includes/reportcolumn-revenueperconversion.md)]|
|Spend|[!INCLUDE[reportcolumn_spend](../reporting-api/includes/reportcolumn-spend.md)]|
|TargetingSetting|[!INCLUDE[reportcolumn_TargetingSetting](../reporting-api/includes/reportcolumn-targetingsetting.md)]|
|TimePeriod|[!INCLUDE[reportcolumn_timeperiod](../reporting-api/includes/reportcolumn-timeperiod.md)]|

## <a name="requiredcolumns"></a>Required Columns
The report must include the following columns.

|Column|
|----------|
|AccountId|
|AudienceId|
|TimePeriod<br /><br />**Note**: This column is required for all aggregation types except Summary.|
[!INCLUDE[reportcolumn_statsrequired](../reporting-api/includes/reportcolumn-statsrequired.md)]
## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[AudiencePerformanceReportRequest](../reporting-api/audienceperformancereportrequest-data-object.md)

