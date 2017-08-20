---
title: "AgeGenderDemographicReportColumn Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7fbdfc99-1ce8-4185-a606-1f10ab52848c
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AgeGenderDemographicReportColumn Value Set
Defines the attributes and performance statistics columns that you can include in the [AgeGenderDemographicReportRequest](../reporting-api/agegenderdemographicreportrequest-data-object.md).

[!INCLUDE[reportcolumn_header](../reporting-api/includes/reportcolumn-header.md)]
## Syntax

```xml
\<xs:simpleType name="AgeGenderDemographicReportColumn">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="AccountName"/>
    \<xs:enumeration value="AccountNumber"/>
    \<xs:enumeration value="AccountId"/>
    \<xs:enumeration value="TimePeriod"/>
    \<xs:enumeration value="CampaignName"/>
    \<xs:enumeration value="CampaignId"/>
    \<xs:enumeration value="AdGroupName"/>
    \<xs:enumeration value="AdGroupId"/>
    \<xs:enumeration value="AdDistribution"/>
    \<xs:enumeration value="AgeGroup"/>
    \<xs:enumeration value="Gender"/>
    \<xs:enumeration value="EstimatedImpressionPercent"/>
    \<xs:enumeration value="EstimatedClickPercent"/>
    \<xs:enumeration value="EstimatedCtr"/>
    \<xs:enumeration value="Language"/>
    \<xs:enumeration value="EstimatedImpressions"/>
    \<xs:enumeration value="EstimatedClicks"/>
    \<xs:enumeration value="EstimatedConversions"/>
    \<xs:enumeration value="EstimatedConversionRate"/>
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
|AdDistribution|[!INCLUDE[reportcolumn_addistribution](../reporting-api/includes/reportcolumn-addistribution.md)]|
|AdGroupId|[!INCLUDE[reportcolumn_adgroupid](../reporting-api/includes/reportcolumn-adgroupid.md)]|
|AdGroupName|[!INCLUDE[reportcolumn_adgroupname](../reporting-api/includes/reportcolumn-adgroupname.md)]|
|AdGroupStatus|[!INCLUDE[reportcolumn_adgroupstatus](../reporting-api/includes/reportcolumn-adgroupstatus.md)]|
|AgeGroup|[!INCLUDE[reportcolumn_agegroup](../reporting-api/includes/reportcolumn-agegroup.md)]|
|CampaignId|[!INCLUDE[reportcolumn_campaignid](../reporting-api/includes/reportcolumn-campaignid.md)]|
|CampaignName|[!INCLUDE[reportcolumn_campaignname](../reporting-api/includes/reportcolumn-campaignname.md)]|
|CampaignStatus|[!INCLUDE[reportcolumn_campaignstatus](../reporting-api/includes/reportcolumn-campaignstatus.md)]|
|EstimatedClickPercent|[!INCLUDE[reportcolumn_estimatedclickpercent](../reporting-api/includes/reportcolumn-estimatedclickpercent.md)]|
|EstimatedClicks|[!INCLUDE[reportcolumn_estimatedclicks](../reporting-api/includes/reportcolumn-estimatedclicks.md)]|
|EstimatedConversionRate|[!INCLUDE[reportcolumn_estimatedconversionrate](../reporting-api/includes/reportcolumn-estimatedconversionrate.md)]|
|EstimatedConversions|[!INCLUDE[reportcolumn_estimatedconversions](../reporting-api/includes/reportcolumn-estimatedconversions.md)]|
|EstimatedCtr|[!INCLUDE[reportcolumn_estimatedctr](../reporting-api/includes/reportcolumn-estimatedctr.md)]|
|EstimatedImpressionPercent|[!INCLUDE[reportcolumn_estimatedimpressionpercent](../reporting-api/includes/reportcolumn-estimatedimpressionpercent.md)]|
|EstimatedImpressions|[!INCLUDE[reportcolumn_estimatedimpressions](../reporting-api/includes/reportcolumn-estimatedimpressions.md)]|
|Gender|[!INCLUDE[reportcolumn_gender](../reporting-api/includes/reportcolumn-gender.md)]|
|Language|[!INCLUDE[reportcolumn_language](../reporting-api/includes/reportcolumn-language.md)]|
|TimePeriod|[!INCLUDE[reportcolumn_timeperiod](../reporting-api/includes/reportcolumn-timeperiod.md)]|

## <a name="requiredcolumns"></a>Required Columns
The following columns are required (you must include these columns in your age and gender demographic report request).

|Column|
|----------|
|AccountName|
|AdGroupName|
|AgeGroup|
|Gender|
|TimePeriod<br /><br />**Note**: This column is required for all aggregation types except Summary.|
[!INCLUDE[reportcolumn_statsrequired](../reporting-api/includes/reportcolumn-statsrequired.md)]
## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[AgeGenderDemographicReportRequest](../reporting-api/agegenderdemographicreportrequest-data-object.md)

