---
title: "AdGroupPerformanceReportColumn Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0ebb4532-439c-4708-abe3-2993507336b8
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdGroupPerformanceReportColumn Value Set
Defines the attributes and performance statistics columns that you can include in the [AdGroupPerformanceReportRequest](../reporting-api/adgroupperformancereportrequest-data-object.md).

[!INCLUDE[reportcolumn_header](../reporting-api/includes/reportcolumn-header.md)]
## Syntax

```xml
<xs:simpleType name="AdGroupPerformanceReportColumn">
  <xs:restriction base="xs:string">
    <xs:enumeration value="AccountName"/>
    <xs:enumeration value="AccountNumber"/>
    <xs:enumeration value="AccountId"/>
    <xs:enumeration value="TimePeriod"/>
    <xs:enumeration value="Status"/>
    <xs:enumeration value="CampaignName"/>
    <xs:enumeration value="CampaignId"/>
    <xs:enumeration value="AdGroupName"/>
    <xs:enumeration value="AdGroupId"/>
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
    <xs:enumeration value="DeviceType" />
    <xs:enumeration value="Language"/>
    <xs:enumeration value="DeviceOS" /> 
    <xs:enumeration value="ImpressionSharePercent" /> 
    <xs:enumeration value="ImpressionLostToBudgetPercent" /> 
    <xs:enumeration value="ImpressionLostToRankPercent" /> 
    <xs:enumeration value="QualityScore" /> 
    <xs:enumeration value="ExpectedCtr" /> 
    <xs:enumeration value="AdRelevance" /> 
    <xs:enumeration value="LandingPageExperience" /> 
    <xs:enumeration value="HistoricQualityScore" /> 
    <xs:enumeration value="HistoricExpectedCtr" /> 
    <xs:enumeration value="HistoricAdRelevance" /> 
    <xs:enumeration value="HistoricLandingPageExperience" /> 
    <xs:enumeration value="ImpressionLostToBidPercent" />
    <xs:enumeration value="ImpressionLostToAdRelevancePercent" />
    <xs:enumeration value="ImpressionLostToExpectedCtrPercent" />
    <xs:enumeration value="BusinessListingId" /> 
    <xs:enumeration value="BusinessListingName"/>
    <xs:enumeration value="BusinessCategoryId" /> 
    <xs:enumeration value="BusinessCategoryName" /> 
    <xs:enumeration value="PhoneImpressions" /> 
    <xs:enumeration value="PhoneCalls" />
    <xs:enumeration value="ManualCalls" /> 
    <xs:enumeration value="ClickCalls" /> 
    <xs:enumeration value="Ptr" /> 
    <xs:enumeration value="AverageCpp" /> 
    <xs:enumeration value="Network" /> 
    <xs:enumeration value="TopVsOther" /> 
    <xs:enumeration value="BidMatchType" />
    <xs:enumeration value="DeliveredMatchType" /> 
    <xs:enumeration value="Assists" /> 
    <xs:enumeration value="Revenue"/>
    <xs:enumeration value="ReturnOnAdSpend" /> 
    <xs:enumeration value="CostPerAssist"/>
    <xs:enumeration value="RevenuePerConversion" /> 
    <xs:enumeration value="RevenuePerAssist" />
    <xs:enumeration value="TrackingTemplate"/>
    <xs:enumeration value="CustomParameters"/>
    <xs:enumeration value="AccountStatus"/>
    <xs:enumeration value="CampaignStatus"/> 
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
|AdRelevance|[!INCLUDE[reportcolumn_adrelevance](../reporting-api/includes/reportcolumn-adrelevance.md)]|
|Assists|[!INCLUDE[reportcolumn_assists](../reporting-api/includes/reportcolumn-assists.md)]|
|AverageCpc|[!INCLUDE[reportcolumn_averagecpc](../reporting-api/includes/reportcolumn-averagecpc.md)]|
|AverageCpp|[!INCLUDE[reportcolumn_averagecpp](../reporting-api/includes/reportcolumn-averagecpp.md)]|
|AveragePosition|[!INCLUDE[reportcolumn_averageposition](../reporting-api/includes/reportcolumn-averageposition.md)]|
|BidMatchType|[!INCLUDE[reportcolumn_bidmatchtype](../reporting-api/includes/reportcolumn-bidmatchtype.md)]|
|BusinessCategoryId|Reserved for internal use.|
|BusinessCategoryName|Reserved for internal use.|
|BusinessListingId|Reserved for internal use.|
|BusinessListingName|Reserved for internal use.|
|CampaignId|[!INCLUDE[reportcolumn_campaignid](../reporting-api/includes/reportcolumn-campaignid.md)]|
|CampaignName|[!INCLUDE[reportcolumn_campaignname](../reporting-api/includes/reportcolumn-campaignname.md)]|
|CampaignStatus|[!INCLUDE[reportcolumn_campaignstatus](../reporting-api/includes/reportcolumn-campaignstatus.md)]|
|ClickCalls|[!INCLUDE[reportcolumn_clickcalls](../reporting-api/includes/reportcolumn-clickcalls.md)]|
|Clicks|[!INCLUDE[reportcolumn_clicks](../reporting-api/includes/reportcolumn-clicks.md)]|
|ConversionRate|[!INCLUDE[reportcolumn_conversionrate](../reporting-api/includes/reportcolumn-conversionrate.md)]|
|Conversions|[!INCLUDE[reportcolumn_conversions](../reporting-api/includes/reportcolumn-conversions.md)]|
|CostPerAssist|[!INCLUDE[reportcolumn_costperassist](../reporting-api/includes/reportcolumn-costperassist.md)]|
|CostPerConversion|[!INCLUDE[reportcolumn_costperconversion](../reporting-api/includes/reportcolumn-costperconversion.md)]|
|Ctr|[!INCLUDE[reportcolumn_ctr](../reporting-api/includes/reportcolumn-ctr.md)]|
|CurrencyCode|[!INCLUDE[reportcolumn_currencycode](../reporting-api/includes/reportcolumn-currencycode.md)]|
|CustomParameters|The current custom parameters set for the ad group.<br /><br />Each custom parameter is a key and value pair. The list of custom parameters is semicolon-delimited and each key is enclosed by braces and a leading underscore, for example *{_key1}=value1;{_key2}=value2*.|
|DeliveredMatchType|[!INCLUDE[reportcolumn_deliveredmatchtype](../reporting-api/includes/reportcolumn-deliveredmatchtype.md)]|
|DeviceOS|[!INCLUDE[reportcolumn_deviceos](../reporting-api/includes/reportcolumn-deviceos.md)]|
|DeviceType|[!INCLUDE[reportcolumn_devicetype](../reporting-api/includes/reportcolumn-devicetype.md)]|
|ExpectedCtr|[!INCLUDE[reportcolumn_expectedctr](../reporting-api/includes/reportcolumn-expectedctr.md)]|
|HistoricAdRelevance|[!INCLUDE[reportcolumn_historicadrelevance](../reporting-api/includes/reportcolumn-historicadrelevance.md)]|
|HistoricExpectedCtr|[!INCLUDE[reportcolumn_historicexpectedctr](../reporting-api/includes/reportcolumn-historicexpectedctr.md)]|
|HistoricLandingPageExperience|[!INCLUDE[reportcolumn_historiclandingpageexperience](../reporting-api/includes/reportcolumn-historiclandingpageexperience.md)]|
|HistoricQualityScore|[!INCLUDE[reportcolumn_historicqualityscore](../reporting-api/includes/reportcolumn-historicqualityscore.md)]|
|ImpressionLostToAdRelevancePercent|[!INCLUDE[reportcolumn_impressionlosttoadrelevancepercent](../reporting-api/includes/reportcolumn-impressionlosttoadrelevancepercent.md)]|
|ImpressionLostToBidPercent|[!INCLUDE[reportcolumn_impressionlosttobidpercent](../reporting-api/includes/reportcolumn-impressionlosttobidpercent.md)]|
|ImpressionLostToBudgetPercent|[!INCLUDE[reportcolumn_impressionlosttobudgetpercent](../reporting-api/includes/reportcolumn-impressionlosttobudgetpercent.md)]|
|ImpressionLostToExpectedCtrPercent|[!INCLUDE[reportcolumn_impressionlosttoexpectedctrpercent](../reporting-api/includes/reportcolumn-impressionlosttoexpectedctrpercent.md)]|
|ImpressionLostToRankPercent|[!INCLUDE[reportcolumn_impressionlosttorankpercent](../reporting-api/includes/reportcolumn-impressionlosttorankpercent.md)]|
|Impressions|[!INCLUDE[reportcolumn_impressions](../reporting-api/includes/reportcolumn-impressions.md)]|
|ImpressionSharePercent|[!INCLUDE[reportcolumn_impressionsharepercent](../reporting-api/includes/reportcolumn-impressionsharepercent.md)]|
|LandingPageExperience|[!INCLUDE[reportcolumn_landingpageexperience](../reporting-api/includes/reportcolumn-landingpageexperience.md)]|
|Language|[!INCLUDE[reportcolumn_language](../reporting-api/includes/reportcolumn-language.md)]|
|ManualCalls|[!INCLUDE[reportcolumn_manualcalls](../reporting-api/includes/reportcolumn-manualcalls.md)]|
|Network|[!INCLUDE[reportcolumn_network](../reporting-api/includes/reportcolumn-network.md)]|
|PhoneCalls|[!INCLUDE[reportcolumn_phonecalls](../reporting-api/includes/reportcolumn-phonecalls.md)]|
|PhoneImpressions|[!INCLUDE[reportcolumn_phoneimpressions](../reporting-api/includes/reportcolumn-phoneimpressions.md)]|
|Ptr|[!INCLUDE[reportcolumn_ptr](../reporting-api/includes/reportcolumn-ptr.md)]|
|QualityScore|[!INCLUDE[reportcolumn_qualityscore](../reporting-api/includes/reportcolumn-qualityscore.md)]|
|ReturnOnAdSpend|[!INCLUDE[reportcolumn_returnonadspend](../reporting-api/includes/reportcolumn-returnonadspend.md)]|
|Revenue|[!INCLUDE[reportcolumn_revenue](../reporting-api/includes/reportcolumn-revenue.md)]|
|RevenuePerAssist|[!INCLUDE[reportcolumn_revenueperassist](../reporting-api/includes/reportcolumn-revenueperassist.md)]|
|RevenuePerConversion|[!INCLUDE[reportcolumn_revenueperconversion](../reporting-api/includes/reportcolumn-revenueperconversion.md)]|
|Spend|[!INCLUDE[reportcolumn_spend](../reporting-api/includes/reportcolumn-spend.md)]|
|Status|[!INCLUDE[reportcolumn_status](../reporting-api/includes/reportcolumn-status.md)]|
|TimePeriod|[!INCLUDE[reportcolumn_timeperiod](../reporting-api/includes/reportcolumn-timeperiod.md)]|
|TopVsOther|[!INCLUDE[reportcolumn_topvsother](../reporting-api/includes/reportcolumn-topvsother.md)]|
|TrackingTemplate|The current tracking template for the ad group.|

## <a name="requiredcolumns"></a>Required Columns
The report must include the following columns.

|Column|
|----------|
|TimePeriod<br /><br />**Note**: This column is required for all aggregation types except Summary.|
[!INCLUDE[reportcolumn_statsrequired](../reporting-api/includes/reportcolumn-statsrequired.md)]
## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[AdGroupPerformanceReportRequest](../reporting-api/adgroupperformancereportrequest-data-object.md)  

