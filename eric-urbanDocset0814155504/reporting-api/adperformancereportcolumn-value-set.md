---
title: "AdPerformanceReportColumn Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b4fbf86e-c7fb-45e9-ab08-9df7458b6bda
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdPerformanceReportColumn Value Set
Defines the attributes and performance statistics columns that you can include in the [AdPerformanceReportRequest](../reporting-api/adperformancereportrequest-data-object.md).

[!INCLUDE[reportcolumn_header](../reporting-api/includes/reportcolumn-header.md)]
## Syntax

```xml
<xs:simpleType name="AdPerformanceReportColumn">
  <xs:restriction base="xs:string">
    <xs:enumeration value="AccountName"/>
    <xs:enumeration value="AccountNumber"/>
    <xs:enumeration value="AccountId"/>
    <xs:enumeration value="CampaignName"/>
    <xs:enumeration value="CampaignId"/>
    <xs:enumeration value="AdGroupName"/>
    <xs:enumeration value="AdId"/>
    <xs:enumeration value="AdGroupId"/>
    <xs:enumeration value="AdTitle"/>
    <xs:enumeration value="AdDescription"/>
    <xs:enumeration value="AdType"/>
    <xs:enumeration value="CurrencyCode"/>
    <xs:enumeration value="AdDistribution"/>
    <xs:enumeration value="Impressions"/>
    <xs:enumeration value="Clicks"/>
    <xs:enumeration value="Ctr"/>
    <xs:enumeration value="AverageCpc"/>
    <xs:enumeration value="Spend"/>
    <xs:enumeration value="AveragePosition"/>
    <xs:enumeration value="Conversions"/>
    <xs:enumeration value="ConversionRate"/>
    <xs:enumeration value="CostPerConversion"/>
    <xs:enumeration value="DestinationUrl"/>
    <xs:enumeration value="DeviceType"/>
    <xs:enumeration value="Language"/>
    <xs:enumeration value="DisplayUrl"/>
    <xs:enumeration value="BusinessListingId"/> 
    <xs:enumeration value="BusinessListingName"/>
    <xs:enumeration value="BusinessCategoryId"/> 
    <xs:enumeration value="BusinessCategoryName"/> 
    <xs:enumeration value="AdStatus"/> 
    <xs:enumeration value="Network"/> 
    <xs:enumeration value="TopVsOther"/>
    <xs:enumeration value="BidMatchType"/>
    <xs:enumeration value="DeliveredMatchType"/>
    <xs:enumeration value="DeviceOS"/>
    <xs:enumeration value="Assists"/> 
    <xs:enumeration value="Revenue"/> 
    <xs:enumeration value="ReturnOnAdSpend"/> 
    <xs:enumeration value="CostPerAssist"/> 
    <xs:enumeration value="RevenuePerConversion"/> 
    <xs:enumeration value="RevenuePerAssist"/>
    <xs:enumeration value="TrackingTemplate"/> 
    <xs:enumeration value="CustomParameters"/> 
    <xs:enumeration value="FinalURL"/>
    <xs:enumeration value="FinalMobileURL"/> 
    <xs:enumeration value="FinalAppURL"/>
    <xs:enumeration value="AccountStatus"/>
    <xs:enumeration value="CampaignStatus"/>
    <xs:enumeration value="AdGroupStatus"/>
    <xs:enumeration value="TitlePart1"/>
    <xs:enumeration value="TitlePart2"/>
    <xs:enumeration value="Path1"/>
    <xs:enumeration value="Path2"/> 
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
|AdDescription|[!INCLUDE[reportcolumn_addescription](../reporting-api/includes/reportcolumn-addescription.md)]|
|AdDistribution|[!INCLUDE[reportcolumn_addistribution](../reporting-api/includes/reportcolumn-addistribution.md)]|
|AdGroupId|[!INCLUDE[reportcolumn_adgroupid](../reporting-api/includes/reportcolumn-adgroupid.md)]|
|AdGroupName|[!INCLUDE[reportcolumn_adgroupname](../reporting-api/includes/reportcolumn-adgroupname.md)]|
|AdGroupStatus|[!INCLUDE[reportcolumn_adgroupstatus](../reporting-api/includes/reportcolumn-adgroupstatus.md)]|
|AdId|[!INCLUDE[reportcolumn_adid](../reporting-api/includes/reportcolumn-adid.md)]|
|AdStatus|[!INCLUDE[reportcolumn_adstatus](../reporting-api/includes/reportcolumn-adstatus.md)]|
|AdTitle|[!INCLUDE[reportcolumn_adtitle](../reporting-api/includes/reportcolumn-adtitle.md)]|
|AdType|[!INCLUDE[reportcolumn_adtype](../reporting-api/includes/reportcolumn-adtype.md)]|
|Assists|[!INCLUDE[reportcolumn_assists](../reporting-api/includes/reportcolumn-assists.md)]|
|AverageCpc|[!INCLUDE[reportcolumn_averagecpc](../reporting-api/includes/reportcolumn-averagecpc.md)]|
|AveragePosition|[!INCLUDE[reportcolumn_averageposition](../reporting-api/includes/reportcolumn-averageposition.md)]|
|BidMatchType|[!INCLUDE[reportcolumn_bidmatchtype](../reporting-api/includes/reportcolumn-bidmatchtype.md)]|
|BusinessCategoryId|Reserved for internal use.|
|BusinessCategoryName|Reserved for internal use.|
|BusinessListingId|Reserved for internal use.|
|BusinessListingName|Reserved for internal use.|
|CampaignId|[!INCLUDE[reportcolumn_campaignid](../reporting-api/includes/reportcolumn-campaignid.md)]|
|CampaignName|[!INCLUDE[reportcolumn_campaignname](../reporting-api/includes/reportcolumn-campaignname.md)]|
|CampaignStatus|[!INCLUDE[reportcolumn_campaignstatus](../reporting-api/includes/reportcolumn-campaignstatus.md)]|
|Clicks|[!INCLUDE[reportcolumn_clicks](../reporting-api/includes/reportcolumn-clicks.md)]|
|ConversionRate|[!INCLUDE[reportcolumn_conversionrate](../reporting-api/includes/reportcolumn-conversionrate.md)]|
|Conversions|[!INCLUDE[reportcolumn_conversions](../reporting-api/includes/reportcolumn-conversions.md)]|
|CostPerAssist|[!INCLUDE[reportcolumn_costperassist](../reporting-api/includes/reportcolumn-costperassist.md)]|
|CostPerConversion|[!INCLUDE[reportcolumn_costperconversion](../reporting-api/includes/reportcolumn-costperconversion.md)]|
|Ctr|[!INCLUDE[reportcolumn_ctr](../reporting-api/includes/reportcolumn-ctr.md)]|
|CurrencyCode|[!INCLUDE[reportcolumn_currencycode](../reporting-api/includes/reportcolumn-currencycode.md)]|
|CustomParameters|The current custom parameters set of the ad, keyword, or criterion.<br /><br />Each custom parameter is a key and value pair. The list of custom parameters is semicolon-delimited and each key is enclosed by braces and a leading underscore, for example `{_key1}=value1;{_key2}=value2`.|
|DeliveredMatchType|[!INCLUDE[reportcolumn_deliveredmatchtype](../reporting-api/includes/reportcolumn-deliveredmatchtype.md)]|
|DestinationUrl|[!INCLUDE[reportcolumn_destinationurl](../reporting-api/includes/reportcolumn-destinationurl.md)]|
|DeviceOS|[!INCLUDE[reportcolumn_deviceos](../reporting-api/includes/reportcolumn-deviceos.md)]|
|DeviceType|[!INCLUDE[reportcolumn_devicetype](../reporting-api/includes/reportcolumn-devicetype.md)]|
|DisplayUrl|[!INCLUDE[reportcolumn_displayurl](../reporting-api/includes/reportcolumn-displayurl.md)]|
|FinalAppURL|Reserved for future use.|
|FinalMobileURL|The Final Mobile URL of the ad, keyword, or criterion.<br /><br />Only the first URL in the list is reported. If the URL contains dynamic text substitution parameters (for example, {param1}), the report will contain the URL before substitution.|
|FinalURL|The Final URL of the ad, keyword, or criterion.<br /><br />Only the first URL in the list is reported. If the URL contains dynamic text substitution parameters (for example, {param1}), the report will contain the URL before substitution.|
|Impressions|[!INCLUDE[reportcolumn_impressions](../reporting-api/includes/reportcolumn-impressions.md)]|
|Language|[!INCLUDE[reportcolumn_language](../reporting-api/includes/reportcolumn-language.md)]|
|Network|[!INCLUDE[reportcolumn_network](../reporting-api/includes/reportcolumn-network.md)]|
|Path1|[!INCLUDE[reportcolumn_path1](../reporting-api/includes/reportcolumn-path1.md)]|
|Path2|[!INCLUDE[reportcolumn_path2](../reporting-api/includes/reportcolumn-path2.md)]|
|ReturnOnAdSpend|[!INCLUDE[reportcolumn_returnonadspend](../reporting-api/includes/reportcolumn-returnonadspend.md)]|
|Revenue|[!INCLUDE[reportcolumn_revenue](../reporting-api/includes/reportcolumn-revenue.md)]|
|RevenuePerAssist|[!INCLUDE[reportcolumn_revenueperassist](../reporting-api/includes/reportcolumn-revenueperassist.md)]|
|RevenuePerConversion|[!INCLUDE[reportcolumn_revenueperconversion](../reporting-api/includes/reportcolumn-revenueperconversion.md)]|
|Spend|[!INCLUDE[reportcolumn_spend](../reporting-api/includes/reportcolumn-spend.md)]|
|TimePeriod|[!INCLUDE[reportcolumn_timeperiod](../reporting-api/includes/reportcolumn-timeperiod.md)]|
|TitlePart1|[!INCLUDE[reportcolumn_titlepart1](../reporting-api/includes/reportcolumn-titlepart1.md)]|
|TitlePart2|[!INCLUDE[reportcolumn_titlepart2](../reporting-api/includes/reportcolumn-titlepart2.md)]|
|TopVsOther|[!INCLUDE[reportcolumn_topvsother](../reporting-api/includes/reportcolumn-topvsother.md)]|
|TrackingTemplate|The current tracking template of the ad, keyword, or criterion.|

## <a name="requiredcolumns"></a>Required Columns
The report must include the following columns.

|Column|
|----------|
|TimePeriod<br /><br />**Note**: This column is required for all aggregation types except Summary.|
[!INCLUDE[reportcolumn_statsrequired](../reporting-api/includes/reportcolumn-statsrequired.md)]
## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[AdPerformanceReportRequest](../reporting-api/adperformancereportrequest-data-object.md)  

